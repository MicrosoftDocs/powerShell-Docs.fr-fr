---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une vue large
description: Création d’une vue large
ms.openlocfilehash: 4230ef91a3612e962b2773b12e8016df6f760eae
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655602"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="ffeca-103">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="ffeca-103">Creating a Wide View</span></span>

<span data-ttu-id="ffeca-104">Un affichage étendu affiche une seule valeur pour chaque objet affiché.</span><span class="sxs-lookup"><span data-stu-id="ffeca-104">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="ffeca-105">La valeur affichée peut être la valeur d’une propriété d’objet .NET ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="ffeca-105">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="ffeca-106">Par défaut, il n’y a pas d’étiquette ou d’en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-106">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="ffeca-107">Affichage étendu</span><span class="sxs-lookup"><span data-stu-id="ffeca-107">A Wide View Display</span></span>

<span data-ttu-id="ffeca-108">L’exemple suivant montre comment Windows PowerShell affiche l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) retourné par l’applet de commande d' [obtention de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) quand sa sortie est dirigée vers l’applet de commande [format-global](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-108">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="ffeca-109">(Par défaut, l’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne une vue table.) Dans cet exemple, les deux colonnes sont utilisées pour afficher le nom du processus pour chaque objet retourné.</span><span class="sxs-lookup"><span data-stu-id="ffeca-109">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="ffeca-110">Le nom de la propriété de l’objet n’est pas affiché, uniquement la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ffeca-110">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="ffeca-111">Définition de la vue étendue</span><span class="sxs-lookup"><span data-stu-id="ffeca-111">Defining the Wide View</span></span>

<span data-ttu-id="ffeca-112">Le code XML suivant montre le schéma de vue larges pour l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-112">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="ffeca-113">Les éléments XML suivants sont utilisés pour définir une vue étendue :</span><span class="sxs-lookup"><span data-stu-id="ffeca-113">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="ffeca-114">L’élément [View](./view-element-format.md) est l’élément parent de la vue larges.</span><span class="sxs-lookup"><span data-stu-id="ffeca-114">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="ffeca-115">(Il s’agit du même élément parent pour les vues de table, de liste et de contrôle personnalisé.)</span><span class="sxs-lookup"><span data-stu-id="ffeca-115">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="ffeca-116">L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="ffeca-117">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="ffeca-117">This element is required for all views.</span></span>

- <span data-ttu-id="ffeca-118">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="ffeca-119">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ffeca-119">This element is required.</span></span>

- <span data-ttu-id="ffeca-120">L’élément [GroupBy](./groupby-element-for-view-format.md) définit le moment où un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="ffeca-120">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="ffeca-121">Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="ffeca-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ffeca-122">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-122">This element is optional.</span></span>

