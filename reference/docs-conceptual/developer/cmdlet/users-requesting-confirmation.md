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
# <a name="users-requesting-confirmation"></a>Utilisateurs demandant une confirmation

Lorsque vous spécifiez la valeur `true` pour le paramètre `SupportsShouldProcess` de la déclaration d’attribut d’applet de commande, les utilisateurs peuvent spécifier le paramètre `Confirm` à l’invite de commandes.

Dans l’environnement par défaut, les utilisateurs peuvent spécifier le paramètre `Confirm` ou `"-Confirm:$true` afin que la confirmation soit demandée lors de l’appel de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess. Cela contourne les demandes de confirmation [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , même pour les opérations à impact élevé.

Si `Confirm` n’est pas spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation si la variable de préférence `$ConfirmPreference` est supérieure ou égale au paramètre `ConfirmImpact` de l’applet de commande ou du fournisseur. Le paramètre par défaut de `$ConfirmPreference` est élevé. Par conséquent, dans l’environnement par défaut, seules les applets de commande et les fournisseurs qui spécifient une demande d’action à impact élevé demandent une confirmation.

Si `Confirm` a la valeur false ou si `"-Confirm:$false` est spécifié, l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) demande une confirmation à l’utilisateur et la variable shell `$ConfirmPreference` est ignorée.

## <a name="remarks"></a>Remarks

- Pour les applets de commande et les fournisseurs qui spécifient `SupportsShouldProcess`, mais qui ne sont pas `ConfirmImpact`, ces actions sont gérées en tant qu’actions « impact moyen », et elles ne sont pas demandées par défaut. Leur niveau d’impact est inférieur au paramètre par défaut de la variable de préférence `$ConfirmPreference`.

- Si l’utilisateur spécifie le paramètre `Verbose`, il est prévenu de l’opération même s’il n’est pas invité à confirmer l’opération.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
