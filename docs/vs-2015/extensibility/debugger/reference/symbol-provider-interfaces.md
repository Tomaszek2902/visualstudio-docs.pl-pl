---
title: Interfejsy dostawcy symboli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c409175fb39207bc0e83a521577ad6d641731691
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204869"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Poniżej przedstawiono interfejsy obsługi symboli dla [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)] .  
  
## <a name="discussion"></a>Dyskusja  
 Te interfejsy są używane do obliczania zmiennych w stosie wywołań w trybie przerwania. Są one implementowane tylko dla dostawców symboli środowiska uruchomieniowego języka wspólnego (SP).  
  
|Interfejs|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|REQUIREMENT|Reprezentuje adres elementu.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|REQUIREMENT|Reprezentuje adres elementu, zapewniając dostęp do identyfikatora procesu.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|REQUIREMENT|Reprezentuje symbol tablicy lub typ tablicy.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|REQUIREMENT|Reprezentuje symbol klasy lub typ klasy.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|REQUIREMENT|Reprezentuje dostawcę symboli modelu COM+ z metodami specyficznymi dla kodu zarządzanego.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|REQUIREMENT|Reprezentuje dostawcę symboli modelu COM+ z metodami specyficznymi dla kodu zarządzanego i rozszerza **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|REQUIREMENT|Reprezentuje symbol lub typ, który jest kontenerem dla innych symboli lub typów.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|REQUIREMENT|Reprezentuje atrybut niestandardowy, który może być dołączany do symbolu.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|REQUIREMENT|Reprezentuje zapytanie dla atrybutów niestandardowych metody lub typu.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|REQUIREMENT|Zapewnia dostęp do atrybutów niestandardowych dla symbolu.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|REQUIREMENT|Interfejs podstawowy dla dowolnego typu, który można określić w czasie wykonywania.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|REQUIREMENT|Reprezentuje dynamiczne pole dla obiektu [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|REQUIREMENT|Reprezentuje typ wyliczeniowy.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Requirement|Rozszerza typy dostępnych pól w celu obsługi typów ogólnych w kodzie zarządzanym.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|REQUIREMENT|Klasa bazowa dla wszystkich pól; reprezentuje opis symbolu lub typu.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|REQUIREMENT|Reprezentuje definicję pola dla ogólnego typu kodu zarządzanego.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|REQUIREMENT|Reprezentuje wystąpienie pola dla ogólnego typu kodu zarządzanego.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|REQUIREMENT|Reprezentuje parametr dla ogólnego typu kodu zarządzanego.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|REQUIREMENT|Reprezentuje metodę.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|REQUIREMENT|Reprezentuje opcjonalny modyfikator debugowania.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|REQUIREMENT|Reprezentuje wskaźnik.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|REQUIREMENT|Reprezentuje wartość wyliczenia typu pierwotnego z interfejsu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|REQUIREMENT|Reprezentuje właściwość zarządzanej klasy kodu, którą można pobrać lub ustawić.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|REQUIREMENT|Reprezentuje dostawcę symboli, który zawiera symbole i typy.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|REQUIREMENT|Reprezentuje dostawcę symboli, który ma bezpośredni dostęp do metadanych i podstawowych interfejsów symboli.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|REQUIREMENT|Reprezentuje możliwość utworzenia pola, które reprezentuje typ.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|REQUIREMENT|Rozszerza **IDebugTypeFieldBuilder** , aby można było tworzyć typy tablic.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|REQUIREMENT|Reprezentuje kolekcję obiektów [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|REQUIREMENT|Reprezentuje kolekcję obiektów [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) .|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|REQUIREMENT|Reprezentuje kolekcję obiektów [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
