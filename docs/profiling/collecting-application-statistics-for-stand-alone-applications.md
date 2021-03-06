---
title: 'Wiersz polecenia profilera: Zbierz statystyki aplikacji autonomicznej'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 150a1a010a33a3b4fcfe0954ec70db2ff4de7816
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808919"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla aplikacji klienckiej (autonomicznej) za pomocą metody próbkowania z wiersza polecenia.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Uruchamianie aplikacji przy użyciu profilowania**|-   [Instrukcje: uruchamianie aplikacji autonomicznej i zbieranie statystyk aplikacji](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Dołącz profiler do uruchomionej aplikacji .NET Framework**|-   [Instrukcje: dołączanie profilera do aplikacji .NET Framework i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Dołącz profiler do uruchomionej aplikacji C/C++**|-   [Instrukcje: dołączanie profilera do natywnej aplikacji i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Zadania powiązane

### <a name="profile-stand-alone-applications"></a>Profile aplikacji autonomicznych

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Instrumentacja aplikacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Zbierz dane alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Zbieranie danych rywalizacji o zasoby i wykonywanie wątków**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody próbkowania

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|**Profilowanie aplikacji sieci Web ASP.NET**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Usługi profilu**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Opisuje sposób zbierania statystyk wydajności z usług systemu Windows przy użyciu metody próbkowania.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
