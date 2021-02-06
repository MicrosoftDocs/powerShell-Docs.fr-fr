---
description: Explique comment utiliser la fonctionnalité exécuter avec PowerShell pour exécuter un script à partir d’un lecteur du système de fichiers.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 7070fa2bc8bb30e83f59e3d1193faa3a8495f109
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596752"
---
# <a name="about-run-with-powershell"></a>À propos de l’exécution avec PowerShell

## <a name="short-description"></a>DESCRIPTION COURTE
Explique comment utiliser la fonctionnalité exécuter avec PowerShell pour exécuter un script à partir d’un lecteur du système de fichiers.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

À compter de Windows PowerShell 3,0, vous pouvez utiliser la fonctionnalité « exécuter avec PowerShell » pour exécuter des scripts à partir de l’Explorateur de fichiers dans Windows 8 et Windows Server 2012 et à partir de l’Explorateur Windows dans les versions antérieures de Windows.

La fonctionnalité « exécuter avec PowerShell » est conçue pour exécuter des scripts qui n’ont pas de paramètres requis et ne renvoient pas de sortie à l’invite de commandes.

Lorsque vous utilisez la fonctionnalité « exécuter avec PowerShell », la fenêtre de console PowerShell s’affiche brièvement, si ce n’est le cas. Vous ne pouvez pas interagir avec lui.

Pour utiliser la fonctionnalité « exécuter avec PowerShell » :

Dans l’Explorateur de fichiers (ou l’Explorateur Windows), cliquez avec le bouton droit sur le nom du fichier de script, puis sélectionnez exécuter avec PowerShell.

La fonctionnalité « exécuter avec PowerShell » démarre une session PowerShell qui a une stratégie d’exécution de contournement, exécute le script et ferme la session.

Il exécute une commande qui a le format suivant :

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

« Exécuter avec PowerShell » définit la stratégie d’exécution de contournement uniquement pour la session (l’instance actuelle du processus PowerShell) dans laquelle le script s’exécute.
Cette fonctionnalité ne modifie pas la stratégie d’exécution de l’ordinateur ou de l’utilisateur.

La fonctionnalité « exécuter avec PowerShell » est uniquement affectée par la stratégie d’exécution AllSigned. Si la stratégie d’exécution AllSigned est effective pour l’ordinateur ou l’utilisateur, « exécuter avec PowerShell » exécute uniquement les scripts signés. « Exécuter avec PowerShell » n’est pas affecté par les autres stratégies d’exécution. Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).

Remarque sur la résolution des problèmes : exécuter avec la commande PowerShell peut vous inviter à confirmer la modification de la stratégie d’exécution.

## <a name="see-also"></a>VOIR AUSSI

[about_Execution_Policies](about_Execution_Policies.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Scripts](about_Scripts.md)

