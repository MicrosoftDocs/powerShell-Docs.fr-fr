---
title: Validation de l’entrée de paramètre | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783991"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="a3227-102">Validation des entrées de paramètre</span><span class="sxs-lookup"><span data-stu-id="a3227-102">Validating Parameter Input</span></span>

<span data-ttu-id="a3227-103">PowerShell peut valider les arguments passés aux paramètres de l’applet de commande de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="a3227-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="a3227-104">PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument.</span><span class="sxs-lookup"><span data-stu-id="a3227-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="a3227-105">Il peut valider le nombre d’arguments disponibles (le nombre).</span><span class="sxs-lookup"><span data-stu-id="a3227-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="a3227-106">Ces règles de validation sont définies par des attributs de validation qui sont déclarés avec l’attribut de paramètre sur les propriétés publiques de la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3227-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="a3227-107">Pour valider un argument de paramètre, le runtime PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3227-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="a3227-108">Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a3227-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="a3227-109">Chaque paramètre de validation définit une règle de validation appliquée par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3227-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="a3227-110">PowerShell applique les règles de validation en fonction des attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="a3227-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="a3227-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="a3227-111">ValidateCount</span></span>

<span data-ttu-id="a3227-112">Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter.</span><span class="sxs-lookup"><span data-stu-id="a3227-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="a3227-113">Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a3227-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="a3227-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="a3227-114">ValidateLength</span></span>

<span data-ttu-id="a3227-115">Spécifie le nombre minimal et maximal de caractères dans l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3227-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="a3227-116">Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a3227-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="a3227-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="a3227-117">ValidatePattern</span></span>

<span data-ttu-id="a3227-118">Spécifie une expression régulière qui valide l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3227-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="a3227-119">Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a3227-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="a3227-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="a3227-120">ValidateRange</span></span>

<span data-ttu-id="a3227-121">Spécifie les valeurs minimale et maximale de l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3227-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="a3227-122">Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a3227-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="a3227-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="a3227-123">ValidateSet</span></span>

<span data-ttu-id="a3227-124">Spécifie les valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3227-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="a3227-125">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a3227-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3227-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3227-126">See Also</span></span>

[<span data-ttu-id="a3227-127">Guide pratique pour valider l’entrée des paramètres</span><span class="sxs-lookup"><span data-stu-id="a3227-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="a3227-128">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3227-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
