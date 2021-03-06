---
title: Błędy zasad analizy kodu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac7a949b3f8a1e0c9d44c6194f87745b4e3f17a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587748"
---
# <a name="code-analysis-policy-errors"></a>Błędy zasad analizy kodu

Jeśli zasady analizy kodu nie są spełnione podczas zaewidencjonowania, wystąpią następujące błędy:

**Ustawienia analizy kodu dla co najmniej jednego projektu są niezgodne z zasadami analizy kodu.**

Wymagania analizy kodu, które można zaewidencjonować do kontroli źródła projektu, nie zostały spełnione dla co najmniej jednego projektu kodu. Ten błąd może być spowodowany przez jeden lub więcej z następujących warunków:

- Analiza kodu nie jest włączona podczas kompilacji dla wszystkich projektów w rozwiązaniu.

- Lokalna reguła zestawu reguł dla projektu w programie Visual Studio ma mniej restrykcyjne ustawienie **akcji** niż zestaw reguł projektu na przykład reguła, która jest ustawiona na **Action** = **błąd** akcji na serwerze, ma ustawioną **akcję** na **Ostrzeżenie** lub **Brak** w zestawie reguł uruchomionym w programie Visual Studio).

- Zestaw reguł określony w programie Visual Studio nie zawiera wszystkich reguł, które są określone w zestawie reguł, określonym w zasadach ewidencjonowania analizy kodu dla projektu.

**Zasady analizy kodu nie powiodły się. Istnieją błędy w projekcie {0} lub kompilacja jest nieaktualna.**

Kompilacja zawiera błędy lub błędy zostały naprawione, ale Analiza kodu nie została wykonana po usunięciu poprawki.

**Zaewidencjonowanie nie powiodło się. Zasady analizy kodu wymagają wyewidencjonowania za pomocą programu Visual Studio z otwartym rozwiązaniem.**

Zasady analizy kodu wymagają, aby wszystkie pliki, które zostały zaewidencjonowane, muszą znajdować się w aktualnie otwartym rozwiązaniu. Aby naprawić ten błąd, Otwórz rozwiązanie, które zawiera plik do zaewidencjonowania.

**Nie wszystkie pliki w oczekujących zaewidencjonowania znajdują się w aktualnie otwartym rozwiązaniu.**

Zasady analizy kodu wymagają, aby wszystkie pliki, które zostały zaewidencjonowane, muszą znajdować się w aktualnie otwartym rozwiązaniu. Ten błąd jest zgłaszany, gdy istnieje otwarte rozwiązanie, ale niektóre pliki w widoku "oczekujące na sprawdzenie" nie są częścią aktualnie otwartego rozwiązania. Aby naprawić ten błąd, Otwórz rozwiązanie, które zawiera plik do zaewidencjonowania.

**Wersja elementu " {0} " jest niepoprawna. Silna nazwa określona w zasadach to " {1} ".**

Ten błąd dotyczy projektów platformy .NET. Reguła. dll wymagana przez zasady analizy kodu istnieje na komputerze lokalnym, ale wersja/klucz publiczny nie są zgodne. Aby naprawić ten błąd, twórca zasad musi zaktualizować pliki dll w katalogu *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\ * na swoim komputerze.

**{0}zestaw "" określony w zasadach nie istnieje.**

Ten błąd dotyczy projektów platformy .NET. Reguła wymagana przez zasady analizy kodu nie ma odpowiedniej biblioteki DLL zainstalowanej na komputerze klienckim. Aby naprawić ten błąd, twórca zasad musi zaktualizować bibliotekę DLL w katalogu *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\ * na swoim komputerze.

**{0}Ustawienia reguły projektu nie są zgodne z zasadami analizy kodu.**

Ten błąd dotyczy projektów platformy .NET. Ustawienia reguł kodu zarządzanego nie są zgodne z wymaganiami zasad. Aby naprawić ten błąd, ustawienie klienta musi być takie samo lub rygorystyczne jak wymaganie zasad na serwerze.

**Analiza kodu nie jest włączona w aktywnej konfiguracji. Przełącz się do konfiguracji {0} i skompiluj projekt {1} przed zaewidencjonowaniem.**

W programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aktywna konfiguracja nie ma włączonej analizy kodu, ale jest włączona co najmniej jedna Analiza kodu.

**Należy włączyć analizę kodu dla zarządzanych plików binarnych we {0} właściwościach projektu i skompilować przed zaewidencjonowaniem.**

Ten błąd dotyczy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji .NET. Zasady wymagają wykonania analizy kodu zarządzanego, ale nie jest ona włączona w bieżącym projekcie na kliencie.

**Należy włączyć analizę kodu we {0} właściwościach projektu i skompilować przed zaewidencjonowaniem.**

Ten błąd został zastosowany do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów i projektów sieci Web. Zasady wymagają wykonania analizy kodu zarządzanego, ale nie jest ona włączona w bieżącym projekcie na kliencie.

**Przed zaewidencjonowaniem należy włączyć analizę kodu C/C++ we {0} właściwościach projektu i skompilować ją.**

Ten błąd dotyczy projektów niezarządzanych. Zasady analizy kodu wymagają analizy kodu C/C++, ale nie jest ona włączona w bieżącym projekcie na kliencie.

## <a name="see-also"></a>Zobacz też

- [Błędy aplikacji analizy kodu](../code-quality/code-analysis-application-errors.md)
