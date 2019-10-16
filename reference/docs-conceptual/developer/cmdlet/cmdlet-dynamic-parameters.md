---
title: Paramètres dynamiques des applets de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369878"
---
# <a name="cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande

Les applets de commande peuvent définir des paramètres qui sont disponibles pour l’utilisateur dans des conditions spéciales, par exemple lorsque l’argument d’un autre paramètre est une valeur spécifique. Ces paramètres sont ajoutés au moment de l’exécution et sont appelés paramètres dynamiques, car ils sont ajoutés uniquement lorsque cela est nécessaire. Par exemple, vous pouvez concevoir une applet de commande qui ajoute plusieurs paramètres uniquement lorsqu’un paramètre de commutateur spécifique est spécifié.

> [!NOTE]
> Les fournisseurs et les fonctions PowerShell peuvent également définir des paramètres dynamiques.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Paramètres dynamiques dans les applets de commande PowerShell

PowerShell utilise des paramètres dynamiques dans plusieurs de ses applets de commande de fournisseur. Par exemple, les applets de commande `Get-Item` et `Get-ChildItem` ajoutent un paramètre **CodeSigningCert** au moment de l’exécution lorsque le paramètre **path** spécifie le chemin d’accès du fournisseur de **certificats** . Si le paramètre **path** spécifie un chemin d’accès pour un autre fournisseur, le paramètre **CodeSigningCert** n’est pas disponible.

Les exemples suivants montrent comment le paramètre **CodeSigningCert** est ajouté lors de l’exécution lorsque `Get-Item` est exécutée.

Dans cet exemple, le runtime PowerShell a ajouté le paramètre et l’applet de commande est réussie.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

Dans cet exemple, un lecteur de **système de fichiers** est spécifié et une erreur est retournée. Le message d’erreur indique que le paramètre **CodeSigningCert** est introuvable.

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Prise en charge des paramètres dynamiques

Pour prendre en charge les paramètres dynamiques, les éléments suivants doivent être inclus dans le code de l’applet de commande.

### <a name="interface"></a>Interface

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Cette interface fournit la méthode qui récupère les paramètres dynamiques.

Par exemple :

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Méthode

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Cette méthode récupère l’objet qui contient les définitions de paramètres dynamiques.

Par exemple :

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

### <a name="class"></a>Classe

Classe qui définit les paramètres dynamiques à ajouter. Cette classe doit inclure un attribut de **paramètre** pour chaque paramètre et tout **alias** facultatif et attributs de **validation** requis par l’applet de commande.

Par exemple :

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

Pour obtenir un exemple complet d’une applet de commande qui prend en charge les paramètres dynamiques, consultez [comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
