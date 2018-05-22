---
title: 使用 Visual Studio 建立及發佈 .NET Standard NuGet 套件的入門指南
description: 使用 Visual Studio 2017 建立及發佈 .NET Standard NuGet 套件的逐步解說教學課程。
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 03/18/2018
ms.topic: quickstart
ms.openlocfilehash: c5d58aa6312eae801607ca44a81bc092a7a7c15f
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="quickstart-create-and-publish-a-nuget-package-using-visual-studio-net-standard"></a><span data-ttu-id="0de71-103">快速入門：使用 Visual Studio 建立及發佈 NuGet 套件 (.NET Standard)</span><span class="sxs-lookup"><span data-stu-id="0de71-103">Quickstart: Create and publish a NuGet package using Visual Studio (.NET Standard)</span></span>

<span data-ttu-id="0de71-104">只要使用 CLI 工具，就能輕鬆從 Visual Studio 中的 .NET Standard 類別庫建立 NuGet 套件，然後將其發佈到 nuget.org。</span><span class="sxs-lookup"><span data-stu-id="0de71-104">It's a simple process to create a NuGet package from a .NET Standard Class Library in Visual Studio, and then publish it to nuget.org using a CLI tool.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0de71-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="0de71-105">Prerequisites</span></span>

1. <span data-ttu-id="0de71-106">使用任何 .NET 相關的工作負載，從 [visualstudio.com](https://www.visualstudio.com/) 安裝任何版本的 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="0de71-106">Install any edition of Visual Studio 2017 from [visualstudio.com](https://www.visualstudio.com/) with any .NET-related workload.</span></span> <span data-ttu-id="0de71-107">Visual Studio 2017 會在安裝 .NET 工作負載時，自動包含 NuGet 功能。</span><span class="sxs-lookup"><span data-stu-id="0de71-107">Visual Studio 2017 automatically includes NuGet capabilities when a .NET workload is installed.</span></span>

1. <span data-ttu-id="0de71-108">安裝 `nuget.exe` CLI，作法是從 [nuget.org](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) 下載它、將該 `.exe` 檔案儲存至適當的資料夾，然後將該資料夾新增至您的 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="0de71-108">Install the `nuget.exe` CLI by downloading it from [nuget.org](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe), saving that `.exe` file to a suitable folder, and adding that folder to your PATH environment variable.</span></span>

    <span data-ttu-id="0de71-109">或者，如果您已安裝 [.NET Core SDK](https://www.microsoft.com/net/download/)，就可以使用 `dotnet` CLI。</span><span class="sxs-lookup"><span data-stu-id="0de71-109">Alternately, if you have the [.NET Core SDK](https://www.microsoft.com/net/download/) installed, you can use the `dotnet` CLI.</span></span>

1. <span data-ttu-id="0de71-110">如果您還沒有帳戶，請[在 nuget.org 上註冊一個免費帳戶](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="0de71-110">[Register for a free account on nuget.org](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) if you don't have one already.</span></span> <span data-ttu-id="0de71-111">建立新的帳戶會傳送一封確認電子郵件。</span><span class="sxs-lookup"><span data-stu-id="0de71-111">Creating a new account sends a confirmation email.</span></span> <span data-ttu-id="0de71-112">您必須確認帳戶，才可以上傳套件。</span><span class="sxs-lookup"><span data-stu-id="0de71-112">You must confirm the account before you can upload a package.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="0de71-113">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="0de71-113">Create a class library project</span></span>

<span data-ttu-id="0de71-114">您可以針對要封裝的程式碼使用現有的 .NET Standard 類別庫專案，或建立一個簡單的專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0de71-114">You can use an existing .NET Standard Class Library project for the code you want to package, or create a simple one as follows:</span></span>

1. <span data-ttu-id="0de71-115">在 Visual Studio 中，選擇 [檔案] > [新增] > [專案]、展開 [Visual C#] > [.NET Standard] 節點、選取 [類別庫 (.NET Standard)] 範本、將專案命名為 AppLogger，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0de71-115">In Visual Studio, choose **File > New > Project**, expand the **Visual C# > .NET Standard** node, select the "Class Library (.NET Standard)" template, name the project AppLogger, and click **OK**.</span></span>

1. <span data-ttu-id="0de71-116">在產生的專案檔上按一下滑鼠右鍵，然後選取 [建置] 以確定已適當建立專案。</span><span class="sxs-lookup"><span data-stu-id="0de71-116">Right-click on the resulting project file and select **Build** to make sure the project was created properly.</span></span> <span data-ttu-id="0de71-117">DLL 位於 Debug 資料夾 (如果您改為建置該組態則為 Release)。</span><span class="sxs-lookup"><span data-stu-id="0de71-117">The DLL is found within the Debug folder (or Release if you build that configuration instead).</span></span>

<span data-ttu-id="0de71-118">當然，在真實的 NuGet 套件中，您會實作其他人可以用來建置應用程式的許多實用功能。</span><span class="sxs-lookup"><span data-stu-id="0de71-118">Within a real NuGet package, of course, you implement many useful features with which others can build applications.</span></span> <span data-ttu-id="0de71-119">不過，對於此逐步解說，您將不會撰寫任何額外的程式碼，因為來自範本的類別庫已足夠建立套件。</span><span class="sxs-lookup"><span data-stu-id="0de71-119">For this walkthrough, however, you won't write any additional code because a class library from the template is sufficient to create a package.</span></span> <span data-ttu-id="0de71-120">不過，如果您想要為套件新增一些函式程式碼，可以使用下列方式：</span><span class="sxs-lookup"><span data-stu-id="0de71-120">Still, if you'd like some functional code for the package, use the following:</span></span>

```cs
namespace AppLogger
{
    public class Logger
    {
        public void Log(string text)
        {
            Console.WriteLine(text);
        }
    }
}
```

> [!Tip]
> <span data-ttu-id="0de71-121">除非您有理由選擇，否則 .NET Standard 是 NuGet 套件的慣用目標，因為它能與範圍最廣泛的取用專案相容。</span><span class="sxs-lookup"><span data-stu-id="0de71-121">Unless you have a reason to choose otherwise, .NET Standard is the preferred target for NuGet packages, as it provides compatibility with the widest range of consuming projects.</span></span>

## <a name="configure-package-properties"></a><span data-ttu-id="0de71-122">設定套件屬性</span><span class="sxs-lookup"><span data-stu-id="0de71-122">Configure package properties</span></span>

1. <span data-ttu-id="0de71-123">選取 [專案] > [屬性] 功能表命令，然後選取 [套件] 索引標籤。([套件] 索引標籤只會出現於 .NET Standard 類別庫專案；如果您的目標是 .NET Framework，請參閱[建立及發佈 .NET Framework 套件](create-and-publish-a-package-using-visual-studio-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="0de71-123">Select the **Project > Properties** menu command, then select the **Package** tab. (The **Package** tab appears only for .NET Standard class library projects; if you are targeting .NET Framework, see [Create and publish a .NET Framework package](create-and-publish-a-package-using-visual-studio-net-framework.md) instead.</span></span> <span data-ttu-id="0de71-124">如果未出現在 .NET Standard 專案中，您可能需要將 Visual Studio 2017 更新至最新版本。)</span><span class="sxs-lookup"><span data-stu-id="0de71-124">If it doesn't appear for a .NET Standard project, you may need to update Visual Studio 2017 to the latest release.)</span></span>

    ![Visual Studio 專案中的 NuGet 套件屬性](media/qs_create-vs-01-package-properties.png)

    > [!Note]
    > <span data-ttu-id="0de71-126">針對公眾取用而建置的套件，請特別注意 **Tags** 屬性，因為標籤可協助其他人找到您的套件，並了解其用途。</span><span class="sxs-lookup"><span data-stu-id="0de71-126">For packages built for public consumption, pay special attention to the **Tags** property, as tags help others find your package and understand what it does.</span></span>

1. <span data-ttu-id="0de71-127">為套件指定唯一識別碼，並填入任何其他所需的屬性。</span><span class="sxs-lookup"><span data-stu-id="0de71-127">Give your package a unique identifier and fill out any other desired properties.</span></span> <span data-ttu-id="0de71-128">如需不同屬性的說明，請參閱 [.nuspec 檔案參考](../reference/nuspec.md)。</span><span class="sxs-lookup"><span data-stu-id="0de71-128">For a description of the different properties, see [.nuspec file reference](../reference/nuspec.md).</span></span> <span data-ttu-id="0de71-129">此處的所有屬性都會移入 Visual Studio 針對專案建立的 `.nuspec` 資訊清單。</span><span class="sxs-lookup"><span data-stu-id="0de71-129">All of the properties here go into the `.nuspec` manifest that Visual Studio creates for the project.</span></span>

    > [!Important]
    > <span data-ttu-id="0de71-130">您必須為套件指定識別碼，此識別碼在 nuget.org 上或您使用的任何主機上都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0de71-130">You must give the package an identifier that's unique across nuget.org or whatever host you're using.</span></span> <span data-ttu-id="0de71-131">針對此逐步解說，我們建議在名稱中包含 "Sample" 或 "Test" (如同稍後發行步驟所做的)，讓套件能夠成為公開可見的 (儘管實際上不太可能會有人使用它)。</span><span class="sxs-lookup"><span data-stu-id="0de71-131">For this walkthrough we recommend including "Sample" or "Test" in the name as the later publishing step does make the package publicly visible (though it's unlikely anyone will actually use it).</span></span>
    >
    > <span data-ttu-id="0de71-132">如果您嘗試發行名稱已經存在的套件，則會看到錯誤。</span><span class="sxs-lookup"><span data-stu-id="0de71-132">If you attempt to publish a package with a name that already exists, you see an error.</span></span>

1. <span data-ttu-id="0de71-133">選擇性：若要直接查看專案檔中的屬性，請以滑鼠右鍵按一下 [方案總管] 中的專案，並選取 [編輯 AppLogger.csproj]。</span><span class="sxs-lookup"><span data-stu-id="0de71-133">Optional: to see the properties directly in the project file, right-click the project in Solution Explorer and select **Edit AppLogger.csproj**.</span></span>

## <a name="run-the-pack-command"></a><span data-ttu-id="0de71-134">執行 pack 命令</span><span class="sxs-lookup"><span data-stu-id="0de71-134">Run the pack command</span></span>

1. <span data-ttu-id="0de71-135">設定要**發行**的組態。</span><span class="sxs-lookup"><span data-stu-id="0de71-135">Set the configuration to **Release**.</span></span>

1. <span data-ttu-id="0de71-136">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [封裝] 命令：</span><span class="sxs-lookup"><span data-stu-id="0de71-136">Right click the project in **Solution Explorer** and select the **Pack** command:</span></span>

    ![Visual Studio 專案捷徑功能表上的 NuGet 封裝命令](media/qs_create-vs-02-pack-command.png)

1. <span data-ttu-id="0de71-138">Visual Studio 會建置專案並建立 `.nupkg` 檔案。</span><span class="sxs-lookup"><span data-stu-id="0de71-138">Visual Studio builds the project and creates the `.nupkg` file.</span></span> <span data-ttu-id="0de71-139">檢查 [輸出] 視窗以取得詳細資料 (如下所示)，其中包含套件檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0de71-139">Examine the **Output** window for details (similar to the following), which contains the path to the package file.</span></span> <span data-ttu-id="0de71-140">另請注意，建置的組建是位於 `bin\Release\netstandard2.0`，以適用 .NET Standard 2.0 目標。</span><span class="sxs-lookup"><span data-stu-id="0de71-140">Note also that the built assembly is in `bin\Release\netstandard2.0` as befits the .NET Standard 2.0 target.</span></span>

    ```output
    1>------ Build started: Project: AppLogger, Configuration: Release Any CPU ------
    1>AppLogger -> d:\proj\AppLogger\AppLogger\bin\Release\netstandard2.0\AppLogger.dll
    1>Successfully created package 'd:\proj\AppLogger\AppLogger\bin\Release\AppLogger.1.0.0.nupkg'.
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

### <a name="alternate-option-pack-with-msbuild"></a><span data-ttu-id="0de71-141">替代選項：使用 MSBuild 封裝</span><span class="sxs-lookup"><span data-stu-id="0de71-141">Alternate option: pack with MSBuild</span></span>

<span data-ttu-id="0de71-142">當專案包含必要的套件資料時，NuGet 4.x+ 和 MSBuild 15.1+ 可支援 `pack` 目標，而這是使用 [封裝] 功能表命令的另一種替代方法。</span><span class="sxs-lookup"><span data-stu-id="0de71-142">As an alternate to using the **Pack** menu command, NuGet 4.x+ and MSBuild 15.1+ supports a `pack` target when the project contains the necessary package data.</span></span> <span data-ttu-id="0de71-143">請開啟命令提示字元，巡覽至專案資料夾並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0de71-143">Open a command prompt, navigate to your project folder and run the following command.</span></span> <span data-ttu-id="0de71-144">(若從 [開始] 功能表啟動 [適用於 Visual Studio 的開發人員命令提示字元]，其中就會設定好 MSBuild 的所有必要路徑，因此這是建議的做法。)</span><span class="sxs-lookup"><span data-stu-id="0de71-144">(You typically want to start the "Developer Command Prompt for Visual Studio" from the Start menu, as it will be configured with all the necessary paths for MSBuild.)</span></span>

```cli
msbuild /t:pack /p:Configuration=Release
```

<span data-ttu-id="0de71-145">接著可在 `bin\Release` 資料夾中找到套件。</span><span class="sxs-lookup"><span data-stu-id="0de71-145">The package can then be found in the `bin\Release` folder.</span></span>

<span data-ttu-id="0de71-146">如需 `msbuild /t:pack` 的其他選項，請參閱 [NuGet 套件和還原為 MSBuild 目標](../reference/msbuild-targets.md#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="0de71-146">For additional options with `msbuild /t:pack`, see [NuGet pack and restore as MSBuild targets](../reference/msbuild-targets.md#pack-target).</span></span>

## <a name="publish-the-package"></a><span data-ttu-id="0de71-147">發行套件</span><span class="sxs-lookup"><span data-stu-id="0de71-147">Publish the package</span></span>

<span data-ttu-id="0de71-148">一旦擁有 `.nupkg` 檔案之後，您會使用 `nuget.exe` CLI 或 `dotnet.exe` CLI 以及從 nuget.org 取得的 API 金鑰，將它發行到 nuget.org。</span><span class="sxs-lookup"><span data-stu-id="0de71-148">Once you have a `.nupkg` file, you publish it to nuget.org using either the `nuget.exe` CLI or the `dotnet.exe` CLI along with an API key acquired from nuget.org.</span></span>

[!INCLUDE [publish-notes](includes/publish-notes.md)]

### <a name="acquire-your-api-key"></a><span data-ttu-id="0de71-149">取得 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="0de71-149">Acquire your API key</span></span>

[!INCLUDE [publish-api-key](includes/publish-api-key.md)]

### <a name="publish-with-nuget-push"></a><span data-ttu-id="0de71-150">使用 nuget push 發行</span><span class="sxs-lookup"><span data-stu-id="0de71-150">Publish with nuget push</span></span>

<span data-ttu-id="0de71-151">這個步驟是使用 `dotnet.exe` 的替代方案。</span><span class="sxs-lookup"><span data-stu-id="0de71-151">This step is an alternative to using `dotnet.exe`.</span></span>

1. <span data-ttu-id="0de71-152">變更為包含 `.nupkg` 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0de71-152">Change to the folder containing the `.nupkg` file.</span></span>

1. <span data-ttu-id="0de71-153">執行下列命令，指定套件名稱並使用您的 API 金鑰來取代金鑰值：</span><span class="sxs-lookup"><span data-stu-id="0de71-153">Run the following command, specifying your package name and replacing the key value with your API key:</span></span>

    ```cli
    nuget push AppLogger.1.0.0.nupkg qz2jga8pl3dvn2akksyquwcs9ygggg4exypy3bhxy6w6x6 -Source https://api.nuget.org/v3/index.json
    ```

1. <span data-ttu-id="0de71-154">nuget.exe 顯示發行程序的結果：</span><span class="sxs-lookup"><span data-stu-id="0de71-154">nuget.exe displays the results of the publishing process:</span></span>

    ```output
    Pushing AppLogger.1.0.0.nupkg to 'https://www.nuget.org/api/v2/package'...
        PUT https://www.nuget.org/api/v2/package/
        Created https://www.nuget.org/api/v2/package/ 6829ms
    Your package was pushed.
    ```

<span data-ttu-id="0de71-155">請參閱 [nuget push](../tools/cli-ref-push.md)。</span><span class="sxs-lookup"><span data-stu-id="0de71-155">See [nuget push](../tools/cli-ref-push.md).</span></span>

### <a name="publish-with-dotnet-nuget-push"></a><span data-ttu-id="0de71-156">使用 dotnet nuget push 發行</span><span class="sxs-lookup"><span data-stu-id="0de71-156">Publish with dotnet nuget push</span></span>

<span data-ttu-id="0de71-157">這個步驟是使用 `nuget.exe` 的替代方案。</span><span class="sxs-lookup"><span data-stu-id="0de71-157">This step is an alternative to using `nuget.exe`.</span></span>

[!INCLUDE [publish-dotnet](includes/publish-dotnet.md)]

### <a name="publish-errors"></a><span data-ttu-id="0de71-158">發行錯誤</span><span class="sxs-lookup"><span data-stu-id="0de71-158">Publish errors</span></span>

[!INCLUDE [publish-errors](includes/publish-errors.md)]

### <a name="manage-the-published-package"></a><span data-ttu-id="0de71-159">管理已發行的套件</span><span class="sxs-lookup"><span data-stu-id="0de71-159">Manage the published package</span></span>

[!INCLUDE [publish-manage](includes/publish-manage.md)]

## <a name="related-topics"></a><span data-ttu-id="0de71-160">相關主題</span><span class="sxs-lookup"><span data-stu-id="0de71-160">Related topics</span></span>

- [<span data-ttu-id="0de71-161">建立套件</span><span class="sxs-lookup"><span data-stu-id="0de71-161">Create a Package</span></span>](../create-packages/creating-a-package.md)
- [<span data-ttu-id="0de71-162">套件</span><span class="sxs-lookup"><span data-stu-id="0de71-162">Publish a Package</span></span>](../create-packages/publish-a-package.md)
- [<span data-ttu-id="0de71-163">發行前套件</span><span class="sxs-lookup"><span data-stu-id="0de71-163">Pre-release Packages</span></span>](../create-packages/Prerelease-Packages.md)
- [<span data-ttu-id="0de71-164">支援多個目標架構</span><span class="sxs-lookup"><span data-stu-id="0de71-164">Support multiple target frameworks</span></span>](../create-packages/supporting-multiple-target-frameworks.md)
- [<span data-ttu-id="0de71-165">套件版本控制</span><span class="sxs-lookup"><span data-stu-id="0de71-165">Package versioning</span></span>](../reference/package-versioning.md)
- [<span data-ttu-id="0de71-166">建立當地語系化的套件</span><span class="sxs-lookup"><span data-stu-id="0de71-166">Creating localized packages</span></span>](../create-packages/creating-localized-packages.md)
- [<span data-ttu-id="0de71-167">.NET Standard 程式庫文件</span><span class="sxs-lookup"><span data-stu-id="0de71-167">.NET Standard Library documentation</span></span>](/dotnet/articles/standard/library)
- [<span data-ttu-id="0de71-168">從 .NET Framework 移轉到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="0de71-168">Porting to .NET Core from .NET Framework</span></span>](/dotnet/articles/core/porting/index)