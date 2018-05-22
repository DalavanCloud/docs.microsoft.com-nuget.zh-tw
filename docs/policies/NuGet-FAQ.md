---
title: NuGet 常見問題集
description: 在命令列上和 Visual Studio 中使用 NuGet 以及使用 NuGet 資源庫的常見問題和解答。
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/11/2018
ms.topic: conceptual
ms.openlocfilehash: bcdb4e8971ee4e742e6cf37f8b662e50a77604f0
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="nuget-frequently-asked-questions"></a><span data-ttu-id="4c73b-103">NuGet 常見問題集</span><span class="sxs-lookup"><span data-stu-id="4c73b-103">NuGet frequently-asked questions</span></span>

<span data-ttu-id="4c73b-104">**執行 NuGet 所需的作業為何？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-104">**What is required to run NuGet?**</span></span>

<span data-ttu-id="4c73b-105">[安裝指南](../install-nuget-client-tools.md)包含 UI 和命令列工具的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="4c73b-105">All the information around both UI and command-line tools is available in the [Install guide](../install-nuget-client-tools.md).</span></span>

<span data-ttu-id="4c73b-106">**NuGet 支援 Mono 嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-106">**Does NuGet support Mono?**</span></span>

<span data-ttu-id="4c73b-107">命令列工具 `nuget.exe` 會在 Mono 3.2+ 下建置並執行，而且可以在 Mono 中建立套件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-107">The command-line tool, `nuget.exe`, builds and runs under Mono 3.2+ and can create packages in Mono.</span></span>

