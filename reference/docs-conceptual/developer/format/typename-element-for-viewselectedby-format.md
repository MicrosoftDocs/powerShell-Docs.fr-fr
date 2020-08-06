---
title: Élément TypeName pour ViewSelectedBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9a391565c3e66041dd9a340455dccfce9ce929b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780030"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="34055-102">TypeName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34055-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="34055-103">Spécifie un objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="34055-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="34055-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément ViewSelectedBy (format) TypeName, élément pour ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="34055-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34055-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34055-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34055-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="34055-106">Attributes and Elements</span></span>

<span data-ttu-id="34055-107">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="34055-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34055-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="34055-108">Attributes</span></span>

<span data-ttu-id="34055-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="34055-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34055-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="34055-110">Child Elements</span></span>

<span data-ttu-id="34055-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="34055-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34055-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="34055-112">Parent Elements</span></span>

|<span data-ttu-id="34055-113">Élément</span><span class="sxs-lookup"><span data-stu-id="34055-113">Element</span></span>|<span data-ttu-id="34055-114">Description</span><span class="sxs-lookup"><span data-stu-id="34055-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34055-115">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="34055-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="34055-116">Définit les objets .NET affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="34055-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34055-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="34055-117">Text Value</span></span>

<span data-ttu-id="34055-118">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="34055-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="34055-119">Notes</span><span class="sxs-lookup"><span data-stu-id="34055-119">Remarks</span></span>

<span data-ttu-id="34055-120">Pour plus d’informations sur l’utilisation de cet élément dans différents affichages, consultez [création d’un affichage de table](./creating-a-table-view.md), [création d’un affichage de liste](./creating-a-list-view.md), [création d’un affichage étendu](./creating-a-wide-view.md)et [composants de vue personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="34055-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="34055-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="34055-121">Example</span></span>

<span data-ttu-id="34055-122">L’exemple suivant montre comment spécifier l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="34055-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="34055-123">Le même schéma est utilisé pour les vues de table, larges et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="34055-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="34055-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34055-124">See Also</span></span>

[<span data-ttu-id="34055-125">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="34055-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="34055-126">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="34055-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="34055-127">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="34055-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="34055-128">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="34055-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="34055-129">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="34055-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="34055-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="34055-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
