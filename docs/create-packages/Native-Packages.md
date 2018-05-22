---
title: 建立原生 NuGet 套件
description: 建立包含 C++ 程式碼而非受控程式碼的原生 NuGet 套件，供 C++ 專案使用的詳細資料。
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/09/2017
ms.topic: conceptual
ms.openlocfilehash: 1fa8bf23a3fbed686b99f1c783b0ce55b373e548
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="creating-native-packages"></a><span data-ttu-id="65817-103">建立原生套件</span><span class="sxs-lookup"><span data-stu-id="65817-103">Creating native packages</span></span>

<span data-ttu-id="65817-104">原生套件包含原生 C++ 程式碼而非受控程式碼，所以可以用在 C++ 專案中。</span><span class="sxs-lookup"><span data-stu-id="65817-104">A native package contains native C++ code instead of managed code, allowing it to be used within C++ projects.</span></span> <span data-ttu-id="65817-105">(請參閱＜取用＞一節的[原生 C++ 套件](../consume-packages/finding-and-choosing-packages.md#native-c-packages)。)</span><span class="sxs-lookup"><span data-stu-id="65817-105">(See [Native C++ Packages](../consume-packages/finding-and-choosing-packages.md#native-c-packages) in the Consume section.)</span></span>

<span data-ttu-id="65817-106">套件必須以 `native` 架構為目標，才能在 C++ 專案中取用。</span><span class="sxs-lookup"><span data-stu-id="65817-106">To be consumable in a C++ project, a package must target the `native` framework.</span></span> <span data-ttu-id="65817-107">目前沒有任何版本號碼與此架構建立關聯，因為 NuGet 對所有 C++ 專案一視同仁。</span><span class="sxs-lookup"><span data-stu-id="65817-107">At present there are not any version numbers associated with this framework as NuGet treats all C++ projects the same.</span></span>

> [!Note]
> <span data-ttu-id="65817-108">`.nuspec` 的 `<tags>` 區段務必包含 *native*，以協助其他開發人員搜尋該標記以找到您的套件。</span><span class="sxs-lookup"><span data-stu-id="65817-108">Be sure to include *native* in the `<tags>` section of your `.nuspec` to help other developers find your package by searching on that tag.</span></span>

<span data-ttu-id="65817-109">原生 NuGet 套件先以 `native` 為目標，再提供 `\build`、`\content` 和 `\tools` 資料夾中的檔案。這種情況不使用 `\lib` (NuGet 無法直接將參考新增至 C++ 專案)。</span><span class="sxs-lookup"><span data-stu-id="65817-109">Native NuGet packages targeting `native` then provide files in `\build`, `\content`, and `\tools` folders; `\lib` is not used in this case (NuGet cannot directly add references to a C++ project).</span></span> <span data-ttu-id="65817-110">套件也可以在 `\build` 中包含目標與 props 檔案，NuGet 會自動將它匯入取用該套件的專案。</span><span class="sxs-lookup"><span data-stu-id="65817-110">A package may also include targets and props files in `\build` that NuGet will automatically import into projects that consume the package.</span></span> <span data-ttu-id="65817-111">這些檔案必須與 `.targets` 及/或 `.props` 副檔名的套件識別碼同名。</span><span class="sxs-lookup"><span data-stu-id="65817-111">Those files must be named the same as the package ID with the `.targets` and/or `.props` extensions.</span></span> <span data-ttu-id="65817-112">例如，[cpprestsdk](https://nuget.org/packages/cpprestsdk/) 套件在其 `\build` 資料夾中包含 `cpprestsdk.targets` 檔案。</span><span class="sxs-lookup"><span data-stu-id="65817-112">For example, the [cpprestsdk](https://nuget.org/packages/cpprestsdk/) package includes a `cpprestsdk.targets` file in its `\build` folder.</span></span>

<span data-ttu-id="65817-113">`\build` 資料夾可用於所有 NuGet 套件，而不只是原生套件。</span><span class="sxs-lookup"><span data-stu-id="65817-113">The `\build` folder can be used for all NuGet packages and not just native packages.</span></span> <span data-ttu-id="65817-114">`\build` 資料夾和 `\content`、`\lib` 和 `\tools` 資料夾一樣採用目標架構。</span><span class="sxs-lookup"><span data-stu-id="65817-114">The `\build` folder respects target frameworks just like the `\content`, `\lib`, and `\tools` folders.</span></span> <span data-ttu-id="65817-115">這表示您可以建立 `\build\net40` 資料夾和 `\build\net45` 資料夾，然後 NuGet 會將適當的 props 和目標檔案匯入專案。</span><span class="sxs-lookup"><span data-stu-id="65817-115">This means you can create a `\build\net40` folder and a `\build\net45` folder and NuGet will import the appropriate props and targets files into the project.</span></span> <span data-ttu-id="65817-116">(不需要使用 PowerShell 指令碼匯入 MSBuild 目標。)</span><span class="sxs-lookup"><span data-stu-id="65817-116">(Use of PowerShell scripts to import MSBuild targets is not needed.)</span></span>