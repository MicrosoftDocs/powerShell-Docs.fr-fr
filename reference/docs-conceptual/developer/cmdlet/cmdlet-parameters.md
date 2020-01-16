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
ms.openlocfilehash: c1d8984f4aad7bae6f9be66a2222e2c74c8afa3d
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022213"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="cef73-102">Paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="cef73-102">Cmdlet Parameters</span></span>

<span data-ttu-id="cef73-103">Les paramètres d’applet de commande fournissent le mécanisme qui permet à une applet de commande d’accepter l’entrée.</span><span class="sxs-lookup"><span data-stu-id="cef73-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="cef73-104">Les paramètres peuvent accepter l’entrée directement à partir de la ligne de commande, ou à partir d’objets passés à l’applet de commande via le pipeline, les arguments (également appelés *valeurs*) de ces paramètres peuvent spécifier l’entrée que l’applet de commande accepte, comment l’applet de commande doit effectuer ses actions et les données retournées par l’applet de commande au pipeline.</span><span class="sxs-lookup"><span data-stu-id="cef73-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cef73-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cef73-105">In This Section</span></span>

<span data-ttu-id="cef73-106">[Déclarer des propriétés en tant que paramètres](./declaring-properties-as-parameters.md) Fournit les informations de base que vous devez comprendre avant de déclarer les paramètres d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cef73-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="cef73-107">[Types de paramètres d’applet de](./types-of-cmdlet-parameters.md) commande Décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="cef73-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="cef73-108">[Instructions relatives au nom et aux fonctionnalités des applets de](./standard-cmdlet-parameter-names-and-types.md) commande Décrit les noms, le type de données recommandé et les fonctionnalités des paramètres standard.</span><span class="sxs-lookup"><span data-stu-id="cef73-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="cef73-109">[Alias de paramètres](./parameter-aliases.md) Décrit les alias que vous pouvez définir pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="cef73-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="cef73-110">[Noms de paramètres communs](./common-parameter-names.md) Cette rubrique décrit les paramètres que Windows PowerShell ajoute aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="cef73-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="cef73-111">[Ensembles de paramètres d’applet](./cmdlet-parameter-sets.md) de commande Explique comment les jeux de paramètres vous permettent d’écrire une applet de commande unique qui peut exécuter différentes actions pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="cef73-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="cef73-112">[Paramètres dynamiques des applets](./cmdlet-dynamic-parameters.md) de commande Décrit les paramètres qui sont disponibles pour l’utilisateur dans des conditions spéciales.</span><span class="sxs-lookup"><span data-stu-id="cef73-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="cef73-113">[Prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md) commande Décrit comment fournir une prise en charge des caractères génériques lors de la conception d’une applet de commande qui sera exécutée sur un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="cef73-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="cef73-114">[Validation](./validating-parameter-input.md) de l’entrée de paramètre Décrit comment Windows PowerShell valide les arguments passés aux paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cef73-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="cef73-115">[Paramètres de filtre d’entrée](./input-filter-parameters.md) Décrit les paramètres `Filter`, `Include`et `Exclude` qui filtrent le jeu d’objets d’entrée que l’applet de commande affecte.</span><span class="sxs-lookup"><span data-stu-id="cef73-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="cef73-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="cef73-116">Related Sections</span></span>

[<span data-ttu-id="cef73-117">Comment valider une entrée de paramètre</span><span class="sxs-lookup"><span data-stu-id="cef73-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="cef73-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cef73-118">See Also</span></span>

[<span data-ttu-id="cef73-119">Déclaration d’attribut de paramètre</span><span class="sxs-lookup"><span data-stu-id="cef73-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="cef73-120">Applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cef73-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
