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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735140"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="0a5de-102">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="0a5de-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="0a5de-103">L’attribut de paramètre identifie une propriété publique de la classe de l’applet de commande comme un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a5de-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a5de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a5de-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="0a5de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a5de-105">Parameters</span></span>

<span data-ttu-id="0a5de-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="0a5de-107">`True` Indique le paramètre d’applet de commande est requis.</span><span class="sxs-lookup"><span data-stu-id="0a5de-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="0a5de-108">Si un paramètre obligatoire n’est pas fourni lorsque l’applet de commande est appelée, Windows PowerShell invite l’utilisateur à une valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0a5de-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="0a5de-109">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-109">The default is `false`.</span></span>

<span data-ttu-id="0a5de-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="0a5de-111">Spécifie que le paramètre défini que ce paramètre d’applet de commande appartient.</span><span class="sxs-lookup"><span data-stu-id="0a5de-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="0a5de-112">Si aucun jeu de paramètres n’est spécifié, le paramètre appartient à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a5de-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="0a5de-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="0a5de-114">Spécifie la position du paramètre dans une commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a5de-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="0a5de-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="0a5de-116">`True` Indique que le paramètre d’applet de commande prend sa valeur à partir d’un objet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="0a5de-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="0a5de-117">Spécifiez ce mot clé si l’applet de commande accède à l’ensemble de l’objet, pas seulement une propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0a5de-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="0a5de-118">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-118">The default is `false`.</span></span>

<span data-ttu-id="0a5de-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="0a5de-120">`True` Indique que le paramètre d’applet de commande prend sa valeur à partir d’une propriété d’un objet de pipeline qui a le même nom ou le même alias comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="0a5de-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="0a5de-121">Par exemple, si l’applet de commande a un `Name` paramètre et l’objet de pipeline possède également un `Name` propriété, la valeur de la `Name` propriété est affectée à la `Name` paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a5de-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="0a5de-122">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-122">The default is `false`.</span></span>

<span data-ttu-id="0a5de-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="0a5de-124">`True` Indique que le paramètre d’applet de commande accepte tous les autres arguments passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a5de-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="0a5de-125">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-125">The default is `false`.</span></span>

<span data-ttu-id="0a5de-126">`HelpMessage` Paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a5de-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="0a5de-127">Spécifie une brève description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="0a5de-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="0a5de-128">Windows PowerShell affiche ce message lorsqu’une applet de commande est exécutée et un paramètre obligatoire n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="0a5de-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="0a5de-129">`HelpMessageBaseName` Paramètre nommé facultatif. Spécifie l’emplacement où résident les identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="0a5de-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="0a5de-130">Par exemple, ce paramètre peut spécifier un assembly de ressources qui contient des messages d’aide que vous souhaitez localiser.</span><span class="sxs-lookup"><span data-stu-id="0a5de-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="0a5de-131">`HelpMessageResourceId` Paramètre nommé facultatif. Spécifie l’identificateur de ressource pour un message d’aide.</span><span class="sxs-lookup"><span data-stu-id="0a5de-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a5de-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="0a5de-132">Remarks</span></span>

- <span data-ttu-id="0a5de-133">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0a5de-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="0a5de-134">Une applet de commande peut avoir n’importe quel nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a5de-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="0a5de-135">Toutefois, pour une meilleure expérience utilisateur, limitez le nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a5de-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="0a5de-136">Paramètres doivent être déclarés sur les champs non statiques publiques ou des propriétés.</span><span class="sxs-lookup"><span data-stu-id="0a5de-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="0a5de-137">Les paramètres doivent être déclarés sur les propriétés.</span><span class="sxs-lookup"><span data-stu-id="0a5de-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="0a5de-138">La propriété doit avoir un accesseur set public et si le `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` mot clé est spécifié, la propriété doit avoir un accesseur get public.</span><span class="sxs-lookup"><span data-stu-id="0a5de-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="0a5de-139">Lorsque vous spécifiez des paramètres positionnels, limitez le nombre de paramètres positionnels dans un paramètre de la valeur est inférieure à cinq.</span><span class="sxs-lookup"><span data-stu-id="0a5de-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="0a5de-140">Et, les paramètres positionnels n’ont pas à être contiguës.</span><span class="sxs-lookup"><span data-stu-id="0a5de-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="0a5de-141">Positions 5, 100 et 250 fonctionnent de la même comme des positions 0, 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="0a5de-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="0a5de-142">Lorsque le `Position` mot clé n’est pas spécifié, le paramètre d’applet de commande doit être référencé par son nom.</span><span class="sxs-lookup"><span data-stu-id="0a5de-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="0a5de-143">Lorsque vous utilisez des jeux de paramètres, notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="0a5de-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="0a5de-144">Chaque jeu de paramètres doit avoir au moins un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="0a5de-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="0a5de-145">Applet de commande bonne conception indique ce paramètre unique doit également être obligatoire si possible.</span><span class="sxs-lookup"><span data-stu-id="0a5de-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="0a5de-146">Si votre applet de commande est conçue pour être exécutée sans paramètre, le paramètre unique ne peut pas être obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0a5de-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="0a5de-147">Aucun jeu de paramètres ne doit contenir plus d’un paramètre positionnel avec la même position.</span><span class="sxs-lookup"><span data-stu-id="0a5de-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="0a5de-148">Qu’un seul paramètre dans un jeu de paramètres doit déclarer `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="0a5de-149">Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="0a5de-150">Plusieurs paramètres peuvent définir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="0a5de-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="0a5de-151">Pour plus d’informations sur les instructions pour les noms de paramètres, consultez [noms de paramètre d’applet de commande](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a5de-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="0a5de-152">L’attribut de paramètre est définie par le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="0a5de-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a5de-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a5de-153">See Also</span></span>

[<span data-ttu-id="0a5de-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="0a5de-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="0a5de-155">Noms de paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a5de-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="0a5de-156">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a5de-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
