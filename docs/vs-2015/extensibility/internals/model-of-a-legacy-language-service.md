---
title: Model starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27d51df6dd11509b86e6648d59978b87d9cd8a02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157655"
---
# <a name="model-of-a-legacy-language-service"></a>Model starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługa języka definiuje elementy i funkcje dla określonego języka i służy do udostępniania edytora informacji specyficznych dla danego języka. Na przykład edytor musi znać elementy i słowa kluczowe języka w celu obsługi kolorowania składni.  
  
 Usługa języka ściśle współpracuje z buforem tekstu zarządzanym przez Edytor i widokiem zawierającym Edytor. Opcja **szybkich informacji** IntelliSense firmy Microsoft jest przykładem funkcji udostępnianej przez usługę języka.  
  
## <a name="a-minimal-language-service"></a>Minimalna usługa języka  
 Najbardziej podstawowa usługa języka zawiera dwa następujące obiekty:  
  
- *Usługa językowa* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs. Usługa językowa zawiera informacje o języku, w tym jego nazwę, rozszerzenia nazw plików, Menedżer okien kodu i kolorowanie.  
  
- *Kolor* zaimplementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs.  
  
  Poniższy rysunek koncepcyjny przedstawia model podstawowej usługi językowej.  
  
  ![Grafika modelu usługi językowej](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Model usługi języka Basic  
  
  Okno dokumentu zawiera *widok dokumentu* edytora, w tym przypadku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podstawowy edytor. Widok dokumentu i bufor tekstowy są własnością edytora. Te obiekty współpracują z programem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] za pomocą wyspecjalizowanego okna dokumentu o nazwie *okno kodu*. Okno kod jest zawarte w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekcie, który jest tworzony i kontrolowany przez IDE.  
  
  Po załadowaniu pliku z danym rozszerzeniem Edytor lokalizuje usługę języka skojarzoną z tym rozszerzeniem i przekazuje do niej okno kodu, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodę. Usługa języka zwraca *Menedżera okien kodu*, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejs.  
  
  Poniższa tabela zawiera omówienie obiektów w modelu.  
  
|Składnik|Obiekt|Funkcja|  
|---------------|------------|--------------|  
|Bufor tekstu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Strumień tekstowy do odczytu/zapisu w formacie Unicode. Użycie innych kodowań jest możliwe w przypadku tekstu.|  
|Okno kodu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Okno dokumentu, które zawiera co najmniej jeden widok tekstu. Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest w trybie interfejsu wielu dokumentów (MDI), okno kod jest elementem podrzędnym MDI.|  
|Widok tekstu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Okno, które umożliwia użytkownikowi nawigowanie i wyświetlanie tekstu przy użyciu klawiatury i myszy. Widok tekstu jest widoczny dla użytkownika jako edytor. Możesz użyć widoków tekstowych w zwykłych oknach edytora, oknie danych wyjściowych i oknie bezpośrednim. Ponadto można skonfigurować jeden lub więcej widoków tekstu w oknie kodu.|  
|Menedżer tekstu|Zarządzane przez <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługę, z którego uzyskujesz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> wskaźnik|Składnik, który przechowuje wspólne informacje udostępniane przez wszystkie opisane wcześniej składniki.|  
|Usługa języka|Zależne od implementacji; wprowadza <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Obiekt, który zapewnia Edytor z informacjami specyficznymi dla języka, takimi jak wyróżnianie składni, uzupełnianie instrukcji i nawiasy klamrowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../../extensibility/document-data-and-document-view-in-custom-editors.md)
