---
title: Exemples de code d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364498"
---
# <a name="examples-of-cmdlet-code"></a>Exemples de code d’applet de commande

Cette section contient des exemples de code d’applet de commande que vous pouvez utiliser pour commencer à écrire vos propres applets de commande.

> [!IMPORTANT]
> Si vous souhaitez obtenir des instructions pas à pas pour l’écriture d’applets de commande, consultez [tutoriels pour l’écriture d’applets de](./tutorials-for-writing-cmdlets.md)commande.

## <a name="in-this-section"></a>Dans cette section

[Comment écrire une applet](./how-to-write-a-simple-cmdlet.md) de commande simple Cet exemple illustre la structure de base du code de l’applet de commande.

[Comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md) commande Cet exemple montre comment déclarer les différents types de paramètres.

[Comment déclarer des jeux de paramètres](./how-to-declare-parameter-sets.md) Cet exemple montre comment déclarer des ensembles de paramètres qui peuvent modifier l’action effectuée par une applet de commande.

[Comment valider une entrée de paramètre](./how-to-validate-parameter-input.md) Ces exemples montrent comment valider une entrée de paramètre.

[Comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md) Cet exemple montre comment déclarer un paramètre qui est ajouté au moment de l’exécution.

[Comment appeler des scripts dans une applet de](./how-to-invoke-scripts-within-a-cmdlet.md) commande Cet exemple montre comment appeler un script fourni à une applet de commande.

[Comment remplacer les méthodes de traitement d’entrée](./how-to-override-input-processing-methods.md) Ces exemples illustrent la structure de base utilisée pour substituer les méthodes BeginProcessing, ProcessRecord et EndProcessing.

[Comment prendre en charge les appels ShouldProcess](./how-to-request-confirmations.md) Cet exemple montre comment les méthodes [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doivent être appelées à partir d’une applet de commande.

[Comment prendre en charge les transactions](./how-to-support-transactions.md) Cet exemple montre comment indiquer que l’applet de commande prend en charge les transactions et comment implémenter l’action qui est effectuée lorsque l’applet de commande est utilisée dans une transaction.

[Comment prendre en charge les travaux](./how-to-support-jobs.md) Cet exemple montre comment prendre en charge des travaux lorsque vous écrivez des applets de commande.

[Comment appeler une applet de commande à partir d’une applet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) de commande Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, ce qui vous permet d’ajouter la fonctionnalité de l’applet de commande appelée à l’applet de commande que vous développez.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
