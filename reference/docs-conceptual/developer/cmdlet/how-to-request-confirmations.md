---
title: Comment demander des confirmations | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebe928724f1b750afc11c1e3c1207375f4ec8e42
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784093"
---
# <a name="how-to-request-confirmations"></a>Guide pratique pour demander des confirmations

Cet exemple montre comment appeler les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) pour demander des confirmations à l’utilisateur avant qu’une action soit effectuée.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont Windows PowerShell gère ces requêtes, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Pour demander une confirmation

1. Assurez-vous que le `SupportsShouldProcess` paramètre de l’attribut d’applet de commande a la valeur `true` . (Pour functions, il s’agit d’un paramètre de l’attribut CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Ajoutez un `Force` paramètre à votre applet de commande pour permettre à l’utilisateur de remplacer une demande de confirmation.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Ajoutez une `if` instruction qui utilise la valeur de retour de la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour déterminer si la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est appelée.

4. Ajoutez une deuxième `if` instruction qui utilise la valeur de retour de la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et la valeur du `Force` paramètre pour déterminer si l’opération doit être effectuée.

## <a name="example"></a>Exemple

Dans l’exemple de code suivant, les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) sont appelées à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Toutefois, vous pouvez également appeler ces méthodes à partir des autres méthodes de traitement d’entrée.

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
