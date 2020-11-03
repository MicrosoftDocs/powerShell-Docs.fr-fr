---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 876129fc8df9a78df257bf95220fc6587e68b9a2
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239840"
---
# <span data-ttu-id="0473d-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="0473d-103">Set-Variable</span></span>

## <span data-ttu-id="0473d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0473d-104">SYNOPSIS</span></span>
<span data-ttu-id="0473d-105">Définit la valeur d'une variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-105">Sets the value of a variable.</span></span> <span data-ttu-id="0473d-106">Crée la variable si celle avec le nom demandé n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="0473d-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="0473d-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0473d-107">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0473d-108">Description</span><span class="sxs-lookup"><span data-stu-id="0473d-108">DESCRIPTION</span></span>

<span data-ttu-id="0473d-109">L' `Set-Variable` applet de commande attribue une valeur à une variable spécifiée ou modifie la valeur actuelle.</span><span class="sxs-lookup"><span data-stu-id="0473d-109">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="0473d-110">Si la variable n'existe pas, l'applet de commande la crée.</span><span class="sxs-lookup"><span data-stu-id="0473d-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="0473d-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0473d-111">EXAMPLES</span></span>

### <span data-ttu-id="0473d-112">Exemple 1 : définir une variable et obtenir sa valeur</span><span class="sxs-lookup"><span data-stu-id="0473d-112">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="0473d-113">Ces commandes définissent la valeur de la `$desc` variable sur `A description` , puis obtient la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-113">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="0473d-114">Exemple 2 : définir une variable globale en lecture seule</span><span class="sxs-lookup"><span data-stu-id="0473d-114">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="0473d-115">Cet exemple crée une variable globale en lecture seule qui contient tous les processus sur le système, puis affiche toutes les propriétés de la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-115">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="0473d-116">La commande utilise l' `Set-Variable` applet de commande pour créer la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-116">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="0473d-117">Elle utilise le paramètre **PassThru** pour créer un objet représentant la nouvelle variable, et elle utilise l’opérateur de pipeline ( `|` ) pour passer l’objet à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="0473d-117">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="0473d-118">Elle utilise le paramètre **Property** de `Format-List` avec la valeur All ( `*` ) pour afficher toutes les propriétés de la variable nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="0473d-118">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="0473d-119">La valeur, `(Get-Process)` , est placée entre parenthèses pour s’assurer qu’elle est exécutée avant d’être stockée dans la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-119">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="0473d-120">Sinon, la variable contient les mots « **obtien-process** ».</span><span class="sxs-lookup"><span data-stu-id="0473d-120">Otherwise, the variable contains the words " **Get-Process** ".</span></span>

### <span data-ttu-id="0473d-121">Exemple 3 : comprendre les variables publiques et les variables privées</span><span class="sxs-lookup"><span data-stu-id="0473d-121">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="0473d-122">Cet exemple montre comment modifier la visibilité d’une variable en `Private` .</span><span class="sxs-lookup"><span data-stu-id="0473d-122">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="0473d-123">Cette variable peut être lue et modifiée par les scripts avec les autorisations requises, mais elle n'est pas visible par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0473d-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

<span data-ttu-id="0473d-124">Cette commande montre comment modifier la visibilité d’une variable en private.</span><span class="sxs-lookup"><span data-stu-id="0473d-124">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="0473d-125">Cette variable peut être lue et modifiée par les scripts avec les autorisations requises, mais elle n'est pas visible par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0473d-125">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="0473d-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0473d-126">PARAMETERS</span></span>

### <span data-ttu-id="0473d-127">Description</span><span class="sxs-lookup"><span data-stu-id="0473d-127">-Description</span></span>

<span data-ttu-id="0473d-128">Spécifie la description de la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-128">Specifies the description of the variable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-129">-Exclude</span><span class="sxs-lookup"><span data-stu-id="0473d-129">-Exclude</span></span>

