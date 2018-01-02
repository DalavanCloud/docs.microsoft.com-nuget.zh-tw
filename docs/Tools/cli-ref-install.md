---
title: "NuGet CLI 安裝命令 |Microsoft 文件"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/07/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 59ac622f-837c-4545-bc93-a56330e02d71
description: "Nuget.exe 安裝命令的參考"
keywords: "nuget 安裝參考時，安裝套件 命令"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 88c123a7f2a3d628713cefcc4b110fb0205093b4
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="install-command-nuget-cli"></a>安裝命令 (NuGet CLI)

**適用於：**封裝耗用量&bullet;**支援的版本：**所有

下載並安裝到專案，將預設為目前的資料夾，使用指定的封裝來源的封裝。

> [!Tip]
> 若要下載的封裝，直接在專案內容之外，請瀏覽封裝的頁面上[nuget.org](https://www.nuget.org)選取**下載**連結。 

如果未不指定任何來源，列出全域組態檔中， `%APPDATA%\NuGet\NuGet.Config`，所使用。 請參閱[設定 NuGet 行為](../consume-packages/configuring-nuget-behavior.md)如需詳細資訊。

如果未不指定任何特定的封裝，`install`將列在專案中的所有封裝都安裝`packages.config`檔案，讓它變成類似[ `restore` ](#restore)。 (`install`命令不適用於`project.json`。)

`install`命令不會修改專案檔或`packages.config`; 如此一來，類似於`restore`，只能將封裝新增至磁碟，但不會變更專案的相依性。

若要加入相依性，請在 Visual Studio 中，將透過封裝管理員 UI 或主控台專案，或是修改`packages.config`，然後執行 `install`或`restore`。 使用專案`project.json`，您可以修改該檔案，然後執行`restore`。

## <a name="usage"></a>使用方式

```
nuget install <packageID | configFilePath> [options]
```

其中`<packageID>`名稱 （使用最新版本） 來安裝封裝或`<configFilePath>`識別`packages.config`檔案，其中列出要安裝的封裝。 您可以指定特定版本與`-Version`選項。

## <a name="options"></a>選項

| 選項 | 說明 |
| --- | --- |
| ConfigFile | *（2.5 +)* NuGet 組態檔來套用。 如果未指定， *%AppData%\NuGet\NuGet.Config*用。 |
| DisableParallelProcessing | 安裝多個封裝，以平行方式停用。 |
| ExcludeVersion | 會封裝安裝到名為與封裝名稱和版本號碼。 |
| FallbackSource | *（3.2 +)*作為後援，萬一主要中找不到封裝的封裝來源的清單或預設的來源。 |
| ForceEnglishOutput | *（3.5 +)*強制 nuget.exe 使用不變，英文的文化特性來執行。 |
| 架構 | *（4.4 +)*用於選取的相依性的目標 framework。 預設值是 'Any' 如果未指定。 |
| 說明 | 顯示說明命令的資訊。 |
| 無快取記憶體 | NuGet 可防止從本機電腦的快取使用的封裝。 |
| 非互動式 | 抑制使用者輸入或確認提示。 |
| OutputDirectory | 指定在其中安裝封裝的資料夾。 如果沒有指定資料夾，則會使用目前的資料夾。 |
| PackageSaveMode | 指定要儲存封裝的安裝後的檔案類型： 其中一個`nuspec`， `nupkg`，或`nuspec;nupkg`。 |
| 發行前版本 | 允許安裝的套件發行前版本。 還原的封裝時，不需要此旗標`packages.config`。 |
| RequireConsent | 確認一次還原封裝才能下載和安裝封裝。 如需詳細資訊，請參閱[封裝還原，](../consume-packages/package-restore.md)。 |
| SolutionDirectory | 指定要還原封裝方案的根資料夾。 |
| 來源 | 指定封裝來源清單 （Url) 使用。 如果省略，則此命令會使用組態檔中提供的來源，請參閱[設定 NuGet 行為](../Consume-Packages/Configuring-NuGet-Behavior.md)。 |
| 詳細資訊 | 指定在輸出中顯示詳細資料的數量：*正常*，*安靜*，*詳細 （2.5 +）*。 |
| 版本 | 指定要安裝之封裝的版本。 |

另請參閱[環境變數](cli-ref-environment-variables.md)

## <a name="examples"></a>範例

```
nuget install elmah

nuget install packages.config

nuget install ninject -OutputDirectory c:\proj
```