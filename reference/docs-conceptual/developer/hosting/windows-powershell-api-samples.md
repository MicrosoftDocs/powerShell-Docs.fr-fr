---
title: Exemples d’API Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d7232bb16851f1d568cbdfc4374e287d0875adc8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780166"
---
# <a name="windows-powershell-api-samples"></a>Exemples d’API Windows PowerShell

Cette section comprend un exemple de code qui montre comment créer des instances d’exécution qui restreignent les fonctionnalités et comment exécuter de façon asynchrone des commandes à l’aide d’un pool d’instances d’exécution pour fournir le instances d’exécution. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console, puis copier le code à partir des rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

[Exemple PowerShell01](./windows-powershell01-sample.md) Cet exemple montre comment utiliser un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour limiter les fonctionnalités d’une instance d’exécution. La sortie de cet exemple montre comment limiter le mode de langage de l’instance d’exécution, comment marquer une applet de commande comme étant privée, comment ajouter et supprimer des applets de commande et des fournisseurs, ajouter une commande de proxy, et bien plus encore.

[Exemple PowerShell02](./windows-powershell02-sample.md) Cet exemple montre comment exécuter des commandes de manière asynchrone à l’aide du instances d’exécution d’un pool d’instances d’exécution. L’exemple génère une liste de commandes, puis exécute ces commandes lorsque le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsque cela est nécessaire.
