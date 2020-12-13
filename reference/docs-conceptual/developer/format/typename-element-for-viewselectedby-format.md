---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour ViewSelectedBy (Format)
description: TypeName, élément pour ViewSelectedBy (Format)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667723"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="975fb-103">TypeName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="975fb-103">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="975fb-104">Spécifie un objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="975fb-104">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="975fb-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément ViewSelectedBy (format) TypeName, élément pour ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="975fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="975fb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="975fb-106">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="975fb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="975fb-107">Attributes and Elements</span></span>

<span data-ttu-id="975fb-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="975fb-108">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="975fb-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="975fb-109">Attributes</span></span>

<span data-ttu-id="975fb-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="975fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="975fb-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="975fb-111">Child Elements</span></span>

<span data-ttu-id="975fb-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="975fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="975fb-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="975fb-113">Parent Elements</span></span>

|<span data-ttu-id="975fb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="975fb-114">Element</span></span>|<span data-ttu-id="975fb-115">Description</span><span class="sxs-lookup"><span data-stu-id="975fb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="975fb-116">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="975fb-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="975fb-117">Définit les objets .NET affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="975fb-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="975fb-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="975fb-118">Text Value</span></span>

<span data-ttu-id="975fb-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="975fb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="975fb-120">Notes</span><span class="sxs-lookup"><span data-stu-id="975fb-120">Remarks</span></span>

<span data-ttu-id="975fb-121">Pour plus d’informations sur l’utilisation de cet élément dans différents affichages, consultez [création d’un affichage de table](./creating-a-table-view.md), [création d’un affichage de liste](./creating-a-list-view.md), [création d’un affichage étendu](./creating-a-wide-view.md)et [composants de vue personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="975fb-121">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="975fb-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="975fb-122">Example</span></span>

<span data-ttu-id="975fb-123">L’exemple suivant montre comment spécifier l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="975fb-123">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="975fb-124">Le même schéma est utilisé pour les vues de table, larges et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="975fb-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="975fb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="975fb-125">See Also</span></span>

[<span data-ttu-id="975fb-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="975fb-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="975fb-127">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="975fb-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="975fb-128">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="975fb-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="975fb-129">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="975fb-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="975fb-130">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="975fb-130">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="975fb-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="975fb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
