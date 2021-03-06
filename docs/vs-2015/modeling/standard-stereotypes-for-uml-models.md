---
title: Standardowe stereotypy dla modeli UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a16c68b3b14be57fb0a6a45c740e5420a82c2ddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661047"
---
# <a name="standard-stereotypes-for-uml-models"></a>Standardowe stereotypy dla modeli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dodać stereotypy do elementów modelu UML, aby uzyskać dodatkowe informacje dotyczące czytnika lub przetwarzania maszynowego. Stereotypy są zdefiniowane w profilach, a każdy profil zawiera zestaw stereotypów. Do programu Visual Studio są dostarczane różne profile. Można również zdefiniować własne profile, które mogą zawierać własne stereotypy. Aby uzyskać więcej informacji, zobacz [Definiowanie profilu do rozszerania UML](../modeling/define-a-profile-to-extend-uml.md).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="the-standard-profiles"></a>Profile standardowe
 Następujące profile są dostępne w obsługiwanej wersji programu Visual Studio zaraz po jej zainstalowaniu.

|Profil|Przeznaczenie|
|-------------|-------------|
|[Standardowy profil UML — L2](#L2)|Standardowy zestaw stereotypów, który może służyć do dodawania dodatkowych informacji na temat elementu lub relacji.|
|[Profil standardowy UML P3](#L3)|Standardowy zestaw stereotypów, który może służyć do dodawania dodatkowych informacji na temat elementu lub relacji.|
|[Profil C#](#NetProfile)|Jeśli planujesz klasę lub inny element w modelu UML, aby reprezentować kod programu, możesz wskazać ten obiekt, stosując jeden z stereotypów z profilu języka C#.<br /><br /> Te stereotypy również dodają właściwości do elementów modelu.|

 Podczas tworzenia nowego modelu UML w przypadku standardowych profilów UML i L3 są połączone z modelem, chyba że usuniesz linki.

 Aby użyć stereotypów w dowolnym z tych profilów, należy najpierw połączyć profil z pakietem lub modelem zawierającym elementy, do których mają zostać zastosowane.

#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Aby połączyć profil z modelem lub pakietem

1. Otwórz **Eksploratora modelu UML**. W menu **Architektura** wskaż polecenie **Windows**, a następnie kliknij pozycję **Eksplorator modelu UML**.

2. Znajdź pakiet lub model, który zawiera wszystkie elementy, do których chcesz zastosować stereotypy w profilu.

3. Kliknij prawym przyciskiem myszy pakiet lub model, a następnie kliknij polecenie **Właściwości**.

4. W oknie **Właściwości** ustaw właściwość **Profile** na żądane profile.

#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Aby usunąć łącze między profilem a modelem lub pakietem

1. W Eksploratorze modelu UML, kliknij prawym przyciskiem myszy Model lub pakiet, a następnie kliknij polecenie **Właściwości**.

2. W okno Właściwości ustaw właściwość **Profile** na wartość Empty.

    > [!NOTE]
    > Możesz odłączyć profil tylko wtedy, gdy żaden z elementów w modelu lub pakiecie nie używa tego samego stereotypu tego profilu.

#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Aby zastosować stereotyp do elementu modelu

1. Kliknij prawym przyciskiem myszy element modelu na diagramie lub w **Eksploratorze modelu UML**, a następnie kliknij polecenie **Właściwości**.

2. Kliknij właściwość **stereotypy** i wybierz stereotypy, które chcesz zastosować.

     Wybrane Stereotypy pojawiają się w obrębie elementu "pagons" w elemencie modelu w przypadku większości rodzajów elementu.

    > [!NOTE]
    > Jeśli nie widzisz właściwości **stereotypów** lub jeśli odpowiedni stereotyp nie jest wyświetlany, sprawdź, czy element modelu znajduje się w pakiecie lub modelu, do którego został połączony odpowiedni profil.

3. Niektóre stereotypy umożliwiają ustawienie wartości dodatkowych właściwości dla elementu modelu. Aby wyświetlić te właściwości, rozwiń Właściwość **stereotypy** .

### <a name="uml-standard-profile-l2"></a><a name="L2"></a> Standardowy profil UML — L2
 Następujące Stereotypy mogą służyć do specjalizacji znaczenia elementów modelu UML, chyba że link do profilu został usunięty z modelu.

 Dokładne znaczenie tych stereotypów zależy od własnych Konwencji lokalnych i narzędzi, które mogą być używane do przetwarzania modelu.

|Stereotyp|Dotyczy|Znaczenie|
|----------------|----------------|-------------|
|dodatkowy|Klasa|Klasa, która obsługuje inną klasę, zazwyczaj przez implementację dodatkowej logiki. Druga klasa może mieć stereotyp «Focus».|
| — wywołanie|Zależność|Klasa klienta wywołuje operacje dostawcy.|
|create|Zależność|Klasa Client tworzy wystąpienia dostawcy.|
|create|Komunikat|Nadawca tworzy odbiornik.|
|create|Operacja|Ta operacja jest konstruktorem.|
|pochodn|Zależność|Element Client jest obliczany całkowicie lub częściowo od dostawcy.|
|zniszcz|Operacja|Operacja niszczy jego wystąpienie.|
|dokument|Artefakt|«Plik», który nie jest źródłem lub plikiem wykonywalnym.|
|jednostka|Składnik|Składnik reprezentuje koncepcję biznesową.|
|plik|Artefakt|Plik wykonywalny «».|
| — plik|Artefakt|Plik fizyczny.|
|fokus|Klasa|Klasa definiująca podstawową logikę biznesową, która jest obsługiwana przez kilka klas «pomocnicze».|
|szablon|Pakiet|Ten pakiet definiuje wzorzec projektu wielokrotnego użytku.|
|wprowadzą|Składnik|Implementacja «specyfikacji».|
|implementationClass|Klasa|Klasa opisuje implementację, a każde wystąpienie środowiska uruchomieniowego ma jedną stałą klasę implementacji. Kontrast z «Type».|
|tworzenia|Zależność|Klient tworzy wystąpienia dostawcy.|
|biblioteka|Artefakt|Biblioteka «plik».|
|metaclass|Klasa|Wystąpienia tej klasy są również klasami.|
|modelLibrary|Pakiet|Zawiera elementy modelu, które mają być ponownie używane przez zaimportowanie pakietów. Zwykle zdefiniowane jako część profilu i zaimportowane automatycznie przez aplikację profilu.|
|proces|Składnik|Składnik oparty na transakcji lub jeden, który przeniesie wątek.|
|Realizacja|Klasa, interfejs, składnik|Opisuje implementację programu.|
|Uściślij|Zależność|Klasa, składnik lub pakiet klienta zawiera więcej informacji na temat specyfikacji lub projektu niż dostawca.|
|odpowiedzialność za|Zależność|Komentarz na końcu zależności od dostawcy definiuje obowiązki klasy klienta lub składnika.|
|skrypt|Artefakt|Interpreter «plik».|
|wyślij|Zależność|Operacja źródłowa wysyła sygnał docelowy.|
|usługa|Składnik|Składnik bezstanowy.|
|source|Artefakt|Nadawać «plik».|
|specyfikacja|Klasa, interfejs, składnik|Definiuje zachowanie składnika lub obiektu bez definiowania sposobu, w jaki działa wewnętrznie.|
|wykonawc|Składnik|Część dużego systemu. Podsystem na diagramie przypadków użycia jest składnikiem z stereotypem podsystemu.|
|śledzenie|Zależność|Element Client jest częścią projektu, który realizuje dostawcę. Dwa zakończenia tej zależności są zwykle w różnych modelach. Jeden z tych modeli jest realizowany przez inne.|
|typ|Klasa|Określa zachowanie obiektu bez określania sposobu jego implementacji. Obiekt jest składową typu, jeśli jest zgodny ze specyfikacją.|
|utility|Klasa|Kolekcja funkcji statycznych. Klasa nie ma wystąpień.|

### <a name="uml-standard-profile-l3"></a><a name="L3"></a> Profil standardowy UML P3
 Następujące Stereotypy mogą służyć do specjalizacji znaczenia elementów modelu UML, chyba że profil został odłączone od modelu.

 Dokładne znaczenie tych stereotypów zależy od własnych Konwencji lokalnych i narzędzi, które mogą być używane do przetwarzania modelu.

|Stereotyp|Dotyczy|Opis|
|----------------|----------------|-----------------|
|buildComponent|Składnik|Kolekcja elementów służąca do definiowania kompilacji.|
|metaModel|Model|Definiuje język modelowania, taki jak odmiana UML lub język specyficzny dla domeny.|
|systemModel|Model|Model, który jest kolekcją modeli, które mają zastosowanie do tego samego systemu, na przykład specyfikacji, realizacji i relacji śledzenia między nimi.|

## <a name="c-profile"></a><a name="NetProfile"></a> Profil C#
 Stereotypy zdefiniowane w tym profilu pozwalają wskazać, że element modelu jest przeznaczony do tłumaczenia na kod programu. Każdy stereotyp definiuje dodatkowe właściwości, które można ustawić dla elementu modelu.

 Aby udostępnić te stereotypy, Połącz model lub pakiet z profilem języka C#. Następnie można zastosować stereotypy do elementów modelu w tym modelu lub pakiecie.

 Dostępne stereotypy, elementy, do których mają zastosowanie, oraz dodatkowe właściwości, które udostępniają, zostały podsumowane w poniższej tabeli.

|Stereotyp|Dotyczy|Właściwości|
|----------------|----------------|----------------|
|**Klasa języka C#**|Klasa UML<br /><br /> Składnik|**Atrybuty CLR**<br /><br /> **Jest częściowy**<br /><br /> **Jest zapieczętowany**<br /><br /> **Jest statyczny**<br /><br /> **Jest niebezpieczny**<br /><br /> **Widoczność pakietu**|
|**Struktura C#**|Klasa UML<br /><br /> Składnik|**Atrybuty CLR**<br /><br /> **Jest częściowy**<br /><br /> **Jest niebezpieczny**<br /><br /> **Widoczność pakietu**|
|**Globalne elementy członkowskie C#**|Klasa UML<br /><br /> Składnik|**Atrybuty CLR**|
|**Interfejs C#**|Interfejs UML|**Atrybuty CLR**<br /><br /> **Jest częściowy**<br /><br /> **Widoczność pakietu**|
|**Wyliczenie C#**|Wyliczenie UML|**ClrAttributes**<br /><br /> **Typ podstawowy**|
|**Przestrzeń nazw C#**|Pakiet UML|**Atrybuty CLR**<br /><br /> **Nazwa podstawowa**<br /><br /> **Korzystanie z przestrzeni nazw**|

## <a name="see-also"></a>Zobacz też
 [Dodaj stereotypy do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md) [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Zdefiniuj profil, aby zwiększyć UML](../modeling/define-a-profile-to-extend-uml.md)