<span data-ttu-id="0473d-130">Spécifie un tableau d’éléments que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="0473d-130">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="0473d-131">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="0473d-131">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0473d-132">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0473d-132">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="0473d-133">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0473d-133">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0473d-134">-Force</span><span class="sxs-lookup"><span data-stu-id="0473d-134">-Force</span></span>

<span data-ttu-id="0473d-135">Vous permet de créer une variable portant le même nom qu'une variable en lecture seule existante ou de modifier la valeur d'une variable en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="0473d-135">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="0473d-136">Par défaut, vous pouvez remplacer une variable, sauf si la variable a une valeur d’option de `ReadOnly` ou `Constant` .</span><span class="sxs-lookup"><span data-stu-id="0473d-136">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="0473d-137">Pour plus d’informations, consultez le paramètre **option** .</span><span class="sxs-lookup"><span data-stu-id="0473d-137">For more information, see the **Option** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-138">-Include</span><span class="sxs-lookup"><span data-stu-id="0473d-138">-Include</span></span>

<span data-ttu-id="0473d-139">Spécifie un tableau d’éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="0473d-139">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="0473d-140">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="0473d-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="0473d-141">Entrez un nom ou un modèle de nom, tel que `c*` .</span><span class="sxs-lookup"><span data-stu-id="0473d-141">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="0473d-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0473d-142">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0473d-143">-Name</span><span class="sxs-lookup"><span data-stu-id="0473d-143">-Name</span></span>

<span data-ttu-id="0473d-144">Spécifie le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-144">Specifies the variable name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-145">-Option</span><span class="sxs-lookup"><span data-stu-id="0473d-145">-Option</span></span>

<span data-ttu-id="0473d-146">Spécifie la valeur de la propriété **options** de la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-146">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="0473d-147">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="0473d-147">Valid values are:</span></span>

- <span data-ttu-id="0473d-148">`None`: Ne définit aucune option.</span><span class="sxs-lookup"><span data-stu-id="0473d-148">`None`: Sets no options.</span></span> <span data-ttu-id="0473d-149">(« None » est la valeur par défaut.)</span><span class="sxs-lookup"><span data-stu-id="0473d-149">("None" is the default.)</span></span>
- <span data-ttu-id="0473d-150">`ReadOnly`: Peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="0473d-150">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="0473d-151">Ne peut pas être modifié, sauf en utilisant le paramètre force.</span><span class="sxs-lookup"><span data-stu-id="0473d-151">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="0473d-152">`Constant`: Ne peut pas être supprimé ou modifié.</span><span class="sxs-lookup"><span data-stu-id="0473d-152">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="0473d-153">`Constant` est valide uniquement lorsque vous créez une variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-153">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="0473d-154">Vous ne pouvez pas remplacer les options d’une variable existante par `Constant` .</span><span class="sxs-lookup"><span data-stu-id="0473d-154">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="0473d-155">`Private`: La variable est disponible uniquement dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="0473d-155">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="0473d-156">`AllScope`: La variable est copiée vers toutes les nouvelles étendues créées.</span><span class="sxs-lookup"><span data-stu-id="0473d-156">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0473d-157">-PassThru</span></span>

<span data-ttu-id="0473d-158">Retourne un objet représentant la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-158">Returns an object representing the new variable.</span></span> <span data-ttu-id="0473d-159">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="0473d-159">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-160">-Étendue</span><span class="sxs-lookup"><span data-stu-id="0473d-160">-Scope</span></span>

<span data-ttu-id="0473d-161">Spécifie l’étendue de la variable. Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0473d-161">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0473d-162">Global</span><span class="sxs-lookup"><span data-stu-id="0473d-162">Global</span></span>
- <span data-ttu-id="0473d-163">Local</span><span class="sxs-lookup"><span data-stu-id="0473d-163">Local</span></span>
- <span data-ttu-id="0473d-164">Script</span><span class="sxs-lookup"><span data-stu-id="0473d-164">Script</span></span>
- <span data-ttu-id="0473d-165">Privées</span><span class="sxs-lookup"><span data-stu-id="0473d-165">Private</span></span>
- <span data-ttu-id="0473d-166">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent).</span><span class="sxs-lookup"><span data-stu-id="0473d-166">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="0473d-167">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0473d-167">Local is the default.</span></span>

