---
title: Eliminacja plików ~ SAK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708502"
---
# <a name="elimination-of-sak-files"></a>Eliminacja plików ~ SAK
W interfejsie API wtyczki kontroli źródła 1,2 pliki *~ SAK* zostały zastąpione przez flagi możliwości i nowe funkcje, które wykrywają, czy wtyczka do kontroli źródła obsługuje plik *MSSCCPRJ* i udostępnione wyewidencjonowania.

## <a name="sak-files"></a>~ Pliki SAK
Program Visual Studio .NET 2003 utworzył pliki tymczasowe poprzedzone znakiem *~ SAK*. Te pliki służą do określenia, czy wtyczka do kontroli źródła obsługuje:

- Plik *MSSCCPRJ. SCC* .

- Wiele (udostępnione) wyewidencjonowania.

W przypadku wtyczek, które obsługują zaawansowane funkcje dostępne w interfejsie API dodatku plug-in kontroli źródła 1,2, IDE może wykryć te możliwości bez tworzenia plików tymczasowych przy użyciu nowych funkcji, flag i funkcji opisanych w poniższych sekcjach.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nowe funkcje
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Jeśli wtyczka kontroli źródła obsługuje wiele (udostępnione) wyewidencjonowania, deklaruje `SCC_CAP_MULTICHECKOUT` możliwość i implementuje `SccIsMultiCheckOutEnabled` funkcję. Ta funkcja jest wywoływana za każdym razem, gdy operacja wyewidencjonowywania będzie odbywać się w dowolnym z projektów z kontrolą źródła.

 Jeśli wtyczka do kontroli źródła obsługuje tworzenie i używanie pliku *MSSCCPRJ. SCC* , deklaruje `SCC_CAP_SCCFILE` możliwość i implementuje [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Ta funkcja jest wywoływana z listą plików. Funkcja zwraca `TRUE' or 'FALSE` dla każdego pliku, aby wskazać, czy program Visual Studio ma używać pliku *MSSCCPRJ. SCC* . Jeśli wtyczka do kontroli źródła wybierze nie obsługę tych nowych funkcji i funkcji, może użyć następującego klucza rejestru, aby wyłączyć tworzenie tych plików:

 **[HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] DoNotCreateTemporaryFilesInSourceControl**  =  *DWORD: 00000001*

> [!NOTE]
> Jeśli ten klucz rejestru jest ustawiony na *wartość DWORD: 00000000*, odpowiada kluczowi nieistniejącemu, a program Visual Studio nadal próbuje utworzyć pliki tymczasowe. Jeśli jednak klucz rejestru jest ustawiony na *wartość DWORD: 00000001*, program Visual Studio nie próbuje utworzyć plików tymczasowych. Zamiast tego przyjmuje się, że wtyczka do kontroli źródła nie obsługuje pliku *MSSCCPRJ. SCC* i nie obsługuje udostępnionych wyewidencjonowania.

## <a name="see-also"></a>Zobacz też
- [Co nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
