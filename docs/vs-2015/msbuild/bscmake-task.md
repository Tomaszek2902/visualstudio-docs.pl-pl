---
title: BscMake — Zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684543"
---
# <a name="bscmake-task"></a>BscMake — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WAŻNE
> BSCMAKE nie jest już używana przez środowisko IDE programu Visual Studio. Ponieważ program Visual Studio 2008, informacje o przeglądaniu są automatycznie przechowywane w pliku. sdf w folderze rozwiązania.  
  
 Pakuje narzędzie do konserwacji informacji przeglądarki Microsoft (bscmake.exe).  Narzędzie bscmake.exe kompiluje plik informacji o przeglądaniu (BSC) z plików przeglądarki źródłowej (. sbr), które są tworzone podczas kompilacji. Użyj **Przeglądarka obiektów** , aby wyświetlić plik. BSC. Aby uzyskać więcej informacji, zobacz [BSCMAKE Reference](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **BSCMAKE** . Większość parametrów zadań odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji określona w wierszu polecenia. Na przykład "/*opcja1*  / *opcja2*  / *Option #*". Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **BSCMAKE** .<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [opcjach BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Plik_wyjściowy**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcja w [opcjach BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , wymusza nieprzyrostową kompilację. Pełna, nieprzyrostowa kompilacja odbywa się niezależnie od tego, czy plik. bsc istnieje i uniemożliwia obcinanie plików. sbr.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji w [opcjach BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Źródła**|Opcjonalny parametr **ITaskItem []** .<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/nologo** w opcjach [BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
