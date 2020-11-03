---
description: Décrit les paramètres qui peuvent être utilisés avec n’importe quelle applet de commande.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: c0e995e4677d235e7f218267162c15d7f1693e06
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207165"
---
# <a name="about-commonparameters"></a><span data-ttu-id="e4718-104">À propos de Paramètres_courants</span><span class="sxs-lookup"><span data-stu-id="e4718-104">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="e4718-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="e4718-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e4718-106">Décrit les paramètres qui peuvent être utilisés avec n’importe quelle applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-106">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="e4718-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="e4718-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e4718-108">Les paramètres communs sont un ensemble de paramètres d’applet de commande que vous pouvez utiliser avec n’importe quelle applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-108">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="e4718-109">Elles sont implémentées par PowerShell, et non par le développeur d’applets de commande, et sont automatiquement disponibles pour n’importe quelle applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-109">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="e4718-110">Vous pouvez utiliser les paramètres communs avec n’importe quelle applet de commande, mais ils peuvent ne pas avoir d’effet sur toutes les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-110">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="e4718-111">Par exemple, si une applet de commande ne génère pas de sortie détaillée, l’utilisation du paramètre commun **Verbose** n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="e4718-111">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="e4718-112">Les paramètres communs sont également disponibles sur les fonctions avancées qui utilisent l’attribut **CmdletBinding** ou l’attribut **Parameter** .</span><span class="sxs-lookup"><span data-stu-id="e4718-112">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="e4718-113">Plusieurs paramètres communs remplacent les valeurs par défaut ou les préférences système que vous définissez à l’aide des variables de préférence PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4718-113">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="e4718-114">Contrairement aux variables de préférence, les paramètres communs affectent uniquement les commandes dans lesquelles ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="e4718-114">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="e4718-115">Pour plus d’informations, consultez [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e4718-115">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="e4718-116">La liste suivante affiche les paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="e4718-116">The following list displays the common parameters.</span></span> <span data-ttu-id="e4718-117">Leurs alias sont répertoriés entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="e4718-117">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="e4718-118">**Debug** (db)</span><span class="sxs-lookup"><span data-stu-id="e4718-118">**Debug** (db)</span></span>
- <span data-ttu-id="e4718-119">**ErrorAction** (EA)</span><span class="sxs-lookup"><span data-stu-id="e4718-119">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="e4718-120">**ErrorVariable** (EV)</span><span class="sxs-lookup"><span data-stu-id="e4718-120">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="e4718-121">**InformationAction** (INFA)</span><span class="sxs-lookup"><span data-stu-id="e4718-121">**InformationAction** (infa)</span></span>
- <span data-ttu-id="e4718-122">**InformationVariable** (IV)</span><span class="sxs-lookup"><span data-stu-id="e4718-122">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="e4718-123">En- **variable** (OV)</span><span class="sxs-lookup"><span data-stu-id="e4718-123">**OutVariable** (ov)</span></span>
- <span data-ttu-id="e4718-124">**Mémoire tampon** (OB)</span><span class="sxs-lookup"><span data-stu-id="e4718-124">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="e4718-125">**PipelineVariable** (PV)</span><span class="sxs-lookup"><span data-stu-id="e4718-125">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="e4718-126">**Verbose** (VB)</span><span class="sxs-lookup"><span data-stu-id="e4718-126">**Verbose** (vb)</span></span>
- <span data-ttu-id="e4718-127">**WarningAction** (WA)</span><span class="sxs-lookup"><span data-stu-id="e4718-127">**WarningAction** (wa)</span></span>
- <span data-ttu-id="e4718-128">**WarningVariable** (WV)</span><span class="sxs-lookup"><span data-stu-id="e4718-128">**WarningVariable** (wv)</span></span>

