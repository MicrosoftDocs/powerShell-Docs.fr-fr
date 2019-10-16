---
title: Fichiers de mise en forme personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369828"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="95659-102">Fichiers de mise en forme personnalisée</span><span class="sxs-lookup"><span data-stu-id="95659-102">Custom Formatting Files</span></span>

<span data-ttu-id="95659-103">Le format d’affichage des objets retournés par les applets de commande, les fonctions et les scripts est défini à l’aide des fichiers de mise en forme (fichiers format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="95659-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="95659-104">Plusieurs de ces fichiers sont fournis par Windows PowerShell pour définir le format d’affichage par défaut pour les objets retournés par les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95659-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="95659-105">Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisés pour remplacer les formats d’affichage par défaut ou pour définir l’affichage des objets retournés par vos propres commandes.</span><span class="sxs-lookup"><span data-stu-id="95659-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="95659-106">Windows PowerShell utilise les données de ces fichiers de mise en forme pour déterminer ce qui est affiché et la façon dont les données sont mises en forme.</span><span class="sxs-lookup"><span data-stu-id="95659-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="95659-107">Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="95659-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="95659-108">Les blocs de script sont utilisés si vous souhaitez afficher une valeur qui n’est pas directement disponible à partir des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="95659-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="95659-109">Par exemple, vous souhaiterez peut-être ajouter la valeur de deux propriétés d’un objet et afficher la somme sous la forme d’un élément de données distinct.</span><span class="sxs-lookup"><span data-stu-id="95659-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="95659-110">Lorsque vous écrivez votre propre fichier de mise en forme, vous devez définir des *vues* pour les objets que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="95659-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="95659-111">Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet.</span><span class="sxs-lookup"><span data-stu-id="95659-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="95659-112">Il n’existe aucune limite quant au nombre d’affichages que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="95659-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95659-113">La mise en forme des fichiers ne détermine pas les éléments d’un objet qui sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="95659-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="95659-114">Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="95659-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="95659-115">Mettre en forme les vues</span><span class="sxs-lookup"><span data-stu-id="95659-115">Format Views</span></span>

<span data-ttu-id="95659-116">Les vues de mise en forme peuvent afficher des objets dans un format de tableau, un format de liste, un format étendu et un format personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95659-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="95659-117">Pour l’essentiel, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent une vue.</span><span class="sxs-lookup"><span data-stu-id="95659-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="95659-118">Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, tels que les informations de colonne et de ligne pour une vue de table.</span><span class="sxs-lookup"><span data-stu-id="95659-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="95659-119">Les vues suivantes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="95659-119">The following views are available.</span></span>

<span data-ttu-id="95659-120">La vue table répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="95659-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="95659-121">Chaque colonne représente une propriété de l’objet ou une valeur de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="95659-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="95659-122">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet, ou une combinaison de propriétés et de valeurs de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="95659-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="95659-123">Chaque ligne de la table représente un objet retourné.</span><span class="sxs-lookup"><span data-stu-id="95659-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="95659-124">Pour plus d’informations sur cette vue, consultez [vue table](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="95659-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="95659-125">Le mode liste répertorie les propriétés d’un objet ou une valeur de bloc de script dans une seule colonne.</span><span class="sxs-lookup"><span data-stu-id="95659-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="95659-126">Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété, suivi de la valeur de la propriété ou du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="95659-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="95659-127">Pour plus d’informations sur cette vue, consultez [affichage de liste](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="95659-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="95659-128">Vue larges répertorie une seule propriété d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="95659-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="95659-129">Il n’y a pas d’étiquette ou d’en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="95659-129">There is no label or header for this view.</span></span> <span data-ttu-id="95659-130">Pour plus d’informations sur cette vue, consultez [vue étendue](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="95659-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="95659-131">Affichage personnalisé affiche une vue personnalisable des propriétés de l’objet ou des valeurs de bloc de script qui n’adhère pas à la structure rigide des vues de table, des affichages de liste ou des vues larges.</span><span class="sxs-lookup"><span data-stu-id="95659-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="95659-132">Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par une autre vue, telle qu’une vue de table ou une vue de liste.</span><span class="sxs-lookup"><span data-stu-id="95659-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="95659-133">Pour plus d’informations sur cette vue, consultez [vue personnalisée](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="95659-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="95659-134">Afficher les éléments XML</span><span class="sxs-lookup"><span data-stu-id="95659-134">View XML Elements</span></span>

<span data-ttu-id="95659-135">L’exemple suivant montre les balises XML utilisées pour définir une vue de table qui contient deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="95659-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="95659-136">L’élément [ViewDefinitions](../format/viewdefinitions-element-format.md) est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="95659-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="95659-137">L’élément [View](../format/view-element-format.md) définit la table, la liste, la largeur ou la vue personnalisée spécifique.</span><span class="sxs-lookup"><span data-stu-id="95659-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="95659-138">Dans chaque vue, l’élément [Name](../format/name-element-for-view-format.md) spécifie le nom de la vue, l’élément [ViewSelectedBy](../format/viewselectedby-element-format.md) définit les objets qui utilisent la vue, et les différents éléments de contrôle (tels que l’élément `TableControl`) définissent le format de la vue.</span><span class="sxs-lookup"><span data-stu-id="95659-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="95659-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95659-139">See Also</span></span>

[<span data-ttu-id="95659-140">Vue table</span><span class="sxs-lookup"><span data-stu-id="95659-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="95659-141">Mode liste</span><span class="sxs-lookup"><span data-stu-id="95659-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="95659-142">Vue étendue</span><span class="sxs-lookup"><span data-stu-id="95659-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="95659-143">Vue personnalisée</span><span class="sxs-lookup"><span data-stu-id="95659-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="95659-144">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95659-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
