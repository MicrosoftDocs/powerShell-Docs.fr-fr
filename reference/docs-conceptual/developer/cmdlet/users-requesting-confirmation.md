---
title: Utilisateurs demandant confirmation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369248"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="80b24-102">Utilisateurs demandant une confirmation</span><span class="sxs-lookup"><span data-stu-id="80b24-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="80b24-103">Lorsque vous spécifiez la valeur `true` pour le paramètre `SupportsShouldProcess` de la déclaration d’attribut d’applet de commande, les utilisateurs peuvent spécifier le paramètre `Confirm` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="80b24-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="80b24-104">Dans l’environnement par défaut, les utilisateurs peuvent spécifier le paramètre `Confirm` ou `"-Confirm:$true` afin que la confirmation soit demandée lors de l’appel de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="80b24-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="80b24-105">Cela contourne les demandes de confirmation [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , même pour les opérations à impact élevé.</span><span class="sxs-lookup"><span data-stu-id="80b24-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="80b24-106">Si `Confirm` n’est pas spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation si la variable de préférence `$ConfirmPreference` est supérieure ou égale au paramètre `ConfirmImpact` de l’applet de commande ou du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="80b24-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="80b24-107">Le paramètre par défaut de `$ConfirmPreference` est élevé.</span><span class="sxs-lookup"><span data-stu-id="80b24-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="80b24-108">Par conséquent, dans l’environnement par défaut, seules les applets de commande et les fournisseurs qui spécifient une demande d’action à impact élevé demandent une confirmation.</span><span class="sxs-lookup"><span data-stu-id="80b24-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="80b24-109">Si `Confirm` a la valeur false ou si `"-Confirm:$false` est spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation à l’utilisateur et la variable shell `$ConfirmPreference` est ignorée.</span><span class="sxs-lookup"><span data-stu-id="80b24-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="80b24-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="80b24-110">Remarks</span></span>

- <span data-ttu-id="80b24-111">Pour les applets de commande et les fournisseurs qui spécifient `SupportsShouldProcess`, mais qui ne sont pas `ConfirmImpact`, ces actions sont gérées en tant qu’actions « impact moyen », et elles ne sont pas demandées par défaut.</span><span class="sxs-lookup"><span data-stu-id="80b24-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="80b24-112">Leur niveau d’impact est inférieur au paramètre par défaut de la variable de préférence `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="80b24-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="80b24-113">Si l’utilisateur spécifie le paramètre `Verbose`, il est prévenu de l’opération même s’il n’est pas invité à confirmer l’opération.</span><span class="sxs-lookup"><span data-stu-id="80b24-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="80b24-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80b24-114">See Also</span></span>

[<span data-ttu-id="80b24-115">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80b24-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
