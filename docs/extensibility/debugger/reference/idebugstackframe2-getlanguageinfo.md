---
title: 'IDebugStackFrame2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cefb4bdd9d0c85311c63e6a988956301a6c2cc14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719703"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Pobiera język skojarzony z tą ramką stosu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parametry

`pbstrLanguage`\
określoną Zwraca nazwę języka implementującego metodę skojarzoną z tą ramką stosu.

`pguidLanguage`\
określoną Zwraca wartość `GUID` języka. Na [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] przykład dla języków można zwrócić następujące elementy:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Wartość zwracana

 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
