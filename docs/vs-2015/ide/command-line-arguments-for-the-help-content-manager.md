---
title: Argumenty wiersza polecenia dla Menedżera zawartości pomocy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3e7cc942550c979ca4b3f3138da252321b4c983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619689"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumenty wiersza poleceń Menedżera zawartości pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz określić sposób wdrażania lokalnej zawartości pomocy i zarządzania nią za pomocą argumentów wiersza polecenia dla Menedżera zawartości pomocy (HlpCtntmgr.exe). Należy uruchomić skrypty dla tego narzędzia wiersza polecenia z uprawnieniami administratora i nie można uruchamiać tych skryptów jako usługi. Za pomocą tego narzędzia można wykonać następujące zadania:

- Dodaj lub Aktualizuj lokalną zawartość pomocy z dysku lub z chmury.

- Usuń lokalną zawartość pomocy.

- Przenieś lokalny magazyn zawartości pomocy.

- Dodawanie, aktualizowanie, usuwanie lub przenoszenie lokalnej zawartości pomocy w trybie dyskretnym.

  Składnia:

```
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

 Na przykład:

```
hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

## <a name="switches-and-arguments"></a>Przełączniki i argumenty
 W poniższej tabeli zdefiniowano przełączniki i argumenty, których można użyć do narzędzia wiersza polecenia dla Menedżera zawartości pomocy:

