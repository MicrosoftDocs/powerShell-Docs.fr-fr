---
title: Paramètres d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365928"
---
# <a name="cmdlet-parameters"></a>Paramètres des applets de commande

Les paramètres d’applet de commande fournissent le mécanisme qui permet à une applet de commande d’accepter l’entrée. Les paramètres peuvent accepter l’entrée directement à partir de la ligne de commande, ou à partir d’objets passés à l’applet de commande via le pipeline, les arguments (également appelés *valeurs*) de ces paramètres peuvent spécifier l’entrée que l’applet de commande accepte, comment l’applet de commande doit effectuer ses actions et les données retournées par l’applet de commande au pipeline.

## <a name="in-this-section"></a>Dans cette section

[Déclarer des propriétés en tant que paramètres](./declaring-properties-as-parameters.md) Fournit les informations de base que vous devez comprendre avant de déclarer les paramètres d’une applet de commande.

[Types de paramètres d’applet de](./types-of-cmdlet-parameters.md) commande Décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande.

[Instructions relatives au nom et aux fonctionnalités des applets de](./standard-cmdlet-parameter-names-and-types.md) commande Étudiez les noms, le type de données recommandé et les fonctionnalités des paramètres standard.

[Alias de paramètres](./parameter-aliases.md) Décrit les alias que vous pouvez définir pour les paramètres.

[Noms de paramètres communs](./common-parameter-names.md) Cette rubrique décrit les paramètres que Windows PowerShell ajoute aux applets de commande.

[Ensembles de paramètres d’applet](./cmdlet-parameter-sets.md) de commande Explique comment les jeux de paramètres vous permettent d’écrire une applet de commande unique qui peut exécuter différentes actions pour différents scénarios.

[Paramètres dynamiques des applets](./cmdlet-dynamic-parameters.md) de commande Décrit les paramètres qui sont disponibles pour l’utilisateur dans des conditions spéciales.

[Prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md) commande Décrit comment fournir une prise en charge des caractères génériques lors de la conception d’une applet de commande qui sera exécutée sur un groupe de ressources.

[Validation](./validating-parameter-input.md) de l’entrée de paramètre Décrit comment Windows PowerShell valide les arguments passés aux paramètres de l’applet de commande.

[Paramètres de filtre d’entrée](./input-filter-parameters.md) Décrit les paramètres `Filter`, `Include`et `Exclude` qui filtrent le jeu d’objets d’entrée que l’applet de commande affecte.

## <a name="related-sections"></a>Sections connexes

[Comment valider une entrée de paramètre](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Voir aussi

[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md)

[Applets de commande Windows PowerShell](./cmdlet-overview.md)
