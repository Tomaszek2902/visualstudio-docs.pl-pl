---
title: Konfiguracja projektu do zarządzania wdrożeniem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429954"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurowanie projektu do zarządzania wdrożeniem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wdrożenie to czynność fizycznej przenoszenia elementów wyjściowych z procesu kompilacji do oczekiwanej lokalizacji na potrzeby debugowania i instalacji. Na przykład aplikacja sieci Web może być skompilowana na komputerze lokalnym, a następnie umieszczana na serwerze.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Program obsługuje dwa sposoby, w których projekty mogą być uwzględnione we wdrożeniu:  
  
- W ramach procesu wdrażania.  
  
- Jako Menedżer procesu wdrażania.  
  
  Przed wdrożeniem rozwiązań należy najpierw dodać projekt wdrożenia w celu skonfigurowania opcji wdrażania. Jeśli projekt wdrożenia jeszcze nie istnieje, zostanie wyświetlony monit o jego utworzenie, gdy wybierzesz opcję **Wdróż rozwiązanie** z menu **kompilacja** lub kliknij prawym przyciskiem myszy rozwiązanie. Kliknięcie przycisku **tak** spowoduje otwarcie okna dialogowego **Dodawanie nowego projektu** z wybranym projektem **Kreatora wdrażania zdalnego** .  
  
  Kreator zdalnego wdrażania monituje o typ aplikacji (Windows lub Web), grupy danych wyjściowych projektu do uwzględnienia, wszelkie dodatkowe pliki, które mają zostać uwzględnione, oraz komputer zdalny, na którym ma zostać wdrożony. Ostatnia strona kreatora wyświetla podsumowanie wybranych opcji.  
  
  Projekty, które są podmiotem procesu wdrażania, tworzą elementy wyjściowe, które muszą zostać przeniesione do alternatywnego środowiska. Te elementy wyjściowe są opisane jako parametry <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfejsu, którego głównym celem jest umożliwienie projektom grupowania danych wyjściowych. Aby uzyskać więcej informacji dotyczących implementacji programu `IVsProjectCfg2` , zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).  
  
  Projekty wdrażania, które zarządzają procesem wdrażania, włączają polecenie Wdróż i reagują, gdy to polecenie jest zaznaczone. Projekty wdrożenia implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejs do wykonania wdrożenia i wykonują wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfejsu w celu raportowania zdarzeń stanu wdrożenia.  
  
  Konfiguracje mogą określać zależności, które wpływają na operacje kompilowania lub wdrażania. Zależności kompilacji lub wdrożenia to projekty, które muszą zostać skompilowane lub wdrożone przed lub po skompilowaniu lub zakończeniu konfiguracji. Zależności kompilacji między projektami są opisane w <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfejsie i wdrażają zależności z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsem. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguracja projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
