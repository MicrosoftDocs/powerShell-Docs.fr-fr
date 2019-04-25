---
title: Paramètres de l’applet de commande dynamique | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068536"
---
# <a name="cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande

Applets de commande peut définir des paramètres qui sont disponibles à l’utilisateur sous certaines conditions, par exemple lorsque l’argument d’un autre paramètre est une valeur spécifique. Ces paramètres sont ajoutés lors de l’exécution et sont appelés *paramètres dynamiques* , car ils sont ajoutés uniquement lorsqu’elles sont nécessaires. Par exemple, vous pouvez concevoir une applet de commande qui ajoute plusieurs paramètres uniquement lorsqu’un paramètre de commutateur spécifique est spécifié.

> [!NOTE]
> Fournisseurs et des fonctions Windows PowerShell peuvent également définir des paramètres dynamiques.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Paramètres dynamiques dans les applets de commande Windows PowerShell

Windows PowerShell utilise des paramètres dynamiques dans plusieurs de ses applets de commande fournisseur. Par exemple, le `Get-Item` et `Get-ChildItem` ajouter des applets de commande un `CodeSigningCert` paramètre lors de l’exécution lorsque le `Path` paramètre de l’applet de commande spécifie le chemin d’accès du fournisseur de certificat. Si le `Path` paramètre de l’applet de commande spécifie un chemin d’accès pour un autre fournisseur, le `CodeSigningCert` paramètre n’est pas disponible.

Les exemples suivants montrent comment la `CodeSigningCert` paramètre est ajouté lors de l’exécution lorsque le `Get-Item` applet de commande est exécutée.

Dans le premier exemple, le runtime Windows PowerShell a ajouté le paramètre, et l’applet de commande a réussi.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

Dans le deuxième exemple, un lecteur de système de fichiers est spécifié, et une erreur est retournée. Le message d’erreur indique que le `CodeSigningCert` paramètre ne peut pas être trouvé.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Prise en charge pour les paramètres dynamiques

Pour prendre en charge des paramètres dynamiques, le code de l’applet de commande doit inclure les éléments suivants.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) cette interface fournit la méthode qui Récupère les paramètres dynamiques.

Exemple :

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) cette méthode récupère l’objet qui contient les définitions de paramètre dynamique.

Exemple :

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

Classe de paramètre dynamique cette classe définit les paramètres à ajouter. Cette classe doit inclure un attribut de paramètre pour chaque paramètre et les attributs facultatifs Alias et la Validation qui sont requises par l’applet de commande.

Exemple :

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Pour obtenir un exemple complet d’une applet de commande qui prend en charge des paramètres dynamiques, consultez [comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
