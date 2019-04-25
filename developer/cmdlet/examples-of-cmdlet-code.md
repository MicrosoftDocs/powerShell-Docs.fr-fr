---
title: Exemples de Code de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068196"
---
# <a name="examples-of-cmdlet-code"></a>Exemples de code d’applet de commande

Cette section contient des exemples de code d’applet de commande que vous pouvez utiliser pour commencer à écrire vos propres applets de commande.

> [!IMPORTANT]
> Si vous souhaitez obtenir des instructions détaillées pour l’écriture des applets de commande, consultez [didacticiels pour écrire les applets de commande](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>Dans cette section

[Comment écrire une applet de commande Simple](./how-to-write-a-simple-cmdlet.md) cet exemple montre la structure de base de code de l’applet de commande.

[Comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md) cet exemple montre comment déclarer les différents types de paramètres.

[Comment déclarer des jeux de paramètres](./how-to-declare-parameter-sets.md) cet exemple montre comment déclarer des jeux de paramètres qui peuvent changer l’action effectue une applet de commande.

[Comment valider l’entrée paramètre](./how-to-validate-parameter-input.md) ces exemples montrent comment valider les entrées de paramètre.

[Comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md) cet exemple montre comment déclarer un paramètre qui est ajouté à l’exécution.

[Comment appeler des Scripts au sein d’une applet de commande](./how-to-invoke-scripts-within-a-cmdlet.md) cet exemple montre comment appeler un script qui est fourni à une applet de commande.

[Comment substituer les méthodes de traitement de l’entrée](./how-to-override-input-processing-methods.md) ces exemples montrent la structure de base utilisée pour substituer les méthodes BeginProcessing, ProcessRecord et EndProcessing.

[Comment la prise en charge les appels de ShouldProcess](./how-to-request-confirmations.md) cet exemple montre comment la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes doivent être appelées à partir une applet de commande.

[Comment la prise en charge des Transactions](./how-to-support-transactions.md) cet exemple montre comment indiquer que l’applet de commande prend en charge les transactions et l’implémentation de l’action qui est effectuée lorsque l’applet de commande est utilisée dans une transaction.

[Comment prendre en charge les travaux](./how-to-support-jobs.md) cet exemple montre comment prendre en charge des travaux lorsque vous écrivez des applets de commande.

[L’appel d’une applet de commande à partir d’au sein d’une applet de commande](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, qui vous permet d’ajouter les fonctionnalités de l’applet de commande appelée à l’applet de commande que vous développez.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
