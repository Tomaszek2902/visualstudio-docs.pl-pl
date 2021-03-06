---
title: Obiekt VSTextView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690699"
---
# <a name="vstextview-object"></a>VSTextView, obiekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok tekstu to okno, które umożliwia użytkownikom wyświetlanie i edytowanie tekstu w formacie Unicode w buforze tekstu. W rzeczywistości widok jest tym, czego większość użytkowników odwołuje się jako edytor. Ponieważ widok jest oddzielony od buforu przez różne warstwy tekstu (Zawijanie wierszy, tekst konspektu itd.), widok nie musi być dokładną reprezentacją tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstu, zobacz [dostęp do widoku TheText przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 W poniższej tabeli przedstawiono interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekcie.  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji złożonych (czyli akcji, które są pogrupowane w jednej jednostce cofania/ponawiania).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Zapewnia podstawowe metody zarządzania widokiem i uzyskiwania do niego dostępu. `IVsTextView` nie jest bezpieczny wątkowo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy okienko okna i zarządza nim.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwami tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje w widoku z innego wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edycja ilustracji](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Obiekt VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
