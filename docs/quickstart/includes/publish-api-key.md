1. <span data-ttu-id="cb80f-101">[登入 nuget.org 帳戶](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) \(英文\)，或者，如果您還沒有帳戶，則建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb80f-101">[Sign into your nuget.org account](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) or create an account if you don't have one already.</span></span>

1. <span data-ttu-id="cb80f-102">選取您的使用者名稱 (在右上方)，然後選取 [API 金鑰]。</span><span class="sxs-lookup"><span data-stu-id="cb80f-102">Select your user name (on the upper right), then select **API Keys**.</span></span>

1. <span data-ttu-id="cb80f-103">選取 [建立]，提供金鑰的名稱，選取 [選取範圍] > [推送]。</span><span class="sxs-lookup"><span data-stu-id="cb80f-103">Select **Create**, provide a name for your key, select **Select Scopes > Push**.</span></span> <span data-ttu-id="cb80f-104">在 [API 金鑰] 底下，針對 [Glob 模式] 輸入 \*，然後選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="cb80f-104">Under **API Key**, enter \* for **Glob pattern**, then select **Create**.</span></span> <span data-ttu-id="cb80f-105">(如需範圍的詳細資訊，請參閱下方)。</span><span class="sxs-lookup"><span data-stu-id="cb80f-105">(See below for more about scopes.)</span></span>

1. <span data-ttu-id="cb80f-106">建立金鑰之後，選取 [複製] 以擷取 CLI 中您需要的存取金鑰：</span><span class="sxs-lookup"><span data-stu-id="cb80f-106">Once the key is created, select **Copy** to retrieve the access key you need in the CLI:</span></span>

    ![將 API 金鑰複製到剪貼簿](../media/QS_Create-02-APIKey.png)

1. <span data-ttu-id="cb80f-108">**重要**：將您的金鑰儲存於安全的位置，因為您稍後就無法再次複製此金鑰。</span><span class="sxs-lookup"><span data-stu-id="cb80f-108">**Important**: Save your key in a secure location because you cannot copy the key again later on.</span></span> <span data-ttu-id="cb80f-109">如果您返回 API 金鑰頁面，則需要重新產生金鑰才能加以複製。</span><span class="sxs-lookup"><span data-stu-id="cb80f-109">If you return to the API key page, you need to regenerate the key to copy it.</span></span> <span data-ttu-id="cb80f-110">如果您不再想要透過 CLI 推送套件，也可以移除 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="cb80f-110">You can also remove the API key if you no longer want to push packages via the CLI.</span></span>

<span data-ttu-id="cb80f-111">設定範圍可讓您針對不同用途建立個別的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="cb80f-111">Scoping allows you to create separate API keys for different purposes.</span></span> <span data-ttu-id="cb80f-112">每個金鑰都有其到期的時間範圍，且可將範圍設定為特定套件 (或 Glob 模式)。</span><span class="sxs-lookup"><span data-stu-id="cb80f-112">Each key has its expiration timeframe and can be scoped to specific packages (or glob patterns).</span></span> <span data-ttu-id="cb80f-113">每個金鑰也可將範圍設定為特定作業：新套件和更新的推送、僅更新的推送，或取消列入。</span><span class="sxs-lookup"><span data-stu-id="cb80f-113">Each key is also scoped to specific operations: push of new packages and updates, push of updates only, or delisting.</span></span> <span data-ttu-id="cb80f-114">透過設定範圍，您就可針對組織中管理套件的不同人員建立 API 金鑰，讓他們只具有所需的權限。</span><span class="sxs-lookup"><span data-stu-id="cb80f-114">Through scoping, you can create API keys for different people who manage packages for your organization such that they have only the permissions they need.</span></span> <span data-ttu-id="cb80f-115">如需詳細資訊，請參閱[具範圍的 API 金鑰簡介](https://blog.nuget.org/20170202/introducing-scoped-api-keys.html) \(英文\) (blogs.nuget.org)。</span><span class="sxs-lookup"><span data-stu-id="cb80f-115">For more information, see [Introducing scoped API keys](https://blog.nuget.org/20170202/introducing-scoped-api-keys.html) (blogs.nuget.org).</span></span>