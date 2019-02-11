---
title: Wdrażanie kontenera platformy Docker programu ASP.NET do usługi Azure Container Registry (ACR) | Dokumentacja firmy Microsoft
description: Dowiedz się, jak wdrożyć aplikację sieci web platformy ASP.NET Core do rejestru kontenerów za pomocą programu Visual Studio Tools for Docker
services: azure-container-service
documentationcenter: .net
author: mlearned
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.service: azure-container-service
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 05/21/2018
ms.author: mlearned
ms.openlocfilehash: 8ba7244ffc482c33409bc280617b60ce1e85b504
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55701315"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Wdrażanie kontenera platformy ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio

## <a name="overview"></a>Omówienie

Docker to aparat uproszczone kontenera, podobne pod pewnymi względami na maszynę wirtualną, której można użyć do hostowania aplikacji i usług.
Ten samouczek przeprowadzi Cię przez publikowanie konteneryzowaną aplikację przy użyciu programu Visual Studio [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs).

## <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

* Zainstaluj najnowszą wersję [programu Visual Studio 2017](https://azure.microsoft.com/downloads/) z obciążeniem "programowanie aplikacji platformy ASP.NET i sieci web"
* Zainstaluj [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="1-create-an-aspnet-core-web-app"></a>1. Tworzenie aplikacji internetowej platformy ASP.NET Core
Poniższe kroki prowadzą przez proces tworzenia podstawowej aplikacji platformy ASP.NET Core, który będzie używany w ramach tego samouczka.

[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]

## <a name="2-publish-your-container-to-azure-container-registry"></a>2. Opublikowany kontener w usłudze Azure Container Registry
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **Publikuj**.
2. W oknie dialogowym docelowej publikowania wybierz **Container Registry** kartę.
3. Wybierz **nowy rejestr Azure Container Registry** i kliknij przycisk **Publikuj**.
4. Wprowadź żądane wartości w **Utwórz nowy rejestr Azure Container Registry**.

    | Ustawienie      | Sugerowana wartość  | Opis                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefiks DNS** | Nazwa unikatowa w skali globalnej | Unikatowa nazwa identyfikująca rejestru kontenerów. |
    | **Subskrypcja** | Wybierz subskrypcję | Subskrypcja platformy Azure do użycia. |
    | **[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nazwa grupy zasobów, w której chcesz utworzyć rejestru kontenerów. Wybierz **New** do tworzenia nowej grupy zasobów.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standardowa (Standard) | Warstwy usługi container Registry  |
    | **Lokalizacja w rejestrze** | Bliską lokalizację | Wybierz lokalizację w [region](https://azure.microsoft.com/regions/) okolicy lub w pobliżu innych usług używających usługi container registry. |

    ![Visual Studio utworzyć okno dialogowe usługi Azure Container Registry](media/vs-azure-tools-docker-hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Kliknij przycisk **Utwórz**.

Możesz teraz ściągnąć kontenera z rejestru na dowolnym hoście może uruchamiać obrazy Docker, na przykład [usługi Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).