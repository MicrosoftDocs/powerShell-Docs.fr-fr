---
description: Décrit comment définir des valeurs par défaut personnalisées pour les paramètres d’applet de commande et les fonctions avancées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: c16af49308df26fc51f57c9bd176ad2fd5537e2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207466"
---
# <a name="about-parameters-default-values"></a><span data-ttu-id="1a880-104">À propos des valeurs par défaut des paramètres</span><span class="sxs-lookup"><span data-stu-id="1a880-104">About Parameters Default Values</span></span>

## <a name="short-description"></a><span data-ttu-id="1a880-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="1a880-105">Short description</span></span>

<span data-ttu-id="1a880-106">Décrit comment définir des valeurs par défaut personnalisées pour les paramètres d’applet de commande et les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="1a880-106">Describes how to set custom default values for cmdlet parameters and advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="1a880-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="1a880-107">Long description</span></span>

<span data-ttu-id="1a880-108">La `$PSDefaultParameterValues` variable de préférence vous permet de spécifier des valeurs par défaut personnalisées pour une applet de commande ou une fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="1a880-108">The `$PSDefaultParameterValues` preference variable lets you specify custom default values for any cmdlet or advanced function.</span></span> <span data-ttu-id="1a880-109">Les applets de commande et fonctions avancées utilisent la valeur par défaut personnalisée, sauf si vous spécifiez une autre valeur dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1a880-109">Cmdlets and advanced functions use the custom default value unless you specify another value in the command.</span></span>

<span data-ttu-id="1a880-110">Les auteurs des applets de commande et des fonctions avancées définissent les valeurs par défaut standard de leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="1a880-110">The authors of cmdlets and advanced functions set standard default values for their parameters.</span></span> <span data-ttu-id="1a880-111">En règle générale, les valeurs par défaut standard sont utiles, mais elles peuvent ne pas convenir à tous les environnements.</span><span class="sxs-lookup"><span data-stu-id="1a880-111">Typically, the standard default values are useful, but they might not be appropriate for all environments.</span></span>

<span data-ttu-id="1a880-112">Cette fonctionnalité est particulièrement utile lorsque vous devez spécifier la même valeur de paramètre de remplacement presque chaque fois que vous utilisez la commande ou lorsqu’une valeur de paramètre particulière est difficile à mémoriser, par exemple un nom de serveur de messagerie ou un GUID de projet.</span><span class="sxs-lookup"><span data-stu-id="1a880-112">This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.</span></span>

<span data-ttu-id="1a880-113">Si la valeur par défaut souhaitée varie de manière prévisible, vous pouvez spécifier un bloc de script qui fournit différentes valeurs par défaut pour un paramètre dans des conditions différentes.</span><span class="sxs-lookup"><span data-stu-id="1a880-113">If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.</span></span>

<span data-ttu-id="1a880-114">`$PSDefaultParameterValues` a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1a880-114">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a880-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a880-115">Syntax</span></span>

<span data-ttu-id="1a880-116">La `$PSDefaultParameterValues` variable est une table de hachage qui valide le format des clés en tant que type d’objet de **System. Management. Automation. DefaultParameterDictionary** .</span><span class="sxs-lookup"><span data-stu-id="1a880-116">The `$PSDefaultParameterValues` variable is a hash table that validates the format of keys as an object type of **System.Management.Automation.DefaultParameterDictionary** .</span></span> <span data-ttu-id="1a880-117">La table de hachage contient des paires **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-117">The hash table contains **Key/Value** pairs.</span></span> <span data-ttu-id="1a880-118">Une **clé** est au format `CmdletName:ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="1a880-118">A **Key** is in the format `CmdletName:ParameterName`.</span></span> <span data-ttu-id="1a880-119">Une **valeur** est le **DefaultValue** ou le **scriptblock** affecté à la clé.</span><span class="sxs-lookup"><span data-stu-id="1a880-119">A **Value** is the **DefaultValue** or **ScriptBlock** assigned to the key.</span></span>

<span data-ttu-id="1a880-120">La syntaxe de la `$PSDefaultParameterValues` variable de préférence est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1a880-120">The syntax of the `$PSDefaultParameterValues` preference variable is as follows:</span></span>

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

