---
title: 'Ostrzeżenie: debugowanie skryptu wyłączone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36065120dc636f0004f0e00d8b17a0059a680723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161373"
---
# <a name="warning-script-debugging-disabled"></a>Ostrzeżenie: debugowanie skryptu wyłączone
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie skryptów jest obecnie wyłączone w programie Internet Explorer  
  
 To ostrzeżenie występuje podczas próby debugowania skryptu bez włączania debugowania skryptów w programie Internet Explorer. Ze względów bezpieczeństwa program Internet Explorer domyślnie wyłącza debugowanie skryptów.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Aby włączyć debugowanie skryptów w programie Internet Explorer  
  
1. W menu **Narzędzia** programu Internet Explorer wybierz pozycję **Opcje internetowe**.  
  
2. W oknie dialogowym **Opcje internetowe** kliknij kartę **Zaawansowane** .  
  
3. Na karcie **Zaawansowane** poszukaj w oknie **Ustawienia** , **przeglądanie** kategorii.  
  
4. Wyczyść pole **Wyłącz debugowanie skryptów (Internet Explorer)**.  
  
5. Kliknij przycisk **OK**.  
  
6. Zamknij i uruchom ponownie program Internet Explorer.  
  
     Nowe ustawienia będą obowiązywać.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dołączanie do skryptu](../debugger/how-to-attach-to-script.md)
