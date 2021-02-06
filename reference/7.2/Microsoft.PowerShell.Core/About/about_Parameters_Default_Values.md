---
description: Décrit comment définir des valeurs par défaut personnalisées pour les paramètres d’applet de commande et les fonctions avancées.
Locale: en-US
ms.date: 05/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 102f163287717f7c9cd4f430704cc27ddea7ff4c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596955"
---
# <a name="about-parameters-default-values"></a><span data-ttu-id="8b253-103">À propos des valeurs par défaut des paramètres</span><span class="sxs-lookup"><span data-stu-id="8b253-103">About Parameters Default Values</span></span>

## <a name="short-description"></a><span data-ttu-id="8b253-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="8b253-104">Short description</span></span>

<span data-ttu-id="8b253-105">Décrit comment définir des valeurs par défaut personnalisées pour les paramètres d’applet de commande et les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="8b253-105">Describes how to set custom default values for cmdlet parameters and advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="8b253-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="8b253-106">Long description</span></span>

<span data-ttu-id="8b253-107">La `$PSDefaultParameterValues` variable de préférence vous permet de spécifier des valeurs par défaut personnalisées pour une applet de commande ou une fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="8b253-107">The `$PSDefaultParameterValues` preference variable lets you specify custom default values for any cmdlet or advanced function.</span></span> <span data-ttu-id="8b253-108">Les applets de commande et fonctions avancées utilisent la valeur par défaut personnalisée, sauf si vous spécifiez une autre valeur dans la commande.</span><span class="sxs-lookup"><span data-stu-id="8b253-108">Cmdlets and advanced functions use the custom default value unless you specify another value in the command.</span></span>

<span data-ttu-id="8b253-109">Les auteurs des applets de commande et des fonctions avancées définissent les valeurs par défaut standard de leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="8b253-109">The authors of cmdlets and advanced functions set standard default values for their parameters.</span></span> <span data-ttu-id="8b253-110">En règle générale, les valeurs par défaut standard sont utiles, mais elles peuvent ne pas convenir à tous les environnements.</span><span class="sxs-lookup"><span data-stu-id="8b253-110">Typically, the standard default values are useful, but they might not be appropriate for all environments.</span></span>

<span data-ttu-id="8b253-111">Cette fonctionnalité est particulièrement utile lorsque vous devez spécifier la même valeur de paramètre de remplacement presque chaque fois que vous utilisez la commande ou lorsqu’une valeur de paramètre particulière est difficile à mémoriser, par exemple un nom de serveur de messagerie ou un GUID de projet.</span><span class="sxs-lookup"><span data-stu-id="8b253-111">This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.</span></span>

<span data-ttu-id="8b253-112">Si la valeur par défaut souhaitée varie de manière prévisible, vous pouvez spécifier un bloc de script qui fournit différentes valeurs par défaut pour un paramètre dans des conditions différentes.</span><span class="sxs-lookup"><span data-stu-id="8b253-112">If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.</span></span>

<span data-ttu-id="8b253-113">`$PSDefaultParameterValues` a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b253-113">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b253-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b253-114">Syntax</span></span>