<span data-ttu-id="1a880-121">Les caractères génériques sont autorisés dans les valeurs **CmdletName** et **ParameterName** .</span><span class="sxs-lookup"><span data-stu-id="1a880-121">Wildcard characters are permitted in the **CmdletName** and **ParameterName** values.</span></span>

<span data-ttu-id="1a880-122">Pour définir, modifier, ajouter ou supprimer une paire **clé/valeur** spécifique de `$PSDefaultParameterValues` , utilisez les méthodes pour modifier une table de hachage standard.</span><span class="sxs-lookup"><span data-stu-id="1a880-122">To set, change, add, or remove a specific **Key/Value** pair from `$PSDefaultParameterValues`, use the methods to edit a standard hash table.</span></span> <span data-ttu-id="1a880-123">Par exemple, les méthodes **Add** et **Remove** .</span><span class="sxs-lookup"><span data-stu-id="1a880-123">For example, the **Add** and **Remove** methods.</span></span> <span data-ttu-id="1a880-124">Ces méthodes ne remplacent pas les autres valeurs de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="1a880-124">These methods don't overwrite other values in the hash table.</span></span>

<span data-ttu-id="1a880-125">Il existe une autre syntaxe qui ne remplace pas une `$PSDefaultParameterValues` table de hachage existante.</span><span class="sxs-lookup"><span data-stu-id="1a880-125">There's another syntax that doesn't overwrite an existing `$PSDefaultParameterValues` hash table.</span></span> <span data-ttu-id="1a880-126">Pour ajouter ou modifier une paire **clé/valeur** spécifique, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="1a880-126">To add or change a specific **Key/Value** pair, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="1a880-127">**CmdletName** doit être le nom d’une applet de commande ou le nom d’une fonction avancée qui utilise l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="1a880-127">The **CmdletName** must be the name of a cmdlet or the name of an advanced function that uses the **CmdletBinding** attribute.</span></span> <span data-ttu-id="1a880-128">Vous ne pouvez pas utiliser `$PSDefaultParameterValues` pour spécifier des valeurs par défaut pour les scripts ou les fonctions simples.</span><span class="sxs-lookup"><span data-stu-id="1a880-128">You can't use `$PSDefaultParameterValues` to specify default values for scripts or simple functions.</span></span>

<span data-ttu-id="1a880-129">Le **DefaultValue** peut être un objet ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="1a880-129">The **DefaultValue** can be an object or a script block.</span></span> <span data-ttu-id="1a880-130">Si la valeur est un bloc de script, PowerShell évalue le bloc de script et utilise le résultat comme valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="1a880-130">If the value is a script block, PowerShell evaluates the script block and uses the result as the parameter value.</span></span> <span data-ttu-id="1a880-131">Lorsque le paramètre spécifié accepte une valeur de bloc de script, mettez la valeur du bloc de script entre accolades, par exemple :</span><span class="sxs-lookup"><span data-stu-id="1a880-131">When the specified parameter accepts a script block value, enclose the script block value in a second set of braces, such as:</span></span>

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

<span data-ttu-id="1a880-132">Pour plus d’informations, consultez les documents suivants :</span><span class="sxs-lookup"><span data-stu-id="1a880-132">For more information, see the following documents:</span></span>

- [<span data-ttu-id="1a880-133">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="1a880-133">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="1a880-134">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="1a880-134">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="1a880-135">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="1a880-135">about_Preference_Variables</span></span>](about_Preference_Variables.md)

## <a name="examples"></a><span data-ttu-id="1a880-136">Exemples</span><span class="sxs-lookup"><span data-stu-id="1a880-136">Examples</span></span>

### <a name="how-to-set-psdefaultparametervalues"></a><span data-ttu-id="1a880-137">Comment définir \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="1a880-137">How to set \$PSDefaultParameterValues</span></span>

<span data-ttu-id="1a880-138">`$PSDefaultParameterValues` est une variable de préférence, donc elle existe uniquement dans la session dans laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="1a880-138">`$PSDefaultParameterValues` is a preference variable, so it exists only in the session in which it's set.</span></span> <span data-ttu-id="1a880-139">Il n'a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1a880-139">It has no default value.</span></span>

