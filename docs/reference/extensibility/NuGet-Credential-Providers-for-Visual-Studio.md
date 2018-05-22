---
title: Visual Studio 的 NuGet 認證提供者
description: NuGet 的認證提供者會向 IVsCredentialProvider 介面實作中的 Visual Studio 擴充功能的摘要。
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/09/2017
ms.topic: conceptual
ms.openlocfilehash: 740df87b0d663aac482d888e916662528ce27030
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="authenticating-feeds-in-visual-studio-with-nuget-credential-providers"></a><span data-ttu-id="91147-103">驗證 Visual Studio 中搭配 NuGet 認證提供者使用的摘要</span><span class="sxs-lookup"><span data-stu-id="91147-103">Authenticating feeds in Visual Studio with NuGet credential providers</span></span>

<span data-ttu-id="91147-104">NuGet Visual Studio 擴充功能 3.6 + 支援認證提供者，可讓已驗證的摘要所使用的 NuGet。</span><span class="sxs-lookup"><span data-stu-id="91147-104">The NuGet Visual Studio Extension 3.6+ supports credential providers, which enable NuGet to work with authenticated feeds.</span></span>
<span data-ttu-id="91147-105">安裝 Visual Studio 的 NuGet 認證提供者之後，Visual Studio 擴充功能會自動取得，並重新整理的已驗證的摘要，視需要的認證。</span><span class="sxs-lookup"><span data-stu-id="91147-105">After you install a NuGet credential provider for Visual Studio, the NuGet Visual Studio extension will automatically acquire and refresh credentials for authenticated feeds as necessary.</span></span>