<span data-ttu-id="8b253-115">La `$PSDefaultParameterValues` variable est une table de hachage qui valide le format des clés en tant que type d’objet de **System. Management. Automation. DefaultParameterDictionary**.</span><span class="sxs-lookup"><span data-stu-id="8b253-115">The `$PSDefaultParameterValues` variable is a hash table that validates the format of keys as an object type of **System.Management.Automation.DefaultParameterDictionary**.</span></span> <span data-ttu-id="8b253-116">La table de hachage contient des paires **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="8b253-116">The hash table contains **Key/Value** pairs.</span></span> <span data-ttu-id="8b253-117">Une **clé** est au format `CmdletName:ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="8b253-117">A **Key** is in the format `CmdletName:ParameterName`.</span></span> <span data-ttu-id="8b253-118">Une **valeur** est le **DefaultValue** ou le **scriptblock** affecté à la clé.</span><span class="sxs-lookup"><span data-stu-id="8b253-118">A **Value** is the **DefaultValue** or **ScriptBlock** assigned to the key.</span></span>

<span data-ttu-id="8b253-119">La syntaxe de la `$PSDefaultParameterValues` variable de préférence est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8b253-119">The syntax of the `$PSDefaultParameterValues` preference variable is as follows:</span></span>

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

<span data-ttu-id="8b253-120">Les caractères génériques sont autorisés dans les valeurs **CmdletName** et **ParameterName** .</span><span class="sxs-lookup"><span data-stu-id="8b253-120">Wildcard characters are permitted in the **CmdletName** and **ParameterName** values.</span></span>

<span data-ttu-id="8b253-121">Pour définir, modifier, ajouter ou supprimer une paire **clé/valeur** spécifique de `$PSDefaultParameterValues` , utilisez les méthodes pour modifier une table de hachage standard.</span><span class="sxs-lookup"><span data-stu-id="8b253-121">To set, change, add, or remove a specific **Key/Value** pair from `$PSDefaultParameterValues`, use the methods to edit a standard hash table.</span></span> <span data-ttu-id="8b253-122">Par exemple, les méthodes **Add** et **Remove** .</span><span class="sxs-lookup"><span data-stu-id="8b253-122">For example, the **Add** and **Remove** methods.</span></span> <span data-ttu-id="8b253-123">Ces méthodes ne remplacent pas les autres valeurs de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b253-123">These methods don't overwrite other values in the hash table.</span></span>

<span data-ttu-id="8b253-124">Il existe une autre syntaxe qui ne remplace pas une `$PSDefaultParameterValues` table de hachage existante.</span><span class="sxs-lookup"><span data-stu-id="8b253-124">There's another syntax that doesn't overwrite an existing `$PSDefaultParameterValues` hash table.</span></span> <span data-ttu-id="8b253-125">Pour ajouter ou modifier une paire **clé/valeur** spécifique, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8b253-125">To add or change a specific **Key/Value** pair, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="8b253-126">**CmdletName** doit être le nom d’une applet de commande ou le nom d’une fonction avancée qui utilise l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="8b253-126">The **CmdletName** must be the name of a cmdlet or the name of an advanced function that uses the **CmdletBinding** attribute.</span></span> <span data-ttu-id="8b253-127">Vous ne pouvez pas utiliser `$PSDefaultParameterValues` pour spécifier des valeurs par défaut pour les scripts ou les fonctions simples.</span><span class="sxs-lookup"><span data-stu-id="8b253-127">You can't use `$PSDefaultParameterValues` to specify default values for scripts or simple functions.</span></span>

<span data-ttu-id="8b253-128">Le **DefaultValue** peut être un objet ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="8b253-128">The **DefaultValue** can be an object or a script block.</span></span> <span data-ttu-id="8b253-129">Si la valeur est un bloc de script, PowerShell évalue le bloc de script et utilise le résultat comme valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="8b253-129">If the value is a script block, PowerShell evaluates the script block and uses the result as the parameter value.</span></span> <span data-ttu-id="8b253-130">Lorsque le paramètre spécifié accepte une valeur de bloc de script, mettez la valeur du bloc de script entre accolades, par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b253-130">When the specified parameter accepts a script block value, enclose the script block value in a second set of braces, such as:</span></span>

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

<span data-ttu-id="8b253-131">Pour plus d’informations, consultez les documents suivants :</span><span class="sxs-lookup"><span data-stu-id="8b253-131">For more information, see the following documents:</span></span>

- [<span data-ttu-id="8b253-132">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="8b253-132">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="8b253-133">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="8b253-133">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="8b253-134">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="8b253-134">about_Preference_Variables</span></span>](about_Preference_Variables.md)

## <a name="examples"></a><span data-ttu-id="8b253-135">Exemples</span><span class="sxs-lookup"><span data-stu-id="8b253-135">Examples</span></span>

### <a name="how-to-set-psdefaultparametervalues"></a><span data-ttu-id="8b253-136">Comment définir \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="8b253-136">How to set \$PSDefaultParameterValues</span></span>

<span data-ttu-id="8b253-137">`$PSDefaultParameterValues` est une variable de préférence, donc elle existe uniquement dans la session dans laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="8b253-137">`$PSDefaultParameterValues` is a preference variable, so it exists only in the session in which it's set.</span></span> <span data-ttu-id="8b253-138">Il n'a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b253-138">It has no default value.</span></span>

<span data-ttu-id="8b253-139">Pour définir `$PSDefaultParameterValues` , tapez le nom de la variable et une ou plusieurs paires **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="8b253-139">To set `$PSDefaultParameterValues`, type the variable name and one or more **Key/Value** pairs.</span></span> <span data-ttu-id="8b253-140">Si vous exécutez une autre `$PSDefaultParameterValues` commande, elle remplace la table de hachage existante.</span><span class="sxs-lookup"><span data-stu-id="8b253-140">If you run another `$PSDefaultParameterValues` command, it overwrites the existing hash table.</span></span>

<span data-ttu-id="8b253-141">Pour obtenir des exemples sur la modification des paires **clé/valeur** sans remplacer les valeurs existantes de la table de hachage, consultez [How to Add values to \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) ou [How to change values in \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span><span class="sxs-lookup"><span data-stu-id="8b253-141">For examples about how to change **Key/Value** pairs without overwriting existing hash table values, see [How to add values to \$PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) or [How to change values in \$PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span></span>

<span data-ttu-id="8b253-142">Pour enregistrer `$PSDefaultParameterValues` les sessions ultérieures, ajoutez une `$PSDefaultParameterValues` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b253-142">To save `$PSDefaultParameterValues` for future sessions, add a `$PSDefaultParameterValues` command to your PowerShell profile.</span></span> <span data-ttu-id="8b253-143">Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8b253-143">For more information, see [about_Profiles](about_Profiles.md).</span></span>

#### <a name="set-a-custom-default-value"></a><span data-ttu-id="8b253-144">Définir une valeur par défaut personnalisée</span><span class="sxs-lookup"><span data-stu-id="8b253-144">Set a custom default value</span></span>

<span data-ttu-id="8b253-145">La paire **clé/valeur** affecte `Send-MailMessage:SmtpServer` à la clé une valeur par défaut personnalisée de **SERVEUR123**.</span><span class="sxs-lookup"><span data-stu-id="8b253-145">The **Key/Value** pair sets the `Send-MailMessage:SmtpServer` key to a custom default value of **Server123**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a><span data-ttu-id="8b253-146">Définir des valeurs par défaut pour plusieurs paramètres</span><span class="sxs-lookup"><span data-stu-id="8b253-146">Set default values for multiple parameters</span></span>

<span data-ttu-id="8b253-147">Pour définir des valeurs par défaut pour plusieurs paramètres, séparez chaque paire **clé/valeur** par un point-virgule ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="8b253-147">To set default values for multiple parameters, separate each **Key/Value** pair with a semicolon (`;`).</span></span> <span data-ttu-id="8b253-148">Les `Send-MailMessage:SmtpServer` `Get-WinEvent:LogName` clés et sont définies sur des valeurs par défaut personnalisées.</span><span class="sxs-lookup"><span data-stu-id="8b253-148">The `Send-MailMessage:SmtpServer` and `Get-WinEvent:LogName` keys are set to custom default values.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a><span data-ttu-id="8b253-149">Utiliser des caractères génériques et des paramètres de commutateur</span><span class="sxs-lookup"><span data-stu-id="8b253-149">Use wildcards and switch parameters</span></span>

<span data-ttu-id="8b253-150">Les noms des applets de commande et des paramètres peuvent contenir des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="8b253-150">The cmdlet and parameter names can contain wildcard characters.</span></span> <span data-ttu-id="8b253-151">Utilisez `$True` et `$False` pour définir des valeurs pour les paramètres de commutateur, tels que **Verbose**.</span><span class="sxs-lookup"><span data-stu-id="8b253-151">Use `$True` and `$False` to set values for switch parameters, such as **Verbose**.</span></span> <span data-ttu-id="8b253-152">Le paramètre **Verbose** du paramètre commun a la valeur `$True` pour toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="8b253-152">The common parameter's **Verbose** parameter is set to `$True` for all commands.</span></span>

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a><span data-ttu-id="8b253-153">Utiliser un tableau pour la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8b253-153">Use an array for the default value</span></span>

<span data-ttu-id="8b253-154">Si un paramètre peut accepter plusieurs valeurs, un tableau, vous pouvez définir plusieurs valeurs comme valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b253-154">If a parameter can accept multiple values, an array, you can set multiple values as the default values.</span></span> <span data-ttu-id="8b253-155">La valeur par défaut de la `Invoke-Command:ComputerName` clé est définie sur une valeur de tableau **SERVEUR01** et **Server02**.</span><span class="sxs-lookup"><span data-stu-id="8b253-155">The default value of the `Invoke-Command:ComputerName` key is set to an array value of **Server01** and **Server02**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a><span data-ttu-id="8b253-156">Utiliser un bloc de script</span><span class="sxs-lookup"><span data-stu-id="8b253-156">Use a script block</span></span>

<span data-ttu-id="8b253-157">Vous pouvez utiliser un bloc de script pour spécifier différentes valeurs par défaut pour un paramètre dans des conditions différentes.</span><span class="sxs-lookup"><span data-stu-id="8b253-157">You can use a script block to specify different default values for a parameter under different conditions.</span></span> <span data-ttu-id="8b253-158">PowerShell évalue le bloc de script et utilise le résultat comme valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b253-158">PowerShell evaluates the script block and uses the result as the default parameter value.</span></span>

<span data-ttu-id="8b253-159">La `Format-Table:AutoSize` clé affecte à ce paramètre la valeur par défaut **true**.</span><span class="sxs-lookup"><span data-stu-id="8b253-159">The `Format-Table:AutoSize` key sets that switch parameter to a default value of **True**.</span></span> <span data-ttu-id="8b253-160">L' `If` instruction contient une condition qui `$host.Name` doit être la console PowerShell, **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="8b253-160">The `If` statement contains a condition that the `$host.Name` must be the PowerShell console, **ConsoleHost**.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

<span data-ttu-id="8b253-161">Si un paramètre accepte une valeur de bloc de script, placez le bloc de script entre accolades.</span><span class="sxs-lookup"><span data-stu-id="8b253-161">If a parameter accepts a script block value, enclose the script block in an extra set of braces.</span></span> <span data-ttu-id="8b253-162">Lorsque PowerShell évalue le bloc de script externe, le résultat est le bloc de script interne et défini comme valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b253-162">When PowerShell evaluates the outer script block, the result is the inner script block, and that is set as the default parameter value.</span></span>

<span data-ttu-id="8b253-163">La `Invoke-Command:ScriptBlock` clé est définie sur une valeur par défaut du **Journal des événements système** , car le bloc de script est entouré d’un deuxième ensemble d’accolades.</span><span class="sxs-lookup"><span data-stu-id="8b253-163">The `Invoke-Command:ScriptBlock` key set to a default value of the **System event log** because the script block is enclosed in a second set of braces.</span></span> <span data-ttu-id="8b253-164">Le résultat du bloc de script est passé à l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8b253-164">The result of the script block is passed to the `Invoke-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a><span data-ttu-id="8b253-165">Obtention de \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="8b253-165">How to get \$PSDefaultParameterValues</span></span>

