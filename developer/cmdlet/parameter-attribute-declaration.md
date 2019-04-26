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
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067550"
---
# <a name="parameter-attribute-declaration"></a>Déclaration de l’attribut Parameter

L’attribut de paramètre identifie une propriété publique de la classe de l’applet de commande comme un paramètre d’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Paramètres

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` Indique le paramètre d’applet de commande est requis. Si un paramètre obligatoire n’est pas fourni lorsque l’applet de commande est appelée, Windows PowerShell invite l’utilisateur à une valeur de paramètre. La valeur par défaut est `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) paramètre nommé facultatif. Spécifie que le paramètre défini que ce paramètre d’applet de commande appartient. Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres.

`Position` ([System.Integer](/dotnet/api/System.Integer)) paramètre nommé facultatif. Spécifie la position du paramètre dans une commande Windows PowerShell.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` Indique que le paramètre d’applet de commande prend sa valeur à partir d’un objet de pipeline. Spécifiez ce mot clé si l’applet de commande accède à l’ensemble de l’objet, pas seulement une propriété de l’objet. La valeur par défaut est `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` Indique que le paramètre d’applet de commande prend sa valeur à partir d’une propriété d’un objet de pipeline qui a le même nom ou le même alias comme paramètre. Par exemple, si l’applet de commande a un `Name` paramètre et l’objet de pipeline possède également un `Name` propriété, la valeur de la `Name` propriété est affectée à la `Name` paramètre de l’applet de commande. La valeur par défaut est `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. `True` Indique que le paramètre d’applet de commande accepte tous les autres arguments passés à l’applet de commande. La valeur par défaut est `false`.

`HelpMessage` Paramètre nommé facultatif. Spécifie une brève description du paramètre. Windows PowerShell affiche ce message lorsqu’une applet de commande est exécutée et un paramètre obligatoire n’est pas spécifié.

`HelpMessageBaseName` Paramètre nommé facultatif. Spécifie l’emplacement où résident les identificateurs de ressource. Par exemple, ce paramètre peut spécifier un assembly de ressources qui contient des messages d’aide que vous souhaitez localiser.

`HelpMessageResourceId` Paramètre nommé facultatif. Spécifie l’identificateur de ressource pour un message d’aide.

## <a name="remarks"></a>Remarques

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md).

- Une applet de commande peut avoir n’importe quel nombre de paramètres. Toutefois, pour une meilleure expérience utilisateur, limitez le nombre de paramètres.

- Paramètres doivent être déclarés sur les champs non statiques publiques ou des propriétés. Les paramètres doivent être déclarés sur les propriétés. La propriété doit avoir un accesseur set public et si le `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` mot clé est spécifié, la propriété doit avoir un accesseur get public.

- Lorsque vous spécifiez des paramètres positionnels, limitez le nombre de paramètres positionnels dans un paramètre de la valeur est inférieure à cinq. Et, les paramètres positionnels n’ont pas à être contiguës. Positions 5, 100 et 250 fonctionnent de la même comme des positions 0, 1 et 2.

- Lorsque le `Position` mot clé n’est pas spécifié, le paramètre d’applet de commande doit être référencé par son nom.

- Lorsque vous utilisez des jeux de paramètres, notez les points suivants :

    - Chaque jeu de paramètres doit avoir au moins un paramètre unique. Applet de commande bonne conception indique ce paramètre unique doit également être obligatoire si possible. Si votre applet de commande est conçue pour être exécutée sans paramètre, le paramètre unique ne peut pas être obligatoire.

    - Aucun jeu de paramètres ne doit contenir plus d’un paramètre positionnel avec la même position.

    - Qu’un seul paramètre dans un jeu de paramètres doit déclarer `ValueFromPipeline = true`. Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.

    - Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.

- Pour plus d’informations sur les instructions pour les noms de paramètres, consultez [noms de paramètre d’applet de commande](standard-cmdlet-parameter-names-and-types.md).

- L’attribut de paramètre est définie par le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Noms de paramètres de l’applet de commande](standard-cmdlet-parameter-names-and-types.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
