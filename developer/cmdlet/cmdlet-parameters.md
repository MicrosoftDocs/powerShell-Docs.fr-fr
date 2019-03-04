---
title: Paramètres de l’applet de commande | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853845"
---
# <a name="cmdlet-parameters"></a>Paramètres des applets de commande

Paramètres de l’applet de commande fournissent un mécanisme qui permet à une applet de commande d’accepter l’entrée. Paramètres peuvent accepter l’entrée directement à partir de la ligne de commande, ou à partir d’objets passés à l’applet de commande via le pipeline, les arguments (également appelé *valeurs*) de ces paramètres peut spécifier l’entrée acceptant l’applet de commande, comment la applet de commande doit exécuter ses actions et les données de l’applet de commande retourne au pipeline.

## <a name="in-this-section"></a>Dans cette section

[Déclarer des propriétés en tant que paramètres](./declaring-properties-as-parameters.md) fournit des informations de base vous devez comprendre avant de déclarer les paramètres d’applet de commande.

[Types de paramètres de l’applet de commande](./types-of-cmdlet-parameters.md) décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande.

[Nom de paramètre d’applet de commande et des instructions de la fonctionnalité](./standard-cmdlet-parameter-names-and-types.md) étudiez les noms, recommandé de type de données et la fonctionnalité des paramètres standards.

[Alias de paramètre](./parameter-aliases.md) traite les alias que vous pouvez définir des paramètres.

[Les noms de paramètres courants](./common-parameter-names.md) cette rubrique décrit les paramètres Windows PowerShell ajoute aux applets de commande.

[Définit des paramètres d’applet de commande](./cmdlet-parameter-sets.md) explique comment les jeux de paramètres vous permettent d’écrire une seule applet de commande qui peut effectuer des actions différentes pour différents scénarios.

[Applet de commande des paramètres dynamiques](./cmdlet-dynamic-parameters.md) décrit les paramètres qui sont disponibles à l’utilisateur sous conditions spéciales.

[Prise en charge des caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md) explique comment assurer la prise en charge des caractères génériques lorsque vous concevez une applet de commande qui est exécutée par rapport à un groupe de ressources.

[Validation des entrées de paramètre](./validating-parameter-input.md) décrit comment Windows PowerShell valide les arguments passés aux paramètres de l’applet de commande.

[Paramètres de filtre d’entrée](./input-filter-parameters.md) présente le `Filter`, `Include`, et `Exclude` paramètres qui filtrent l’ensemble des objets d’entrée qui affecte l’applet de commande.

## <a name="related-sections"></a>Sections connexes

[Comment valider l’entrée de paramètre](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Voir aussi

[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md)

[Applets de commande Windows PowerShell](./cmdlet-overview.md)
