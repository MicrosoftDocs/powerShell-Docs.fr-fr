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
ms.openlocfilehash: f8a8c9300d1ac811c7fbbf7050dd24f78306db8f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068468"
---
# <a name="cmdlet-overview"></a>Vue d’ensemble des applets de commande

Une applet de commande est une commande légère utilisée dans l’environnement Windows PowerShell. Le runtime de Windows PowerShell appelle ces applets de commande dans le contexte des scripts d’automatisation qui sont fournies à la ligne de commande. Le runtime Windows PowerShell également les appelle par programme via Windows APIs PowerShell.

## <a name="cmdlets"></a>Applets de commande

Applets de commande effectuent une action et retournent généralement un objet Microsoft .NET Framework à la commande suivante dans le pipeline. Pour écrire une applet de commande, vous devez implémenter une classe d’applet de commande qui dérive d’une des deux classes de base d’applet de commande spécialisé. La classe dérivée doit :

- Déclarer un attribut qui identifie la classe dérivée en tant qu’une applet de commande.

- Définir des propriétés publiques qui sont décorées avec des attributs qui identifient les propriétés publiques en tant que paramètres de l’applet de commande.

- Substituez une ou plusieurs de l’entrée de méthodes pour traiter les enregistrements de traitement.

Vous pouvez charger l’assembly qui contient la classe directement à l’aide du [Import-Module](/powershell/module/microsoft.powershell.core/import-module) applet de commande, ou vous pouvez créer une application hôte qui charge l’assembly à l’aide de la [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Les deux méthodes fournissent un accès par programmation et de ligne de commande pour les fonctionnalités de l’applet de commande.

## <a name="cmdlet-terms"></a>Termes du contrat de l’applet de commande

Les termes suivants sont fréquemment utilisées dans la documentation d’applet de commande Windows PowerShell :

- **Attribut de l’applet de commande**: Un attribut .NET Framework qui est utilisé pour déclarer une classe de l’applet de commande comme une applet de commande. Bien que Windows PowerShell utilise plusieurs autres attributs sont facultatifs, l’attribut de l’applet de commande est requis. Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).

- **Paramètre d’applet de commande**: Les propriétés publiques qui définissent les paramètres qui sont disponibles à l’utilisateur ou à l’application qui exécute l’applet de commande. Applets de commande peut avoir requis, nommé, positionnels, et *basculer* paramètres. Paramètres de commutateur permettent de définir des paramètres qui sont évaluées uniquement si les paramètres sont spécifiés dans l’appel. Pour plus d’informations sur les différents types de paramètres, consultez [paramètres de l’applet de commande](./cmdlet-parameters.md).

- **Jeu de paramètres**: Groupe de paramètres qui peut être utilisé dans la même commande pour effectuer une action spécifique. Une applet de commande peut avoir plusieurs jeux de paramètres, mais chaque jeu de paramètres doit avoir au moins un paramètre qui est unique. Conception de l’applet de commande bonne suggère fortement que le paramètre unique doit également être un paramètre obligatoire. Pour plus d’informations sur les jeux de paramètres, consultez [définit des paramètres d’applet de commande](./cmdlet-parameter-sets.md).

- **Paramètre dynamique**: Un paramètre qui est ajouté à l’applet de commande lors de l’exécution. En règle générale, les paramètres dynamiques sont ajoutés à l’applet de commande quand un autre paramètre est défini sur une valeur spécifique. Pour plus d’informations sur les paramètres dynamiques, consultez [applet de commande des paramètres dynamiques](./cmdlet-dynamic-parameters.md).

- **Méthode de traitement d’entrée**: Méthode qu’une applet de commande peut utiliser pour traiter les enregistrements qu’elle reçoit en entrée. Les méthodes de traitement d’entrée incluent la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode), le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode), le [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode) et le [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) (méthode). Lorsque vous implémentez une applet de commande, vous devez substituer au moins de la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)et [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthodes. En règle générale, le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode est la méthode que vous substituez parce qu’elle est appelée pour chaque enregistrement qui traite de l’applet de commande. En revanche, le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode) et le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode est appelée une fois pour effectuer prétraitement ou de post-traitement des enregistrements. Pour plus d’informations sur ces méthodes, consultez [méthodes de traitement d’entrée](./cmdlet-input-processing-methods.md).

- **Fonctionnalité de ShouldProcess**: Windows PowerShell vous permet de créer des applets de commande qui invite l’utilisateur pour envoyer des commentaires avant que l’applet de commande effectue une modification dans le système. Pour utiliser cette fonctionnalité, l’applet de commande doit déclarer qu’il prend en charge la fonctionnalité de ShouldProcess quand vous déclarez l’attribut de l’applet de commande et l’applet de commande doit appeler le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes à partir d’au sein d’une méthode de traitement des entrées. Pour plus d’informations sur la prise en charge la fonctionnalité de ShouldProcess, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

- **Transaction**: Un groupe logique de commandes qui sont traitées comme une seule tâche. Automatiquement, la tâche échoue si une commande dans le groupe échoue et l’utilisateur a le choix d’accepter ou rejeter les actions effectuées au sein de la transaction. Pour participer à une transaction, l’applet de commande doit être déclarée qu’il prend en charge les transactions lorsque l’attribut de l’applet de commande est déclaré. Prise en charge des transactions a été introduite dans Windows PowerShell 2.0. Pour plus d’informations sur les transactions, consultez [Windows PowerShell Transactions](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).

## <a name="how-cmdlets-differ-from-commands"></a>Comment diffèrent des applets de commande des commandes

Applets de commande diffèrent des commandes dans d’autres environnements de l’interface de commande comme suit :

