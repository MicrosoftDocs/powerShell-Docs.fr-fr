---
description: Explique la disponibilité et l’objectif des flux de sortie dans PowerShell.
keywords: PowerShell, applet de commande
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 2f63c468f6b0d82559fca354a8ce5c1343eb2084
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208449"
---
# <a name="about-output-streams"></a>À propos des flux de sortie

## <a name="short-description"></a>Description courte
Explique la disponibilité et l’objectif des flux de sortie dans PowerShell.

## <a name="long-description"></a>Description longue

PowerShell fournit plusieurs flux de sortie. Les flux fournissent des canaux pour différents types de messages. Vous pouvez écrire dans ces flux à l’aide de l’applet de commande ou de la redirection associée. Pour plus d’informations, consultez [about_Redirection](about_Redirection.md).

PowerShell prend en charge les flux de sortie suivants.

| Train # |      Description       | Introduite dans  |    Écrire l’applet de commande     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | Flux de **réussite**     | PowerShell 2.0 | `Write-Output`      |
| 2        | Flux d' **Erreurs**       | PowerShell 2.0 | `Write-Error`       |
| 3        | Flux d' **Avertissement**     | PowerShell 3.0 | `Write-Warning`     |
| 4        | Flux **détaillé**     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | Flux de **débogage**       | PowerShell 3.0 | `Write-Debug`       |
| 6        | Flux d' **informations** | PowerShell 5.0 | `Write-Information` |
| n/a      | Flux de **progression**    | PowerShell 3.0 | `Write-Progress`    |

> [!NOTE]
> Le flux de **progression** ne prend pas en charge la redirection.

## <a name="success-stream"></a>Flux de réussite

Le flux de **réussite** est le flux par défaut pour les résultats normaux et réussis.
Utilisez l' `Write-Output` applet de commande pour écrire explicitement des objets dans ce flux. Ce flux est utilisé pour passer des objets via le pipeline PowerShell. Le flux de **réussite** est connecté au flux **stdout** pour les applications natives.

## <a name="error-stream"></a>Flux d’erreurs

Le flux d' **erreur** est le flux par défaut des résultats d’erreur. Utilisez l' `Write-Error` applet de commande pour écrire explicitement dans ce flux. Le flux d' **erreur** est connecté au flux de **stderr** pour les applications natives. Dans la plupart des cas, ces erreurs peuvent mettre fin au pipeline d’exécution. Les erreurs écrites dans ce flux sont également ajoutées à la `$Error` variable automatique. Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

## <a name="warning-stream"></a>Flux d’avertissement

Le flux d' **Avertissement** est destiné à des conditions d’erreur moins graves que les erreurs écrites dans le flux d' **Erreurs** . Dans des conditions normales, ces avertissements ne terminent pas l’exécution. Les avertissements ne sont pas écrits dans la `$Error` variable automatique. Utilisez l' `Write-Warning` applet de commande pour écrire explicitement dans ce flux.

## <a name="verbose-stream"></a>flux des commentaires

Le flux de **Commentaires** est destiné aux messages aidant les utilisateurs à dépanner les commandes lorsqu’ils sont exécutés de manière interactive ou à partir d’un script. Utilisez l' `Write-Verbose` applet de commande pour écrire explicitement des messages dans ce flux. De nombreuses applets de commande fournissent une sortie détaillée qui est utile pour comprendre le fonctionnement interne de l’applet de commande. Les messages détaillés sont générés uniquement lorsque vous utilisez le `-Verbose` paramètre Common. Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).

## <a name="debug-stream"></a>flux de débogage

Le flux de **débogage** est utilisé pour les messages qui aident les scripteurs à comprendre pourquoi leur code échoue. Utilisez l' `Write-Debug` applet de commande pour écrire explicitement dans ce flux. Les messages de débogage sont générés uniquement lorsque vous utilisez le `-Debug` paramètre Common. Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).

Les messages de débogage sont destinés aux développeurs de script et d’applet de commande plus que les utilisateurs finaux. Ces messages de débogage peuvent contenir des détails internes nécessaires pour un dépannage approfondi.

## <a name="information-stream"></a>Flux d’informations

Le flux d' **informations** est destiné à fournir un message qui permet à l’utilisateur de comprendre ce qu’est un script. Elle peut également être utilisée par les développeurs comme un flux supplémentaire utilisé pour passer des informations par le biais de PowerShell. Le développeur peut baliser les données de flux et disposer d’une gestion spécifique pour ce flux. Utilisez l' `Write-Information` applet de commande pour écrire explicitement dans ce flux.

## <a name="progress-stream"></a>Flux de progression

Le flux de **progression** est utilisé pour les messages qui communiquent la progression dans des commandes et des scripts dont l’exécution est longue. Utilisez l' `Write-Progress` applet de commande pour écrire explicitement des messages dans ce flux. Le flux de **progression** ne prend pas en charge la redirection.

## <a name="see-also"></a>Voir aussi

- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Écriture-erreur](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_CommonParameters](about_CommonParameters.md)
- [about_Redirection](about_Redirection.md)
