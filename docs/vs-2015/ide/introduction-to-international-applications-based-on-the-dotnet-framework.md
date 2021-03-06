---
title: Wprowadzenie do aplikacji międzynarodowych opartych na .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0d57cee8591196d12e51e58fb0e5e6a4a2cdf94a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848376"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Wprowadzenie do aplikacji międzynarodowych na podstawie .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie istnieją [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dwie części do tworzenia aplikacji gotowej do użycia na całym świecie: globalizacja, proces projektowania aplikacji, które można dostosować do różnych kultur i lokalizacji, proces tłumaczenia zasobów dla określonej kultury. Aby uzyskać ogólne informacje na temat projektowania aplikacji dla odbiorców międzynarodowych, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do użytku](https://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Model lokalizacji składa się z głównego zestawu, który zawiera zarówno kod aplikacji, jak i zasoby rezerwowe — ciągi, obrazy i inne obiekty w języku, w którym aplikacja została pierwotnie opracowana. Każda zlokalizowana aplikacja będzie miała zestawy satelickie lub zestawy, które zawierają tylko zlokalizowane zasoby. Ponieważ główny zestaw zawsze zawiera zasoby rezerwowe, jeśli zasób nie zostanie znaleziony w zlokalizowanym zestawie satelickim, <xref:System.Resources.ResourceManager> próba załadowania go w sposób hierarchiczny, a ostatecznie powraca do zasobu w zestawie głównym. System rezerwowy zasobów został szczegółowo wyjaśniony w [hierarchicznej organizacji zasobów na potrzeby lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md).

 Jednym z zasobów lokalizacji, które należy wziąć pod uwagę przy użyciu, jest słownik dla wszystkich zlokalizowanych produktów firmy Microsoft. Ten plik CSV zawiera ponad 12 000 terminów w języku angielskim oraz tłumaczenia warunków w maksymalnie 59 różnych językach. Słownik jest dostępny do pobrania na stronie internetowej [Tłumaczenia terminologii firmy Microsoft](https://msdn.microsoft.com/goglobal/bb688105.aspx) .

 System projektu dla aplikacji Windows Forms może generować pliki zasobów zarówno dla rezerwy, jak i każdej żądanej dodatkowej kultury interfejsu użytkownika. Rezerwowy plik zasobów jest wbudowany w zestaw główny, a pliki zasobów specyficzne dla kultury są następnie wbudowane w zestawy satelickie, po jednym dla każdej kultury interfejsu użytkownika. Podczas kompilowania projektu pliki zasobów są kompilowane z formatu XML programu Visual Studio (. resx) do pośredniego formatu binarnego (Resources), które są następnie osadzone w zestawach satelickich.

 System projektu dla obu Windows Forms i formularzy sieci Web umożliwia tworzenie plików zasobów przy użyciu szablonu pliku zasobów zestawu, uzyskiwanie dostępu do zasobów i kompilowanie projektu. Zestawy satelickie zostaną utworzone wraz z zestawem głównym.

 Po uruchomieniu zlokalizowanej aplikacji jego wygląd jest określany przez dwie wartości kulturowe. ( *Kultura* to zbiór informacji o preferencjach użytkownika związanych z językiem, środowiskiem i konwencjami kulturowymi użytkownika). Ustawienie kultury interfejsu użytkownika określa, które zasoby zostaną załadowane. Kultura interfejsu użytkownika jest ustawiana jako `UICulture` w Web.config pliki i dyrektywy dotyczące stron oraz <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> w kodzie Visual Basic lub Visual C#. Ustawienie kultura określa formatowanie wartości, takich jak daty, liczby, waluta i tak dalej. Kultura jest ustawiana jako " `Culture` Web.config pliki i dyrektywy strony" <xref:System.Globalization.CultureInfo.CurrentCulture%2A> w kodzie Visual Basic lub Visual C#.

## <a name="see-also"></a>Zobacz też
 <xref:System.Globalization> <xref:System.Resources>
 [Globalizacja i lokalizowanie zabezpieczeń aplikacji](../ide/globalizing-and-localizing-applications.md) [i zlokalizowanych zestawów satelickich](../ide/security-and-localized-satellite-assemblies.md)
