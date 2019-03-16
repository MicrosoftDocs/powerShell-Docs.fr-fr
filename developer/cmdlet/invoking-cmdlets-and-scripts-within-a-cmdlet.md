---
title: Appel des applets de commande et Scripts au sein d’une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058876"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Appel d’applets de commande et de scripts dans une applet de commande

Une applet de commande peut appeler les autres applets de commande et les scripts à partir de l’entrée de la méthode de l’applet de commande de traitement. Cela vous permet de vous permet d’ajouter la fonctionnalité d’applets de commande existantes et des scripts à votre applet de commande sans avoir à réécrire le code.

## <a name="the-invoke-method"></a>L’appel de méthode

Toutes les applets de commande peuvent invoquer une cmdlet existante en appelant le [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode à partir d’une entrée de traitement de méthode, telle que [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), qui est remplacée par l’applet de commande. Toutefois, vous pouvez appeler uniquement ces applets de commande qui dérivent directement de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Vous ne pouvez pas appeler une applet de commande qui dérive de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

Le [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode a les variantes suivantes.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet de l’applet de commande et retourne une collection d’objets de type « T ».

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) cette variante appelle l’objet de l’applet de commande et retourne un emumerator fortement typée. Cette variante permet à l’utilisateur à utiliser les objets dans la collection pour effectuer des opérations personnalisées.

## <a name="examples"></a>Exemples

|Exemple|Description|
|-------------|-----------------|
|[Appel des applets de commande au sein d’une applet de commande](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande.|
|[Appel de Scripts au sein d’une applet de commande](./how-to-invoke-scripts-within-a-cmdlet.md)|Cet exemple montre comment appeler un script qui est fourni à l’applet de commande à partir d’une autre applet de commande.|

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