<span data-ttu-id="1a880-140">Pour définir `$PSDefaultParameterValues` , tapez le nom de la variable et une ou plusieurs paires **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-140">To set `$PSDefaultParameterValues`, type the variable name and one or more **Key/Value** pairs.</span></span> <span data-ttu-id="1a880-141">Si vous exécutez une autre `$PSDefaultParameterValues` commande, elle remplace la table de hachage existante.</span><span class="sxs-lookup"><span data-stu-id="1a880-141">If you run another `$PSDefaultParameterValues` command, it overwrites the existing hash table.</span></span>

<span data-ttu-id="1a880-142">Pour obtenir des exemples sur la modification des paires **clé/valeur** sans remplacer les valeurs existantes de la table de hachage, consultez [How to Add values to \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) ou [How to change values in \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span><span class="sxs-lookup"><span data-stu-id="1a880-142">For examples about how to change **Key/Value** pairs without overwriting existing hash table values, see [How to add values to \$PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) or [How to change values in \$PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span></span>

<span data-ttu-id="1a880-143">Pour enregistrer `$PSDefaultParameterValues` les sessions ultérieures, ajoutez une `$PSDefaultParameterValues` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a880-143">To save `$PSDefaultParameterValues` for future sessions, add a `$PSDefaultParameterValues` command to your PowerShell profile.</span></span> <span data-ttu-id="1a880-144">Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1a880-144">For more information, see [about_Profiles](about_Profiles.md).</span></span>

#### <a name="set-a-custom-default-value"></a><span data-ttu-id="1a880-145">Définir une valeur par défaut personnalisée</span><span class="sxs-lookup"><span data-stu-id="1a880-145">Set a custom default value</span></span>

<span data-ttu-id="1a880-146">La paire **clé/valeur** affecte `Send-MailMessage:SmtpServer` à la clé une valeur par défaut personnalisée de **SERVEUR123** .</span><span class="sxs-lookup"><span data-stu-id="1a880-146">The **Key/Value** pair sets the `Send-MailMessage:SmtpServer` key to a custom default value of **Server123** .</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a><span data-ttu-id="1a880-147">Définir des valeurs par défaut pour plusieurs paramètres</span><span class="sxs-lookup"><span data-stu-id="1a880-147">Set default values for multiple parameters</span></span>

<span data-ttu-id="1a880-148">Pour définir des valeurs par défaut pour plusieurs paramètres, séparez chaque paire **clé/valeur** par un point-virgule ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="1a880-148">To set default values for multiple parameters, separate each **Key/Value** pair with a semicolon (`;`).</span></span> <span data-ttu-id="1a880-149">Les `Send-MailMessage:SmtpServer` `Get-WinEvent:LogName` clés et sont définies sur des valeurs par défaut personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1a880-149">The `Send-MailMessage:SmtpServer` and `Get-WinEvent:LogName` keys are set to custom default values.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a><span data-ttu-id="1a880-150">Utiliser des caractères génériques et des paramètres de commutateur</span><span class="sxs-lookup"><span data-stu-id="1a880-150">Use wildcards and switch parameters</span></span>

<span data-ttu-id="1a880-151">Les noms des applets de commande et des paramètres peuvent contenir des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="1a880-151">The cmdlet and parameter names can contain wildcard characters.</span></span> <span data-ttu-id="1a880-152">Utilisez `$True` et `$False` pour définir des valeurs pour les paramètres de commutateur, tels que **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="1a880-152">Use `$True` and `$False` to set values for switch parameters, such as **Verbose** .</span></span> <span data-ttu-id="1a880-153">Le paramètre **Verbose** du paramètre commun a la valeur `$True` pour toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="1a880-153">The common parameter's **Verbose** parameter is set to `$True` for all commands.</span></span>

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a><span data-ttu-id="1a880-154">Utiliser un tableau pour la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="1a880-154">Use an array for the default value</span></span>

<span data-ttu-id="1a880-155">Si un paramètre peut accepter plusieurs valeurs, un tableau, vous pouvez définir plusieurs valeurs comme valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="1a880-155">If a parameter can accept multiple values, an array, you can set multiple values as the default values.</span></span> <span data-ttu-id="1a880-156">La valeur par défaut de la `Invoke-Command:ComputerName` clé est définie sur une valeur de tableau **SERVEUR01** et **Server02** .</span><span class="sxs-lookup"><span data-stu-id="1a880-156">The default value of the `Invoke-Command:ComputerName` key is set to an array value of **Server01** and **Server02** .</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a><span data-ttu-id="1a880-157">Utiliser un bloc de script</span><span class="sxs-lookup"><span data-stu-id="1a880-157">Use a script block</span></span>

<span data-ttu-id="1a880-158">Vous pouvez utiliser un bloc de script pour spécifier différentes valeurs par défaut pour un paramètre dans des conditions différentes.</span><span class="sxs-lookup"><span data-stu-id="1a880-158">You can use a script block to specify different default values for a parameter under different conditions.</span></span> <span data-ttu-id="1a880-159">PowerShell évalue le bloc de script et utilise le résultat comme valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="1a880-159">PowerShell evaluates the script block and uses the result as the default parameter value.</span></span>

<span data-ttu-id="1a880-160">La `Format-Table:AutoSize` clé affecte à ce paramètre la valeur par défaut **true** .</span><span class="sxs-lookup"><span data-stu-id="1a880-160">The `Format-Table:AutoSize` key sets that switch parameter to a default value of **True** .</span></span> <span data-ttu-id="1a880-161">L' `If` instruction contient une condition qui `$host.Name` doit être la console PowerShell, **ConsoleHost** .</span><span class="sxs-lookup"><span data-stu-id="1a880-161">The `If` statement contains a condition that the `$host.Name` must be the PowerShell console, **ConsoleHost** .</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

<span data-ttu-id="1a880-162">Si un paramètre accepte une valeur de bloc de script, placez le bloc de script entre accolades.</span><span class="sxs-lookup"><span data-stu-id="1a880-162">If a parameter accepts a script block value, enclose the script block in an extra set of braces.</span></span> <span data-ttu-id="1a880-163">Lorsque PowerShell évalue le bloc de script externe, le résultat est le bloc de script interne et défini comme valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="1a880-163">When PowerShell evaluates the outer script block, the result is the inner script block, and that is set as the default parameter value.</span></span>

<span data-ttu-id="1a880-164">La `Invoke-Command:ScriptBlock` clé est définie sur une valeur par défaut du **Journal des événements système** , car le bloc de script est entouré d’un deuxième ensemble d’accolades.</span><span class="sxs-lookup"><span data-stu-id="1a880-164">The `Invoke-Command:ScriptBlock` key set to a default value of the **System event log** because the script block is enclosed in a second set of braces.</span></span> <span data-ttu-id="1a880-165">Le résultat du bloc de script est passé à l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1a880-165">The result of the script block is passed to the `Invoke-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a><span data-ttu-id="1a880-166">Obtention de \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="1a880-166">How to get \$PSDefaultParameterValues</span></span>

<span data-ttu-id="1a880-167">Les valeurs de la table de hachage sont affichées en entrant `$PSDefaultParameterValues` à l’invite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a880-167">The hash table values are displayed by entering `$PSDefaultParameterValues` at the PowerShell prompt.</span></span>

<span data-ttu-id="1a880-168">Une `$PSDefaultParameterValues` table de hachage est définie avec trois paires **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-168">A `$PSDefaultParameterValues` hash table is set with three **Key/Value** pairs.</span></span>
<span data-ttu-id="1a880-169">Cette table de hachage est utilisée dans les exemples suivants qui décrivent comment ajouter, modifier et supprimer des valeurs dans `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="1a880-169">This hash table is used in the following examples that describe how to add, change, and remove values from `$PSDefaultParameterValues`.</span></span>

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

<span data-ttu-id="1a880-170">Pour obtenir la valeur d’une `CmdletName:ParameterName` clé spécifique, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="1a880-170">To get the value of a specific `CmdletName:ParameterName` key, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

<span data-ttu-id="1a880-171">Par exemple, pour obtenir la valeur de la `Send-MailMessage:SmtpServer` clé.</span><span class="sxs-lookup"><span data-stu-id="1a880-171">For example, to get the value for the `Send-MailMessage:SmtpServer` key.</span></span>

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a><span data-ttu-id="1a880-172">Ajout de valeurs à \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="1a880-172">How to add values to \$PSDefaultParameterValues</span></span>

<span data-ttu-id="1a880-173">Pour ajouter une valeur à `$PSDefaultParameterValues` , utilisez la méthode **Add** .</span><span class="sxs-lookup"><span data-stu-id="1a880-173">To add a value to `$PSDefaultParameterValues`, use the **Add** method.</span></span> <span data-ttu-id="1a880-174">L’ajout d’une valeur n’affecte pas les valeurs existantes de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="1a880-174">Adding a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="1a880-175">Utilisez une virgule ( `,` ) pour séparer la **clé** de la **valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-175">Use a comma (`,`) to separate the **Key** from the **Value** .</span></span> <span data-ttu-id="1a880-176">La syntaxe suivante indique comment utiliser la méthode **Add** pour `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="1a880-176">The following syntax shows how to use the **Add** method for `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

<span data-ttu-id="1a880-177">La table de hachage créée dans l’exemple précédent est mise à jour avec une nouvelle paire **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-177">The hash table created in the prior example is updated with a new **Key/Value** pair.</span></span> <span data-ttu-id="1a880-178">La méthode **Add** affecte `Get-Process:Name` à la clé la valeur **PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="1a880-178">The **Add** method sets the `Get-Process:Name` key to the value **PowerShell** .</span></span>

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

<span data-ttu-id="1a880-179">La syntaxe suivante remplit le même résultat.</span><span class="sxs-lookup"><span data-stu-id="1a880-179">The following syntax accomplishes the same result.</span></span>

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

<span data-ttu-id="1a880-180">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="1a880-180">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="1a880-181">La `Get-Process:Name` clé a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="1a880-181">The `Get-Process:Name` key was added.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a><span data-ttu-id="1a880-182">Comment supprimer des valeurs de \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="1a880-182">How to remove values from \$PSDefaultParameterValues</span></span>

<span data-ttu-id="1a880-183">Pour supprimer une valeur de `$PSDefaultParameterValues` , utilisez la méthode **Remove** des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="1a880-183">To remove a value from `$PSDefaultParameterValues`, use the **Remove** method of hash tables.</span></span> <span data-ttu-id="1a880-184">La suppression d’une valeur n’affecte pas les valeurs existantes de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="1a880-184">Removing a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="1a880-185">La syntaxe suivante montre comment utiliser la méthode **Remove** sur `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="1a880-185">The following syntax shows how to use the **Remove** method on `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

<span data-ttu-id="1a880-186">Dans cet exemple, la table de hachage créée dans l’exemple précédent est mise à jour pour supprimer une paire **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-186">In this example, the hash table created in the prior example is updated to remove a **Key/Value** pair.</span></span> <span data-ttu-id="1a880-187">La méthode **Remove** supprime la `Get-Process:Name` clé.</span><span class="sxs-lookup"><span data-stu-id="1a880-187">The **Remove** method removes the `Get-Process:Name` key.</span></span>

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

<span data-ttu-id="1a880-188">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="1a880-188">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="1a880-189">La `Get-Process:Name` clé a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="1a880-189">The `Get-Process:Name` key was removed.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a><span data-ttu-id="1a880-190">Comment modifier des valeurs dans \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="1a880-190">How to change values in \$PSDefaultParameterValues</span></span>

<span data-ttu-id="1a880-191">Les modifications apportées à une valeur spécifique n’affectent pas les valeurs existantes de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="1a880-191">Changes to a specific value don't affect existing hash table values.</span></span> <span data-ttu-id="1a880-192">Pour modifier une paire **clé/valeur** spécifique dans `$PSDefaultParameterValues` , utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="1a880-192">To change a specific **Key/Value** pair in `$PSDefaultParameterValues`, use the following syntax:</span></span>

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="1a880-193">Dans cet exemple, la table de hachage créée dans l’exemple précédent est mise à jour pour modifier une paire **clé/valeur** .</span><span class="sxs-lookup"><span data-stu-id="1a880-193">In this example, the hash table created in the prior example is updated to change a **Key/Value** pair.</span></span> <span data-ttu-id="1a880-194">La commande suivante remplace la `Send-MailMessage:SmtpServer` clé par une nouvelle valeur de **ServerXYZ** .</span><span class="sxs-lookup"><span data-stu-id="1a880-194">The following command changes the `Send-MailMessage:SmtpServer` key to a new value of **ServerXYZ** .</span></span>

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

<span data-ttu-id="1a880-195">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="1a880-195">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="1a880-196">La `Send-MailMessage:SmtpServer` clé a été remplacée par une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="1a880-196">The `Send-MailMessage:SmtpServer` key was changed to a new value.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a><span data-ttu-id="1a880-197">Comment désactiver et réactiver \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="1a880-197">How to disable and re-enable \$PSDefaultParameterValues</span></span>

<span data-ttu-id="1a880-198">Vous pouvez désactiver et réactiver temporairement `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="1a880-198">You can temporarily disable and then re-enable `$PSDefaultParameterValues`.</span></span>
<span data-ttu-id="1a880-199">La désactivation `$PSDefaultParameterValues` de est utile si vous exécutez des scripts qui requièrent des valeurs de paramètre par défaut différentes.</span><span class="sxs-lookup"><span data-stu-id="1a880-199">Disabling `$PSDefaultParameterValues` is useful if you're running scripts that need different default parameter values.</span></span>

<span data-ttu-id="1a880-200">Pour désactiver `$PSDefaultParameterValues` , ajoutez une clé `Disabled` avec la valeur **true** .</span><span class="sxs-lookup"><span data-stu-id="1a880-200">To disable `$PSDefaultParameterValues`, add a key of `Disabled` with a value of **True** .</span></span> <span data-ttu-id="1a880-201">Les valeurs de `$PSDefaultParameterValues` sont conservées, mais ne sont pas effectives.</span><span class="sxs-lookup"><span data-stu-id="1a880-201">The values in `$PSDefaultParameterValues` are preserved, but aren't effective.</span></span>

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

<span data-ttu-id="1a880-202">La syntaxe suivante remplit le même résultat.</span><span class="sxs-lookup"><span data-stu-id="1a880-202">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

<span data-ttu-id="1a880-203">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour avec la valeur de la `Disabled` clé.</span><span class="sxs-lookup"><span data-stu-id="1a880-203">The `$PSDefaultParameterValues` variable displays the updated hash table with the value for the `Disabled` key.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

<span data-ttu-id="1a880-204">Pour réactiver `$PSDefaultParameterValues` , supprimez la clé **désactivée** ou remplacez la valeur de la clé **désactivée** par `$False` .</span><span class="sxs-lookup"><span data-stu-id="1a880-204">To re-enable `$PSDefaultParameterValues`, remove the **Disabled** key or change the value of the **Disabled** key to `$False`.</span></span> <span data-ttu-id="1a880-205">La valeur précédente de `$PSDefaultParameterValues` est à nouveau effective.</span><span class="sxs-lookup"><span data-stu-id="1a880-205">The previous value of `$PSDefaultParameterValues` is effective again.</span></span>

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

<span data-ttu-id="1a880-206">La syntaxe suivante remplit le même résultat.</span><span class="sxs-lookup"><span data-stu-id="1a880-206">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

<span data-ttu-id="1a880-207">La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour.</span><span class="sxs-lookup"><span data-stu-id="1a880-207">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="1a880-208">Lorsque la méthode **Remove** est utilisée, la `Disabled` clé est supprimée de la sortie.</span><span class="sxs-lookup"><span data-stu-id="1a880-208">When the **Remove** method is used, the `Disabled` key is removed from the output.</span></span>
<span data-ttu-id="1a880-209">Si l’autre syntaxe a été utilisée pour réactiver `$PSDefaultParameterValues` , la `Disabled` clé est affichée avec la **valeur false** .</span><span class="sxs-lookup"><span data-stu-id="1a880-209">If the alternate syntax was used to re-enable `$PSDefaultParameterValues`, the `Disabled` key is displayed as **False** .</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a><span data-ttu-id="1a880-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a880-210">See also</span></span>

[<span data-ttu-id="1a880-211">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a880-211">about_CommonParameters</span></span>](https://go.microsoft.com/fwlink/?LinkID=113216)

[<span data-ttu-id="1a880-212">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="1a880-212">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="1a880-213">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="1a880-213">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="1a880-214">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="1a880-214">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="1a880-215">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="1a880-215">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="1a880-216">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1a880-216">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="1a880-217">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="1a880-217">about_Script_Blocks</span></span>](about_Script_Blocks.md)

