---
title: Mode liste (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365138"
---
# <a name="list-view-groupby"></a><span data-ttu-id="d6a3b-102">Vue de liste (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="d6a3b-102">List View (GroupBy)</span></span>

<span data-ttu-id="d6a3b-103">Cet exemple montre comment implémenter un affichage de liste qui sépare les lignes de la liste en groupes.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="d6a3b-104">Ce mode liste affiche les propriétés de [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects retournés par l’applet [de commande obtient-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) .</span><span class="sxs-lookup"><span data-stu-id="d6a3b-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="d6a3b-105">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d6a3b-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d6a3b-106">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="d6a3b-106">To load this formatting file</span></span>

1. <span data-ttu-id="d6a3b-107">Copiez le code XML de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d6a3b-108">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-108">Save the text file.</span></span> <span data-ttu-id="d6a3b-109">Veillez à ajouter l’extension `format.ps1xml` au fichier pour l’identifier comme un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d6a3b-110">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d6a3b-111">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d6a3b-112">Vous devez utiliser le paramètre `prependPath` lorsque vous exécutez l’applet de commande, et vous ne pouvez pas charger ce fichier de mise en forme en tant que module.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d6a3b-113">Illustré</span><span class="sxs-lookup"><span data-stu-id="d6a3b-113">Demonstrates</span></span>

<span data-ttu-id="d6a3b-114">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="d6a3b-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d6a3b-115">Élément [Name](./name-element-for-view-format.md) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d6a3b-116">Élément [ViewSelectedBy](./viewselectedby-element-format.md) qui définit les objets affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d6a3b-117">Élément [GroupBy](./viewselectedby-element-format.md) qui définit le mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="d6a3b-118">Élément [ListControl](./listcontrol-element-format.md) qui définit la propriété qui est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="d6a3b-119">Élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) qui définit ce qui est affiché dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d6a3b-120">Élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) qui définit la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="d6a3b-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="d6a3b-121">Example</span></span>

<span data-ttu-id="d6a3b-122">Le code XML suivant définit un affichage de liste qui démarre un nouveau groupe chaque fois que la valeur de la propriété [System. ServiceProcess. ServiceController. Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) change.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="d6a3b-123">Lorsque chaque groupe est démarré, une étiquette personnalisée s’affiche, qui comprend la nouvelle valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="d6a3b-124">L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="d6a3b-125">Les lignes vides ajoutées avant et après l’étiquette de groupe sont automatiquement ajoutées par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6a3b-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="d6a3b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6a3b-126">See Also</span></span>

[<span data-ttu-id="d6a3b-127">Exemples de mise en forme de fichiers</span><span class="sxs-lookup"><span data-stu-id="d6a3b-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d6a3b-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6a3b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
