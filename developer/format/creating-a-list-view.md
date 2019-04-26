---
title: Création d’une vue liste | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066853"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="ab3d5-102">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="ab3d5-102">Creating a List View</span></span>

<span data-ttu-id="ab3d5-103">Une vue de liste affiche les données dans une seule colonne (dans un ordre séquentiel).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="ab3d5-104">Les données affichées dans la liste peuvent être la valeur d’une propriété .NET ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="ab3d5-105">Un affichage de la vue liste</span><span class="sxs-lookup"><span data-stu-id="ab3d5-105">A List View Display</span></span>

<span data-ttu-id="ab3d5-106">La sortie suivante montre comment Windows PowerShell affiche les propriétés de [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets qui sont retournés par la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="ab3d5-107">Dans cet exemple, trois objets ont été retournés, où chaque objet séparé à partir de l’objet précédent par une ligne vide.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="ab3d5-108">Définition de la vue liste</span><span class="sxs-lookup"><span data-stu-id="ab3d5-108">Defining the List View</span></span>

<span data-ttu-id="ab3d5-109">Le code XML suivant montre le schéma de la vue liste permettant d’afficher plusieurs propriétés de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ab3d5-110">Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
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
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="ab3d5-111">Les éléments XML suivants sont utilisés pour définir une vue de liste :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="ab3d5-112">Le [vue](./view-element-format.md) élément est l’élément parent de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="ab3d5-113">(Ceci est le même élément parent pour la table, les vues de contrôle de large et personnalisées).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="ab3d5-114">Le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="ab3d5-115">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-115">This element is required for all views.</span></span>

- <span data-ttu-id="ab3d5-116">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="ab3d5-117">Cet élément est requis.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-117">This element is required.</span></span>

- <span data-ttu-id="ab3d5-118">Le [GroupBy](./groupby-element-for-view-format.md) élément définit quand un nouveau groupe d’objets s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="ab3d5-119">Un nouveau groupe est démarré à chaque modification de la valeur d’une propriété spécifique ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ab3d5-120">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-120">This element is optional.</span></span>

- <span data-ttu-id="ab3d5-121">Le [contrôles](./controls-element-for-view-format.md) élément définit les contrôles personnalisés qui sont définies par l’affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="ab3d5-122">Contrôles vous permettent de préciser la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="ab3d5-123">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-123">This element is optional.</span></span> <span data-ttu-id="ab3d5-124">Une vue peut définir ses propres contrôles personnalisés, ou il peut utiliser des contrôles communs qui peuvent être utilisées par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="ab3d5-125">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="ab3d5-126">Le [ListControl](./listcontrol-element-format.md) élément définit ce qui est affiché dans la vue et la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="ab3d5-127">Comme pour toutes les autres vues, une vue de liste peut afficher les valeurs des propriétés de l’objet ou les valeurs générées par script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="ab3d5-128">Pour obtenir un exemple d’un fichier de mise en forme complète qui définit une vue de liste simple, consultez [vue liste (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="ab3d5-129">Fournissant des définitions de votre affichage de liste</span><span class="sxs-lookup"><span data-stu-id="ab3d5-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="ab3d5-130">Affichages de liste peuvent fournir une ou plusieurs définitions en utilisant les éléments enfants de la [ListControl](./listcontrol-element-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="ab3d5-131">En règle générale, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="ab3d5-132">Dans l’exemple suivant, la vue fournit une définition unique qui permet d’afficher plusieurs propriétés de la [System.Diagnostics.Process ? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="ab3d5-133">Un affichage de liste permet d’afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
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
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="ab3d5-134">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour un affichage de liste :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="ab3d5-135">Le [ListControl](./listcontrol-element-format.md) élément et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="ab3d5-136">Le [situés](./listentries-element-for-listcontrol-format.md) élément fournit les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="ab3d5-137">Dans la plupart des cas, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="ab3d5-138">Cet élément est requis.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-138">This element is required.</span></span>

- <span data-ttu-id="ab3d5-139">Le [ListEntry](./listentry-element-for-listcontrol-format.md) élément fournit une définition de la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="ab3d5-140">Au moins un [ListEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe aucune limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="ab3d5-141">Dans la plupart des cas, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="ab3d5-142">Le [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="ab3d5-143">Cet élément est facultatif et est nécessaire uniquement lorsque vous définissez plusieurs [ListEntry](./listentry-element-for-listcontrol-format.md) éléments qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="ab3d5-144">Le [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) élément spécifie les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="ab3d5-145">Le [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) élément spécifie une propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="ab3d5-146">Une vue de liste doit spécifier au moins une propriété ou le script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="ab3d5-147">Il n’existe aucune limite maximale pour le nombre de lignes qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="ab3d5-148">Le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ab3d5-149">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ab3d5-150">Le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ab3d5-151">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="ab3d5-152">Le [étiquette](./label-element-for-listitem-for-listcontrol-format.md) élément spécifie l’étiquette qui s’affiche à gauche de la valeur de propriété ou un script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="ab3d5-153">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-153">This element is optional.</span></span> <span data-ttu-id="ab3d5-154">Si une étiquette n’est pas spécifiée, le nom de la propriété ou le script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="ab3d5-155">Pour obtenir un exemple complet, consultez [vue liste (étiquettes)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="ab3d5-156">Le [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) élément spécifie une condition qui doit exister pour la ligne à afficher.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="ab3d5-157">Pour plus d’informations sur l’ajout de conditions à l’affichage de liste, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="ab3d5-158">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-158">This element is optional.</span></span>

- <span data-ttu-id="ab3d5-159">Le [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle qui est utilisé pour afficher la valeur de la propriété ou un script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="ab3d5-160">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-160">This element is optional.</span></span>

<span data-ttu-id="ab3d5-161">Pour obtenir un exemple d’un fichier de mise en forme complète qui définit une vue de liste simple, consultez [vue liste (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="ab3d5-162">Définition des objets qui utilisent la vue liste</span><span class="sxs-lookup"><span data-stu-id="ab3d5-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="ab3d5-163">Il existe deux façons de définir les objets .NET utilisent l’affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="ab3d5-164">Vous pouvez utiliser la [ViewSelectedBy](./viewselectedby-element-format.md) élément pour définir les objets qui peuvent être affichées par toutes les définitions de la vue, ou vous pouvez utiliser la [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément pour définir quels objets sont affichés par un définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="ab3d5-165">Dans la plupart des cas, une vue n'a qu’une seule définition, donc les objets sont généralement définies par le [ViewSelectedBy](./viewselectedby-element-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="ab3d5-166">L’exemple suivant montre comment définir les objets qui sont affichés par la vue de liste en utilisant le [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ab3d5-167">Il n’existe aucune limite au nombre de [TypeName](./typename-element-for-viewselectedby-format.md) éléments que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="ab3d5-168">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de liste :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="ab3d5-169">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ab3d5-170">Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie l’objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="ab3d5-171">Le nom de type .NET complet est requis.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="ab3d5-172">Vous devez spécifier au moins un type ou la sélection définie pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ab3d5-173">Pour obtenir un exemple d’un fichier de mise en forme complète, consultez [vue liste (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="ab3d5-174">L’exemple suivant utilise le [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ab3d5-175">Utiliser des jeux de sélection où vous avez un ensemble d’objets qui sont affichés à l’aide de plusieurs vues, comme lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets liés.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="ab3d5-176">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définissant des ensembles de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="ab3d5-177">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de liste :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="ab3d5-178">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ab3d5-179">Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="ab3d5-180">Vous devez spécifier au moins un jeu de sélection ou de type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ab3d5-181">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de liste en utilisant le [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="ab3d5-182">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un ensemble de la sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="ab3d5-183">Pour plus d’informations sur la façon de créer une sélection des conditions, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="ab3d5-184">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de la vue de liste :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="ab3d5-185">Le [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="ab3d5-186">Le [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) élément spécifie l’objet .NET qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="ab3d5-187">Lorsque vous utilisez cet élément, le nom de type .NET complet est requis.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="ab3d5-188">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ab3d5-189">Le [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie un ensemble d’objets qui peuvent être affichées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="ab3d5-190">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ab3d5-191">Le [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie une condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ab3d5-192">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="ab3d5-193">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="ab3d5-194">Affichage des groupes d’objets dans une vue liste</span><span class="sxs-lookup"><span data-stu-id="ab3d5-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="ab3d5-195">Vous pouvez séparer les objets qui sont affichés par la vue de liste en groupes.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="ab3d5-196">Cela ne signifie pas la que vous définissez un groupe, uniquement que PowerShell Windows démarre un nouveau groupe chaque fois que la valeur d’une propriété spécifique ou un script change.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ab3d5-197">Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) les modifications de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="ab3d5-198">Les éléments XML suivants sont utilisés pour définir le démarrage d’un groupe :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="ab3d5-199">Le [GroupBy](./groupby-element-for-view-format.md) élément définit la propriété ou un script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="ab3d5-200">Le [PropertyName](./propertyname-element-for-groupby-format.md) élément spécifie la propriété qui commence un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="ab3d5-201">Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="ab3d5-202">Le [ScriptBlock](./scriptblock-element-for-groupby-format.md) élément spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="ab3d5-203">Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="ab3d5-204">Le [étiquette](./label-element-for-groupby-format.md) élément définit une étiquette qui s’affiche au début de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="ab3d5-205">En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="ab3d5-206">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-206">This element is optional.</span></span>

- <span data-ttu-id="ab3d5-207">Le [CustomControl](./customcontrol-element-for-groupby-format.md) élément définit un contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="ab3d5-208">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-208">This element is optional.</span></span>

- <span data-ttu-id="ab3d5-209">Le [CustomControlName](./customcontrolname-element-for-groupby-format.md) élément spécifie un commun ou d’afficher le contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="ab3d5-210">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-210">This element is optional.</span></span>

<span data-ttu-id="ab3d5-211">Pour obtenir un exemple d’un fichier de mise en forme complète qui définit les groupes, consultez [vue liste (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d5-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="ab3d5-212">À l’aide de chaînes de Format</span><span class="sxs-lookup"><span data-stu-id="ab3d5-212">Using Format Strings</span></span>

<span data-ttu-id="ab3d5-213">Mise en forme de chaînes peuvent être ajoutés à une vue pour définir plus précisément la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="ab3d5-214">L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="ab3d5-215">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="ab3d5-216">Le [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) élément spécifie les données qui sont affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="ab3d5-217">Le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="ab3d5-218">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ab3d5-219">Le [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="ab3d5-220">Le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ab3d5-221">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="ab3d5-222">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="ab3d5-223">Scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="ab3d5-224">Par conséquent, si un objet possède une méthode, tel que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="ab3d5-225">L’élément XML suivant peut être utilisé pour appeler le `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="ab3d5-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="ab3d5-226">Le [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) élément spécifie les données qui sont affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="ab3d5-227">Le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ab3d5-228">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ab3d5-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3d5-229">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab3d5-229">See Also</span></span>

[<span data-ttu-id="ab3d5-230">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab3d5-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
