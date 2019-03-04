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
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860145"
---
# <a name="list-view-groupby"></a><span data-ttu-id="87bec-102">Vue de liste (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="87bec-102">List View (GroupBy)</span></span>

<span data-ttu-id="87bec-103">Cet exemple montre comment implémenter une vue liste qui sépare les lignes de la liste en groupes.</span><span class="sxs-lookup"><span data-stu-id="87bec-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="87bec-104">Cette vue affiche les propriétés de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets retournés par le [Get-Service](/powershell/module/microsoft.powershell.management/get-service) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="87bec-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="87bec-105">Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="87bec-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="87bec-106">Cet exemple montre comment implémenter une vue liste qui sépare les lignes de la liste en groupes.</span><span class="sxs-lookup"><span data-stu-id="87bec-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="87bec-107">Cette vue affiche les propriétés de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets retournés par le [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="87bec-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="87bec-108">Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="87bec-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="87bec-109">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="87bec-109">To load this formatting file</span></span>

1. <span data-ttu-id="87bec-110">Copiez le code XML à partir de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="87bec-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="87bec-111">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="87bec-111">Save the text file.</span></span> <span data-ttu-id="87bec-112">Veillez à ajouter le `format.ps1xml` extension au fichier pour l’identifier comme un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="87bec-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="87bec-113">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="87bec-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="87bec-114">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87bec-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="87bec-115">Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne peut pas charger cette mise en forme de fichiers en tant que module.</span><span class="sxs-lookup"><span data-stu-id="87bec-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="87bec-116">Montre</span><span class="sxs-lookup"><span data-stu-id="87bec-116">Demonstrates</span></span>

<span data-ttu-id="87bec-117">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="87bec-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="87bec-118">Le [nom](./name-element-for-view-format.md) élément pour la vue.</span><span class="sxs-lookup"><span data-stu-id="87bec-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="87bec-119">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément qui définit quels objets sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="87bec-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="87bec-120">Le [GroupBy](./viewselectedby-element-format.md) élément qui définit comment un nouveau groupe d’objets s’affiche.</span><span class="sxs-lookup"><span data-stu-id="87bec-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="87bec-121">Le [ListControl](./listcontrol-element-format.md) élément qui définit la propriété est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="87bec-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="87bec-122">Le [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) élément qui définit ce qui est affiché dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="87bec-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="87bec-123">Le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément qui définit la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="87bec-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="87bec-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="87bec-124">Example</span></span>

<span data-ttu-id="87bec-125">Le code XML suivant définit un affichage de liste qui commence un nouveau groupe chaque fois que la valeur de la [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) les modifications de propriété.</span><span class="sxs-lookup"><span data-stu-id="87bec-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="87bec-126">Au démarrage de chaque groupe, une étiquette personnalisée s’affiche qui inclut la nouvelle valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="87bec-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="87bec-127">L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets une fois que ce fichier de format est chargé.</span><span class="sxs-lookup"><span data-stu-id="87bec-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="87bec-128">Les lignes vides ajoutées avant et après l’étiquette du groupe sont ajoutés automatiquement par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87bec-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="87bec-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87bec-129">See Also</span></span>

[<span data-ttu-id="87bec-130">Exemples de fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="87bec-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="87bec-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="87bec-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
