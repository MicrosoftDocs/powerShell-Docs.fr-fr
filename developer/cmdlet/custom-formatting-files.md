---
title: Fichiers de mise en forme personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068298"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="3052c-102">Fichiers de mise en forme personnalisée</span><span class="sxs-lookup"><span data-stu-id="3052c-102">Custom Formatting Files</span></span>

<span data-ttu-id="3052c-103">Le format d’affichage pour les objets retournés par les applets de commande, les fonctions et les scripts sont définis à l’aide de la mise en forme fichiers (format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="3052c-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="3052c-104">Plusieurs de ces fichiers sont fournis par PowerShell de Windows pour définir le format d’affichage par défaut pour ces objets retournés par les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3052c-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="3052c-105">Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisées pour remplacer les formats d’affichage par défaut ou pour définir l’affichage des objets retournés par vos propres commandes.</span><span class="sxs-lookup"><span data-stu-id="3052c-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="3052c-106">Windows PowerShell utilise les données dans ces fichiers de mise en forme pour déterminer ce qui est affiché et la mise en forme les données.</span><span class="sxs-lookup"><span data-stu-id="3052c-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="3052c-107">Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3052c-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="3052c-108">Blocs de script sont utilisées si vous souhaitez afficher une valeur qui n’est pas disponible directement à partir des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="3052c-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="3052c-109">Par exemple, vous souhaitez ajouter la valeur des deux propriétés d’un objet et afficher la somme en tant qu’une partie des données.</span><span class="sxs-lookup"><span data-stu-id="3052c-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="3052c-110">Lorsque vous écrivez votre propre mise en forme de fichier, vous devez définir *vues* pour les objets que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="3052c-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="3052c-111">Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet.</span><span class="sxs-lookup"><span data-stu-id="3052c-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="3052c-112">Il n’existe aucune limite au nombre de vues que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="3052c-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3052c-113">Fichiers de mise en forme ne déterminent pas les éléments d’un objet qui sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="3052c-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="3052c-114">Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="3052c-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="3052c-115">Vues de format</span><span class="sxs-lookup"><span data-stu-id="3052c-115">Format Views</span></span>

<span data-ttu-id="3052c-116">Vues de mise en forme peuvent afficher des objets dans un format de table, un format de liste, un grand format et un format personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3052c-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="3052c-117">La plupart du temps, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent une vue.</span><span class="sxs-lookup"><span data-stu-id="3052c-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="3052c-118">Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, telles que les informations de ligne et de colonne pour une vue de table.</span><span class="sxs-lookup"><span data-stu-id="3052c-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="3052c-119">Les vues suivantes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="3052c-119">The following views are available.</span></span>

<span data-ttu-id="3052c-120">Affichage de la table répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="3052c-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="3052c-121">Chaque colonne représente une propriété de l’objet ou une valeur de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3052c-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="3052c-122">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet ou une combinaison de propriétés et valeurs de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3052c-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="3052c-123">Chaque ligne de la table représente un objet retourné.</span><span class="sxs-lookup"><span data-stu-id="3052c-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="3052c-124">Pour plus d’informations sur cette vue, consultez [Table vue](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="3052c-125">Affichage de liste répertorie les propriétés d’un objet ou une valeur de bloc de script dans une seule colonne.</span><span class="sxs-lookup"><span data-stu-id="3052c-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="3052c-126">Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété suivie de la valeur du bloc de propriété ou un script.</span><span class="sxs-lookup"><span data-stu-id="3052c-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="3052c-127">Pour plus d’informations sur cette vue, consultez [mode liste](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="3052c-128">Affichage large répertorie une seule propriété d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="3052c-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="3052c-129">Il n’existe aucune étiquette ou un en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="3052c-129">There is no label or header for this view.</span></span> <span data-ttu-id="3052c-130">Pour plus d’informations sur cette vue, consultez [Affichage large](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="3052c-131">Vue personnalisée affiche une vue personnalisable de propriétés de l’objet ou valeurs de bloc de script qui n’est pas conforme à la structure rigide de vues des tables, des affichages de listes ou des vues de larges.</span><span class="sxs-lookup"><span data-stu-id="3052c-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="3052c-132">Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par un autre affichage, comme une liste ou un affichage de la table.</span><span class="sxs-lookup"><span data-stu-id="3052c-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="3052c-133">Pour plus d’informations sur cette vue, consultez [vue personnalisée](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3052c-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="3052c-134">Afficher les éléments XML</span><span class="sxs-lookup"><span data-stu-id="3052c-134">View XML Elements</span></span>

<span data-ttu-id="3052c-135">L’exemple suivant montre les balises XML utilisés pour définir une vue de table qui contient deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="3052c-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="3052c-136">Le [ViewDefinitions](../format/viewdefinitions-element-format.md) élément est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="3052c-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="3052c-137">Le [vue](../format/view-element-format.md) élément définit la table spécifique, la liste, l’affichage large ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3052c-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="3052c-138">Dans chaque vue, le [nom](../format/name-element-for-view-format.md) élément spécifie le nom de la vue, le [ViewSelectedBy](../format/viewselectedby-element-format.md) élément définit les objets qui utilisent la vue et les éléments de contrôle différent (tel que le `TableControl` élément) définissent le format de la vue.</span><span class="sxs-lookup"><span data-stu-id="3052c-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3052c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3052c-139">See Also</span></span>

[<span data-ttu-id="3052c-140">Vue de table</span><span class="sxs-lookup"><span data-stu-id="3052c-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="3052c-141">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="3052c-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="3052c-142">Affichage large</span><span class="sxs-lookup"><span data-stu-id="3052c-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="3052c-143">Vue personnalisée</span><span class="sxs-lookup"><span data-stu-id="3052c-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="3052c-144">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3052c-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
