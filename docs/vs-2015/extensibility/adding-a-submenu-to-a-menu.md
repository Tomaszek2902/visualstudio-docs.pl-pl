---
title: Dodawanie podmenu do menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f458d46395c3a902e62ba5dd4ac7d624c326700c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184889"
---
# <a name="adding-a-submenu-to-a-menu"></a>Dodawanie podmenu do menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik kompiluje się w demonstracji w obszarze [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , pokazując sposób dodawania podmenu do menu **TestMenu** .  
  
 Podmenu to menu pomocnicze, które pojawia się w innym menu. Podmenu może być identyfikowane przez strzałkę, która następuje po jego nazwie. Kliknięcie nazwy powoduje wyświetlenie podmenu i jego poleceń.  
  
 Ten przewodnik tworzy podmenu w menu na pasku menu programu Visual Studio i umieszcza nowe polecenie w podmenu. Przewodnik implementuje również nowe polecenie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Dodawanie podmenu do menu  
  
1. Postępuj zgodnie z instrukcjami w temacie [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , aby utworzyć projekt i element menu. W krokach w tym instruktażu przyjęto założenie, że nazwa projektu VSIX to `TopLevelMenu` .  
  
2. Otwórz TestCommandPackage. vsct. W `<Symbols>` sekcji Dodaj `<IDSymbol>` element dla podmenu, jeden dla grupy podmenu, a drugi dla polecenia, wszystkie w `<GuidSymbol>` węźle o nazwie "guidTopLevelMenuCmdSet". Jest to ten sam węzeł, który zawiera `<IDSymbol>` element menu najwyższego poziomu.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3. Dodaj nowo utworzone podmenu do `<Menus>` sekcji.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Para identyfikator GUID/identyfikator elementu nadrzędnego określa grupę menu, która została wygenerowana podczas [dodawania menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)i jest elementem podrzędnym menu najwyższego poziomu.  
  
4. Dodaj grupę menu zdefiniowaną w kroku 2 do `<Groups>` sekcji i ustaw ją jako podrzędną w podmenu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5. Dodaj nowy `<Button>` element do sekcji, `<Buttons>` Aby zdefiniować polecenie utworzone w kroku 2 jako element w podmenu.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6. Skompiluj rozwiązanie i Rozpocznij debugowanie. Powinno być widoczne wystąpienie eksperymentalne.  
  
7. Kliknij przycisk **TestMenu** , aby wyświetlić nowe podmenu o nazwie **Sub podmenu**. Kliknij przycisk **podmenu** , aby otworzyć podmenu i wyświetlić nowe polecenie, **podpolecenia testu**. Zwróć uwagę, że kliknięcie **polecenia Testuj sub** nic nie robi.  
  
## <a name="adding-a-command"></a>Dodawanie polecenia  
  
1. Otwórz TestCommand.cs i Dodaj następujący identyfikator polecenia po istniejącym IDENTYFIKATORze polecenia.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2. Dodaj polecenie sub. Znajdź konstruktora poleceń. Dodaj następujące wiersze tuż po wywołaniu `AddCommand` metody.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`Program obsługi poleceń zostanie zdefiniowany później. Konstruktor powinien teraz wyglądać następująco:  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3. Dodaj SubItemCallback (). Jest to metoda wywoływana, gdy zostanie kliknięte nowe polecenie w podmenu.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.  
  
5. W menu **TestMenu** kliknij pozycję **sub menu** , a następnie kliknij pozycję **Testuj polecenie sub**. Zostanie wyświetlone okno komunikatu z tekstem "polecenie testowe wewnątrz TestCommand. SubItemCallback ()".  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
