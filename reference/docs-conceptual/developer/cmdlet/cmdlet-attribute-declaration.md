---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut Cmdlet
description: Déclaration de l’attribut Cmdlet
ms.openlocfilehash: 6bdfe39a4ab9ef4d4cc98daa592f69f7fab95e84
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653544"
---
# <a name="cmdlet-attribute-declaration"></a>Déclaration de l’attribut Cmdlet

L’attribut d’applet de commande identifie une classe Microsoft .NET Framework comme une applet de commande et spécifie le verbe et le nom utilisés pour appeler l’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

`VerbName` ([System. String](/dotnet/api/System.String)) requis. Spécifie le verbe d’applet de commande. Ce verbe spécifie l’action effectuée par l’applet de commande. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md) de commande et [instructions de développement requises](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) requis. Spécifie le nom de l’applet de commande. Ce substantif Spécifie la ressource sur laquelle l’applet de commande agit. Pour plus d’informations sur les noms d’applets de commande, consultez [déclaration d’applet](./cmdlet-class-declaration.md) de commande et [conseils de développement fortement encouragés](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` indique que l’applet de commande prend en charge les appels à la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , qui fournit à l’applet de commande un moyen d’inviter l’utilisateur avant l’exécution d’une action qui modifie le système. `False`, la valeur par défaut, indique que l’applet de commande ne prend pas en charge les appels à la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess. Pour plus d’informations sur les demandes de confirmation, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) paramètre nommé facultatif. Spécifie quand l’action de l’applet de commande doit être confirmée par un appel à la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess. [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) est appelé uniquement lorsque la valeur ConfirmImpact de l’applet de commande (par défaut, Medium) est supérieure ou égale à la valeur de la `$ConfirmPreference` variable. Ce paramètre doit être spécifié uniquement lorsque le `SupportsShouldProcess` paramètre est spécifié.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) paramètre nommé facultatif. Spécifie le jeu de paramètres par défaut que le runtime Windows PowerShell tente d’utiliser lorsqu’il ne peut pas déterminer le jeu de paramètres à utiliser. Notez que cette situation peut être éliminée en faisant du paramètre unique de chaque paramètre un paramètre obligatoire.

Il existe un cas où Windows PowerShell ne peut pas utiliser le jeu de paramètres par défaut même si un nom de jeu de paramètres par défaut est spécifié. Le runtime Windows PowerShell ne peut pas faire la distinction entre les jeux de paramètres basés uniquement sur le type d’objet. Par exemple, si vous avez un jeu de paramètres qui prend une chaîne comme chemin d’accès de fichier, et un autre jeu qui prend directement un objet **FileInfo** , Windows PowerShell ne peut pas déterminer le jeu de paramètres à utiliser en fonction des valeurs transmises à l’applet de commande, pas plus qu’il n’utilise le jeu de paramètres par défaut. Dans ce cas, même si vous spécifiez un nom de jeu de paramètres par défaut, Windows PowerShell génère un message d’erreur de jeu de paramètres ambigu.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` indique que l’applet de commande peut être utilisée dans une transaction. Lorsque `True` est spécifié, le runtime Windows PowerShell ajoute le `UseTransaction` paramètre à la liste de paramètres de l’applet de commande. `False`, la valeur par défaut, indique que l’applet de commande ne peut pas être utilisée dans une transaction.

## <a name="remarks"></a>Notes

- Ensemble, le verbe et le nom sont utilisés pour identifier votre cmdlet inscrite et pour appeler votre applet de commande dans un script.

- Lorsque l’applet de commande est appelée à partir de la console Windows PowerShell, la commande ressemble à la commande suivante :

**VerbName-NounName**

- Toutes les applets de commande qui modifient des ressources en dehors de Windows PowerShell doivent inclure le `SupportsShouldProcess` mot clé lorsque l’attribut d’applet de commande est déclaré, ce qui permet à l’applet de commande d’appeler la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) avant que l’applet de commande exécute son action. Si l’appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourne `false` , l’action ne doit pas être effectuée. Pour plus d’informations sur les demandes de confirmation générées par l’appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

Les paramètres de l’applet de commande `Confirm` et `WhatIf` sont uniquement disponibles pour les applets de commande qui prennent en charge les appels [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess.

## <a name="example"></a>Exemple

La définition de classe suivante utilise l’attribut d’applet de commande pour identifier la classe .NET Framework pour une applet de commande **« obtenir-proc »** qui récupère des informations sur les processus en cours d’exécution sur l’ordinateur local.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Pour plus d’informations sur l’applet de commande « **obtenir-proc »** , consultez le [didacticiel GetProc](./getproc-tutorial.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
