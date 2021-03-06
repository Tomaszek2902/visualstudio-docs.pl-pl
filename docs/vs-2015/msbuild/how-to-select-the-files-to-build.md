---
title: 'Instrukcje: Wybieranie plików do skompilowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0968dd8914b99e8d47ef1364231059175aaf73fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780323"
---
# <a name="how-to-select-the-files-to-build"></a>Porady: wybieranie plików do kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania projektu, który zawiera kilka plików, każdy plik można wyświetlić osobno w pliku projektu lub użyć symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżonym zestawie katalogów.  
  
## <a name="specifying-inputs"></a>Określanie danych wejściowych  
 Elementy reprezentują dane wejściowe dla kompilacji. Aby uzyskać więcej informacji o elementach, zobacz [Items](../msbuild/msbuild-items.md).  
  
 Aby dołączyć pliki dla kompilacji, muszą one znajdować się na liście elementów w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu. Do list elementów można dodawać wiele plików przez dołączenie pojedynczych plików lub użycie symboli wieloznacznych w celu uwzględnienia wielu plików jednocześnie.  
  
#### <a name="to-declare-items-individually"></a>Aby zadeklarować elementy indywidualnie  
  
- Użyj `Include` atrybutów podobnych do następujących:  
  
     `<CSFile Include="form1.cs"/>`  
  
     oraz  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    > Jeśli elementy w kolekcji elementów nie znajdują się w tym samym katalogu, co plik projektu, należy określić pełną lub względną ścieżkę do elementu. Na przykład: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Aby zadeklarować wiele elementów  
  
- Użyj `Include` atrybutów podobnych do następujących:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     oraz  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Określanie danych wejściowych za pomocą symboli wieloznacznych  
 Można również użyć symboli wieloznacznych, aby rekursywnie uwzględnić wszystkie pliki lub tylko określone pliki z podkatalogów jako dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [Items](../msbuild/msbuild-items.md)  
  
 Poniższe przykłady opierają się na projekcie zawierającym pliki graficzne w następujących katalogach i podkatalogach z plikiem projektu znajdującym się w katalogu projektu:  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Aby dołączyć wszystkie pliki jpg do katalogu obrazów i podkatalogów  
  
- Użyj następującego `Include` atrybutu:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Aby dołączyć wszystkie pliki jpg, zaczynając od "img"  
  
- Użyj następującego `Include` atrybutu:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Aby uwzględnić wszystkie pliki w katalogach z nazwami kończącymi się na "jpgs"  
  
- Użyj jednego z następujących `Include` atrybutów:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     oraz  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Przekazywanie elementów do zadania  
 W pliku projektu można użyć notacji @ () w zadaniach, aby określić całą listę elementów jako dane wejściowe dla kompilacji. Tej notacji można użyć, aby wyświetlić listę wszystkich plików osobno lub użyć symboli wieloznacznych.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Aby użyć wszystkich plików Visual C# lub Visual Basic jako dane wejściowe  
  
- Użyj `Include` atrybutów podobnych do następujących:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     oraz  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
> Aby określić dane wejściowe dla kompilacji, należy użyć symboli wieloznacznych z elementami. nie można określić danych wejściowych przy użyciu `Sources` atrybutu w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadaniach, takich jak [CSC](../msbuild/csc-task.md) lub [VBC](../msbuild/vbc-task.md). Poniższy przykład nie jest prawidłowy w pliku projektu:  
>   
> `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje projekt, który zawiera wszystkie pliki wejściowe osobno.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa symbolu wieloznacznego w celu uwzględnienia wszystkich plików. cs.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Elementy](../msbuild/msbuild-items.md)
