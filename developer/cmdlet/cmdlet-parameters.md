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
# <a name="cmdlet-parameters"></a><span data-ttu-id="b0c20-102">Paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="b0c20-102">Cmdlet Parameters</span></span>

<span data-ttu-id="b0c20-103">Paramètres de l’applet de commande fournissent un mécanisme qui permet à une applet de commande d’accepter l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b0c20-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="b0c20-104">Paramètres peuvent accepter l’entrée directement à partir de la ligne de commande, ou à partir d’objets passés à l’applet de commande via le pipeline, les arguments (également appelé *valeurs*) de ces paramètres peut spécifier l’entrée acceptant l’applet de commande, comment la applet de commande doit exécuter ses actions et les données de l’applet de commande retourne au pipeline.</span><span class="sxs-lookup"><span data-stu-id="b0c20-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b0c20-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b0c20-105">In This Section</span></span>

<span data-ttu-id="b0c20-106">[Déclarer des propriétés en tant que paramètres](./declaring-properties-as-parameters.md) fournit des informations de base vous devez comprendre avant de déclarer les paramètres d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0c20-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="b0c20-107">[Types de paramètres de l’applet de commande](./types-of-cmdlet-parameters.md) décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="b0c20-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="b0c20-108">[Nom de paramètre d’applet de commande et des instructions de la fonctionnalité](./standard-cmdlet-parameter-names-and-types.md) étudiez les noms, recommandé de type de données et la fonctionnalité des paramètres standards.</span><span class="sxs-lookup"><span data-stu-id="b0c20-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="b0c20-109">[Alias de paramètre](./parameter-aliases.md) traite les alias que vous pouvez définir des paramètres.</span><span class="sxs-lookup"><span data-stu-id="b0c20-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="b0c20-110">[Les noms de paramètres courants](./common-parameter-names.md) cette rubrique décrit les paramètres Windows PowerShell ajoute aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="b0c20-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="b0c20-111">[Définit des paramètres d’applet de commande](./cmdlet-parameter-sets.md) explique comment les jeux de paramètres vous permettent d’écrire une seule applet de commande qui peut effectuer des actions différentes pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="b0c20-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="b0c20-112">[Applet de commande des paramètres dynamiques](./cmdlet-dynamic-parameters.md) décrit les paramètres qui sont disponibles à l’utilisateur sous conditions spéciales.</span><span class="sxs-lookup"><span data-stu-id="b0c20-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="b0c20-113">[Prise en charge des caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md) explique comment assurer la prise en charge des caractères génériques lorsque vous concevez une applet de commande qui est exécutée par rapport à un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="b0c20-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="b0c20-114">[Validation des entrées de paramètre](./validating-parameter-input.md) décrit comment Windows PowerShell valide les arguments passés aux paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0c20-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="b0c20-115">[Paramètres de filtre d’entrée](./input-filter-parameters.md) présente le `Filter`, `Include`, et `Exclude` paramètres qui filtrent l’ensemble des objets d’entrée qui affecte l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0c20-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b0c20-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="b0c20-116">Related Sections</span></span>

[<span data-ttu-id="b0c20-117">Comment valider l’entrée de paramètre</span><span class="sxs-lookup"><span data-stu-id="b0c20-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="b0c20-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0c20-118">See Also</span></span>

[<span data-ttu-id="b0c20-119">Déclaration d’attribut de paramètre</span><span class="sxs-lookup"><span data-stu-id="b0c20-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="b0c20-120">Applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0c20-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