- <span data-ttu-id="ffeca-123">Les éléments de [contrôle](./controls-element-for-view-format.md) définissent les contrôles personnalisés qui sont définis par la vue larges.</span><span class="sxs-lookup"><span data-stu-id="ffeca-123">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="ffeca-124">Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="ffeca-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="ffeca-125">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-125">This element is optional.</span></span> <span data-ttu-id="ffeca-126">Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ffeca-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="ffeca-127">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="ffeca-128">L’élément [WideControl](./widecontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-128">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="ffeca-129">Dans l’exemple précédent, la vue est conçue pour afficher la propriété [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-129">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="ffeca-130">Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage plus simple, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-130">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="ffeca-131">Fournir des définitions pour votre vue étendue</span><span class="sxs-lookup"><span data-stu-id="ffeca-131">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="ffeca-132">Les vues larges peuvent fournir une ou plusieurs définitions à l’aide des éléments enfants de l’élément [WideControl](./widecontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-132">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="ffeca-133">En règle générale, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="ffeca-133">Typically, a view will have only one definition.</span></span> <span data-ttu-id="ffeca-134">Dans l’exemple suivant, la vue fournit une définition unique qui affiche la valeur de la propriété [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-134">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="ffeca-135">Une vue étendue peut afficher la valeur d’une propriété ou la valeur d’un script (non illustrée dans l’exemple).</span><span class="sxs-lookup"><span data-stu-id="ffeca-135">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="ffeca-136">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une vue étendue :</span><span class="sxs-lookup"><span data-stu-id="ffeca-136">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="ffeca-137">L’élément [WideControl](./widecontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-137">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="ffeca-138">L’élément [AutoSize](./autosize-element-for-widecontrol-format.md) spécifie si la taille de la colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="ffeca-138">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="ffeca-139">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-139">This element is optional.</span></span>

- <span data-ttu-id="ffeca-140">L’élément [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) spécifie le nombre de colonnes affichées dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-140">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="ffeca-141">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-141">This element is optional.</span></span>

- <span data-ttu-id="ffeca-142">L’élément [WideEntries](./wideentries-element-for-widecontrol-format.md) fournit les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-142">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="ffeca-143">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="ffeca-143">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="ffeca-144">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ffeca-144">This element is required.</span></span>

- <span data-ttu-id="ffeca-145">L’élément [WideEntry](./wideentry-element-for-widecontrol-format.md) fournit une définition de la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-145">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="ffeca-146">Au moins un [WideEntry](./wideentry-element-for-widecontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="ffeca-146">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="ffeca-147">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="ffeca-147">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="ffeca-148">L’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="ffeca-148">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="ffeca-149">Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [WideEntry](./wideentry-element-for-widecontrol-format.md) qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="ffeca-149">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="ffeca-150">L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-150">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="ffeca-151">Contrairement à d’autres types de vues, un contrôle étendu ne peut afficher qu’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="ffeca-151">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="ffeca-152">L’élément [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-152">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="ffeca-153">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-153">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ffeca-154">L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-154">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ffeca-155">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-155">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="ffeca-156">L’élément [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="ffeca-156">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="ffeca-157">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-157">This element is optional.</span></span>

<span data-ttu-id="ffeca-158">Pour obtenir un exemple de fichier de mise en forme complet qui définit une définition de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-158">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="ffeca-159">Définition des objets qui utilisent l’affichage étendu</span><span class="sxs-lookup"><span data-stu-id="ffeca-159">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="ffeca-160">Il existe deux façons de définir les objets .NET qui utilisent la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-160">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="ffeca-161">Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-161">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="ffeca-162">Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-162">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="ffeca-163">L’exemple suivant montre comment définir les objets affichés par la vue larges à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-163">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ffeca-164">Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-164">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="ffeca-165">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage étendu :</span><span class="sxs-lookup"><span data-stu-id="ffeca-165">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="ffeca-166">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par la vue larges.</span><span class="sxs-lookup"><span data-stu-id="ffeca-166">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="ffeca-167">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie le .net qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-167">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="ffeca-168">Le nom complet du type .NET est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ffeca-168">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="ffeca-169">Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ffeca-169">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ffeca-170">Pour obtenir un exemple de fichier de mise en forme complet, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-170">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="ffeca-171">L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-171">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ffeca-172">Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez une vue étendue et une vue de table pour les mêmes objets.</span><span class="sxs-lookup"><span data-stu-id="ffeca-172">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="ffeca-173">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-173">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="ffeca-174">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage étendu :</span><span class="sxs-lookup"><span data-stu-id="ffeca-174">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="ffeca-175">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par la vue larges.</span><span class="sxs-lookup"><span data-stu-id="ffeca-175">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="ffeca-176">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-176">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="ffeca-177">Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ffeca-177">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ffeca-178">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue larges à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ffeca-178">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="ffeca-179">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ffeca-179">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="ffeca-180">Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-180">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="ffeca-181">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de l’affichage étendu :</span><span class="sxs-lookup"><span data-stu-id="ffeca-181">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="ffeca-182">L’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="ffeca-182">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="ffeca-183">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie le .net qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="ffeca-183">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="ffeca-184">Lors de l’utilisation de cet élément, le nom complet du type .NET est requis.</span><span class="sxs-lookup"><span data-stu-id="ffeca-184">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="ffeca-185">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ffeca-185">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ffeca-186">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="ffeca-186">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="ffeca-187">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ffeca-187">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ffeca-188">L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ffeca-188">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ffeca-189">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ffeca-189">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="ffeca-190">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-190">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="ffeca-191">Affichage des groupes d’objets dans un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="ffeca-191">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="ffeca-192">Vous pouvez séparer les objets affichés par la vue larges en groupes.</span><span class="sxs-lookup"><span data-stu-id="ffeca-192">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="ffeca-193">Cela ne signifie pas que vous définissez un groupe, mais uniquement que Windows PowerShell démarre un nouveau groupe chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="ffeca-193">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ffeca-194">Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) change.</span><span class="sxs-lookup"><span data-stu-id="ffeca-194">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="ffeca-195">Les éléments XML suivants sont utilisés pour définir le moment où un groupe est démarré :</span><span class="sxs-lookup"><span data-stu-id="ffeca-195">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="ffeca-196">L’élément [GroupBy](./groupby-element-for-view-format.md) définit la propriété ou le script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.</span><span class="sxs-lookup"><span data-stu-id="ffeca-196">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="ffeca-197">L’élément [PropertyName](./propertyname-element-for-groupby-format.md) spécifie la propriété qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="ffeca-197">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="ffeca-198">Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-198">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="ffeca-199">L’élément [scriptblock](./scriptblock-element-for-groupby-format.md) spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="ffeca-199">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="ffeca-200">Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-200">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="ffeca-201">L’élément [label](./label-element-for-groupby-format.md) définit une étiquette qui s’affiche au début de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="ffeca-201">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="ffeca-202">En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="ffeca-202">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="ffeca-203">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-203">This element is optional.</span></span>

- <span data-ttu-id="ffeca-204">L’élément [CustomControl](./customcontrol-element-for-groupby-format.md) définit un contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="ffeca-204">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="ffeca-205">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-205">This element is optional.</span></span>

- <span data-ttu-id="ffeca-206">L’élément [CustomControlName](./customcontrolname-element-for-groupby-format.md) spécifie un contrôle d’affichage ou commun qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="ffeca-206">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="ffeca-207">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ffeca-207">This element is optional.</span></span>

<span data-ttu-id="ffeca-208">Pour obtenir un exemple de fichier de mise en forme complet qui définit des groupes, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="ffeca-208">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="ffeca-209">Utilisation de chaînes de format</span><span class="sxs-lookup"><span data-stu-id="ffeca-209">Using Format Strings</span></span>

<span data-ttu-id="ffeca-210">La mise en forme des chaînes peut être ajoutée à une vue étendue pour définir davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="ffeca-210">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="ffeca-211">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="ffeca-211">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="ffeca-212">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="ffeca-212">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="ffeca-213">L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-213">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="ffeca-214">L’élément [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-214">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="ffeca-215">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-215">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ffeca-216">L’élément [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue</span><span class="sxs-lookup"><span data-stu-id="ffeca-216">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="ffeca-217">L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-217">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ffeca-218">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-218">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="ffeca-219">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="ffeca-219">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="ffeca-220">Les scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="ffeca-220">Scripts can call any method of an object.</span></span> <span data-ttu-id="ffeca-221">Par conséquent, si un objet a une méthode, telle que `ToString` , qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="ffeca-221">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="ffeca-222">L’élément XML suivant peut être utilisé pour appeler la `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="ffeca-222">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="ffeca-223">L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-223">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="ffeca-224">L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="ffeca-224">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ffeca-225">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ffeca-225">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffeca-226">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffeca-226">See Also</span></span>

[<span data-ttu-id="ffeca-227">Vue large (De base)</span><span class="sxs-lookup"><span data-stu-id="ffeca-227">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="ffeca-228">Vue large (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="ffeca-228">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="ffeca-229">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffeca-229">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
