---
title: 'Obszar testowy 4: Zaewidencjonuj | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 738b2608d5afa188cad38d92ed613307d2919ca0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155961"
---
# <a name="test-area-4-check-in"></a>Obszar testowy 4: ewidencjonowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten obszar testowania wtyczki kontroli źródła obejmuje wysyłanie zaktualizowanych elementów do magazynu wersji za pomocą polecenia **Zaewidencjonuj** .  
  
## <a name="command-menu-access"></a>Dostęp do menu poleceń  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]W przypadku przypadków testowych używane są następujące ścieżki menu zintegrowanego środowiska deweloperskiego.  
  
##### <a name="check-in"></a>Zamelduj się:  
 **Plik**, **Kontrola źródła**, **ewidencjonowanie**.  
  
 **Plik**, **Zaewidencjonuj**.  
  
 Menu skrótów, **Zaewidencjonuj**.  
  
## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie  
  
- Projekty i pliki dodane do rozwiązania lub projektu pod kontrolą źródła są wyświetlane w oknie dialogowym **ewidencjonowanie** i w oknie **Oczekujące zaewidencjonowania** .  
  
- Po zaewidencjonowaniu dodane elementy są wyświetlane w kontroli źródła.  
  
- Po zaewidencjonowaniu zaktualizowane elementy są prawidłowo zgodne z wersją w sklepie.  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniższe przypadki testowe dotyczą obszaru testowego zaewidencjonowania.  
  
### <a name="case-4a-modified-items"></a>Przypadek 4a: zmodyfikowane elementy  
 Opisuje użycie akcji zaewidencjonowania w celu zaktualizowania pliku w ramach kontroli źródła, który został zmodyfikowany.  
  
|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|  
|------------|----------------|--------------------------------|  
|Modyfikuj plik tekstowy, który został wyewidencjonowany, Zaewidencjonuj tylko plik (okno dialogowe**Zaewidencjonuj** )|1. Utwórz nowy projekt z plikiem tekstowym.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj i zmodyfikuj plik tekstowy.<br />4. Zaewidencjonuj przy użyciu okna dialogowego ewidencjonowanie (**plik**, **Kontrola źródła**, **ewidencjonowanie**).|Typowe oczekiwane zachowanie.|  
|Zmodyfikuj plik tekstowy, który został wyewidencjonowany, Zaewidencjonuj tylko plik (**oczekujące okno zaewidencjonowania** )|1. Utwórz nowy projekt z plikiem tekstowym.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Wyewidencjonuj i zmodyfikuj plik tekstowy.<br />4. Zaewidencjonuj przy użyciu okna **Oczekujące zaewidencjonowania** .|Typowe oczekiwane zachowanie.|  
  
### <a name="case-4b-adding-files"></a>Przypadek 4B: Dodawanie plików  
 Podczas dodawania pliku do projektu lub elementu do rozwiązania, należy również zmienić projekt lub rozwiązanie. W rezultacie plik nadrzędny jest również wyewidencjonowany i musi być zaewidencjonowany, aby ukończyć Dodawanie.  
  
|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|  
|------------|----------------|--------------------------------|  
|Dodaj plik tekstowy i Zaewidencjonuj wszystko (**Zaewidencjonuj** )|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik tekstowy do projektu.<br />4. Zaakceptuj wyewidencjonowanie projektu, jeśli zostanie wyświetlony monit.<br />5. Wybierz rozwiązanie w **Eksplorator rozwiązań**.<br />6. Zaewidencjonuj z okna dialogowego **Zaewidencjonuj** .|Typowe oczekiwane zachowanie.|  
|Dodaj plik tekstowy i Zaewidencjonuj wszystko (**oczekujące okno zaewidencjonowania** )|1. Utwórz nowy projekt.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj plik tekstowy do projektu.<br />4. Zaakceptuj wyewidencjonowanie projektu, jeśli zostanie wyświetlony monit.<br />5. Sprawdź rozwiązanie w oknie **Oczekujące zaewidencjonowania** .|Typowe oczekiwane zachowanie|  
  
### <a name="case-4c-adding-projects"></a>Przypadek 4C: Dodawanie projektów  
 W przypadku dodawania projektu do rozwiązania, rozwiązanie musi być również zmienione. W ten sposób plik rozwiązania jest również wyewidencjonowany i należy go zaewidencjonować, aby ukończyć Dodawanie.  
  
|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|  
|------------|----------------|--------------------------------|  
|Dodaj projekt do pustego rozwiązania w obszarze kontroli źródła (okno dialogowe**ewidencjonowanie** )|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt.<br />4. Zaakceptuj Wyewidencjonuj rozwiązanie, jeśli zostanie wyświetlony monit.<br />5. Zaewidencjonuj z okna dialogowego **Zaewidencjonuj** .|Typowe oczekiwane zachowanie.|  
|Dodaj projekt do pustego rozwiązania w obszarze kontroli źródła (okno**oczekujące na zaewidencjonowania** )|1. Utwórz puste rozwiązanie.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Dodaj nowy projekt.<br />4. Zaakceptuj Wyewidencjonuj rozwiązanie, jeśli zostanie wyświetlony monit.<br />5. Sprawdź rozwiązanie w oknie **Oczekujące zaewidencjonowania** .|Typowe oczekiwane zachowanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
