---
title: Opcje i strony opcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4512867f636e2362aa28d52c5af28bf8eb9697f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851147"
---
# <a name="options-and-options-pages"></a>Opcje i strony opcji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kliknięcie przycisku **Opcje** w menu **Narzędzia** powoduje otwarcie okna dialogowego **Opcje** . Opcje w tym oknie dialogowym są określane zbiorczo jako strony opcji. Kontrolka drzewa w okienku nawigacji zawiera kategorie opcji, a każda kategoria zawiera strony opcji. Po wybraniu strony opcje są wyświetlane w okienku po prawej stronie. Te strony umożliwiają zmianę wartości opcji, które określają stan pakietu VSPackage.  
  
## <a name="support-for-options-pages"></a>Obsługa stron opcji  
 <xref:Microsoft.VisualStudio.Shell.Package>Klasa zapewnia obsługę tworzenia stron opcji i kategorii opcji. <xref:Microsoft.VisualStudio.Shell.DialogPage>Klasa implementuje stronę opcji.  
  
 Domyślna implementacja programu <xref:Microsoft.VisualStudio.Shell.DialogPage> oferuje jego właściwości publiczne użytkownikowi w ogólnej siatce właściwości. To zachowanie można dostosować, zastępując różne metody na stronie w celu utworzenia strony opcji niestandardowych, która ma własny interfejs użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie strony opcji](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Klasa implementuje <xref:Microsoft.VisualStudio.Shell.IProfileManager> , która zapewnia trwałość dla stron opcji, a także dla ustawień użytkownika. Domyślne implementacje <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> metod i są <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> utrwalane zmiany właściwości w sekcji użytkownika rejestru, jeśli właściwość może być konwertowana na i z ciągu.  
  
## <a name="options-page-registry-path"></a>Strona opcji Ścieżka rejestru  
 Domyślnie ścieżka rejestru właściwości zarządzanych przez stronę opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , słowo typu DialogPage i nazwę typu klasy strony opcji. Na przykład Klasa strony opcji może być zdefiniowana w następujący sposób.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Jeśli <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> jest HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0Exp, wówczas nazwa właściwości i pary wartości są podkluczami HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0Exp\DialogPage\Company.optionsPage.OptionsPageGeneral.  
  
 Ścieżka rejestru samej strony opcji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , słowo, ToolsOptionsPages oraz kategorię i nazwę strony opcji. Na przykład, jeśli strona Opcje niestandardowe zawiera kategorię, moje strony opcji i <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> jest HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp, a następnie strona Opcje ma klucz rejestru, HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio\8.0Exp\ToolsOptionsPages\My opcji Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Narzędzia/Opcje strony — atrybuty i układ  
 Ten <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut określa grupowanie stron opcji niestandardowych w kategorii w drzewie nawigacji okna dialogowego **Opcje** . Ten <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut kojarzy stronę opcji z pakietu VSPackage, która dostarcza interfejs. Rozważmy następujący fragment kodu:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Deklaruje, że pakiet webpackage udostępnia dwie strony opcji, OptionsPageGeneral i OptionsPageCustom. W oknie dialogowym **Opcje** obie strony opcji są wyświetlane w kategorii **Moje** opcje jako **Ogólne** i **niestandardowe**odpowiednio.  
  
## <a name="option-attributes-and-layout"></a>Atrybuty i układ opcji  
 Interfejs użytkownika, który zawiera strona określa wygląd opcji na stronie opcji niestandardowych. Układ, etykietowanie i opis opcji na stronie opcji ogólnych są określane przez następujące atrybuty:  
  
- <xref:System.ComponentModel.CategoryAttribute> Określa kategorię opcji.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Określa nazwę wyświetlaną opcji.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Określa opis opcji.  
  
  > [!NOTE]
  > Równoważne atrybuty, SRCategory, LocDisplayName i SRDescription, służą do lokalizowania zasobów ciągów i są zdefiniowane w [próbce projektu zarządzanego](https://msdn.com/vsx).  
  
  Rozważmy następujący fragment kodu:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Opcja OptionInteger jest wyświetlana na stronie Opcje jako **Liczba całkowita** w kategorii **My Options** . Jeśli opcja jest zaznaczona, w polu Opis zostanie wyświetlona opcja Opis, **My Integer**.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Dostęp do stron opcji z innego pakietu VSPackage  
 Pakietu VSPackage, który hostuje i zarządza stroną opcji można programistycznie uzyskać dostęp z innego pakietu VSPackage przy użyciu modelu automatyzacji. Na przykład w poniższym kodzie pakietu VSPackage jest zarejestrowana jako hostowanie strony opcji.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Poniższy fragment kodu pobiera wartość OptionInteger z MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Gdy <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atrybut rejestruje stronę opcji, strona jest zarejestrowana w kluczu AutomationProperties, jeśli `SupportsAutomation` argumentem atrybutu jest `true` . Usługa Automation analizuje ten wpis rejestru, aby znaleźć skojarzone pakietu VSPackage, a następnie usługa Automation uzyskuje dostęp do właściwości za pomocą strony Opcje hostowane, w tym przypadku strony Moje siatki.  
  
 Ścieżka rejestru właściwości automatyzacji jest określana przez połączenie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , słowo, AutomationProperties oraz kategorię i nazwę strony opcji. Na przykład, jeśli strona opcji zawiera kategorię my Category, nazwa strony My Grid, a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp, a następnie właściwość Automation ma klucz rejestru HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio\8.0Exp\AutomationProperties\My Category\My.  
  
> [!NOTE]
> Nazwa kanoniczna, Strona Category.My Grid, jest wartością podklucza nazwy tego klucza.
