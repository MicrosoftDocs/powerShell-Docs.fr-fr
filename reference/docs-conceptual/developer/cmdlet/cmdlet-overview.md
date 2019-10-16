---
title: Vue d’ensemble de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365888"
---
# <a name="cmdlet-overview"></a>Vue d’ensemble des applets de commande

Une applet de commande est une commande légère qui est utilisée dans l’environnement Windows PowerShell. Le runtime Windows PowerShell appelle ces applets de commande dans le contexte des scripts d’automatisation fournis sur la ligne de commande. Le runtime Windows PowerShell les appelle également par programme par le biais des API Windows PowerShell.

## <a name="cmdlets"></a>applets de commande

Les applets de commande effectuent une action et retournent généralement un objet Microsoft .NET Framework à la commande suivante dans le pipeline. Pour écrire une applet de commande, vous devez implémenter une classe d’applet de commande qui dérive de l’une des deux classes de base d’applets de commande spécialisées. La classe dérivée doit :

- Déclarez un attribut qui identifie la classe dérivée en tant qu’applet de commande.

- Définissez les propriétés publiques qui sont décorées avec des attributs qui identifient les propriétés publiques comme paramètres d’applet de commande.

- Remplacez une ou plusieurs méthodes de traitement d’entrée pour traiter les enregistrements.

Vous pouvez charger l’assembly qui contient la classe directement à l’aide de l’applet de commande [import-module](/powershell/module/microsoft.powershell.core/import-module) , ou vous pouvez créer une application hôte qui charge l’assembly à l’aide de l’API [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) . Les deux méthodes fournissent un accès par programmation et en ligne de commande à la fonctionnalité de l’applet de commande.

## <a name="cmdlet-terms"></a>Termes de l’applet de commande

Les termes suivants sont fréquemment utilisés dans la documentation de l’applet de commande Windows PowerShell :

### <a name="cmdlet-attribute"></a>Attribut d’applet de commande

Attribut .NET Framework utilisé pour déclarer une classe d’applet de commande en tant qu’applet de commande.
Bien que PowerShell utilise plusieurs autres attributs facultatifs, l’attribut d’applet de commande est requis.
Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut d’applet](cmdlet-attribute-declaration.md)de commande.

### <a name="cmdlet-parameter"></a>Paramètre d'applet de commande

Les propriétés publiques qui définissent les paramètres disponibles pour l’utilisateur ou pour l’application qui exécute l’applet de commande.
Les applets de commande peuvent avoir des paramètres requis, nommés, positionnels et de *commutateur* .
Les paramètres de commutateur vous permettent de définir des paramètres qui sont évalués uniquement si les paramètres sont spécifiés dans l’appel.
Pour plus d’informations sur les différents types de paramètres, consultez [paramètres d’applet](cmdlet-parameters.md)de commande.

### <a name="parameter-set"></a>Jeu de paramètres

Groupe de paramètres qui peut être utilisé dans la même commande pour effectuer une action spécifique.
Une applet de commande peut avoir plusieurs jeux de paramètres, mais chaque jeu de paramètres doit avoir au moins un paramètre unique.
Une bonne conception d’applet de commande suggère fortement que le paramètre unique est également un paramètre obligatoire.
Pour plus d’informations sur les jeux de paramètres, consultez [jeux de paramètres d’applet](cmdlet-parameter-sets.md)de commande.

### <a name="dynamic-parameter"></a>Paramètre dynamique

Paramètre qui est ajouté à l’applet de commande au moment de l’exécution.
En règle générale, les paramètres dynamiques sont ajoutés à l’applet de commande lorsqu’un autre paramètre est défini sur une valeur spécifique.
Pour plus d’informations sur les paramètres dynamiques, consultez [paramètres dynamiques des applets](cmdlet-dynamic-parameters.md)de commande.

### <a name="input-processing-method"></a>Méthode de traitement d’entrée

