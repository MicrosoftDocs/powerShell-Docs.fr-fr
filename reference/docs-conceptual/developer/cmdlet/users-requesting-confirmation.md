---
title: Utilisateurs demandant confirmation | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f0effb35a110f33248a582fab874e3ab95c7df4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786337"
---
# <a name="users-requesting-confirmation"></a>Utilisateurs demandant une confirmation

Lorsque vous spécifiez la valeur `true` pour le `SupportsShouldProcess` paramètre de la déclaration d’attribut d’applet de commande, les utilisateurs peuvent spécifier le `Confirm` paramètre à l’invite de commandes.

Dans l’environnement par défaut, les utilisateurs peuvent spécifier le `Confirm` paramètre ou `"-Confirm:$true` pour que la confirmation soit demandée lors de l’appel de la méthode [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Cela contourne les demandes de confirmation [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , même pour les opérations à impact élevé.

Si `Confirm` n’est pas spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation si la `$ConfirmPreference` variable de préférence est supérieure ou égale au `ConfirmImpact` paramètre de l’applet de commande ou du fournisseur. La valeur par défaut de `$ConfirmPreference` est haute. Par conséquent, dans l’environnement par défaut, seules les applets de commande et les fournisseurs qui spécifient une demande d’action à impact élevé demandent une confirmation.

Si `Confirm` a la valeur false ou si `"-Confirm:$false` est spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation à l’utilisateur, et la `$ConfirmPreference` variable shell est ignorée.

## <a name="remarks"></a>Notes

- Pour les applets de commande et les fournisseurs qui spécifient `SupportsShouldProcess` , mais pas `ConfirmImpact` , ces actions sont traitées comme des actions à impact moyen, et elles ne sont pas demandées par défaut. Leur niveau d’impact est inférieur au paramètre par défaut de la `$ConfirmPreference` variable de préférence.

- Si l’utilisateur spécifie le `Verbose` paramètre, il est prévenu de l’opération même s’il n’est pas invité à confirmer l’opération.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
