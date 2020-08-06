---
title: Types d’attributs | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 96fdd38ba10eb748ab0762f0c910463dd472494d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782376"
---
# <a name="attribute-types"></a><span data-ttu-id="31d3c-102">Types d’attributs</span><span class="sxs-lookup"><span data-stu-id="31d3c-102">Attribute Types</span></span>

<span data-ttu-id="31d3c-103">Les attributs d’applet de commande peuvent être regroupés par fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="31d3c-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="31d3c-104">Les sections suivantes décrivent les attributs disponibles et décrivent ce que fait le runtime lorsque l’attribut est appelé.</span><span class="sxs-lookup"><span data-stu-id="31d3c-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="31d3c-105">Attributs des applets de commande</span><span class="sxs-lookup"><span data-stu-id="31d3c-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="31d3c-106">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="31d3c-106">Cmdlet</span></span>

<span data-ttu-id="31d3c-107">Identifie une classe .NET Framework en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="31d3c-108">Il s’agit de l’attribut de base requis.</span><span class="sxs-lookup"><span data-stu-id="31d3c-108">This is the required base attribute.</span></span>
<span data-ttu-id="31d3c-109">Pour plus d’informations, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="31d3c-110">Attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="31d3c-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="31d3c-111">Paramètre</span><span class="sxs-lookup"><span data-stu-id="31d3c-111">Parameter</span></span>

<span data-ttu-id="31d3c-112">Identifie une propriété publique dans la classe d’applet de commande en tant que paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="31d3c-113">Pour plus d’informations, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="31d3c-114">Alias</span><span class="sxs-lookup"><span data-stu-id="31d3c-114">Alias</span></span>

<span data-ttu-id="31d3c-115">Spécifie un ou plusieurs alias pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="31d3c-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="31d3c-116">Pour plus d’informations, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="31d3c-117">Attributs de validation d’argument</span><span class="sxs-lookup"><span data-stu-id="31d3c-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="31d3c-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="31d3c-118">ValidateCount</span></span>

<span data-ttu-id="31d3c-119">Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="31d3c-120">Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="31d3c-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="31d3c-121">ValidateLength</span></span>

<span data-ttu-id="31d3c-122">Spécifie un nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="31d3c-123">Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="31d3c-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="31d3c-124">ValidatePattern</span></span>

<span data-ttu-id="31d3c-125">Spécifie un modèle d’expression régulière auquel l’argument du paramètre de l’applet de commande doit correspondre.</span><span class="sxs-lookup"><span data-stu-id="31d3c-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="31d3c-126">Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="31d3c-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="31d3c-127">ValidateRange</span></span>

<span data-ttu-id="31d3c-128">Spécifie les valeurs minimale et maximale d’un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="31d3c-129">Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="31d3c-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="31d3c-130">ValidateSet</span></span>

<span data-ttu-id="31d3c-131">Spécifie un ensemble de valeurs valides pour l’argument du paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31d3c-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="31d3c-132">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31d3c-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31d3c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d3c-133">See Also</span></span>

[<span data-ttu-id="31d3c-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="31d3c-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
