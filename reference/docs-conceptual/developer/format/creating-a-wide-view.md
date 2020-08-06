---
title: Création d’un affichage étendu | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0cf6a35201c47e4b12dd160191570eccec3427ef
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786133"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="6aa75-102">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="6aa75-102">Creating a Wide View</span></span>

<span data-ttu-id="6aa75-103">Un affichage étendu affiche une seule valeur pour chaque objet affiché.</span><span class="sxs-lookup"><span data-stu-id="6aa75-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="6aa75-104">La valeur affichée peut être la valeur d’une propriété d’objet .NET ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="6aa75-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="6aa75-105">Par défaut, il n’y a pas d’étiquette ou d’en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="6aa75-106">Affichage étendu</span><span class="sxs-lookup"><span data-stu-id="6aa75-106">A Wide View Display</span></span>

<span data-ttu-id="6aa75-107">L’exemple suivant montre comment Windows PowerShell affiche l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) retourné par l’applet de commande d' [obtention de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) quand sa sortie est dirigée vers l’applet de commande [format-global](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="6aa75-108">(Par défaut, l’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne une vue table.) Dans cet exemple, les deux colonnes sont utilisées pour afficher le nom du processus pour chaque objet retourné.</span><span class="sxs-lookup"><span data-stu-id="6aa75-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="6aa75-109">Le nom de la propriété de l’objet n’est pas affiché, uniquement la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="6aa75-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="6aa75-110">Définition de la vue étendue</span><span class="sxs-lookup"><span data-stu-id="6aa75-110">Defining the Wide View</span></span>

<span data-ttu-id="6aa75-111">Le code XML suivant montre le schéma de vue larges pour l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="6aa75-112">Les éléments XML suivants sont utilisés pour définir une vue étendue :</span><span class="sxs-lookup"><span data-stu-id="6aa75-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="6aa75-113">L’élément [View](./view-element-format.md) est l’élément parent de la vue larges.</span><span class="sxs-lookup"><span data-stu-id="6aa75-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="6aa75-114">(Il s’agit du même élément parent pour les vues de table, de liste et de contrôle personnalisé.)</span><span class="sxs-lookup"><span data-stu-id="6aa75-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="6aa75-115">L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="6aa75-116">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="6aa75-116">This element is required for all views.</span></span>

- <span data-ttu-id="6aa75-117">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="6aa75-118">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6aa75-118">This element is required.</span></span>

- <span data-ttu-id="6aa75-119">L’élément [GroupBy](./groupby-element-for-view-format.md) définit le moment où un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="6aa75-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="6aa75-120">Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="6aa75-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="6aa75-121">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-121">This element is optional.</span></span>

