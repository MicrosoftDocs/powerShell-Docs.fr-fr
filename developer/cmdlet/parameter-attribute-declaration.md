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
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="a7eb2-102">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="a7eb2-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="a7eb2-103">L’attribut de paramètre identifie une propriété publique de la classe de l’applet de commande comme un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7eb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7eb2-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="a7eb2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7eb2-105">Parameters</span></span>

<span data-ttu-id="a7eb2-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a7eb2-107">`True` Indique le paramètre d’applet de commande est requis.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="a7eb2-108">Si un paramètre obligatoire n’est pas fourni lorsque l’applet de commande est appelée, Windows PowerShell invite l’utilisateur à une valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="a7eb2-109">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-109">The default is `false`.</span></span>

<span data-ttu-id="a7eb2-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="a7eb2-111">Spécifie que le paramètre défini que ce paramètre d’applet de commande appartient.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="a7eb2-112">Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="a7eb2-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="a7eb2-114">Spécifie la position du paramètre dans une commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="a7eb2-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a7eb2-116">`True` Indique que le paramètre d’applet de commande prend sa valeur à partir d’un objet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="a7eb2-117">Spécifiez ce mot clé si l’applet de commande accède à l’ensemble de l’objet, pas seulement une propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="a7eb2-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-118">The default is `false`.</span></span>

<span data-ttu-id="a7eb2-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a7eb2-120">`True` Indique que le paramètre d’applet de commande prend sa valeur à partir d’une propriété d’un objet de pipeline qui a le même nom ou le même alias comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="a7eb2-121">Par exemple, si l’applet de commande a un `Name` paramètre et l’objet de pipeline possède également un `Name` propriété, la valeur de la `Name` propriété est affectée à la `Name` paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="a7eb2-122">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-122">The default is `false`.</span></span>

<span data-ttu-id="a7eb2-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a7eb2-124">`True` Indique que le paramètre d’applet de commande accepte tous les autres arguments passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="a7eb2-125">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-125">The default is `false`.</span></span>

<span data-ttu-id="a7eb2-126">`HelpMessage` Paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="a7eb2-127">Spécifie une brève description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="a7eb2-128">Windows PowerShell affiche ce message lorsqu’une applet de commande est exécutée et un paramètre obligatoire n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="a7eb2-129">`HelpMessageBaseName` Paramètre nommé facultatif. Spécifie l’emplacement où résident les identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="a7eb2-130">Par exemple, ce paramètre peut spécifier un assembly de ressources qui contient des messages d’aide que vous souhaitez localiser.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="a7eb2-131">`HelpMessageResourceId` Paramètre nommé facultatif. Spécifie l’identificateur de ressource pour un message d’aide.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7eb2-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="a7eb2-132">Remarks</span></span>

- <span data-ttu-id="a7eb2-133">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a7eb2-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="a7eb2-134">Une applet de commande peut avoir n’importe quel nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="a7eb2-135">Toutefois, pour une meilleure expérience utilisateur, limitez le nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="a7eb2-136">Paramètres doivent être déclarés sur les champs non statiques publiques ou des propriétés.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="a7eb2-137">Les paramètres doivent être déclarés sur les propriétés.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="a7eb2-138">La propriété doit avoir un accesseur set public et si le `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` mot clé est spécifié, la propriété doit avoir un accesseur get public.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="a7eb2-139">Lorsque vous spécifiez des paramètres positionnels, limitez le nombre de paramètres positionnels dans un paramètre de la valeur est inférieure à cinq.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="a7eb2-140">Et, les paramètres positionnels n’ont pas à être contiguës.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="a7eb2-141">Positions 5, 100 et 250 fonctionnent de la même comme des positions 0, 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="a7eb2-142">Lorsque le `Position` mot clé n’est pas spécifié, le paramètre d’applet de commande doit être référencé par son nom.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="a7eb2-143">Lorsque vous utilisez des jeux de paramètres, notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="a7eb2-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="a7eb2-144">Chaque jeu de paramètres doit avoir au moins un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="a7eb2-145">Applet de commande bonne conception indique ce paramètre unique doit également être obligatoire si possible.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="a7eb2-146">Si votre applet de commande est conçue pour être exécutée sans paramètre, le paramètre unique ne peut pas être obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="a7eb2-147">Aucun jeu de paramètres ne doit contenir plus d’un paramètre positionnel avec la même position.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="a7eb2-148">Qu’un seul paramètre dans un jeu de paramètres doit déclarer `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="a7eb2-149">Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="a7eb2-150">Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="a7eb2-151">Pour plus d’informations sur les instructions pour les noms de paramètres, consultez [noms de paramètre d’applet de commande](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="a7eb2-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="a7eb2-152">L’attribut de paramètre est définie par le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="a7eb2-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7eb2-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7eb2-153">See Also</span></span>

[<span data-ttu-id="a7eb2-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="a7eb2-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="a7eb2-155">Noms de paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="a7eb2-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="a7eb2-156">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7eb2-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
