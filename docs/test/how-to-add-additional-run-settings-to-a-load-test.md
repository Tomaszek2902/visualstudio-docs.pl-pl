---
title: Dodaj Parametry uruchomieniowe do testu obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2f62b3e9797e411138590fc15b0fe872920d203
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288458"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Instrukcje: Dodawanie dodatkowych parametrów uruchomieniowych do testu obciążenia

Parametry uruchomieniowe testu obciążeniowego decydują o różnych innych ustawieniach. Należą do nich ustawienia czasu trwania testu, poziomu szczegółowości zbierania wyników oraz zbiorów liczników, z których dane mają być zbierane podczas przebiegów testowych. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Początkowe ustawienie uruchomieniowe jest dodawane do testu obciążenia podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**.

Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. W danej sesji można używać tylko jednego parametru uruchomieniowego. Przed rozpoczęciem testu należy go też wskazać jako aktywny.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Aby dodać kolejny parametr uruchomieniowy

1. Otwórz test obciążenia.

2. Obowiązkowe Rozwiń folder **Parametry uruchomieniowe** .

3. Kliknij prawym przyciskiem myszy folder **Parametry uruchomieniowe** i wybierz polecenie **Dodaj Parametry uruchomieniowe**.

     Nowe ustawienie uruchomieniowe zostanie dodane do folderu **Parametry uruchomieniowe** .

4. W menu **Widok** wybierz **okno właściwości**.

     Zostanie wyświetlone okno **Właściwości** z właściwościami wybranego ustawienia uruchomieniowego.

5. W oknie **Właściwości** , użyj pola tekstowego dla właściwości **Nazwa** , aby nadać nowemu ustawieniu uruchomieniowemu nazwę opisującą intencję ustawienia przebiegu (na przykład, **Uruchom ustawienie: pięć minut**).

6. Użyj okna **Właściwości** , aby zmienić ustawienia uruchomieniowe. Na przykład zmień czas trwania przebiegu na **00:05:00** , aby uruchomić test przez pięć minut.

    > [!NOTE]
    > Aby zapoznać się z pełną listą właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

     Teraz można określić, że dodany parametr uruchomieniowy ma być używany, ustawiając mu status aktywności. Aby uzyskać więcej informacji, zobacz [How to: SELECT The Run aktywny setting for a test Load](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
