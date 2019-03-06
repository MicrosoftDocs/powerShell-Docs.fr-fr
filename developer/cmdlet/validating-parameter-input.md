---
title: Validation des entrées de paramètre | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429837"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="54aaf-102">Validation des entrées de paramètre</span><span class="sxs-lookup"><span data-stu-id="54aaf-102">Validating Parameter Input</span></span>

<span data-ttu-id="54aaf-103">PowerShell peut valider les arguments passés aux paramètres d’applet de commande de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="54aaf-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="54aaf-104">PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument.</span><span class="sxs-lookup"><span data-stu-id="54aaf-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="54aaf-105">Il peut valider le nombre d’arguments disponibles (nombre).</span><span class="sxs-lookup"><span data-stu-id="54aaf-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="54aaf-106">Ces règles de validation sont définies par les attributs de validation qui sont déclarées avec l’attribut de paramètre sur les propriétés publiques de la classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="54aaf-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="54aaf-107">Pour valider un argument de paramètre, le runtime PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="54aaf-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="54aaf-108">Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="54aaf-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="54aaf-109">Chaque paramètre de validation définit une règle de validation est appliquée par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54aaf-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="54aaf-110">PowerShell applique les règles de validation basées sur les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="54aaf-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="54aaf-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="54aaf-111">ValidateCount</span></span>

<span data-ttu-id="54aaf-112">Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter.</span><span class="sxs-lookup"><span data-stu-id="54aaf-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="54aaf-113">Pour plus d’informations, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="54aaf-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="54aaf-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="54aaf-114">ValidateLength</span></span>

<span data-ttu-id="54aaf-115">Spécifie le nombre minimal et maximal de caractères dans l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="54aaf-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="54aaf-116">Pour plus d’informations, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="54aaf-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="54aaf-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="54aaf-117">ValidatePattern</span></span>

<span data-ttu-id="54aaf-118">Spécifie une expression régulière qui valide l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="54aaf-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="54aaf-119">Pour plus d’informations, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="54aaf-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="54aaf-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="54aaf-120">ValidateRange</span></span>

<span data-ttu-id="54aaf-121">Spécifie les valeurs minimales et maximales de l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="54aaf-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="54aaf-122">Pour plus d’informations, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="54aaf-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="54aaf-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="54aaf-123">ValidateSet</span></span>

<span data-ttu-id="54aaf-124">Spécifie les valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="54aaf-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="54aaf-125">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="54aaf-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54aaf-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54aaf-126">See Also</span></span>

[<span data-ttu-id="54aaf-127">Comment valider l’entrée de paramètre</span><span class="sxs-lookup"><span data-stu-id="54aaf-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="54aaf-128">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="54aaf-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
