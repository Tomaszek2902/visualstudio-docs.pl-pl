---
title: Składnia ścieżki domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ab5f080328338e40bed080ec8a4c7a85eabdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114641"
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
Definicje DSL używają składni podobnej do XPath do lokalizowania określonych elementów w modelu.

 Zwykle nie trzeba bezpośrednio korzystać z tej składni. Gdzie pojawia się w szczegółach lub okno Właściwościach DSL, możesz kliknąć strzałkę w dół i użyć edytora ścieżek. Ścieżka jest jednak wyświetlana w tym formularzu w polu po użyciu edytora.

 Ścieżka domeny ma następującą postać:

 *RelationshipName. PropertyName/! Roli*

 ![Relacja odwołania CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 Składnia przechodzi przez drzewo modelu. Na przykład Relacja domeny **CommentReferencesSubjects** na powyższej ilustracji ma rolę **podmiot** . Segment ścieżki **/! Wartość określa,** że ścieżka kończy się na elementach, do których można uzyskać dostęp za pomocą roli **podmiot** .

 Każdy segment zaczyna się od nazwy relacji domeny. Jeśli przechodzenie pochodzi z elementu do relacji, segment ścieżki zostanie wyświetlony jako *Relationship. PropertyName*. Jeśli przeskok pochodzi z linku do elementu, segment ścieżki jest wyświetlany jako *relacja/! Rolename*.

 Ukośniki oddzielają składnię ścieżki. Każdy segment ścieżki jest przeskokiem z elementu do linku (wystąpienie relacji) lub z linku do elementu. Segmenty ścieżki często pojawiają się w parach. Jeden segment ścieżki reprezentuje przeskok z elementu do linku, a następny segment reprezentuje przeskok z linku do elementu na drugim końcu. (Dowolne łącze może być również źródłem lub obiektem docelowym relacji).

 Nazwa, która jest używana dla skoku element-link, jest wartością roli `Property Name` . Nazwa użyta dla przeskoku link-element jest nazwą roli docelowej.

## <a name="see-also"></a>Zobacz też

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
