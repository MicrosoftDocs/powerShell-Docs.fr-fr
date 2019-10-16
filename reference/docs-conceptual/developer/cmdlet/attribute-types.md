---
title: Types d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364578"
---
# <a name="attribute-types"></a><span data-ttu-id="0923a-102">Types d’attributs</span><span class="sxs-lookup"><span data-stu-id="0923a-102">Attribute Types</span></span>

<span data-ttu-id="0923a-103">Les attributs d’applet de commande peuvent être regroupés par fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0923a-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="0923a-104">Les sections suivantes décrivent les attributs disponibles et décrivent ce que fait le runtime lorsque l’attribut est appelé.</span><span class="sxs-lookup"><span data-stu-id="0923a-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="0923a-105">Attributs des applets de commande</span><span class="sxs-lookup"><span data-stu-id="0923a-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="0923a-106">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="0923a-106">Cmdlet</span></span>

<span data-ttu-id="0923a-107">Identifie une classe .NET Framework en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="0923a-108">Il s’agit de l’attribut de base requis.</span><span class="sxs-lookup"><span data-stu-id="0923a-108">This is the required base attribute.</span></span>
<span data-ttu-id="0923a-109">Pour plus d’informations, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="0923a-110">Attributs de paramètres</span><span class="sxs-lookup"><span data-stu-id="0923a-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="0923a-111">Paramètre</span><span class="sxs-lookup"><span data-stu-id="0923a-111">Parameter</span></span>

<span data-ttu-id="0923a-112">Identifie une propriété publique dans la classe d’applet de commande en tant que paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="0923a-113">Pour plus d’informations, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="0923a-114">Alias</span><span class="sxs-lookup"><span data-stu-id="0923a-114">Alias</span></span>

<span data-ttu-id="0923a-115">Spécifie un ou plusieurs alias pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="0923a-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="0923a-116">Pour plus d’informations, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="0923a-117">Attributs de validation d’argument</span><span class="sxs-lookup"><span data-stu-id="0923a-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="0923a-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="0923a-118">ValidateCount</span></span>

<span data-ttu-id="0923a-119">Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="0923a-120">Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="0923a-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="0923a-121">ValidateLength</span></span>

<span data-ttu-id="0923a-122">Spécifie un nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="0923a-123">Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="0923a-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="0923a-124">ValidatePattern</span></span>

<span data-ttu-id="0923a-125">Spécifie un modèle d’expression régulière auquel l’argument du paramètre de l’applet de commande doit correspondre.</span><span class="sxs-lookup"><span data-stu-id="0923a-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="0923a-126">Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="0923a-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="0923a-127">ValidateRange</span></span>

<span data-ttu-id="0923a-128">Spécifie les valeurs minimale et maximale d’un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="0923a-129">Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="0923a-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="0923a-130">ValidateSet</span></span>

<span data-ttu-id="0923a-131">Spécifie un ensemble de valeurs valides pour l’argument du paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0923a-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="0923a-132">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0923a-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0923a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0923a-133">See Also</span></span>

[<span data-ttu-id="0923a-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0923a-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
