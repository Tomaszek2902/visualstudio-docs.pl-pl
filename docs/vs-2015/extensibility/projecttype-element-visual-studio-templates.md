---
title: ProjectType — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b01dd370fe5e3d7a5207363c5ab7ec4f2a0254c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783052"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klasyfikuje szablon projektu tak, aby pojawił się pod określoną grupą w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .  
  
> [!WARNING]
> Szablony projektów są obsługiwane w języku C++, począwszy od programu Visual Studio 2012. Nie są one obsługiwane w języku C++ w programie Visual Studio 2010 i starszych wersjach.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectType>  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Ta wartość określa typ projektu, który zostanie utworzony przez szablon, i musi zawierać jedną z następujących wartości:  
  
- `CSharp`: Określa, że szablon tworzy [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekt lub element.  
  
- `VisualBasic`: Określa, że szablon tworzy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekt lub element.  
  
- `Web`: Określa, że szablon tworzy projekt lub element sieci Web. Jeśli `ProjectType` element zawiera tę wartość, język projektu lub elementu jest zdefiniowany w [elemencie ProjectSubType (szablony Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Uwagi  
 `ProjectType` jest wymaganym elementem podrzędnym `TemplateData` .  
  
 Wartość `ProjectType` elementu określa, gdzie szablon znajduje się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** . Na przykład szablon o `ProjectType` wartości `CSharp` jest wyświetlany w węźle **Visual C#** w oknie dialogowym **Nowy projekt** .  
  
 Podtyp szablonu można określić za pomocą elementu [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) .  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType, element (szablony Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
