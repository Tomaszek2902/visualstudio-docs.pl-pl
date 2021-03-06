---
title: Informacje o językach specyficznych dla domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b76142dfbc2dca860591bf3c3cb73c2971f56b22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655370"
---
# <a name="about-domain-specific-languages"></a>Języki specyficzne dla domeny — informacje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przeciwieństwie do języka ogólnego przeznaczenia, takiego jak C# lub UML, język specyficzny dla domeny (DSL) jest przeznaczony do ekspresowych instrukcji w konkretnym obszarze problemu lub w domenie.

 Dobrze znane językami DSL obejmują wyrażenia regularne i SQL. Każdy DSL jest znacznie lepszy niż język ogólnego przeznaczenia do opisywania operacji na ciągach tekstowych lub w bazie danych, ale znacznie gorszy dla opisywania pomysłów, które są poza własnym zakresem. Poszczególne branże mają także własne językami DSL. Na przykład w branży telekomunikacyjnej Języki opisu wywołań są szeroko używane do określenia sekwencji stanów w wywołaniu telefonicznym, a w branży podróży samolotem standardowa linia DSL jest używana do opisywania ksiąg lotów.

 Twoja firma i Twój projekt obejmują również specjalne zestawy koncepcji, które można opisać przy użyciu języka DSL. Na przykład można zdefiniować DSL dla jednej z następujących aplikacji:

- Planowanie ścieżek nawigacji w witrynie sieci Web.

- Diagramy okablowania dla składników elektronicznych.

