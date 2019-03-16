---
title: Messages de confirmation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059471"
---
# <a name="confirmation-messages"></a>Messages de confirmation

Voici les messages de confirmation différents qui peuvent être affichées selon les variantes de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes qui sont appelées.

> [!IMPORTANT]
> Pour l’exemple de code qui montre comment demander des confirmations, consultez [comment des Confirmations de demande](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Spécification de la ressource

Vous pouvez spécifier la ressource doit être modifiée en appelant le [System.Management.Automation.Cmdlet.Shouldprocess%2A ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (méthode). Dans ce cas, vous fournissez la ressource à l’aide de le `target` paramètre de la méthode et l’opération est ajouté par Windows PowerShell. Dans le message suivant, le texte « MyResource » est la ressource de l’action et l’opération est le nom de la commande qui effectue l’appel.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si l’utilisateur sélectionne **Oui** ou **Oui pour tout** à la confirmation de la demande (comme indiqué dans l’exemple suivant), un appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)méthode est effectuée, ce qui entraîne un deuxième message de confirmation s’affiche.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Spécification de l’opération et les ressources

Vous pouvez spécifier la ressource qui doit être modifié et l’opération que la commande va effectuer en appelant le [System.Management.Automation.Cmdlet.Shouldprocess%2A ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (méthode). Dans ce cas, vous fournissez la ressource à l’aide de la `target` paramètre et l’opération à l’aide de le `target` paramètre. Dans le message suivant, le texte « MyResource » est la ressource de l’action et « MyAction » est l’opération à effectuer.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si l’utilisateur sélectionne **Oui** ou **Oui pour tout** le message précédent, un appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode est effectué, ce qui conduit un deuxième message de confirmation s’affiche.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
