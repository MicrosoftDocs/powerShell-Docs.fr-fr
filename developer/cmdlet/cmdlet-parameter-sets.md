---
title: Jeux de paramètres de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857265"
---
# <a name="cmdlet-parameter-sets"></a>Jeux de paramètres des applets de commande

Windows PowerShell utilise des jeux de paramètres pour vous permettre d’écrire une seule applet de commande qui peut effectuer des actions différentes pour différents scénarios. Jeux de paramètres permettent d’exposer des paramètres différents pour l’utilisateur et pour retourner des informations différentes en fonction des paramètres spécifiés par l’utilisateur.

## <a name="examples-of-parameter-sets"></a>Exemples de jeux de paramètres

Par exemple, le `Get-EventLog` applet de commande (fourni par Windows PowerShell) renvoie des informations différentes selon que l’utilisateur spécifie le `List` ou `LogName` paramètre. Si le `List` paramètre est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux eux-mêmes, mais pas les informations d’événements qu’ils contiennent. Si le `LogName` paramètre est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements spécifique. Le `List` et `LogName` paramètres identifient deux jeux de paramètres distincts.

## <a name="unique-parameter"></a>Paramètre unique

Chaque jeu de paramètres doit avoir un paramètre unique que le runtime Windows PowerShell peut utiliser pour exposer le jeu de paramètres approprié. Si possible, le paramètre unique doit être un paramètre obligatoire. Lorsqu’un paramètre est obligatoire, l’utilisateur est obligé de spécifier le paramètre, et le runtime de Windows PowerShell peut utiliser ce paramètre pour identifier le paramètre défini à utiliser. Le paramètre unique ne peut pas être obligatoire si votre applet de commande est conçue pour être exécutée sans spécifier de paramètres.

## <a name="multiple-parameter-sets"></a>Plusieurs jeux de paramètres

Dans l’illustration suivante, la colonne de gauche montre trois jeux de paramètres valide. Le paramètre A est unique pour le premier jeu de paramètres, paramètre B est unique pour le deuxième jeu de paramètres, et paramètre C est unique pour le troisième jeu de paramètres. Toutefois, dans la colonne de droite, les jeux de paramètres n’ont pas d’un paramètre unique.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Jeu de paramètres requis

Les conditions suivantes s’appliquent à tous les jeux de paramètres.

- Chaque jeu de paramètres doit avoir au moins un paramètre unique. Si possible, vérifiez ce paramètre pour un paramètre obligatoire.

- Un jeu de paramètres qui contient plusieurs paramètres positionnels doit définir des positions uniques pour chaque paramètre. Aucun deux paramètres positionnels ne peuvent spécifier la même position.

- Qu’un seul paramètre dans un jeu peut déclarer la `ValueFromPipeline` mot clé avec la valeur `true`. Plusieurs paramètres peuvent définir le `ValueFromPipelineByPropertyName` mot clé avec la valeur `true`.

- Si aucun jeu de paramètres n’est spécifié pour un paramètre, le paramètre appartient à tous les jeux de paramètres.

## <a name="default-parameter-sets"></a>Jeux de paramètres par défaut

Lorsque plusieurs jeux de paramètres est définis, vous pouvez utiliser le `DefaultParameterSetName` mot clé de l’attribut de l’applet de commande pour spécifier le jeu de paramètres par défaut. Windows PowerShell utilise le paramètre par défaut défini s’il ne peut pas déterminer le paramètre défini pour utiliser basé sur les informations fournies par la commande. Pour plus d’informations sur l’attribut de l’applet de commande, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Déclarer des jeux de paramètres

Pour créer un jeu de paramètres, vous devez spécifier le `ParameterSetName` mot clé lorsque vous déclarez l’attribut de paramètre pour chaque paramètre dans le jeu de paramètres. Pour les paramètres qui appartiennent à plusieurs jeux de paramètres, ajoutez un attribut de paramètre pour chaque jeu de paramètres. Cela vous permet de définir le paramètre différemment pour chaque jeu de paramètres. Par exemple, vous pouvez définir un paramètre comme obligatoires dans un jeu et facultatifs dans une autre. Toutefois, chaque jeu de paramètres doit contenir un paramètre unique.

Dans l’exemple suivant, le `UserName` paramètre est le paramètre unique de l’ensemble de paramètres Test01 et le `ComputerName` paramètre est le paramètre unique de l’ensemble de paramètres Test02. Le `SharedParam` appartient aux deux ensembles de paramètre et est obligatoire pour le paramètre de Test01 défini mais facultatif pour le jeu de paramètres Test02.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
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
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```