<span data-ttu-id="e4718-129">Les paramètres d' **action** sont des valeurs de type **PréférenceAction** .</span><span class="sxs-lookup"><span data-stu-id="e4718-129">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="e4718-130">**PréférenceAction** est une énumération avec les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4718-130">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="e4718-131">Nom</span><span class="sxs-lookup"><span data-stu-id="e4718-131">Name</span></span>             | <span data-ttu-id="e4718-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="e4718-132">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="e4718-133">Interrompre</span><span class="sxs-lookup"><span data-stu-id="e4718-133">Suspend</span></span>          | <span data-ttu-id="e4718-134">5</span><span class="sxs-lookup"><span data-stu-id="e4718-134">5</span></span>     |
| <span data-ttu-id="e4718-135">Ignorer</span><span class="sxs-lookup"><span data-stu-id="e4718-135">Ignore</span></span>           | <span data-ttu-id="e4718-136">4</span><span class="sxs-lookup"><span data-stu-id="e4718-136">4</span></span>     |
| <span data-ttu-id="e4718-137">Inquire</span><span class="sxs-lookup"><span data-stu-id="e4718-137">Inquire</span></span>          | <span data-ttu-id="e4718-138">3</span><span class="sxs-lookup"><span data-stu-id="e4718-138">3</span></span>     |
| <span data-ttu-id="e4718-139">Continuer</span><span class="sxs-lookup"><span data-stu-id="e4718-139">Continue</span></span>         | <span data-ttu-id="e4718-140">2</span><span class="sxs-lookup"><span data-stu-id="e4718-140">2</span></span>     |
| <span data-ttu-id="e4718-141">Arrêter</span><span class="sxs-lookup"><span data-stu-id="e4718-141">Stop</span></span>             | <span data-ttu-id="e4718-142">1</span><span class="sxs-lookup"><span data-stu-id="e4718-142">1</span></span>     |
| <span data-ttu-id="e4718-143">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="e4718-143">SilentlyContinue</span></span> | <span data-ttu-id="e4718-144">0</span><span class="sxs-lookup"><span data-stu-id="e4718-144">0</span></span>     |

<span data-ttu-id="e4718-145">Vous pouvez utiliser le nom ou la valeur avec le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e4718-145">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="e4718-146">En plus des paramètres communs, de nombreuses applets de commande offrent des paramètres d’atténuation des risques.</span><span class="sxs-lookup"><span data-stu-id="e4718-146">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="e4718-147">Les applets de commande qui impliquent un risque pour le système ou pour des données utilisateur proposent généralement ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="e4718-147">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="e4718-148">Les paramètres d’atténuation des risques sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="e4718-148">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="e4718-149">**WhatIf** (Wi)</span><span class="sxs-lookup"><span data-stu-id="e4718-149">**WhatIf** (wi)</span></span>
- <span data-ttu-id="e4718-150">**Confirmer** (CF)</span><span class="sxs-lookup"><span data-stu-id="e4718-150">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="e4718-151">DESCRIPTIONS DES PARAMÈTRES COMMUNS</span><span class="sxs-lookup"><span data-stu-id="e4718-151">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="e4718-152">Débogage</span><span class="sxs-lookup"><span data-stu-id="e4718-152">Debug</span></span>

<span data-ttu-id="e4718-153">Affiche des détails au niveau du programmeur sur l’opération effectuée par la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-153">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="e4718-154">Ce paramètre fonctionne uniquement lorsque la commande génère un message de débogage.</span><span class="sxs-lookup"><span data-stu-id="e4718-154">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="e4718-155">Par exemple, ce paramètre fonctionne quand une commande contient l' `Write-Debug` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-155">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-156">Par défaut, les messages de débogage ne s’affichent pas, car la valeur de la `$DebugPreference` variable est **SilentlyContinue** .</span><span class="sxs-lookup"><span data-stu-id="e4718-156">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue** .</span></span>

<span data-ttu-id="e4718-157">En mode interactif, le paramètre de **débogage** remplace la valeur de la `$DebugPreference` variable pour la commande actuelle, en affectant à la valeur `$DebugPreference` **inquire** .</span><span class="sxs-lookup"><span data-stu-id="e4718-157">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire** .</span></span>

<span data-ttu-id="e4718-158">En mode non interactif, le paramètre de **débogage** remplace la valeur de la `$DebugPreference` variable pour la commande actuelle, en affectant la valeur `$DebugPreference` à **continue** .</span><span class="sxs-lookup"><span data-stu-id="e4718-158">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue** .</span></span>

