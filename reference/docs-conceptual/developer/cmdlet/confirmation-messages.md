---
ms.date: 09/13/2016
ms.topic: reference
title: Messages de confirmation
description: Messages de confirmation
ms.openlocfilehash: 76302b2f8d8ca6dcdfe1b3c36f71aad23a53f7cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355185"
---
# <a name="confirmation-messages"></a>Messages de confirmation

Voici différents messages de confirmation qui peuvent être affichés en fonction des variantes des méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) qui sont appelées.

> [!IMPORTANT]
> Pour obtenir un exemple de code qui montre comment demander des confirmations, consultez [Comment demander des confirmations](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Spécification de la ressource

Vous pouvez spécifier la ressource qui va être modifiée en appelant [System. Management. Automation. cmdlet. ShouldProcess% 2A ? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). Dans ce cas, vous fournissez la ressource à l’aide du `target` paramètre de la méthode, et l’opération est ajoutée par Windows PowerShell. Dans le message suivant, le texte « MyResource » est la ressource sur laquelle l’opération est effectuée et l’opération est le nom de la commande qui effectue l’appel.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si l’utilisateur sélectionne **Oui** ou **Oui pour l’ensemble** de la demande de confirmation (comme indiqué dans l’exemple suivant), un appel à la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est effectué, ce qui entraîne l’affichage d’un deuxième message de confirmation.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Spécification de l’opération et de la ressource

Vous pouvez spécifier la ressource qui va être modifiée et l’opération que la commande va effectuer en appelant [System. Management. Automation. cmdlet. ShouldProcess% 2A ? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). Dans ce cas, vous fournissez la ressource à l’aide du `target` paramètre et de l’opération à l’aide du `target` paramètre. Dans le message suivant, le texte « MyResource » est la ressource traitée et « MyAction » est l’opération à effectuer.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Si l’utilisateur sélectionne **Oui** ou **Oui pour tout** le message précédent, un appel à la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est effectué, ce qui entraîne l’affichage d’un deuxième message de confirmation.

```Output
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
