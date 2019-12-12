---
title: Élément DisplayError (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363988"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="5d30d-102">DisplayError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="5d30d-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="5d30d-103">Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="5d30d-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="5d30d-104">Élément de configuration (format) DefaultSettings, élément (format) DisplayError, élément (format)</span><span class="sxs-lookup"><span data-stu-id="5d30d-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d30d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d30d-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d30d-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5d30d-106">Attributes and Elements</span></span>

<span data-ttu-id="5d30d-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `DisplayError`.</span><span class="sxs-lookup"><span data-stu-id="5d30d-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d30d-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="5d30d-108">Attributes</span></span>

<span data-ttu-id="5d30d-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5d30d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d30d-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5d30d-110">Child Elements</span></span>

<span data-ttu-id="5d30d-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5d30d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d30d-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5d30d-112">Parent Elements</span></span>

|<span data-ttu-id="5d30d-113">Élément</span><span class="sxs-lookup"><span data-stu-id="5d30d-113">Element</span></span>|<span data-ttu-id="5d30d-114">Description</span><span class="sxs-lookup"><span data-stu-id="5d30d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d30d-115">Élément DefaultSettings (format)</span><span class="sxs-lookup"><span data-stu-id="5d30d-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="5d30d-116">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5d30d-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5d30d-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="5d30d-117">Remarks</span></span>

<span data-ttu-id="5d30d-118">Par défaut, lorsqu’une erreur se produit lors d’une tentative d’affichage d’un élément de données, l’emplacement des données est laissé vide.</span><span class="sxs-lookup"><span data-stu-id="5d30d-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="5d30d-119">Lorsque cet élément est défini sur true, la chaîne de #ERR s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5d30d-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d30d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d30d-120">See Also</span></span>

[<span data-ttu-id="5d30d-121">Élément DefaultSettings (format)</span><span class="sxs-lookup"><span data-stu-id="5d30d-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="5d30d-122">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d30d-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
