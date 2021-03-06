---
title: Udostępnianie plików systemu Windows zostało skonfigurowane... | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dbb1f3493ead985ac946331fdbff7933b6d604
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851674"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Błąd: Udostępnianie plików systemu Windows zostało skonfigurowano...
Udostępnianie plików systemu Windows zostało skonfigurowane w taki sposób, aby nawiązać połączenie z komputerem zdalnym przy użyciu innej nazwy użytkownika. Jest to niezgodne z debugowaniem zdalnym

 Bieżąca konfiguracja udostępniania plików jest skonfigurowana do nawiązywania połączenia z komputerem zdalnym przy użyciu innej nazwy użytkownika. Debugowanie zdalne nie jest możliwe w tym scenariuszu.

 Aby naprawić ten błąd, zaloguj się na komputerze przy użyciu innej nazwy konta lub Zmień udostępnianie plików, tak aby używało nazwy konta, które jest debugowane.

 Jeśli chcesz nawiązać połączenie z komputerem zdalnym przy użyciu tej nazwy użytkownika, musisz najpierw odłączyć się od komputera zdalnego.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Zaloguj się na komputerze lokalnym, z którego chcesz debugować, używając innej nazwy konta.

     —lub—

     . Odłącz od komputera zdalnego, a następnie skonfiguruj ponownie udostępnianie plików, aby połączyć się z inną maszyną przy użyciu nazwy konta:

    1. W menu **Start** wskaż polecenie **akcesoria**, a następnie kliknij pozycję **wiersz polecenia**.

    2. W wierszu polecenia systemu Windows wpisz:

         `net use /delete computer_name`

    3. Zmień ustawienia udostępniania plików przy użyciu dowolnej metody udokumentowanej w pomocy systemu Windows.