---
ms.date: 09/13/2016
ms.topic: reference
title: Appel d’applets de commande et de scripts dans une applet de commande
description: Appel d’applets de commande et de scripts dans une applet de commande
ms.openlocfilehash: 246c61661f2d290e7e7ac62a8ad303b05bdc7582
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652654"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Appel d’applets de commande et de scripts dans une applet de commande

Une applet de commande peut appeler d’autres applets de commande et scripts à partir de la méthode de traitement d’entrée de l’applet de commande. Cela vous permet d’ajouter les fonctionnalités des applets de commande et des scripts existants à votre applet de commande sans avoir à réécrire le code.

## <a name="the-invoke-method"></a>La méthode Invoke

Toutes les applets de commande peuvent appeler une applet de commande existante en appelant la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) de commande à partir d’une méthode de traitement d’entrée, telle que [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), qui est remplacée par l’applet de commande. Toutefois, vous pouvez appeler uniquement les applets de commande qui dérivent directement de la classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande. Vous ne pouvez pas appeler une applet de commande qui dérive de la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

La méthode [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) contient les variantes suivantes.

[System. Management. Automation. applet de commande. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet d’applet de commande et retourne une collection d’objets de type « T ».

[System. Management. Automation. applet de commande. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet cmdlet et retourne un emumerator fortement typé. Cette variante permet à l’utilisateur d’utiliser les objets de la collection pour effectuer des opérations personnalisées.

## <a name="examples"></a>Exemples

|Exemple|Description|
|-------------|-----------------|
|[Appel d’applets de commande dans une applet de commande](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande.|
|[Appel de scripts dans une applet de commande](./how-to-invoke-scripts-within-a-cmdlet.md)|Cet exemple montre comment appeler un script fourni à l’applet de commande à partir d’une autre applet de commande.|

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
