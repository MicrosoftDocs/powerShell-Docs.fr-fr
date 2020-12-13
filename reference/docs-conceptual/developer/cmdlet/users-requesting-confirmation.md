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
