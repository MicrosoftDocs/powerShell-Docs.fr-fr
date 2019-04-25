---
title: Les utilisateurs de demander Confirmation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067213"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="6a794-102">Utilisateurs demandant une confirmation</span><span class="sxs-lookup"><span data-stu-id="6a794-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="6a794-103">Lorsque vous spécifiez une valeur de `true` pour le `SupportsShouldProcess` paramètre de la déclaration d’attribut applet de commande, les utilisateurs peuvent spécifier le `Confirm` paramètre à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6a794-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="6a794-104">Dans l’environnement par défaut, les utilisateurs peuvent spécifier le `Confirm` paramètre ou `"-Confirm:$true` afin que la confirmation est demandée lors de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="6a794-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="6a794-105">Cela contourne [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) des demandes de confirmation, même pour les opérations à fort impact.</span><span class="sxs-lookup"><span data-stu-id="6a794-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="6a794-106">Si `Confirm` n’est pas spécifié, le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appel demande confirmation si la `$ConfirmPreference` variable de préférence est supérieure ou égale à la `ConfirmImpact` définition de la applet de commande ou le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6a794-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="6a794-107">Le paramètre par défaut de `$ConfirmPreference` est élevé.</span><span class="sxs-lookup"><span data-stu-id="6a794-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="6a794-108">Par conséquent, dans l’environnement par défaut, seuls les applets de commande et les fournisseurs qui spécifient une action à fort impact demandent confirmation.</span><span class="sxs-lookup"><span data-stu-id="6a794-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="6a794-109">Si `Confirm` a la valeur false ou si `"-Confirm:$false` est spécifié, le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appel demande confirmation à l’utilisateur et le `$ConfirmPreference` variable d’environnement est ignoré.</span><span class="sxs-lookup"><span data-stu-id="6a794-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a794-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6a794-110">Remarks</span></span>

- <span data-ttu-id="6a794-111">Pour les applets de commande et les fournisseurs qui spécifient `SupportsShouldProcess`, mais pas `ConfirmImpact`, ces actions sont traitées comme des actions de « impact moyen », et ils n’invitera pas par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a794-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="6a794-112">Leur niveau d’impact est inférieure à celle du paramètre par défaut de la `$ConfirmPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="6a794-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="6a794-113">Si l’utilisateur spécifie le `Verbose` paramètre, et être informé de l’opération même s’il n’est pas invité à confirmer l’opération.</span><span class="sxs-lookup"><span data-stu-id="6a794-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a794-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a794-114">See Also</span></span>

[<span data-ttu-id="6a794-115">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a794-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
