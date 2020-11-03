---
description: Fournit des informations détaillées sur les sessions PowerShell et le rôle qu’elles jouent dans les commandes distantes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 6f469d0bf2268604e9a1bf09535c53afe89e184e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207010"
---
# <a name="about-pssession-details"></a>À propos des détails de PSSession

## <a name="short-description"></a>Description courte
Fournit des informations détaillées sur les sessions PowerShell et le rôle qu’elles jouent dans les commandes distantes.

## <a name="long-description"></a>Description longue

Une session est un environnement dans lequel PowerShell s’exécute. Une session est créée à chaque fois que vous démarrez PowerShell. Vous pouvez créer des sessions supplémentaires, appelées « sessions PowerShell » ou « sessions PSSession » sur votre ordinateur ou un autre ordinateur.

Contrairement aux sessions que PowerShell crée pour vous, vous pouvez contrôler et gérer les sessions PSSession que vous créez.

Sessions PSSession jouent un rôle important dans l’informatique à distance. Quand vous créez une session PSSession qui est connectée à un ordinateur distant, PowerShell établit une connexion permanente à l’ordinateur distant pour prendre en charge la session PSSession. Vous pouvez utiliser la session PSSession pour exécuter une série de commandes, de fonctions et de scripts qui partagent des données.

Cette rubrique fournit des informations détaillées sur les sessions et les sessions PSSession dans PowerShell. Pour obtenir des informations de base sur les tâches que vous pouvez effectuer avec les sessions, consultez [about_PSSessions](about_PSSessions.md).

## <a name="about-sessions"></a>À propos des sessions

Techniquement, une session est un environnement d’exécution dans lequel PowerShell s’exécute. Chaque session comprend une instance du moteur System. Management. Automation et un programme hôte dans lequel PowerShell s’exécute. L’hôte peut être la console PowerShell familière ou un autre programme qui exécute des commandes, telles que Cmd.exe, ou un programme conçu pour héberger PowerShell, tel que Environnement d’écriture de scripts intégré de Windows PowerShell (ISE). Du point de vue de Windows, une session est un processus Windows sur l’ordinateur cible.

Chaque session est configurée indépendamment. Il comprend ses propres propriétés, sa propre stratégie d’exécution et ses propres profils. L’environnement qui existe lorsque la session est créée persiste pendant sa durée de vie, même si vous modifiez l’environnement sur l’ordinateur. Toutes les sessions sont créées dans une étendue globale, même les sessions que vous créez dans un script.

Vous ne pouvez exécuter qu’une seule commande (ou pipeline de commande) dans une session à la fois. Une deuxième commande exécutée de façon synchrone (une à la fois) attend jusqu’à quatre minutes que la première commande soit terminée. Une deuxième commande exécutée de façon asynchrone (simultanément) échoue.

## <a name="about-pssessions"></a>À propos de sessions PSSession

Une session est créée chaque fois que vous démarrez PowerShell. Et PowerShell crée des sessions temporaires pour exécuter des commandes individuelles.
Toutefois, vous pouvez également créer des sessions (appelées « sessions PowerShell » ou « sessions PSSession ») que vous contrôlez et gérez.

Les sessions PSSession sont essentiels pour les commandes à distance. Si vous utilisez le paramètre **ComputerName** des `Invoke-Command` `Enter-PSSession` applets de commande ou, PowerShell établit une session temporaire pour exécuter la commande, puis ferme la session dès que la commande ou la session interactive est terminée.

Toutefois, si vous utilisez l' `New-PSSession` applet de commande pour créer une session PSSession, PowerShell établit une session persistante sur l’ordinateur distant dans lequel vous pouvez exécuter plusieurs commandes ou sessions interactives. Les sessions PSSession que vous créez restent ouverts et utilisables jusqu’à ce que vous les supprimiez ou que vous fermiez la session dans laquelle ils ont été créés.

Lorsque vous créez une session PSSession sur un ordinateur distant, le système crée un processus PowerShell sur l’ordinateur distant et établit une connexion entre l’ordinateur local et le processus sur l’ordinateur distant. Lorsque vous créez une session PSSession sur l’ordinateur local, le nouveau processus et les connexions sont créés sur l’ordinateur local.

## <a name="when-do-i-need-a-pssession"></a>Quand ai-je besoin d’une session PSSession ?

Les `Invoke-Command` applets de commande et `Enter-PSSession` possèdent des paramètres **ComputerName** et **session** . Vous pouvez utiliser l’une ou l’autre pour exécuter une commande à distance.

Utilisez le paramètre **ComputerName** pour exécuter une seule commande ou une série de commandes non liées sur un ou plusieurs ordinateurs.

