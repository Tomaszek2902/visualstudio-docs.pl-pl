---
title: 'IDebugGenericParamField:: ConstraintCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ConstraintCount
- IDebugGenericParamField::ConstraintCount
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d539e0f94fd8c1251e2addfb93c0dd2d2b54396
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180817"
---
# <a name="idebuggenericparamfieldconstraintcount"></a>IDebugGenericParamField::ConstraintCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca liczbę ograniczeń, które są skojarzone z tym parametrem ogólnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT ConstraintCount(  
   ULONG32* pcConst  
);  
```  
  
```csharp  
int ConstraintCount(  
   ref uint pcConst  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcConst`  
 [in. out] Liczba ograniczeń, które są skojarzone z tym polem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę dla obiektu **CDebugGenericParamFieldType** , który uwidacznia Interfejs [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<IMetaDataImport2> pMetadata2;  
    HCORENUM hEnum = 0;  
    ULONG cConst = 0;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );  
  
    IfFalseGo(pcConst, E_INVALIDARG );  
    *pcConst = 0;  
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );  
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );  
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,  
              m_tokParam,  
              NULL,  
              0,  
              &cConst) );  
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );  
    pMetadata->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    *pcConst = cConst;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
