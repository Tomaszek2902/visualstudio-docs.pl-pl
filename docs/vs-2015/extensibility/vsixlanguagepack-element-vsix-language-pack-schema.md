---
title: VSIXLanguagePack — element (schemat pakietu Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284353"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack — element (schemat pakietu językowego VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wymagany. Dostarcza element główny pakietu językowego VSIX. Pakiet językowy VSIX zawiera zlokalizowane informacje o instalacji pakietu VSIX.  
  
## <a name="syntax"></a>Składnia  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`xmlns`|Przestrzeń nazw XML, w której jest zdefiniowany schemat pakietu Language Pack VSIX.|  
  
## <a name="xmlns-attribute"></a>Atrybut xmlns  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Wymagany. Lokalizacja pliku, który definiuje schemat pakietów językowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[LocalizedName, element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Wymagany. Zlokalizowana nazwa rozszerzenia, które ma zostać zainstalowane.|  
|[LocalizedDescription, element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Wymagany. Zlokalizowany opis rozszerzenia, które ma zostać zainstalowane.|  
|[MoreInfoURL, element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcjonalny. Link do zlokalizowanych informacji o rozszerzeniu.|  
|[License, element](../extensibility/license-element-vsix-language-pack-schema.md)|Opcjonalny. Ścieżka zlokalizowanej wersji pliku licencji dla rozszerzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
## <a name="element-information"></a>Informacje o elementach  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Przestrzeń nazw    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nazwa schematu   |                 Schemat pakietu Language Pack VSIX                 |
| Plik walidacji |                VSIXLanguagePackSchema. xsd                 |
|  Może być puste   |                            Nie                             |
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pakietu językowego VSX](../extensibility/vsx-language-pack-schema-reference.md) [lokalizowania pakietów VSIX](../extensibility/localizing-vsix-packages.md) [schemat rozszerzenia VSIX schematu 1,0](/previous-versions/dd393700(v=vs.110))
