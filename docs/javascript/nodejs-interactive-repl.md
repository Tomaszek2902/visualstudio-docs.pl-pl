---
title: Użyj REPL środowiska Node.js
description: Program Visual Studio umożliwia wchodzenie w interakcje ze środowiskiem uruchomieniowym platformy Node.js
ms.custom: ''
ms.date: 12/04/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 7b980634a95c14413dd07649893a26b21de6f78d
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2018
ms.locfileid: "53443347"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Praca z okno interaktywne języka Node.js

Node.js Tools for Visual Studio obejmują interakcyjne okno zainstalowanego środowiska uruchomieniowego Node.js. To okno umożliwia wprowadzanie kodu w języku JavaScript i natychmiastowe wyświetlenie wyników w, a także wykonywać polecenia npm na interakcję z bieżącego projektu. Okno interaktywne jest także znana jako REPL (**R**eczytaj /**E**valuate /**P**rukuj **L**obiektowo).

## <a name="open-the-interactive-window"></a>Otwórz okno interaktywne

Okno interaktywne można otworzyć, klikając prawym przyciskiem myszy węzeł projektu środowiska Node.js w Eksploratorze rozwiązań i wybierając polecenie **Otwórz okno interaktywne języka Node.js**.

![Okno interaktywne języka node.js, w menu kontekstowym projektu](../javascript/media/interactivewindow-open-from-project.png)

Klucze skrócone domyślne, aby otworzyć okno interaktywne języka Node.js są **[CTRL] + K, N**. Ewentualnie można otworzyć okna z paska narzędzi, wybierając **widoku** > **Windows** > **okno interaktywne języka Node.js**.

## <a name="use-the-repl"></a>Użyj REPL

Po otwarciu, można wprowadzić poleceń.

![Okno interaktywne języka node.js](../javascript/media/interactivewindow.png)

Okno interaktywne zawiera kilka wbudowanych poleceń, które zaczynają się prefiksem kropka, aby odróżnić je od dowolnej funkcji JavaScript, który został zadeklarowany. Obsługiwane są następujące polecenia:

**.CLS, .clear** Czyści zawartość okna edytora, pozostawiając bez zmian historii i wykonywania kontekstu.

**.Help** Wyświetla Pomoc dotyczącą określonego polecenia lub na wszystkich dostępnych poleceń i powiązań klawiszy, jeśli nie określono.

**.info** zawiera informacje o bieżącym Node.js używanych pliku wykonywalnego.

**.npm** uruchamia polecenie npm. Jeśli rozwiązanie zawiera więcej niż jeden projekt, określ projekt docelowy za pomocą `.npm [projectname] <npm arguments>`.

**.Reset** przywraca stan początkowy, Zachowaj historię środowiska wykonawczego.

**.Save** zapisuje bieżącą sesję REPL do pliku.