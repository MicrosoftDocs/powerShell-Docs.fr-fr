---
title: Création d’un affichage plus large | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066717"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="d1aff-102">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="d1aff-102">Creating a Wide View</span></span>

<span data-ttu-id="d1aff-103">Un affichage plus large affiche une valeur unique pour chaque objet qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1aff-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="d1aff-104">La valeur affichée peut être la valeur d’une propriété d’objet .NET ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="d1aff-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="d1aff-105">Par défaut, il n’existe aucune étiquette ou un en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="d1aff-106">Un écran d’affichage plus large</span><span class="sxs-lookup"><span data-stu-id="d1aff-106">A Wide View Display</span></span>

<span data-ttu-id="d1aff-107">L’exemple suivant montre comment Windows PowerShell affiche le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet qui est retourné par la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande lors de sa sortie est dirigée vers le [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d1aff-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="d1aff-108">(Par défaut, le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande renvoie une table de vue.) Dans cet exemple, les deux colonnes sont utilisés pour afficher le nom du processus pour chaque objet retourné.</span><span class="sxs-lookup"><span data-stu-id="d1aff-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="d1aff-109">Le nom de propriété de l’objet n’est pas affiché, seule la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d1aff-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="d1aff-110">Définition de la vue large</span><span class="sxs-lookup"><span data-stu-id="d1aff-110">Defining the Wide View</span></span>

<span data-ttu-id="d1aff-111">Le code XML suivant montre le schéma de l’affichage plus large pour le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="d1aff-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="d1aff-112">Les éléments XML suivants sont utilisés pour définir un affichage plus large :</span><span class="sxs-lookup"><span data-stu-id="d1aff-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="d1aff-113">Le [vue](./view-element-format.md) élément est l’élément parent de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1aff-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="d1aff-114">(Ceci est le même élément parent pour la table, liste et les vues de contrôle personnalisé.)</span><span class="sxs-lookup"><span data-stu-id="d1aff-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="d1aff-115">Le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="d1aff-116">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="d1aff-116">This element is required for all views.</span></span>

- <span data-ttu-id="d1aff-117">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="d1aff-118">Cet élément est requis.</span><span class="sxs-lookup"><span data-stu-id="d1aff-118">This element is required.</span></span>

- <span data-ttu-id="d1aff-119">Le [GroupBy](./groupby-element-for-view-format.md) élément définit quand un nouveau groupe d’objets s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1aff-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="d1aff-120">Un nouveau groupe est démarré à chaque modification de la valeur d’une propriété spécifique ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="d1aff-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d1aff-121">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-121">This element is optional.</span></span>

- <span data-ttu-id="d1aff-122">Le [contrôles](./controls-element-for-view-format.md) éléments définit les contrôles personnalisés qui sont définies par l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1aff-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="d1aff-123">Contrôles vous permettent de préciser la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="d1aff-124">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-124">This element is optional.</span></span> <span data-ttu-id="d1aff-125">Une vue peut définir ses propres contrôles personnalisés, ou il peut utiliser des contrôles communs qui peuvent être utilisées par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d1aff-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="d1aff-126">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="d1aff-127">Le [WideControl](./widecontrol-element-format.md) élément et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="d1aff-128">Dans l’exemple précédent, la vue est conçue pour afficher le [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriété.</span><span class="sxs-lookup"><span data-stu-id="d1aff-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="d1aff-129">Pour obtenir un exemple d’un fichier de mise en forme complète qui définit un affichage plus large simple, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="d1aff-130">Fournissant des définitions de votre affichage large</span><span class="sxs-lookup"><span data-stu-id="d1aff-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="d1aff-131">Affichage large peut fournir une ou plusieurs définitions en utilisant les éléments enfants de la [WideControl](./widecontrol-element-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1aff-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="d1aff-132">En règle générale, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="d1aff-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="d1aff-133">Dans l’exemple suivant, la vue fournit une définition unique qui affiche la valeur de la [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriété.</span><span class="sxs-lookup"><span data-stu-id="d1aff-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="d1aff-134">Un affichage plus large peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple).</span><span class="sxs-lookup"><span data-stu-id="d1aff-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="d1aff-135">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour un affichage plus large :</span><span class="sxs-lookup"><span data-stu-id="d1aff-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="d1aff-136">Le [WideControl](./widecontrol-element-format.md) élément et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="d1aff-137">Le [AutoSize](./autosize-element-for-widecontrol-format.md) élément spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="d1aff-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="d1aff-138">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-138">This element is optional.</span></span>

- <span data-ttu-id="d1aff-139">Le [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) élément spécifie le nombre de colonnes affichées dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1aff-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="d1aff-140">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-140">This element is optional.</span></span>

- <span data-ttu-id="d1aff-141">Le [WideEntries](./wideentries-element-for-widecontrol-format.md) élément fournit les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="d1aff-142">Dans la plupart des cas, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="d1aff-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="d1aff-143">Cet élément est requis.</span><span class="sxs-lookup"><span data-stu-id="d1aff-143">This element is required.</span></span>

- <span data-ttu-id="d1aff-144">Le [WideEntry](./wideentry-element-for-widecontrol-format.md) élément fournit une définition de la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="d1aff-145">Au moins un [WideEntry](./wideentry-element-for-widecontrol-format.md) est requis ; Toutefois, il n’existe aucune limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="d1aff-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="d1aff-146">Dans la plupart des cas, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="d1aff-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="d1aff-147">Le [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="d1aff-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="d1aff-148">Cet élément est facultatif et est nécessaire uniquement lorsque vous définissez plusieurs [WideEntry](./wideentry-element-for-widecontrol-format.md) éléments qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="d1aff-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="d1aff-149">Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément spécifie les données qui sont affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="d1aff-150">Contrairement à d’autres types de vues, un contrôle large peut afficher qu’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="d1aff-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="d1aff-151">Le [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) élément spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="d1aff-152">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d1aff-153">Le [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) élément spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d1aff-154">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="d1aff-155">Le [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) élément spécifie un modèle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="d1aff-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="d1aff-156">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-156">This element is optional.</span></span>

<span data-ttu-id="d1aff-157">Pour obtenir un exemple d’un fichier de mise en forme complète qui définit une définition d’affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="d1aff-158">Définition des objets qui utilisent l’affichage plus large</span><span class="sxs-lookup"><span data-stu-id="d1aff-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="d1aff-159">Il existe deux façons de définir les objets .NET utilisent l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1aff-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="d1aff-160">Vous pouvez utiliser la [ViewSelectedBy](./viewselectedby-element-format.md) élément pour définir les objets qui peuvent être affichées par toutes les définitions de la vue, ou vous pouvez utiliser la [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément pour définir quels objets sont affichés par un définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="d1aff-161">Dans la plupart des cas, une vue n'a qu’une seule définition, donc les objets sont généralement définies par le [ViewSelectedBy](./viewselectedby-element-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1aff-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="d1aff-162">L’exemple suivant montre comment définir les objets qui sont affichés par l’affichage plus large à l’aide de la [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="d1aff-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d1aff-163">Il n’existe aucune limite au nombre de [TypeName](./typename-element-for-viewselectedby-format.md) éléments que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="d1aff-164">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par l’affichage plus large :</span><span class="sxs-lookup"><span data-stu-id="d1aff-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="d1aff-165">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1aff-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="d1aff-166">Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="d1aff-167">Le nom de type .NET complet est requis.</span><span class="sxs-lookup"><span data-stu-id="d1aff-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="d1aff-168">Vous devez spécifier au moins un type ou la sélection définie pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d1aff-169">Pour obtenir un exemple d’un fichier de mise en forme complète, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="d1aff-170">L’exemple suivant utilise le [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="d1aff-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d1aff-171">Utiliser des jeux de sélection où vous avez un ensemble d’objets qui sont affichés à l’aide de plusieurs vues, comme lorsque vous définissez un affichage plus large et un affichage de tableau pour les mêmes objets liés.</span><span class="sxs-lookup"><span data-stu-id="d1aff-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="d1aff-172">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définissant des ensembles de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="d1aff-173">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par l’affichage plus large :</span><span class="sxs-lookup"><span data-stu-id="d1aff-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="d1aff-174">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1aff-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="d1aff-175">Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="d1aff-176">Vous devez spécifier au moins un jeu de sélection ou de type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d1aff-177">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de l’affichage plus large en utilisant le [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1aff-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="d1aff-178">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un ensemble de la sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d1aff-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="d1aff-179">Pour plus d’informations sur la façon de créer une sélection des conditions, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="d1aff-180">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de l’affichage plus large :</span><span class="sxs-lookup"><span data-stu-id="d1aff-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="d1aff-181">Le [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="d1aff-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="d1aff-182">Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie .NET qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="d1aff-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="d1aff-183">Lors de l’utilisation de cet élément, le nom de type .NET complet est requis.</span><span class="sxs-lookup"><span data-stu-id="d1aff-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="d1aff-184">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d1aff-185">Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément (non illustré) spécifie un ensemble d’objets qui peuvent être affichées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="d1aff-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="d1aff-186">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d1aff-187">Le [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) élément (non illustré) spécifie une condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d1aff-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d1aff-188">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="d1aff-189">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="d1aff-190">Affichage des groupes d’objets dans un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="d1aff-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="d1aff-191">Vous pouvez séparer les objets qui sont affichés par l’affichage plus large en groupes.</span><span class="sxs-lookup"><span data-stu-id="d1aff-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="d1aff-192">Cela ne signifie pas la que vous définissez un groupe, uniquement que PowerShell Windows démarre un nouveau groupe chaque fois que la valeur d’une propriété spécifique ou un script change.</span><span class="sxs-lookup"><span data-stu-id="d1aff-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d1aff-193">Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) les modifications de propriété.</span><span class="sxs-lookup"><span data-stu-id="d1aff-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="d1aff-194">Les éléments XML suivants sont utilisés pour définir le démarrage d’un groupe :</span><span class="sxs-lookup"><span data-stu-id="d1aff-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="d1aff-195">Le [GroupBy](./groupby-element-for-view-format.md) élément définit la propriété ou un script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.</span><span class="sxs-lookup"><span data-stu-id="d1aff-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="d1aff-196">Le [PropertyName](./propertyname-element-for-groupby-format.md) élément spécifie la propriété qui commence un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="d1aff-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="d1aff-197">Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="d1aff-198">Le [ScriptBlock](./scriptblock-element-for-groupby-format.md) élément spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="d1aff-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="d1aff-199">Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="d1aff-200">Le [étiquette](./label-element-for-groupby-format.md) élément définit une étiquette qui s’affiche au début de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="d1aff-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="d1aff-201">En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="d1aff-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="d1aff-202">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-202">This element is optional.</span></span>

- <span data-ttu-id="d1aff-203">Le [CustomControl](./customcontrol-element-for-groupby-format.md) élément définit un contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="d1aff-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="d1aff-204">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-204">This element is optional.</span></span>

- <span data-ttu-id="d1aff-205">Le [CustomControlName](./customcontrolname-element-for-groupby-format.md) élément spécifie un commun ou d’afficher le contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="d1aff-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="d1aff-206">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1aff-206">This element is optional.</span></span>

<span data-ttu-id="d1aff-207">Pour obtenir un exemple d’un fichier de mise en forme complète qui définit les groupes, consultez [affichage plus large (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="d1aff-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="d1aff-208">À l’aide de chaînes de Format</span><span class="sxs-lookup"><span data-stu-id="d1aff-208">Using Format Strings</span></span>

<span data-ttu-id="d1aff-209">Mise en forme de chaînes peuvent être ajoutés à un affichage plus large d’affiner la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="d1aff-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="d1aff-210">L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="d1aff-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="d1aff-211">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="d1aff-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="d1aff-212">Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément spécifie les données qui sont affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="d1aff-213">Le [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) élément spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="d1aff-214">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d1aff-215">Le [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue</span><span class="sxs-lookup"><span data-stu-id="d1aff-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="d1aff-216">Le [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d1aff-217">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="d1aff-218">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="d1aff-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="d1aff-219">Scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d1aff-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="d1aff-220">Par conséquent, si un objet possède une méthode, tel que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="d1aff-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="d1aff-221">L’élément XML suivant peut être utilisé pour appeler le `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="d1aff-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="d1aff-222">Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément spécifie les données qui sont affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="d1aff-223">Le [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1aff-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d1aff-224">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1aff-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1aff-225">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1aff-225">See Also</span></span>

[<span data-ttu-id="d1aff-226">Affichage plus large (Basic)</span><span class="sxs-lookup"><span data-stu-id="d1aff-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="d1aff-227">Affichage plus large (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="d1aff-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="d1aff-228">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1aff-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
