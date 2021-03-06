---
title: 'Instrukcje: Tworzenie zestawu reguł zasad zabezpieczeń (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849316"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Instrukcje: Tworzenie zestawu reguł działania PolicyActivity (starsza wersja)
W tym temacie opisano sposób tworzenia zestawu reguł działania zasad przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] , która jest przeznaczona dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Po przeciągnięciu elementu działania **zasad** z **przybornika** do powierzchni projektowej przepływu pracy należy wybrać istniejącą regułę lub utworzyć nowy zestaw reguł dla działania [zasad](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) . Można wybrać istniejący zestaw reguł przy użyciu okna [dialogowego Wybieranie zestawu reguł (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md) i utworzyć zestawy reguł przy użyciu [okna dialogowego Edytor zestawu reguł (starsza wersja)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Okno dialogowe [Edytor zestawu reguł (starsze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) można otworzyć bezpośrednio przez dwukrotne kliknięcie aktywności [zasad](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) , która znajduje się na powierzchni projektowej przepływu pracy.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Aby wybrać lub utworzyć zestaw reguł dla działania zasad zabezpieczeń

1. Kliknij prawym przyciskiem myszy [zasadę zasad](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx), a następnie kliknij pozycję **Właściwości** , aby otworzyć okno **Właściwości** .

2. Kliknij właściwość **RuleSetReference** .

3. Wykonaj jedną z następujących czynności:

    - Kliknij wielokropek **RuleSetReference** **[...]**, a następnie wybierz istniejący zestaw reguł w oknie [dialogowym Wybieranie zestawu reguł (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Następnie przejdź do kroku 10.

         -lub-

    - Wpisz nazwę zestawu reguł. Kliknij wielokropek **RuleSetReference** **[...]**, a następnie wybierz pozycję **Edytuj** w [oknie dialogowym Wybieranie zestawu reguł (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         -lub-

    - Wpisz nazwę zestawu reguł. Rozwiń Właściwość **RuleSetReference** i wybierz wielokropek **[...]** we właściwości definicji zestawu **reguł** .

         Zostanie otwarte okno [dialogowe Edytor zestawu reguł (starsza wersja)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) .

4. W oknie [dialogowym Edytor zestawu reguł (starsza wersja)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)kliknij przycisk **Dodaj regułę** , aby dodać nową regułę do zestawu reguł.

5. Wprowadź **nazwę**, **priorytet**i właściwości ponownej **oceny** lub Zachowaj wartości domyślne.

6. Wprowadź tekst dla **warunku**.

7. Wprowadź tekst **akcji then** i **else**.

8. Kliknij ponownie przycisk **Dodaj regułę** , aby dodać kolejną regułę.

9. Po zakończeniu kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) Okno [dialogowe wybór zestawu reguł (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md) okno dialogowe [Edytor zestawu reguł](../workflow-designer/rule-set-editor-dialog-box-legacy.md) (starsza wersja) [, przy użyciu działania zasad](https://msdn2.microsoft.com/library/bb675229.aspx) [starszego przepływu pracy](../workflow-designer/legacy-workflow-activities.md)
