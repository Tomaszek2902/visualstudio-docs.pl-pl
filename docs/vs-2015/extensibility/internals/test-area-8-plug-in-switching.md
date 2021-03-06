---
title: 'Obszar testowy 8: przełączanie wtyczek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90650b8b3c3432fce05b03a25033977e68f60fca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203126"
---
# <a name="test-area-8-plug-in-switching"></a>Obszar testowy 8: przełączanie wtyczki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Zintegrowane środowisko programistyczne (IDE) ma interfejs użytkownika, aby zmienić bieżącą wtyczkę kontroli źródła. Ten obszar testowy zawiera przypadki testowe dla procesu wybierania wtyczki, która ma być używana na potrzeby kontroli źródła rozwiązania.  
  
## <a name="command-menu-access"></a>Dostęp do menu poleceń  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]W przypadku przypadków testowych używane są następujące ścieżki menu zintegrowanego środowiska deweloperskiego.  
  
- Bieżąca Wtyczka kontroli źródła: **Narzędzia**  ->  **Opcje**  ->  **Source Control**  ->  **wyboru wtyczki**kontroli źródła.  
  
- Zmień powiązanie kontroli źródła: kontrola źródła **pliku**  ->  **Source Control**  ->  **zmian**kontroli źródła...  
  
## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie  
 Zmiana wtyczki kontroli źródła dla rozwiązania jest możliwa bez kończenia działania programu Visual Studio lub ponownego załadowania rozwiązania. Ponadto obecnie wtyczka do kontroli źródła jest automatycznie zmieniana na ten, który jest używany przez rozwiązanie po załadowaniu tego rozwiązania.  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej wymieniono określone przypadki testowe dla obszaru testowego przełączania wtyczki.  
  
### <a name="case-8a-automatic-change"></a>Przypadek 8a: Automatyczna zmiana  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
 Gdy użytkownik ładuje rozwiązanie, które jest pod kontrolą źródła, jest automatycznie ładowane, a odpowiednia wtyczka kontroli źródła jest wybierana jako bieżąca.  
  
|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|  
|------------|----------------|--------------------------------|  
|Automatyczna zmiana wtyczki kontroli źródła|1. Wybierz wtyczkę w obszarze Testuj jako bieżący (**Tools**  ->  **Opcje**narzędzi  ->  **Source Control**  ->  **wybór wtyczki**kontroli źródła).<br />2. Utwórz nowy projekt.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Wybierz inną wtyczkę (na przykład [!INCLUDE[vsvss](../../includes/vsvss-md.md)] ).<br />5. Zaakceptuj monit rozładowania rozwiązania.<br />6. Otwórz ponownie rozwiązanie z dysku.|Rozwiązanie jest otwarte.<br /><br /> Wtyczka poddawana testom jest bieżącą wtyczką kontroli źródła.|  
  
### <a name="case-8b-solution-based-change"></a>Przypadek 8b: zmiana oparta na rozwiązaniu  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
 Rozwiązanie może mieć zmienioną skojarzoną wtyczkę kontroli źródła.  
  
|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|  
|------------|----------------|--------------------------------|  
|Zmiana wtyczki dla rozwiązania|1. Wybierz wtyczkę w obszarze Testuj jako bieżący (**Tools**  ->  **Opcje**narzędzi  ->  **Source Control**  ->  **wybór wtyczki**kontroli źródła).<br />2. Utwórz nowy projekt i rozwiązanie.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Usuń powiązanie rozwiązania z kontroli źródła (przy użyciu okna dialogowego **Zmień kontrolę źródła** ).<br />5. Wybierz inną wtyczkę (na przykład [!INCLUDE[vsvss](../../includes/vsvss-md.md)] ).<br />6. Załaduj ponownie rozwiązanie z dysku w przypadku jego niezaładowania.<br />7. Dodaj rozwiązanie do kontroli źródła.<br />8. Usuń powiązanie rozwiązania z kontroli źródła (przy użyciu okna dialogowego **Zmień kontrolę źródła** ).<br />9. Wybierz wtyczkę ponownie w obszarze Testuj.<br />10. Załaduj ponownie rozwiązanie z dysku, jeśli zostało zwolnione.<br />11. Powiąż rozwiązanie z oryginalną lokalizacją (przy użyciu okna dialogowego **Zmień kontrolę źródła** ).|Rozwiązanie jest dodawane do kontroli źródła przy użyciu wybranej wtyczki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
