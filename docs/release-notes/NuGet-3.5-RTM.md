---
title: NuGet 3.5 Beta 版本資訊
description: 版本資訊適用於 NuGet 3.5 包括已知的問題、 bug 修正、 新增的功能和 Dcr。
author: karann-msft
ms.author: karann
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: d8df2cb51ddcc03fb3922d9e9def17b39fccc661
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43550680"
---
# <a name="nuget-35-release-notes"></a>NuGet 3.5 的版本資訊

[NuGet 3.5 RC 版本資訊](../release-notes/nuget-3.5-RC.md) | [NuGet 4.0 RC 版本資訊](../release-notes/nuget-4.0-RC.md)

## <a name="bug-fixes"></a>Bug 修正

* 組件不會使用 MSBuild 14.1-在 mono 上[#3550](https://github.com/NuGet/Home/issues/3550)

* 更新] 索引標籤不會選取最新可用版本，來更新改為選取目前的安裝的版本- [#3498](https://github.com/NuGet/Home/issues/3498)

* 驗證私用的 v2 MyGet 摘要，然後按一下 [顯示更多結果 x] 之後，修正損毀- [#3469](https://github.com/NuGet/Home/issues/3469)

* 記錄檔訊息似乎是反向順序的 UI- [#3446](https://github.com/NuGet/Home/issues/3446)

* v3.4.4-Nuget 還原會擲回 「 不支援指定的路徑格式"- [#3442](https://github.com/NuGet/Home/issues/3442)

* NuGet cmdLine 3.6 beta 版不接受-Prop 組態 = 版本- [#3432](https://github.com/NuGet/Home/issues/3432)

* 在大型的專案-上安裝的 Nuget IKVM 緩慢[#3428](https://github.com/NuGet/Home/issues/3428)

* nuget.exe 本身會保留在更新本身-更新[#3395](https://github.com/NuGet/Home/issues/3395)

* 3.5 安裝/還原從 UNC 共用具有效能迴歸 3.4.4- [#3355](https://github.com/NuGet/Home/issues/3355)

* 從 [套件管理 UI net451 專案-安裝 Moq 時的錯誤[#3349](https://github.com/NuGet/Home/issues/3349)

* 在解決方案層級的 [安裝] 索引標籤不會顯示套件的版本- [#3339](https://github.com/NuGet/Home/issues/3339)

* xproj `project.json` update 從已安裝] 索引標籤便會遺失狀態- [#3303](https://github.com/NuGet/Home/issues/3303)

* 在 NuGet 套件`.csproj`會忽略空的檔案中的項目`.nuspec`檔案- [#3257](https://github.com/NuGet/Home/issues/3257)

* 在 IIS 中裝載的網站專案不會導致還原失敗- [#3235](https://github.com/NuGet/Home/issues/3235)

* 認證不從 Nuget.Config 擷取當 v3 端點重新導向至 v2- [#3179](https://github.com/NuGet/Home/issues/3179)

* NuGet 組件無法解析組件時擷取的可攜式組件中繼資料- [#3128](https://github.com/NuGet/Home/issues/3128)

* 找不到 Nuget `msbuild.exe` -在 Mono 上[#3085](https://github.com/NuGet/Home/issues/3085)

* nuget.exe 組件不允許發行前版本標記開頭數字- [# 1743年](https://github.com/NuGet/Home/issues/1743)

* nuget 套件安裝失敗上 VS2015E- [# 1298年](https://github.com/NuGet/Home/issues/1298)

* allowedVersions 篩選不在解決方案層級-工作[#333](https://github.com/NuGet/Home/issues/333)

* 隨機，還原會失敗並具有相同的項目已新增金鑰。 - [#2646](https://github.com/NuGet/Home/issues/2646)

* 無法安裝在 Nuget.Common `.csproj`  -  [# 2635年](https://github.com/NuGet/Home/issues/2635)

* FindPackagesById 時您可以使用 UI 來搜尋 V2 來源，會呼叫兩次的每個識別碼- [# 2517年](https://github.com/NuGet/Home/issues/2517)

* 封裝無法取決於專案- [# 2490年](https://github.com/NuGet/Home/issues/2490)

* nuget.exe pack-排除已記載，但不是支援- [# 2284年](https://github.com/NuGet/Home/issues/2284)

* 問題與錯誤訊息 'contentFiles' 區段`.nuspec`無效- [# 1686年](https://github.com/NuGet/Home/issues/1686)

* 會將一律傳送推播，整個封裝兩次的驗證套件來源- [# 1501年](https://github.com/NuGet/Home/issues/1501)

* 當呼叫 nuget.exe 更新 *.csproj 專案時並沒有提供任何資訊`packages.config`  -  [# 1496年](https://github.com/NuGet/Home/issues/1496)

* `packages.config` 還原不會重試在來源 V2-5xx 狀態碼[# 1217年](https://github.com/NuGet/Home/issues/1217)

* 在檔案中的 src 成雙點`.nuspec`無法運作- [# 2947年](https://github.com/NuGet/Home/issues/2947)

* CoreCLR 還原需要略過與加密-摘要[# 2942年](https://github.com/NuGet/Home/issues/2942)

* nuget.exe 推送 403 處理-錯誤提示輸入認證時- [# 2910年](https://github.com/NuGet/Home/issues/2910)

* 透過套件管理員的 NuGet 更新會移除屬性從`project.json`  -  [# 2888年](https://github.com/NuGet/Home/issues/2888)

* NuGet.PackageManagement.VisualStudio 嘗試載入 「 NuGet.TeamFoundationServer14"，但 DLL 名稱變更為 ["NuGet.TeamFoundationServer"- [# 2857年](https://github.com/NuGet/Home/issues/2857)

* UI 未顯示新的套件管理員更新版本- [# 2828年](https://github.com/NuGet/Home/issues/2828)

* 嘗試使用 [packageid，更新套件版本，而不是 package.version- [# 2771年](https://github.com/NuGet/Home/issues/2771)

* 如果專案不使用 nuget，nuget 還原 csproj 應該錯誤 (`packages.config`或是`project.json`)- [# 2766年](https://github.com/NuGet/Home/issues/2766)

* TFS 錯誤 「 [file] 會在您的工作區中找不到，或您沒有存取權限 」 期間升級或解除安裝方案/專案繫結至 TFS 原始檔控制- [# 2739年](https://github.com/NuGet/Home/issues/2739)

* 更新套件不會取得非目標套件-相依性[# 2724年](https://github.com/NuGet/Home/issues/2724)

* 沒有任何方法來設定記錄檔詳細等級 Nuget 套件管理員 UI 動作- [# 2705年](https://github.com/NuGet/Home/issues/2705)

* nuget 組態無效-VS 2015 VSIX (v3.4.3)- [# 2667年](https://github.com/NuGet/Home/issues/2667)

* 在 [DefaultPushSource `NuGetDefaults.Config` (`ProgramData\NuGet`) 無法運作- [# 2653年](https://github.com/NuGet/Home/issues/2653)

* nuget 3.4.3 版本-取得值不可為 null 套件組建- [# 2648年](https://github.com/NuGet/Home/issues/2648)

* 還原不使用預存的認證從 Nuget.Config 的 VSTS 摘要- [# 2647年](https://github.com/NuGet/Home/issues/2647)

* [dotnet 還原]-configfile 是相對於專案目錄，而不是 cmd dir 中- [# 2639年](https://github.com/NuGet/Home/issues/2639)

* 在版本 comparsion 程式碼-過度配置[# 2632年](https://github.com/NuGet/Home/issues/2632)

* Nuget.exe 嘗試安裝相同的多個執行個體的封裝將平行處理會導致重複的寫入- [# 2628年](https://github.com/NuGet/Home/issues/2628)

* 相依性資訊不會快取的多專案作業- [# 2619年](https://github.com/NuGet/Home/issues/2619)

* 安裝及更新下載的封裝，而不先檢查 [packages] 資料夾[# 2618年](https://github.com/NuGet/Home/issues/2618)

* 如果套件來源清單是空的無法新增封裝來源，透過 UI (NuGet 3.4.x)- [# 2617年](https://github.com/NuGet/Home/issues/2617)

* 誤導錯誤時嘗試安裝套件，取決於設計階段 facade- [# 2594年](https://github.com/NuGet/Home/issues/2594)

* 安裝套件從 PackageManager 主控台中設定 「 All 」 會嘗試第一個來源- [# 2557年](https://github.com/NuGet/Home/issues/2557)

* 無法解壓縮的最新 beta ModernHttpClient- [# 2518年](https://github.com/NuGet/Home/issues/2518)

* 在自行建置 nuget 3.4.1-啟動 VS2015 損毀[# 2419年](https://github.com/NuGet/Home/issues/2419)

* 更新命令可能是比較冗長一點我問要的所以...-如果[# 2418年](https://github.com/NuGet/Home/issues/2418)

* 在本機建置的 VSIX 應該與 CI 組建具有相同的 Dll 和檔案。 - [#2401](https://github.com/NuGet/Home/issues/2401)

* 修正在組建中的 NuGet 降級警告[# 2396年](https://github.com/NuGet/Home/issues/2396)

* 無法驗證套件來源 （3 次） 會封鎖永遠- [# 2362年](https://github.com/NuGet/Home/issues/2362)

* 從 nuget v3.3 + 安裝的套件摘要與引數時未正確地還原套件內容-NoCache 當套件包含`.nupkg`檔案- [# 2354年](https://github.com/NuGet/Home/issues/2354)

* 所有的套件來源，但遺漏 1 個來源，封裝 Nuget 安裝失敗- [# 2322年](https://github.com/NuGet/Home/issues/2322)

* [PerfWatson] UIDelay: nuget.packagemanagement.visualstudio.dll!NuGet.PackageManagement.VisualStudio.VSMSBuildNuGetProjectSystem+*lt;&gt;c__DisplayClass_0+&lt;&lt;AddReference&gt;b__&gt;d.MoveNext - [#2285](https://github.com/NuGet/Home/issues/2285)

* 如果單一來源授權-就會失敗，請安裝區塊[# 2034年](https://github.com/NuGet/Home/issues/2034)

* `.nuspec` 版本範圍應該覆寫-IncludeReferencedProjects 版本- [# 1983年](https://github.com/NuGet/Home/issues/1983)

* 更新套件極為緩慢-「 嘗試收集相依性資訊 」- [# 1909年](https://github.com/NuGet/Home/issues/1909)

* NuGet 隱形降級會封裝當批次更新其相依性- [# 1903年](https://github.com/NuGet/Home/issues/1903)

* nuget.exe 更新卸除組件的強式名稱和私用的屬性。 - [#1778](https://github.com/NuGet/Home/issues/1778)

* 相對檔案路徑，如 「 DefaultPushSource"- [# 1746年](https://github.com/NuGet/Home/issues/1746)

* 改善解析程式失敗的訊息- [# 1373年](https://github.com/NuGet/Home/issues/1373)

* 更新-套件 v3 中無法使用不在指定的來源層中的套件[# 1013年](https://github.com/NuGet/Home/issues/1013)

* 使用相對路徑的套件來源會搭配- [#865](https://github.com/NuGet/Home/issues/865)

* 遺失相依性 NUPKG-如果間接相依性已經存在具有較低的版本需求-從專案所產生的檔案中[#759](https://github.com/NuGet/Home/issues/759)

* 刪除專案關閉對應的 UI 視窗中，但重新命名專案不會重新命名 UI 視窗。 請注意 PMC 接聽專案重新命名] 和 [專案移除的事件- [#670](https://github.com/NuGet/Home/issues/670)

* [柳樹 Web 工作負載]建立 Razor v3 WSP 停止回應- [#3241](https://github.com/NuGet/Home/issues/3241)

* 安裝/還原的特定套件因 「 封裝包含多個 nuspec 檔案 」。 - [#3231](https://github.com/NuGet/Home/issues/3231)

* 小寫識別碼 &`packages.config`案例- [#3209](https://github.com/NuGet/Home/issues/3209)

* [3.5-beta2]套件還原無法還原 「 舊版 」 封裝- [#3208](https://github.com/NuGet/Home/issues/3208)

* nuget 組件強制將.tt 檔案加入至內容的資料夾，無論如何- [#3203](https://github.com/NuGet/Home/issues/3203)

* 更新套件的 ASP.NET web 應用程式會產生與檔案相關的警告： 原始檔- [#3194](https://github.com/NuGet/Home/issues/3194)

* nuget 套件 csproj (與`project.json`) 如果沒有任何 packOptions 及 JSON 檔案中的擁有者會當機[#3180](https://github.com/NuGet/Home/issues/3180)

* 適用於 nuget 套件`project.json`會忽略 packOptions 標記，例如摘要、 作者、 擁有者等- [#3161](https://github.com/NuGet/Home/issues/3161)

* NullReferenceException via NuGet.Packaging.PhysicalPackageFile.GetStream - [#3160](https://github.com/NuGet/Home/issues/3160)

* NuGet 套件會忽略輸出中的相依性`.nuspec`for `project.json`  -  [#3145](https://github.com/NuGet/Home/issues/3145)

* 使用回復更新多個封裝離開專案處於中斷狀態- [#3139](https://github.com/NuGet/Home/issues/3139)

* 任何的 ContentFiles 不會新增為 netstandard 專案- [#3118](https://github.com/NuGet/Home/issues/3118)

* 無法封裝以.Net 為目標的程式庫標準正確- [#3108](https://github.com/NuGet/Home/issues/3108)

* 檔案]-> [新增專案]-> [類別庫 （可攜式） 專案會失敗，VS2015 和 Dev15- [#3094](https://github.com/NuGet/Home/issues/3094)

* NuGet 錯誤-1.0.0-* 不是有效的版本字串- [#3070](https://github.com/NuGet/Home/issues/3070)

* 尋找套件無法顯示，但安裝套件的運作方式- [#3068](https://github.com/NuGet/Home/issues/3068)

* 錯誤時 「 Install-package jquery.validation 」 在 dev15- [#3061](https://github.com/NuGet/Home/issues/3061)

* xproj nuget 組件預設為無效的目標路徑- [#3060](https://github.com/NuGet/Home/issues/3060)

* 當已安裝的 VS 2015 更新 3 上使用的 NuGet 3.5.0 的版本時發生錯誤，就會發生-VS [#3053](https://github.com/NuGet/Home/issues/3053)

* 「 被封鎖的 packages.config 」 `project.json` (UWP，又稱為組建整合) 專案- [#3046](https://github.com/NuGet/Home/issues/3046)

* 更新 dotnet cli 安裝 preview2-003121，也就是正式 preview2 組建的組建指令碼。 - [#3045](https://github.com/NuGet/Home/issues/3045)

* 套件管理員 UI： 不會顯示在更新封裝之後，新的版本- [#3041](https://github.com/NuGet/Home/issues/3041)

* 刪除命令列上的-ApiKey 中不會讀取/傳送 3.5.0-beta- [#3037](https://github.com/NuGet/Home/issues/3037)

* 不正確的字串： 上的發行前版本的相依性不應該有套件的穩定版本。 - [#3030](https://github.com/NuGet/Home/issues/3030)

* OptimizedZipPackage 快取會留下空的資料夾- [#3029](https://github.com/NuGet/Home/issues/3029)

* 正在建立 PCL （net46 和 windows 10） 專案取得 NullRef 例外狀況。 - [#3014](https://github.com/NuGet/Home/issues/3014)

* Nuget 更新應該提供的告知性訊息，當較高的版本會受到 allowedVersions 條件約束- [#3013](https://github.com/NuGet/Home/issues/3013)

* Nuget v3 還原問題- [# 2891年](https://github.com/NuGet/Home/issues/2891)

* 認證外掛程式已結束，錯誤為-1 / 錯誤下載套件時使用多個來源的認證提供者[# 2885年](https://github.com/NuGet/Home/issues/2885)

* `project.json` nuget 還原會造成重新編譯時執行任何動作變更- [# 2817年](https://github.com/NuGet/Home/issues/2817)

* 符號套件應該以往無法用於安裝或更新- [# 2807年](https://github.com/NuGet/Home/issues/2807)

* 與不支援環境變數中 repositoryPath （nuget.exe 執行）- [# 2763年](https://github.com/NuGet/Home/issues/2763)

* 標籤協助工具： 在套件管理員 UI 中未標記的 Uielement [# 2745年](https://github.com/NuGet/Home/issues/2745)

* 可移植的架構，與連字號連接的設定檔會遭到拒絕。 - [#2734](https://github.com/NuGet/Home/issues/2734)

* NuGet 套件管理員可以讓您清楚該詳細資料不適用於封裝中的 [選項] 清單`project.json`  -  [# 2665年](https://github.com/NuGet/Home/issues/2665)

* nuget.exe 推送/刪除不會使用 API 金鑰- [# 2627年](https://github.com/NuGet/Home/issues/2627)

* 已鎖定的屬性移除鎖定檔中- [# 2379年](https://github.com/NuGet/Home/issues/2379)

* NuGet 3.3.0 更新因 '...額外的條件約束中定義 packages.config 可避免這項作業。 ' - [#1816](https://github.com/NuGet/Home/issues/1816)

* 假的訊息-從本機來源不存在則會擲回安裝封裝[# 1674年](https://github.com/NuGet/Home/issues/1674)

* [可升級] 篩選條件會顯示升級違反版本條件約束- [# 1094年](https://github.com/NuGet/Home/issues/1094)

* 無法更新原生套件- [# 1291年](https://github.com/NuGet/Home/issues/1291)


## <a name="features"></a>功能

* 支援設定 CopyLocal 設為 false，參考加入 NuGet- [#329](https://github.com/NuGet/Home/issues/329)

* MSBuild 15-nuget.exe 支援[# 1937年](https://github.com/NuGet/Home/issues/1937)

* 組件支援。`csproj` + `project.json` - [#1689](https://github.com/NuGet/Home/issues/1689)

* 停用使用者動作，當使用者正在執行的動作- [# 1440年](https://github.com/NuGet/Home/issues/1440)

* NuGet 應新增的支援`runtimes/{rid}/nativeassets/{txm}/`  -  [# 2782年](https://github.com/NuGet/Home/issues/2782)

* 新增 NuGet 中遺漏的 framework 相容性 （也就是已經在 3.x） 的 2.x- [# 2720年](https://github.com/NuGet/Home/issues/2720)

* 支援後援的套件資料夾- [# 2899年](https://github.com/NuGet/Home/issues/2899)

* 設計和實作封裝類型的概念，以支援工具套件- [# 2476年](https://github.com/NuGet/Home/issues/2476)

* 新增 API 來取得全域套件資料夾的路徑[# 2403年](https://github.com/NuGet/Home/issues/2403)

* 啟用在組件-SemVer 2.0.0 [#3356](https://github.com/NuGet/Home/issues/3356)

## <a name="dcrs"></a>DCR

* nuget.exe 推送-逾時參數無法運作- [# 2785年](https://github.com/NuGet/Home/issues/2785)

* 封裝描述文字應該是可選取- [# 1769年](https://github.com/NuGet/Home/issues/1769)

* 啟用以產生 nuget.exe`.props`並`.targets`檔案`.nuproj`專案[# 2711年](https://github.com/NuGet/Home/issues/2711)

* 新增擴充性 API，以比較架構與匯入- [# 2633年](https://github.com/NuGet/Home/issues/2633)

* 使用時，隱藏相依性的選項`project.json`  -  [# 2486年](https://github.com/NuGet/Home/issues/2486)

* 印出詳細的輸出層中的 nuget.exe 版本標頭[# 1887年](https://github.com/NuGet/Home/issues/1887)

* NuGet 需要讓使用者知道，升級/安裝中基礎 dotnet tfm PCL 可能會造成問題- [#3138](https://github.com/NuGet/Home/issues/3138)

* 不正確安裝/升級具有 tfm 的專案，即發出警告 ="dotnet"- [#3137](https://github.com/NuGet/Home/issues/3137)

* 更新-修正效能問題 ReShaper 和 NuGet [#3044](https://github.com/NuGet/Home/issues/3044)

* 新增 netcoreapp11 和 netstandard17 支援- [# 2998年](https://github.com/NuGet/Home/issues/2998)

* 運用 AssemblyMetadata 屬性`.nuspec`語彙基元取代- [# 2851年](https://github.com/NuGet/Home/issues/2851)
