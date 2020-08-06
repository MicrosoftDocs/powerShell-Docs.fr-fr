---
title: Élément DisplayError (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774284"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="bbd35-102">DisplayError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd35-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="bbd35-103">Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="bbd35-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="bbd35-104">Élément de configuration (format) DefaultSettings, élément (format) DisplayError, élément (format)</span><span class="sxs-lookup"><span data-stu-id="bbd35-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbd35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbd35-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbd35-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bbd35-106">Attributes and Elements</span></span>

<span data-ttu-id="bbd35-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `DisplayError` élément.</span><span class="sxs-lookup"><span data-stu-id="bbd35-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbd35-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="bbd35-108">Attributes</span></span>

<span data-ttu-id="bbd35-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bbd35-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbd35-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bbd35-110">Child Elements</span></span>

<span data-ttu-id="bbd35-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bbd35-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbd35-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bbd35-112">Parent Elements</span></span>

|<span data-ttu-id="bbd35-113">Élément</span><span class="sxs-lookup"><span data-stu-id="bbd35-113">Element</span></span>|<span data-ttu-id="bbd35-114">Description</span><span class="sxs-lookup"><span data-stu-id="bbd35-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbd35-115">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd35-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="bbd35-116">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bbd35-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bbd35-117">Notes</span><span class="sxs-lookup"><span data-stu-id="bbd35-117">Remarks</span></span>

<span data-ttu-id="bbd35-118">Par défaut, lorsqu’une erreur se produit lors d’une tentative d’affichage d’un élément de données, l’emplacement des données est laissé vide.</span><span class="sxs-lookup"><span data-stu-id="bbd35-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="bbd35-119">Lorsque cet élément est défini sur true, la chaîne de #ERR s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bbd35-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbd35-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbd35-120">See Also</span></span>

[<span data-ttu-id="bbd35-121">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd35-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="bbd35-122">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbd35-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
