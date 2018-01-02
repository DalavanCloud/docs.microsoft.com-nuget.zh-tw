---
title: "NuGet CLI 組態命令 |Microsoft 文件"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: a50295ff-8be9-47d9-a260-822e899334cb
description: "Nuget.exe 組態命令的參考"
keywords: "nuget 組態參考組態命令"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 12a8b51dd11b9bc3a496e02e869cdeb95e67b9e3
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="config-command-nuget-cli"></a>組態命令 (NuGet CLI)

**適用於：**所有&bullet;**支援的版本，**： 所有

取得或設定 NuGet 組態值。 對於其他使用方式，請參閱[設定 NuGet 行為](../consume-packages/configuring-nuget-behavior.md)。 如需允許的索引鍵名稱的詳細資訊，請參閱[NuGet 組態檔參考](../Schema/nuget-config-file.md)。

## <a name="usage"></a>使用方式

```
nuget config -Set <name>=[<value>] [<name>=<value> ...] [options]
nuget config -AsPath <name> [options]
```

其中`<name>`和`<value>`指定要在組態中設定的索引鍵-值組。 您可以視需要指定多組。 若要移除的值，指定名稱和`=`號但沒有值。

在 NuGet 3.4 +`<value>`可以使用[環境變數](cli-ref-environment-variables.md)。

## <a name="options"></a>選項

| 選項 | 說明 |
| --- | --- |
| AsPath | 傳回組態值做為路徑，會忽略時`-Set`用。 |
| ConfigFile | *（2.5 +)* NuGet 組態檔來修改。 如果未指定， *%AppData%\NuGet\NuGet.Config*用。 |
| ForceEnglishOutput | *（3.5 +)*強制 nuget.exe 使用不變，英文的文化特性來執行。 |
| 說明 | 顯示說明命令的資訊。 |
| 非互動式 | 抑制使用者輸入或確認提示。 |
| 詳細資訊 | 指定在輸出中顯示詳細資料的數量：*正常*，*安靜*，*詳細 （2.5 +）*。 |

另請參閱[環境變數](cli-ref-environment-variables.md)

### <a name="examples"></a>範例

```
nuget config -Set repositoryPath=c:\packages -configfile c:\my.config

nuget config -Set repositoryPath=

nuget config -Set repositoryPath=%PACKAGE_REPO% -configfile %ProgramData%\NuGet\NuGetDefaults.Config

nuget config -Set HTTP_PROXY=http://127.0.0.1 -set HTTP_PROXY.USER=domain\user
```