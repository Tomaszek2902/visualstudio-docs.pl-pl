---
title: Instalowanie zawartości lokalnej i zarządzanie nią | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 569254c9df668c7755116f37a819fe65a3ecaa59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670458"
---
# <a name="install-and-manage-local-content"></a>Instalowanie zawartości lokalnej i zarządzanie nią
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą Podgląd Pomocy firmy Microsoft można dodawać, usuwać, aktualizować i przenosić zawartość pomocy, która jest zainstalowana na komputerze, aby dopasować się do potrzeb związanych z programowaniem oprogramowania.

 Aby zarządzać zawartością na komputerze lokalnym, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Ponadto nie można zarządzać zawartością lokalną, jeśli pracujesz w środowisku przedsiębiorstwa, ponieważ Administratorzy systemu mogą podejmować te decyzje w organizacji. Więcej informacji można znaleźć w [podręczniku administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md).

## <a name="changing-the-content-installation-source"></a>Zmiana źródła instalacji zawartości
 Domyślnie podgląd pomocy instaluje zawartość przy użyciu usługi online firmy Microsoft jako źródła. Zazwyczaj nie należy zmieniać źródła zawartości, chyba że Pracujesz w środowisku przedsiębiorstwa, dla którego administrator systemu już zainstalował zawartość w innej lokalizacji.

#### <a name="to-change-the-content-installation-source"></a>Aby zmienić źródło instalacji zawartości

1. Na karcie **Zarządzanie zawartością** wybierz przycisk opcji **dysk** .

    > [!NOTE]
    > Opcja **dysk** nie będzie dostępna, jeśli administrator uniemożliwił zmodyfikowanie źródła instalacji zawartości. Więcej informacji można znaleźć w [podręczniku administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md).

2. Wykonaj jedną z następujących czynności:

    - Wprowadź ścieżkę do pliku. msha lub adres URL punktu końcowego usługi.

    - Wybierz przycisk Przeglądaj (**...**), aby przejść do pliku MSHA.

    - Z listy wybierz pozycję, która była ostatnio używana.

## <a name="download-and-install-content-locally"></a>Pobierz i zainstaluj zawartość lokalnie
 Jeśli pobierasz i instalujesz zawartość na komputerze lokalnym, możesz wyświetlić tematy bez połączenia z Internetem.

> [!IMPORTANT]
> Aby zainstalować zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.

 Jeśli środowisko IDE programu Visual Studio jest ustawione na język inny niż angielski, można zainstalować zawartość w języku angielskim, zlokalizowaną zawartość lub obie te funkcje. Jednak żadna zawartość nie zostanie wyświetlona, jeśli zostanie zainstalowana tylko wersja angielskojęzyczna, a pole wyboru **Uwzględnij angielską zawartość na wszystkich kartach nawigacji i żądania F1** w oknie dialogowym **Opcje podglądu** zostanie wyczyszczone.

#### <a name="to-download-and-install-content"></a>Aby pobrać i zainstalować zawartość

1. Wybierz kartę **Zarządzanie zawartością** .

2. Z listy zawartość wybierz link **Dodaj** obok książki lub książek, które chcesz pobrać i zainstalować.

     Książka zostanie dodana do listy **oczekujące zmiany** , a szacowany rozmiar określonej książki lub książek zostanie wyświetlony poniżej tej listy. Niektóre książki udostępniają tematy, ale łączny rozmiar pobierania wielu książek może być mniejszy niż wynik dodawania wszystkich określonych książek.

3. Wybierz przycisk **Aktualizuj** .

     Określona książka lub książki są instalowane wraz z wszelkimi aktualizacjami książek, które już znajdują się na komputerze. Czasy instalacji różnią się, ale postęp można przeglądać na pasku stanu.

## <a name="removing-local-content"></a>Usuwanie zawartości lokalnej
 Możesz zaoszczędzić miejsce na dysku, usuwając niechcianą zawartość z komputera.

> [!IMPORTANT]
> Musisz mieć uprawnienia administracyjne, aby usunąć zawartość.

 Nie zostanie wyświetlona żadna zawartość, jeśli środowisko IDE programu Visual Studio jest ustawione na język inny niż angielski, zostanie usunięta zlokalizowana zawartość, a pole wyboru **Uwzględnij zawartość w języku angielskim na wszystkich kartach nawigacji i żądania F1** w oknie dialogowym **Opcje podglądu** jest wyczyszczone.

#### <a name="to-remove-content"></a>Aby usunąć zawartość

1. Wybierz kartę **Zarządzanie zawartością** .

2. Z listy zawartość wybierz łącze **Usuń** obok książki lub książek, które chcesz usunąć.

     Książka zostanie dodana do listy **oczekujące zmiany** .

3. Wybierz przycisk **Aktualizuj** .

     Określona książka lub książki są usuwane z komputera.

## <a name="updating-local-content"></a>Aktualizowanie zawartości lokalnej
 Pasek stanu wskazuje, kiedy są dostępne aktualizacje zainstalowanej zawartości.

> [!IMPORTANT]
> Jeśli chcesz, aby Podgląd pomocy automatycznie sprawdzał dostępność aktualizacji online, należy otworzyć okno dialogowe **Opcje podglądu** , a następnie zaznaczyć pole wyboru **Przejdź do trybu online, aby sprawdzić dostępność aktualizacji zawartości** .

#### <a name="to-update-local-content"></a>Aby zaktualizować zawartość lokalną

- W prawym dolnym rogu paska stanu wybierz link **kliknij tutaj, aby pobrać teraz** .

  Czasy aktualizacji mogą się różnić, ale na pasku stanu można wyświetlić postęp aktualizacji.

## <a name="moving-local-content"></a>Przeniesienie zawartości lokalnej
 Możesz zaoszczędzić miejsce na dysku, przenosząc zainstalowaną zawartość z komputera lokalnego do udziału sieciowego lub na inną partycję na komputerze lokalnym.

> [!IMPORTANT]
> Aby przenieść zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.

#### <a name="to-move-local-content"></a>Aby przenieść zawartość lokalną

1. Na karcie **Zarządzanie zawartością** wybierz przycisk **Przenieś** w obszarze Ścieżka do **magazynu lokalnego**.

     Zostanie otwarte okno dialogowe **przenoszenie zawartości** .

2. W polu tekstowym **do** wprowadź inną lokalizację zawartości, a następnie wybierz przycisk **OK** .

3. Wybierz przycisk **Zamknij** , gdy zawartość została przeniesiona.

## <a name="see-also"></a>Zobacz też
 [Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)
