---
title: Przegląd rozwiązań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb3bb85ab172404262c147cce285cebaf756afc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831848"
---
# <a name="solutions-overview"></a>Omówienie rozwiązań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozwiązanie to grupa składająca się z jednego lub wielu projektów, które współpracują ze sobą w celu utworzenia aplikacji. Informacje o projekcie i stanie odnoszące się do rozwiązania są przechowywane w dwóch różnych plikach rozwiązania. Plik rozwiązania (. sln) jest oparty na tekście i można go umieścić pod kontrolą kodu źródłowego i udostępnić między użytkownikami. Plik opcji użytkownika rozwiązania (. suo) jest binarny. W związku z tym plik SUO nie może zostać umieszczony pod kontrolą kodu źródłowego i zawiera informacje specyficzne dla użytkownika.  
  
 Każdy pakietu VSPackage może zapisywać w dowolnym typie pliku rozwiązania. Ze względu na charakter plików istnieją dwa różne interfejsy zaimplementowane do zapisu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>Interfejs zapisuje informacje tekstowe do pliku. sln, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejs zapisuje strumienie binarne do pliku. suo.  
  
> [!NOTE]
> Projekt nie musi jawnie pisać wpisu do pliku rozwiązania; środowisko obsługuje dla projektu. W związku z tym, chyba że chcesz dodać do pliku rozwiązania dodatkową zawartość, nie musisz rejestrować pakietu VSPackage w ten sposób.  
  
 Każdy pakietu VSPackage, który obsługuje trwałość rozwiązań, używa trzech interfejsów, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejsu, który jest implementowany przez środowisko i wywoływany przez pakietu VSPackage, i `IVsPersistSolutionProps` i `IVsPersistSolutionOpts` , które są implementowane przez pakietu VSPackage. `IVsPersistSolutionOpts`Interfejs musi być zaimplementowany tylko wtedy, gdy prywatne informacje są zapisywane przez pakietu VSPackage w pliku. suo.  
  
 Po otwarciu rozwiązania zostanie wykonany następujący proces.  
  
1. Środowisko odczytuje rozwiązanie.  
  
2. Jeśli środowisko znajdzie a `CLSID` , ładuje odpowiednie pakietu VSPackage.  
  
3. W przypadku załadowania pakietu VSPackage środowisko wywołuje `QueryInterface` interfejs dla interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> , którego wymaga pakietu VSPackage.  
  
   1. Podczas odczytywania z pliku. sln środowisko wywołuje program `QueryInterface` `IVsPersistSolutionProps` .  
  
   2. Podczas odczytywania z pliku. suo środowisko wywołuje program `QueryInterface` `IVsPersistSolutionOpts` .  
  
   Szczegółowe informacje dotyczące korzystania z tych plików znajdują się w [rozwiązaniu (. Sln)](../../extensibility/internals/solution-dot-sln-file.md) Opcje użytkownika dotyczące plików i [rozwiązań (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
> Jeśli chcesz utworzyć nową konfigurację rozwiązania składającą się z dwóch konfiguracji projektów i Wyklucz trzeci z kompilacji, musisz użyć interfejsu użytkownika stron właściwości lub automatyzacji. Nie można zmienić konfiguracji Menedżera kompilacji rozwiązań i ich właściwości bezpośrednio, ale można manipulować menedżerem kompilacji rozwiązania przy użyciu `SolutionBuild` klasy z DTE w modelu automatyzacji. Aby uzyskać więcej informacji o konfigurowaniu rozwiązań, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