<span data-ttu-id="8b253-166">Les valeurs de la table de hachage sont affichées en entrant `$PSDefaultParameterValues` à l’invite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b253-166">The hash table values are displayed by entering `$PSDefaultParameterValues` at the PowerShell prompt.</span></span>

<span data-ttu-id="8b253-167">Une `$PSDefaultParameterValues` table de hachage est définie avec trois paires **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="8b253-167">A `$PSDefaultParameterValues` hash table is set with three **Key/Value** pairs.</span></span>
<span data-ttu-id="8b253-168">Cette table de hachage est utilisée dans les exemples suivants qui décrivent comment ajouter, modifier et supprimer des valeurs dans `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="8b253-168">This hash table is used in the following examples that describe how to add, change, and remove values from `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

<span data-ttu-id="8b253-169">Pour obtenir la valeur d’une `CmdletName:ParameterName` clé spécifique, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8b253-169">To get the value of a specific `CmdletName:ParameterName` key, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

<span data-ttu-id="8b253-170">Par exemple, pour obtenir la valeur de la `Send-MailMessage:SmtpServer` clé.</span><span class="sxs-lookup"><span data-stu-id="8b253-170">For example, to get the value for the `Send-MailMessage:SmtpServer` key.</span></span>

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a><span data-ttu-id="8b253-171">Ajout de valeurs à \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="8b253-171">How to add values to \$PSDefaultParameterValues</span></span>

