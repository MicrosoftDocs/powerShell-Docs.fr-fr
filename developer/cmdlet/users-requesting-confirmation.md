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
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856235"
---
# <a name="users-requesting-confirmation"></a>Utilisateurs demandant une confirmation

Lorsque vous spécifiez une valeur de `true` pour le `SupportsShouldProcess` paramètre de la déclaration d’attribut applet de commande, les utilisateurs peuvent spécifier le `Confirm` paramètre à l’invite de commandes.

Dans l’environnement par défaut, les utilisateurs peuvent spécifier le `Confirm` paramètre ou `"-Confirm:$true` afin que la confirmation est demandée lors de la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode est appelée. Cela contourne [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) des demandes de confirmation, même pour les opérations à fort impact.

Si `Confirm` n’est pas spécifié, le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appel demande confirmation si la `$ConfirmPreference` variable de préférence est supérieure ou égale à la `ConfirmImpact` définition de la applet de commande ou le fournisseur. Le paramètre par défaut de `$ConfirmPreference` est élevé. Par conséquent, dans l’environnement par défaut, seuls les applets de commande et les fournisseurs qui spécifient une action à fort impact demandent confirmation.

Si `Confirm` a la valeur false ou si `"-Confirm:$false` est spécifié, le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appel demande confirmation à l’utilisateur et le `$ConfirmPreference` variable d’environnement est ignoré.

## <a name="remarks"></a>Remarques

- Pour les applets de commande et les fournisseurs qui spécifient `SupportsShouldProcess`, mais pas `ConfirmImpact`, ces actions sont traitées comme des actions de « impact moyen », et ils n’invitera pas par défaut. Leur niveau d’impact est inférieure à celle du paramètre par défaut de la `$ConfirmPreference` variable de préférence.

- Si l’utilisateur spécifie le `Verbose` paramètre, et être informé de l’opération même s’il n’est pas invité à confirmer l’opération.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