Méthode qu’une applet de commande peut utiliser pour traiter les enregistrements qu’elle reçoit en entrée.
Les méthodes de traitement d’entrée incluent la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , l’applet de [commande System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) et la méthode [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) . Lorsque vous implémentez une applet de commande, vous devez substituer au moins l’une des [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)et [ Méthodes System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing.
En règle générale, la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est la méthode que vous substituez, car elle est appelée pour chaque enregistrement traité par l’applet de commande.
En revanche, la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et la méthode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) sont appelées une fois pour effectuer le prétraitement ou le traitement des enregistrements.
Pour plus d’informations sur ces méthodes, consultez [méthodes de traitement d’entrée](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>Fonction ShouldProcess

PowerShell vous permet de créer des applets de commande qui invitent l’utilisateur à entrer des commentaires avant que l’applet de commande n’apporte une modification au système.
Pour utiliser cette fonctionnalité, l’applet de commande doit déclarer qu’elle prend en charge la fonctionnalité ShouldProcess lorsque vous déclarez l’attribut d’applet de commande, et l’applet de commande doit appeler [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [ Méthodes System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) à partir d’une méthode de traitement d’entrée.
Pour plus d’informations sur la prise en charge de la fonctionnalité ShouldProcess, consultez [demande de confirmation](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaction

Groupe logique de commandes traitées comme une tâche unique.
La tâche échoue automatiquement si une commande du groupe échoue et que l’utilisateur a le choix d’accepter ou de rejeter les actions effectuées dans la transaction.
Pour participer à une transaction, l’applet de commande doit déclarer qu’elle prend en charge les transactions lorsque l’attribut d’applet de commande est déclaré.
La prise en charge des transactions a été introduite dans Windows PowerShell 2,0.
Pour plus d’informations sur les transactions, consultez [How to support transactions](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Différences entre les applets de commande et les commandes

Les applets de commande diffèrent des commandes dans d’autres environnements de l’interpréteur de commandes des manières suivantes :

- Les applets de commande sont des instances de .NET Framework classes ; ce ne sont pas des exécutables autonomes.

- Les applets de commande peuvent être créées à partir d’une douzaine de lignes de code.

- Les applets de commande n’effectuent généralement pas leur propre analyse, présentation d’erreur ou mise en forme de sortie. L’analyse, la présentation des erreurs et la mise en forme de la sortie sont gérées par le runtime Windows PowerShell.

- Les applets de commande traitent les objets d’entrée du pipeline plutôt que des flux de texte, et les cmdlets délivrent généralement des objets comme sortie au pipeline.

- Les applets de commande sont orientées enregistrement, car elles traitent un seul objet à la fois.

## <a name="cmdlet-base-classes"></a>Classes de base de l’applet de commande

Windows PowerShell prend en charge les applets de commande dérivées des deux classes de base suivantes.

- La plupart des applets de commande sont basées sur les classes de .NET Framework qui dérivent de la classe de base [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande. La dérivation de cette classe permet à une applet de commande d’utiliser l’ensemble minimal de dépendances sur le runtime Windows PowerShell. Cela présente deux avantages. Le premier avantage est que les objets d’applet de commande sont plus petits et que vous êtes moins susceptible d’être affecté par les modifications apportées au runtime Windows PowerShell. Le deuxième avantage est que, si vous en avez besoin, vous pouvez créer directement une instance de l’objet cmdlet, puis l’appeler directement au lieu de l’appeler par le biais du runtime Windows PowerShell.

- Les cmdlets les plus complexes sont basées sur les classes de .NET Framework qui dérivent de la classe de base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . La dérivation de cette classe vous donne un plus grand accès au runtime Windows PowerShell. Cet accès permet à votre applet de commande d’appeler des scripts, d’accéder à des fournisseurs et d’accéder à l’état de session actuel. (Pour accéder à l’état de session actuel, vous recevez et définissez des variables et des préférences de session.) Toutefois, la dérivation de cette classe augmente la taille de l’objet cmdlet, et cela signifie que votre applet de commande est plus étroitement couplée à la version actuelle du runtime Windows PowerShell.

En général, sauf si vous avez besoin de l’accès étendu au runtime Windows PowerShell, vous devez dériver de la classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande. Toutefois, le runtime Windows PowerShell dispose de fonctionnalités de journalisation étendues pour l’exécution des applets de commande. Si votre modèle d’audit dépend de cette journalisation, vous pouvez empêcher l’exécution de votre applet de commande à partir d’une autre applet de commande en dérivant de la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="input-processing-methods"></a>Méthodes de traitement d’entrée

La classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande fournit les méthodes virtuelles suivantes qui sont utilisées pour traiter les enregistrements. Toutes les classes d’applet de commande dérivées doivent remplacer une ou plusieurs des trois premières méthodes :

- [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): permet de fournir une fonctionnalité facultative de prétraitement pour l’applet de commande.

- [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): permet de fournir des fonctionnalités d’enregistrement par enregistrement pour l’applet de commande. La méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) peut être appelée un nombre quelconque de fois, ou pas du tout, en fonction de l’entrée de l’applet de commande.

- [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): permet de fournir une fonctionnalité facultative de prétraitement pour l’applet de commande.

- [System. Management. Automation. applet de commande. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): utilisé pour arrêter le traitement lorsque l’utilisateur arrête l’applet de commande de façon asynchrone (par exemple, en appuyant sur Ctrl + C).

Pour plus d’informations sur ces méthodes, consultez [méthodes de traitement d’entrée des applets](./cmdlet-input-processing-methods.md)de commande.

## <a name="cmdlet-attributes"></a>Attributs des applets de commande

Windows PowerShell définit plusieurs attributs de .NET Framework qui sont utilisés pour gérer les applets de commande et pour spécifier les fonctionnalités communes fournies par Windows PowerShell et qui peuvent être requises par l’applet de commande. Par exemple, les attributs sont utilisés pour désigner une classe comme applet de commande, pour spécifier les paramètres de l’applet de commande et pour demander la validation de l’entrée afin que les développeurs d’applets de commande n’aient pas à implémenter cette fonctionnalité dans leur code d’applet de commande. Pour plus d’informations sur les attributs, consultez [attributs Windows PowerShell](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Noms des applets de commande

Windows PowerShell utilise une paire verbe-nom-nom pour nommer les applets de commande. Par exemple, l’applet de commande `Get-Command` incluse dans Windows PowerShell est utilisée pour obtenir toutes les cmdlets inscrites dans l’interface de commande. Le verbe identifie l’action effectuée par l’applet de commande, et le nom identifie la ressource sur laquelle l’applet de commande exécute son action.

Ces noms sont spécifiés lorsque la classe .NET Framework est déclarée en tant qu’applet de commande. Pour plus d’informations sur la façon de déclarer une classe .NET Framework en tant qu’applet de commande, consultez [déclaration d’attribut d’applet](./cmdlet-class-declaration.md)de commande.

## <a name="writing-cmdlet-code"></a>Écriture du code de l’applet de commande

Ce document propose deux méthodes pour découvrir comment le code de l’applet de commande est écrit. Si vous préférez voir le code sans trop d’explications, consultez [exemples de code d’applet de](./examples-of-cmdlet-code.md)commande. Si vous préférez plus d’explications sur le code, consultez les rubriques didacticiel [GetProc](./getproc-tutorial.md), didacticiel [StopProc](./stopproc-tutorial.md)ou [didacticiel SelectStr](./selectstr-tutorial.md) .

Pour plus d’informations sur les instructions d’écriture des applets de commande, consultez [instructions de développement d’applets](./cmdlet-development-guidelines.md)de commande.

## <a name="see-also"></a>Voir aussi

[Concepts des applets de commande Windows PowerShell](./windows-powershell-cmdlet-concepts.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
