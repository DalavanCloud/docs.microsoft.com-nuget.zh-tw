---
title: NuGet 3.4.4 版本資訊
description: 版本資訊 NuGet 3.4.4 包括已知問題、 bug 修正、 新增的功能和 Dcr。
author: karann-msft
ms.author: karann
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 44a9f21c61f0552fdc21aab24f48eee993654b01
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43547469"
---
# <a name="nuget-344-release-notes"></a>NuGet 3.4.4 版本資訊

[NuGet 3.4.3 版本資訊](../release-notes/nuget-3.4.3.md) | [NuGet 3.5 Beta 版本資訊](../release-notes/nuget-3.5-Beta.md)

此版本的主要焦點是 3.4.3 品質改善新版的 nuget.exe 與 Visual Studio 擴充功能的一些修正程式。

您可以下載 VSIX 和 nuget.exe[此處](https://dist.nuget.org/index.html)。

## <a name="344-rtmhttpsgithubcomnugetnugetclienttree344-rtm-2016-05-19"></a>[3.4.4-rtm](https://github.com/NuGet/NuGet.Client/tree/3.4.4-rtm) (2016年-05-19)

[完整的變更記錄](https://github.com/NuGet/NuGet.Client/compare/3.5.0-beta-final...3.4.4-rtm)

[問題清單](https://github.com/NuGet/Home/issues?q=is%3Aissue+milestone%3A3.4.4+is%3Aclosed)

### <a name="changes"></a>變更

- 組件的改進： 改進封裝符號，使用封裝`project.json`等等[ \#606](https://github.com/NuGet/NuGet.Client/pull/606)
- 尋找專案中更新命令失敗時所顯示的例外狀況 [\#605] (https://github.com/NuGet/NuGet.Client/pull/605
- 從輸入讀取封裝的型別`.nuspec`並`project.json`封裝時[ \#603](https://github.com/NuGet/NuGet.Client/pull/603)
- 請 NuGet.Shared 不是專案。 [\#602](https://github.com/NuGet/NuGet.Client/pull/602)
- 推播逾時做為 HTTP 回應逾時[ \#599](https://github.com/NuGet/NuGet.Client/pull/599)
- 未來時間的套件檔案不會使用其時間[ \#597](https://github.com/NuGet/NuGet.Client/pull/597)
- 更新`NuGet.Core.dll`版本來修正 XML 問題 2.12.0 [ \#594](https://github.com/NuGet/NuGet.Client/pull/594)
- 支援./NuGet.CommandLine.XPlat-v \</verbosity\> \<模式\> [ \#593](https://github.com/NuGet/NuGet.Client/pull/593)
- 顯示錯誤還原而不需要`project.json`或是`packages.config` [ \#590](https://github.com/NuGet/NuGet.Client/pull/590)
- 修正相依性版本，當所需的版本不同時[ \#559](https://github.com/NuGet/NuGet.Client/pull/559)