<span data-ttu-id="91147-106">中可以找到範例實作[VsCredentialProvider 範例](https://github.com/NuGet/Samples/tree/master/VsCredentialProvider)。</span><span class="sxs-lookup"><span data-stu-id="91147-106">A sample implementation can be found in [the VsCredentialProvider sample](https://github.com/NuGet/Samples/tree/master/VsCredentialProvider).</span></span>

> [!Note]
> <span data-ttu-id="91147-107">Visual Studio 的 NuGet 認證提供者必須安裝成一般的 Visual Studio 擴充功能，而且需要[Visual Studio 2017](https://aka.ms/vs/15/preview/vs_enterprise) （目前處於預覽階段） 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="91147-107">NuGet credential providers for Visual Studio must be installed as a regular Visual Studio extension and will require [Visual Studio 2017](https://aka.ms/vs/15/preview/vs_enterprise) (currently in preview) or above.</span></span>
>
> <span data-ttu-id="91147-108">Visual Studio 的 NuGet 認證提供者僅適用於 Visual Studio （不在 dotnet 還原或 nuget.exe）。</span><span class="sxs-lookup"><span data-stu-id="91147-108">NuGet credential providers for Visual Studio work only in Visual Studio (not in dotnet restore or nuget.exe).</span></span> <span data-ttu-id="91147-109">對於與 nuget.exe 的認證提供者，請參閱[nuget.exe 認證提供者](nuget-exe-Credential-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="91147-109">For credential providers with nuget.exe, see [nuget.exe Credential Providers](nuget-exe-Credential-providers.md).</span></span>

## <a name="available-nuget-credential-providers-for-visual-studio"></a><span data-ttu-id="91147-110">使用 Visual Studio 的 NuGet 認證提供者</span><span class="sxs-lookup"><span data-stu-id="91147-110">Available NuGet credential providers for Visual Studio</span></span>

<span data-ttu-id="91147-111">沒有認證提供者內建於 Visual Studio 的 NuGet 延伸模組來支援 Visual Studio Team Services。</span><span class="sxs-lookup"><span data-stu-id="91147-111">There is a credential provider built into the Visual Studio NuGet extension to support Visual Studio Team Services.</span></span>

<span data-ttu-id="91147-112">NuGet Visual Studio 擴充功能會使用內部`VsCredentialProviderImporter`這也會掃描外掛程式的認證提供者。</span><span class="sxs-lookup"><span data-stu-id="91147-112">The NuGet Visual Studio Extension uses an internal `VsCredentialProviderImporter` which also scans for plug-in credential providers.</span></span> <span data-ttu-id="91147-113">這些外掛程式的認證提供者必須是做為 MEF 匯出類型的可探索`IVsCredentialProvider`。</span><span class="sxs-lookup"><span data-stu-id="91147-113">These plug-in credential providers must be discoverable as a MEF Export of type `IVsCredentialProvider`.</span></span>

<span data-ttu-id="91147-114">可用的外掛程式認證提供者包括：</span><span class="sxs-lookup"><span data-stu-id="91147-114">Available plug-in credential providers include:</span></span>

- [<span data-ttu-id="91147-115">MyGet Credential Provider for Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="91147-115">MyGet Credential Provider for Visual Studio 2017</span></span>](http://docs.myget.org/docs/reference/credential-provider-for-visual-studio)

## <a name="creating-a-nuget-credential-provider-for-visual-studio"></a><span data-ttu-id="91147-116">建立 Visual Studio 的 NuGet 認證提供者</span><span class="sxs-lookup"><span data-stu-id="91147-116">Creating a NuGet credential provider for Visual Studio</span></span>

<span data-ttu-id="91147-117">NuGet Visual Studio 擴充功能 3.6 + 會實作內部 CredentialService 用來取得認證。</span><span class="sxs-lookup"><span data-stu-id="91147-117">The NuGet Visual Studio Extension 3.6+ implements an internal CredentialService that is used to acquire credentials.</span></span> <span data-ttu-id="91147-118">CredentialService 具有內建和外掛程式的認證提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="91147-118">The CredentialService has a list of built-in and plug-in credential providers.</span></span> <span data-ttu-id="91147-119">每個提供者會嘗試依序直到取得認證。</span><span class="sxs-lookup"><span data-stu-id="91147-119">Each provider is tried sequentially until credentials are acquired.</span></span>

<span data-ttu-id="91147-120">認證擷取期間認證服務會嘗試依下列順序，停止只要取得認證的認證提供者：</span><span class="sxs-lookup"><span data-stu-id="91147-120">During credential acquisition, the credential service will try credential providers in the following order, stopping as soon as credentials are acquired:</span></span>

1. <span data-ttu-id="91147-121">認證將會提取從 NuGet 組態檔 (使用內建`SettingsCredentialProvider`)。</span><span class="sxs-lookup"><span data-stu-id="91147-121">Credentials will be fetched from NuGet configuration files (using the built-in `SettingsCredentialProvider`).</span></span>
1. <span data-ttu-id="91147-122">如果套件來源位於 Visual Studio Team Services，`VisualStudioAccountProvider`將使用。</span><span class="sxs-lookup"><span data-stu-id="91147-122">If the package source is on Visual Studio Team Services, the `VisualStudioAccountProvider` will be used.</span></span>
1. <span data-ttu-id="91147-123">所有其他外掛程式的認證提供者會嘗試依序。</span><span class="sxs-lookup"><span data-stu-id="91147-123">All other plug-in credential providers will be tried sequentially.</span></span>
1. <span data-ttu-id="91147-124">如果已取得不含認證的資訊，將會提示使用者輸入認證，使用標準的基本驗證 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="91147-124">If no credentials have been acquired yet, the user will be prompted for credentials using a standard basic authentication dialog.</span></span>

### <a name="implementing-ivscredentialprovidergetcredentialsasync"></a><span data-ttu-id="91147-125">實作 IVsCredentialProvider.GetCredentialsAsync</span><span class="sxs-lookup"><span data-stu-id="91147-125">Implementing IVsCredentialProvider.GetCredentialsAsync</span></span>

<span data-ttu-id="91147-126">若要建立 Visual Studio 的 NuGet 認證提供者，建立 Visual Studio 擴充功能會公開公用 MEF 匯出實作`IVsCredentialProvider`輸入，並遵守如下所述的原則。</span><span class="sxs-lookup"><span data-stu-id="91147-126">To create a NuGet credential provider for Visual Studio, create a Visual Studio Extension that exposes a public MEF Export implementing the `IVsCredentialProvider` type, and adheres to the principles outlined below.</span></span>

```cs
public interface IVsCredentialProvider
{
    Task<ICredentials> GetCredentialsAsync(
        Uri uri,
        IWebProxy proxy,
        bool isProxyRequest,
        bool isRetry,
        bool nonInteractive,
        CancellationToken cancellationToken);
}
```

<span data-ttu-id="91147-127">中可以找到範例實作[VsCredentialProvider 範例](https://github.com/NuGet/Samples/tree/master/VsCredentialProvider)。</span><span class="sxs-lookup"><span data-stu-id="91147-127">A sample implementation can be found in [the VsCredentialProvider sample](https://github.com/NuGet/Samples/tree/master/VsCredentialProvider).</span></span>

<span data-ttu-id="91147-128">Visual Studio 的每個 NuGet 認證提供者必須：</span><span class="sxs-lookup"><span data-stu-id="91147-128">Each NuGet credential provider for Visual Studio must:</span></span>

1. <span data-ttu-id="91147-129">判斷是否它可以提供認證的目標 URI 初始化認證擷取之前。</span><span class="sxs-lookup"><span data-stu-id="91147-129">Determine whether it can provide credentials for the targeted URI before initiating credential acquisition.</span></span> <span data-ttu-id="91147-130">如果提供者無法提供認證做為目標的來源，則應該傳回`null`。</span><span class="sxs-lookup"><span data-stu-id="91147-130">If the provider cannot supply credentials for the targeted source, then it should return `null`.</span></span>
1. <span data-ttu-id="91147-131">如果提供者無法處理要求的目標 URI，但無法提供認證，就應該擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91147-131">If the provider does handle requests for the targeted URI, but cannot supply credentials, an exception should be thrown.</span></span>

<span data-ttu-id="91147-132">Visual Studio 的自訂 NuGet 認證提供者必須實作`IVsCredentialProvider`中提供的介面[NuGet.VisualStudio 封裝](https://www.nuget.org/packages/NuGet.VisualStudio/)。</span><span class="sxs-lookup"><span data-stu-id="91147-132">A custom NuGet credential provider for Visual Studio must implement the `IVsCredentialProvider` interface available in the [NuGet.VisualStudio package](https://www.nuget.org/packages/NuGet.VisualStudio/).</span></span>

#### <a name="getcredentialasync"></a><span data-ttu-id="91147-133">GetCredentialAsync</span><span class="sxs-lookup"><span data-stu-id="91147-133">GetCredentialAsync</span></span>

| <span data-ttu-id="91147-134">輸入的參數</span><span class="sxs-lookup"><span data-stu-id="91147-134">Input Parameter</span></span> |<span data-ttu-id="91147-135">描述</span><span class="sxs-lookup"><span data-stu-id="91147-135">Description</span></span>|
| ----------------|-----------|
| <span data-ttu-id="91147-136">Uri 的 uri</span><span class="sxs-lookup"><span data-stu-id="91147-136">Uri uri</span></span> | <span data-ttu-id="91147-137">封裝來源 Uri 要求認證。</span><span class="sxs-lookup"><span data-stu-id="91147-137">The package source Uri for which credentials are being requested.</span></span>|
| <span data-ttu-id="91147-138">IWebProxy proxy</span><span class="sxs-lookup"><span data-stu-id="91147-138">IWebProxy proxy</span></span> | <span data-ttu-id="91147-139">若要在網路上通訊時使用的 web proxy。</span><span class="sxs-lookup"><span data-stu-id="91147-139">Web proxy to use when communicating on the network.</span></span> <span data-ttu-id="91147-140">如果不沒有設定任何 proxy 驗證，則為 null。</span><span class="sxs-lookup"><span data-stu-id="91147-140">Null if there is no proxy authentication configured.</span></span> |
| <span data-ttu-id="91147-141">bool isProxyRequest</span><span class="sxs-lookup"><span data-stu-id="91147-141">bool isProxyRequest</span></span> | <span data-ttu-id="91147-142">如果這個要求是以取得 proxy 驗證認證，則為 true。</span><span class="sxs-lookup"><span data-stu-id="91147-142">True if this request is to get proxy authentication credentials.</span></span> <span data-ttu-id="91147-143">如果實作取得 proxy 認證無效，應該會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="91147-143">If the implementation is not valid for acquiring proxy credentials, then null should be returned.</span></span> |
| <span data-ttu-id="91147-144">bool isRetry</span><span class="sxs-lookup"><span data-stu-id="91147-144">bool isRetry</span></span> | <span data-ttu-id="91147-145">如果這個 uri，先前要求的認證，但提供的認證不允許存取的權限，則為 true。</span><span class="sxs-lookup"><span data-stu-id="91147-145">True if credentials were previously requested for this Uri, but the supplied credentials did not allow authorized access.</span></span> |
| <span data-ttu-id="91147-146">非互動式 bool</span><span class="sxs-lookup"><span data-stu-id="91147-146">bool nonInteractive</span></span> | <span data-ttu-id="91147-147">如果為 true，則認證提供者必須抑制所有使用者提示，並改為使用預設值。</span><span class="sxs-lookup"><span data-stu-id="91147-147">If true, the credential provider must suppress all user prompts and use default values instead.</span></span> |
| <span data-ttu-id="91147-148">CancellationToken cancellationToken</span><span class="sxs-lookup"><span data-stu-id="91147-148">CancellationToken cancellationToken</span></span> | <span data-ttu-id="91147-149">這個取消語彙基元應該檢查以判斷作業要求認證已被取消。</span><span class="sxs-lookup"><span data-stu-id="91147-149">This cancellation token should be checked to determine if the operation requesting credentials has been cancelled.</span></span> |

<span data-ttu-id="91147-150">**傳回值**： 認證物件實作[`System.Net.ICredentials`介面](/dotnet/api/system.net.icredentials?view=netstandard-2.0)。</span><span class="sxs-lookup"><span data-stu-id="91147-150">**Return value**: A credentials object implementing the [`System.Net.ICredentials` interface](/dotnet/api/system.net.icredentials?view=netstandard-2.0).</span></span>