---
title: Windows PowerShell référence - Nouveautés
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080524"
---
# <a name="whats-new"></a>Nouveautés

Windows PowerShell 2.0 fournit les nouvelles fonctionnalités suivantes à utiliser lors de l’écriture des applets de commande, fournisseurs et héberger des applications.

## <a name="modules"></a>Modules

Vous pouvez empaqueter et distribuer des solutions de Windows PowerShell à l’aide de modules. Modules vous permettent de partition, organiser et d’abstraire votre code Windows PowerShell en unités autonomes réutilisables. Pour plus d’informations sur les modules, consultez écrire un PowerShell Module de Windows.

## <a name="the-powershell-class"></a>La classe de PowerShell

La classe PowerShell fournit une solution plus simple pour créer des applications, appelées à héberger des applications qui exécutent les commandes par programme. Cette classe vous permet de créer un pipeline de commandes, spécifiez l’instance d’exécution qui est utilisé pour exécuter les commandes et indiquez appeler les commandes de manière synchrone ou asynchrone.

## <a name="the-runspacepool-class"></a>La classe RunspacePool

Pools d’instance d’exécution permettent de créer plusieurs instances d’exécution à l’aide d’un seul appel. La méthode CreateRunspacePool fournit plusieurs surcharges qui peuvent être utilisées pour créer des instances d’exécution qui ont les mêmes fonctionnalités, telles que le même hôte, état de session initial et les informations de connexion.

## <a name="the-initialsessionstate-class"></a>La classe InitialSessionState

La classe InitialSessionState vous permet de créer une configuration d’état de session qui est utilisée lorsqu’une instance d’exécution est ouverte. Vous pouvez créer une configuration personnalisée, une configuration par défaut qui inclut les commandes fournies par mshshort et une configuration dont les commandes sont limitées en fonction des capacités de la session.

## <a name="remote-runspaces"></a>Instances d’exécution à distance

Vous pouvez désormais créer des instances d’exécution qui peuvent être ouverts sur des ordinateurs distants, ce qui vous permet d’exécuter des commandes sur l’ordinateur distant et collecter les résultats localement. Pour créer une instance d’exécution à distance, vous devez spécifier des informations sur la connexion à distance lors de la création de l’instance d’exécution. Consultez les méthodes CreateRunspace et CreateRunspacePool pour obtenir des exemples. Les informations de connexion sont définies par la classe RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Éléments de l’instance d’exécution privé

Vous pouvez désormais créer des instances d’exécution dont les éléments sont publics ou privés. Cela vous permet de créer des instances d’exécution dont les éléments sont disponibles pour l’instance d’exécution, mais ne sont pas disponibles à l’utilisateur. Consultez la classe ConstrainedSessionStateEntry pour savoir quels éléments de l’instance d’exécution peuvent être rendues privés.

## <a name="runspace-threading-modes-and-apartment-state"></a>Instance d’exécution modes et état de cloisonnement de thread

Vous pouvez désormais spécifier comment les threads sont créés et utilisés lors de l’exécution des commandes dans une instance d’exécution. Consultez les propriétés System.Management.Automation.Runspaces.Runspace.ThreadOptions et System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Vous pouvez désormais obtenir l’état de cloisonnement des threads qui sont utilisés pour exécuter des commandes dans une instance d’exécution. Consultez les propriétés System.Management.Automation.Runspaces.Runspace.ApartmentState et System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Applets de commande de transaction

Vous pouvez désormais créer des applets de commande qui peut être utilisé dans une transaction. Lorsqu’une applet de commande est utilisée dans une transaction, ses actions sont temporaires et peuvent être acceptées ou rejetées par les applets de commande de transaction fournie par Windows PowerShell.

Pour plus d’informations sur les transactions, consultez Comment la prise en charge des Transactions.

## <a name="transaction-provider"></a>Fournisseur de transaction

Vous pouvez désormais créer des fournisseurs qui peuvent être utilisées dans une transaction. Comme pour les applets de commande, lorsqu’un fournisseur est utilisé dans une transaction, ses actions sont temporaires et peuvent être acceptées ou rejetées par les applets de commande de transaction fournie par Windows PowerShell.

Pour plus d’informations sur la spécification de prise en charge des transactions au sein d’une classe de fournisseur, consultez la propriété System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Applets de commande Job

Vous pouvez maintenant écrire des applets de commande qui peuvent exécuter leur action en tant que tâche. Ces travaux sont exécutés en arrière-plan sans interaction avec la session active. Pour plus d’informations sur la façon dont Windows PowerShell prend en charge les tâches, consultez les tâches en arrière-plan.

## <a name="cmdlet-output-types"></a>Types de sorties d’applet de commande

Vous pouvez désormais spécifier les types .NET Framework qui sont retournés par vos applets de commande en déclarant l’attribut OutputType lors de l’écriture de vos applets de commande. Cela permettra à d’autres personnes déterminer le type d’objets sont retournés par une applet de commande en examinant la propriété OutputType de l’applet de commande.

## <a name="event-support"></a>Prise en charge de l’événement

Vous pouvez maintenant écrire des applets de commande qui ajoutent et consommer des événements. Consultez la classe PSEvent.

## <a name="proxy-commands"></a>Commandes de proxy

Vous pouvez maintenant écrire des commandes de proxy qui peuvent être utilisées pour exécuter une autre commande. Une commande de proxy vous permet de contrôler quelles sont les fonctionnalités de l’applet de commande source sont disponible pour l’utilisateur. Par exemple, vous pouvez créer une commande de proxy qui supprime un paramètre qui est fourni par la commande de la source. Consultez la classe ProxyCommand.

## <a name="multiple-choice-prompts"></a>Plusieurs invites de choix

Vous pouvez maintenant écrire des applications qui peuvent fournir des invites qui permettent à l’utilisateur de sélectionner plusieurs options. Consultez l’interface IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sessions interactives

Vous pouvez maintenant écrire des applications qui peuvent démarrer et arrêter une session interactive sur un ordinateur distant.
Consultez l’interface IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Aide des applets de commande personnalisées pour les fournisseurs

Vous pouvez désormais créer des rubriques d’aide personnalisées pour les applets de commande fournisseur. Rubriques d’aide applet de commande personnalisée peuvent expliquer le fonctionnement de l’applet de commande dans les chemin d’accès et le document spéciales fonctionnalités du fournisseur, y compris les paramètres dynamiques que le fournisseur ajoute à l’applet de commande.
