---
title: Moduły wyliczające | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204565"
---
# <a name="enumerators"></a>Modułów wyliczających
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta sekcja zawiera listę typów danych modułu wyliczającego w interfejsie API Plug-in kontroli źródła, które musi znać Wtyczka kontroli źródła.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kod polecenia](../extensibility/command-code-enumerator.md)  
 Wylicza opcje funkcji [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
 [Wiadomość](../extensibility/message-enumerator.md)  
 Wylicza flagi używane dla wywołania zwrotnego drukowania, [lpTextOutProc](../extensibility/lptextoutproc.md).  
  
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)  
 Zawiera nazwane wartości stałe, które określają stan pliku w ramach kontroli źródła.  
  
 [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)  
 Zawiera nazwane wartości stałe, które określają stan katalogu pod kontrolą źródła.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiuje zestaw SDK wtyczki kontroli źródła i opisuje uwzględnione zasoby.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Monituje użytkownika o opcje zaawansowane dla danego polecenia.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Bada listę plików do ich bieżącego stanu. Ponadto program używa `pfnPopulate` funkcji do powiadamiania wywołującego, gdy plik jest niezgodny z kryteriami dla `nCommand` .  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Opisuje funkcję wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) do wyświetlania komunikatów z wtyczki kontroli źródła za pośrednictwem IDE.  
  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)  
 Zawiera kompletną listę wszystkich elementów w interfejsie API dodatku plug-in kontroli źródła.
