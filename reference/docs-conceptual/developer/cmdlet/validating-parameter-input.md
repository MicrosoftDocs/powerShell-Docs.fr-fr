---
ms.date: 09/13/2016
ms.topic: reference
title: Validation des entrées de paramètre
description: Validation des entrées de paramètre
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660402"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="06a59-103">Validation des entrées de paramètre</span><span class="sxs-lookup"><span data-stu-id="06a59-103">Validating Parameter Input</span></span>

<span data-ttu-id="06a59-104">PowerShell peut valider les arguments passés aux paramètres de l’applet de commande de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="06a59-104">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="06a59-105">PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument.</span><span class="sxs-lookup"><span data-stu-id="06a59-105">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="06a59-106">Il peut valider le nombre d’arguments disponibles (le nombre).</span><span class="sxs-lookup"><span data-stu-id="06a59-106">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="06a59-107">Ces règles de validation sont définies par des attributs de validation qui sont déclarés avec l’attribut de paramètre sur les propriétés publiques de la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06a59-107">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="06a59-108">Pour valider un argument de paramètre, le runtime PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06a59-108">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="06a59-109">Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="06a59-109">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="06a59-110">Chaque paramètre de validation définit une règle de validation appliquée par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06a59-110">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="06a59-111">PowerShell applique les règles de validation en fonction des attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="06a59-111">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="06a59-112">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="06a59-112">ValidateCount</span></span>

<span data-ttu-id="06a59-113">Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter.</span><span class="sxs-lookup"><span data-stu-id="06a59-113">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="06a59-114">Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="06a59-114">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="06a59-115">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="06a59-115">ValidateLength</span></span>

<span data-ttu-id="06a59-116">Spécifie le nombre minimal et maximal de caractères dans l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="06a59-116">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="06a59-117">Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="06a59-117">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="06a59-118">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="06a59-118">ValidatePattern</span></span>

<span data-ttu-id="06a59-119">Spécifie une expression régulière qui valide l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="06a59-119">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="06a59-120">Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="06a59-120">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="06a59-121">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="06a59-121">ValidateRange</span></span>

<span data-ttu-id="06a59-122">Spécifie les valeurs minimale et maximale de l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="06a59-122">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="06a59-123">Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="06a59-123">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="06a59-124">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="06a59-124">ValidateSet</span></span>

<span data-ttu-id="06a59-125">Spécifie les valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="06a59-125">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="06a59-126">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="06a59-126">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06a59-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06a59-127">See Also</span></span>

[<span data-ttu-id="06a59-128">Guide pratique pour valider l’entrée des paramètres</span><span class="sxs-lookup"><span data-stu-id="06a59-128">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="06a59-129">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="06a59-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
