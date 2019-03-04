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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858845"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="c01a2-102">Validation des entrées de paramètre</span><span class="sxs-lookup"><span data-stu-id="c01a2-102">Validating Parameter Input</span></span>

<span data-ttu-id="c01a2-103">Windows PowerShell peut valider les arguments passés aux paramètres d’applet de commande de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="c01a2-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="c01a2-104">Windows PowerShell peut valider la longueur, la plage et le modèle des caractères de l’argument.</span><span class="sxs-lookup"><span data-stu-id="c01a2-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="c01a2-105">Il peut valider le nombre d’arguments disponibles (nombre).</span><span class="sxs-lookup"><span data-stu-id="c01a2-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="c01a2-106">Ces règles de validation sont définies par les attributs de validation qui sont déclarées avec l’attribut de paramètre sur les propriétés publiques de la classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c01a2-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="c01a2-107">Pour valider un argument de paramètre, le runtime Windows PowerShell utilise les informations fournies par les attributs de validation pour confirmer la valeur du paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c01a2-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="c01a2-108">Si l’entrée de paramètre n’est pas valide, l’utilisateur reçoit un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c01a2-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="c01a2-109">Chaque paramètre de validation définit une règle de validation est appliquée par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c01a2-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="c01a2-110">Windows PowerShell applique les règles de validation basées sur les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="c01a2-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="c01a2-111">ValidateCount Spécifie le nombre minimal et maximal d’arguments qu’un paramètre peut accepter.</span><span class="sxs-lookup"><span data-stu-id="c01a2-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="c01a2-112">Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c01a2-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="c01a2-113">ValidateLength Spécifie le nombre minimal et maximal de caractères dans l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c01a2-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="c01a2-114">Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c01a2-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="c01a2-115">ValidatePattern spécifie une expression régulière qui valide l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c01a2-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="c01a2-116">Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c01a2-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="c01a2-117">ValidateRange spécifie les valeurs minimales et maximales de l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c01a2-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="c01a2-118">Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c01a2-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="c01a2-119">ValidateSet spécifie les valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c01a2-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="c01a2-120">Pour plus d’informations sur la syntaxe utilisée pour déclarer cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c01a2-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c01a2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c01a2-121">See Also</span></span>

[<span data-ttu-id="c01a2-122">Comment valider l’entrée de paramètre</span><span class="sxs-lookup"><span data-stu-id="c01a2-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="c01a2-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c01a2-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
