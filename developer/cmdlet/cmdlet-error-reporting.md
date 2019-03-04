---
title: Rapport d’erreurs applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 7b54fc220a66a47c25b3e8cba644882d31713cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857685"
---
# <a name="cmdlet-error-reporting"></a>Rapport d’erreurs des applets de commande

Applets de commande doit signaler les erreurs différemment selon si les erreurs sont fin des erreurs ou des erreurs sans fin d’exécution. Erreurs avec fin d’exécution sont des erreurs qui provoquent le pipeline pour être immédiatement arrêtées ou les erreurs qui se produisent lorsqu’il n’existe aucune raison de continuer le traitement. Erreurs sans fin d’exécution sont les erreurs qui signalent une condition d’erreur actuel, mais l’applet de commande peut continuer à traiter les objets d’entrée. Avec des erreurs sans fin d’exécution, l’utilisateur est généralement informé du problème, mais l’applet de commande continue de traiter l’objet d’entrée suivant.

## <a name="terminating-and-nonterminating-errors"></a>Erreurs avec et sans fin d’exécution

Les instructions suivantes peuvent être utilisées pour déterminer si une condition d’erreur est une erreur avec fin ou une erreur sans fin d’exécution.

- Ne la condition d’erreur empêche votre applet de commande pour traiter correctement les objets davantage d’entrée ? Dans ce cas, il s’agit d’une erreur avec fin d’exécution.

- La condition d’erreur est liée à un objet d’entrée spécifique ou un sous-ensemble des objets d’entrée ? Dans ce cas, il s’agit d’une erreur sans fin d’exécution.

- L’applet de commande accepte des plusieurs objets d’entrée, tels que le traitement peut réussir sur un autre objet d’entrée ? Dans ce cas, il s’agit d’une erreur sans fin d’exécution.

- Applets de commande qui peut accepter plusieurs objets d’entrée doit décider entre ce qui sont en fin d’exécution et les erreurs sans fin d’exécution, même lorsqu’une situation particulière s’applique à un seul objet d’entrée.

- Applets de commande peut recevoir n’importe quel nombre d’objets d’entrée et envoyer n’importe quel nombre d’objets de réussite ou d’erreur avant de lever une exception de fin. Il n’existe aucune relation entre le nombre d’objets d’entrée reçus et le nombre d’objets de réussite et d’erreur envoyés.

- Applets de commande qui peut accepter uniquement 0-1 d’entrée d’objets et générer uniquement 0-1 de sortie objets doivent traiter les erreurs comme des erreurs avec fin d’exécution et génèrent des exceptions avec fin d’exécution.

## <a name="reporting-nonterminating-errors"></a>Rapports d’erreurs sans fin d’exécution

La création de rapports d’une erreur sans fin d’exécution doit toujours être effectuée au sein de l’implémentation de l’applet de commande de la [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode), le [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode), ou le [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode). Ces types d’erreurs sont signalées en appelant le [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode qui à son tour envoie un enregistrement d’erreur dans le flux d’erreurs.

## <a name="reporting-terminating-errors"></a>Signalement des erreurs avec fin d’exécution

Erreurs avec fin d’exécution sont signalées en levant des exceptions ou en appelant le [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (méthode). N’oubliez pas qu’applets de commande peut également intercepter et lever à nouveau les exceptions telles que OutOfMemory, toutefois, ils ne sont pas nécessaires pour relancer des exceptions comme le runtime Windows PowerShell les interceptera également.

Vous pouvez également définir vos propres exceptions pour résoudre les problèmes spécifiques à votre situation, ou ajouter des informations supplémentaires à une exception existante à l’aide de son enregistrement d’erreur.

## <a name="error-records"></a>Enregistrements d’erreur

Windows PowerShell décrit une condition d’erreur sans fin d’exécution à l’aide de [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objets. Chaque [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet fournit des informations de catégorie d’erreur, un objet cible facultatif et plus d’informations sur la condition d’erreur.

### <a name="error-identifiers"></a>Identificateurs d’erreur

Identificateur de l’erreur est une chaîne simple qui identifie la condition d’erreur au sein de l’applet de commande. Windows PowerShell associe cet identificateur avec un identificateur de l’applet de commande pour créer un identificateur d’erreur complet qui peut être utilisé ultérieurement lors du filtrage des flux d’erreur ou la journalisation des erreurs lors de la réponse à des erreurs spécifiques, ou avec d’autres activités spécifiques à l’utilisateur.

Lorsque vous spécifiez des identificateurs d’erreur, vous devraient suivre les instructions suivantes.

- Affecter des identificateurs d’erreur différents, très spécifiques, à différents chemins de code. Chaque chemin d’accès du code qui appelle [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) doit avoir son propre identificateur de l’erreur.

- Identificateurs d’erreur doivent être uniques pour les types d’exceptions CLR pour les erreurs avec et sans fin d’exécution.

- Ne modifiez pas la sémantique d’un identificateur de l’erreur entre les versions de votre applet de commande ou d’un fournisseur Windows PowerShell. Une fois établie la sémantique d’un identificateur de l’erreur, il doit rester constante tout au long du cycle de vie de votre applet de commande.

- Pour les erreurs avec fin d’exécution, utilisez un identificateur unique d’erreur pour un type particulier d’exception CLR. Si le type d’exception change, utilisez un nouvel identificateur de l’erreur.

- Pour les erreurs sans fin d’exécution, utilisez un identificateur de l’erreur spécifique pour un objet d’entrée spécifique.

- Choisissez le texte pour l’identificateur tersely correspond à l’erreur signalée. N’utilisez pas les espaces blancs ou des signes de ponctuation.

- Ne génèrent pas d’identificateurs d’erreur qui ne sont pas reproductibles. Par exemple, ne génèrent pas les identificateurs qui incluent un identificateur de processus. Identificateurs d’erreur sont utiles uniquement lorsqu’ils correspondent aux identificateurs sont visibles par d’autres utilisateurs qui rencontrent le même problème.

### <a name="error-categories"></a>Catégories d’erreur

Catégories d’erreur permettent de regrouper des erreurs pour l’utilisateur final. Windows PowerShell définit ces catégories et les applets de commande et les fournisseurs Windows PowerShell doivent choisir entre eux lors de la génération de l’enregistrement d’erreur.

Pour obtenir une description des catégories d’erreur qui sont disponibles, consultez le [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) énumération. En règle générale, évitez d’utiliser NoError UndefinedError et erreur générique chaque fois que possible.

Les utilisateurs peuvent afficher des erreurs lorsqu’ils définis selon la catégorie «`$ErrorView`» à « CategoryView ».

## <a name="see-also"></a>Voir aussi

[Applets de commande Windows PowerShell](./cmdlet-overview.md)

[Sortie de l’applet de commande](./types-of-cmdlet-output.md)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
