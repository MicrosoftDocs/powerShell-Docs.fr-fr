---
title: Comment demander des confirmations | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369678"
---
# <a name="how-to-request-confirmations"></a>Guide pratique pour demander des confirmations

Cet exemple montre comment appeler les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) pour demander des confirmations à l’utilisateur avant qu’une action soit effectuée.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont Windows PowerShell gère ces requêtes, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Pour demander une confirmation

1. Assurez-vous que le paramètre `SupportsShouldProcess` de l’attribut d’applet de commande est défini sur `true`. (Pour functions, il s’agit d’un paramètre de l’attribut CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Ajoutez un paramètre `Force` à votre applet de commande afin que l’utilisateur puisse remplacer une demande de confirmation.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Ajoutez une instruction `if` qui utilise la valeur de retour de la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour déterminer si la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est appelée.

4. Ajoutez une deuxième instruction `if` qui utilise la valeur de retour de la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et la valeur du paramètre `Force` pour déterminer si l’opération doit être effectuée.

## <a name="example"></a>Exemple

Dans l’exemple de code suivant, les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) sont appelées à partir de la substitution de l' [applet de commande Méthode System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Toutefois, vous pouvez également appeler ces méthodes à partir des autres méthodes de traitement d’entrée.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
