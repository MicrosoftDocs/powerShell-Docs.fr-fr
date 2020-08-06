---
title: Exemple Windows PowerShell02 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a82366a88addb08e186eede79e621d90d915c50f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779384"
---
# <a name="windows-powershell02-sample"></a>Exemple Windows PowerShell02

Cet exemple montre comment exécuter des commandes de manière asynchrone à l’aide du instances d’exécution d’un pool d’instances d’exécution. L’exemple génère une liste de commandes, puis exécute ces commandes lorsque le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsque cela est nécessaire.

## <a name="requirements"></a>Spécifications

- Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple indique :

- La création d’un objet RunspacePool avec un nombre minimal et maximal de instances d’exécution autorisé à être ouvert en même temps.
- Création d’une liste de commandes.
- Exécution des commandes de manière asynchrone.
- Appel de la méthode [System. Management. Automation. instances d’exécution. Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) pour connaître le nombre de instances d’exécution disponibles.
- Capture de la sortie de commande avec la méthode [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

## <a name="example"></a>Exemple

Cet exemple montre comment ouvrir le instances d’exécution d’un pool d’instances d’exécution et comment exécuter de manière asynchrone des commandes dans ces instances d’exécution.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>Voir aussi

[Écriture d’une application hôte Windows PowerShell](./writing-a-windows-powershell-host-application.md)
