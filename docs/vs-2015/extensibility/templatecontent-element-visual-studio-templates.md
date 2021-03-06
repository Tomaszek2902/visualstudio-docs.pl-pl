---
title: TemplateContent, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe87bff62c1044442b579664fb789f918a2e6c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186465"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa zawartość szablonu.  
  
 \<VSTemplate>  
 \<TemplateContent>  
  
## <a name="syntax"></a>Składnia  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Określa, czy rozwiązanie ma zostać skompilowane po utworzeniu projektu na podstawie szablonu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa organizację i zawartość szablonów wieloprojektowych.|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa pliki lub katalogi, które mają zostać dodane do projektu.|  
|[Dokumentacja](../extensibility/references-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa odwołania do zestawów wymagane dla szablonu elementu.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Element opcjonalny.<br /><br /> Określa plik zawarty w szablonie.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa wszelkie parametry niestandardowe, które mają być używane podczas tworzenia projektu lub elementu z szablonu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablonu elementu lub zestawu startowego.|  
  
## <a name="remarks"></a>Uwagi  
 `TemplateContent` jest elementem wymaganym.  
  
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
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
