---
title: Określanie lokalizacji pliku pakietu VSPackage w usłudze VS Shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0662bfe22b4c78bb754bbac2fbfdd281a4a7bce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832949"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] musi być w stanie zlokalizować bibliotekę DLL zestawu, aby załadować pakietu VSPackage. Można go zlokalizować na różne sposoby, zgodnie z opisem w poniższej tabeli.  
  
|Metoda|Opis|  
|------------|-----------------|  
|Użyj klucza rejestru CodeBase.|Klucz CodeBase może służyć do kierowania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zestawu pakietu VSPackage z dowolnej w pełni kwalifikowanej ścieżki pliku. Wartością klucza powinna być ścieżka do pliku DLL. Jest to najlepszy sposób na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] załadowanie zestawu pakietów. Ta technika jest czasami nazywana techniką "bazowa baza kodu/prywatny katalog instalacji". Podczas rejestracji wartość bazowej bazy danych jest przenoszona do klas atrybutów rejestracji za pomocą wystąpienia <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> typu.|  
|Umieść bibliotekę DLL w katalogu **PrivateAssemblies** .|Umieść zestaw w podkatalogu **PrivateAssemblies** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] katalogu. Zestawy znajdujące się w **PrivateAssemblies** są wykrywane automatycznie, ale nie są widoczne w oknie dialogowym **Dodaj odwołania** . Różnica między **PrivateAssemblies** i **PublicAssemblies** polega na tym, że zestawy w **PublicAssemblies** są wyliczane w oknie dialogowym **Dodaj odwołania** . Jeśli nie zostanie użyta technika "bazowa baza/katalog instalacji prywatnej", należy zainstalować program w katalogu **PrivateAssemblies** .|  
|Użyj zestawu o silnej nazwie i klucza rejestru zestawu.|Za pomocą klucza zestawu można jawnie skierować [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do załadowania silnie nazwanego zestawu pakietu VSPackage. Wartość klucza powinna być silną nazwą zestawu.|  
|Umieść bibliotekę DLL w katalogu **PublicAssemblies** .|Na koniec zestaw można również umieścić w podkatalogu **PublicAssemblies** . Zestawy znajdujące się w **PublicAssemblies** są wykrywane automatycznie i pojawią się w oknie dialogowym **Dodaj odwołania** w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .<br /><br /> Zestawy pakietu VSPackage powinny być umieszczane w katalogu **PublicAssemblies** , jeśli zawierają składniki zarządzane, które mają być ponownie używane przez innych deweloperów pakietu VSPackage. Większość zestawów nie spełnia tego kryterium.|  
  
> [!NOTE]
> Używaj podpisanych zestawów o silnych nazwach dla wszystkich zestawów zależnych. Te zestawy należy również zainstalować we własnym katalogu lub w globalnej pamięci podręcznej zestawów (GAC). Chroni przed konfliktami z zestawami, które mają taką samą nazwę pliku podstawowego, jak powiązanie słabej nazwy.