<span data-ttu-id="8b253-172">Pour ajouter une valeur à `$PSDefaultParameterValues` , utilisez la méthode **Add** .</span><span class="sxs-lookup"><span data-stu-id="8b253-172">To add a value to `$PSDefaultParameterValues`, use the **Add** method.</span></span> <span data-ttu-id="8b253-173">L’ajout d’une valeur n’affecte pas les valeurs existantes de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b253-173">Adding a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="8b253-174">Utilisez une virgule ( `,` ) pour séparer la **clé** de la **valeur**.</span><span class="sxs-lookup"><span data-stu-id="8b253-174">Use a comma (`,`) to separate the **Key** from the **Value**.</span></span> <span data-ttu-id="8b253-175">La syntaxe suivante indique comment utiliser la méthode **Add** pour `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="8b253-175">The following syntax shows how to use the **Add** method for `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

<span data-ttu-id="8b253-176">La table de hachage créée dans l’exemple précédent est mise à jour avec une nouvelle paire **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="8b253-176">The hash table created in the prior example is updated with a new **Key/Value** pair.</span></span> <span data-ttu-id="8b253-177">La méthode **Add** affecte `Get-Process:Name` à la clé la valeur **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="8b253-177">The **Add** method sets the `Get-Process:Name` key to the value **PowerShell**.</span></span>

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

