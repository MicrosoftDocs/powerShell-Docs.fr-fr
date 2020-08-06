---
title: Paramètres d’applet de commande | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.openlocfilehash: 98b1d5fd0e7ffbf2d4d161f1bed73fb96a737bd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774760"
---
# <a name="cmdlet-parameters"></a>Paramètres des applets de commande

Les paramètres d’applet de commande fournissent le mécanisme qui permet à une applet de commande d’accepter l’entrée. Les paramètres peuvent accepter l’entrée directement à partir de la ligne de commande, ou à partir d’objets passés à l’applet de commande via le pipeline, les arguments (également appelés *valeurs*) de ces paramètres peuvent spécifier l’entrée que l’applet de commande accepte, comment l’applet de commande doit effectuer ses actions et les données retournées par l’applet de commande au pipeline.

## <a name="in-this-section"></a>Dans cette section

[Déclarer des propriétés en tant que paramètres](./declaring-properties-as-parameters.md) Fournit les informations de base que vous devez comprendre avant de déclarer les paramètres d’une applet de commande.

[Types de paramètres d’applet de](./types-of-cmdlet-parameters.md) commande Décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande.

[Instructions relatives au nom et aux fonctionnalités des applets de](./standard-cmdlet-parameter-names-and-types.md) commande Décrit les noms, le type de données recommandé et les fonctionnalités des paramètres standard.

[Alias de paramètres](./parameter-aliases.md) Décrit les alias que vous pouvez définir pour les paramètres.

[Noms de paramètres communs](./common-parameter-names.md) Cette rubrique décrit les paramètres que Windows PowerShell ajoute aux applets de commande.

[Ensembles de paramètres d’applet](./cmdlet-parameter-sets.md) de commande Explique comment les jeux de paramètres vous permettent d’écrire une applet de commande unique qui peut exécuter différentes actions pour différents scénarios.

[Paramètres dynamiques des applets](./cmdlet-dynamic-parameters.md) de commande Décrit les paramètres qui sont disponibles pour l’utilisateur dans des conditions spéciales.

[Prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md) commande Décrit comment fournir une prise en charge des caractères génériques lors de la conception d’une applet de commande qui sera exécutée sur un groupe de ressources.

[Validation](./validating-parameter-input.md) de l’entrée de paramètre Décrit comment Windows PowerShell valide les arguments passés aux paramètres de l’applet de commande.

[Paramètres de filtre d’entrée](./input-filter-parameters.md) Décrit les `Filter` paramètres, `Include` et `Exclude` qui filtrent le jeu d’objets d’entrée que l’applet de commande affecte.

## <a name="related-sections"></a>Sections connexes

[Guide pratique pour valider l’entrée des paramètres](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Voir aussi

[Déclaration de l’attribut Parameter](./parameter-attribute-declaration.md)

[Applets de commande Windows PowerShell](./cmdlet-overview.md)
