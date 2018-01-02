---
title: "project.json 對 NuGet 套件作者的影響 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 1/9/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 983485df-9375-4827-b58b-70065320ee37
description: "NuGet 3.x 中的 project.json 實作如何影響套件作者的詳細資料，例如不支援的功能、內容以及套件格式。"
keywords: "NuGet 和 project.json, project.json 影響, 套件撰寫考量, project.json 功能"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 93a4e9f9cb57c8acbe516a957e01b801bac0e116
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="impact-of-projectjson-when-creating-packages"></a>建立套件時 project.json 的影響

NuGet 3+ 中使用的 `project.json` 系統在很多方面會影響套件作者，如下列各節中所述。

## <a name="changes-affecting-existing-packages-usage"></a>影響現有套件使用方式的變更

傳統的 NuGet 套件支援一組不會保留到過渡環境的功能。

### <a name="install-and-uninstall-scripts-are-ignored"></a>安裝和解除安裝指令碼都予以忽略

過渡的還原模型，如[相依性解析](../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference-and-projectjson)中所述，沒有「套件安裝時間」的概念。 無論套件是否存在，安裝套件時，都不會出現任何一致的程序。

此外，僅 Visual Studio 支援安裝指令碼。 其他 IDE 必須模擬 Visual Studio 擴充性 API 嘗試支援這類指令碼，一般編輯器和命令列工具中不提供支援。

### <a name="content-transforms-are-not-supported"></a>不支援內容轉換。

與安裝指令碼相類似，在套件安裝上執行的轉換通常不是等冪。 因為不再有安裝時間，所以如果過渡案例使用這類套件，就不支援並會忽略 XDT 轉換和類似的功能。


### <a name="content"></a>內容

傳統的 NuGet 套件傳送內容檔案，例如原始程式碼和組態檔。 通常用在兩個案例中：

1. 放入專案的初始檔案，讓使用者可稍後編輯它們。 常見範例為預設的組態檔。

2. 內容檔案用為安裝在專案中的組件隨附產品。 此處的範例是組件使用的標誌影像。

因類似原因，指令碼和轉換目前已停用內容支援，但我們正在努力設計內容支援。

內容檔案仍然可以載入套件中，且目前仍予忽略，不過使用者仍可以將其複製到正確的位置。

您可以查看這裡的其中一項提議，帶回內容檔案並追蹤其進度：[https://github.com/NuGet/Home/issues/627](https://github.com/NuGet/Home/issues/627)。

## <a name="impact-for-package-authors"></a>對套件作者的影響

使用上述功能的套件必須使用不同的機制。 最常用的機制是持續獲得完整支援的 MSBuild 目標/props。 組建系統可以選擇挑選套件中的其他慣例。 這是 MSBuild 目標以及 Roslyn 分析器的支援方式。 您可以建置套件，支援 `packages.config` 和 `project.json` 案例的目標和分析器。

嘗試修改專案以簡化啟動的套件，能夠作用的情況一般非常有限，應該改為提供有關如何使用套件的讀我檔案或指引。

現有的套件大部分應該不需要使用下文描述的套件格式。

格式會讓原生內容成為第一級案例。 這表示受控組件依賴與硬體實作的距離，根據目標平台沿著受控組件傳送二進位實作。 例如，System.IO.Compression 套件就是使用這項技術。 [https://www.nuget.org/packages/System.IO.Compression](https://www.nuget.org/packages/System.IO.Compression)

在摘要中，如果上述功能不是絕對必要，建議您繼續使用現有的套件格式，因為這裡描述的格式只有 NuGet 3.x+ 支援。

您可以建置套件透過填充處理 `packages.config` 和 `project.json` 案例，不過以傳統方法結構套件通常會更簡單，不需要使用上述已取代的功能。


## <a name="3x-package-format"></a>3.x 套件格式  ##

3.x 套件格式允許數個超越 NuGet 2.x 的其他功能：

1. 定義用於編譯的參考組件，和一組用於不同平台/裝置執行階段的實作組件。 可讓您充分利用平台特定的 API，同時為您的取用者提供常見的介面區。 具體而言，這讓撰寫中繼可攜式程式庫變得更容易。

2. 讓套件對平台進行樞紐分析，例如作業系統或 CPU 架構。

3. 讓您分隔附屬套件的平台特定實作。

4. 支援原生相依性成為第一級成員。