---
title: NuGet CLI 登命令 |Microsoft 文件
author: dtivel
ms.author: dtivel
manager: doronm
ms.date: 03/06/2018
ms.topic: reference
ms.prod: nuget
ms.technology: ''
description: Nuget.exe 登命令參考
keywords: nuget 符號參考登命令
ms.reviewer:
- karann
- rmpablos
ms.workload:
- dotnet
- aspnet
ms.openlocfilehash: 9c83e5abae0e70cdc62917861c1febfce4f792c7
ms.sourcegitcommit: beb229893559824e8abd6ab16707fd5fe1c6ac26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="sign-command-nuget-cli"></a>符號命令 (NuGet CLI)

**適用於：**封裝建立&bullet;**支援的版本：** 4.6 +

簽署憑證的第一個引數比對的所有封裝。 從檔案或從安裝在憑證存放區提供主體名稱或指紋的憑證，您可以取得具有私密金鑰的憑證。

封裝簽章尚未支援單聲道下或在非 Windows 平台上。

## <a name="usage"></a>使用量

```cli
nuget sign <package(s)> [options]
```

其中`<package(s)>`是一個或多個`.nupkg`檔案。

## <a name="options"></a>選項

| 選項 | 描述 |
| --- | --- |
| CertificateFingerprint | 指定用來搜尋憑證的本機憑證存放區的憑證的 sha-1 指紋。 |
| CertificatePassword | 如有需要請指定憑證的密碼。 如果憑證是受密碼保護，但不提供任何密碼，此命令會提示輸入密碼在執行階段，除非-傳遞非互動式選項。 |
| CertificatePath | 指定要用來簽署封裝的憑證的檔案路徑。 |
| CertificateStoreLocation | 指定 X.509 憑證存放區用來搜尋憑證的名稱。 預設值為"CurrentUser"，目前使用者所使用的 X.509 憑證存放區。 指定透過-CertificateSubjectName 或-CertificateFingerprint 選項憑證時，應該使用這個選項。 |
| CertificateStoreName | 指定要用於搜尋憑證的 X.509 憑證存放區的名稱。 預設為 「 我的 」，個人憑證的 X.509 憑證存放區。 指定透過-CertificateSubjectName 或-CertificateFingerprint 選項憑證時，應該使用這個選項。 |
| CertificateSubjectName | 指定用來搜尋憑證的本機憑證存放區的憑證的主體名稱。  搜尋不區分大小寫字串比較，使用所提供的值，會發現所有憑證的主體名稱，包含該字串，不論其他主體的值。  -CertificateStoreName 和-CertificateStoreLocation 選項所指定的憑證存放區。 |
| ConfigFile | 要套用的 NuGet 設定檔案。 如果未指定， `%AppData%\NuGet\NuGet.Config` (Windows) 或`~/.nuget/NuGet/NuGet.Config`(Mac/Linux) 會使用。|
| ForceEnglishOutput | 強制使用的非變異的英文文化特性來執行 nuget.exe。 |
| HashAlgorithm | 要用來簽署套件的雜湊演算法。 預設為 SHA256。 |
| 說明 | 顯示說明命令的資訊。 |
| NonInteractive | 抑制使用者輸入或確認提示。 |
| OutputDirectory | 指定用來儲存已簽署的封裝的目錄。 依預設會覆寫的已簽署套件的原始封裝。 |
| 覆寫 | 表示是否應該覆寫目前的簽章的參數。 如果已經有套件的簽章，則預設將會失敗命令。 |
| Timestamper | RFC 3161 時間戳記伺服器的 URL。 |
| TimestampHashAlgorithm | RFC 3161 時間戳記伺服器所使用的雜湊演算法。 預設為 SHA256。 |
| 詳細資訊 | 指定在輸出中顯示詳細資料的數量：*正常*，*安靜*，*詳細*。 |

## <a name="examples"></a>範例

```cli
nuget sign MyPackage.nupkg -Timestamper http://timestamp.test

nuget sign .\..\MyPackage.nupkg -Timestamper http://timestamp.test -OutputDirectory .\..\Signed
```