- <span data-ttu-id="6aa75-122">Les éléments de [contrôle](./controls-element-for-view-format.md) définissent les contrôles personnalisés qui sont définis par la vue larges.</span><span class="sxs-lookup"><span data-stu-id="6aa75-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="6aa75-123">Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="6aa75-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="6aa75-124">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-124">This element is optional.</span></span> <span data-ttu-id="6aa75-125">Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="6aa75-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="6aa75-126">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="6aa75-127">L’élément [WideControl](./widecontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="6aa75-128">Dans l’exemple précédent, la vue est conçue pour afficher la propriété [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="6aa75-129">Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage plus simple, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="6aa75-130">Fournir des définitions pour votre vue étendue</span><span class="sxs-lookup"><span data-stu-id="6aa75-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="6aa75-131">Les vues larges peuvent fournir une ou plusieurs définitions à l’aide des éléments enfants de l’élément [WideControl](./widecontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="6aa75-132">En règle générale, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="6aa75-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="6aa75-133">Dans l’exemple suivant, la vue fournit une définition unique qui affiche la valeur de la propriété [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="6aa75-134">Une vue étendue peut afficher la valeur d’une propriété ou la valeur d’un script (non illustrée dans l’exemple).</span><span class="sxs-lookup"><span data-stu-id="6aa75-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="6aa75-135">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une vue étendue :</span><span class="sxs-lookup"><span data-stu-id="6aa75-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="6aa75-136">L’élément [WideControl](./widecontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="6aa75-137">L’élément [AutoSize](./autosize-element-for-widecontrol-format.md) spécifie si la taille de la colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="6aa75-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="6aa75-138">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-138">This element is optional.</span></span>

- <span data-ttu-id="6aa75-139">L’élément [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) spécifie le nombre de colonnes affichées dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="6aa75-140">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-140">This element is optional.</span></span>

- <span data-ttu-id="6aa75-141">L’élément [WideEntries](./wideentries-element-for-widecontrol-format.md) fournit les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="6aa75-142">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="6aa75-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="6aa75-143">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6aa75-143">This element is required.</span></span>

- <span data-ttu-id="6aa75-144">L’élément [WideEntry](./wideentry-element-for-widecontrol-format.md) fournit une définition de la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="6aa75-145">Au moins un [WideEntry](./wideentry-element-for-widecontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="6aa75-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="6aa75-146">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="6aa75-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="6aa75-147">L’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="6aa75-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="6aa75-148">Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [WideEntry](./wideentry-element-for-widecontrol-format.md) qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="6aa75-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="6aa75-149">L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="6aa75-150">Contrairement à d’autres types de vues, un contrôle étendu ne peut afficher qu’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="6aa75-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="6aa75-151">L’élément [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="6aa75-152">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="6aa75-153">L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="6aa75-154">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="6aa75-155">L’élément [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="6aa75-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="6aa75-156">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-156">This element is optional.</span></span>

<span data-ttu-id="6aa75-157">Pour obtenir un exemple de fichier de mise en forme complet qui définit une définition de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="6aa75-158">Définition des objets qui utilisent l’affichage étendu</span><span class="sxs-lookup"><span data-stu-id="6aa75-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="6aa75-159">Il existe deux façons de définir les objets .NET qui utilisent la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="6aa75-160">Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="6aa75-161">Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="6aa75-162">L’exemple suivant montre comment définir les objets affichés par la vue larges à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="6aa75-163">Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="6aa75-164">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage étendu :</span><span class="sxs-lookup"><span data-stu-id="6aa75-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="6aa75-165">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par la vue larges.</span><span class="sxs-lookup"><span data-stu-id="6aa75-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="6aa75-166">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie le .net qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="6aa75-167">Le nom complet du type .NET est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6aa75-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="6aa75-168">Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="6aa75-169">Pour obtenir un exemple de fichier de mise en forme complet, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="6aa75-170">L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="6aa75-171">Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez une vue étendue et une vue de table pour les mêmes objets.</span><span class="sxs-lookup"><span data-stu-id="6aa75-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="6aa75-172">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="6aa75-173">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage étendu :</span><span class="sxs-lookup"><span data-stu-id="6aa75-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="6aa75-174">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par la vue larges.</span><span class="sxs-lookup"><span data-stu-id="6aa75-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="6aa75-175">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="6aa75-176">Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="6aa75-177">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue larges à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6aa75-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="6aa75-178">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6aa75-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="6aa75-179">Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="6aa75-180">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de l’affichage étendu :</span><span class="sxs-lookup"><span data-stu-id="6aa75-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="6aa75-181">L’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="6aa75-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="6aa75-182">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie le .net qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="6aa75-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="6aa75-183">Lors de l’utilisation de cet élément, le nom complet du type .NET est requis.</span><span class="sxs-lookup"><span data-stu-id="6aa75-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="6aa75-184">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="6aa75-185">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="6aa75-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="6aa75-186">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="6aa75-187">L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6aa75-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="6aa75-188">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="6aa75-189">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="6aa75-190">Affichage des groupes d’objets dans un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="6aa75-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="6aa75-191">Vous pouvez séparer les objets affichés par la vue larges en groupes.</span><span class="sxs-lookup"><span data-stu-id="6aa75-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="6aa75-192">Cela ne signifie pas que vous définissez un groupe, mais uniquement que Windows PowerShell démarre un nouveau groupe chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="6aa75-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="6aa75-193">Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) change.</span><span class="sxs-lookup"><span data-stu-id="6aa75-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="6aa75-194">Les éléments XML suivants sont utilisés pour définir le moment où un groupe est démarré :</span><span class="sxs-lookup"><span data-stu-id="6aa75-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="6aa75-195">L’élément [GroupBy](./groupby-element-for-view-format.md) définit la propriété ou le script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.</span><span class="sxs-lookup"><span data-stu-id="6aa75-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="6aa75-196">L’élément [PropertyName](./propertyname-element-for-groupby-format.md) spécifie la propriété qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="6aa75-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="6aa75-197">Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="6aa75-198">L’élément [scriptblock](./scriptblock-element-for-groupby-format.md) spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="6aa75-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="6aa75-199">Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="6aa75-200">L’élément [label](./label-element-for-groupby-format.md) définit une étiquette qui s’affiche au début de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="6aa75-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="6aa75-201">En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="6aa75-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="6aa75-202">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-202">This element is optional.</span></span>

- <span data-ttu-id="6aa75-203">L’élément [CustomControl](./customcontrol-element-for-groupby-format.md) définit un contrôle qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="6aa75-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="6aa75-204">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-204">This element is optional.</span></span>

- <span data-ttu-id="6aa75-205">L’élément [CustomControlName](./customcontrolname-element-for-groupby-format.md) spécifie un contrôle d’affichage ou commun qui est utilisé pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="6aa75-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="6aa75-206">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6aa75-206">This element is optional.</span></span>

<span data-ttu-id="6aa75-207">Pour obtenir un exemple de fichier de mise en forme complet qui définit des groupes, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="6aa75-208">Utilisation de chaînes de format</span><span class="sxs-lookup"><span data-stu-id="6aa75-208">Using Format Strings</span></span>

<span data-ttu-id="6aa75-209">La mise en forme des chaînes peut être ajoutée à une vue étendue pour définir davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="6aa75-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="6aa75-210">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="6aa75-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="6aa75-211">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="6aa75-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="6aa75-212">L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="6aa75-213">L’élément [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="6aa75-214">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="6aa75-215">L’élément [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue</span><span class="sxs-lookup"><span data-stu-id="6aa75-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="6aa75-216">L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="6aa75-217">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="6aa75-218">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="6aa75-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="6aa75-219">Les scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="6aa75-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="6aa75-220">Par conséquent, si un objet a une méthode, telle que `ToString` , qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="6aa75-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="6aa75-221">L’élément XML suivant peut être utilisé pour appeler la `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="6aa75-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="6aa75-222">L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="6aa75-223">L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="6aa75-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="6aa75-224">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6aa75-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6aa75-225">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aa75-225">See Also</span></span>

[<span data-ttu-id="6aa75-226">Vue large (De base)</span><span class="sxs-lookup"><span data-stu-id="6aa75-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="6aa75-227">Vue large (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="6aa75-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="6aa75-228">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6aa75-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
