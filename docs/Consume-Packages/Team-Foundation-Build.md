---
title: "使用 Team Foundation Build 的 NuGet 套件還原逐步解說 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 1/9/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 3113cccd-35f7-4980-8a6e-fc06556b5064
description: "使用 Team Foundation Build (TFS 和 Visual Studio Team Services) 進行 NuGet 套件還原的逐步解說。"
keywords: "NuGet 套件還原、NuGet 和 TFS、NuGet 和 VSTS、NuGet 組建系統、Team Foundation Build、自訂 MSBuild 專案、雲端組建、持續整合"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 4be1bb83549958897a15d690439cac073c9683d1
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="setting-up-package-restore-with-team-foundation-build"></a>使用 Team Foundation Build 設定套件還原

> 適用於：
>  - 在任何 TFS 版本上執行的自訂 MSBuild 專案
>  - Team Foundation Server 2012 或更早版本
>  - 移轉至 TFS 2013 或更新版本的自訂 Team Foundation Build 流程範本
>  - 已移除 Nuget 還原功能的建置流程範本
>
> 如果您搭配使用 Visual Studio Team Services 或內部部署 Team Foundation Server 2013 與其建置流程範本，則會在建置流程進行自動套件還原。

本節提供在 [git](http://en.wikipedia.org/wiki/Git_(software)) 和 [TF 版本設定](http://msdn.microsoft.com/library/ms181237(v=vs.120).aspx) 的 [Team Foundation 建置](http://msdn.microsoft.com/library/ms181710(v=VS.90).aspx)期間如何還原套件的詳細逐步解說。

雖然這個逐步解說專屬於使用 [Team Foundation Service](http://tfs.visualstudio.com/) 的案例，但是這些概念也適用於其他版本設定和組建系統。

## <a name="the-general-approach"></a>一般方法

使用 NuGet 的優點在於，您可以使用它來避免將二進位檔簽入到版本設定系統。

因為開發人員必須在本機上開始工作之前複製整個存放庫 (包含完整歷程記錄)，所以如果您使用[分散式版本設定](http://en.wikipedia.org/wiki/Distributed_revision_control)系統 (例如 git)，則這特別有趣。 因為二進位檔案在儲存時通常不會進行差異壓縮，所以簽入二進位檔可能會造成明顯存放庫膨脹。

NuGet 現在已支援在建置期間[還原套件](../consume-packages/package-restore.md)較長的時間。 先前的實作具有要擴充建置流程之套件的無解問題，因為 NuGet 已在建置專案時還原套件。 不過，MSBuild 不允許在建置期間擴充建置；有人可能會認為這是 MSBuild 中的問題，但我認為這是無法避免的問題。 根據您需要擴充的層面，在還原套件時註冊可能會太晚。

修復此問題是確保還原套件為建置流程中的第一個步驟。 NuGet 2.7+ 透過簡化的命令列來簡化這項作業：

```
nuget restore path\to\solution.sln
```

當您的建置流程在建置程式碼之前還原套件時，您不需要簽入 `.targets` 檔案

> [!Note]
> 必須編寫套件，以允許在 Visual Studio 中載入。 否則，您可能仍然想要簽入 `.targets` 檔案，讓其他開發人員只需要開啟方案，而不需要先還原套件。

下列示範專案會示範如何設定組建，而使用此方式，則不需要簽入 `packages` 資料夾和 `.targets` 檔案。 它也會示範如何在 Team Foundation Service 上設定這個範例專案的自動化建置。

## <a name="repository-structure"></a>存放庫結構

我們的示範專案是一種簡單命令列工具，可使用命令列引數來查詢 Bing。 它的目標設為 .NET Framework 4，並使用許多 [BCL 套件](http://www.nuget.org/profiles/dotnetframework/) ([Microsoft.Net.Http](http://www.nuget.org/packages/Microsoft.Net.Http)、[Microsoft.Bcl](http://www.nuget.org/packages/Microsoft.Bcl)、[Microsoft.Bcl.Async](http://www.nuget.org/packages/Microsoft.Bcl.Async) 和 [Microsoft.Bcl.Build](http://www.nuget.org/packages/Microsoft.Bcl.Build))。

存放庫的結構如下：

    <Project>
        │   .gitignore
        │   .tfignore
        │   build.proj
        │
        ├───src
        │   │   BingSearcher.sln
        │   │
        │   └───BingSearcher
        │       │   App.config
        │       │   BingSearcher.csproj
        │       │   packages.config
        │       │   Program.cs
        │       │
        │       └───Properties
        │               AssemblyInfo.cs
        │
        └───tools
            └───NuGet
                    nuget.exe

您可以看到我們尚未簽入 `packages` 資料夾，也未簽入任何 `.targets` 檔案。

不過，我們已在建置期間簽入必要 `nuget.exe`。 遵循廣泛使用的慣例，我們已將它簽入共用的 `tools` 資料夾下方。

原始程式碼是在 `src` 資料夾下方。 雖然我們的示範僅使用單一方案，但是您可以輕鬆地想像此資料夾包含多個方案。

### <a name="ignore-files"></a>忽略檔案

> [!Note]
> 目前 [NuGet 用戶端中有已知 Bug](https://nuget.codeplex.com/workitem/4072)，可讓用戶端仍然將 `packages` 資料夾新增至版本設定。 因應措施是停用原始檔控制整合。 若要這樣做，您需要與方案平行的 `.nuget` 資料夾中有 `Nuget.Config ` 檔案。 如果此資料夾尚未存在，則您需要建立它。 在 [`Nuget.Config`](../consume-packages/configuring-nuget-behavior.md) 中，新增下列內容：

```xml
<configuration>
    <solution>
        <add key="disableSourceControlIntegration" value="true" />
    </solution>
</configuration>
```


為了與不想要簽入 **packages** 資料夾的版本設定進行通訊，我們已新增 git (`.gitignore`) 和 TF 版本設定 (`.tfignore`) 的忽略檔案。 這些檔案描述您不想要簽入之檔案的模式。

`.gitignore` 檔案的內容如下：

    syntax: glob
    *.user
    *.suo
    bin
    obj
    packages

`.gitignore` 檔案的[功能相當強大](https://www.kernel.org/pub/software/scm/git/docs/gitignore.html)。 例如，如果您想要通常不要簽入 `packages` 資料夾的內容，但想要進行先前之簽入 `.targets` 檔案的指引，則可能改為具有下列規則：

    packages
    !packages/**/*.targets

這會排除所有 `packages` 資料夾，但會重新包含所有內含的 `.targets` 檔案。 但您可以在[這裡](https://github.com/github/gitignore/blob/master/VisualStudio.gitignore)找到 `.gitignore` 檔案的範本，此範本是特別為 Visual Studio 開發人員需求量身訂做。

TF 版本設定透過 [.tfignore](http://msdn.microsoft.com/library/ms245454.aspx) 檔案支援非常類似的機制。 語法幾乎相同：

    *.user
    *.suo
    bin
    obj
    packages

## <a name="buildproj"></a>build.proj

在我們的示範中，建置流程相當簡單。 我們將建立 MSBuild 專案以建置所有方案，同時確保先還原套件，再建置方案。

這個專案會有三個傳統目標 (`Clean`、`Build` 和 `Rebuild`) 以及一個新的目標 (`RestorePackages`)。

- `Build` 和 `Rebuild` 目標都是根據 `RestorePackages`。 這確保您可以同時執行 `Build` 和 `Rebuild`，並且依賴所還原的套件。
- `Clean`、`Build` 和 `Rebuild` 會叫用所有方案檔上的對應 MSBuild 目標。
- `RestorePackages` 目標會叫用每個方案檔的 `nuget.exe`。 這是使用 [MSBuild 的批次功能](http://msdn.microsoft.com/library/ms171473.aspx)所完成。

結果如下所示：

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0"
            DefaultTargets="Build"
            xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
    <OutDir Condition=" '$(OutDir)'=='' ">$(MSBuildThisFileDirectory)bin\</OutDir>
    <Configuration Condition=" '$(Configuration)'=='' ">Release</Configuration>
    <SourceHome Condition=" '$(SourceHome)'=='' ">$(MSBuildThisFileDirectory)src\</SourceHome>
    <ToolsHome Condition=" '$(ToolsHome)'=='' ">$(MSBuildThisFileDirectory)tools\</ToolsHome>
    </PropertyGroup>

    <ItemGroup>
    <Solution Include="$(SourceHome)*.sln">
        <AdditionalProperties>OutDir=$(OutDir);Configuration=$(Configuration)</AdditionalProperties>
    </Solution>
    </ItemGroup>

    <Target Name="RestorePackages">
    <Exec Command="&quot;$(ToolsHome)NuGet\nuget.exe&quot; restore &quot;%(Solution.Identity)&quot;" />
    </Target>

    <Target Name="Clean">
    <MSBuild Targets="Clean"
                Projects="@(Solution)" />
    </Target>

    <Target Name="Build" DependsOnTargets="RestorePackages">
    <MSBuild Targets="Build"
                Projects="@(Solution)" />
    </Target>

    <Target Name="Rebuild" DependsOnTargets="RestorePackages">
    <MSBuild Targets="Rebuild"
                Projects="@(Solution)" />
    </Target>
</Project>
```

## <a name="configuring-team-build"></a>設定 Team Build

Team Build 提供各種流程範本。 在此示範中，我們將使用 Team Foundation Service。 內部部署 TFS 安裝極為類似。

Git 和 TF 版本設定具有不同的 Team Build 範本，因此下列步驟會根據使用的版本設定系統而不同。 在這兩種情況下，您只需要選取 build.proj 作為您想要建置的專案。

首先，請查看 git 的流程範本。 在 git 範本中，透過 `Solution to build` 屬性選取組建：

![git 的建置流程](media/PackageRestoreTeamBuildGit.png)

請注意，此屬性是您存放庫中的位置。 因為 `build.proj` 位在根目錄中，所以我們只是使用 `build.proj`。 如果您將組建檔案置於稱為 `tools` 的資料夾下方，則值會是 `tools\build.proj`。

在 TF 版本設定範本中，會透過 `Projects` 屬性選取專案：

![TFVC 的建置流程](media/PackageRestoreTeamBuildTFVC.png)

相較於 git 範本，TF 版本設定支援選擇器 (右側有三個點的按鈕)。 因此，為了避免任何鍵入錯誤，建議您使用它們來選取專案。