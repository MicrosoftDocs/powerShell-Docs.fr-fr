---
description: Décrit comment utiliser les paramètres de commande dans PowerShell.
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595515"
---
# <a name="about-parameters"></a><span data-ttu-id="4e259-103">À propos des paramètres</span><span class="sxs-lookup"><span data-stu-id="4e259-103">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="4e259-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="4e259-104">Short description</span></span>
<span data-ttu-id="4e259-105">Décrit comment utiliser les paramètres de commande dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e259-105">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4e259-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="4e259-106">Long description</span></span>

<span data-ttu-id="4e259-107">La plupart des commandes PowerShell, telles que les applets de commande, les fonctions et les scripts, s’appuient sur des paramètres pour permettre aux utilisateurs de sélectionner des options ou de fournir une entrée.</span><span class="sxs-lookup"><span data-stu-id="4e259-107">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="4e259-108">Les paramètres suivent le nom de la commande et se présentent sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="4e259-108">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="4e259-109">Le nom du paramètre est précédé d’un trait d’Union (-), qui signale à PowerShell que le mot qui suit le trait d’Union est un nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-109">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="4e259-110">Le nom et la valeur du paramètre peuvent être séparés par un espace ou un signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="4e259-110">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="4e259-111">Certains paramètres ne nécessitent pas ou n’acceptent pas une valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-111">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="4e259-112">D’autres paramètres requièrent une valeur, mais ne requièrent pas le nom du paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-112">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="4e259-113">Le type de paramètres et la configuration requise pour ces paramètres varient.</span><span class="sxs-lookup"><span data-stu-id="4e259-113">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="4e259-114">Pour rechercher des informations sur les paramètres d’une commande, utilisez l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4e259-114">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4e259-115">Par exemple, pour rechercher des informations sur les paramètres de l’applet de commande `Get-ChildItem` , tapez :</span><span class="sxs-lookup"><span data-stu-id="4e259-115">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="4e259-116">Pour rechercher des informations sur les paramètres d’un script, utilisez le chemin d’accès complet au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="4e259-116">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="4e259-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4e259-117">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="4e259-118">L' `Get-Help` applet de commande retourne divers détails sur la commande, y compris une description, la syntaxe de la commande, des informations sur les paramètres et des exemples montrant comment utiliser les paramètres dans une commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-118">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="4e259-119">Vous pouvez également utiliser le paramètre parameter de l' `Get-Help` applet de commande pour rechercher des informations sur un paramètre particulier.</span><span class="sxs-lookup"><span data-stu-id="4e259-119">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="4e259-120">Ou bien, vous pouvez utiliser le paramètre de **paramètre** avec la valeur de caractère générique ( `*` ) pour rechercher des informations sur tous les paramètres de la commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-120">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="4e259-121">Par exemple, la commande suivante obtient des informations sur tous les paramètres de l’applet de commande `Get-Member` :</span><span class="sxs-lookup"><span data-stu-id="4e259-121">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="4e259-122">Valeurs de paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="4e259-122">Default parameter values</span></span>

<span data-ttu-id="4e259-123">Les paramètres facultatifs ont une valeur par défaut, qui est la valeur utilisée ou supposée lorsque le paramètre n’est pas spécifié dans la commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-123">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="4e259-124">Par exemple, la valeur par défaut du paramètre **ComputerName** de nombreuses applets de commande est le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4e259-124">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="4e259-125">Par conséquent, le nom de l’ordinateur local est utilisé dans la commande, sauf si le paramètre **ComputerName** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="4e259-125">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="4e259-126">Pour rechercher la valeur de paramètre par défaut, consultez la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-126">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="4e259-127">La description du paramètre doit inclure la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e259-127">The parameter description should include the default value.</span></span>

