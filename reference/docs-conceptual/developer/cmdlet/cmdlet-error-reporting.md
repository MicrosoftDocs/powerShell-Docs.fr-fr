---
ms.date: 09/13/2016
ms.topic: reference
title: Rapport d’erreurs des applets de commande
description: Rapport d’erreurs des applets de commande
ms.openlocfilehash: f06cf98183d56249080623895bd1f5a3e070cefd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653407"
---
# <a name="cmdlet-error-reporting"></a>Rapport d’erreurs d’applet de commande

Les applets de commande doivent signaler les erreurs différemment selon que les erreurs se terminent par des erreurs ou qu’elles ne sont pas terminées. Les erreurs de fin sont des erreurs qui provoquent l’arrêt immédiat du pipeline, ou des erreurs qui se produisent lorsqu’il n’y a aucune raison de poursuivre le traitement. Les erreurs sans fin d’opération sont les erreurs qui signalent une condition d’erreur actuelle, mais l’applet de commande peut continuer à traiter les objets d’entrée. Avec les erreurs sans fin d’exécution, l’utilisateur est généralement averti du problème, mais l’applet de commande continue à traiter l’objet d’entrée suivant.

## <a name="terminating-and-nonterminating-errors"></a>Erreurs de fin et de fin

Les instructions suivantes peuvent être utilisées pour déterminer si une condition d’erreur est une erreur de fin ou une erreur sans fin d’achèvement.

- La condition d’erreur empêche-t-elle l’applet de commande de traiter d’autres objets d’entrée ? Dans ce cas, il s’agit d’une erreur de fin.

- La condition d’erreur est-elle liée à un objet d’entrée spécifique ou à un sous-ensemble d’objets d’entrée ? Dans ce cas, il s’agit d’une erreur qui ne se termine pas.

- L’applet de commande accepte-t-elle plusieurs objets d’entrée, de sorte que le traitement peut être effectué sur un autre objet d’entrée ? Dans ce cas, il s’agit d’une erreur qui ne se termine pas.

- Les applets de commande qui peuvent accepter plusieurs objets d’entrée doivent décider des erreurs de fin et de fin, même si une situation particulière ne s’applique qu’à un seul objet d’entrée.

- Les applets de commande peuvent recevoir un nombre quelconque d’objets d’entrée et envoyer un nombre quelconque d’objets de réussite ou d’erreur avant de lever une exception d’arrêt. Il n’existe aucune relation entre le nombre d’objets d’entrée reçus et le nombre d’objets de réussite et d’erreur envoyés.

- Les applets de commande qui peuvent accepter uniquement des objets d’entrée 0-1 et générer uniquement des objets de sortie 0-1 doivent traiter les erreurs comme des erreurs de fin et générer des exceptions de fin.

## <a name="reporting-nonterminating-errors"></a>Signalement d’erreurs qui ne se terminent pas

La création de rapports d’une erreur qui ne se termine pas doit toujours être effectuée au sein de l’implémentation de la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , de la méthode System. [Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ou de la méthode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de l’applet de commande. Ces types d’erreurs sont signalés en appelant la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) qui, à son tour, envoie un enregistrement d’erreur au flux d’erreurs.

## <a name="reporting-terminating-errors"></a>Signalement des erreurs de fin

Les erreurs de fin sont signalées par la levée d’exceptions ou par l’appel de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) de commande. ThrowTerminatingError. Sachez que les applets de commande peuvent également intercepter et lever à nouveau des exceptions telles que **OutOfMemory**. Toutefois, elles ne sont pas requises pour lever à nouveau des exceptions, car le runtime PowerShell les intercepte également.

Vous pouvez également définir vos propres exceptions pour les problèmes spécifiques à votre situation, ou ajouter des informations supplémentaires à une exception existante à l’aide de son enregistrement d’erreur.

## <a name="error-records"></a>Enregistrements d’erreurs

PowerShell décrit une condition d’erreur sans fin d’achèvement avec les objets [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Chaque objet fournit des informations sur la catégorie d’erreur, un objet cible facultatif et des détails sur la condition d’erreur.

### <a name="error-identifiers"></a>Identificateurs d’erreur

L’identificateur d’erreur est une chaîne simple qui identifie la condition d’erreur dans l’applet de commande.
PowerShell associe cet identificateur à un identificateur d’applet de commande pour créer un identificateur d’erreur complet qui peut être utilisé ultérieurement lors du filtrage des flux d’erreurs ou de la journalisation des erreurs, lors de la réponse à des erreurs spécifiques ou avec d’autres activités spécifiques à l’utilisateur.

Les instructions suivantes doivent être suivies lors de la spécification des identificateurs d’erreur :

- Assignez des identificateurs d’erreur différents et très spécifiques aux différents chemins de code. Chaque chemin de code qui appelle [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) doit avoir son propre identificateur d’erreur.

- Les identificateurs d’erreur doivent être uniques aux types d’exceptions CLR (Common Language Runtime) pour les erreurs de fin et sans fin d’exécution.

- Ne modifiez pas la sémantique d’un identificateur d’erreur entre les versions de votre applet de commande ou du fournisseur PowerShell. Une fois la sémantique d’un identificateur d’erreur établie, elle doit rester constante tout au long du cycle de vie de votre applet de commande.

- Pour les erreurs de fin, utilisez un identificateur d’erreur unique pour un type d’exception CLR particulier. Si le type d’exception change, utilisez un nouvel identificateur d’erreur.

- Pour les erreurs qui ne se terminent pas, utilisez un identificateur d’erreur spécifique pour un objet d’entrée spécifique.

- Choisissez du texte pour l’identificateur que tersely correspond à l’erreur signalée. N’utilisez pas d’espace blanc ou de ponctuation.

- Ne générez pas d’identificateurs d’erreur qui ne sont pas reproductibles. Par exemple, ne générez pas d’identificateurs qui incluent un identificateur de processus. Les identificateurs d’erreur sont utiles uniquement lorsqu’ils correspondent à des identificateurs qui sont visibles par d’autres utilisateurs qui rencontrent le même problème.

### <a name="error-categories"></a>Catégories d’erreur

Les catégories d’erreur sont utilisées pour regrouper les erreurs de l’utilisateur. PowerShell définit ces catégories et ces applets de commande, et les fournisseurs PowerShell doivent choisir entre eux lors de la génération de l’enregistrement d’erreur.

Pour obtenir une description des catégories d’erreurs disponibles, consultez l’énumération [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . En général, vous devez éviter d’utiliser **NOERROR**, **UndefinedError** et **erreur générique** dans la mesure du possible.

Les utilisateurs peuvent afficher les erreurs en fonction de la catégorie lorsqu’ils sont définis `$ErrorView` sur **CategoryView**.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des applets de commande](./cmdlet-overview.md)

[Types de sortie des applets de commande](./types-of-cmdlet-output.md)

[Référence Windows PowerShell](../windows-powershell-reference.md)
