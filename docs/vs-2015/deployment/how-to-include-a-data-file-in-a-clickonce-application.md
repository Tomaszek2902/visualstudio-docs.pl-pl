---
title: 'Instrukcje: uwzględnianie pliku danych w aplikacji ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9120a5b3cb60f6c607ed97ab2df24bb157c72371
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153768"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Porady: uwzględnianie pliku danych w aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Każda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalowana aplikacja ma przypisany katalog danych na dysku lokalnym komputera docelowego, na którym aplikacja może zarządzać własnymi danymi. Pliki danych mogą zawierać pliki dowolnego typu: pliki tekstowe, pliki XML, a nawet pliki bazy danych programu Microsoft Access (mdb). Poniższe procedury pokazują, jak dodać plik danych dowolnego typu do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Aby dołączyć plik danych przy użyciu Mage.exe  
  
1. Dodaj plik danych do katalogu aplikacji przy użyciu pozostałych plików aplikacji.  
  
    Zazwyczaj katalog aplikacji będzie katalogiem z bieżącą wersją wdrożenia — na przykład, w wersji 1.0.0.0.  
  
2. Zaktualizuj manifest aplikacji, aby wyświetlić listę plików danych.  
  
    **Mage-u v 1.0.0.0 \ Application. manifest-FromDirectory v 1.0.0.0**  
  
    Wykonanie tego zadania spowoduje ponowne utworzenie listy plików w manifeście aplikacji, a także automatyczne wygenerowanie sygnatury skrótu.  
  
3. Otwórz manifest aplikacji w preferowanym edytorze tekstu lub XML i Znajdź `file` element dla ostatnio dodanego pliku.  
  
    Jeśli dodano plik XML o nazwie `Data.xml` , plik będzie wyglądać podobnie do poniższego przykładu kodu.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Dodaj atrybut `type` do tego elementu i podaj go wartością `data` .  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Ponownie podpisz manifest aplikacji przy użyciu pary kluczy lub certyfikatu, a następnie ponownie podpisz manifest wdrożenia.  
  
    Musisz ponowić podpisanie manifestu wdrożenia, ponieważ jego skrót do manifestu aplikacji został zmieniony.  
  
    **manifest aplikacji Mage-s — hasło CF cert_file-PWD**  
  
    **Manifest wdrożenia w programie Mage-u — manifest aplikacji APPM**  
  
    **Manifest wdrożenia w programie Mage-s — hasło CF CERTFILE-PWD**  
  
6. 
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Aby dołączyć plik danych przy użyciu MageUI.exe  
  
1. Dodaj plik danych do katalogu aplikacji przy użyciu pozostałych plików aplikacji.  
  
2. Zazwyczaj katalog aplikacji będzie katalogiem z bieżącą wersją wdrożenia — na przykład, w wersji 1.0.0.0.  
  
3. W menu **plik** kliknij polecenie **Otwórz** , aby otworzyć manifest aplikacji.  
  
4. Wybierz kartę **pliki** .  
  
5. W polu tekstowym w górnej części karty wprowadź katalog zawierający pliki aplikacji, a następnie kliknij pozycję **Wypełnij**.  
  
     Plik danych pojawi się w siatce.  
  
6. Ustaw wartość **Typ pliku** danych na **dane**.  
  
7. Zapisz manifest aplikacji, a następnie ponownie Podpisz plik.  
  
     MageUI.exe wyświetli monit o ponowne podpisanie pliku.  
  
8. Ponowne podpisywanie manifestu wdrożenia  
  
     Musisz ponowić podpisanie manifestu wdrożenia, ponieważ jego skrót do manifestu aplikacji został zmieniony.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
