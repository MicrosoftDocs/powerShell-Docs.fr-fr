---
title: Controls, élément de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368998"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="700a5-102">Controls, élément pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="700a5-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="700a5-103">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="700a5-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="700a5-104">Élément de configuration (format) contrôle l’élément de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="700a5-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="700a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="700a5-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="700a5-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="700a5-106">Attributes and Elements</span></span>

<span data-ttu-id="700a5-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Controls`.</span><span class="sxs-lookup"><span data-stu-id="700a5-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="700a5-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="700a5-108">Attributes</span></span>

<span data-ttu-id="700a5-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="700a5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="700a5-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="700a5-110">Child Elements</span></span>

|<span data-ttu-id="700a5-111">Élément</span><span class="sxs-lookup"><span data-stu-id="700a5-111">Element</span></span>|<span data-ttu-id="700a5-112">Description</span><span class="sxs-lookup"><span data-stu-id="700a5-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="700a5-113">Élément Control pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="700a5-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="700a5-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="700a5-114">Required element.</span></span><br /><br /> <span data-ttu-id="700a5-115">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="700a5-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="700a5-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="700a5-116">Parent Elements</span></span>

|<span data-ttu-id="700a5-117">Élément</span><span class="sxs-lookup"><span data-stu-id="700a5-117">Element</span></span>|<span data-ttu-id="700a5-118">Description</span><span class="sxs-lookup"><span data-stu-id="700a5-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="700a5-119">Élément configuration (format)</span><span class="sxs-lookup"><span data-stu-id="700a5-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="700a5-120">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="700a5-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="700a5-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="700a5-121">Remarks</span></span>

<span data-ttu-id="700a5-122">Vous pouvez créer n’importe quel nombre de contrôles communs.</span><span class="sxs-lookup"><span data-stu-id="700a5-122">You can create any number of common controls.</span></span> <span data-ttu-id="700a5-123">Pour chaque contrôle, vous devez spécifier le nom utilisé pour référencer le contrôle et les composants du contrôle.</span><span class="sxs-lookup"><span data-stu-id="700a5-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="700a5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="700a5-124">See Also</span></span>

[<span data-ttu-id="700a5-125">Élément configuration (format)</span><span class="sxs-lookup"><span data-stu-id="700a5-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="700a5-126">Élément Control pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="700a5-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="700a5-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="700a5-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
