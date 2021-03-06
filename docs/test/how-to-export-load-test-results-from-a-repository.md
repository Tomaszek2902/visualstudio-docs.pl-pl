---
title: Eksportuj Wyniki testów ładowania
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9b20915d5c320ff8db4da849d20267355c26590
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287756"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Instrukcje: Eksportowanie wyników testu obciążenia z repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyniki testów ładowania](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Można zarządzać wynikami testów obciążenia z Edytor testu obciążeniowego przy użyciu okna dialogowego **Otwórz i zarządzaj wyniki testów ładowania** . Można otwierać, importować, eksportować i usuwać wyniki testów obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Aby wyeksportować wyniki z repozytorium

1. Z projektu testu wydajności i obciążenia sieci Web Otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz pozycję **Otwórz i Zarządzaj wynikami**.

     Zostanie wyświetlone okno dialogowe **Otwórz i zarządzaj wyniki testów ładowania** .

3. W polu **Wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz **\<Local - No controller>** , aby uzyskać dostęp do wyników przechowywanych lokalnie.

4. W polu **Pokaż wyniki dla następującego testu obciążenia**wybierz test obciążenia, którego wyniki chcesz wyświetlić. Wybierz **\<Show results for all tests>** , aby wyświetlić wszystkie wyniki dla wszystkich testów.

     Jeśli wyniki testów obciążenia są dostępne, pojawiają się na liście **wyników testu obciążenia** . Kolumny są typu **Time**, **Duration**, **User**, **wynik**, **test**i **Description**. **Test** zawiera nazwę testu, a **Opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu. W kolumnie **Opis** są wyświetlane krótkie opisy, które zostały wprowadzone w **komentarzach analizy** dla tego wyniku testu.

5. Na liście **wyników testu obciążenia** wybierz wynik. Możesz użyć klawisza **SHIFT** , klawisza **Ctrl** lub obu, aby zaznaczyć więcej niż jeden wynik i wyeksportować je do pojedynczego pliku.

6. Wybierz pozycję **Eksportuj**.

     Zostanie wyświetlone okno dialogowe **eksportuj wyniki testów ładowania** .

7. W polu **Nazwa pliku** wpisz nazwę, a następnie wybierz pozycję **Zapisz**.

     Wyniki zostaną wyeksportowane do pliku archiwum.

    > [!NOTE]
    > Okno dialogowe **otwieranie i zarządzanie ładowaniem wyniki testów** pozostaje otwarte po wyświetleniu wyników.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie wynikami testów obciążenia w repozytorium Wyniki testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Instrukcje: usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)
