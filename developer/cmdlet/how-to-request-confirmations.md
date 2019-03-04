---
title: Comment demander des Confirmations | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863405"
---
# <a name="how-to-request-confirmations"></a>Guide pratique pour demander des confirmations

Cet exemple montre comment appeler le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes pour demander des confirmations à partir de la utilisateur avant d’effectuer une action.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont Windows PowerShell gère ces demandes, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Vous demande confirmation

1. Vérifiez que le `SupportsShouldProcess` paramètre de l’attribut de l’applet de commande est défini sur `true`. (Pour les fonctions ce paramètre est de l’attribut CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Ajouter un `Force` paramètre à votre applet de commande afin que l’utilisateur peut remplacer une demande de confirmation.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Ajouter un `if` instruction qui utilise la valeur de retour de la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode pour déterminer si le [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode est appelée.

4. Ajoutez une deuxième `if` instruction qui utilise la valeur de retour de la [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode) et la valeur de la `Force` paramètre pour déterminer si l’opération doit être effectuée.

## <a name="example"></a>Exemple

Dans l’exemple de code suivant, le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes sont appelées depuis le la substitution de la [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode). Toutefois, vous pouvez également appeler ces méthodes à partir de l’autre entrée de méthodes de traitement.

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
