---
title: Kontrolowanie koloru, stylu linii i innych właściwości kształtu
description: Zawiera informacje o kontrolce właściwości kształtu, takie jak kolor i styl linii.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 759c7def23cf8ac0df33a75d25eb5bcbcf44b209
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100430"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Kontrolowanie koloru, stylu linii i innych właściwości kształtu

Niektóre właściwości kształtu, takie jak kolor mogą być "uwidocznione". Oznacza to, że właściwości mogą być połączone z właściwością domeny kształtu. Inne osoby muszą być kontrolowane bezpośrednio.

## <a name="exposing-a-property"></a>Uwidacznianie właściwości
 Niektóre właściwości kształtu, takie jak kolor, można połączyć z wartością właściwości domeny.

 W definicji DSL wybierz kształt, łącznik lub klasę diagramu. W menu po kliknięciu prawym przyciskiem myszy wybierz pozycję **Dodaj uwidocznione**, a następnie wybierz odpowiednią właściwość, taką jak kolor wypełnienia.

 Kształt ma teraz właściwość domeny, którą można ustawić w kodzie programu lub jako użytkownik.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamiczne aktualizowanie uwidocznionej właściwości
 Zazwyczaj chcesz uczynić uwidocznioną Właściwość zależną od innej właściwości. Na przykład możesz chcieć, aby kształt wyłączał kolor czerwony, gdy określona właściwość domeny jest mniejsza od zera. Aby utworzyć Tę zależność, Utwórz [regułę](../modeling/rules-propagate-changes-within-the-model.md). Na przykład:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```