- Applets de commande sont des instances de classes .NET Framework ; ils ne sont pas exécutables autonomes.

- Applets de commande peuvent être créés à partir d’une dizaine de lignes de code seulement.

- Applets de commande ne procédez pas généralement leurs propres l’analyse, présentation de l’erreur ou la mise en forme de sortie. L’analyse, la présentation de l’erreur et la mise en forme de sortie sont gérées par le runtime de Windows PowerShell.

- Processus des applets de commande d’entrée d’objets du pipeline, plutôt qu’à partir de flux de texte et applets de commande fournissent généralement des objets en tant que sortie au pipeline.

- Applets de commande sont orientées par enregistrement, car ils traitent un seul objet à la fois.

## <a name="cmdlet-base-classes"></a>Classes de Base de l’applet de commande

Windows PowerShell prend en charge les applets de commande qui sont dérivées de deux classes de base suivantes.

- La plupart des applets de commande sont basées sur les classes de .NET Framework qui dérivent de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe de base. Dérivation à partir de cette classe permet à une applet de commande à utiliser l’ensemble minimal de dépendances sur le runtime de Windows PowerShell. Cela présente deux avantages. Le premier avantage est que les objets de l’applet de commande sont plus petits, et vous êtes moins susceptible d’être affecté par les modifications à l’exécution de Windows PowerShell. Le deuxième avantage est que, si vous devez, vous pouvez créer directement une instance de l’objet de l’applet de commande, puis l’appeler directement au lieu d’appeler via le runtime de Windows PowerShell.

- Les applets de commande plus complexes sont basés sur les classes .NET Framework qui dérivent de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe de base. Dérivation à partir de cette classe vous donne un accès beaucoup plus à l’exécution de Windows PowerShell. Cet accès permet à votre applet de commande à appeler des scripts, pour accéder aux fournisseurs et à accéder à l’état de session en cours. (Pour accéder à l’état de session actuel, vous obtenez et définissez les préférences et les variables de session.) Toutefois, dérivation à partir de cette classe augmente la taille de l’objet de l’applet de commande, et cela signifie que votre applet de commande est plus étroitement lié à la version actuelle du runtime Windows PowerShell.

En règle générale, sauf si vous avez besoin de l’accès étendu à l’exécution de Windows PowerShell, vous devez dériver de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Toutefois, le runtime de Windows PowerShell a des fonctions de journalisation étendues pour l’exécution d’applets de commande. Si votre modèle audit dépend de cette journalisation, vous pouvez empêcher l’exécution de votre applet de commande à partir d’une autre applet de commande en dérivant le [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

## <a name="input-processing-methods"></a>Méthodes de traitement d’entrée

Le [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fournit les méthodes virtuelles suivantes qui sont utilisés pour traiter les enregistrements. Toutes les classes de l’applet de commande dérivées doivent remplacer une ou plusieurs des trois premières méthodes :

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Utilisé pour fournir une fonctionnalité de prétraitement unique facultative pour l’applet de commande.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Utilisé pour fournir des fonctionnalités de traitement de l’enregistrement par enregistrement pour l’applet de commande. Le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode peut être appelée à n’importe quel nombre de fois ou pas du tout, selon les entrées de l’applet de commande.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Utilisé pour fournir une fonctionnalité de post-traitement unique facultative pour l’applet de commande.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Utilisé pour arrêter le traitement lorsque l’utilisateur arrête l’applet de commande de façon asynchrone (par exemple, en appuyant sur CTRL + C).

Pour plus d’informations sur ces méthodes, consultez [méthodes de traitement entrée applet de commande](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Attributs des applets de commande

Windows PowerShell définit plusieurs attributs de .NET Framework qui sont utilisées pour gérer des applets de commande et pour spécifier des fonctionnalités communes, qui est fournie par Windows PowerShell et qui peut être requis par l’applet de commande. Par exemple, les attributs sont utilisés pour désigner une classe comme une applet de commande pour spécifier les paramètres de l’applet de commande et pour demander la validation d’entrée afin que les développeurs de l’applet de commande n’ont pas à implémenter cette fonctionnalité dans leur code de l’applet de commande. Pour plus d’informations sur les attributs, consultez [Windows PowerShell attributs](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Noms d’applet de commande

Windows PowerShell utilise une paire de nom de type verbe-substantif aux applets de commande de nom. Par exemple, le `Get-Command` applet de commande inclus dans Windows PowerShell est utilisé pour obtenir toutes les applets de commande qui sont inscrits dans l’interface de commande. Le verbe identifie l’action qui exécute l’applet de commande, et le substantif identifie la ressource sur laquelle l’applet de commande effectue son action.

Ces noms sont spécifiés lors de la classe .NET Framework est déclarée comme une applet de commande. Pour plus d’informations sur la façon de déclarer une classe .NET Framework en tant qu’une applet de commande, consultez [déclaration d’attribut applet de commande](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Écriture de Code applet de commande

Ce document fournit deux méthodes pour découvrir comment le code de l’applet de commande est écrit. Si vous préférez afficher le code sans trop d’explications, consultez [exemples de Code d’applet de commande](./examples-of-cmdlet-code.md). Si vous préférez une explication plus détaillée concernant le code, consultez le [GetProc didacticiel](./getproc-tutorial.md), [StopProc didacticiel](./stopproc-tutorial.md), ou [SelectStr didacticiel](./selectstr-tutorial.md) rubriques.

Pour plus d’informations sur les instructions pour les applets de commande écriture, consultez [directives de développement d’applet de commande](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Voir aussi

[Concepts d’applet de commande PowerShell de Windows](./windows-powershell-cmdlet-concepts.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
