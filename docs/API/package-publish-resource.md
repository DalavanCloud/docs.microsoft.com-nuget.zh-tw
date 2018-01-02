---
title: "發送和刪除，NuGet API |Microsoft 文件"
author:
- joelverhagen
- kraigb
ms.author:
- joelverhagen
- kraigb
manager: skofman
ms.date: 10/26/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 1eaa403a-5c13-4c05-9352-2f791b98aa7e
description: "發行服務可讓用戶端對發佈新的套件和 unlist 或刪除現有的封裝。"
keywords: "NuGet API 發送套件，NuGet API 刪除套件，NuGet API unlist 套件，NuGet API 上傳封裝、 NuGet API 建立封裝"
ms.reviewer:
- karann
- unniravindranathan
ms.openlocfilehash: 1fa3c0e1698a11208d9ef29fdf26a4980cb60cf5
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="push-and-delete"></a>發送和刪除

可推入，並刪除 （或 unlist，不同的伺服器實作） 使用 NuGet V3 API 的封裝。
這兩項作業會為基礎`PackagePublish`資源中找到[服務索引](service-index.md)。

## <a name="versioning"></a>版本控制

下列`@type`會使用值：

@type 值          | 注意
-------------------- | -----
PackagePublish/2.0.0 | 初版

## <a name="base-url"></a>基礎 URL

下列應用程式開發介面的基底 URL 是值`@id`屬性`PackagePublish/2.0.0`封裝來源中的資源[服務索引](service-index.md)。 如下列文件，會使用 nuget.org 的 URL。 請考慮`https://www.nuget.org/api/v2/package`做為預留位置`@id`值的索引中找到服務。

請注意，此 URL 指向舊版 V2 推入端點的相同位置因為通訊協定是相同。

## <a name="http-methods"></a>HTTP 方法

`PUT`和`DELETE`這項資源所支援的 HTTP 方法。 針對每個端點都支援的方法，請參閱下文。

## <a name="push-a-package"></a>推播封裝

nuget.org 支援使用下列 API 的推送新套件。 如果提供的識別碼和版本的套件已經存在，nuget.org 將會拒絕推送。 其他封裝來源可能會支援取代現有的封裝。

```
PUT https://www.nuget.org/api/v2/package
```

### <a name="request-parameters"></a>要求參數

名稱           | In     | 類型   | 必要 | 注意
-------------- | ------ | ------ | -------- | -----
X-NuGet-ApiKey | 頁首 | 字串 | 是      | 例如：`X-NuGet-ApiKey: {USER_API_KEY}`

API 金鑰是不透明的字串從套件來源取得的使用者，並設定在用戶端。 託管沒有特定字串的格式，但 API 金鑰的長度應該超過合理的大小，如 HTTP 標頭值。

### <a name="request-body"></a>要求本文

要求主體必須有下列形式：

#### <a name="multipart-form-data"></a>多部分表單資料

要求標頭`Content-Type`是`multipart/form-data`和要求主體中的第一個項目會被按下的.nupkg 未經處理位元組。 在多組件主體中的後續項目都會被忽略。 檔案名稱或其他任何標頭的多組件的項目都會被忽略。

### <a name="response"></a>回應

狀態碼 | 意義
----------- | -------
201, 202    | 封裝已成功推入
400         | 提供的封裝無效
409         | 提供的識別碼和版本的封裝已經存在

當封裝成功推入時傳回成功狀態碼有所不同伺服器實作。

## <a name="delete-a-package"></a>刪除的封裝

nuget.org 會解譯為封裝刪除要求的"unlist"。 這表示封裝仍可供現有消費者的封裝，但封裝不會再出現在搜尋結果中或在 web 介面。 如需此作法的詳細資訊，請參閱[刪除封裝](../policies/deleting-packages.md)原則。 其他伺服器實作會解譯為永久刪除這個信號、 虛刪除，或 unlist 可用。 例如， [NuGet.Server](https://www.nuget.org/packages/NuGet.Server) （只支援較舊的 V2 API 的伺服器實作） 支援處理此要求為 unlist 或永久刪除，根據組態選項。

```
DELETE https://www.nuget.org/api/v2/package/{ID}/{VERSION}
```

### <a name="request-parameters"></a>要求參數

名稱           | In     | 類型   | 必要 | 注意
-------------- | ------ | ------ | -------- | -----
ID             | URL    | 字串 | 是      | 要刪除的封裝識別碼
VERSION        | URL    | 字串 | 是      | 若要刪除封裝版本
X-NuGet-ApiKey | 頁首 | 字串 | 是      | 例如：`X-NuGet-ApiKey: {USER_API_KEY}`

### <a name="response"></a>回應

狀態碼 | 意義
----------- | -------
204         | 已刪除封裝
404         | 使用提供的封裝`ID`和`VERSION`存在