<span data-ttu-id="e4718-159">`-Debug:$true` a le même effet que `-Debug` .</span><span class="sxs-lookup"><span data-stu-id="e4718-159">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="e4718-160">Utilisez `-Debug:$false` pour supprimer l’affichage des messages de débogage lorsque `$DebugPreference` n’est pas **SilentlyContinue** , qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4718-160">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue** , which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="e4718-161">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="e4718-161">ErrorAction</span></span>

<span data-ttu-id="e4718-162">Détermine la façon dont l’applet de commande répond à une erreur sans fin d’achèvement de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-162">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="e4718-163">Ce paramètre fonctionne uniquement lorsque la commande génère une erreur sans fin d’achèvement, telle que celles de l' `Write-Error` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-163">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-164">Le paramètre **ErrorAction** remplace la valeur de la `$ErrorActionPreference` variable pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4718-164">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="e4718-165">Étant donné que la valeur par défaut de la `$ErrorActionPreference` variable est **continue** , les messages d’erreur s’affichent et l’exécution se poursuit, sauf si vous utilisez le paramètre **ErrorAction** .</span><span class="sxs-lookup"><span data-stu-id="e4718-165">Because the default value of the `$ErrorActionPreference` variable is **Continue** , error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="e4718-166">Le paramètre **ErrorAction** n’a aucun effet sur les erreurs de fin (telles que les données manquantes, les paramètres qui ne sont pas valides ou les autorisations insuffisantes) qui empêchent une commande de se terminer correctement.</span><span class="sxs-lookup"><span data-stu-id="e4718-166">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="e4718-167">`-ErrorAction:Continue` Affichez le message d’erreur et poursuivez l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-167">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="e4718-168">`Continue` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4718-168">`Continue` is the default.</span></span>

<span data-ttu-id="e4718-169">`-ErrorAction:Ignore` supprime le message d’erreur et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-169">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="e4718-170">Contrairement à **SilentlyContinue** , **ignore** n’ajoute pas le message d’erreur à la `$Error` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="e4718-170">Unlike **SilentlyContinue** , **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="e4718-171">La valeur **ignorée** est introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e4718-171">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="e4718-172">`-ErrorAction:Inquire` affiche le message d’erreur et vous invite à confirmer avant de poursuivre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4718-172">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="e4718-173">Cette valeur est rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="e4718-173">This value is rarely used.</span></span>

<span data-ttu-id="e4718-174">`-ErrorAction:SilentlyContinue` supprime le message d’erreur et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-174">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="e4718-175">`-ErrorAction:Stop` affiche le message d’erreur et arrête l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-175">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="e4718-176">`-ErrorAction:Suspend` est uniquement disponible pour les flux de travail qui ne sont pas pris en charge dans PowerShell 6 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e4718-176">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="e4718-177">Le paramètre **ErrorAction** substitue, mais ne remplace pas la valeur de la `$ErrorAction` variable de préférence lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="e4718-177">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="e4718-178">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="e4718-178">ErrorVariable</span></span>

<span data-ttu-id="e4718-179">**ErrorVariable** stocke les messages d’erreur relatifs à la commande dans la variable spécifiée et dans la `$Error` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="e4718-179">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="e4718-180">Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="e4718-180">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-181">Par défaut, les nouveaux messages d’erreur remplacent les messages d’erreur qui sont déjà stockés dans la variable.</span><span class="sxs-lookup"><span data-stu-id="e4718-181">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="e4718-182">Pour ajouter le message d’erreur au contenu de la variable, tapez un signe plus ( `+` ) avant le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="e4718-182">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="e4718-183">Par exemple, la commande suivante crée la `$a` variable et y stocke les erreurs :</span><span class="sxs-lookup"><span data-stu-id="e4718-183">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="e4718-184">La commande suivante ajoute tous les messages d’erreur à la `$a` variable :</span><span class="sxs-lookup"><span data-stu-id="e4718-184">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="e4718-185">La commande suivante affiche le contenu de `$a` :</span><span class="sxs-lookup"><span data-stu-id="e4718-185">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="e4718-186">Vous pouvez utiliser ce paramètre pour créer une variable qui contient uniquement des messages d’erreur de commandes spécifiques et n’affecte pas le comportement de la `$Error` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="e4718-186">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="e4718-187">La `$Error` variable automatique contient des messages d’erreur de toutes les commandes de la session.</span><span class="sxs-lookup"><span data-stu-id="e4718-187">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="e4718-188">Vous pouvez utiliser la notation de tableau, telle que `$a[0]` ou, `$error[1,2]` pour faire référence à des erreurs spécifiques stockées dans les variables.</span><span class="sxs-lookup"><span data-stu-id="e4718-188">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="e4718-189">La variable d’erreur personnalisée contient toutes les erreurs générées par la commande, y compris les erreurs des appels à des fonctions ou des scripts imbriqués.</span><span class="sxs-lookup"><span data-stu-id="e4718-189">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="e4718-190">InformationAction</span><span class="sxs-lookup"><span data-stu-id="e4718-190">InformationAction</span></span>

