---
title: Tworzenie pakietu VSPackage kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709189"
---
# <a name="create-a-source-control-vspackage"></a>Tworzenie pakietu VSPackage kontroli źródła
Ta dokumentacja zawiera linki do omówienia architektury pakietu kontroli źródła zintegrowanego z programem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , interfejs API, który jest zdefiniowany przez interfejsy do zaimplementowania i usługi, które mają być używane, oraz przykład, który ilustruje prostą implementację pakietu kontroli źródła.

 Za pomocą pakietu VSPackage kontroli źródła można utworzyć ścieżkę głębokiej integracji dla kontroli źródła w celu integracji z programem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Umożliwia pakietowi ominięcie domyślnego interfejsu użytkownika kontroli źródła hostowanego przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , odpowiadanie na żądania kontroli źródła od systemu projektu i współdziałanie ze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składnikami, takimi jak **Eksplorator rozwiązań**. Program umożliwia [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partnerom Tworzenie pakietu VSPackage, który można zintegrować z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usługą przy użyciu modelu usług.

## <a name="in-this-section"></a>W tej sekcji
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Omawia pakiet kontroli źródła, który jest bardziej zaawansowaną alternatywą dla wtyczki kontroli źródła na potrzeby implementowania funkcji kontroli źródła w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Architektura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Przedstawia diagram i objaśnia składniki pakietu kontroli źródła.

- [Funkcje](../../extensibility/internals/source-control-vspackage-features.md)

 Opisuje różne funkcje pakietu kontroli źródła.

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Opisuje strukturę pakietu VSPackage, którą musi zaimplementować pakiet kontroli źródła na potrzeby głębokiej integracji.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)

 W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła, która dostarcza funkcje kontroli źródła w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsie użytkownika kontroli źródła (UI).

- [Kontrola źródła](../../extensibility/internals/source-control.md)

 W tym artykule omówiono opcje implementowania kontroli źródła jako funkcji zintegrowanej programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