|Przełącznik|Wymagane?|Argumenty|
|------------|---------------|---------------|
|/operation|Tak|-   **Zainstaluj**— dodaje książki z określonego źródła instalacji do magazynu zawartości lokalnej.<br />     Ten przełącznik wymaga argumentu/booklist, argumentu/sourceURI lub obu tych wartości. Jeśli nie określisz argumentu/sourceURI, domyślny identyfikator URI programu Visual Studio jest używany jako źródło instalacji. Jeśli nie określisz argumentu/booklist, zostaną zainstalowane wszystkie książki na/sourceUri.<br />-   **Odinstaluj**— usuwa książki określone przez użytkownika z lokalnego magazynu zawartości.<br />     Ten przełącznik wymaga argumentu/booklist lub argumentu/sourceURI.  Jeśli określisz argument/sourceURI, wszystkie książki zostaną usunięte, a argument/booklist zostanie zignorowany.<br />-   **Move**--przenosi magazyn lokalny do określonej ścieżki. Domyślna ścieżka do lokalnego magazynu jest ustawiana przez Instalatora pomocy w obszarze% PROGRAMDATA%<br />     Ten przełącznik wymaga argumentów/locationPath i/catalogName. Komunikaty o błędach będą rejestrowane w dzienniku zdarzeń w przypadku określenia ścieżki, która jest nieprawidłowa lub jeśli dysk nie zawiera wystarczającej ilości wolnego miejsca do przechowywania zawartości.<br />-   **Odśwież**--aktualizuje tematy, które uległy zmianie od czasu ich instalacji lub niedawno zaktualizowane.<br />     Ten przełącznik wymaga argumentu/sourceURI.|
|/catalogName|Tak|Określa nazwę wykazu zawartości.|
|wymaganego/locale.|Nie|Określa ustawienia regionalne produktu, które są używane do wyświetlania zawartości i zarządzania nią dla bieżącego wystąpienia podglądu pomocy. Na przykład należy określić `EN-US` dla Stany Zjednoczone w języku angielskim.<br /><br /> Jeśli nie określisz ustawień regionalnych, zostanie użyta wartość ustawienia regionalne systemu operacyjnego. Jeśli nie można określić tego ustawienia regionalnego, `EN-US` jest ono używane.<br /><br /> W przypadku określenia ustawień regionalnych, które nie są prawidłowe, komunikat o błędzie jest rejestrowany w dzienniku zdarzeń.|
|/e|Nie|Podnosi poziom Menedżera zawartości pomocy do naszemu kontu administracyjnych, jeśli bieżący użytkownik ma poświadczenia administracyjne.|
|/sourceURI|Nie|Określa adres URL, z którego zainstalowano zawartość (interfejs API usługi) lub ścieżkę do pliku instalacyjnego zawartości (. msha). Adres URL może wskazywać na grupę produktów (węzeł najwyższego poziomu) lub do książek produktu (węzeł poziomu liścia) w punkcie końcowym stylu programu Visual Studio 2010. Nie musisz zawierać ukośnika (/) na końcu adresu URL. Jeśli dołączysz końcowy ukośnik, będzie on odpowiednio obsługiwany.<br /><br /> Komunikat o błędzie jest rejestrowany w dzienniku zdarzeń, jeśli określisz plik, który nie został znaleziony, jest nieprawidłowy lub niedostępny lub jeśli połączenie z Internetem nie jest dostępne lub jest przerywane w trakcie zarządzania zawartością.|
|/vendor|Nie|Określa dostawcę zawartości produktu, który zostanie usunięty (na przykład `Microsoft` ). Domyślnym argumentem tego przełącznika jest Microsoft.|
|/productName|Nie|Określa nazwę produktu dla ksiąg, które zostaną usunięte. Nazwa produktu jest identyfikowana w plikach HelpContentSetup. msha lub books.html, które zostały dostarczone z zawartością. Książki można usuwać tylko z jednego produktu jednocześnie. Aby usunąć książki z wielu produktów, należy wykonać wiele instalacji.|
|/booklist|Nie|Określa nazwy książek, które mają być zarządzane, rozdzielone spacjami. Wartości muszą być zgodne z nazwami książek wymienionymi na nośniku instalacyjnym programu.<br /><br /> Jeśli ten argument nie zostanie określony, wszystkie zalecane książki dla określonego produktu w/sourceURI zostaną zainstalowane, jeśli źródło instalacji jest w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] formacie.<br /><br /> Jeśli nazwa książki zawiera jedną lub więcej spacji, należy ująć ją w podwójne cudzysłowy ("), aby lista została odpowiednio ograniczona.<br /><br /> Komunikaty o błędach będą rejestrowane w przypadku określenia/sourceURI, który jest nieprawidłowy lub nieosiągalny.|
|/skuId.|Nie|Określa jednostkę magazynową (SKU) produktu ze źródła instalacji i filtruje książki, które identyfikuje przełącznik/SourceURI.|
|/membership|Nie|-   **Minimum**— instaluje minimalny zestaw zawartości pomocy w oparciu o jednostkę SKU określoną za pomocą przełącznika/skuId.. Mapowanie między jednostką SKU a zestawem zawartości jest uwidocznione w interfejsie API usługi.<br />-   **Zalecane**— instaluje zestaw zalecanych książek dla jednostki SKU określonej przy użyciu argumentu/skuId.. Źródłem instalacji jest interfejs API usługi lub. MSHA.<br />-   **Pełne**— instaluje cały zbiór książek dla jednostki SKU określonej przy użyciu argumentu/skuId.. Źródłem instalacji jest interfejs API usługi lub. MSHA.|
|/locationpath|Nie|Określa folder domyślny dla lokalnej zawartości pomocy. Tego przełącznika należy używać tylko w celu instalowania lub przenoszenia zawartości. W przypadku określenia tego przełącznika należy również określić przełącznik/Silent.|
|/silent|Nie|Instaluje lub usuwa zawartość pomocy bez monitowania użytkownika ani wyświetlania żadnego interfejsu użytkownika, łącznie z ikoną w obszarze powiadomień o stanie. Dane wyjściowe są rejestrowane w pliku w katalogu% Temp%. **Ważne:**  Aby zainstalować zawartość dyskretnie, należy użyć cyfrowo podpisanych plików CAB, nie plików. mshc.|
|/launchingApp|Nie|Definiuje kontekst aplikacji i katalogu, gdy Podgląd pomocy jest uruchamiany bez aplikacji nadrzędnej. Argumenty dla tego przełącznika to *NazwaFirmy*, *ProductName*i *versionNumber* (na przykład `/launchingApp Microsoft,VisualStudio,11.0` ).<br /><br /> Jest to wymagane do zainstalowania zawartości przy użyciu parametru/Silent ".|
|/wait *s*|Nie|Wstrzymuje operacje instalowania, odinstalowywania i odświeżania. Jeśli operacja jest już w toku dla wykazu, proces będzie oczekiwać na podaną liczbę sekund, aby kontynuować. Aby czekać w nieskończoność, użyj wartości 0.|
|/?|Nie|Wyświetla listę przełączników i ich opisów dla narzędzia wiersza polecenia dla Menedżera zawartości pomocy.|

### <a name="exit-codes"></a>Kody zakończenia
 Po uruchomieniu narzędzia wiersza polecenia dla Menedżera zawartości pomocy w trybie dyskretnym zwraca następujące kody zakończenia:

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 – (Signals that the update didn't run because another was in progress.)

```

## <a name="see-also"></a>Zobacz też
 [Podręcznik administratora programu Help Viewer](../ide/help-viewer-administrator-guide.md) [Help Content Manager Overrides](../ide/help-content-manager-overrides.md)
