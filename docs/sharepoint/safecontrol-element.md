---
title: SafeControl — element | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c9936054c5cc622e6f335d81d1568ebed16518f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547930"
---
# <a name="safecontrol-element"></a>SafeControl — element
  Reprezentuje kontrolkę ASPX lub składnik Web Part, który jest oznaczony jako bezpieczny dla każdego użytkownika, aby mógł uzyskać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.

## <a name="syntax"></a>Składnia

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**Zestaw**|Opcjonalny atrybut **xs: String** .<br /><br /> Nazwa zestawu, w którym jest zdefiniowana kontrolka ASPX lub składnik Web Part. Domyślnie ten atrybut używa dla nazwy zestawu parametru **$SharePoint. Project. AssemblyFullName $** . Aby uzyskać więcej informacji, zobacz [Parametry wymienne](../sharepoint/replaceable-parameters.md).|
|**Issafe**|Opcjonalny atrybut **xs: Boolean** .<br /><br /> Określa, czy formant ASPX lub część sieci Web są bezpieczne dla niezaufanych użytkowników, którzy mają do nich dostęp.|
|**IsSafeAgainstScript**|Opcjonalny atrybut **xs: Boolean** .<br /><br /> Określa, czy niezaufani użytkownicy mogą wyświetlać lub edytować właściwości kontrolki ASPX lub składnika Web Part.|
|**Nazwa**|Opcjonalny atrybut **xs: String** .<br /><br /> Nazwa tego wpisu bezpiecznego sterowania w kolekcji.|
|**Przestrzeń nazw**|Opcjonalny atrybut **xs: String** .<br /><br /> Przestrzeń nazw kontrolki ASPX lub składnika Web Part.|
|**Nazwa**|Opcjonalny atrybut **xs: String** .<br /><br /> Nazwa typu kontrolki ASPX lub części sieci Web.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[SafeControls —](../sharepoint/safecontrols-element.md)|Reprezentuje kolekcję formantów ASPX i składniki Web Part, które są wyznaczeni jako bezpieczne dla każdego użytkownika, który ma dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji o bezpiecznych kontrolkach, zobacz temat [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
