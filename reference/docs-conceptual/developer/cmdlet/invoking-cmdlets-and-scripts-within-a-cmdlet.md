---
title: Appel d’applets de commande et de scripts au sein d’une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364288"
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