- Sieci na taśmach i urządzeniach do obsługi bagażu dla lotniska.

  Podczas projektowania DSL, należy zdefiniować *klasy domeny* dla każdego z ważnych koncepcji w domenie, takich jak strona sieci Web, Lampa lub telefon rejestracyjny lotniska. Należy zdefiniować *relacje domeny* , takie jak Hyperlink, drut lub taśma przenośnika, aby połączyć koncepcje ze sobą.

  Użytkownicy tworzonych *modeli DSL.* Modele to *wystąpienia* DSL. Przykładowo opisują one określoną witrynę sieci Web lub okablowanie określonego urządzenia lub systemu obsługi bagażu w konkretnym porcie.

  Użytkownicy mogą wyświetlać model jako diagram lub formularz systemu Windows. Modele mogą być również wyświetlane jako XML, które są przechowywane. Podczas definiowania linii DSL definiuje się, jak wystąpienia każdej klasy domeny i relacji pojawiają się na ekranie użytkownika. Typowy DSL jest wyświetlany jako kolekcja ikon lub prostokątów połączonych za pomocą strzałek.

  Poniższy rysunek przedstawia mały model w diagramowy DSL:

  ![Model drzewa rodziny Tudor](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

## <a name="what-you-can-do-with-dsls"></a>Co możesz zrobić z językami DSL
 Typowa aplikacja DSL polega na wygenerowaniu kodu programu lub innych artefaktów. Podczas definiowania kombinacji DSL można zdefiniować *Szablony tekstowe* , które odczytają model DSL i generują pliki tekstowe.

 Można na przykład napisać szablony, które przenoszą plan lotniska i generować część oprogramowania na potrzeby obsługi bagażu, a także niektóre dokumenty użytkowników opisujące plan.

 Po zdefiniowaniu modemu DSL można go rozpowszechnić do innych użytkowników, którzy będą mogli go zainstalować na swoich komputerach. Użytkownicy programu DSL mogą tworzyć i edytować modele w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Można także definiować polecenia menu i inne narzędzia, które ułatwiają użytkownikom edycję DSL, ograniczenia sprawdzania poprawności w celu zapewnienia prawidłowego użycia DSL oraz szablonów elementów, które ułatwiają użytkownikom tworzenie nowych wystąpień. Możesz otoczyć jeden lub więcej językami DSL z narzędziami i innymi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeniami jako pakietem zintegrowanym.

 Zazwyczaj język specyficzny dla domeny jest tworzony, gdy zespół programistyczny ma pisać podobny kod dla kilku produktów. Na przykład firma wyspecjalizowana w systemach obsługi bagażu może zdefiniować Śledzenie bagażu DSL, z którego mogą generować kod dla każdej instalacji. Korzyści wynikające z używania DSL są zrozumiałe dla klientów, że kod wygenerowany z niego jest niezawodny i że system może być szybko aktualizowany w przypadku zmiany wymagań klientów.

 [!INCLUDE[dsl](../includes/dsl-md.md)] umożliwia utworzenie języka specyficznego dla domeny z własnym projektantem graficznym i własną notacją diagramu, a następnie użycie tego języka do wygenerowania odpowiedniego kodu źródłowego dla każdego projektu.

## <a name="domain-specific-development"></a>Programowanie specyficzne dla domeny
 Programowanie specyficzne dla domeny to proces identyfikowania części aplikacji, które można modelować przy użyciu języka specyficznego dla domeny, a następnie konstruowania języka i wdrażania go dla deweloperów aplikacji. Deweloperzy wykorzystują język specyficzny dla domeny do konstruowania modeli, które są specyficzne dla aplikacji, używają modeli do generowania kodu źródłowego, a następnie używają kodu źródłowego do tworzenia aplikacji.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekty graficznego programowania specyficznego dla domeny
 Graficzny język specyficzny dla domeny musi zawierać następujące funkcje:

- Notacja

- Model domeny

- Generowanie artefaktu

- Serializacja

- Integracja z programem Visual Studio

### <a name="notation"></a>Notacja
 Język specyficzny dla domeny musi mieć dostatecznie mały zestaw elementów, który można łatwo definiować i rozszerzać w celu reprezentowania konstrukcji specyficznych dla domeny. Notacja składa się z kształtów, które reprezentują elementy i łączniki, które reprezentują relacje między elementami na graficznym diagramie. W programie [!INCLUDE[dsl](../includes/dsl-md.md)] kształty mogą być rozszerzane i udoskonalane, aby reprezentować elementy języka specyficznego dla domeny.

### <a name="domain-model"></a>Model domeny
 Język specyficzny dla domeny musi łączyć zestaw elementów i relacje między nimi w spójną gramatykę. Należy również określić, czy kombinacje elementów i relacji są prawidłowe. Na przykład języki programowania zazwyczaj uniemożliwiają Dziedziczenie cykliczne, w którym jedna klasa jest pochodną drugiej klasy, a druga Klasa pochodzi od pierwszej klasy. Ograniczenia mogą również służyć do wyrażenia logiki biznesowej, na przykład jedna osoba nie może być zależna od siebie. [!INCLUDE[dsl](../includes/dsl-md.md)] używa ograniczeń do wyrażania rodzajów ograniczeń, których wymagają większość języków specyficznych dla domeny.

### <a name="artifact-generation"></a>Generowanie artefaktu
 Jednym z głównych zastosowań języka specyficznego dla domeny jest generowanie artefaktu, na przykład kod źródłowy, plik XML lub inne użyteczne dane. Zwykle zmiana w modelu oznacza zmianę w artefaktie. Za pomocą [!INCLUDE[dsl](../includes/dsl-md.md)] programu można generować artefakty i generować je ponownie po zmianie modelu.

### <a name="serialization"></a>Serializacja
 Język specyficzny dla domeny musi zostać utrwalony w niektórych formularzach, które można edytować, zapisać, zamknąć i ponownie załadować. [!INCLUDE[dsl](../includes/dsl-md.md)] Program korzysta z formatu XML, który pozwala definiować i dostosowywać sposób serializacji lub utrwalania języka specyficznego dla domeny.

### <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio
 Ponieważ [!INCLUDE[dsl](../includes/dsl-md.md)] program jest hostowany w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , rozszerza wiele [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okien i kontrolek. Umożliwia również dostosowanie zachowania poleceń menu, elementów przybornika i innych elementów interfejsu użytkownika.

 Możesz również utworzyć modelową kartę magistrali dla języka specyficznego dla domeny. Ta karta umożliwia odwołuje się do modelu i elementów w ramach modelu i pozwala napisać kod, który może uzyskać dostęp do wystąpienia DSL i zaktualizować go. Korzystając z zaawansowanego mechanizmu magistrali modelu, można pisać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia, które działają z wieloma modelami. Możesz również pisać aplikacje autonomiczne, które pracują z modelami. Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą programu Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Zalety programowania specyficznego dla domeny
 Język specyficzny dla domeny może mieć następujące zalety:

- Zawiera konstrukcje, które dokładnie pasują do przestrzeni problemu.

     W przeciwieństwie do języków ogólnego przeznaczenia, język specyficzny dla domeny składa się z elementów i relacji, które bezpośrednio reprezentują logikę przestrzeni problemu. Na przykład aplikacja zasad ubezpieczeniowych musi zawierać elementy zasad i oświadczeń. Język specyficzny dla domeny ułatwia projektowanie aplikacji i znajdowanie i poprawianie błędów logiki.

- Umożliwia deweloperom i osobom, które nie znają domeny, rozumieją cały projekt.

     Korzystając z graficznego języka specyficznego dla domeny, można utworzyć wizualną reprezentację domeny, aby inni deweloperzy mogli łatwo zrozumieć projekt aplikacji.

- Ułatwia tworzenie prototypu końcowej aplikacji.

     Deweloperzy mogą używać kodu, który generuje model, aby utworzyć prototypową aplikację, którą mogą pokazać klientom.

## <a name="the-process-of-domain-specific-development"></a>Proces opracowywania specyficznego dla domeny
 Większość zespołów programistycznych oprogramowania korzystających z języków specyficznych dla domeny wykonaj następujące kroki, aby utworzyć i używać ich modeli:

- Zespół odróżnia zmienne części domeny od części, które nigdy nie ulegną zmianie.

- Deweloperzy piszą kod dla części stałych i opuszczają punkty rozszerzenia dla części zmiennych.

- Deweloper oprogramowania dla lidera lub Architekt tworzy język specyficzny dla domeny, który zawiera wzorce projektowe stałych części domeny i punkty rozszerzenia dla części zmiennych.

- Deweloper oprogramowania dla lidera lub architekt wdraża język specyficzny dla domeny dla deweloperów różnych aplikacji wytwarzanych przez zespół.

- Każdy deweloper tworzy model, który ma zastosowanie do określonej aplikacji.
