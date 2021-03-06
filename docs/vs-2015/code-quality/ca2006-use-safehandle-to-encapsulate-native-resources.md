---
title: 'CA2006: Użyj elementu SafeHandle do hermetyzacji zasobów natywnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fdf3ff02c86a878e9c955d2b3b92879870700efa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521150"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategoria|Microsoft. niezawodność|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Kod zarządzany używa <xref:System.IntPtr> do uzyskiwania dostępu do zasobów natywnych.

## <a name="rule-description"></a>Opis reguły
 Użycie `IntPtr` w kodzie zarządzanym może wskazywać na potencjalny problem z zabezpieczeniami i niezawodnością. Wszystkie zastosowania programu `IntPtr` muszą zostać zweryfikowane w celu ustalenia, czy <xref:System.Runtime.InteropServices.SafeHandle> w jego miejscu wymagane jest użycie lub Podobna technologia. Występują problemy `IntPtr` , jeśli reprezentuje jakiś zasób natywny, taki jak pamięć, dojście do pliku lub gniazdo, że kod zarządzany jest traktowany jako własny. Jeśli zarządzany kod jest właścicielem zasobu, musi również zwolnić natywne skojarzone z nim zasoby, ponieważ nie spowoduje to powstania wycieku zasobów.

 W takich scenariuszach istnieją również problemy z zabezpieczeniami lub niezawodnością, jeśli dostęp wielowątkowy jest dozwolony do i w sposób umożliwiający `IntPtr` zwolnienie zasobu reprezentowanego przez program `IntPtr` . Te problemy obejmują odtwarzanie `IntPtr` wartości w wydaniu zasobów podczas jednoczesnego używania zasobu w innym wątku. Może to spowodować sytuacje wyścigu, w których jeden wątek może odczytywać lub zapisywać dane skojarzone z niewłaściwym zasobem. Na przykład, jeśli typ przechowuje dojście systemu operacyjnego jako `IntPtr` i umożliwia użytkownikom wywoływanie zarówno **zamknięcia** , jak i innej metody, która używa tego uchwytu jednocześnie i bez pewnego rodzaju synchronizacji, kod ma problem z odtwarzaniem obsługi.

 Ten problem z odtwarzaniem obsłudze może spowodować uszkodzenie danych i często lukę w zabezpieczeniach. `SafeHandle` i jej klasy równorzędnej <xref:System.Runtime.InteropServices.CriticalHandle> zapewniają mechanizm hermetyzowania natywnego uchwytu do zasobu, co pozwala uniknąć takich problemów z wątkami. Ponadto można użyć `SafeHandle` klasy i jej elementów równorzędnych `CriticalHandle` do innych problemów związanych z wątkami, na przykład w celu starannej kontroli okresu istnienia zarządzanych obiektów, które zawierają kopię natywnego uchwytu w przypadku wywołań metod natywnych. W takiej sytuacji często można usunąć wywołania do `GC.KeepAlive` . Narzuty wydajnościowe Thay naliczane podczas korzystania z `SafeHandle` i, w mniejszym stopniu, `CriticalHandle` , często można je zmniejszyć poprzez staranne projektowanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Konwertuj `IntPtr` użycie na `SafeHandle` , aby bezpiecznie zarządzać dostępem do zasobów natywnych. Przykłady można znaleźć w <xref:System.Runtime.InteropServices.SafeHandle> temacie Reference.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie należy pomijać tego ostrzeżenia.

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable>
