---
title: Debuguj kod przykładowy HTML i CSS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 460419d976211747c44f156a5821b88b75aa2e6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745546"
---
# <a name="debug-html-and-css-sample-code"></a>Debugowanie przykładowego kodu HTML i CSS

Kod w tym temacie to przykładowy plik do [szybkiego startu: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md). Błędy występujące w projekcie w szybkim samouczku są rozwiązane w tej wersji kodu.

## <a name="sample-code"></a>Przykładowy kod
Następujący kod HTML jest używany w \<body> tagu w przewodniku Szybki Start.

```html
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"
         style="display:none">
    <div class="fixedItem" >
        <img src="#" data-win-bind="src: flipImg" />
    </div>
</div>
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
</div>
```

Poniższy kod CSS pokazuje Dodatki wprowadzone do default. css.

```css
#fView {
    background-color:#0094ff;
    height: 500px;
    margin: 25px;
}
```

Poniższy przykład kodu pokazuje kompletny kod JavaScript w default.js. Odwołania do przestrzeni nazw WinJS dla tego kodu znajdują się w pliku default.html szablonu.

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
        myData[x] = { flipImg: "/images/logo.png" }
    };

    var pages = new WinJS.Binding.List(myData, { proxy: true });

    app.onactivated = function (args) {
        if (args.detail.kind === activation.ActivationKind.launch) {
            if (args.detail.previousExecutionState !==
            activation.ApplicationExecutionState.terminated) {
                // TODO: . . .
            } else {
                // TODO: . . .
            }
            args.setPromise(WinJS.UI.processAll());

            updateImages();
        }
    };

    function updateImages() {

        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    };

    app.oncheckpoint = function (args) {
    };

    app.start();

    var publicMembers = {
        items: pages
    };

    WinJS.Namespace.define("Data", publicMembers);

})();
```

## <a name="see-also"></a>Zobacz też
- [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)
