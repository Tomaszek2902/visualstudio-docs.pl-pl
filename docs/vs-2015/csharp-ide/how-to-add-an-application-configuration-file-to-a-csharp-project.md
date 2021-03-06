---
title: 'Instrukcje: Dodawanie pliku konfiguracji aplikacji do projektu C# | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667534"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Porady: Dodawanie pliku konfiguracji aplikacji do projektu C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodając plik konfiguracji aplikacji (plik app.config) do projektu C#, można dostosować sposób lokalizowania i ładowania plików zestawu przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji na temat plików konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> Sklep Windows nie obsługuje <xref:System.Configuration> . W związku z tym aplikacje ze sklepu nie zawierają szablonu app.config.

 Podczas kompilowania projektu środowisko programistyczne automatycznie kopiuje plik app.config, zmienia nazwę pliku kopii w celu dopasowania do pliku wykonywalnego, a następnie przenosi kopię do katalogu bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#

1. Na pasku menu wybierz **projekt**, **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. Rozwiń węzeł **zainstalowane**, rozwiń pozycję **elementy Visual C#**, a następnie wybierz szablon **plik konfiguracji aplikacji** .

3. W polu tekstowym **Nazwa** wprowadź nazwę, a następnie wybierz przycisk **Dodaj** .

     Plik o nazwie app.config zostanie dodany do projektu.

## <a name="see-also"></a>Zobacz też
 [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md) [Schemat pliku konfiguracji](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [Konfigurowanie aplikacji](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) [instrukcje: Konfigurowanie aplikacji jako docelowej dla .NET Framework wersji](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [przy użyciu środowiska programistycznego Visual Studio dla języka C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)