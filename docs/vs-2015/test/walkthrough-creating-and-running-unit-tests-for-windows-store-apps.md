---
title: 'Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla aplikacji do sklepu Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e62fe83d644b577d7d0a5f87312642f438c490
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851183"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Wskazówki: tworzenie i uruchamianie testów jednostkowych dla aplikacji sklepu Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio obejmuje obsługę testów jednostkowych zarządzanych [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji i zawiera szablony bibliotek testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.

> [!TIP]
> Aby uzyskać więcej informacji na temat opracowywania [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, zobacz [wprowadzenie do aplikacji ze sklepu Windows](https://msdn.microsoft.com/windows/apps/br211386.aspx).

 Program Visual Studio udostępnia następujące funkcje testowania jednostek:

- [Tworzenie projektów testów jednostkowych](#CreateAndRunUnitTestWin8Tailored_Create)

- [Edytuj manifest dla projektu testów jednostkowych](#CreateAndRunUnitTestWin8Tailored_Manifest)

- [Kod testu jednostkowego](#CreateAndRunUnitTestWin8Tailored_Code)

- [Uruchom testy jednostkowe](#CreateAndRunUnitTestWin8Tailored_Run)

  W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla zarządzanej aplikacji systemu Windows 8 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .

## <a name="prerequisites"></a>Wymagania wstępne
 Visual Studio

## <a name="create-unit-test-projects"></a><a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Tworzenie projektów testów jednostkowych

#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Aby utworzyć projekt testu jednostkowego dla aplikacji ze sklepu Windows

1. Z menu **plik** wybierz pozycję **Nowy projekt**.

     Zostanie wyświetlone okno dialogowe Nowy projekt.

2. W obszarze szablony wybierz język programowania, w którym chcesz utworzyć test jednostkowy, a następnie wybierz skojarzoną [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] bibliotekę testów jednostkowych. Na przykład wybierz pozycję **Visual C#** , a następnie wybierz pozycję **Sklep Windows**, a następnie wybierz pozycję **Biblioteka testów jednostkowych (aplikacje do sklepu Windows)**.

    > [!NOTE]
    > Program Visual Studio zawiera szablony bibliotek testów jednostkowych dla Visual C#, Visual Basic i Visual C++.

3. Obowiązkowe W polu tekstowym **Nazwa** wprowadź nazwę, która ma być używana dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu testów jednostkowych.

4. Obowiązkowe Zmodyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając ją w polu tekstowym **Lokalizacja** lub wybierając przycisk **Przeglądaj** .

5. Obowiązkowe W polu tekstowym Nazwa **rozwiązania** wprowadź tę nazwę, która ma być używana dla Twojego rozwiązania.

6. Pozostaw wybraną opcję **Utwórz katalog dla rozwiązania** , a następnie wybierz przycisk **OK** .

     ![Dostosowana Biblioteka testów jednostkowych](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")

     Eksplorator rozwiązań jest wypełniany nowym [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektem testów jednostkowych, a w edytorze kodu zostanie wyświetlony domyślny test jednostkowy o nazwie UnitTest1.

     ![Nowy dostosowany projekt testu jednostkowego](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="edit-the-manifest-for-the-unit-test-project"></a><a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Edytuj manifest dla projektu testów jednostkowych
 Może być konieczne edytowanie manifestu dla projektu testów jednostkowych w celu zapewnienia wymaganych możliwości uruchomienia aplikacji.

#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Aby edytować plik manifestu aplikacji ze sklepu Windows dla projektu testów jednostkowych

1. W Eksplorator rozwiązań w nowym [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekcie testów jednostkowych kliknij prawym przyciskiem myszy plik Package. appxmanifest i wybierz polecenie **Otwórz**.

     Projektant manifestów jest wyświetlany do edycji.

2. W Projektancie manifestów wybierz kartę **możliwości** .

3. Na liście w obszarze **możliwości**wybierz funkcje, które są potrzebne do testu jednostkowego, oraz kod, który ma być testowany. Na przykład zaznacz pole wyboru **Internet** , jeśli wymagane są testy jednostkowe i kod, który jest testowany, musi mieć możliwość uzyskania dostępu do Internetu.

    > [!NOTE]
    > Wybrane możliwości powinny zawierać tylko funkcje, które są niezbędne do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] poprawnego działania testu jednostkowego. Możliwości nigdy nie muszą obejmować możliwości, które nie są częścią [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] testowanej aplikacji i ogólnie powinny być podzbiorem możliwości określonych dla aplikacji poddawanej [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] testom.

     Aby uzyskać więcej informacji na temat projektanta manifestu, zobacz [Konfigurowanie pakietu aplikacji Windows 8.1 przy użyciu projektanta manifestu](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).

     ![Manifest testu jednostkowego](../test/media/unit-test-win8.png "Unit_Test_Win8_")

## <a name="code-the-unit-test"></a><a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Kod testu jednostkowego

#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Aby zakodować testy jednostkowe dla aplikacji ze sklepu Windows

1. W edytorze kodu Edytuj test jednostkowy i Dodaj potwierdzenia i logikę wymagane dla testu.

     Aby uzyskać więcej informacji, zobacz w temacie [Korzystanie z klas potwierdzeń](https://msdn.microsoft.com/library/ms182530.aspx) w bibliotece MSDN.

## <a name="run-unit-tests"></a><a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Uruchom testy jednostkowe

#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Aby skompilować rozwiązanie i uruchomić test jednostkowy przy użyciu Eksploratora testów

1. W menu **test** wybierz pozycję **Windows**, a następnie wybierz **Eksplorator testów**.

     Eksplorator testów wyświetla się bez na liście testów.

2. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

     Test jednostkowy znajduje się teraz na liście.

    > [!NOTE]
    > Należy skompilować rozwiązanie w celu zaktualizowania listy testów jednostkowych w Eksploratorze testów.

    > [!WARNING]
    > Znany problem programu Visual Studio: należy otworzyć Eksploratora testów przed skompilowaniem projektu testowego.

3. W Eksploratorze testów wybierz utworzony test jednostkowy.

    > [!TIP]
    > Eksplorator testów udostępnia link do kodu źródłowego obok **źródła:**.

4. Wybierz pozycję **Uruchom wszystkie**.

     ![Eksplorator testów jednostkowych &#45; uruchomić test jednostkowy](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")

    > [!TIP]
    > Można wybrać co najmniej jeden test jednostkowy wymieniony w Eksploratorze, a następnie kliknąć prawym przyciskiem myszy i wybrać polecenie **Uruchom wybrane testy**.
    >
    >  Ponadto możesz wybrać **debugowanie wybranych testów**, **otworzyć test**i użyć opcji **Właściwości** .
    >
    >  ![Menu kontekstowe Eksploratora testów jednostkowych &#45; Uni](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

     Uruchomienia testów jednostkowych. Po zakończeniu Eksplorator testów wyświetla stan testu, Upłynęło czasu i zawiera link do źródła.

     ![Test jednostkowy Eksploratora testów &#45; zakończony](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="videos"></a>Filmy wideo
 [Channel 9: testowanie jednostkowe aplikacji ze sklepu Windows skompilowanych przy użyciu języka XAML](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Fora
 [Testowanie jednostkowe programu Visual Studio](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="msdn-library"></a>Biblioteka MSDN
 [Biblioteka MSDN — Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu (Visual Studio 2010)](https://msdn.microsoft.com/library/hh270865(v=vs.110).aspx)

## <a name="see-also"></a>Zobacz też
 [Testowanie aplikacji ze sklepu za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md) [Build i testowanie aplikacji ze sklepu Windows za pomocą programu Team Foundation Build](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
