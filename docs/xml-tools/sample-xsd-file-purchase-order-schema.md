---
title: 'Przykładowy plik XSD: Schemat zamówienia zakupu'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d841b75b58dc977b5141dce0b8c7275e4a3ced8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592571"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>Przykładowy plik XSD: schemat zamówienia zakupu

Następujący plik XSD jest używany w różnych przykładach w dokumentacji projektanta schematu XSD. Ten plik jest schematem zamówienia zakupu.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
          elementFormDefault="qualified">
  <xsd:element name='comment' type='xsd:string'/>

  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>

  <xsd:complexType name='USAddress'>
    <xsd:annotation>
      <xsd:documentation>
        Purchase order schema for Example.Microsoft.com.
      </xsd:documentation>
    </xsd:annotation>
    <xsd:sequence>
      <xsd:element name='name'   type='xsd:string'/>
      <xsd:element name='street' type='xsd:string'/>
      <xsd:element name='city'   type='xsd:string'/>
      <xsd:element name='state'  type='xsd:string'/>
      <xsd:element name='zip'    type='xsd:decimal'/>
    </xsd:sequence>
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>
  </xsd:complexType>

  <xsd:simpleType name='SKU'>
    <xsd:restriction base='xsd:string'>
      <xsd:pattern value='\d{3}\w{3}'/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:complexType name='Items'>
    <xsd:sequence>
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name='productName' type='xsd:string'/>
            <xsd:element name='quantity'>
              <xsd:simpleType>
                <xsd:restriction base='xsd:positiveInteger'>
                  <xsd:minInclusive value='1'/>
                  <xsd:maxExclusive value='100'/>
                </xsd:restriction>
              </xsd:simpleType>
            </xsd:element>
            <xsd:element name='USPrice'  type='xsd:decimal'/>
            <xsd:element ref='tns:comment'/>
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>
          </xsd:sequence>
          <xsd:attribute name='partNum' type='tns:SKU'/>
        </xsd:complexType>
      </xsd:element>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name='PurchaseOrderType'>
    <xsd:sequence>
      <xsd:element name='shipTo' type='tns:USAddress'/>
      <xsd:element name='billTo' type='tns:USAddress'/>
      <xsd:element ref='tns:comment' minOccurs='0'/>
      <xsd:element name='items'  type='tns:Items'/>
    </xsd:sequence>
    <xsd:attribute name='orderDate' type='xsd:date'/>
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>
  </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w tym dokumencie są fikcyjne. Żadne powiązania z rzeczywistymi firmami, organizacjami, produktami, nazwami domen, adresami e-mail, logo, osobami, miejscami lub zdarzeniami nie są zamierzone ani wywnioskowane.
