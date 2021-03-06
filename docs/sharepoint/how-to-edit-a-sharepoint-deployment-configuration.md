---
title: 'Instrukcje: edytowanie konfiguracji wdrożenia programu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74f6377bad0f62aa2c470e72afe64b85b3017ee6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016783"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Instrukcje: edytowanie konfiguracji wdrożenia programu SharePoint
  Można utworzyć konfigurację wdrożenia lub zmodyfikować istniejącą konfigurację wdrożenia. Można na przykład uruchomić pojedynczy krok lub zmienić kolejność kroków w procesie wdrażania. Możesz chcieć utworzyć lub zmodyfikować konfiguracje wdrożenia, ponieważ wbudowane i programowo dodane konfiguracje nie mogą zostać zmienione.

## <a name="create-a-sharepoint-deployment-configuration"></a>Tworzenie konfiguracji wdrożenia programu SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Aby utworzyć konfigurację wdrożenia programu SharePoint

1. W **Eksplorator rozwiązań**wybierz projekt SharePoint, a następnie na pasku menu wybierz **projekt**,**Właściwości** _ProjectName_.

2. Na karcie **SharePoint** wybierz przycisk **Nowy** .

     Zostanie wyświetlone okno dialogowe **Dodawanie nowej konfiguracji wdrożenia** .

3. W polu tekstowym **Nazwa** wprowadź nazwę konfiguracji wdrożenia.

4. W okienku **dostępne kroki wdrożenia** wybierz czynności, które chcesz dodać do konfiguracji wdrożenia, wybierz **>** przycisk (), a następnie wybierz przycisk **OK** .

    > [!NOTE]
    > Jeśli skonfigurowano polecenie przed wdrożeniem lub polecenie po wdrożeniu, te kroki są wykonywane tylko wtedy, gdy zostaną dodane do niestandardowej konfiguracji wdrożenia.

## <a name="change-the-active-deployment-configuration"></a>Zmiana konfiguracji aktywnego wdrożenia

#### <a name="to-change-the-active-deployment-configuration"></a>Aby zmienić konfigurację aktywnego wdrożenia

1. W **Eksplorator rozwiązań**wybierz projekt SharePoint, a następnie na pasku menu wybierz **Project**  >  ** \<*ProjectName*> Właściwości**projektu.

2. Wybierz kartę **SharePoint** .

3. W polu listy **Konfiguracja wdrożenia aktywnego** wybierz nazwę konfiguracji wdrożenia, która ma być używana.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
