---
title: Exemple de PowerShell02 Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082513"
---
# <a name="windows-powershell02-sample"></a>Exemple Windows PowerShell02

Cet exemple montre comment exécuter des commandes de façon asynchrone à l’aide les instances d’exécution d’un pool de l’instance d’exécution. L’exemple génère une liste de commandes, puis exécute ces commandes pendant que le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsqu’il est nécessaire.

## <a name="requirements"></a>Spécifications

- Cet exemple requiert Windows PowerShell 2.0.

## <a name="demonstrates"></a>Montre

Cet exemple montre les éléments suivants :

- Création d’un objet RunspacePool avec un nombre minimal et maximal d’instances d’exécution peuvent être ouverts en même temps.

- Création d’une liste de commandes.

- Exécuter les commandes de façon asynchrone.

- Appel de la [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) méthode pour voir combien d’instances sont gratuits.

- Capture la sortie de commande avec le [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (méthode).

## <a name="example"></a>Exemple

Cet exemple montre comment ouvrir les instances d’exécution d’un pool de l’instance d’exécution et comment exécuter des commandes de façon asynchrone dans ces instances d’exécution.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Voir aussi

[Écriture d’une Application hôte PowerShell de Windows](./writing-a-windows-powershell-host-application.md)