---
title: 'Instrukcje: Dodawanie deskryptora filtru do metody wyszukiwania | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 228afb2f49f4d528fa9b806e9bf8d2531f7de901
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016736"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Instrukcje: Dodawanie deskryptora filtru do metody wyszukiwania
  Deskryptory filtru umożliwiają odbiorcom modelu przekazywanie wartości do metod przed ich wykonaniem. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

 Typowym scenariuszem jest to, że użytkownicy w programie SharePoint chcą pobrać wystąpienia zewnętrznego typu zawartości, które pasują do niektórych kryteriów. Możesz obsłużyć ten scenariusz, dodając Deskryptor filtru do metody wyszukiwania.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Aby dodać Deskryptor filtru do metody wyszukiwania

1. W oknie **Szczegóły metody BDC** rozwiń węzeł metody wyszukiwania, rozwiń węzeł **Parametry** , a następnie Dodaj parametr wejściowy. Aby uzyskać więcej informacji, zobacz [How to: Add a Parameter to a Method](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. W oknie **Szczegóły metody** wybierz deskryptor typu parametru.

3. Na pasku menu wybierz **View**  >  **okno właściwości**widoku.

4. W oknie **Właściwości** ustaw właściwość **Nazwa typu** na typ danych, który jest odpowiedni dla filtra.

     Na przykład filtr może użyć daty zamówienia, aby ograniczyć liczbę zamówień sprzedaży zwracanych przez metodę. Aby można było obsługiwać ten filtr, właściwość **Nazwa typu** deskryptora typu musi być ustawiona na **System. DateTime**.

5. W oknie **Szczegóły metody** rozwiń węzeł **deskryptory filtru** .

6. Na liście **Dodaj Deskryptor filtru** wybierz pozycję **Utwórz Deskryptor filtru**.

     Nowy Deskryptor filtru pojawia się pod węzłem **deskryptorów filtru** .

7. Na pasku menu wybierz **View**  >  **okno właściwości**widoku.

8. W oknie **Właściwości** wybierz właściwość **Typ** .

9. Na liście, która pojawia się dla właściwości **Typ** , wybierz odpowiedni wzorzec filtrowania.

     Na przykład, aby utworzyć filtr, który używa daty zamówienia, aby ograniczyć liczbę zamówień sprzedaży zwracanych w metodzie wyszukiwania, wybierz opcję **porównanie**. Filtr porównania zapewnia, że metoda wyszukiwania zwraca tylko te wystąpienia, które spełniają określony warunek. Aby uzyskać więcej informacji na temat poszczególnych wzorców filtrowania, zobacz [typy filtrów obsługiwanych przez ten kontroler BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. W oknie **Właściwości** wybierz **skojarzoną Właściwość deskryptorów typu** .

11. Na liście, która pojawia się dla właściwości **skojarzonej deskryptorów typu** , wybierz deskryptor typu, który został utworzony wcześniej w tej procedurze. Powoduje to odfiltrowanie filtru do parametru wejściowego metody wyszukiwania.

12. Dodaj kod do metody wyszukiwania, która zwraca dane. W zapytaniu SELECT można użyć parametru wejściowego jako warunku.

     Poniższy przykład zwraca zamówienia sprzedaży z określoną datą zamówienia.

    > [!NOTE]
    > Zamień wartość `ServerName` pola na nazwę serwera.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie deskryptora typu dla parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
