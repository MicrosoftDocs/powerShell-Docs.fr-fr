---
title: Élément DisplayError (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854915"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="c26a8-102">DisplayError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c26a8-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="c26a8-103">Spécifie que la chaîne #ERR est affichée lorsqu’une erreur se produit à afficher un élément de données.</span><span class="sxs-lookup"><span data-stu-id="c26a8-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="c26a8-104">Configuration élément (Format) DefaultSettings (Format) DisplayError élément (Frmat)</span><span class="sxs-lookup"><span data-stu-id="c26a8-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="c26a8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c26a8-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c26a8-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c26a8-106">Attributes and Elements</span></span>

<span data-ttu-id="c26a8-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `DisplayError` élément.</span><span class="sxs-lookup"><span data-stu-id="c26a8-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c26a8-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="c26a8-108">Attributes</span></span>

<span data-ttu-id="c26a8-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c26a8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c26a8-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c26a8-110">Child Elements</span></span>

<span data-ttu-id="c26a8-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c26a8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c26a8-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c26a8-112">Parent Elements</span></span>

|<span data-ttu-id="c26a8-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c26a8-113">Element</span></span>|<span data-ttu-id="c26a8-114">Description</span><span class="sxs-lookup"><span data-stu-id="c26a8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c26a8-115">Élément DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="c26a8-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="c26a8-116">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="c26a8-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c26a8-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="c26a8-117">Remarks</span></span>

<span data-ttu-id="c26a8-118">Par défaut, lorsqu’une erreur se produit en essayant d’afficher un élément de données, l’emplacement des données est vide.</span><span class="sxs-lookup"><span data-stu-id="c26a8-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="c26a8-119">Lorsque cet élément est défini sur true, la chaîne #ERR s’affichera.</span><span class="sxs-lookup"><span data-stu-id="c26a8-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c26a8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c26a8-120">See Also</span></span>

[<span data-ttu-id="c26a8-121">Élément DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="c26a8-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="c26a8-122">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c26a8-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
