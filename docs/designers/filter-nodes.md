---
title: Węzły filtrów
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfc74287706976f96a5e565bef3da1493cd44866
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769283"
---
# <a name="filter-nodes"></a>Węzły filtrów

W projektancie programu do cieniowania węzły filtrują Przekształć dane wejściowe — na przykład, koloru lub tekstury próbki — do wartości koloru Figurative. Te wartości koloru Figurative są często używane w nierealistycznym renderowaniu lub jako składniki w innych efektach wizualizacji.

## <a name="filter-node-reference"></a>Filtruj odwołanie do węzła

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Rozmazan**|Rozmywa piksele w tekstury przy użyciu funkcji gaussowskie.<br /><br /> Możesz użyć tego, aby zredukować szczegóły koloru lub szum w teksturę.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne Texel do przetestowania.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmytego.|**Tekstura**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas rozmywania.|
|**Zmniejsz nasycenie**|Zmniejsza ilość koloru w określonym kolorze.<br /><br /> Po usunięciu koloru wartość koloru zbliża się do jego odpowiedników w skali szarości.<br /><br /> **Klawiatur**<br /><br /> `RGB`: `float3`<br /> Kolor zmniejszający nasycenie.<br /><br /> `Percent`: `float`<br /> Procent koloru do usunięcia wyrażony jako znormalizowana wartość w zakresie [0, 1].<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float3`<br /> Nasycenie koloru.|**Jaskrawość**<br /> Wagi nadawane czerwonym, zielonym i niebieskim składnikom koloru.|
|**Wykrywanie krawędzi**|Wykrywa krawędzie tekstury przy użyciu detektora krawędzi w puszkach. Piksele brzegowe są wyprowadzane jako białe. piksele inne niż brzegowe są wyprowadzane jako czarne.<br /><br /> Można jej użyć do identyfikacji krawędzi tekstury, aby można było użyć dodatkowych efektów do traktowania pikseli brzegowych.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne Texel do przetestowania.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Biały, jeśli Texel znajduje się na krawędzi; w przeciwnym razie czarny.|**Tekstura**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wykrywania krawędzi.|
|**Intensyw**|Wyostrza teksturę.<br /><br /> Możesz użyć tej funkcji, aby wyróżnić szczegółowe szczegóły tekstury.<br /><br /> **Klawiatur**<br /><br /> `UV`: `float2`<br /> Współrzędne Texel do przetestowania.<br /><br /> **Rozdzielczości**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmytego.|**Tekstura**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wyostrzania.|