<span data-ttu-id="4c73b-108">雖然 `nuget.exe` 完整運作於 Windows 上，但是 Linux 和 OS X 上已有已知問題。請參閱 GitHub 上的 [Mono 問題](https://github.com/NuGet/Home/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+mono)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-108">Although `nuget.exe` works fully on Windows, there are known issues on Linux and OS X. Refer to [Mono issues](https://github.com/NuGet/Home/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+mono) on GitHub.</span></span>

<span data-ttu-id="4c73b-109">[圖形化用戶端](https://github.com/mrward/monodevelop-nuget-addin)可作為 MonoDevelop 的增益集。</span><span class="sxs-lookup"><span data-stu-id="4c73b-109">A [graphical client](https://github.com/mrward/monodevelop-nuget-addin) is available as an add-in for MonoDevelop.</span></span>

<span data-ttu-id="4c73b-110">**如何判斷套件所包含的內容，以及它對我的應用程式而言是否穩定而且有用？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-110">**How can I determine what a package contains and whether it's stable and useful for my application?**</span></span>

<span data-ttu-id="4c73b-111">了解套件的主要來源是其在 nuget.org 上的清單頁面 (或另一個私人摘要)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-111">The primary source for learning about a package is its listing page on nuget.org (or another private feed).</span></span> <span data-ttu-id="4c73b-112">nuget.org 上的每個套件頁面都會包含套件的描述、其版本歷程記錄和使用量統計資料。</span><span class="sxs-lookup"><span data-stu-id="4c73b-112">Each package page on nuget.org includes a description of the package, its version history, and usage statistics.</span></span> <span data-ttu-id="4c73b-113">套件頁面上的 [資訊] 區段也會包含專案網站的連結，而在專案網站中，您一般可以找到許多範例和其他文件協助您了解如何使用套件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-113">The **Info** section on the package page also contains a link to the project's web site where you typically find many examples and other documentation to help you learn how the package is used.</span></span>

<span data-ttu-id="4c73b-114">如需詳細資訊，請參閱[尋找及選擇套件](../consume-packages/finding-and-choosing-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-114">For more information, see [Finding and choosing packages](../consume-packages/finding-and-choosing-packages.md).</span></span>

## <a name="nuget-in-visual-studio"></a><span data-ttu-id="4c73b-115">Visual Studio 中的 NuGet</span><span class="sxs-lookup"><span data-stu-id="4c73b-115">NuGet in Visual Studio</span></span>

<span data-ttu-id="4c73b-116">**在不同的 Visual Studio 產品中，如何支援 NuGet？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-116">**How is NuGet supported in different Visual Studio products?**</span></span>

- <span data-ttu-id="4c73b-117">Windows 上的 Visual Studio 支援[套件管理員 UI](../tools/package-manager-ui.md) 和[套件管理員主控台](../tools/package-manager-console.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-117">Visual Studio on Windows supports the [Package Manager UI](../tools/package-manager-ui.md) and the [Package Manager Console](../tools/package-manager-console.md).</span></span>
- <span data-ttu-id="4c73b-118">Visual Studio for Mac 具有內建 NuGet 功能，如[在專案中包含 NuGet 套件](/visualstudio/mac/nuget-walkthrough)中所述。</span><span class="sxs-lookup"><span data-stu-id="4c73b-118">Visual Studio for Mac has built-in NuGet capabilities as described on [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough).</span></span>
- <span data-ttu-id="4c73b-119">Visual Studio Code (所有平台) 沒有任何直接 NuGet 整合。</span><span class="sxs-lookup"><span data-stu-id="4c73b-119">Visual Studio Code (all platforms) does not have any direct NuGet integration.</span></span> <span data-ttu-id="4c73b-120">請使用 [NuGet CLI](../tools/nuget-exe-cli-reference.md) 或 [dotnet CLI](../tools/dotnet-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-120">Use the [NuGet CLI](../tools/nuget-exe-cli-reference.md) or the [dotnet CLI](../tools/dotnet-commands.md).</span></span>
- <span data-ttu-id="4c73b-121">Visual Studio Team Services 提供[還原 NuGet 套件的建置步驟](/vsts/build-release/tasks/package/nuget)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-121">Visual Studio Team Services provides [a build step to restore NuGet packages](/vsts/build-release/tasks/package/nuget).</span></span> <span data-ttu-id="4c73b-122">您也可以[在 Team Services 上裝載私用 NuGet 套件摘要](https://www.visualstudio.com/docs/package/nuget/publish)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-122">You can also [host private NuGet package feeds on Team Services](https://www.visualstudio.com/docs/package/nuget/publish).</span></span>

<span data-ttu-id="4c73b-123">**如何檢查已安裝 NuGet 工具的確切版本？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-123">**How do I check the exact version of the NuGet tools that are installed?**</span></span>

<span data-ttu-id="4c73b-124">在 Visual Studio 中，使用 [說明] > [關於 Microsoft Visual Studio] 命令，並查看 [NuGet 套件管理員] 旁邊所顯示的版本。</span><span class="sxs-lookup"><span data-stu-id="4c73b-124">In Visual Studio, use the **Help > About Microsoft Visual Studio** command and look at the version displayed next to **NuGet Package Manager**.</span></span>

<span data-ttu-id="4c73b-125">或者，啟動 [套件管理員主控台] ([工具] > [NuGet 套件管理員] > [套件管理員主控台])，並輸入 `$host` 以查看 NuGet 的相關資訊 (包含版本)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-125">Alternatively, launch the Package Manager Console (**Tools > NuGet Package Manager > Package Manager Console**) and enter `$host` to see information about NuGet including the version.</span></span>

<span data-ttu-id="4c73b-126">**NuGet 支援哪些程式設計語言？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-126">**What programming languages are supported by NuGet?**</span></span>

<span data-ttu-id="4c73b-127">NuGet 一般適用於 .NET 語言，並且設計目的是將 .NET 程式庫帶入專案中。</span><span class="sxs-lookup"><span data-stu-id="4c73b-127">NuGet generally works for .NET languages and is designed to bring .NET libraries into a project.</span></span> <span data-ttu-id="4c73b-128">在某些專案類型中，它也支援 MSBuild 和 Visual Studio 自動化，因此在各種程度上也支援其他專案和語言。</span><span class="sxs-lookup"><span data-stu-id="4c73b-128">Because it also supports MSBuild and Visual Studio automation in some project types, it also supports other projects and languages to various degrees.</span></span>

<span data-ttu-id="4c73b-129">最新版的 NuGet 支援 C#、Visual Basic、F#、WiX 和 C++。</span><span class="sxs-lookup"><span data-stu-id="4c73b-129">The most recent version of NuGet supports C#, Visual Basic, F#, WiX, and C++.</span></span>

<span data-ttu-id="4c73b-130">**NuGet 支援哪些專案範本？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-130">**What project templates are supported by NuGet?**</span></span>

<span data-ttu-id="4c73b-131">NuGet 完整支援各種專案範本，例如 Windows、Web、Cloud、SharePoint、Wix 等等。</span><span class="sxs-lookup"><span data-stu-id="4c73b-131">NuGet has full support for a variety of project templates like Windows, Web, Cloud, SharePoint, Wix, and so on.</span></span>

<span data-ttu-id="4c73b-132">**如何更新屬於 Visual Studio 範本的套件？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-132">**How do I update packages that are part of Visual Studio templates?**</span></span>

<span data-ttu-id="4c73b-133">移至套件管理員 UI 中的 [更新] 索引標籤，然後選取 [全部更新]，或使用套件管理員主控台中的 [`Update-Package` 命令](../tools/ps-ref-update-package.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-133">Go to the **Updates** tab in the Package Manager UI and select **Update All**, or use the [`Update-Package` command](../tools/ps-ref-update-package.md) from the Package Manager Console.</span></span>

<span data-ttu-id="4c73b-134">若要更新範本本身，您需要手動更新範本存放庫。</span><span class="sxs-lookup"><span data-stu-id="4c73b-134">To update the template itself, you need to manually update the template repository.</span></span> <span data-ttu-id="4c73b-135">請參閱有關本主題的 [Xavier Decoster 部落格](http://www.xavierdecoster.com/update-project-template-to-latest-nuget-packages)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-135">See [Xavier Decoster's blog](http://www.xavierdecoster.com/update-project-template-to-latest-nuget-packages) on this subject.</span></span> <span data-ttu-id="4c73b-136">請注意，您必須自負這項作業的風險；因為，如果所有相依性的最新版本彼此不相容，則手動更新可能會損毀範本。</span><span class="sxs-lookup"><span data-stu-id="4c73b-136">Note that this is done at your own risk, because manual updates might corrupt the template if the latest version of all dependencies are not compatible with each other.</span></span>

<span data-ttu-id="4c73b-137">**可以在 Visual Studio 外部使用 NuGet 嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-137">**Can I use NuGet outside of Visual Studio?**</span></span>

<span data-ttu-id="4c73b-138">是，NuGet 只能直接從命令列運作。</span><span class="sxs-lookup"><span data-stu-id="4c73b-138">Yes, NuGet works directly from the command line.</span></span> <span data-ttu-id="4c73b-139">請參閱[安裝指南](../install-nuget-client-tools.md)和 [CLI 參考](../tools/nuget-exe-cli-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-139">See the [Install guide](../install-nuget-client-tools.md) and the [CLI reference](../tools/nuget-exe-cli-reference.md).</span></span>

## <a name="nuget-command-line"></a><span data-ttu-id="4c73b-140">NuGet 命令列</span><span class="sxs-lookup"><span data-stu-id="4c73b-140">NuGet command line</span></span>

<span data-ttu-id="4c73b-141">**如何取得最新版的 NuGet 命令列工具？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-141">**How do I get the latest version of NuGet command line tool?**</span></span>

<span data-ttu-id="4c73b-142">請參閱[安裝指南](../install-nuget-client-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-142">See the [Install guide](../install-nuget-client-tools.md).</span></span>

<span data-ttu-id="4c73b-143">**nuget.exe 的授權為何？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-143">**What is the license for nuget.exe?**</span></span>

<span data-ttu-id="4c73b-144">您可以根據 MIT 授權的規定來轉散發 nuget.exe。</span><span class="sxs-lookup"><span data-stu-id="4c73b-144">You are allowed to redistribute nuget.exe under the terms of the MIT license.</span></span> <span data-ttu-id="4c73b-145">您負責更新和維護您選擇要轉散發的任何 nuget.exe 複本。</span><span class="sxs-lookup"><span data-stu-id="4c73b-145">You are responsible for updating and servicing any copies of nuget.exe that you choose to redistribute.</span></span>

<span data-ttu-id="4c73b-146">**可以擴充 NuGet 命令列工具嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-146">**Is it possible to extend the NuGet command line tool?**</span></span>

<span data-ttu-id="4c73b-147">是，可以將自訂命令新增至 `nuget.exe`，如 [Rob Reynold 文章](http://geekswithblogs.net/robz/archive/2011/07/15/extend-nuget-command-line.aspx)中所述。</span><span class="sxs-lookup"><span data-stu-id="4c73b-147">Yes, it's possible to add custom commands to `nuget.exe`, as described in [Rob Reynold's post](http://geekswithblogs.net/robz/archive/2011/07/15/extend-nuget-command-line.aspx).</span></span>

## <a name="nuget-package-manager-console-visual-studio-on-windows"></a><span data-ttu-id="4c73b-148">NuGet 套件管理員主控台 (Windows 上的 Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="4c73b-148">NuGet Package Manager Console (Visual Studio on Windows)</span></span>

<span data-ttu-id="4c73b-149">**如何在套件管理員主控台中存取 DTE 物件？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-149">**How do I get access to the DTE object in the Package Manager console?**</span></span>

<span data-ttu-id="4c73b-150">Visual Studio 自動化物件模型中的最上層物件稱為 DTE (開發工具環境) 物件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-150">The top-level object in the Visual Studio automation object model is called the DTE (Development Tools Environment) object.</span></span> <span data-ttu-id="4c73b-151">此主控台透過名為 `$DTE` 的變數提供這個項目。</span><span class="sxs-lookup"><span data-stu-id="4c73b-151">The console provides this through a variable named `$DTE`.</span></span> <span data-ttu-id="4c73b-152">如需詳細資訊，請參閱＜Visual Studio 擴充性＞文件中的 [Automation Model Overview](/visualstudio/extensibility/internals/automation-model-overview) (自動化模型概觀)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-152">For more information, see [Automation Model Overview](/visualstudio/extensibility/internals/automation-model-overview) in the Visual Studio Extensibility documentation.</span></span>

<span data-ttu-id="4c73b-153">**我嘗試將 $DTE 變數轉換為類型 DTE2，但收到錯誤：無法將 "EnvDTE.DTEClass" 類型的 "EnvDTE.DTEClass" 值轉換為 "EnvDTE80.DTE2" 類型。有什麼問題？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-153">**I try to cast the $DTE variable to the type DTE2, but I get an error: Cannot convert the "EnvDTE.DTEClass" value of type "EnvDTE.DTEClass" to type "EnvDTE80.DTE2". What's wrong?**</span></span>

<span data-ttu-id="4c73b-154">這是 PowerShell 如何與 COM 物件互動的已知問題。</span><span class="sxs-lookup"><span data-stu-id="4c73b-154">This is a known issue with how PowerShell interacts with a COM object.</span></span> <span data-ttu-id="4c73b-155">請嘗試下列動作：</span><span class="sxs-lookup"><span data-stu-id="4c73b-155">Try the following:</span></span>

```ps
`$dte2 = Get-Interface $dte ([EnvDTE80.DTE2])`
```

<span data-ttu-id="4c73b-156">`Get-Interface` 是 NuGet PowerShell 主機所新增的 Helper 函式。</span><span class="sxs-lookup"><span data-stu-id="4c73b-156">`Get-Interface` is a helper function added by the NuGet PowerShell host.</span></span>

## <a name="creating-and-publishing-packages"></a><span data-ttu-id="4c73b-157">建立並發行套件</span><span class="sxs-lookup"><span data-stu-id="4c73b-157">Creating and publishing packages</span></span>

<span data-ttu-id="4c73b-158">**如何在摘要中列出我的套件？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-158">**How do I list my package in a feed?**</span></span>

<span data-ttu-id="4c73b-159">請參閱[建立並發行套件](../quickstart/create-and-publish-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-159">See [Creating and publishing a package](../quickstart/create-and-publish-a-package.md).</span></span>

<span data-ttu-id="4c73b-160">**我的程式庫有多個版本將目標設為不同的 .NET Framework 版本。如何建置支援此項目的單一套件？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-160">**I have multiple versions of my library that target different versions of the .NET Framework. How do I build a single package that supports this?**</span></span>

<span data-ttu-id="4c73b-161">請參閱[支援多個 .NET Framework 版本和設定檔](../create-packages/supporting-multiple-target-frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-161">See [Supporting Multiple .NET Framework Versions and Profiles](../create-packages/supporting-multiple-target-frameworks.md).</span></span>

<span data-ttu-id="4c73b-162">**如何設定我自己的存放庫或摘要？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-162">**How do I set up my own repository or feed?**</span></span>

<span data-ttu-id="4c73b-163">請參閱[裝載套件概觀](../hosting-packages/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-163">See the [Hosting packages overview](../hosting-packages/overview.md).</span></span>

<span data-ttu-id="4c73b-164">**如何將套件大量上傳至 NuGet 摘要？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-164">**How can I upload packages to my NuGet feed in bulk?**</span></span>

<span data-ttu-id="4c73b-165">請參閱[大量發行 NuGet 套件](http://jeffhandley.com/archive/2012/12/13/Bulk-Publishing-NuGet-Packages.aspx) (jeffhandly.com)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-165">See [Bulk publishing NuGet packages](http://jeffhandley.com/archive/2012/12/13/Bulk-Publishing-NuGet-Packages.aspx) (jeffhandly.com).</span></span>

## <a name="working-with-packages"></a><span data-ttu-id="4c73b-166">使用套件</span><span class="sxs-lookup"><span data-stu-id="4c73b-166">Working with packages</span></span>

<span data-ttu-id="4c73b-167">**專案層級套件與方案層級套件之間的差異為何？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-167">**What is the difference between a project-level package and a solution-level package?**</span></span>

<span data-ttu-id="4c73b-168">只要在方案中安裝方案層級套件 (NuGet 3.x+) 一次，就可以用於方案中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="4c73b-168">A solution-level package (NuGet 3.x+) is installed only once in a solution and is then available for all projects in the solution.</span></span> <span data-ttu-id="4c73b-169">專案層級套件會安裝在使用它的每個專案中。</span><span class="sxs-lookup"><span data-stu-id="4c73b-169">A project-level package is installed in each project that uses it.</span></span> <span data-ttu-id="4c73b-170">方案層級套件也可能會安裝可從套件管理員主控台內呼叫的新命令。</span><span class="sxs-lookup"><span data-stu-id="4c73b-170">A solution-level package might also install new commands that can be called from within the Package Manager Console.</span></span>

<span data-ttu-id="4c73b-171">**可以在沒有網際網路連線的情況下安裝 NuGet 套件嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-171">**Is it possible to install NuGet packages without Internet connectivity?**</span></span>

<span data-ttu-id="4c73b-172">是，請參閱 Scott Hanselman 的部落格文章 [How to access NuGet when nuget.org is down (or you're on a plane](http://www.hanselman.com/blog/HowToAccessNuGetWhenNuGetorgIsDownOrYoureOnAPlane.aspx) (如何在 nuget.org 關閉 (或您在飛機上) 時存取 NuGet) (hanselman.com)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-172">Yes, see Scott Hanselman's Blog post [How to access NuGet when nuget.org is down (or you're on a plane)](http://www.hanselman.com/blog/HowToAccessNuGetWhenNuGetorgIsDownOrYoureOnAPlane.aspx) (hanselman.com).</span></span>

<span data-ttu-id="4c73b-173">**如何將套件從預設套件資料夾安裝至不同位置？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-173">**How do I install packages in a different location from the default packages folder?**</span></span>

<span data-ttu-id="4c73b-174">請使用 `nuget config -set repositoryPath=<path>` 在 `Nuget.Config` 中設定 [`repositoryPath`](../reference/nuget-config-file.md#config-section) 設定。</span><span class="sxs-lookup"><span data-stu-id="4c73b-174">Set the [`repositoryPath`](../reference/nuget-config-file.md#config-section) setting in `Nuget.Config` using `nuget config -set repositoryPath=<path>`.</span></span>

<span data-ttu-id="4c73b-175">**如何避免將 NuGet 套件資料夾新增至原始檔控制嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-175">**How do I avoid adding the NuGet packages folder into to source control?**</span></span>

<span data-ttu-id="4c73b-176">將 `Nuget.Config` 中的 [`disableSourceControlIntegration`](../reference/nuget-config-file.md#solution-section) 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4c73b-176">Set the [`disableSourceControlIntegration`](../reference/nuget-config-file.md#solution-section) in `Nuget.Config` to `true`.</span></span> <span data-ttu-id="4c73b-177">此索引鍵作用於方案層級，因此需要新增至 `$(Solutiondir)\.nuget\Nuget.Config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="4c73b-177">This key works at the solution level and hence need to be added to the `$(Solutiondir)\.nuget\Nuget.Config` file.</span></span> <span data-ttu-id="4c73b-178">從 Visual Studio 啟用套件還原時會自動建立這個檔案。</span><span class="sxs-lookup"><span data-stu-id="4c73b-178">Enabling package restore from Visual Studio creates this file automatically.</span></span>

<span data-ttu-id="4c73b-179">**如何關閉套件還原？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-179">**How do I turn off package restore?**</span></span>

<span data-ttu-id="4c73b-180">請參閱[啟用和停用套件還原](../consume-packages/package-restore.md#enabling-and-disabling-package-restore)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-180">See [Enabling and disabling package restore](../consume-packages/package-restore.md#enabling-and-disabling-package-restore).</span></span>

<span data-ttu-id="4c73b-181">**安裝含遠端相依性的本機套件時，為什麼收到「無法解決相依性錯誤」？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-181">**Why do I get an "Unable to resolve dependency error" when installing a local package with remote dependencies?**</span></span>

<span data-ttu-id="4c73b-182">將本機套件安裝至專案時，您需要選取**所有**來源。</span><span class="sxs-lookup"><span data-stu-id="4c73b-182">You need to select the **All** source when installing a local package into the project.</span></span> <span data-ttu-id="4c73b-183">這會彙總所有摘要，而不是只使用一個。</span><span class="sxs-lookup"><span data-stu-id="4c73b-183">This aggregates all the feeds instead of using just one.</span></span> <span data-ttu-id="4c73b-184">出現此錯誤的原因是本機存放庫使用者經常會因公司原則而想要避免不小心安裝遠端套件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-184">The reason this error appears is that users of a local repository often want to avoid accidentally installing a remote package due to corporate polices.</span></span>

<span data-ttu-id="4c73b-185">**我在同一個資料夾中有多個專案，我該如何為每個專案使用不同的 packages.config 檔案？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-185">**I have multiple projects in the same folder, how can I use separate packages.config files for each project?**</span></span>

<span data-ttu-id="4c73b-186">在不同專案位於不同資料夾的大部分專案中，這在 NuGet 識別每個專案中的 `packages.config` 檔案時不是問題。</span><span class="sxs-lookup"><span data-stu-id="4c73b-186">In most projects where separate projects live in separate folders, this is not a problem as NuGet identifies the `packages.config` files in each project.</span></span> <span data-ttu-id="4c73b-187">相同的資料夾中有 NuGet 3.3+ 和多個專案時，您可以將專案名稱插入至使用模式 `packages.{project-name}.config` 的 `packages.config` 檔案名稱，而且 NuGet 會使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="4c73b-187">With NuGet 3.3+ and multiple projects in the same folder, you can insert the name of the project into the `packages.config` filenames use the pattern `packages.{project-name}.config`, and NuGet uses that file.</span></span>

<span data-ttu-id="4c73b-188">因為每個專案檔都包含它自己的相依性清單，所以使用 PackageReference 時，這不是問題。</span><span class="sxs-lookup"><span data-stu-id="4c73b-188">This is not an issue when using PackageReference, as each project file contains its own list of dependencies.</span></span>

<span data-ttu-id="4c73b-189">**我在存放庫清單中看不到 nuget.org，要如何取得它？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-189">**I don't see nuget.org in my list of repositories, how do I get it back?**</span></span>

- <span data-ttu-id="4c73b-190">將 `https://api.nuget.org/v3/index.json` 新增至來源清單，或者</span><span class="sxs-lookup"><span data-stu-id="4c73b-190">Add `https://api.nuget.org/v3/index.json` to your list of sources, or</span></span>
- <span data-ttu-id="4c73b-191">刪除 `%appdata%\.nuget\NuGet.Config` (Windows) 或 `~/.nuget/NuGet/NuGet.Config` (Mac/Linux)，讓 NuGet 重新加以建立。</span><span class="sxs-lookup"><span data-stu-id="4c73b-191">Delete `%appdata%\.nuget\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) and let NuGet re-create it.</span></span>

<span data-ttu-id="4c73b-192">**如果套件未提供特定授權資訊，則預設授權條款是什麼？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-192">**What are the default license terms if a package doesn't provide specific license information?**</span></span>

<span data-ttu-id="4c73b-193">每個套件都是受套件隨附的條款所控管。</span><span class="sxs-lookup"><span data-stu-id="4c73b-193">Each package is governed by the terms that are included with the package.</span></span> <span data-ttu-id="4c73b-194">您應該先檢閱適用的條款，再存取、下載或取得任何套件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-194">You should review the applicable terms before accessing, downloading, or acquiring any packages.</span></span> <span data-ttu-id="4c73b-195">在 nuget.org 上，使用套件頁面上的 [授權資訊] 連結。</span><span class="sxs-lookup"><span data-stu-id="4c73b-195">On nuget.org, use the **License Info** link on the package page.</span></span>

<span data-ttu-id="4c73b-196">如果套件未指定授權條款，請使用 nuget.org 套件頁面上的 [連絡擁有者] 連結直接連絡套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="4c73b-196">If a package does not specify the licensing terms, contact the package owner directly using the **Contact owners** link on the nuget.org package page.</span></span> <span data-ttu-id="4c73b-197">Microsoft 不會將任何智慧財產權從協力廠商套件提供者授權給您，而且不負責協力廠商所提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c73b-197">Microsoft does not license any intellectual property to you from third party package providers and is not responsible for information provided by third parties.</span></span>

## <a name="managing-packages-on-nugetorg"></a><span data-ttu-id="4c73b-198">在 nuget.org 上管理套件</span><span class="sxs-lookup"><span data-stu-id="4c73b-198">Managing packages on nuget.org</span></span>

<span data-ttu-id="4c73b-199">**我可以在上傳套件之後編輯套件中繼資料嗎？為什麼必須編輯 nuspec 及上傳新的套件才能變更套件中繼資料？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-199">**Can I edit package metadata after it's been uploaded? Why do you require editing the nuspec and uploading a new package for making changes to package metadata?**</span></span>

<span data-ttu-id="4c73b-200">NuGet 需要所有套件皆已簽署。</span><span class="sxs-lookup"><span data-stu-id="4c73b-200">NuGet requires all packages to be signed.</span></span> <span data-ttu-id="4c73b-201">套件簽署的設計原則是已簽署的套件內容必須是不可變的，其中包含 nuspec。</span><span class="sxs-lookup"><span data-stu-id="4c73b-201">A design principle of package signing is that signed package content must be immutable, which includes the nuspec.</span></span> <span data-ttu-id="4c73b-202">編輯套件中繼資料會導致 nuspec 變更，並讓現有簽章失效。</span><span class="sxs-lookup"><span data-stu-id="4c73b-202">Editing the package metadata results in changes to the nuspec, invalidating existing signatures.</span></span> <span data-ttu-id="4c73b-203">建議修改現有工作流程，使其不需要在建立套件之後編輯套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4c73b-203">We recommend modifying existing workflows to not require editing the package metadata after the package has been created.</span></span>

<span data-ttu-id="4c73b-204">請注意，會自動從您套件本身產生針對套件所列出的相依性，而且無法進行編輯。</span><span class="sxs-lookup"><span data-stu-id="4c73b-204">Note that dependencies listed for your package are generated automatically from the package itself and cannot be edited.</span></span>

<span data-ttu-id="4c73b-205">此外，將套件上傳至 [staging.nuget.org](http://staging.nuget.org) 是測試和驗證套件的不錯方式，而不需要將套件設為可在公用資源庫中使用。</span><span class="sxs-lookup"><span data-stu-id="4c73b-205">In addition, uploading packages to [staging.nuget.org](http://staging.nuget.org) is a great way to test and validate your package without making a package available in the public gallery.</span></span>

<span data-ttu-id="4c73b-206">**可以保留將在未來發行之套件的名稱嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-206">**Is it possible to reserve names for packages that will be published in future?**</span></span>

<span data-ttu-id="4c73b-207">可以。</span><span class="sxs-lookup"><span data-stu-id="4c73b-207">Yes.</span></span> <span data-ttu-id="4c73b-208">要求帳戶的套件識別碼前置詞，即可在 [nuget.org](https://www.nuget.org/) 上保留套件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4c73b-208">You can reserve IDs for packages on [nuget.org](https://www.nuget.org/) by requesting a package ID prefix for your account.</span></span> <span data-ttu-id="4c73b-209">若要要求套件識別碼首碼，請遵循[文件](https://docs.microsoft.com/nuget/reference/id-prefix-reservation)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4c73b-209">In order to request a package ID prefix, follow the instructions in the [documentation](https://docs.microsoft.com/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="4c73b-210">**如何宣告套件擁有權？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-210">**How do I claim ownership for packages ?**</span></span>

<span data-ttu-id="4c73b-211">請參閱[在 nuget.org 上管理套件擁有者](../create-packages/publish-a-package.md#managing-package-owners-on-nugetorg)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-211">See [Managing package owners on nuget.org](../create-packages/publish-a-package.md#managing-package-owners-on-nugetorg).</span></span>

<span data-ttu-id="4c73b-212">**如何處理違反我軟體授權的套件擁有者？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-212">**How do I deal with a package owner who is violating my software license?**</span></span>

<span data-ttu-id="4c73b-213">鼓勵 NuGet 社群合作，以解決套件擁有者與其他軟體擁有者之間可能發生的任何爭議。</span><span class="sxs-lookup"><span data-stu-id="4c73b-213">We encourage the NuGet community to work together to resolve any disputes that may arise between package owners and the owners of other software.</span></span> <span data-ttu-id="4c73b-214">我們已製作可在要求 nuget.org 管理員仲裁之前遵循的[爭議解決程序](../policies/dispute-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-214">We have crafted a [dispute resolution process](../policies/dispute-resolution.md) to follow before asking nuget.org administrators to intercede.</span></span>

<span data-ttu-id="4c73b-215">**建議將測試套件上傳至 nuget.org 嗎？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-215">**Is it recommended to upload my test packages to nuget.org?**</span></span>

<span data-ttu-id="4c73b-216">基於測試目的，您可以使用 [staging.nuget.org](http://staging.nuget.org) 或替代公用 NuGet 伺服器 (例如 [myget.org](https://myget.org) 或 [Visual Studio Team Services](https://blogs.msdn.microsoft.com/visualstudioalm/2015/08/27/announcing-package-management-support-for-vsotfs/))。</span><span class="sxs-lookup"><span data-stu-id="4c73b-216">For test purposes, you can use [staging.nuget.org](http://staging.nuget.org), or alternative public NuGet servers like [myget.org](https://myget.org) or [Visual Studio Team Services](https://blogs.msdn.microsoft.com/visualstudioalm/2015/08/27/announcing-package-management-support-for-vsotfs/).</span></span>

<span data-ttu-id="4c73b-217">請注意，可能不會保留上傳至 staging.nuget.org 的套件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-217">Note that packages uploaded to staging.nuget.org may not be preserved.</span></span> <span data-ttu-id="4c73b-218">請參閱 [Goodbye 預覽](http://blog.nuget.org/20130419/goodbye-preview.html)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-218">See [Goodbye preview](http://blog.nuget.org/20130419/goodbye-preview.html).</span></span>

<span data-ttu-id="4c73b-219">**我可以上傳至 nuget.org 的套件大小上限為何？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-219">**What is the maximum size of packages I can upload to nuget.org?**</span></span>

<span data-ttu-id="4c73b-220">nuget.org 允許最多 250MB 的套件，但建議盡可能保持 1MB 的套件，並使用相依性將套件連結在一起。</span><span class="sxs-lookup"><span data-stu-id="4c73b-220">nuget.org allows packages up to 250MB, but we recommend keeping packages under 1MB if possible and using dependencies to link packages together.</span></span> <span data-ttu-id="4c73b-221">根據經驗法則，套件只包含一個組件來避免發生衝突。</span><span class="sxs-lookup"><span data-stu-id="4c73b-221">As a rule of thumb, packages contain only one assembly to avoid collisions.</span></span>

<span data-ttu-id="4c73b-222">NuGet 使用 HTTP 來下載套件，因此較大的套件與較小的套件相較之下更有可能會讓安裝失敗。</span><span class="sxs-lookup"><span data-stu-id="4c73b-222">NuGet uses HTTP to download packages, so larger packages have a higher likelihood of failed installs than smaller ones.</span></span>

<span data-ttu-id="4c73b-223">可能會在多個套件之間共用相依性，讓 NuGet 套件取用者的總下載大小變小。</span><span class="sxs-lookup"><span data-stu-id="4c73b-223">It is possible to share dependencies between multiple packages, making the total download size for consumers of your NuGet packages smaller.</span></span>

<span data-ttu-id="4c73b-224">相依性大部分是靜態的，而且永遠不會變更。</span><span class="sxs-lookup"><span data-stu-id="4c73b-224">Dependencies are mostly static and never change.</span></span> <span data-ttu-id="4c73b-225">使用程式碼修正 Bug 時，可能不需要更新相依性。</span><span class="sxs-lookup"><span data-stu-id="4c73b-225">When fixing a bug in code, the dependencies may not need to be updated.</span></span> <span data-ttu-id="4c73b-226">如果您組合相依性，則每次最後都會得到較大的套件。</span><span class="sxs-lookup"><span data-stu-id="4c73b-226">If you bundle dependencies, you end up reshipping larger packages every time.</span></span> <span data-ttu-id="4c73b-227">將 NuGet 套件分割為相關相依性，以更精細地調整您套件取用者的升級。</span><span class="sxs-lookup"><span data-stu-id="4c73b-227">By splitting NuGet packages into related dependencies, upgrades are much more fine-grained for consumers of your package.</span></span>

## <a name="nugetorg-not-accessible"></a><span data-ttu-id="4c73b-228">無法存取 nuget.org</span><span class="sxs-lookup"><span data-stu-id="4c73b-228">nuget.org not accessible</span></span>

<span data-ttu-id="4c73b-229">**為何無法從 nuget.org 下載套件或將套件上傳至其中？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-229">**Why can't I download packages from or upload packages to nuget.org?**</span></span>

<span data-ttu-id="4c73b-230">首先，請確定您使用最新版的 NuGet。</span><span class="sxs-lookup"><span data-stu-id="4c73b-230">First, make sure you're using the latest versions of NuGet.</span></span> <span data-ttu-id="4c73b-231">如果該版本持續失敗，請[連絡支援人員](https://www.nuget.org/policies/Contact)，並提供其他連線疑難排解資訊，包含：</span><span class="sxs-lookup"><span data-stu-id="4c73b-231">If that version continues to fail, [contact support](https://www.nuget.org/policies/Contact) and provide additional connection troubleshooting information including:</span></span>

- <span data-ttu-id="4c73b-232">您所使用的 NuGet 版本</span><span class="sxs-lookup"><span data-stu-id="4c73b-232">The version of NuGet you're using</span></span>
- <span data-ttu-id="4c73b-233">您所使用的套件來源</span><span class="sxs-lookup"><span data-stu-id="4c73b-233">The package sources you're using</span></span>
- <span data-ttu-id="4c73b-234">含詳細之詳細資訊的還原記錄</span><span class="sxs-lookup"><span data-stu-id="4c73b-234">A restore log with detailed verbosity</span></span>
- <span data-ttu-id="4c73b-235">MTR 或 Fiddler 追蹤 (請參閱下面)</span><span class="sxs-lookup"><span data-stu-id="4c73b-235">MTR or a Fiddler traces (see below)</span></span>
- <span data-ttu-id="4c73b-236">您的地理區域</span><span class="sxs-lookup"><span data-stu-id="4c73b-236">Your geographical area</span></span>
- <span data-ttu-id="4c73b-237">作業系統版本</span><span class="sxs-lookup"><span data-stu-id="4c73b-237">Your operating system version</span></span>
- <span data-ttu-id="4c73b-238">電腦組態 (CPU、網路、硬碟機)</span><span class="sxs-lookup"><span data-stu-id="4c73b-238">Machine configuration (CPU, Network, hard drive)</span></span>
- <span data-ttu-id="4c73b-239">是否為受 Proxy 或防火牆保護的電腦</span><span class="sxs-lookup"><span data-stu-id="4c73b-239">Whether is your machine behind a proxy or firewall</span></span>
- <span data-ttu-id="4c73b-240">電腦上所安裝的 .NET 版本</span><span class="sxs-lookup"><span data-stu-id="4c73b-240">The versions of .NET that are installed on the machine</span></span>
- <span data-ttu-id="4c73b-241">您所使用的跨平台工具 (例如 .NET CLI 或 DNU) 版本</span><span class="sxs-lookup"><span data-stu-id="4c73b-241">Versions of cross-platform tools such as .NET CLI, or DNU that you're using</span></span>

<span data-ttu-id="4c73b-242">*擷取 MTR：*</span><span class="sxs-lookup"><span data-stu-id="4c73b-242">*To capture MTR:*</span></span>

- <span data-ttu-id="4c73b-243">從 [http://winmtr.net/download/](http://winmtr.net/) 下載 WinMTR</span><span class="sxs-lookup"><span data-stu-id="4c73b-243">Download WinMTR from [http://winmtr.net/download/](http://winmtr.net/)</span></span>
- <span data-ttu-id="4c73b-244">輸入 `api.nuget.org` 作為主機名稱，然後按一下 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="4c73b-244">Enter `api.nuget.org` as the hostname and click **Start**.</span></span>
- <span data-ttu-id="4c73b-245">等到 [已傳送] 資料行 >= 100。</span><span class="sxs-lookup"><span data-stu-id="4c73b-245">Wait until the **Sent** column is >= 100.</span></span>

    ![擷取 MTR](media/mtr.png)

- <span data-ttu-id="4c73b-247">將文字複製至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="4c73b-247">Copy text to clipboard.</span></span>

<span data-ttu-id="4c73b-248">*擷取 Fiddler：*</span><span class="sxs-lookup"><span data-stu-id="4c73b-248">*To capture Fiddler:*</span></span>

- <span data-ttu-id="4c73b-249">安裝最新版的 [Fiddler](http://www.telerik.com/download/fiddler)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-249">Install the latest version of [Fiddler](http://www.telerik.com/download/fiddler).</span></span>
- <span data-ttu-id="4c73b-250">啟動 Fiddler，並使用 [檔案] > [擷取流量] 功能表來停用擷取流量。</span><span class="sxs-lookup"><span data-stu-id="4c73b-250">Start Fiddler and disable capturing traffic using the **File > Capture Traffic** menu.</span></span>
- <span data-ttu-id="4c73b-251">移除所有工作階段 (選取清單中的所有項目，並按 **Delete** 鍵)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-251">Remove all sessions (select all items in the list, press the **Delete** key).</span></span>
- <span data-ttu-id="4c73b-252">設定 Fiddler 擷取 HTTPS 流量，方法是核取 [工具] > [Fiddler 選項] 功能表的 [HTTPS] 索引標籤中的 [Decrypt HTTPS traffic] (將 HTTPS 流量解密)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-252">Configure Fiddler to capture HTTPS traffic by checking **Decrypt HTTPS traffic** in the **HTTPS** tab of the **Tools > Fiddler Options...** menu.</span></span>
- <span data-ttu-id="4c73b-253">關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4c73b-253">Close Visual Studio.</span></span>
- <span data-ttu-id="4c73b-254">啟用 [檔案] > [擷取流量] 功能表。</span><span class="sxs-lookup"><span data-stu-id="4c73b-254">Enable the **File > Capture Traffic** menu.</span></span>
- <span data-ttu-id="4c73b-255">啟動 Visual Studio 或 nuget.exe，然後執行無法運作的動作。</span><span class="sxs-lookup"><span data-stu-id="4c73b-255">Start Visual Studio or nuget.exe .exe and perform the actions that are not working.</span></span> <span data-ttu-id="4c73b-256">這些動作所產生的流量應該會顯示在 Fiddler 中。</span><span class="sxs-lookup"><span data-stu-id="4c73b-256">The traffic generated by these actions should show up in Fiddler.</span></span>
- <span data-ttu-id="4c73b-257">執行動作之後，請使用 [檔案] > [儲存] > [所有工作階段] 來儲存所擷取的工作階段。</span><span class="sxs-lookup"><span data-stu-id="4c73b-257">Once the actions have run, use **File > Save > All Sessions** to store the captured sessions.</span></span>

<span data-ttu-id="4c73b-258">注意：可能必須將 `HTTP_PROXY` 環境變數設定為 `http://127.0.0.1:8888`，以透過 Fiddler 路由傳送 NuGet 流量。</span><span class="sxs-lookup"><span data-stu-id="4c73b-258">Note: it may be required to set the `HTTP_PROXY` environment variable to `http://127.0.0.1:8888` for routing NuGet traffic through Fiddler.</span></span>

<span data-ttu-id="4c73b-259">如果該作業失敗，請嘗試[這篇 StackOverflow 文章所提及的祕訣](http://stackoverflow.com/questions/21049908/using-fiddler-to-sniff-visual-studio-2013-requests-proxy-firewall)。</span><span class="sxs-lookup"><span data-stu-id="4c73b-259">If that fails, try the [tips mentioned in this StackOverflow post](http://stackoverflow.com/questions/21049908/using-fiddler-to-sniff-visual-studio-2013-requests-proxy-firewall).</span></span>

<span data-ttu-id="4c73b-260">**nuget.org 的 API 端點為何？**</span><span class="sxs-lookup"><span data-stu-id="4c73b-260">**What are the API endpoints for nuget.org?**</span></span>

<span data-ttu-id="4c73b-261">V3：`https://api.nuget.org/v3/index.json` V2：`https://www.nuget.org/api/v2/` (請注意，V2 API 已被取代，無法與 NuGet 4+ 搭配使用。)</span><span class="sxs-lookup"><span data-stu-id="4c73b-261">V3: `https://api.nuget.org/v3/index.json` V2: `https://www.nuget.org/api/v2/` (Note that the V2 API is deprecated and does not work with NuGet 4+.)</span></span>