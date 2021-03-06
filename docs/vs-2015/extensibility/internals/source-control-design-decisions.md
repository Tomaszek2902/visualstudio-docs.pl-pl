---
title: Decyzje dotyczące projektowania kontroli źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89d125dc52340e8528ee9692d5de00784632e6f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187897"
---
# <a name="source-control-design-decisions"></a>Decyzje projektowe dotyczące kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas implementowania kontroli źródła należy wziąć pod uwagę następujące decyzje projektowe.  
  
## <a name="will-information-be-shared-or-private"></a>Czy informacje będą udostępniane lub prywatne?  
 Najważniejsze podejmowane decyzje projektowe to informacje, które można udostępniać i jakie są prywatne. Na przykład lista plików dla projektu jest udostępniona, ale w ramach tej listy plików niektórzy użytkownicy mogą chcieć mieć prywatne pliki. Ustawienia kompilatora są udostępniane, ale projekt startowy jest ogólnie prywatny. Ustawienia są wyłącznie udostępniane, udostępniane z przesłonięciem lub czysto prywatnie. Po zaprojektowaniu elementy prywatne, takie jak pliki opcji użytkownika rozwiązania (. suo), nie są sprawdzane [!INCLUDE[vsvss](../../includes/vsvss-md.md)] . Pamiętaj, aby przechowywać informacje prywatne w plikach prywatnych, takich jak plik. suo, lub określony prywatny plik, na przykład plik. csproj. User dla Visual C# lub plik. vbproj. User dla Visual Basic.  
  
 Ta decyzja nie jest cała włącznie i może być wykonywana na poszczególnych elementach.  
  
## <a name="will-the-project-include-special-files"></a>Czy projekt będzie zawierać specjalne pliki?  
 Inną ważną decyzją projektową jest to, czy struktura projektu używa specjalnych plików. Pliki specjalne to ukryte pliki, które podstawą pliki, które są widoczne w Eksplorator rozwiązań i w oknach dialogowych ewidencjonowanie i wyewidencjonowywania. Jeśli używasz specjalnych plików, postępuj zgodnie z następującymi wskazówkami:  
  
1. Nie należy kojarzyć specjalnych plików z węzłem głównym projektu — to znaczy, z samym plikiem projektu. Plik projektu musi być pojedynczym plikiem.  
  
2. Po dodaniu lub usunięciu plików specjalnych lub zmianie ich nazwy w projekcie odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> zdarzenia muszą być wywoływane z zestawem flag, który wskazuje, że pliki są plikami specjalnymi. Zdarzenia te są wywoływane przez środowisko w odpowiedzi na projekt wywołujący odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody.  
  
3. Gdy projekt lub Edytor wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> plik, pliki specjalne skojarzone z tym plikiem nie są automatycznie wyewidencjonowywane. Przekaż pliki specjalne w programie wraz z plikiem nadrzędnym. Środowisko wykrywa relację między wszystkimi plikami, które są przesyłane, i odpowiednio ukrywa pliki specjalne w interfejsie użytkownika wyewidencjonowywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
