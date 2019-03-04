---
title: Comment écrire une applet de commande Simple | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251453"
---
# <a name="how-to-write-a-cmdlet"></a>Comment écrire une applet de commande

Cet article explique comment écrire une applet de commande. Le `Send-Greeting` applet de commande prend un nom d’utilisateur unique comme entrée, puis écrit un message d’accueil pour cet utilisateur. Bien que l’applet de commande ne fait pas beaucoup de travail, cet exemple montre les sections principales d’une applet de commande.

## <a name="steps-to-write-a-cmdlet"></a>Étapes permettant d’écrire une applet de commande

1. Pour déclarer la classe comme une applet de commande, utilisez le **applet de commande** attribut. Le **applet de commande** attribut spécifie le verbe et le nom pour le nom de l’applet de commande.

   Pour plus d’informations sur la **applet de commande** d’attribut, consultez [déclaration CmdletAttribute](cmdlet-attribute-declaration.md).

2. Spécifiez le nom de la classe.

3. Spécifier que l’applet de commande dérivée d’une des classes suivantes :

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Pour définir les paramètres de l’applet de commande, utilisez le **paramètre** attribut. Dans ce cas, seul obligatoire de paramètre est spécifié.

   Pour plus d’informations sur la **paramètre** d’attribut, consultez [ParameterAttribute déclaration](parameter-attribute-declaration.md).

5. Substituez la méthode qui traite l’entrée de traitement des entrées. Dans ce cas, le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) la substitution de méthode.

6. Pour écrire le message d’accueil, utilisez la méthode [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Le message d’accueil s’affiche dans le format suivant :

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

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Déclaration CmdletAttribute](cmdlet-attribute-declaration.md)

[Déclaration de ParameterAttribute](parameter-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](writing-a-windows-powershell-cmdlet.md)