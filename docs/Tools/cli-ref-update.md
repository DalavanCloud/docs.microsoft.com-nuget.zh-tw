---
title: "NuGet CLI 更新命令 |Microsoft 文件"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/07/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 61fde945-6983-46a5-8636-da0fada4e641
description: "Nuget.exe 更新命令的參考"
keywords: "nuget 更新參考更新套件 命令"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 654144e93a99a4a4f8d79c0db5660cfb7c6c308e
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="update-command-nuget-cli"></a>update 命令 (NuGet CLI)

**適用於：**封裝耗用量&bullet;**支援的版本：**所有

更新專案中的所有封裝 (使用`packages.config`) 為其最新可用版本。 建議您執行['restore'](#restore)再執行`update`。 (若要更新個別的封裝，請使用[ `nuget install` ](cli-ref-install.md)但未指定版本號碼，case NuGet 會安裝最新版本。)

注意：`update`不適用於 CLI 單聲道 （Mac OSX 或 Linux） 下執行。 此命令也無法搭配使用的專案`project.json`或 PackageReference 管理格式。

`update`命令也會更新專案檔中的組件參考、 提供的參考已經存在。 如果已更新的封裝加入組件，新的參考是*不*加入。 新的封裝相依性也不需要加入其組件參考。 若要更新的組件中包含這些作業，請更新 Visual Studio 中使用封裝管理員 UI 或 Package Manager Console 中的封裝。

此命令也可用來更新本身 nuget.exe 使用*-自我*旗標。

## <a name="usage"></a>使用方式

```
nuget update <configPath> [options]
```

其中`<configPath>`識別其中`packages.config`或列出專案的相依性的方案檔。

## <a name="options"></a>選項

| 選項 | 說明 |
| --- | --- |
| ConfigFile | *（2.5 +)* NuGet 組態檔來套用。 如果未指定， *%AppData%\NuGet\NuGet.Config*用。 |
| FileConflictAction | *（2.5 +)*指定詢問您要覆寫或略過專案所參考的現有檔案時要採取的動作。 值為*覆寫，忽略無*。 |
| ForceEnglishOutput | *（3.5 +)*強制 nuget.exe 使用不變，英文的文化特性來執行。 |
| 說明 | 顯示說明命令的資訊。 |
| ID | 指定封裝識別碼，以更新的清單。 |
| MSBuildPath | *（4.0 +)*指定之路徑的 MSBuild 命令，優先於使用`-MSBuildVersion`。 |
| MSBuildVersion | *（3.2 +)*指定要搭配此命令使用 MSBuild 的版本。 支援的值為 4，12，14，15。 根據預設，在路徑中的 MSBuild 會挑出，否則，預設為最高的已安裝版本的 MSBuild。 |
| 非互動式 | 抑制使用者輸入或確認提示。 |
| 發行前版本 | 可讓更新的發行前版本。 更新已安裝的套件發行前版本時，則不需要此旗標。 |
| RepositoryPath | 指定已安裝的套件的本機資料夾。 |
| 安全 | 指定，只更新相同的主要和次要版本中可用的最高版本時已安裝的封裝將會安裝。 |
| 自我 | *（1.4 +)* Nuget.exe 更新為最新的版本; 所有其他引數會被忽略。 |
| 來源 | 指定封裝來源清單 （Url) 若要使用的更新。 如果省略，則此命令會使用組態檔中提供的來源，請參閱[設定 NuGet 行為](../Consume-Packages/Configuring-NuGet-Behavior.md)。 |
| 詳細資訊 | 指定在輸出中顯示詳細資料的數量：*正常*，*安靜*，*詳細 （2.5 +）*。 |
| 版本 | 一個封裝識別碼搭配使用時，指定要更新之封裝的版本。 |

另請參閱[環境變數](cli-ref-environment-variables.md)

## <a name="examples"></a>範例

```
nuget update

# update packages installed in solution.sln, using MSBuild version 14.0 to load the solution and its project(s).
nuget update solution.sln -MSBuildVersion 14

nuget update -safe

nuget update -self
```