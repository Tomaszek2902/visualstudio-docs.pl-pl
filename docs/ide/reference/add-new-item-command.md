---
title: Dodaj nowy element — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38be691ae7c49ffbd6c98c9e4beb25b6ebb021b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585694"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
Dodaje nowy element rozwiązania, taki jak. htm, CSS, txt lub FRAMESET do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Opcjonalny. Ścieżka i nazwa pliku elementu, który ma zostać dodany do rozwiązania.

## <a name="switches"></a>Przełączniki
/t `templatename`\
Opcjonalny. Określa typ pliku, który ma zostać utworzony. Jeśli nie podano nazwy szablonu, plik tekstowy jest tworzony domyślnie.

Składnia/t: `templatename` argument odzwierciedla informacje znajdujące się w oknie dialogowym **Dodaj nowy element rozwiązania** . Należy wprowadzić kompletną kategorię, a następnie typ pliku, oddzielając nazwę kategorii od typu pliku przez ukośnik odwrotny ( `\` ) i otaczając cały ciąg w cudzysłowie.

Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujące polecenie dla/t: `templatename` argumentu.

```cmd
/t:"General\Style Sheet"
```

/e `editorname`\
Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w **oknie dialogowym Otwórz za pomocą**, ujętym w cudzysłów.

Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, dla argumentu/e: należy wprowadzić następujące elementy `editorname` .

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
W tym przykładzie dodano nowy element rozwiązania MyHTMLpg do bieżącego rozwiązania.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
