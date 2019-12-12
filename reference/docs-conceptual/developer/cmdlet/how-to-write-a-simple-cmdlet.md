---
title: Comment écrire une applet de commande simple | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365468"
---
# <a name="how-to-write-a-cmdlet"></a>Comment écrire une applet de commande

Cet article explique comment écrire une applet de commande. L’applet de commande `Send-Greeting` prend un nom d’utilisateur unique comme entrée, puis écrit un message d’accueil pour cet utilisateur. Bien que l’applet de commande n’effectue pas de nombreuses tâches, cet exemple illustre les principales sections d’une applet de commande.

## <a name="steps-to-write-a-cmdlet"></a>Étapes d’écriture d’une applet de commande

1. Pour déclarer la classe en tant qu’applet de commande, utilisez l’attribut d' **applet** de commande. L’attribut d' **applet** de commande spécifie le verbe et le nom du nom de l’applet de commande.

   Pour plus d’informations sur l’attribut d' **applet** de commande, consultez [déclaration CmdletAttribute](cmdlet-attribute-declaration.md).

2. Spécifiez le nom de la classe.

3. Spécifiez que l’applet de commande dérive de l’une des classes suivantes :

   * [System. Management. Automation. applet de commande](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Pour définir les paramètres de l’applet de commande, utilisez l’attribut **Parameter** . Dans ce cas, un seul paramètre obligatoire est spécifié.

   Pour plus d’informations sur l’attribut de **paramètre** , consultez [déclaration ParameterAttribute](parameter-attribute-declaration.md).

5. Substituez la méthode de traitement d’entrée qui traite l’entrée. Dans ce cas, la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est remplacée.

6. Pour écrire le message d’accueil, utilisez la méthode [System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Le message d’accueil s’affiche au format suivant :

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Exemple

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande](/dotnet/api/System.Management.Automation.Cmdlet)

[System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Déclaration CmdletAttribute](cmdlet-attribute-declaration.md)

[Déclaration ParameterAttribute](parameter-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](writing-a-windows-powershell-cmdlet.md)