---
title: Widok wskaźników instrukcji (IP) — dane próbkowania pamięci platformy .NET
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6f02c2cea714b6c9688efff217ed546490f61764
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809953"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Widok wskaźników instrukcji (IP) — dane próbkowania pamięci platformy .NET
Widok adresy IP w obszarze Alokacja pamięci platformy .NET dane, które zostały zebrane przy użyciu metody próbkowania zawiera instrukcje dotyczące zestawu, które przydzieliły pamięć podczas przebiegu profilowania. Kolumny widoku są również wyświetlane według rozmiaru i liczby przydziałów.

 Wyświetlane są tylko wartości wykluczane.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres początkowy funkcji.|
|**Początek linii źródłowej**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Koniec linii źródłowej**|Numer wiersza końcowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Końcowy znak źródłowy**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Adres instrukcji**|Adres instrukcji.|
|**Alokacje wyłączne**|Całkowita liczba obiektów, które zostały utworzone przez instrukcję.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które zostały przydzielone przez instrukcję.|
|**Bajty wyłączne**|Liczba bajtów pamięci przydzielonej w ramach uruchomienia profilowania, które zostały przydzielone przez instrukcję.|
|**% Bajtów wyłącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonej w ramach uruchomienia profilowania, która została przypisana przez instrukcję.|

## <a name="see-also"></a>Zobacz też
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
