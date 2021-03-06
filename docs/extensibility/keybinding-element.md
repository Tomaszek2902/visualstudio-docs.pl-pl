---
title: Powiązanie klawiszy — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703142"
---
# <a name="keybinding-element"></a>Powiązanie klawiszy, element
Element powiązanie klawiszy określa skróty klawiaturowe dla poleceń.

 Polecenia mogą zawierać skojarzone z nimi powiązania z pojedynczym i podwójnym kluczem. Przykładem pojedynczego powiązania klucza jest **Ctrl** + **S** dla polecenia **Zapisz** . Podwójne powiązania klawiszy wymagają dwóch kolejnych kombinacji klawiszy, aby wyzwolić polecenie. Przykładem podwójnego powiązania klawiszy jest <strong>Ctrl *+</strong> k<strong>,</strong>Ctrl <strong>+</strong> k** w celu ustawienia zakładki.

## <a name="syntax"></a>Składnia

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagany.|
|identyfikator|Wymagany.|
|edytor|Wymagany. Identyfikator GUID edytora wskazuje kontekst edycji, dla którego będzie aktywny ten skrót klawiaturowy. Globalna wartość zakresu powiązania to "guidVSStd97".|
|key1|Wymagany. Prawidłowe wartości to wszystkie typable alfanumeryczne, a także dwucyfrowe wartości szesnastkowe poprzedzone 0x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Opcjonalny. Dowolna kombinacja kombinacji **klawiszy CTRL**, **Alt**i **SHIFT** oddzielona spacją.|
|key2|Opcjonalny. Prawidłowe wartości to wszystkie typable alfanumeryczne, a także dwucyfrowe wartości szesnastkowe poprzedzone 0x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Opcjonalny. Dowolna kombinacja kombinacji **klawiszy CTRL**, **Alt**i **SHIFT** oddzielona spacją.|
|emulator|Opcjonalny.|
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny||
|Adnotacja||

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element powiązań klawiszy](../extensibility/keybindings-element.md)|Grupuje elementy powiązanie klawiszy i inne grupowania powiązań klawiszy.|

## <a name="example"></a>Przykład

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Zobacz też
- [Element powiązań klawiszy](../extensibility/keybindings-element.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
