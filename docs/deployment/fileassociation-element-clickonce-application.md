---
title: '&lt;fileAssociation, &gt; element (Aplikacja ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d3a43af5b2c7d50034cbed9d7da16e65b402f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928523"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation, &gt; element (Aplikacja ClickOnce)
Identyfikuje rozszerzenie pliku, które ma być skojarzone z aplikacją.

## <a name="syntax"></a>Składnia

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `fileAssociation`Element jest opcjonalny. Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`extension`|Wymagany. Rozszerzenie pliku, które ma być skojarzone z aplikacją.|
|`description`|Wymagany. Opis typu pliku do użycia przez powłokę.|
|`progid`|Wymagany. Nazwa, która jednoznacznie identyfikuje typ pliku.|
|`defaultIcon`|Wymagany. Określa ikonę, która ma być używana dla plików z tym rozszerzeniem. Plik ikony należy określić za pomocą [ \<file> elementu](../deployment/file-element-clickonce-application.md) w [ \<assembly> elemencie](../deployment/assembly-element-clickonce-application.md) , który zawiera ten element.|

## <a name="remarks"></a>Uwagi
 Ten element musi zawierać odwołanie do przestrzeni nazw XML do "urn: schematys-Microsoft-com: ClickOnce. v1". Jeśli `<fileAssociation>` element jest używany, musi znajdować się po `<application>` elemencie w jego [ \<assembly> elemencie](../deployment/assembly-element-clickonce-application.md)nadrzędnym.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie spowoduje zastąpienia istniejących skojarzeń plików. Jednak aplikacja ClickOnce może zastąpić rozszerzenie pliku tylko dla bieżącego użytkownika. Gdy aplikacja ClickOnce zostanie odinstalowana, ClickOnce usunie skojarzenie pliku dla użytkownika, a skojarzenie dla poszczególnych maszyn jest aktywne ponownie.

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `fileAssociation` elementy w manifeście aplikacji dla aplikacji edytora tekstu wdrożonej przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Ten przykład kodu zawiera również [ \<file> element](../deployment/file-element-clickonce-application.md) wymagany przez `defaultIcon` atrybut.

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>Zobacz też
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)