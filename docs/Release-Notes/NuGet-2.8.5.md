---
title: "NuGet 2.8.5 版本資訊 |Microsoft 文件"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 60b96b2e-2a61-4f10-b5ad-3299f5a6d453
description: "版本資訊包含 NuGet 2.8.5 已知問題、 錯誤修正、 新增的功能，以及 Dcr。"
keywords: "NuGet 2.8.5 版本資訊，將 bug 修正、 已知問題、 已新增的功能，Dcr"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 3b297704968b8423f60e9de08e27860dc375c019
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-285-release-notes"></a>NuGet 2.8.5 版本資訊

[NuGet 2.8.3 版本資訊](../release-notes/nuget-2.8.3.md) | [NuGet 2.8.6 版本資訊](../release-notes/nuget-2.8.6.md)

NuGet 2.8.5 2015 年 3 月 30 日發行。 它是次要更新某些 VSIX 設為我們 2.8.3 目標修正程式。

在本版中的 NuGet 封裝管理員 新增的支援[DNX 目標 Framework Moniker](https://github.com/aspnet/dnx)。  這些新的 framework moniker 的支援包括：

* **core50** -'base' 的目標 framework moniker (TFM) 和核心 CLR 相容。
* **dnx452** -使用完整 4.5.2 TFM DNX 為基礎的特定應用程式的 framework 版本
* **dnx46** -使用 framework 完整 4.6 版 TFM DNX 為基礎的特定應用程式
* **dnxcore50** -A TFM DNX 為基礎的特定應用程式使用 framework Core 5.0 版

一個 bug 已修正無法正確安裝到 FSharp 專案無法在封裝：

https://nuget.codeplex.com/workitem/4400