<span data-ttu-id="0473d-168">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="0473d-168">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-169">-Value</span><span class="sxs-lookup"><span data-stu-id="0473d-169">-Value</span></span>

<span data-ttu-id="0473d-170">Spécifie la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="0473d-170">Specifies the value of the variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-171">-Visibilité</span><span class="sxs-lookup"><span data-stu-id="0473d-171">-Visibility</span></span>

<span data-ttu-id="0473d-172">Détermine si la variable est visible en dehors de la session dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="0473d-172">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="0473d-173">Ce paramètre est conçu pour être utilisé dans les scripts et les commandes qui seront remis à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="0473d-173">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="0473d-174">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="0473d-174">Valid values are:</span></span>

- <span data-ttu-id="0473d-175">Public : la variable est visible.</span><span class="sxs-lookup"><span data-stu-id="0473d-175">Public:  The variable is visible.</span></span> <span data-ttu-id="0473d-176">(« Public » est la valeur par défaut.)</span><span class="sxs-lookup"><span data-stu-id="0473d-176">("Public" is the default.)</span></span>
- <span data-ttu-id="0473d-177">Privé : la variable n’est pas visible.</span><span class="sxs-lookup"><span data-stu-id="0473d-177">Private: The variable is not visible.</span></span>

<span data-ttu-id="0473d-178">Quand une variable est privée, elle n’apparaît pas dans les listes de variables, telles que celles retournées par `Get-Variable` , ou dans les affichages du lecteur **variable :** .</span><span class="sxs-lookup"><span data-stu-id="0473d-178">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="0473d-179">Les commandes pour lire ou modifier la valeur d'une variable privée retournent une erreur.</span><span class="sxs-lookup"><span data-stu-id="0473d-179">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="0473d-180">Toutefois, l'utilisateur peut exécuter des commandes qui utilisent une variable privée si les commandes ont été écrites dans la session dans laquelle la variable a été définie.</span><span class="sxs-lookup"><span data-stu-id="0473d-180">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0473d-181">-Confirm</span></span>

<span data-ttu-id="0473d-182">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0473d-182">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0473d-183">-WhatIf</span></span>

<span data-ttu-id="0473d-184">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0473d-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0473d-185">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="0473d-185">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0473d-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0473d-186">CommonParameters</span></span>

<span data-ttu-id="0473d-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0473d-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0473d-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0473d-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0473d-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0473d-189">INPUTS</span></span>

### <span data-ttu-id="0473d-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="0473d-190">System.Object</span></span>

<span data-ttu-id="0473d-191">Vous pouvez diriger un objet qui représente la valeur de la variable vers `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="0473d-191">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="0473d-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0473d-192">OUTPUTS</span></span>

### <span data-ttu-id="0473d-193">None ou System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="0473d-193">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="0473d-194">Quand vous utilisez le paramètre **PassThru** , `Set-Variable` génère un objet **System. Management. Automation. PSVariable** représentant la variable nouvelle ou modifiée.</span><span class="sxs-lookup"><span data-stu-id="0473d-194">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="0473d-195">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="0473d-195">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0473d-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0473d-196">NOTES</span></span>

## <span data-ttu-id="0473d-197">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0473d-197">RELATED LINKS</span></span>

[<span data-ttu-id="0473d-198">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="0473d-198">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="0473d-199">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="0473d-199">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="0473d-200">New-Variable</span><span class="sxs-lookup"><span data-stu-id="0473d-200">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="0473d-201">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="0473d-201">Remove-Variable</span></span>](Remove-Variable.md)
