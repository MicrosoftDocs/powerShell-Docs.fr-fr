---
title: Élément TypeName pour ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083754"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="afda4-102">TypeName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="afda4-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="afda4-103">Spécifie un objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="afda4-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="afda4-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément ViewSelectedBy (Format) TypeName élément de configuration pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="afda4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afda4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afda4-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afda4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="afda4-106">Attributes and Elements</span></span>

<span data-ttu-id="afda4-107">Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="afda4-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="afda4-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="afda4-108">Attributes</span></span>

<span data-ttu-id="afda4-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="afda4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afda4-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="afda4-110">Child Elements</span></span>

<span data-ttu-id="afda4-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="afda4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="afda4-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="afda4-112">Parent Elements</span></span>

|<span data-ttu-id="afda4-113">Élément</span><span class="sxs-lookup"><span data-stu-id="afda4-113">Element</span></span>|<span data-ttu-id="afda4-114">Description</span><span class="sxs-lookup"><span data-stu-id="afda4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afda4-115">Élément ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="afda4-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="afda4-116">Définit les objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="afda4-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="afda4-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="afda4-117">Text Value</span></span>

<span data-ttu-id="afda4-118">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="afda4-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="afda4-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="afda4-119">Remarks</span></span>

<span data-ttu-id="afda4-120">Pour plus d’informations sur la façon dont cet élément est utilisé dans les différentes vues, consultez [création d’une vue de Table](./creating-a-table-view.md), [création d’une vue liste](./creating-a-list-view.md), [création d’un affichage plus large](./creating-a-wide-view.md), et [ Composants de la vue personnalisée](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="afda4-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="afda4-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="afda4-121">Example</span></span>

<span data-ttu-id="afda4-122">L’exemple suivant montre comment spécifier le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="afda4-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="afda4-123">Le même schéma est utilisé pour les vues table, large et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="afda4-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="afda4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afda4-124">See Also</span></span>

[<span data-ttu-id="afda4-125">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="afda4-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="afda4-126">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="afda4-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="afda4-127">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="afda4-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="afda4-128">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="afda4-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="afda4-129">Élément ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="afda4-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="afda4-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="afda4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
