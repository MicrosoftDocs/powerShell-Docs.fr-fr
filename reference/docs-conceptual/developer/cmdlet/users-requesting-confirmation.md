---
ms.date: 09/13/2016
ms.topic: reference
title: Utilisateurs demandant une confirmation
description: Utilisateurs demandant une confirmation
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646310"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="e1ea0-103">Utilisateurs demandant une confirmation</span><span class="sxs-lookup"><span data-stu-id="e1ea0-103">Users Requesting Confirmation</span></span>

<span data-ttu-id="e1ea0-104">Lorsque vous spécifiez la valeur `true` pour le `SupportsShouldProcess` paramètre de la déclaration d’attribut d’applet de commande, les utilisateurs peuvent spécifier le `Confirm` paramètre à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-104">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="e1ea0-105">Dans l’environnement par défaut, les utilisateurs peuvent spécifier le `Confirm` paramètre ou `"-Confirm:$true` pour que la confirmation soit demandée lors de l’appel de la méthode [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="e1ea0-105">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="e1ea0-106">Cela contourne les demandes de confirmation [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , même pour les opérations à impact élevé.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-106">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="e1ea0-107">Si `Confirm` n’est pas spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation si la `$ConfirmPreference` variable de préférence est supérieure ou égale au `ConfirmImpact` paramètre de l’applet de commande ou du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-107">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="e1ea0-108">La valeur par défaut de `$ConfirmPreference` est haute.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-108">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="e1ea0-109">Par conséquent, dans l’environnement par défaut, seules les applets de commande et les fournisseurs qui spécifient une demande d’action à impact élevé demandent une confirmation.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-109">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="e1ea0-110">Si `Confirm` a la valeur false ou si `"-Confirm:$false` est spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation à l’utilisateur, et la `$ConfirmPreference` variable shell est ignorée.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-110">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1ea0-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e1ea0-111">Remarks</span></span>

- <span data-ttu-id="e1ea0-112">Pour les applets de commande et les fournisseurs qui spécifient `SupportsShouldProcess` , mais pas `ConfirmImpact` , ces actions sont traitées comme des actions à impact moyen, et elles ne sont pas demandées par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-112">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="e1ea0-113">Leur niveau d’impact est inférieur au paramètre par défaut de la `$ConfirmPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-113">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="e1ea0-114">Si l’utilisateur spécifie le `Verbose` paramètre, il est prévenu de l’opération même s’il n’est pas invité à confirmer l’opération.</span><span class="sxs-lookup"><span data-stu-id="e1ea0-114">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1ea0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1ea0-115">See Also</span></span>

[<span data-ttu-id="e1ea0-116">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1ea0-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
