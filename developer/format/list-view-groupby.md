---
title: Mode (GroupBy) liste | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794437"
---
# <a name="list-view-groupby"></a><span data-ttu-id="47bdb-102">Vue de liste (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="47bdb-102">List View (GroupBy)</span></span>

<span data-ttu-id="47bdb-103">Cet exemple montre comment implémenter une vue liste qui sépare les lignes de la liste en groupes.</span><span class="sxs-lookup"><span data-stu-id="47bdb-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="47bdb-104">Cette vue affiche les propriétés de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets retournés par le [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47bdb-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="47bdb-105">Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="47bdb-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="47bdb-106">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="47bdb-106">To load this formatting file</span></span>

1. <span data-ttu-id="47bdb-107">Copiez le code XML à partir de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="47bdb-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="47bdb-108">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="47bdb-108">Save the text file.</span></span> <span data-ttu-id="47bdb-109">Veillez à ajouter le `format.ps1xml` extension au fichier pour l’identifier comme un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="47bdb-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="47bdb-110">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="47bdb-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="47bdb-111">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47bdb-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="47bdb-112">Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne peut pas charger cette mise en forme de fichiers en tant que module.</span><span class="sxs-lookup"><span data-stu-id="47bdb-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="47bdb-113">Montre</span><span class="sxs-lookup"><span data-stu-id="47bdb-113">Demonstrates</span></span>

<span data-ttu-id="47bdb-114">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="47bdb-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="47bdb-115">Le [nom](./name-element-for-view-format.md) élément pour la vue.</span><span class="sxs-lookup"><span data-stu-id="47bdb-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="47bdb-116">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément qui définit quels objets sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="47bdb-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="47bdb-117">Le [GroupBy](./viewselectedby-element-format.md) élément qui définit comment un nouveau groupe d’objets s’affiche.</span><span class="sxs-lookup"><span data-stu-id="47bdb-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="47bdb-118">Le [ListControl](./listcontrol-element-format.md) élément qui définit la propriété est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="47bdb-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="47bdb-119">Le [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) élément qui définit ce qui est affiché dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="47bdb-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="47bdb-120">Le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément qui définit la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="47bdb-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="47bdb-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="47bdb-121">Example</span></span>

<span data-ttu-id="47bdb-122">Le code XML suivant définit un affichage de liste qui commence un nouveau groupe chaque fois que la valeur de la [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) les modifications de propriété.</span><span class="sxs-lookup"><span data-stu-id="47bdb-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="47bdb-123">Au démarrage de chaque groupe, une étiquette personnalisée s’affiche qui inclut la nouvelle valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="47bdb-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="47bdb-124">L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets une fois que ce fichier de format est chargé.</span><span class="sxs-lookup"><span data-stu-id="47bdb-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="47bdb-125">Les lignes vides ajoutées avant et après l’étiquette du groupe sont ajoutés automatiquement par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47bdb-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="47bdb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47bdb-126">See Also</span></span>

[<span data-ttu-id="47bdb-127">Exemples de fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="47bdb-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="47bdb-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="47bdb-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
