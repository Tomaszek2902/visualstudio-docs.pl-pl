---
title: Oczekiwano znaku ")" w wyrażeniu regularnym (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29b25b5ab48ffe0a9a9dfafa9e60d66913c5e25e
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861891"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „)" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia przechwycenia wyrażenia regularnego, potwierdzenia lub grupy, ale nie zawiera nawiasu zamykającego. Nawiasy mają kilka celów w wyrażeniach regularnych. Przede wszystkim są one używane do przechwytywania wyrażeń podrzędnych, określania zatwierdzeń lub grupowania wzorców ze sobą, aby elementy mogły być traktowane jako pojedyncze jednostki przez *, +,? itd.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias zamykający.  
  
    > [!NOTE]
    > Jeśli chcesz dopasować pojedyncze nawiasy, należy wyjść z ukośnikiem odwrotnym \\ (-tak, aby nie był interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt wyrażenia regularnego](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Składnia wyrażenia regularnego (JavaScript)](/previous-versions/1400241x(v=vs.100))