<span data-ttu-id="e4718-191">Introduit dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="e4718-191">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="e4718-192">Dans la commande ou le script dans lequel elle est utilisée, le paramètre commun **InformationAction** remplace la valeur de la `$InformationPreference` variable de préférence, qui est définie par défaut sur **SilentlyContinue** .</span><span class="sxs-lookup"><span data-stu-id="e4718-192">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue** .</span></span> <span data-ttu-id="e4718-193">Lorsque vous utilisez `Write-Information` dans un script avec **InformationAction** , les `Write-Information` valeurs sont affichées en fonction de la valeur du paramètre **InformationAction** .</span><span class="sxs-lookup"><span data-stu-id="e4718-193">When you use `Write-Information` in a script with **InformationAction** , `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="e4718-194">Pour plus d’informations sur `$InformationPreference` , consultez [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e4718-194">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-195">`-InformationAction:Stop` arrête une commande ou un script à une occurrence de la `Write-Information` commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-195">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="e4718-196">`-InformationAction:Ignore` supprime le message d’information et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-196">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="e4718-197">Contrairement à **SilentlyContinue** , **ignore** complètement le message d’information ; elle n’ajoute pas le message d’information au flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="e4718-197">Unlike **SilentlyContinue** , **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="e4718-198">`-InformationAction:Inquire` affiche le message d’information que vous spécifiez dans une `Write-Information` commande, puis vous demande si vous souhaitez continuer.</span><span class="sxs-lookup"><span data-stu-id="e4718-198">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="e4718-199">`-InformationAction:Continue` affiche le message d’information et poursuit son exécution.</span><span class="sxs-lookup"><span data-stu-id="e4718-199">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="e4718-200">`-InformationAction:Suspend` n’est pas pris en charge sur PowerShell Core, car il n’est disponible que pour les flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e4718-200">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="e4718-201">`-InformationAction:SilentlyContinue` aucun effet, car le message d’information n’est pas (valeur par défaut) s’affiche et le script se poursuit sans interruption.</span><span class="sxs-lookup"><span data-stu-id="e4718-201">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="e4718-202">Le paramètre **InformationAction** substitue, mais ne remplace pas la valeur de la `$InformationAction` variable de préférence lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="e4718-202">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="e4718-203">InformationVariable</span><span class="sxs-lookup"><span data-stu-id="e4718-203">InformationVariable</span></span>

<span data-ttu-id="e4718-204">Introduit dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="e4718-204">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="e4718-205">Dans la commande ou le script dans lequel elle est utilisée, le paramètre commun **InformationVariable** stocke dans une variable une chaîne que vous spécifiez en ajoutant la `Write-Information` commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-205">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="e4718-206">`Write-Information` les valeurs sont affichées en fonction de la valeur du paramètre commun **InformationAction** ; Si vous n’ajoutez pas le paramètre commun **InformationAction** , les `Write-Information` chaînes sont affichées en fonction de la valeur de la `$InformationPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="e4718-206">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="e4718-207">Pour plus d’informations sur `$InformationPreference` , consultez [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e4718-207">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e4718-208">La variable d’informations contient tous les messages d’information générés par la commande, y compris les messages d’informations provenant d’appels à des fonctions ou des scripts imbriqués.</span><span class="sxs-lookup"><span data-stu-id="e4718-208">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="e4718-209">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="e4718-209">OutBuffer</span></span>

<span data-ttu-id="e4718-210">Détermine le nombre d’objets à accumuler dans une mémoire tampon avant l’envoi des objets via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="e4718-210">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="e4718-211">Si vous omettez ce paramètre, les objets sont envoyés lorsqu’ils sont générés.</span><span class="sxs-lookup"><span data-stu-id="e4718-211">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-212">Ce paramètre de gestion des ressources est conçu pour les utilisateurs expérimentés.</span><span class="sxs-lookup"><span data-stu-id="e4718-212">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="e4718-213">Lorsque vous utilisez ce paramètre, PowerShell envoie des données à l’applet de commande suivante dans des lots de `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="e4718-213">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="e4718-214">L’exemple suivant montre comment afficher entre `ForEach-Object` les blocs pour traiter les blocs qui utilisent l’applet de commande `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="e4718-214">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="e4718-215">L’affichage alterne dans les lots de 2 ou `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="e4718-215">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a><span data-ttu-id="e4718-216">OutVariable</span><span class="sxs-lookup"><span data-stu-id="e4718-216">OutVariable</span></span>

<span data-ttu-id="e4718-217">Stocke les objets de sortie de la commande dans la variable spécifiée, en plus de l’envoi de la sortie le long du pipeline.</span><span class="sxs-lookup"><span data-stu-id="e4718-217">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-218">Pour ajouter la sortie à la variable, au lieu de remplacer une sortie qui peut déjà y être stockée, tapez un signe plus ( `+` ) avant le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="e4718-218">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="e4718-219">Par exemple, la commande suivante crée la `$out` variable et y stocke l’objet processus :</span><span class="sxs-lookup"><span data-stu-id="e4718-219">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="e4718-220">La commande suivante ajoute l’objet processus à la `$out` variable :</span><span class="sxs-lookup"><span data-stu-id="e4718-220">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="e4718-221">La commande suivante affiche le contenu de la `$out` variable :</span><span class="sxs-lookup"><span data-stu-id="e4718-221">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="e4718-222">La variable créée par le paramètre de la variable de la **variable** est un `[System.Collections.ArrayList]` .</span><span class="sxs-lookup"><span data-stu-id="e4718-222">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="e4718-223">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="e4718-223">PipelineVariable</span></span>

<span data-ttu-id="e4718-224">**PipelineVariable** stocke la valeur de l’élément de pipeline actuel sous la forme d’une variable, pour toute commande nommée à travers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="e4718-224">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-225">Les valeurs valides sont les chaînes, les mêmes que pour les noms de variable.</span><span class="sxs-lookup"><span data-stu-id="e4718-225">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="e4718-226">Voici un exemple de fonctionnement de **PipelineVariable** .</span><span class="sxs-lookup"><span data-stu-id="e4718-226">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="e4718-227">Dans cet exemple, le paramètre **PipelineVariable** est ajouté à une `Foreach-Object` commande pour stocker les résultats de la commande dans les variables.</span><span class="sxs-lookup"><span data-stu-id="e4718-227">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="e4718-228">Une plage de nombres, de 1 à 10, est dirigée vers la première `Foreach-Object` commande, dont les résultats sont stockés dans une variable nommée **Left** .</span><span class="sxs-lookup"><span data-stu-id="e4718-228">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left** .</span></span>

<span data-ttu-id="e4718-229">Les résultats de la première `Foreach-Object` commande sont dirigés vers une deuxième `Foreach-Object` commande, qui filtre les objets retournés par la première `Foreach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-229">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="e4718-230">Les résultats de la deuxième commande sont stockés dans une variable nommée **Right** .</span><span class="sxs-lookup"><span data-stu-id="e4718-230">The results of the second command are stored in a variable named **Right** .</span></span>

<span data-ttu-id="e4718-231">Dans la troisième `Foreach-Object` commande, les résultats des deux premières `Foreach-Object` commandes dirigées, représentées par les variables **Left** et **Right** , sont traités à l’aide d’un opérateur de multiplication.</span><span class="sxs-lookup"><span data-stu-id="e4718-231">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right** , are processed by using a multiplication operator.</span></span> <span data-ttu-id="e4718-232">La commande indique que les objets stockés dans les variables de **gauche** et de **droite** doivent être multipliés, et spécifie que les résultats doivent être affichés sous la forme « membre de la plage de gauche \* membre de la plage droite = produit ».</span><span class="sxs-lookup"><span data-stu-id="e4718-232">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a><span data-ttu-id="e4718-233">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e4718-233">Verbose</span></span>

<span data-ttu-id="e4718-234">Affiche des informations détaillées sur l’opération effectuée par la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-234">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="e4718-235">Ces informations sont semblables aux informations contenues dans une trace ou dans un journal des transactions.</span><span class="sxs-lookup"><span data-stu-id="e4718-235">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="e4718-236">Ce paramètre fonctionne uniquement lorsque la commande génère un message détaillé.</span><span class="sxs-lookup"><span data-stu-id="e4718-236">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="e4718-237">Par exemple, ce paramètre fonctionne quand une commande contient l' `Write-Verbose` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-237">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-238">Le paramètre **Verbose** remplace la valeur de la `$VerbosePreference` variable pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4718-238">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="e4718-239">Étant donné que la valeur par défaut de la `$VerbosePreference` variable est **SilentlyContinue** , les messages détaillés ne sont pas affichés par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4718-239">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue** , verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="e4718-240">`-Verbose:$true` a le même effet que `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="e4718-240">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="e4718-241">`-Verbose:$false` supprime l’affichage des messages détaillés.</span><span class="sxs-lookup"><span data-stu-id="e4718-241">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="e4718-242">Utilisez ce paramètre lorsque la valeur de `$VerbosePreference` n’est pas **SilentlyContinue** (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="e4718-242">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="e4718-243">WarningAction</span><span class="sxs-lookup"><span data-stu-id="e4718-243">WarningAction</span></span>

<span data-ttu-id="e4718-244">Détermine la façon dont l’applet de commande répond à un avertissement de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-244">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="e4718-245">**Continue** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4718-245">**Continue** is the default value.</span></span> <span data-ttu-id="e4718-246">Ce paramètre fonctionne uniquement lorsque la commande génère un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="e4718-246">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="e4718-247">Par exemple, ce paramètre fonctionne quand une commande contient l' `Write-Warning` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-247">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-248">Le paramètre **WarningAction** remplace la valeur de la `$WarningPreference` variable pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4718-248">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="e4718-249">Étant donné que la valeur par défaut de la `$WarningPreference` variable est **continue** , les avertissements sont affichés et l’exécution se poursuit, sauf si vous utilisez le paramètre **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="e4718-249">Because the default value of the `$WarningPreference` variable is **Continue** , warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="e4718-250">`-WarningAction:Continue` affiche les messages d’avertissement et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-250">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="e4718-251">`Continue` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4718-251">`Continue` is the default.</span></span>

<span data-ttu-id="e4718-252">`-WarningAction:Inquire` affiche le message d’avertissement et vous invite à confirmer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4718-252">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="e4718-253">Cette valeur est rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="e4718-253">This value is rarely used.</span></span>

<span data-ttu-id="e4718-254">`-WarningAction:SilentlyContinue` supprime le message d’avertissement et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-254">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="e4718-255">`-WarningAction:Stop` affiche le message d’avertissement et arrête l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-255">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="e4718-256">Le paramètre **WarningAction** substitue, mais ne remplace pas la valeur de la `$WarningAction` variable de préférence lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="e4718-256">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="e4718-257">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="e4718-257">WarningVariable</span></span>

<span data-ttu-id="e4718-258">Stocke les avertissements relatifs à la commande dans la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e4718-258">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-259">Tous les avertissements générés sont enregistrés dans la variable même si les avertissements ne sont pas affichés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e4718-259">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="e4718-260">Pour ajouter les avertissements au contenu de la variable, au lieu de remplacer les avertissements qui peuvent déjà y être stockés, tapez un signe plus ( `+` ) avant le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="e4718-260">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="e4718-261">Par exemple, la commande suivante crée la `$a` variable et y stocke tous les avertissements :</span><span class="sxs-lookup"><span data-stu-id="e4718-261">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="e4718-262">La commande suivante ajoute tous les avertissements à la `$a` variable :</span><span class="sxs-lookup"><span data-stu-id="e4718-262">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="e4718-263">La commande suivante affiche le contenu de `$a` :</span><span class="sxs-lookup"><span data-stu-id="e4718-263">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="e4718-264">Vous pouvez utiliser ce paramètre pour créer une variable qui contient uniquement les avertissements de commandes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e4718-264">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="e4718-265">Vous pouvez utiliser la notation de tableau, telle que `$a[0]` ou, `$warning[1,2]` pour faire référence à des avertissements spécifiques stockés dans la variable.</span><span class="sxs-lookup"><span data-stu-id="e4718-265">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="e4718-266">La variable d’avertissement contient tous les avertissements générés par la commande, y compris les avertissements liés aux appels à des fonctions ou des scripts imbriqués.</span><span class="sxs-lookup"><span data-stu-id="e4718-266">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>

### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="e4718-267">Descriptions des paramètres de gestion des risques</span><span class="sxs-lookup"><span data-stu-id="e4718-267">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="e4718-268">WhatIf</span><span class="sxs-lookup"><span data-stu-id="e4718-268">WhatIf</span></span>

<span data-ttu-id="e4718-269">Affiche un message qui décrit l’effet de la commande, au lieu d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-269">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-270">Le paramètre **WhatIf** remplace la valeur de la `$WhatIfPreference` variable pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4718-270">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="e4718-271">Étant donné que la valeur par défaut de la `$WhatIfPreference` variable est 0 (désactivé), le comportement **WhatIf** n’est pas effectué sans le paramètre **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="e4718-271">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="e4718-272">Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="e4718-272">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="e4718-273">`-WhatIf:$true` a le même effet que `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="e4718-273">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="e4718-274">`-WhatIf:$false` supprime le comportement WhatIf automatique qui se produit lorsque la valeur de la `$WhatIfPreference` variable est 1.</span><span class="sxs-lookup"><span data-stu-id="e4718-274">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="e4718-275">Par exemple, la commande suivante utilise le `-WhatIf` paramètre dans une `Remove-Item` commande :</span><span class="sxs-lookup"><span data-stu-id="e4718-275">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="e4718-276">Au lieu de supprimer l’élément, PowerShell répertorie les opérations qu’il ferait et les éléments qui seraient affectés.</span><span class="sxs-lookup"><span data-stu-id="e4718-276">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="e4718-277">Cette commande génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e4718-277">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="e4718-278">Confirmer</span><span class="sxs-lookup"><span data-stu-id="e4718-278">Confirm</span></span>

<span data-ttu-id="e4718-279">Demande une confirmation avant d'exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-279">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="e4718-280">Le paramètre **Confirm** remplace la valeur de la `$ConfirmPreference` variable pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4718-280">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="e4718-281">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="e4718-281">The default value is true.</span></span> <span data-ttu-id="e4718-282">Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="e4718-282">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="e4718-283">`-Confirm:$true` a le même effet que `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="e4718-283">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="e4718-284">`-Confirm:$false` supprime la confirmation automatique, qui se produit lorsque la valeur de `$ConfirmPreference` est inférieure ou égale au risque estimé de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-284">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="e4718-285">Par exemple, la commande suivante utilise le paramètre **Confirm** avec une `Remove-Item` commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-285">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="e4718-286">Avant de supprimer l’élément, PowerShell répertorie les opérations qu’il ferait et les éléments qui seraient affectés et demande l’approbation.</span><span class="sxs-lookup"><span data-stu-id="e4718-286">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="e4718-287">Les options de confirmation de la réponse sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4718-287">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="e4718-288">response</span><span class="sxs-lookup"><span data-stu-id="e4718-288">Response</span></span>       |<span data-ttu-id="e4718-289">Résultats</span><span class="sxs-lookup"><span data-stu-id="e4718-289">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="e4718-290">Oui (Y)</span><span class="sxs-lookup"><span data-stu-id="e4718-290">Yes (Y)</span></span>        |<span data-ttu-id="e4718-291">Effectuez l’action.</span><span class="sxs-lookup"><span data-stu-id="e4718-291">Perform the action.</span></span>                                        |
|<span data-ttu-id="e4718-292">Oui pour tout (A)</span><span class="sxs-lookup"><span data-stu-id="e4718-292">Yes to All (A)</span></span> |<span data-ttu-id="e4718-293">Effectuer toutes les actions et supprimer les requêtes Confirm suivantes</span><span class="sxs-lookup"><span data-stu-id="e4718-293">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="e4718-294">pour cette commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-294">for this command.</span></span>                                          |
|<span data-ttu-id="e4718-295">Non (N) :</span><span class="sxs-lookup"><span data-stu-id="e4718-295">No (N):</span></span>        |<span data-ttu-id="e4718-296">N’effectuez pas l’action.</span><span class="sxs-lookup"><span data-stu-id="e4718-296">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="e4718-297">Non pour tout (L) :</span><span class="sxs-lookup"><span data-stu-id="e4718-297">No to All (L):</span></span> |<span data-ttu-id="e4718-298">Ne pas effectuer d’actions et supprimer la confirmation suivante</span><span class="sxs-lookup"><span data-stu-id="e4718-298">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="e4718-299">requêtes pour cette commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-299">queries for this command.</span></span>                                  |
|<span data-ttu-id="e4718-300">Interruption (S) :</span><span class="sxs-lookup"><span data-stu-id="e4718-300">Suspend (S):</span></span>   |<span data-ttu-id="e4718-301">Suspendez la commande et créez une session temporaire.</span><span class="sxs-lookup"><span data-stu-id="e4718-301">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="e4718-302">Aide ( ?)</span><span class="sxs-lookup"><span data-stu-id="e4718-302">Help (?)</span></span>       |<span data-ttu-id="e4718-303">Affichez l’aide pour ces options.</span><span class="sxs-lookup"><span data-stu-id="e4718-303">Display help for these options.</span></span>                            |

<span data-ttu-id="e4718-304">L’option **suspend** place la commande en attente et crée une session imbriquée temporaire dans laquelle vous pouvez travailler jusqu’à ce que vous soyez prêt à choisir une option de **confirmation** .</span><span class="sxs-lookup"><span data-stu-id="e4718-304">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="e4718-305">L’invite de commandes pour la session imbriquée comporte deux signes (>>) supplémentaires pour indiquer qu’il s’agit d’une opération enfant de la commande parent d’origine.</span><span class="sxs-lookup"><span data-stu-id="e4718-305">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="e4718-306">Vous pouvez exécuter des commandes et des scripts dans la session imbriquée.</span><span class="sxs-lookup"><span data-stu-id="e4718-306">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="e4718-307">Pour mettre fin à la session imbriquée et revenir aux options Confirm pour la commande d’origine, tapez « exit ».</span><span class="sxs-lookup"><span data-stu-id="e4718-307">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="e4718-308">Dans l’exemple suivant, l’option **suspend** (S) est utilisée pour arrêter temporairement une commande pendant que l’utilisateur vérifie l’aide d’un paramètre de commande.</span><span class="sxs-lookup"><span data-stu-id="e4718-308">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="e4718-309">Une fois les informations nécessaires recueillies, l’utilisateur tape « Exit » pour terminer l’invite imbriquée, puis sélectionne la réponse oui (y) à la requête Confirm.</span><span class="sxs-lookup"><span data-stu-id="e4718-309">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a><span data-ttu-id="e4718-310">MOT</span><span class="sxs-lookup"><span data-stu-id="e4718-310">KEYWORDS</span></span>

<span data-ttu-id="e4718-311">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="e4718-311">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="e4718-312">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="e4718-312">SEE ALSO</span></span>

[<span data-ttu-id="e4718-313">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="e4718-313">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="e4718-314">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="e4718-314">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="e4718-315">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="e4718-315">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="e4718-316">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="e4718-316">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="e4718-317">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="e4718-317">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