<span data-ttu-id="4e259-128">Vous pouvez également définir une valeur par défaut personnalisée pour n’importe quel paramètre d’une applet de commande ou d’une fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="4e259-128">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="4e259-129">Pour plus d’informations sur la définition des valeurs par défaut personnalisées, consultez [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span><span class="sxs-lookup"><span data-stu-id="4e259-129">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="4e259-130">Table d’attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="4e259-130">Parameter attribute table</span></span>

<span data-ttu-id="4e259-131">Lorsque vous utilisez les paramètres **complet**, **Parameter** ou **Online** de l’applet de commande `Get-Help` , `Get-Help` affiche une table d’attributs de paramètre avec des informations détaillées sur le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-131">When you use the **Full**, **Parameter**, or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="4e259-132">Ces informations comprennent les détails que vous devez connaître pour utiliser le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-132">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="4e259-133">Par exemple, la rubrique d’aide de l' `Get-ChildItem` applet de commande contient les détails suivants sur son paramètre Path :</span><span class="sxs-lookup"><span data-stu-id="4e259-133">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

<span data-ttu-id="4e259-134">Les informations sur les paramètres incluent la syntaxe du paramètre, une description du paramètre et les attributs du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-134">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="4e259-135">Les sections suivantes décrivent les attributs du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-135">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="4e259-136">Paramètre requis</span><span class="sxs-lookup"><span data-stu-id="4e259-136">Parameter Required</span></span>

<span data-ttu-id="4e259-137">Ce paramètre indique si le paramètre est obligatoire, c’est-à-dire si toutes les commandes qui utilisent cette applet de commande doivent inclure ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-137">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="4e259-138">Lorsque la valeur est **true** et que le paramètre est manquant dans la commande, PowerShell vous invite à entrer une valeur pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-138">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="4e259-139">Position du paramètre</span><span class="sxs-lookup"><span data-stu-id="4e259-139">Parameter Position</span></span>

<span data-ttu-id="4e259-140">Si le `Position` paramètre est défini sur un entier positif, le nom du paramètre n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4e259-140">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="4e259-141">Ce type de paramètre est appelé un paramètre positionnel et le nombre indique la position dans laquelle le paramètre doit apparaître par rapport à d’autres paramètres positionnels.</span><span class="sxs-lookup"><span data-stu-id="4e259-141">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="4e259-142">Un paramètre nommé peut figurer dans n’importe quelle position après le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-142">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="4e259-143">Si vous incluez le nom de paramètre pour un paramètre positionnel, le paramètre peut être listé dans n’importe quelle position après le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-143">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="4e259-144">Par exemple, l' `Get-ChildItem` applet de commande a des paramètres Path et Exclude.</span><span class="sxs-lookup"><span data-stu-id="4e259-144">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="4e259-145">Le `Position` paramètre **path** a la valeur **0**, ce qui signifie qu’il s’agit d’un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="4e259-145">The `Position` setting for **Path** is **0**, which means that it is a positional parameter.</span></span> <span data-ttu-id="4e259-146">Le `Position` paramètre de l’option **exclure** est **nommé**.</span><span class="sxs-lookup"><span data-stu-id="4e259-146">The `Position` setting for **Exclude** is **named**.</span></span>

<span data-ttu-id="4e259-147">Cela signifie que le **chemin d’accès** n’a pas besoin du nom du paramètre, mais que sa valeur de paramètre doit être la première ou la seule valeur de paramètre sans nom dans la commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-147">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="4e259-148">Toutefois, étant donné que le paramètre Exclude est un paramètre nommé, vous pouvez le placer dans n’importe quelle position de la commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-148">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="4e259-149">À la suite des `Position` paramètres de ces deux paramètres, vous pouvez utiliser l’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4e259-149">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="4e259-150">Si vous deviez inclure un autre paramètre positionnel sans inclure le nom du paramètre, ce paramètre doit être placé dans l’ordre spécifié par le `Position` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-150">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="4e259-151">Type de paramètre</span><span class="sxs-lookup"><span data-stu-id="4e259-151">Parameter Type</span></span>

<span data-ttu-id="4e259-152">Ce paramètre spécifie le type de Microsoft .NET Framework de la valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-152">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="4e259-153">Par exemple, si le type est **Int32**, la valeur du paramètre doit être un entier.</span><span class="sxs-lookup"><span data-stu-id="4e259-153">For example, if the type is **Int32**, the parameter value must be an integer.</span></span> <span data-ttu-id="4e259-154">Si le type est String, la valeur du paramètre doit être une chaîne de caractères.</span><span class="sxs-lookup"><span data-stu-id="4e259-154">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="4e259-155">Si la chaîne contient des espaces, la valeur doit être placée entre guillemets, ou les espaces doivent être précédés du caractère d’échappement (').</span><span class="sxs-lookup"><span data-stu-id="4e259-155">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="4e259-156">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="4e259-156">Default Value</span></span>

<span data-ttu-id="4e259-157">Ce paramètre spécifie la valeur que le paramètre doit supposer si aucune autre valeur n’est fournie.</span><span class="sxs-lookup"><span data-stu-id="4e259-157">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="4e259-158">Par exemple, la valeur par défaut du paramètre Path est souvent le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4e259-158">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="4e259-159">Les paramètres obligatoires n’ont jamais de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e259-159">Required parameters never have a default value.</span></span>
<span data-ttu-id="4e259-160">Pour de nombreux paramètres facultatifs, il n’y a pas de valeur par défaut, car le paramètre n’a aucun effet s’il n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="4e259-160">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="4e259-161">Accepte plusieurs valeurs</span><span class="sxs-lookup"><span data-stu-id="4e259-161">Accepts Multiple Values</span></span>

<span data-ttu-id="4e259-162">Ce paramètre indique si un paramètre accepte plusieurs valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-162">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="4e259-163">Lorsqu’un paramètre accepte plusieurs valeurs, vous pouvez taper une liste séparée par des virgules comme valeur du paramètre dans la commande, ou enregistrer une liste séparée par des virgules (un tableau) dans une variable, puis spécifier la variable comme valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-163">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="4e259-164">Par exemple, le paramètre ServiceName de l' `Get-Service` applet de commande accepte plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="4e259-164">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="4e259-165">Les commandes suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="4e259-165">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="4e259-166">Accepte l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="4e259-166">Accepts Pipeline Input</span></span>

<span data-ttu-id="4e259-167">Ce paramètre indique si vous pouvez utiliser l’opérateur de pipeline ( `|` ) pour envoyer une valeur au paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-167">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

<span data-ttu-id="4e259-168">Lorsqu’un paramètre a la valeur « true (par valeur) », PowerShell tente d’associer toute valeur dirigée à ce paramètre avant de tenter d’autres méthodes pour interpréter la commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-168">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="4e259-169">Par exemple, vous pouvez diriger une valeur vers un paramètre de **nom** uniquement lorsque la valeur a une propriété appelée **Name**.</span><span class="sxs-lookup"><span data-stu-id="4e259-169">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name**.</span></span>

> [!NOTE]
> <span data-ttu-id="4e259-170">Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de **liaison différée** sur le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-170">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="4e259-171">Le bloc **de script de liaison différée** est exécuté automatiquement pendant la **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="4e259-171">The **delay-bind** script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="4e259-172">Le résultat est lié au paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e259-172">The result is bound to the parameter.</span></span> <span data-ttu-id="4e259-173">La liaison différée ne fonctionne **pas** pour les paramètres définis en tant que type `ScriptBlock` ou `System.Object` , le bloc de script est passé **sans** être appelé.</span><span class="sxs-lookup"><span data-stu-id="4e259-173">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="4e259-174">Vous pouvez en savoir plus sur **les blocs de script de liaison différée** ici [about_Script_Blocks. MD](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="4e259-174">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="4e259-175">Accepte les caractères génériques</span><span class="sxs-lookup"><span data-stu-id="4e259-175">Accepts Wildcard Characters</span></span>

<span data-ttu-id="4e259-176">Ce paramètre indique si la valeur du paramètre peut contenir des caractères génériques afin que la valeur du paramètre puisse être mise en correspondance avec plusieurs éléments existants dans le conteneur cible.</span><span class="sxs-lookup"><span data-stu-id="4e259-176">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="4e259-177">Paramètres communs</span><span class="sxs-lookup"><span data-stu-id="4e259-177">Common Parameters</span></span>

<span data-ttu-id="4e259-178">Les paramètres communs sont des paramètres que vous pouvez utiliser avec n’importe quelle applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e259-178">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="4e259-179">Pour plus d’informations sur les paramètres communs, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4e259-179">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e259-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e259-180">See also</span></span>

[<span data-ttu-id="4e259-181">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="4e259-181">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="4e259-182">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="4e259-182">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="4e259-183">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="4e259-183">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="4e259-184">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="4e259-184">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="4e259-185">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="4e259-185">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="4e259-186">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="4e259-186">about_Wildcards</span></span>](about_Wildcards.md)

