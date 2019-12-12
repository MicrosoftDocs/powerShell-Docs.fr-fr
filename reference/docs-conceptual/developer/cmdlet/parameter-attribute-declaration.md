---
title: Déclaration d’attribut de paramètre | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365358"
---
# <a name="parameter-attribute-declaration"></a>Déclaration de l’attribut Parameter

L’attribut de paramètre identifie une propriété publique de la classe d’applet de commande en tant que paramètre d’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` indique que le paramètre d’applet de commande est requis. Si un paramètre obligatoire n’est pas fourni lors de l’appel de l’applet de commande, Windows PowerShell invite l’utilisateur à entrer une valeur de paramètre. La valeur par défaut est `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) paramètre nommé facultatif. Spécifie le jeu de paramètres auquel appartient ce paramètre d’applet de commande. Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres.

`Position` ([System. Int32](/dotnet/api/System.Int32)) paramètre nommé facultatif. Spécifie la position du paramètre dans une commande Windows PowerShell.

`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` indique que le paramètre d’applet de commande prend sa valeur d’un objet Pipeline. Spécifiez ce mot clé si l’applet de commande accède à l’objet complet, et pas simplement à une propriété de l’objet. La valeur par défaut est `false`.

`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` indique que le paramètre d’applet de commande prend sa valeur d’une propriété d’un objet de pipeline qui a le même nom ou le même alias que ce paramètre. Par exemple, si l’applet de commande a un paramètre `Name` et que l’objet pipeline a également une propriété `Name`, la valeur de la propriété `Name` est assignée au paramètre `Name` de l’applet de commande. La valeur par défaut est `false`.

`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` indique que le paramètre d’applet de commande accepte tous les arguments restants qui sont passés à l’applet de commande. La valeur par défaut est `false`.

`HelpMessage` paramètre nommé facultatif. Spécifie une brève description du paramètre. Windows PowerShell affiche ce message lorsqu’une applet de commande est exécutée et qu’un paramètre obligatoire n’est pas spécifié.

`HelpMessageBaseName` paramètre nommé facultatif. Spécifie l’emplacement où résident les identificateurs de ressource. Par exemple, ce paramètre peut spécifier un assembly de ressource qui contient les messages d’aide que vous souhaitez localiser.

`HelpMessageResourceId` paramètre nommé facultatif. Spécifie l’identificateur de ressource pour un message d’aide.

## <a name="remarks"></a>Remarks

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.

- Une applet de commande peut avoir n’importe quel nombre de paramètres. Toutefois, pour une meilleure expérience utilisateur, limitez le nombre de paramètres.

- Les paramètres doivent être déclarés sur des propriétés ou des champs non statiques publics. Les paramètres doivent être déclarés sur les propriétés. La propriété doit avoir un accesseur Set public et, si le mot clé `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` est spécifié, la propriété doit avoir un accesseur get public.

- Lorsque vous spécifiez des paramètres positionnels, limitez le nombre de paramètres positionnels dans un paramètre défini à une valeur inférieure à 5. Les paramètres positionnels ne doivent pas nécessairement être contigus. Les positions 5, 100 et 250 fonctionnent de la même façon que les positions 0, 1 et 2.

- Lorsque le mot clé `Position` n’est pas spécifié, le paramètre de l’applet de commande doit être référencé par son nom.

- Lorsque vous utilisez des jeux de paramètres, notez les points suivants :

    - Chaque jeu de paramètres doit avoir au moins un paramètre unique. Une bonne conception d’applet de commande indique que ce paramètre unique doit également être obligatoire si possible. Si votre applet de commande est conçue pour être exécutée sans paramètres, le paramètre unique ne peut pas être obligatoire.

    - Aucun jeu de paramètres ne doit contenir plus d’un paramètre positionnel avec la même position.

    - Un seul paramètre d’un jeu de paramètres doit déclarer `ValueFromPipeline = true`. Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.

    - Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.

- Pour plus d’informations sur les instructions relatives aux noms de paramètres, consultez [noms des paramètres](standard-cmdlet-parameter-names-and-types.md)de l’applet de commande.

- L’attribut Parameter est défini par la classe [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Noms des paramètres de l’applet de commande](standard-cmdlet-parameter-names-and-types.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
