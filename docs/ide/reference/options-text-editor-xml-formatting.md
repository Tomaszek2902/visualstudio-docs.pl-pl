---
title: Opcje, Edytor tekstu, XML, formatowanie
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568142"
---
# <a name="options-text-editor-xml-formatting"></a>Opcje, Edytor tekstu, XML, formatowanie

Na stronie opcje **formatowania** można określić sposób formatowania elementów i atrybutów w dokumentach XML. Aby uzyskać dostęp do opcji formatowania XML, wybierz opcje **Narzędzia**  >  **Options**  >  **Edytor tekstu**  >  **XML**, a następnie wybierz **Formatowanie**.

## <a name="attributes"></a>Atrybuty

**Zachowaj ręczne formatowanie atrybutów**

Nie należy formatować atrybutów. Jest to ustawienie domyślne.

> [!NOTE]
> Jeśli atrybuty są w wielu wierszach, Edytor Wetnij każdy wiersz atrybutów, aby dopasować wcięcia elementu nadrzędnego.

**Wyrównaj atrybuty każdy w osobnym wierszu**

Wyrównaj drugą i kolejne atrybuty w pionie, aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu wyrównania atrybutów:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Autoformatowanie

**Przy wklejaniu ze schowka**

Umożliwia sformatowanie tekstu XML wklejonego ze schowka.

**Po zakończeniu tagu końcowego**

Ponownie sformatuj element po zakończeniu znacznika końcowego.

## <a name="mixed-content"></a>Zawartość mieszana

**Domyślnie sformatuj zawartość mieszaną.**

Spróbuj ponownie sformatować zawartość mieszaną, z wyjątkiem sytuacji, w której zawartość znajduje się w `xml:space="preserve"` zakresie. Jest to ustawienie domyślne.

Jeśli element zawiera mieszankę tekstu i znaczników, zawartość jest traktowana jako zawartość mieszana. Poniżej znajduje się przykład elementu z zawartością mieszaną.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz też

- [Opcje XML — różne](options-text-editor-xml-miscellaneous.md)
- [Narzędzia XML w Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
