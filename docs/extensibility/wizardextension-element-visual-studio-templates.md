---
title: WizardExtension —, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd81b32861114d654aa794b992826589406b1df9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740373"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension — Element (szablony Visual Studio)
Zawiera elementy rejestracji do dostosowywania Kreatora szablonów.

 \<VSTemplate> ... \<WizardExtension>

## <a name="syntax"></a>Składnia

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Zestaw](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Element wymagany.<br /><br /> Określa nazwę lub silną nazwę zestawu, który pojawia się w globalnej pamięci podręcznej zestawów. Element musi zawierać co najmniej jeden `Assembly` element `WizardExtension` .|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Element wymagany.<br /><br /> W pełni kwalifikowana nazwa klasy, która implementuje `IWizard` interfejs. Element musi zawierać co najmniej jeden `FullClassName` element `WizardExtension` .|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Zawiera wszystkie metadane szablonu projektu, szablonu elementu lub zestawu startowego.|

## <a name="remarks"></a>Uwagi
 `WizardExtension` jest opcjonalnym elementem podrzędnym `VSTemplate` .

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane standardowego szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji systemu Windows.

```
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [Porady: korzystanie z kreatora z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
