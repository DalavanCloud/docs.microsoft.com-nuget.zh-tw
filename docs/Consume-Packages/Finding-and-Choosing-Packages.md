---
title: "尋找和選擇 NuGet 套件 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/07/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 8886f899-797b-4704-9d16-820b55b71186
description: "如何尋找和選擇專案之最佳 NuGet 套件的概觀，包含 NuGet 搜尋語法的詳細資料。"
keywords: "NuGet 套件使用, NuGet 套件探索, 最佳 NuGet 套件, 在套件上決定, 使用套件, 評估套件, NuGet 搜尋語法"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 23ef9832af0bd864b6dcd31ab8666ac21c7b2f67
ms.sourcegitcommit: 122bf7ce308365ea45da018b0768f0536de76a1f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="finding-and-evaluating-nuget-packages-for-your-project"></a>尋找和評估您專案的 NuGet 套件

啟動任何 .NET 專案時，或只要識別到您應用程式或服務的功能需求時，就可以使用滿足這項需求的現有 NuGet 套件來節省大量時間和麻煩。 這些套件可以來自 [nuget.org](http://www.nuget.org/packages/) 上的公用集合，或是您組織或其他協力廠商所提供的私人來源。

在此頁面上：

- [尋找套件](#finding-packages)
- [評估套件](#evaluating-packages)
- [搜尋語法](#search-syntax)

## <a name="finding-packages"></a>尋找套件

當您前往 nuget.org 或在 Visual Studio 中開啟套件管理員 UI 時，會看到依總下載次數排序的套件。 這會立即顯示數百萬個 .NET 專案中您最廣泛使用的套件。 接著，前幾個頁面上列出的套件至少有一些可能適用於您的專案。

![顯示最常用套件的 nuget.org/套件的預設檢視](media/Finding-01-Popularity.png)

請注意頁面右上方的 [包含發行前版本] 選項。 選取時，nuget.org 會顯示套件的所有版本，包含搶鮮版 (Beta) 和其他早期版本。 若只要顯示穩定發行的版本，請清除此選項。

針對特定需求，依標記搜尋 (在 Visual Studio 的套件管理員內或在 nuget.org 這類入口網站上) 是探索適合套件的最常見方法。 例如，搜尋 "json" 會列出所有標上該關鍵字的 NuGet 套件，因此具有與 JSON 資料格式的某種關聯性。

![nuget.org 上 'json' 的搜尋結果](media/Finding-02-SearchResults.png)

您也可以使用已知的套件識別碼進行搜尋。 請參閱下面的[搜尋語法](#search-syntax)。

此時，只會依相關性來排序搜尋結果，因此您一般至少會想要查看符合您需求的前幾頁套件結果，或將您的搜尋字詞精簡為更為具體。

### <a name="does-the-package-support-my-projects-target-framework"></a>套件支援我專案的目標架構嗎？

只有在套件支援的架構包含專案的目標架構時，NuGet 才會將該套件安裝至專案  (如需在建立套件時如何完成這項作業的資訊，請參閱[支援多個目標架構](../create-packages/supporting-multiple-target-frameworks.md))。如果套件不相容，NuGet 就會發出錯誤。

部分套件會直接在 nuget.org 資源庫中列出其支援的架構，但因為不需要這類資料，所以許多套件都不會包含該清單。 目前沒有方法可以搜尋 nuget.org 中是否有支援特定目標架構的套件 (這項功能已列入考量，請參閱 [NuGet 問題 2936](https://github.com/NuGet/NuGetGallery/issues/2936))。

幸運的是，您可以透過其他兩種方法來判斷支援的架構：

1. 嘗試在 NuGet 套件管理員主控台中使用 [`Install-Package`](../tools/ps-ref-install-package.md) 命令，以將套件安裝至專案。 如果套件不相容，則此命令會顯示套件所支援的架構。

1. 使用 [資訊] 下的 [手動下載] 連結，以從套件在 nuget.org 上的頁面下載套件。 將副檔名從 `.nupkg` 變更為 `.zip`，並開啟檔案來檢查其 `lib` 資料夾的內容。 在這裡，您會看到每個所支援架構的子資料夾，其中使用目標架構 Moniker (TFM；請參閱[目標架構](../schema/Target-Frameworks.md)) 來命名每個子資料夾。 如果您在 `lib` 下看不到任何子資料夾，而且只有單一 DLL，則必須嘗試將套件安裝至您的專案，以探索其相容性。

## <a name="pre-release-packages"></a>發行前套件

許多套件作者都會將預覽和搶鮮版 (Beta) 版本設為可用，因為他們會繼續進行改善並搜尋其最新版本的意見。

nuget.org 預設會在搜尋結果中顯示發行前套件。 若只要搜尋穩定發行版本，請清除頁面右上方的 [包含發行前版本] 選項

![nuget.org 上的 [包含發行前版本] 核取方塊](media/Finding-06-include-prerelease.png)

在 Visual Studio 中，並且使用 NuGet CLI 時，NuGet 預設不會包含發行前版本。 若要變更此行為，請執行下列步驟：

- **Visual Studio 中的套件管理員 UI**：在 [管理 NuGet 套件] UI 中，設定 [包含發行前版本] 方塊。 設定或清除此方塊時，會重新整理套件管理員 UI 以及您可以安裝的可用版本清單。

    ![Visual Studio 中的 [包含發行前版本] 核取方塊](media/Prerelease_02-CheckPrerelease.png)

- **套件管理員主控台**：使用 `-IncludePrerelease` 參數搭配 `Find-Package`、`Get-Package`、`Install-Package`、`Sync-Package` 和 `Update-Package` 命令。 請參閱 [PowerShell 參考](../tools/powershell-reference.md)。

- **NuGet CLI**：使用 `-prerelease` 參數搭配 `install`、`update`、`delete` 和 `mirror` 命令。 請參閱 [NuGet CLI 參考](../tools/nuget-exe-cli-reference.md)

<a name="native-cpp-packages"></a>

### <a name="native-c-packages"></a>原生 C++ 套件

NuGet (2.5+) 支援可在 Visual Studio 的 C++ 專案中使用的原生 C++ 套件。 這會啟用專案的 [管理 NuGet 套件] 操作功能表命令、引進 `native` 目標架構，並提供 MSBuild 整合。

若要在 [nuget.org](https://www.nuget.org/packages) 上尋找原生套件，請使用 `tag:native` 進行搜尋。 這類套件一般會提供 `.targets` 和 `.props` 檔案，而 NuGet 會在將套件新增至專案時自動匯入這些檔案。

如需建立原生套件的資訊，請參閱[原生套件](../create-packages/native-packages.md)。

## <a name="evaluating-packages"></a>評估套件

評估套件實用性的最佳方式是下載套件並在您的程式碼中進行試用。 畢竟，只有少數使用高度常用之套件的開發人員才能啟動高度常用的套件，而且您可能是早期採用者  (請注意，nuget.org 上的所有套件都會定期掃描是否有病毒)。

同時，使用 NuGet 套件表示與其相依，因此您想要確定其為穩定且可靠。 因為安裝和直接測試套件相當耗時，所以您也可以使用套件清單頁面上的資訊來深入了解套件品質：

- *下載統計資料*：在 nuget.org 的套件頁面上，[統計資料] 區段會顯示總下載次數、最新版的下載，以及每天的平均下載次數。 較大的數字指出許多其他開發人員都具有與套件的相依性，這表示它已證明它自己。

    ![下載套件清單頁面上的統計資料](media/Finding-03-Downloads.png)

- *版本歷程記錄*：在套件頁面上，查看 [資訊] 下的最新更新日期，並檢查 [版本歷程記錄]。 維護良好的套件具有新的更新和豐富的版本歷程記錄。 忽略的套件有幾個更新，而且有時通常尚未更新。

    ![套件清單頁面上的版本歷程記錄](media/Finding-04-VersionHistory.png)

- *最近安裝*：在套件頁面的 [統計資料] 下方，選取 [View full stats] (檢視完整統計資料)。完整統計資料頁面會依版本號碼顯示過去六週的套件安裝。 其他開發人員主動使用的套件一般是比未使用的套件還適合的選擇。

- *支援*：在套件頁面的 [資訊] 下方，選取 [專案網站] (如果有的話) 以查看可用的支援選項。 具有專用網站的專案通常有較佳的支援。

- *開發人員歷程記錄*：在套件頁面的 [擁有者] 下方，選取擁有者以查看他們已發行的其他套件。 具有多個套件的擁有者未來較可能繼續支援其工作。

- *開放原始碼參與*：開放原始碼存放庫會維護許多套件，因此與其相依的開發人員可以直接參與 Bug 修正和功能改善。 任何指定套件的參與歷程記錄也是有多少開發人員主動參與的不錯指標。

- *訪談擁有者*：可以肯定平均認可新的開發人員，以產生您可使用的不錯套件，讓它們有機會帶入 NuGet 生態系統的新項目。 請記住，透過清單頁面的 [資訊] 下方的 [連絡擁有者] 選項直接聯繫套件開發人員。 而且他們很樂意與您合作來滿足您的需求！

> [!Note]
> 請一律留意套件的授權條款，而選取 nuget.org 的套件清單頁面上的 [授權資訊] 即可看到授權條款。如果套件未指定授權條款，請使用套件頁面上的 [連絡擁有者] 連結直接連絡套件擁有者。 Microsoft 不會將任何智慧財產權從協力廠商套件提供者授權給您，而且不負責協力廠商所提供的資訊。

## <a name="search-syntax"></a>搜尋語法

在 nuget.org 上、從 NuGet CLI 中，以及 Visual Studio 的 NuGet 套件管理員延伸模組內，NuGet 套件搜尋的運作都相同。 一般而言，會將搜尋套用至關鍵字和套件描述。

- **關鍵字**：搜尋會尋找包含所有已提供關鍵字的相關套件。 範例：

    ```
    modern UI javascript
    ```

- **詞組**：輸入以雙引號括住的字詞會尋找與這些字詞完全相同且不區分大小寫的相符項。 範例：

    ```
    "modern UI" package
    ```

- **篩選**：您可以使用 `<property>:<term>` 語法，將搜尋字詞套用至特定屬性，其中 `<property>` (不區分大小寫) 可以是 `id`、`packageid`、`version`、`title`、`tags`、`author`、`description`、`summary` 和 `owner`。 必要時，可以使用引號括住字詞，而且您可以同時搜尋多個屬性。 此外，對 `id` 屬性的搜尋是子字串比對，而 `packageid` 使用精確比對。 例如：

    ```
    id:NuGet.Core                //Match any part of the id property
    Id:"Nuget.Core"
    ID:jQuery
    title:jquery                 //Searches title as shown on the package listing
    PackageId:jquery             //Match the package id exactly
    id:jquery id:ui              //Search for multiple terms in the id
    id:jquery tags:validation    //Search multiple properties
    id:"jquery.ui"               //Phrase search
    invalid:jquery ui            //Unsupported properties are ignored, so this
                                 //is the same as searching on jquery ui
    ```