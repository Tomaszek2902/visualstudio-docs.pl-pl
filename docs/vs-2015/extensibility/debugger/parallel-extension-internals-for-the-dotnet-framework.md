---
title: Wewnętrzne rozszerzenia równoległe dla .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42c472190469e7d008fa8c525f50eabfaf37053f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65680924"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tej sekcji opisano typy wewnętrzne, metody i pola klas, które ułatwiają zaimplementowanie niestandardowego debugera dla rozszerzeń równoległych do .NET Framework.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie danych <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy.  
  
 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie danych <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy.  
  
 [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie danych `System.Threading.Tasks.ContingentProperties` klasy.  
  
 [AsyncTaskMethodBuilder, struktura](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.  
  
 [AsyncTaskMethodBuilder\<TResult>, struktura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.  
  
 [AsyncVoidMethodBuilder, struktura](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
