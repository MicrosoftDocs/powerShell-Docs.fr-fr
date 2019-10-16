---
title: Création d’un affichage de liste | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368978"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="59d69-102">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="59d69-102">Creating a List View</span></span>

<span data-ttu-id="59d69-103">Un affichage de liste affiche des données dans une seule colonne (dans l’ordre séquentiel).</span><span class="sxs-lookup"><span data-stu-id="59d69-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="59d69-104">Les données affichées dans la liste peuvent être la valeur d’une propriété .NET ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="59d69-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="59d69-105">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="59d69-105">A List View Display</span></span>

<span data-ttu-id="59d69-106">La sortie suivante montre comment Windows PowerShell affiche les propriétés de [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objets qui sont retournés par l’applet de commande [obtient-service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="59d69-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="59d69-107">Dans cet exemple, trois objets ont été retournés, chaque objet étant séparé de l’objet précédent par une ligne vide.</span><span class="sxs-lookup"><span data-stu-id="59d69-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="59d69-108">Définition de la vue Liste</span><span class="sxs-lookup"><span data-stu-id="59d69-108">Defining the List View</span></span>

<span data-ttu-id="59d69-109">Le code XML suivant montre le schéma de la vue liste pour afficher plusieurs propriétés de [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet.</span><span class="sxs-lookup"><span data-stu-id="59d69-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="59d69-110">Vous devez spécifier chaque propriété que vous souhaitez afficher en mode liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="59d69-111">Les éléments XML suivants sont utilisés pour définir un mode liste :</span><span class="sxs-lookup"><span data-stu-id="59d69-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="59d69-112">L’élément [View](./view-element-format.md) est l’élément parent de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="59d69-113">(Il s’agit du même élément parent pour les vues de contrôle table, larges et personnalisées.)</span><span class="sxs-lookup"><span data-stu-id="59d69-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="59d69-114">L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="59d69-115">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="59d69-115">This element is required for all views.</span></span>

- <span data-ttu-id="59d69-116">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="59d69-117">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="59d69-117">This element is required.</span></span>

- <span data-ttu-id="59d69-118">L’élément [GroupBy](./groupby-element-for-view-format.md) définit le moment où un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="59d69-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="59d69-119">Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="59d69-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="59d69-120">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-120">This element is optional.</span></span>

- <span data-ttu-id="59d69-121">L’élément [Controls](./controls-element-for-view-format.md) définit les contrôles personnalisés qui sont définis par l’affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="59d69-122">Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="59d69-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="59d69-123">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-123">This element is optional.</span></span> <span data-ttu-id="59d69-124">Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="59d69-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="59d69-125">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="59d69-126">L’élément [ListControl](./listcontrol-element-format.md) définit ce qui est affiché dans la vue et comment il est mis en forme.</span><span class="sxs-lookup"><span data-stu-id="59d69-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="59d69-127">Comme pour toutes les autres vues, un affichage de liste peut afficher les valeurs des propriétés d’objet ou les valeurs générées par le script.</span><span class="sxs-lookup"><span data-stu-id="59d69-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="59d69-128">Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage de liste simple, consultez [mode liste (de base)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="59d69-129">Fournir des définitions pour votre mode liste</span><span class="sxs-lookup"><span data-stu-id="59d69-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="59d69-130">Les affichages de liste peuvent fournir une ou plusieurs définitions à l’aide des éléments enfants de l’élément [ListControl](./listcontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="59d69-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="59d69-131">En règle générale, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="59d69-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="59d69-132">Dans l’exemple suivant, la vue fournit une définition unique qui affiche plusieurs propriétés de [System. Diagnostics. Process ? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) , objet.</span><span class="sxs-lookup"><span data-stu-id="59d69-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="59d69-133">Un affichage de liste peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple).</span><span class="sxs-lookup"><span data-stu-id="59d69-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="59d69-134">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une vue Liste :</span><span class="sxs-lookup"><span data-stu-id="59d69-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="59d69-135">L’élément [ListControl](./listcontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="59d69-136">L’élément [ListEntries](./listentries-element-for-listcontrol-format.md) fournit les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="59d69-137">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="59d69-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="59d69-138">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="59d69-138">This element is required.</span></span>

- <span data-ttu-id="59d69-139">L’élément [ListEntry](./listentry-element-for-listcontrol-format.md) fournit une définition de la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="59d69-140">Au moins un [ListEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="59d69-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="59d69-141">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="59d69-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="59d69-142">L’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="59d69-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="59d69-143">Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [ListEntry](./listentry-element-for-listcontrol-format.md) qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="59d69-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="59d69-144">L’élément [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) spécifie les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="59d69-145">L’élément [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) spécifie une propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="59d69-146">Un affichage de liste doit spécifier au moins une propriété ou un script.</span><span class="sxs-lookup"><span data-stu-id="59d69-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="59d69-147">Il n’existe pas de limite maximale pour le nombre de lignes qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="59d69-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="59d69-148">L’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="59d69-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="59d69-149">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="59d69-150">L’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="59d69-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="59d69-151">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="59d69-152">L’élément [label](./label-element-for-listitem-for-listcontrol-format.md) spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="59d69-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="59d69-153">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-153">This element is optional.</span></span> <span data-ttu-id="59d69-154">Si aucune étiquette n’est spécifiée, le nom de la propriété ou du script est affiché.</span><span class="sxs-lookup"><span data-stu-id="59d69-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="59d69-155">Pour obtenir un exemple complet, consultez [affichage de liste (étiquettes)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="59d69-156">L’élément [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) spécifie une condition qui doit exister pour que la ligne soit affichée.</span><span class="sxs-lookup"><span data-stu-id="59d69-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="59d69-157">Pour plus d’informations sur l’ajout de conditions à l’affichage de liste, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="59d69-158">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-158">This element is optional.</span></span>

- <span data-ttu-id="59d69-159">L’élément [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) spécifie un modèle qui est utilisé pour afficher la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="59d69-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="59d69-160">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-160">This element is optional.</span></span>

<span data-ttu-id="59d69-161">Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage de liste simple, consultez [mode liste (de base)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="59d69-162">Définition des objets qui utilisent le mode liste</span><span class="sxs-lookup"><span data-stu-id="59d69-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="59d69-163">Il existe deux façons de définir les objets .NET qui utilisent le mode liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="59d69-164">Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="59d69-165">Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="59d69-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="59d69-166">L’exemple suivant montre comment définir les objets qui sont affichés par le mode liste à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="59d69-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="59d69-167">Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="59d69-168">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :</span><span class="sxs-lookup"><span data-stu-id="59d69-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="59d69-169">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="59d69-170">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie l’objet .net qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="59d69-171">Le nom complet du type .NET est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="59d69-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="59d69-172">Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="59d69-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="59d69-173">Pour obtenir un exemple de fichier de mise en forme complet, consultez [vue liste (de base)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="59d69-174">L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="59d69-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="59d69-175">Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets.</span><span class="sxs-lookup"><span data-stu-id="59d69-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="59d69-176">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="59d69-177">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :</span><span class="sxs-lookup"><span data-stu-id="59d69-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="59d69-178">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="59d69-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="59d69-179">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="59d69-180">Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="59d69-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="59d69-181">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue liste à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="59d69-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="59d69-182">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="59d69-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="59d69-183">Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="59d69-184">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par une définition spécifique de la vue Liste :</span><span class="sxs-lookup"><span data-stu-id="59d69-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="59d69-185">L’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="59d69-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="59d69-186">L’élément [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) spécifie l’objet .net qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="59d69-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="59d69-187">Lors de l’utilisation de cet élément, le nom complet du type .NET est requis.</span><span class="sxs-lookup"><span data-stu-id="59d69-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="59d69-188">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="59d69-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="59d69-189">L’élément [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="59d69-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="59d69-190">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="59d69-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="59d69-191">L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="59d69-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="59d69-192">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="59d69-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="59d69-193">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="59d69-194">Affichage des groupes d’objets dans une liste</span><span class="sxs-lookup"><span data-stu-id="59d69-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="59d69-195">Vous pouvez séparer les objets qui sont affichés par le mode liste en groupes.</span><span class="sxs-lookup"><span data-stu-id="59d69-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="59d69-196">Cela ne signifie pas que vous définissez un groupe, mais uniquement que Windows PowerShell démarre un nouveau groupe chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="59d69-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="59d69-197">Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) change.</span><span class="sxs-lookup"><span data-stu-id="59d69-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="59d69-198">Les éléments XML suivants sont utilisés pour définir le moment où un groupe est démarré :</span><span class="sxs-lookup"><span data-stu-id="59d69-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="59d69-199">L’élément [GroupBy](./groupby-element-for-view-format.md) définit la propriété ou le script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.</span><span class="sxs-lookup"><span data-stu-id="59d69-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="59d69-200">L’élément [PropertyName](./propertyname-element-for-groupby-format.md) spécifie la propriété qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="59d69-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="59d69-201">Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="59d69-202">L’élément [scriptblock](./scriptblock-element-for-groupby-format.md) spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="59d69-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="59d69-203">Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="59d69-204">L’élément [label](./label-element-for-groupby-format.md) définit une étiquette qui s’affiche au début de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="59d69-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="59d69-205">En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="59d69-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="59d69-206">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-206">This element is optional.</span></span>

- <span data-ttu-id="59d69-207">L’élément [CustomControl](./customcontrol-element-for-groupby-format.md) définit un contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="59d69-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="59d69-208">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-208">This element is optional.</span></span>

- <span data-ttu-id="59d69-209">L’élément [CustomControlName](./customcontrolname-element-for-groupby-format.md) spécifie un contrôle d’affichage ou commun qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="59d69-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="59d69-210">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="59d69-210">This element is optional.</span></span>

<span data-ttu-id="59d69-211">Pour obtenir un exemple de fichier de mise en forme complet qui définit des groupes, consultez [vue liste (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="59d69-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="59d69-212">Utilisation de chaînes de format</span><span class="sxs-lookup"><span data-stu-id="59d69-212">Using Format Strings</span></span>

<span data-ttu-id="59d69-213">La mise en forme des chaînes peut être ajoutée à une vue pour définir davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="59d69-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="59d69-214">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la propriété `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="59d69-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="59d69-215">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="59d69-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="59d69-216">L’élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="59d69-217">L’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="59d69-218">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="59d69-219">L’élément [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="59d69-220">L’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="59d69-221">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="59d69-222">Dans l’exemple suivant, la méthode `ToString` est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="59d69-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="59d69-223">Les scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="59d69-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="59d69-224">Par conséquent, si un objet a une méthode, telle que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="59d69-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="59d69-225">L’élément XML suivant peut être utilisé pour appeler la méthode `ToString` :</span><span class="sxs-lookup"><span data-stu-id="59d69-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="59d69-226">L’élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="59d69-227">L’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="59d69-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="59d69-228">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="59d69-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="59d69-229">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59d69-229">See Also</span></span>

[<span data-ttu-id="59d69-230">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59d69-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
