---
title: Déclaration d’attribut de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 2bc03aaade1f18d48f65ecf5f9ee437ffaf07f92
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863425"
---
# <a name="cmdlet-attribute-declaration"></a>Déclaration de l’attribut Cmdlet

L’attribut de l’applet de commande identifie une classe Microsoft .NET Framework en tant qu’une applet de commande et spécifie le verbe et substantif, utilisé pour appeler l’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

`VerbName` ([System.String](/dotnet/api/System.String)) requis. Spécifie le verbe de l’applet de commande. Ce verbe Spécifie l’action effectuée par l’applet de commande. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe Cmdlet](./approved-verbs-for-windows-powershell-commands.md) et [directives de développement requis](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) requis. Spécifie le nom de l’applet de commande. Ce nom spécifie la ressource à laquelle l’applet de commande agit. Pour plus d’informations sur les noms d’applet de commande, consultez [déclaration de l’applet de commande](./cmdlet-class-declaration.md) et [fortement encouragés les directives de développement](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` Indique que l’applet de commande prend en charge les appels à la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode), qui fournit un moyen d’inviter l’utilisateur avant l’exécution d’une action qui modifie le système à l’applet de commande. `False`, la valeur par défaut, indique que l’applet de commande ne prend pas en charge les appels à la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). Pour plus d’informations sur les demandes de confirmation, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) paramètre nommé facultatif. Spécifie quand l’action de l’applet de commande doit être confirmée par un appel à la [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sera appelée lorsque la valeur de ConfirmImpact de l’applet de commande (par défaut, les moyennes) est égale ou supérieure à la valeur de la `$ConfirmPreference` variable. Ce paramètre doit être spécifié uniquement lorsque le `SupportsShouldProcess` est précisé.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) paramètre nommé facultatif. Le paramètre par défaut Spécifie que le runtime Windows PowerShell tente d’utiliser lorsqu’il ne peut pas déterminer le jeu de paramètres à utiliser. Notez que cette situation peut être éliminée en rendant le paramètre unique de chaque paramètre à définir un paramètre obligatoire.

Il existe un cas où Windows PowerShell ne peut pas utiliser le paramètre par défaut défini même si un nom de jeu de paramètre par défaut est spécifié. Le runtime Windows PowerShell ne peut pas faire la distinction entre les jeux de paramètres basées uniquement sur le type d’objet. Par exemple, si vous avez un jeu de paramètres qui prend une chaîne en tant que le chemin d’accès de fichier et un autre ensemble qui prend un **FileInfo** objet directement, Windows PowerShell ne peut pas déterminer quel paramètre configuré pour utiliser selon les valeurs passées à la l’applet de commande, et n’utilise pas le jeu de paramètres par défaut. Dans ce cas, même si vous spécifiez un paramètre par défaut nom, Windows PowerShell génère un message d’erreur ambigu paramètre ensemble.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` Indique que l’applet de commande peut être utilisé dans une transaction. Lorsque `True` est spécifié, le runtime Windows PowerShell ajoute le `UseTransaction` paramètre à la liste des paramètres de l’applet de commande. `False`, la valeur par défaut, indique que l’applet de commande ne peut pas être utilisé dans une transaction.

## <a name="remarks"></a>Remarques

- Ensemble, le verbe et substantif servent à identifier votre applet de commande inscrit et pour appeler votre applet de commande au sein d’un script.

- Lors de l’applet de commande est appelée à partir de la console Windows PowerShell, la commande ressemble à la commande suivante :

**VerbName-NounName**

- Toutes les applets de commande qui modifient les ressources en dehors de Windows PowerShell doivent inclure le `SupportsShouldProcess` mot clé lors de l’attribut de l’applet de commande est déclaré, ce qui permet à l’applet de commande appeler le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode avant que l’applet de commande effectue son action. Si le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appeler retourne `false`, l’action ne doit pas être effectuée. Pour plus d’informations sur les demandes de confirmation générées par le [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appeler, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

Le `Confirm` et `WhatIf` paramètres de l’applet de commande sont disponibles uniquement pour les applets de commande qui prennent en charge [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appels.

## <a name="example"></a>Exemple

La définition de classe suivante utilise l’attribut de l’applet de commande pour identifier la classe .NET Framework pour un **Get-Process** applet de commande qui Récupère des informations sur les processus en cours d’exécution sur l’ordinateur local.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Pour plus d’informations sur la **Get-Process** applet de commande, consultez [GetProc didacticiel](./getproc-tutorial.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
