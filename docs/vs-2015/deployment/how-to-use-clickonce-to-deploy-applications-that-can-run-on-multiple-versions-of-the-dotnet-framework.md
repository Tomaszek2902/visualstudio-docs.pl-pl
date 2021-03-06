---
title: 'Instrukcje: używanie technologii ClickOnce do wdrażania aplikacji, które mogą być uruchamiane na wielu wersjach .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 164fe64f360e41c06ef3f7bfd2d8091a6ebefecd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679948"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Porady: użycie technologii ClickOnce do wdrażania aplikacji uruchamianych w wielu wersjach systemu .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikację, która jest przeznaczona dla wielu wersji .NET Framework, można wdrożyć przy użyciu technologii wdrażania ClickOnce. Wymaga to wygenerowania i zaktualizowania manifestów aplikacji i wdrożenia.  
  
> [!NOTE]
> Przed zmianą aplikacji na docelową wiele wersji .NET Framework należy upewnić się, że aplikacja działa z wieloma wersjami .NET Framework. Wersja środowiska uruchomieniowego języka wspólnego jest różna w [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] porównaniu do .NET Framework 2,0, .NET Framework 3,0 i .NET Framework 3,5.  
  
 Ten proces wymaga wykonania następujących czynności:  
  
1. Generowanie manifestów aplikacji i wdrożenia.  
  
2. Zmień manifest wdrożenia, aby wyświetlić listę wielu wersji .NET Framework.  
  
3. Zmień plik app.config, aby wyświetlić listę zgodnych wersji .NET Framework środowiska uruchomieniowego.  
  
4. Zmień manifest aplikacji, aby oznaczyć zestawy zależne jako zestawy .NET Framework.  
  
5. Podpisz manifest aplikacji.  
  
6. Zaktualizuj i podpisz manifest wdrożenia.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Aby wygenerować aplikacje i manifesty wdrożenia  
  
- Użyj Kreatora publikacji lub strony publikowania projektanta projektu, aby opublikować aplikację i wygenerować pliki manifestu aplikacji i wdrożenia. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) lub [strony publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Aby zmienić manifest wdrożenia na listę wielu wersji .NET Framework  
  
1. W katalogu publikowania Otwórz manifest wdrożenia przy użyciu edytora XML w programie Visual Studio. Manifest wdrożenia ma rozszerzenie nazwy pliku. Application.  
  
2. Zastąp kod XML między `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` elementami i `</compatibleFrameworks>` plikiem XML, który zawiera listę obsługiwanych .NET Framework wersji aplikacji.  
  
     W poniższej tabeli przedstawiono niektóre dostępne wersje .NET Framework i odpowiadające im dane XML, które można dodać do manifestu wdrożenia.  
  
    |Wersja programu .NET Framework|XML|  
    |----------------------------|---------|  
    |4 klient|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|  
    |4 pełne|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|  
    |Klient 3,5|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|  
    |3,5 pełne|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|  
    |3,0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Aby zmienić plik app.config, aby wyświetlić listę zgodnych wersji środowiska uruchomieniowego .NET Framework  
  
1. W Eksplorator rozwiązań otwórz plik App.config przy użyciu edytora XML w programie Visual Studio.  
  
2. Zastąp (lub Dodaj) kod XML między `<startup>` elementami i i `</startup>` XML, który zawiera listę obsługiwanych .NET Framework środowiska uruchomieniowego dla aplikacji.  
  
     W poniższej tabeli przedstawiono niektóre dostępne wersje .NET Framework i odpowiadające im dane XML, które można dodać do manifestu wdrożenia.  
  
    |Wersja środowiska uruchomieniowego .NET Framework|XML|  
    |------------------------------------|---------|  
    |4 klient|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|  
    |4 pełne|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|  
    |3,5 pełne|\<supportedRuntime version="v2.0.50727"/>|  
    |Klient 3,5|\<supportedRuntime version="v2.0.50727" sku="Client"/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Aby zmienić manifest aplikacji, aby oznaczyć zestawy zależne jako zestawy .NET Framework  
  
1. W katalogu publikowania Otwórz manifest aplikacji przy użyciu edytora XML w programie Visual Studio. Manifest wdrożenia ma rozszerzenie nazwy pliku manifestu.  
  
2. Dodaj `group="framework"` do pliku XML zależności dla zestawów wskaźnikowych ( `System.Core` , `WindowsBase` , `Sentinel.v3.5Client` i `System.Data.Entity` ). Na przykład kod XML powinien wyglądać następująco:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. Zaktualizuj numer wersji `<assemblyIdentity>` elementu Microsoft. Windows. CommonLanguageRuntime do numeru wersji dla .NET Framework, który jest najniższym typowym mianownikiem. Na przykład jeśli aplikacja jest przeznaczona dla .NET Framework 3,5 i [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , użyj numeru wersji 2.0.50727.0, a kod XML powinien wyglądać następująco:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Aby zaktualizować i podpisać aplikacje i manifesty wdrożenia  
  
- Aktualizowanie i ponowne podpisywanie aplikacji i manifestów wdrożenia. Aby uzyskać więcej informacji, zobacz [jak: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks> Postaci](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependency> Postaci](../deployment/dependency-element-clickonce-application.md)   
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Schemat pliku konfiguracji](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