<span data-ttu-id="8b253-178">La syntaxe suivante remplit le même résultat.</span><span class="sxs-lookup"><span data-stu-id="8b253-178">The following syntax accomplishes the same result.</span></span>

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

<span data-ttu-id="8b253-179">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="8b253-179">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="8b253-180">La `Get-Process:Name` clé a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="8b253-180">The `Get-Process:Name` key was added.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a><span data-ttu-id="8b253-181">Comment supprimer des valeurs de \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="8b253-181">How to remove values from \$PSDefaultParameterValues</span></span>

<span data-ttu-id="8b253-182">Pour supprimer une valeur de `$PSDefaultParameterValues` , utilisez la méthode **Remove** des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b253-182">To remove a value from `$PSDefaultParameterValues`, use the **Remove** method of hash tables.</span></span> <span data-ttu-id="8b253-183">La suppression d’une valeur n’affecte pas les valeurs existantes de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b253-183">Removing a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="8b253-184">La syntaxe suivante montre comment utiliser la méthode **Remove** sur `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="8b253-184">The following syntax shows how to use the **Remove** method on `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

<span data-ttu-id="8b253-185">Dans cet exemple, la table de hachage créée dans l’exemple précédent est mise à jour pour supprimer une paire **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="8b253-185">In this example, the hash table created in the prior example is updated to remove a **Key/Value** pair.</span></span> <span data-ttu-id="8b253-186">La méthode **Remove** supprime la `Get-Process:Name` clé.</span><span class="sxs-lookup"><span data-stu-id="8b253-186">The **Remove** method removes the `Get-Process:Name` key.</span></span>

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

<span data-ttu-id="8b253-187">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="8b253-187">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="8b253-188">La `Get-Process:Name` clé a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="8b253-188">The `Get-Process:Name` key was removed.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a><span data-ttu-id="8b253-189">Comment modifier des valeurs dans \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="8b253-189">How to change values in \$PSDefaultParameterValues</span></span>

<span data-ttu-id="8b253-190">Les modifications apportées à une valeur spécifique n’affectent pas les valeurs existantes de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b253-190">Changes to a specific value don't affect existing hash table values.</span></span> <span data-ttu-id="8b253-191">Pour modifier une paire **clé/valeur** spécifique dans `$PSDefaultParameterValues` , utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8b253-191">To change a specific **Key/Value** pair in `$PSDefaultParameterValues`, use the following syntax:</span></span>

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="8b253-192">Dans cet exemple, la table de hachage créée dans l’exemple précédent est mise à jour pour modifier une paire **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="8b253-192">In this example, the hash table created in the prior example is updated to change a **Key/Value** pair.</span></span> <span data-ttu-id="8b253-193">La commande suivante remplace la `Send-MailMessage:SmtpServer` clé par une nouvelle valeur de **ServerXYZ**.</span><span class="sxs-lookup"><span data-stu-id="8b253-193">The following command changes the `Send-MailMessage:SmtpServer` key to a new value of **ServerXYZ**.</span></span>

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

