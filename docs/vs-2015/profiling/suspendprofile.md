---
title: SuspendProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b40b37c8c0ee97b5d7e0cc33773af140bd1010b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155624"
---
# <a name="suspendprofile"></a>SuspendProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SuspendProfile`Metoda zwiększa licznik wstrzymania/wznawiania dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Level`  
  
 Wskazuje poziom profilu, do którego można zastosować zbieranie danych wydajności. Poniższe moduły wyliczające **PROFILE_CONTROL_LEVEL** mogą służyć do wskazania jednego z trzech poziomów, do których można zastosować zbieranie danych o wydajności:  
  
|Liczeni|Opis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globalne ustawienie poziomu ma wpływ na wszystkie procesy i wątki w przebiegu profilowania.|  
|PROFILE_PROCESSLEVEL|Ustawienie poziomu procesu wpływa na wszystkie wątki, które są częścią określonego procesu.|  
|PROFILE_THREADLEVEL|Ustawienie poziomu profilowania wątku ma wpływ na określony wątek.|  
  
 `dwId`  
  
 Identyfikator procesu lub wątku generowany przez system.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Funkcja wskazuje powodzenie lub niepowodzenie przy użyciu wyliczenia **PROFILE_COMMAND_STATUS** . Zwracana wartość może być jedną z następujących:  
  
|Liczeni|Opis|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Identyfikator elementu profilowania nie istnieje.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Określony poziom profilowania nie istnieje.|  
|PROFILE_ERROR_MODE_NEVER|Tryb profilowania został ustawiony tak, aby nigdy nie był wywoływany przez funkcję.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Nie zaimplementowano jeszcze wywołania funkcji profilowania, poziomu profilowania lub kombinacji wywołania i poziomu.|  
|PROFILE_OK|Wywołanie zakończyło się pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Początkowa wartość licznika Wstrzymanie/wznowienie wynosi 0. Każde wywołanie SuspendProfile dodaje 1 do liczby wstrzymania/wznowienia; Każde wywołanie ResumeProfile odejmuje 1.  
  
 Gdy liczba wstrzymań/wznowień jest większa niż 0, stan wstrzymania/wznowienia dla poziomu jest wyłączony. Gdy liczba jest mniejsza lub równa 0, stan wstrzymania/wznowienia jest włączony.  
  
 Gdy stan uruchomienia/zatrzymania i wstrzymania/wznowienia jest włączony, stan profilowania dla poziomu jest włączony. W przypadku wątku, który ma zostać profilowany, Stany globalne, proces i poziom wątku dla wątku muszą być włączone.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacje o funkcji  
 Nagłówek: zadeklarowany w VSPerf. h  
  
 Biblioteka importowana: VSPerf. lib  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje metodę SuspendProfile. W tym przykładzie przyjęto założenie, że dla procesu lub wątku identyfikowanego przez [PROFILE_CURRENTID](../profiling/profile-currentid.md)zostało wykonane wcześniejsze wywołanie StartProfile.  
  
```  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
