---
title: Narzędzie CreatePkgDef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709167"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
Przyjmuje plik. dll rozszerzenia programu Visual Studio jako parametr i tworzy plik *. pkgdef* , który towarzyszy plikowi *. dll* . Plik *. pkgdef* zawiera wszystkie informacje, które w przeciwnym razie byłyby zapisywane w rejestrze systemowym, gdy rozszerzenie zostanie zainstalowane.

> [!NOTE]
> Większość szablonów projektu, które są zawarte w zestawie SDK programu Visual Studio, automatycznie tworzy pliki *pkgdef* jako część procesu kompilacji. Ten dokument jest przeznaczony dla użytkowników, którzy chcą ręcznie tworzyć pakiety, lub konwertować istniejące pakiety do użycia *. pkgdef*  .

## <a name="syntax"></a>Składnia

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumenty
**/out = &lt; filename&gt;**\
Wymagany. Ustawia nazwę pliku wyjściowego *. pkgdef* na &lt; filename &gt; .

**/codebase**\
Opcjonalny. Wymusza rejestrację za pomocą narzędzia **codebase** .

**/Assembly**\
Wymusza rejestrację za pomocą narzędzia **zestawu** .

**&lt;AssemblyPath&gt;**\
Ścieżka do pliku *dll* , z którego chcesz wygenerować plik *. pkgdef*.

## <a name="remarks"></a>Uwagi
Wdrożenie rozszerzenia przy użyciu plików *. pkgdef* zastępuje wymagania dotyczące rejestru wcześniejszych wersji programu Visual Studio.

::: moniker range=">=vs-2019"

Pliki *. pkgdef* muszą być zainstalowane w jednej z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Jeśli folder instalacji to *%LocalAppData%\Microsoft\Visual Studio\16.0\Extensions \\ *, rozszerzenie jest rozpoznawane przez program Visual Studio, ale jest domyślnie wyłączone. Użytkownik może włączyć rozszerzenie przy użyciu opcji **Zarządzaj rozszerzeniami**.

Jeśli folder instalacyjny to *%VSInstallDir%\Common7\IDE\Extensions \\ *, rozszerzenie jest domyślnie włączone.

> [!NOTE]
> Narzędzia do **zarządzania rozszerzeniami** nie można użyć w celu uzyskania dostępu do rozszerzenia, chyba że zostanie ono zainstalowane jako część pakietu VSIX.

::: moniker-end

::: moniker range="vs-2017"

Pliki *. pkgdef* muszą być zainstalowane w jednej z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Jeśli folder instalacji to *%LocalAppData%\Microsoft\Visual Studio\15.0\Extensions \\ *, rozszerzenie jest rozpoznawane przez program Visual Studio, ale jest domyślnie wyłączone. Użytkownik może włączyć rozszerzenie przy użyciu **rozszerzeń i aktualizacji**.

Jeśli folder instalacyjny to *%VSInstallDir%\Common7\IDE\Extensions \\ *, rozszerzenie jest domyślnie włączone.

> [!NOTE]
> Narzędzia **rozszerzenia i aktualizacje** nie można użyć w celu uzyskania dostępu do rozszerzenia, chyba że zostanie ono zainstalowane jako część pakietu VSIX.

::: moniker-end

## <a name="see-also"></a>Zobacz też
- [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
