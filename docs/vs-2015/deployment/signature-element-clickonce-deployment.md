---
title: '&lt;Signature — &gt; element (wdrożenie ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db696546fdd64199753054b38fa2ac554f6a774f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295081"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature — &gt; element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera informacje niezbędne do podpisania cyfrowo tego manifestu wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Uwagi  
 Podpisywanie manifestu wdrożenia przy użyciu podpisu koperty jest opcjonalne, ale zalecane. Aby uzyskać więcej informacji o podpisywaniu plików XML, zobacz zalecenia dotyczące organizacja World Wide Web Consortium "składnia i przetwarzanie podpisu XML", opisane w temacie [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .  
  
 Jeśli chcesz podpisać manifest, należy podać skróty dla wszystkich plików. Nie można podpisać manifestu z plikami, które nie są skrótami, ponieważ użytkownicy nie mogą zweryfikować zawartości plików niebędących skrótami.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje `Signature` element w manifeście wdrożenia używanym we [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeniu.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)
