---
ms.date: 09/13/2016
ms.topic: reference
title: Jeux de paramètres des applets de commande
description: Jeux de paramètres des applets de commande
ms.openlocfilehash: e84af7faf5b7459d8dbe06847526efe804e2c5e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668284"
---
# <a name="cmdlet-parameter-sets"></a>Ensembles de paramètres d’applet de commande

PowerShell utilise des jeux de paramètres pour vous permettre d’écrire une applet de commande unique qui peut effectuer différentes actions pour différents scénarios. Les jeux de paramètres vous permettent d’exposer des paramètres différents à l’utilisateur. Et pour retourner des informations différentes en fonction des paramètres spécifiés par l’utilisateur.

## <a name="examples-of-parameter-sets"></a>Exemples de jeux de paramètres

Par exemple, l’applet de commande PowerShell `Get-EventLog` retourne des informations différentes selon que l’utilisateur spécifie ou non le paramètre **List** ou **logname** . Si le paramètre **List** est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux, mais pas sur les informations d’événement qu’elles contiennent. Si le paramètre **logname** est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements spécifique. Les paramètres **List** et **logname** identifient deux jeux de paramètres distincts.

## <a name="unique-parameter"></a>Paramètre unique

Chaque jeu de paramètres doit avoir un paramètre unique que le runtime PowerShell utilise pour exposer le jeu de paramètres approprié. Si possible, le paramètre unique doit être un paramètre obligatoire. Lorsqu’un paramètre est obligatoire, l’utilisateur doit spécifier le paramètre, et le runtime PowerShell utilise ce paramètre pour identifier le jeu de paramètres. Le paramètre unique ne peut pas être obligatoire si votre applet de commande est conçue pour s’exécuter sans spécifier de paramètres.

## <a name="multiple-parameter-sets"></a>Jeux de paramètres multiples

Dans l’illustration suivante, la colonne de gauche affiche trois jeux de paramètres valides. Le **paramètre a** est unique pour le premier jeu de paramètres, le **paramètre B** est unique pour le deuxième jeu de paramètres, et le **paramètre C** est unique pour le troisième jeu de paramètres. Dans la colonne de droite, les jeux de paramètres n’ont pas de paramètre unique.

![Illustration des jeux de paramètres](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Spécifications du jeu de paramètres

Les exigences suivantes s’appliquent à tous les jeux de paramètres.

- Chaque jeu de paramètres doit avoir au moins un paramètre unique. Si possible, définissez ce paramètre sur un paramètre obligatoire.

- Un jeu de paramètres qui contient plusieurs paramètres positionnels doit définir des positions uniques pour chaque paramètre. Deux paramètres positionnels ne peuvent pas spécifier la même position.

- Un seul paramètre d’un ensemble peut déclarer le `ValueFromPipeline` mot clé avec la valeur `true` .
  Plusieurs paramètres peuvent définir le `ValueFromPipelineByPropertyName` mot clé avec la valeur `true` .

- Si aucun jeu de paramètres n’est spécifié pour un paramètre, le paramètre appartient à tous les jeux de paramètres.

> [!NOTE]
> Pour une applet de commande ou une fonction, il existe une limite de 32 jeux de paramètres.

## <a name="default-parameter-sets"></a>Jeux de paramètres par défaut

Lorsque plusieurs jeux de paramètres sont définis, vous pouvez utiliser le `DefaultParameterSetName` mot clé de l’attribut d' **applet** de commande pour spécifier le jeu de paramètres par défaut. PowerShell utilise le jeu de paramètres par défaut s’il ne peut pas déterminer le jeu de paramètres à utiliser en fonction des informations fournies par la commande. Pour plus d’informations sur l’attribut d' **applet** de commande, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.

## <a name="declaring-parameter-sets"></a>Déclarer des jeux de paramètres

Pour créer un jeu de paramètres, vous devez spécifier le `ParameterSetName` mot clé lorsque vous déclarez l’attribut de **paramètre** pour chaque paramètre dans le jeu de paramètres. Pour les paramètres appartenant à plusieurs jeux de paramètres, ajoutez un attribut de **paramètre** pour chaque jeu de paramètres. Cet attribut vous permet de définir différemment le paramètre pour chaque jeu de paramètres. Par exemple, vous pouvez définir un paramètre comme obligatoire dans un jeu et facultatif dans un autre. Toutefois, chaque jeu de paramètres doit contenir un paramètre unique. Pour plus d’informations, consultez [déclaration d’attribut de paramètre](parameter-attribute-declaration.md).

Dans l’exemple suivant, le paramètre **username** est le paramètre unique du `Test01` jeu de paramètres, et le paramètre **ComputerName** est le paramètre unique du jeu de `Test02` paramètres. Le paramètre **SharedParam** appartient aux deux ensembles et est obligatoire pour le `Test01` jeu de paramètres, mais facultatif pour le `Test02` jeu de paramètres.

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
