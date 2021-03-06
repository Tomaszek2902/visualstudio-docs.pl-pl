---
title: Właściwości dokumentu XML, Właściwości, okno
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b21f4435737597136e1ac4a4dd8651decaf4c65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592428"
---
# <a name="xml-document-properties-properties-window"></a>Właściwości dokumentu XML, okno Właściwości

Okno **Właściwości** zawiera podstawowe informacje o dokumencie aktywnym w edytorze XML. Dostępne właściwości różnią się w zależności od typu dokumentu XML, który jest obecnie aktywny.

> [!NOTE]
> Wszystkie właściwości dokumentu XML są zapisywane w rozwiązaniu. W związku z tym nie trzeba ponownie wprowadzać tych wartości przy następnym otwarciu rozwiązania.

**Kodowanie**

Kodowanie znaków dla pliku. Zmiana tej właściwości powoduje także zmianę atrybutu kodowania w deklaracji XML i odwrotnie. Nowe kodowanie jest używane do kodowania pliku podczas zapisywania pliku.

**Dane wejściowe**

Dokument wejściowy skojarzony z arkuszem stylów XSLT. Jest on używany przez polecenia **Uruchom XSLT** , na przykład **kod XML**  >  **uruchamiania XSLT bez debugowania**. Dokument można wybrać za pomocą przycisku Przeglądaj (..**.**).

Ta właściwość jest widoczna tylko wtedy, gdy plik XSLT jest otwarty w edytorze.

**Dane wyjściowe**

Plik, który jest generowany podczas przekształcania dokumentu XML.

Jeśli plik nie zostanie określony, domyślna nazwa pliku jest generowana na podstawie `method` atrybutu `xsl:output` elementu, który określa rozszerzenie pliku. Plik domyślny znajduje się w katalogu tymczasowym bieżącego użytkownika.

**Schematy**

Schematy do użycia na potrzeby walidacji. Przycisk otwiera okno dialogowe **schematy XSD** , za pomocą którego można wybrać schematy do użycia.

Możesz również wprowadzić ścieżkę do schematów. Jeśli określono wiele schematów, każda ścieżka schematu musi być ujęta w cudzysłów.

**Rozszerzaln**

Plik XSLT, który jest używany do przekształcania dokumentu po użyciu poleceń **Rozpocznij debugowanie XSLT** i **Rozpocznij XSLT bez debugowania** . Jeśli to pole jest puste, Edytor używa wartości podanej w `xml-stylesheet` instrukcji przetwarzania dokumentu lub poprosi o nazwę pliku.

Podczas edytowania pliku XSLT ta właściwość może służyć do określenia, że inny arkusz stylów ma być używany, gdy jest zaznaczone polecenie **Rozpocznij debugowanie XSLT** lub **Rozpocznij XSLT bez debugowania** . Na przykład możesz to zrobić, gdy edytujesz arkusz stylów, który znajduje się w arkuszu stylów nadrzędnych.

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