Pour exécuter des commandes qui partagent des données, vous devez disposer d’une connexion permanente à l’ordinateur distant. Dans ce cas, créez une session PSSession, puis utilisez le paramètre session pour exécuter des commandes dans la **session** PSSession.

De nombreuses autres applets de commande qui obtiennent des données à partir d’ordinateurs distants, telles que `Get-Process` ,, `Get-Service` `Get-EventLog` et `Get-WmiObject` ont uniquement un paramètre **ComputerName** . Ils utilisent des technologies autres que la communication à distance PowerShell pour collecter des données à distance. Ces applets de commande n’ont pas de paramètre de **session** , mais vous pouvez utiliser l' `Invoke-Command` applet de commande pour exécuter ces commandes dans une session PSSession.

## <a name="how-do-i-create-a-pssession"></a>Comment créer une session PSSession ?

Pour créer une session PSSession, utilisez l’applet de commande `New-PSSession` . Vous pouvez utiliser `New-PSSession` pour créer une session PSSession sur un ordinateur local ou distant.

## <a name="can-i-create-a-pssession-on-any-computer"></a>Puis-je créer une session PSSession sur n’importe quel ordinateur ?

Pour créer une session PSSession qui est connectée à un ordinateur distant, l’ordinateur doit être configuré pour la communication à distance dans PowerShell. L’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur distant, ou l’utilisateur actuel doit être en mesure de fournir les informations d’identification d’un membre du groupe administrateurs. Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).

## <a name="can-i-see-my-pssessions-in-other-sessions"></a>Puis-je voir mes sessions PSSession dans d’autres sessions ?

À compter de Windows PowerShell 3,0, le paramètre **ComputerName** de l' `Get-PSSession` applet de commande obtient les sessions PSSession que vous avez créés sur les ordinateurs distants spécifiés.

Les sessions PSSession actifs sont conservés sur l’ordinateur distant (côté serveur d’une connexion) et vous pouvez les obtenir à partir de n’importe quelle session sur n’importe quel ordinateur.

Par exemple, si vous créez une session PSSession à partir de l’ordinateur SERVEUR01 vers l’ordinateur Server02, puis que vous basculez vers l’ordinateur Server03, vous pouvez utiliser une commande comme celle qui suit pour obtenir la session.

```powershell
Get-PSSession -ComputerName Server02
```

Même si vous vous déconnectez de la session, la session est conservée sur l’ordinateur distant jusqu’à ce que vous le supprimiez ou expirez.

Dans Windows PowerShell 2,0, vous pouvez obtenir uniquement les sessions PSSession que vous avez créés dans la session active. Vous ne pouvez pas accéder aux sessions PSSession que vous avez créés dans d’autres sessions.

Pour plus d’informations, consultez la page [obtenir-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession).

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a>Puis-je voir le sessions PSSession que les autres ont créés sur Poste de travail ?

Vous pouvez obtenir et gérer uniquement les sessions PSSession que d’autres ont créés uniquement si vous pouvez fournir les informations d’identification de l’utilisateur qui a créé la session PSSession ou la configuration de session que la session PSSession utilise, y compris les informations d’identification RunAs. Dans le cas contraire, vous pouvez vous procurer, vous connecter à, utiliser et gérer uniquement les sessions PSSession que vous avez créés.

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a>Puis-je me connecter à une session PSSession à partir d’un autre ordinateur ?

À compter de Windows PowerShell 3,0, les sessions PSSession sont indépendants des sessions dans lesquelles elles ont été créées. Les sessions PSSession actifs sont conservés sur l’ordinateur à distance ou côté serveur d’une connexion.

Vous pouvez utiliser l' `Disconnect-PSSession` applet de commande pour vous déconnecter d’une session PSSession. La session PSSession est déconnectée de la session locale, mais est conservée sur l’ordinateur distant.
Les commandes continuent à s’exécuter dans la session PSSession déconnectée. Vous pouvez fermer PowerShell et arrêter l’ordinateur d’origine sans interrompre la session PSSession.

Ensuite, même quelques heures plus tard, vous pouvez utiliser l' `Get-PSSession` applet de commande pour obtenir la session PSSession et l' `Connect-PSSession` applet de commande pour vous connecter à la session PSSession à partir d’une nouvelle session sur un autre ordinateur.

