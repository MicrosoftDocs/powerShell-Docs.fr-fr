---
ms.date: 09/13/2016
ms.topic: reference
title: Types d’attributs
description: Types d’attributs
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667111"
---
# <a name="attribute-types"></a><span data-ttu-id="7ddf3-103">Types d’attributs</span><span class="sxs-lookup"><span data-stu-id="7ddf3-103">Attribute Types</span></span>

<span data-ttu-id="7ddf3-104">Les attributs d’applet de commande peuvent être regroupés par fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-104">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="7ddf3-105">Les sections suivantes décrivent les attributs disponibles et décrivent ce que fait le runtime lorsque l’attribut est appelé.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-105">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="7ddf3-106">Attributs des applets de commande</span><span class="sxs-lookup"><span data-stu-id="7ddf3-106">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="7ddf3-107">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="7ddf3-107">Cmdlet</span></span>

<span data-ttu-id="7ddf3-108">Identifie une classe .NET Framework en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-108">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="7ddf3-109">Il s’agit de l’attribut de base requis.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-109">This is the required base attribute.</span></span>
<span data-ttu-id="7ddf3-110">Pour plus d’informations, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-110">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="7ddf3-111">Attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="7ddf3-111">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="7ddf3-112">Paramètre</span><span class="sxs-lookup"><span data-stu-id="7ddf3-112">Parameter</span></span>

<span data-ttu-id="7ddf3-113">Identifie une propriété publique dans la classe d’applet de commande en tant que paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-113">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="7ddf3-114">Pour plus d’informations, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-114">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="7ddf3-115">Alias</span><span class="sxs-lookup"><span data-stu-id="7ddf3-115">Alias</span></span>

<span data-ttu-id="7ddf3-116">Spécifie un ou plusieurs alias pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-116">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="7ddf3-117">Pour plus d’informations, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-117">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="7ddf3-118">Attributs de validation d’argument</span><span class="sxs-lookup"><span data-stu-id="7ddf3-118">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="7ddf3-119">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="7ddf3-119">ValidateCount</span></span>

<span data-ttu-id="7ddf3-120">Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-120">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="7ddf3-121">Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-121">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="7ddf3-122">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="7ddf3-122">ValidateLength</span></span>

<span data-ttu-id="7ddf3-123">Spécifie un nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-123">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="7ddf3-124">Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-124">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="7ddf3-125">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="7ddf3-125">ValidatePattern</span></span>

<span data-ttu-id="7ddf3-126">Spécifie un modèle d’expression régulière auquel l’argument du paramètre de l’applet de commande doit correspondre.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-126">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="7ddf3-127">Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-127">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="7ddf3-128">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="7ddf3-128">ValidateRange</span></span>

<span data-ttu-id="7ddf3-129">Spécifie les valeurs minimale et maximale d’un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-129">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="7ddf3-130">Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-130">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="7ddf3-131">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="7ddf3-131">ValidateSet</span></span>

<span data-ttu-id="7ddf3-132">Spécifie un ensemble de valeurs valides pour l’argument du paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ddf3-132">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="7ddf3-133">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf3-133">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ddf3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ddf3-134">See Also</span></span>

[<span data-ttu-id="7ddf3-135">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7ddf3-135">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
