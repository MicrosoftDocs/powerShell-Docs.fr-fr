---
title: Informations de référence sur Windows PowerShell-nouveautés
ms.date: 09/13/2016
ms.openlocfilehash: 4e87fce34f74e0fcbfe25939e1555df308a7f7d0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786694"
---
# <a name="whats-new"></a>What's New

Windows PowerShell 2,0 fournit les nouvelles fonctionnalités suivantes à utiliser lors de l’écriture d’applets de commande, de fournisseurs et d’applications hôtes.

## <a name="modules"></a>Modules

Vous pouvez désormais empaqueter et distribuer des solutions Windows PowerShell à l’aide de modules. Les modules vous permettent de partitionner, d’organiser et d’abstraire votre code Windows PowerShell en unités autonomes réutilisables. Pour plus d’informations sur les modules, consultez écriture d’un module Windows PowerShell.

## <a name="the-powershell-class"></a>Classe PowerShell

La classe PowerShell fournit une solution plus simple pour la création d’applications, appelées applications hôtes, qui exécutent des commandes par programmation. Cette classe vous permet de créer un pipeline de commandes, de spécifier l’instance d’exécution utilisée pour exécuter les commandes et de spécifier l’appel des commandes de façon synchrone ou asynchrone.

## <a name="the-runspacepool-class"></a>La classe RunspacePool

Les pools d’instances d’exécution vous permettent de créer plusieurs instances d’exécution à l’aide d’un seul appel. La méthode CreateRunspacePool fournit plusieurs surcharges qui peuvent être utilisées pour créer des instances d’exécution qui ont les mêmes fonctionnalités, telles que le même hôte, l’état de session initial et les informations de connexion.

## <a name="the-initialsessionstate-class"></a>La classe InitialSessionState

La classe InitialSessionState vous permet de créer une configuration d’état de session qui est utilisée lorsqu’une instance d’exécution est ouverte. Vous pouvez créer une configuration personnalisée, une configuration par défaut qui comprend les commandes fournies par mshshort et une configuration dont les commandes sont limitées en fonction des fonctionnalités de la session.

## <a name="remote-runspaces"></a>Instances d’exécution à distance

Vous pouvez maintenant créer des instances d’exécution qui peuvent être ouverts sur des ordinateurs distants, ce qui vous permet d’exécuter des commandes sur l’ordinateur distant et de collecter les résultats localement. Pour créer une instance d’exécution distante, vous devez spécifier des informations sur la connexion distante lors de la création de l’instance d’exécution. Pour obtenir des exemples, consultez les méthodes CreateRunspace et CreateRunspacePool. Les informations de connexion sont définies par la classe RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Éléments d’instance d’exécution privés

Vous pouvez maintenant créer des instances d’exécution dont les éléments sont publics ou privés. Cela vous permet de créer des instances d’exécution dont les éléments sont disponibles pour l’instance d’exécution, mais qui ne sont pas accessibles à l’utilisateur. Consultez la classe ConstrainedSessionStateEntry pour connaître les éléments de l’instance d’exécution qui peuvent être rendus privés.

## <a name="runspace-threading-modes-and-apartment-state"></a>Modes de thread de l’instance d’exécution et état de cloisonnement

Vous pouvez maintenant spécifier la manière dont les threads sont créés et utilisés lors de l’exécution de commandes dans une instance d’exécution. Consultez les propriétés System. Management. Automation. instances d’exécution. Runspace. ThreadOptions et System. Management. Automation. instances d’exécution. RunspacePool. ThreadOptions.

Vous pouvez désormais obtenir l’état de cloisonnement des threads utilisés pour exécuter des commandes dans une instance d’exécution. Consultez les propriétés System. Management. Automation. instances d’exécution. Runspace. ApartmentState et System. Management. Automation. instances d’exécution. RunspacePool. ApartmentState.

## <a name="transaction-cmdlets"></a>Applets de commande de transaction

Vous pouvez maintenant créer des applets de commande qui peuvent être utilisées dans une transaction. Lorsqu’une applet de commande est utilisée dans une transaction, ses actions sont temporaires et peuvent être acceptées ou rejetées par les applets de commande de transaction fournies par Windows PowerShell.

Pour plus d’informations sur les transactions, consultez How to support transactions.

## <a name="transaction-provider"></a>Fournisseur de transactions

Vous pouvez désormais créer des fournisseurs qui peuvent être utilisés dans une transaction. Comme pour les applets de commande, lorsqu’un fournisseur est utilisé dans une transaction, ses actions sont temporaires et peuvent être acceptées ou rejetées par les applets de commande de transaction fournies par Windows PowerShell.

Pour plus d’informations sur la spécification de la prise en charge de transaction dans une classe de fournisseur, consultez la propriété System. Management. Automation. Provider. CmdletProviderAttribute. ProviderCapabilities.

## <a name="job-cmdlets"></a>Applets de commande Job

Vous pouvez maintenant écrire des applets de commande qui peuvent exécuter leur action en tant que tâche. Ces travaux sont exécutés en arrière-plan sans interagir avec la session active. Pour plus d’informations sur la façon dont Windows PowerShell prend en charge les travaux, consultez travaux en arrière-plan.

## <a name="cmdlet-output-types"></a>Types de sortie de l’applet de commande

Vous pouvez maintenant spécifier les types de .NET Framework qui sont retournés par vos applets de commande en déclarant l’attribut OutputType lors de l’écriture de vos applets de commande. Cela permet à d’autres utilisateurs de déterminer le type d’objets qui sont renvoyés par une applet de commande en regardant la propriété OutputType de l’applet de commande.

## <a name="event-support"></a>Prise en charge des événements

Vous pouvez maintenant écrire des applets de commande qui ajoutent et consomment des événements. Consultez la classe PSEvent.

## <a name="proxy-commands"></a>Commandes de proxy

Vous pouvez maintenant écrire des commandes de proxy qui peuvent être utilisées pour exécuter une autre commande. Une commande de proxy vous permet de contrôler la fonctionnalité de l’applet de commande source qui est disponible pour l’utilisateur. Par exemple, vous pouvez créer une commande de proxy qui supprime un paramètre fourni par la commande source. Consultez la classe ProxyCommand.

## <a name="multiple-choice-prompts"></a>Demandes à choix multiples

Vous pouvez maintenant écrire des applications qui peuvent fournir des invites qui permettent à l’utilisateur de sélectionner plusieurs choix. Consultez l’interface IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sessions interactives

Vous pouvez maintenant écrire des applications qui peuvent démarrer et arrêter une session interactive sur un ordinateur distant.
Consultez l’interface IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Aide sur les applets de commande personnalisées pour les fournisseurs

Vous pouvez désormais créer des rubriques d’aide personnalisées pour les applets de commande du fournisseur. Les rubriques d’aide sur les applets de commande personnalisées peuvent expliquer le fonctionnement de l’applet de commande dans le chemin d’accès du fournisseur et documenter des fonctionnalités spéciales, y compris les paramètres dynamiques ajoutés par le fournisseur à l’applet de commande.