Pour plus d’informations, consultez [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a>Qu’advient-il de ma session PSSession si Poste de travail s’arrête ?

Les sessions PSSession déconnectées sont indépendantes des sessions dans lesquelles elles ont été créées. Si vous déconnectez une session PSSession, puis fermez l’ordinateur d’origine, la session PSSession est conservée sur l’ordinateur distant.

En outre, PowerShell tente de récupérer les sessions PSSession actifs qui sont déconnectés involontairement, par exemple par un redémarrage de l’ordinateur, une panne d’alimentation temporaire ou une interruption du réseau. PowerShell tente de maintenir ou de récupérer la session PSSession à un état ouvert, si la session d’origine est toujours disponible, ou à un état déconnecté, si ce n’est pas le cas.

Une session PSSession « active » est une session qui exécute des commandes. Si une session PSSession est connectée (non déconnectée) et si les commandes s’exécutent dans la session PSSession lorsque la session connectée se ferme, PowerShell tente de maintenir la session PSSession sur l’ordinateur distant. Toutefois, si aucune commande n’est en cours d’exécution dans la session PSSession, PowerShell ferme la session PSSession lorsque la session connectée se ferme.

Pour plus d’informations, consultez [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md).

## <a name="can-i-run-a-background-job-in-a-pssession"></a>Puis-je exécuter une tâche en arrière-plan dans une session PSSession ?

Oui. Une tâche en arrière-plan est une commande qui s’exécute de façon asynchrone en arrière-plan sans interagir avec la session active. Lorsque vous envoyez une commande pour démarrer un travail, la commande retourne un objet de traitement, mais le travail continue à s’exécuter en arrière-plan jusqu’à ce qu’il soit terminé.

Pour démarrer une tâche en arrière-plan sur un ordinateur local, utilisez la `Start-Job` commande.
Vous pouvez exécuter le travail en arrière-plan dans une connexion temporaire (à l’aide du paramètre **ComputerName** ) ou dans une session PSSession (à l’aide du paramètre **session** ).

Pour démarrer une tâche en arrière-plan sur un ordinateur distant, utilisez l' `Invoke-Command` applet de commande avec son paramètre **AsJob** ou utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande sur un ordinateur distant. Quand vous utilisez le paramètre **AsJob** , vous pouvez utiliser les paramètres **ComputerName** ou **session** .

Lorsque `Invoke-Command` vous utilisez pour exécuter une `Start-Job` commande, vous devez exécuter la commande dans une session PSSession. Si vous utilisez le paramètre **ComputerName** , PowerShell met fin à la connexion quand l’objet de traitement est retourné et la tâche est interrompue.

Pour plus d’informations, consultez [à propos des_tâches](about_Jobs.md).

## <a name="can-i-run-an-interactive-session"></a>Puis-je exécuter une session interactive ?

Oui. Pour démarrer une session interactive avec un ordinateur distant, utilisez l' `Enter-PSSession` applet de commande. Dans une session interactive, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous les tapiiez directement sur l’ordinateur distant.

Vous pouvez exécuter une session interactive dans une session temporaire (à l’aide du paramètre **ComputerName** ) ou dans une session PSSession (à l’aide du paramètre **session** ).
Si vous utilisez une session PSSession, la session PSSession conserve les données des commandes précédentes, et la session PSSession conserve toutes les données générées pendant la session interactive pour une utilisation dans les commandes ultérieures.

Lorsque vous terminez la session interactive, la session PSSession reste ouverte et disponible pour utilisation.

Pour plus d’informations, consultez [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) et [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession).

## <a name="must-i-delete-the-pssessions"></a>Dois-je supprimer le sessions PSSession ?

Oui. Une session PSSession est un processus, qui est un environnement autonome qui utilise de la mémoire et d’autres ressources même lorsque vous ne l’utilisez pas. Une fois que vous avez terminé avec une session PSSession, supprimez-la. Si vous créez plusieurs sessions PSSession, fermez ceux que vous n’utilisez pas et conservez uniquement ceux en cours d’utilisation.

Pour supprimer sessions PSSession, utilisez l' `Remove-PSSession` applet de commande. Elle supprime le sessions PSSession et libère toutes les ressources qu’il utilisait.

Vous pouvez également utiliser le paramètre **IdleTimeout** de `New-PSSessionOption` pour fermer une session PSSession inactive après un intervalle que vous spécifiez. Pour plus d’informations, consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

Si vous enregistrez un objet PSSession dans une variable, puis supprimez la session PSSession ou laissez-le expirer, la variable contient toujours l’objet PSSession, mais la session PSSession n’est pas active et ne peut pas être utilisée ou réparée.

## <a name="are-all-sessions-and-pssessions-alike"></a>Toutes les sessions et sessions PSSession sont-elles identiques ?

Non. Les développeurs peuvent créer des sessions personnalisées qui incluent uniquement des fournisseurs et des applets de commande sélectionnés. Si une commande fonctionne dans une session, mais pas dans une autre, cela peut être dû au fait que la session est restreinte.

## <a name="see-also"></a>Voir aussi

[about_Jobs](about_Jobs.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)
