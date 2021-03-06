---
title: Publikowanie aplikacji sieci Web przy użyciu skryptu programu PowerShell
description: Dowiedz się, jak opublikować projekt sieci Web w witrynie sieci Web platformy Azure. Ten skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.
ms.custom: vs-azure
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e91fed105ce61dfc7e1cd2779ebcca0b33a06c97
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036499"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (skrypt programu Windows PowerShell)
## <a name="syntax"></a>Składnia
Publikuje projekt sieci Web w witrynie sieci Web platformy Azure. Skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>Konfigurowanie
Ścieżka do pliku konfiguracji JSON opisującego Szczegóły wdrożenia.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagane? |true |
| Położenie |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |fałsz |
| Akceptować symbole wieloznaczne? |fałsz |

## <a name="subscriptionname"></a>SubscriptionName
Nazwa subskrypcji platformy Azure, w której chcesz utworzyć witrynę sieci Web.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagane? |fałsz |
| Położenie |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |fałsz |
| Akceptować symbole wieloznaczne? |fałsz |

## <a name="webdeploypackage"></a>Webdeploypackage została
Ścieżka do pakietu wdrożeniowego sieci Web do opublikowania w witrynie sieci Web. Ten pakiet można utworzyć przy użyciu Kreatora publikacji w sieci Web w programie Visual Studio. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z usługą Azure Cloud Services i ASP.NET](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md).

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagane? |fałsz |
| Położenie |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |fałsz |
| Akceptować symbole wieloznaczne? |fałsz |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Nazwa użytkownika i hasło do bazy danych SQL na platformie Azure.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagane? |fałsz |
| Położenie |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |fałsz |
| Akceptować symbole wieloznaczne? |fałsz |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Jeśli wartość jest równa true, Wydrukuj komunikaty ze skryptu do strumienia wyjściowego.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagane? |fałsz |
| Położenie |nazwane |
| Wartość domyślna |fałsz |
| Akceptujesz dane wejściowe potoku? |fałsz |
| Akceptować symbole wieloznaczne? |fałsz |

## <a name="remarks"></a>Uwagi
Aby uzyskać pełne wyjaśnienie, jak używać skryptu do tworzenia środowisk deweloperskich i testowych, zobacz [Używanie skryptów programu Windows PowerShell do publikowania w środowiskach deweloperskich i testowych](vs-azure-tools-publishing-using-powershell-scripts.md).

Plik konfiguracji JSON określa szczegóły dotyczące tego, co ma zostać wdrożone. Zawiera informacje, które zostały określone podczas tworzenia projektu, takie jak nazwa i username witryny sieci Web. Zawiera również bazę danych, która ma zostać zainicjowana, jeśli istnieje. Poniższy kod przedstawia przykładowy plik konfiguracji JSON:

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication10554",
            "location": "West US"
        },
        "databases": [
            {
                "connectionStringName": "DefaultConnection",
                "databaseName": "WebApplication10554_db",
                "serverName": "iss00brc88",
                "user": "sqluser2",
                "password": "",
                "edition": "",
                "size": "",
                "collation": "",
                "location": "West US"
            }
        ]
    }
}
```

Plik konfiguracji JSON można edytować w celu zmiany wdrożenia. Sekcja witryny sieci Web jest wymagana, ale sekcja bazy danych jest opcjonalna.

## <a name="next-steps"></a>Następne kroki
Aby uzyskać więcej informacji, zobacz [Publish-WebApplicationVM (skrypt programu Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md).