<span data-ttu-id="8b253-194">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="8b253-194">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="8b253-195">La `Send-MailMessage:SmtpServer` clé a été remplacée par une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="8b253-195">The `Send-MailMessage:SmtpServer` key was changed to a new value.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a><span data-ttu-id="8b253-196">Comment désactiver et réactiver \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="8b253-196">How to disable and re-enable \$PSDefaultParameterValues</span></span>

<span data-ttu-id="8b253-197">Vous pouvez désactiver et réactiver temporairement `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="8b253-197">You can temporarily disable and then re-enable `$PSDefaultParameterValues`.</span></span>
<span data-ttu-id="8b253-198">La désactivation `$PSDefaultParameterValues` de est utile si vous exécutez des scripts qui requièrent des valeurs de paramètre par défaut différentes.</span><span class="sxs-lookup"><span data-stu-id="8b253-198">Disabling `$PSDefaultParameterValues` is useful if you're running scripts that need different default parameter values.</span></span>

<span data-ttu-id="8b253-199">Pour désactiver `$PSDefaultParameterValues` , ajoutez une clé `Disabled` avec la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="8b253-199">To disable `$PSDefaultParameterValues`, add a key of `Disabled` with a value of **True**.</span></span> <span data-ttu-id="8b253-200">Les valeurs de `$PSDefaultParameterValues` sont conservées, mais ne sont pas effectives.</span><span class="sxs-lookup"><span data-stu-id="8b253-200">The values in `$PSDefaultParameterValues` are preserved, but aren't effective.</span></span>

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

<span data-ttu-id="8b253-201">La syntaxe suivante remplit le même résultat.</span><span class="sxs-lookup"><span data-stu-id="8b253-201">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

<span data-ttu-id="8b253-202">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour avec la valeur de la `Disabled` clé.</span><span class="sxs-lookup"><span data-stu-id="8b253-202">The `$PSDefaultParameterValues` variable displays the updated hash table with the value for the `Disabled` key.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

<span data-ttu-id="8b253-203">Pour réactiver `$PSDefaultParameterValues` , supprimez la clé **désactivée** ou remplacez la valeur de la clé **désactivée** par `$False` .</span><span class="sxs-lookup"><span data-stu-id="8b253-203">To re-enable `$PSDefaultParameterValues`, remove the **Disabled** key or change the value of the **Disabled** key to `$False`.</span></span> <span data-ttu-id="8b253-204">La valeur précédente de `$PSDefaultParameterValues` est à nouveau effective.</span><span class="sxs-lookup"><span data-stu-id="8b253-204">The previous value of `$PSDefaultParameterValues` is effective again.</span></span>

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

<span data-ttu-id="8b253-205">La syntaxe suivante remplit le même résultat.</span><span class="sxs-lookup"><span data-stu-id="8b253-205">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

<span data-ttu-id="8b253-206">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="8b253-206">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="8b253-207">Lorsque la méthode **Remove** est utilisée, la `Disabled` clé est supprimée de la sortie.</span><span class="sxs-lookup"><span data-stu-id="8b253-207">When the **Remove** method is used, the `Disabled` key is removed from the output.</span></span>
<span data-ttu-id="8b253-208">Si l’autre syntaxe a été utilisée pour réactiver `$PSDefaultParameterValues` , la `Disabled` clé est affichée avec la **valeur false**.</span><span class="sxs-lookup"><span data-stu-id="8b253-208">If the alternate syntax was used to re-enable `$PSDefaultParameterValues`, the `Disabled` key is displayed as **False**.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a><span data-ttu-id="8b253-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b253-209">See also</span></span>

[<span data-ttu-id="8b253-210">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b253-210">about_CommonParameters</span></span>](https://go.microsoft.com/fwlink/?LinkID=113216)

[<span data-ttu-id="8b253-211">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="8b253-211">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="8b253-212">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="8b253-212">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="8b253-213">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="8b253-213">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="8b253-214">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="8b253-214">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="8b253-215">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="8b253-215">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="8b253-216">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="8b253-216">about_Script_Blocks</span></span>](about_Script_Blocks.md)

