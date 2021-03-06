---
title: Zapisz dziennik testu obciążenia dla niepowodzeń testów
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaef2888cecc7622a3dc589a6bab816b0c134668
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287509"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Instrukcje: Określanie, czy niepowodzenia testu są zapisywane w dziennikach testów przy użyciu Edytor testu obciążeniowego

Po utworzeniu testu obciążenia z **nowym Kreator testu obciążeniowego**można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości testu obciążenia, aby spełniały potrzeby testowania i cele. Zobacz [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md). Możesz określić, czy ma być zapisany dziennik testu, jeśli test zakończy się niepowodzeniem w teście obciążenia, zmieniając właściwość **Zapisz dziennik podczas testu** .

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Aby określić, czy dziennik testowy ma być zapisany, gdy test zakończy się niepowodzeniem w scenariuszu

1. Otwórz test obciążenia.

     Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Ustawienia uruchomieniowe** drzew testów obciążenia wybierz węzeł Parametry uruchomieniowe, dla którego chcesz określić maksymalną liczbę iteracji testu dla.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

     Kategorie i właściwości parametrów uruchomieniowych są wyświetlane w oknie **Właściwości** .

4. W obszarze **Zapisz dziennik dla niepowodzenia testu** wybierz **wartość PRAWDA** lub **Fałsz** , aby określić, czy chcesz zapisać dziennik testu w przypadku niepowodzenia testu w scenariuszu.

     Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** .

     Dane zapisane w dzienniku można wyświetlić za pomocą widoku tabele analizatora testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
