---
title: Mode liste (étiquettes) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362788"
---
# <a name="list-view-labels"></a><span data-ttu-id="7c1ae-102">Vue de liste (Étiquettes)</span><span class="sxs-lookup"><span data-stu-id="7c1ae-102">List View (Labels)</span></span>

<span data-ttu-id="7c1ae-103">Cet exemple montre comment implémenter un affichage de liste qui affiche une étiquette personnalisée pour chaque ligne de la liste.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="7c1ae-104">Ce mode liste affiche les propriétés de [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objet qui est retourné par l’applet de commande de l’applet [de](/powershell/module/Microsoft.PowerShell.Management/Get-Service) commande.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="7c1ae-105">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7c1ae-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="7c1ae-106">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="7c1ae-106">To load this formatting file</span></span>

1. <span data-ttu-id="7c1ae-107">Copiez le code XML de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="7c1ae-108">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-108">Save the text file.</span></span> <span data-ttu-id="7c1ae-109">Veillez à ajouter l’extension `format.ps1xml` au fichier pour l’identifier comme un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="7c1ae-110">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="7c1ae-111">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="7c1ae-112">Vous devez utiliser le paramètre `prependPath` lorsque vous exécutez l’applet de commande, et vous ne pouvez pas charger ce fichier de mise en forme en tant que module.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7c1ae-113">Illustré</span><span class="sxs-lookup"><span data-stu-id="7c1ae-113">Demonstrates</span></span>

<span data-ttu-id="7c1ae-114">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="7c1ae-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="7c1ae-115">Élément [Name](./name-element-for-view-format.md) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="7c1ae-116">Élément [ViewSelectedBy](./viewselectedby-element-format.md) qui définit les objets affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="7c1ae-117">Élément [ListControl](./listcontrol-element-format.md) qui définit la propriété qui est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="7c1ae-118">Élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) qui définit ce qui est affiché dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="7c1ae-119">Élément [label](./label-element-for-listitem-for-listcontrol-format.md) qui définit ce qui est affiché dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="7c1ae-120">Élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) qui définit la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="7c1ae-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c1ae-121">Example</span></span>

<span data-ttu-id="7c1ae-122">Le code XML suivant définit un affichage de liste qui affiche une étiquette personnalisée dans chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="7c1ae-123">Dans ce cas, l’étiquette comprend le nom de la propriété avec les lettres majuscules et le mot « propriété ».</span><span class="sxs-lookup"><span data-stu-id="7c1ae-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="7c1ae-124">Dans chaque ligne, le nom de la propriété est affiché, suivi de la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

<span data-ttu-id="7c1ae-125">L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.</span><span class="sxs-lookup"><span data-stu-id="7c1ae-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="7c1ae-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c1ae-126">See Also</span></span>

[<span data-ttu-id="7c1ae-127">Exemples de mise en forme de fichiers</span><span class="sxs-lookup"><span data-stu-id="7c1ae-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="7c1ae-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c1ae-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
