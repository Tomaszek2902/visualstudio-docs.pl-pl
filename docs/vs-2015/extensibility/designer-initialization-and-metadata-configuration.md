---
title: Inicjowanie projektanta i konfiguracja metadanych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703071"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicjowanie projektanta i konfiguracja metadanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manipulowanie metadanymi i atrybutami filtrów skojarzonymi z projektantem lub składnikiem projektanta zapewnia mechanizm do definiowania, które narzędzia są używane przez określony Projektant do obsługi różnych <xref:System.Type> obiektów (takich jak struktury danych, klasy lub jednostki graficzne), gdy Projektant jest dostępny, a także sposób, w jaki środowisko IDE programu Visual Studio jest skonfigurowane do obsługi projektanta (na przykład **Toolbox** dostępność kategorii lub karty).  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Zapewnia kilka mechanizmów ułatwiających kontrolę inicjalizacji składnika projektanta lub projektanta oraz manipulowanie jego metadanymi przez pakietu VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicjowanie informacji o metadanych i konfiguracji  
 Ponieważ są one ładowane na żądanie, pakietów VSPackage mogły nie zostać załadowane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisko przed wystąpieniem projektanta. W związku z tym pakietów VSPackage nie może używać standardowego mechanizmu do konfigurowania projektanta lub składnika projektanta podczas tworzenia, który ma obsłużyć <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> zdarzenie. Zamiast tego pakietu VSPackage implementuje wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfejsu i rejestruje się w celu zapewnienia dostosowań, nazywanych rozszerzeniami powierzchni projektowania.  
  
### <a name="customizing-initialization"></a>Dostosowywanie inicjalizacji  
 Dostosowywanie projektanta, składnika lub powierzchni projektanta obejmuje:  
  
1. Modyfikowanie metadanych projektanta i efektywne Zmienianie sposobu <xref:System.Type> uzyskiwania dostępu do określonego lub konwersji.  
  
     Zwykle jest to realizowane za pomocą <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> mechanizmów lub.  
  
     Na przykład po <xref:System.Windows.Forms> zainicjowaniu projektantów opartych na czasie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisko modyfikuje <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> obiekty dla obiektów używanych z projektantem, aby używać Menedżera zasobów do uzyskiwania map bitowych, a nie systemu plików.  
  
2. Integracja ze środowiskiem, na przykład przez subskrybowanie zdarzeń lub uzyskiwanie informacji o konfiguracji projektu. Możesz uzyskać informacje o konfiguracji projektu i subskrybować zdarzenia, uzyskując <xref:System.ComponentModel.Design.ITypeResolutionService> interfejs.  
  
3. Modyfikacja środowiska użytkownika przez aktywowanie odpowiednich kategorii **przybornika** lub ograniczenie możliwości projektowania przez zastosowanie instancji <xref:System.ComponentModel.ToolboxItemFilterAttribute> klasy do projektanta.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicjowanie projektanta przez pakietu VSPackage  
 Pakietu VSPackage powinien obsługiwać inicjalizację projektanta przez:  
  
1. Tworzenie obiektu implementującego <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> klasę.  
  
   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Klasy nigdy nie należy implementować na tym samym obiekcie co <xref:Microsoft.VisualStudio.Shell.Package> Klasa.  
  
2. Zarejestruj klasę implementującą <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obsługę rozszerzeń projektanta pakietu VSPackage przez zastosowanie wystąpień  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do klasy zapewniającej implementację pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Za każdym razem, gdy tworzony jest dowolny składnik projektanta lub projektanta, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisko:  
  
3. Uzyskuje dostęp do każdego zarejestrowanego dostawcy rozszerzeń powierzchni projektowej.  
  
4. Tworzy wystąpienia i Inicjuje wystąpienie każdego obiektu dostawcy rozszerzenia powierzchni projektowej <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
5. Wywołuje każdą metodę lub metodę dostawcy rozszerzenia powierzchni projektowej <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (zgodnie z potrzebami).  
  
   Podczas implementowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu jako elementu członkowskiego pakietu VSPackage należy zrozumieć, że:  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Środowisko nie zapewnia żadnej kontroli nad tym, jakie metadane lub inne ustawienia konfiguracji `DesignSurfaceExtension` są modyfikowane przez określonego dostawcę. Istnieje możliwość, że co najmniej dwóch `DesignSurfaceExtension` dostawców modyfikuje tę samą funkcję projektanta w sprzecznych sposobach wraz z ostateczną modyfikacją. Nie jest to nieokreślone, która modyfikacja została ostatnio zastosowana.  
  
7. Można jawnie ograniczyć implementację <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu do określonych projektantów, stosując wystąpienia <xref:System.ComponentModel.ToolboxItemFilterAttribute> dla tej implementacji. Aby uzyskać więcej informacji na temat filtrowania elementów **przybornika** , zobacz <xref:System.ComponentModel.ToolboxItemFilterAttribute> i <xref:System.ComponentModel.ToolboxItemFilterType> .  
  
## <a name="additional-metadata-provisioning"></a>Dodatkowe Inicjowanie obsługi metadanych  
 Pakietu VSPackage może zmienić konfigurację projektanta lub składnika projektanta innego niż w czasie projektowania.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Klasa może być używana programowo lub zastosowana do pakietu VSPackage.  
  
 Wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> klasy służy do modyfikowania metadanych składników utworzonych na powierzchni projektowej. Na przykład jedna może zastąpić domyślną przeglądarkę właściwości używaną przez <xref:System.Windows.Forms.CommonDialog> obiekty z niestandardową przeglądarką właściwości.  
  
 Modyfikacje dostarczone przez wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> zastosowane do implementacji elementu pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> mogą mieć jeden z dwóch zakresów:  
  
- Global--dla wszystkich nowych wystąpień danego składnika  
  
- Lokalne — dotyczy tylko wystąpienia składnika utworzonego na powierzchni projektowej udostępnionej przez bieżącą pakietu VSPackage.  
  
  `IsGlobal`Właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienia zastosowana do implementacji elementu pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> określa ten zakres.  
  
  Zastosowanie atrybutu do implementacji <xref:Microsoft.VisualStudio.Shell.Package> z <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> właściwością <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> obiektu ustawionego na `true` , jak poniżej, zmienia przeglądarkę dla całego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiska:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Jeśli Flaga globalna została ustawiona na `false` , wówczas zmiana metadanych jest lokalna dla bieżącego projektanta obsługiwanego przez bieżącą pakietu VSPackage:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> W danym momencie powierzchnia projektowania obsługuje tylko Tworzenie składników, a w związku z tym tylko składniki mogą mieć lokalne metadane. W powyższym przykładzie podjęto próbę zmodyfikowania właściwości, takiej jak `Color` właściwość obiektu. Jeśli `false` została przeniesiona do flagi globalnej, `CustomBrowser` nigdy nie zostanie wyświetlona, ponieważ Projektant nigdy nie tworzy wystąpienia `Color` . Ustawienie flagi globalnej na `false` jest przydatne w przypadku składników, takich jak kontrolki, czasomierze i okna dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Rozszerzona pomoc techniczna czasu projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
