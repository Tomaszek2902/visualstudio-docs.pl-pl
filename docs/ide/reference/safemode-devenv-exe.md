---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593593"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Uruchamia program Visual Studio w trybie awaryjnym, ładując tylko domyślne środowisko i usługi.

## <a name="syntax"></a>Składnia

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Uwagi

Ten przełącznik zapobiega ładowaniu wszystkich pakietów VSPackage innych firm podczas uruchamiania programu Visual Studio, co pozwala na stabilne wykonanie.

## <a name="example"></a>Przykład

W poniższym przykładzie program Visual Studio jest uruchamiany w trybie awaryjnym.

```shell
devenv /safemode
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
