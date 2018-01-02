---
title: "NuGet 2.9 RC 版本資訊 |Microsoft 文件"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 04d76a22-63b0-41d1-9c27-799f4b35058f
description: "包括已知的問題、 錯誤修正、 新增的功能，以及 Dcr NuGet 2.9 RC 版本資訊。"
keywords: "NuGet 2.9 RC 版本資訊、 錯誤修正的已知問題，已新增的功能，Dcr"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 64b4cd17394ddb902c7101b9117039f381dc8488
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-29-rc-release-notes"></a>NuGet 2.9 RC 版本資訊

[NuGet 2.8.7 版本資訊](../release-notes/nuget-2.8.7.md) | [NuGet 3.0 Preview 版本資訊](../release-notes/nuget-3.0-preview.md)

NuGet 2.9 已釋放 2015 年 9 月 10 日，當做 2.8.7 更新 Visual Studio 2012 和 2013年的 VSIX。

### <a name="updates-in-this-release"></a>在此版本的更新

* 現在略過處理封裝，如果其包含`.nuspec`文件的格式不正確- [PR8](https://github.com/NuGet/NuGet2/pull/8)
* 已更正的 Unix/Linux 案例-\r\n multipartwebrequest 處理[776](https://github.com/NuGet/Home/issues/776)
* 修正在 Visual Studio 2013 Community 版-建置事件與整合[1180年](https://github.com/NuGet/Home/issues/1180)


在此版本中修正的完整清單可以在 GitHub 上找到[2.8.8 里程碑](https://github.com/NuGet/Home/issues?q=milestone%3A2.8.8+is%3Aclosed)