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
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="f0171-102">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="f0171-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="f0171-103">L’attribut de paramètre identifie une propriété publique de la classe d’applet de commande en tant que paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0171-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0171-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0171-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="f0171-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0171-105">Parameters</span></span>

<span data-ttu-id="f0171-106">`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f0171-107">`True` indique que le paramètre d’applet de commande est requis.</span><span class="sxs-lookup"><span data-stu-id="f0171-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="f0171-108">Si un paramètre obligatoire n’est pas fourni lors de l’appel de l’applet de commande, Windows PowerShell invite l’utilisateur à entrer une valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f0171-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="f0171-109">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f0171-109">The default is `false`.</span></span>

<span data-ttu-id="f0171-110">`ParameterSetName` ([System. String](/dotnet/api/System.String)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="f0171-111">Spécifie le jeu de paramètres auquel appartient ce paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0171-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="f0171-112">Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f0171-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="f0171-113">`Position` ([System. Int32](/dotnet/api/System.Int32)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="f0171-114">Spécifie la position du paramètre dans une commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0171-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="f0171-115">`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f0171-116">`True` indique que le paramètre d’applet de commande prend sa valeur d’un objet Pipeline.</span><span class="sxs-lookup"><span data-stu-id="f0171-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="f0171-117">Spécifiez ce mot clé si l’applet de commande accède à l’objet complet, et pas simplement à une propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f0171-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="f0171-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f0171-118">The default is `false`.</span></span>

<span data-ttu-id="f0171-119">`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f0171-120">`True` indique que le paramètre d’applet de commande prend sa valeur d’une propriété d’un objet de pipeline qui a le même nom ou le même alias que ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="f0171-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="f0171-121">Par exemple, si l’applet de commande a un paramètre `Name` et que l’objet pipeline a également une propriété `Name`, la valeur de la propriété `Name` est assignée au paramètre `Name` de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0171-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="f0171-122">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f0171-122">The default is `false`.</span></span>

<span data-ttu-id="f0171-123">`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f0171-124">`True` indique que le paramètre d’applet de commande accepte tous les arguments restants qui sont passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0171-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="f0171-125">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f0171-125">The default is `false`.</span></span>

<span data-ttu-id="f0171-126">`HelpMessage` paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0171-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="f0171-127">Spécifie une brève description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f0171-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="f0171-128">Windows PowerShell affiche ce message lorsqu’une applet de commande est exécutée et qu’un paramètre obligatoire n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="f0171-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="f0171-129">`HelpMessageBaseName` paramètre nommé facultatif. Spécifie l’emplacement où résident les identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="f0171-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="f0171-130">Par exemple, ce paramètre peut spécifier un assembly de ressource qui contient les messages d’aide que vous souhaitez localiser.</span><span class="sxs-lookup"><span data-stu-id="f0171-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="f0171-131">`HelpMessageResourceId` paramètre nommé facultatif. Spécifie l’identificateur de ressource pour un message d’aide.</span><span class="sxs-lookup"><span data-stu-id="f0171-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0171-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0171-132">Remarks</span></span>

- <span data-ttu-id="f0171-133">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.</span><span class="sxs-lookup"><span data-stu-id="f0171-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="f0171-134">Une applet de commande peut avoir n’importe quel nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f0171-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="f0171-135">Toutefois, pour une meilleure expérience utilisateur, limitez le nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f0171-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="f0171-136">Les paramètres doivent être déclarés sur des propriétés ou des champs non statiques publics.</span><span class="sxs-lookup"><span data-stu-id="f0171-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="f0171-137">Les paramètres doivent être déclarés sur les propriétés.</span><span class="sxs-lookup"><span data-stu-id="f0171-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="f0171-138">La propriété doit avoir un accesseur Set public et, si le mot clé `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` est spécifié, la propriété doit avoir un accesseur get public.</span><span class="sxs-lookup"><span data-stu-id="f0171-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="f0171-139">Lorsque vous spécifiez des paramètres positionnels, limitez le nombre de paramètres positionnels dans un paramètre défini à une valeur inférieure à 5.</span><span class="sxs-lookup"><span data-stu-id="f0171-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="f0171-140">Les paramètres positionnels ne doivent pas nécessairement être contigus.</span><span class="sxs-lookup"><span data-stu-id="f0171-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="f0171-141">Les positions 5, 100 et 250 fonctionnent de la même façon que les positions 0, 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="f0171-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="f0171-142">Lorsque le mot clé `Position` n’est pas spécifié, le paramètre de l’applet de commande doit être référencé par son nom.</span><span class="sxs-lookup"><span data-stu-id="f0171-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="f0171-143">Lorsque vous utilisez des jeux de paramètres, notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="f0171-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="f0171-144">Chaque jeu de paramètres doit avoir au moins un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="f0171-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="f0171-145">Une bonne conception d’applet de commande indique que ce paramètre unique doit également être obligatoire si possible.</span><span class="sxs-lookup"><span data-stu-id="f0171-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="f0171-146">Si votre applet de commande est conçue pour être exécutée sans paramètres, le paramètre unique ne peut pas être obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f0171-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="f0171-147">Aucun jeu de paramètres ne doit contenir plus d’un paramètre positionnel avec la même position.</span><span class="sxs-lookup"><span data-stu-id="f0171-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="f0171-148">Un seul paramètre d’un jeu de paramètres doit déclarer `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="f0171-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="f0171-149">Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="f0171-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="f0171-150">Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="f0171-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="f0171-151">Pour plus d’informations sur les instructions relatives aux noms de paramètres, consultez [noms des paramètres](standard-cmdlet-parameter-names-and-types.md)de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0171-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="f0171-152">L’attribut Parameter est défini par la classe [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f0171-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0171-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0171-153">See Also</span></span>

[<span data-ttu-id="f0171-154">System. Management. Automation. ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="f0171-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="f0171-155">Noms des paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="f0171-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="f0171-156">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0171-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
