---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 4398ec332dfddfb4cdb2c29dceabb5bedaffdab5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201229"
---
# <span data-ttu-id="f2f27-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="f2f27-103">Set-Variable</span></span>

## <span data-ttu-id="f2f27-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f2f27-104">SYNOPSIS</span></span>
<span data-ttu-id="f2f27-105">Définit la valeur d'une variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-105">Sets the value of a variable.</span></span>
<span data-ttu-id="f2f27-106">Crée la variable si celle avec le nom demandé n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="f2f27-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="f2f27-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2f27-107">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f2f27-108">Description</span><span class="sxs-lookup"><span data-stu-id="f2f27-108">DESCRIPTION</span></span>

<span data-ttu-id="f2f27-109">L’applet de commande **Set-variable** affecte une valeur à une variable spécifiée ou modifie la valeur actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2f27-109">The **Set-Variable** cmdlet assigns a value to a specified variable or changes the current value.</span></span>
<span data-ttu-id="f2f27-110">Si la variable n'existe pas, l'applet de commande la crée.</span><span class="sxs-lookup"><span data-stu-id="f2f27-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="f2f27-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f2f27-111">EXAMPLES</span></span>

### <span data-ttu-id="f2f27-112">Exemple 1 : définir une variable et obtenir sa valeur</span><span class="sxs-lookup"><span data-stu-id="f2f27-112">Example 1: Set a variable and get its value</span></span>

```
PS C:\> Set-Variable -Name "desc" -Value "A description"
PS C:\> Get-Variable -Name "desc"
```

<span data-ttu-id="f2f27-113">Ces commandes définissent la valeur de la variable DESC sur une description, puis obtient la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-113">These commands set the value of the desc variable to A description, and then gets the value of the variable.</span></span>

### <span data-ttu-id="f2f27-114">Exemple 2 : définir une variable globale en lecture seule</span><span class="sxs-lookup"><span data-stu-id="f2f27-114">Example 2: Set a global, read-only variable</span></span>

```
PS C:\> Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru | Format-List -Property *
```

<span data-ttu-id="f2f27-115">Cette commande crée une variable globale, variable en lecture seule qui contient tous les processus sur le système, puis affiche toutes les propriétés de la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-115">This command creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

<span data-ttu-id="f2f27-116">La commande utilise l’applet de commande **Set-variable** pour créer la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-116">The command uses the **Set-Variable** cmdlet to create the variable.</span></span>
<span data-ttu-id="f2f27-117">Elle utilise le paramètre *PassThru* pour créer un objet représentant la nouvelle variable, et elle utilise l’opérateur de pipeline (|) pour passer l’objet à l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="f2f27-117">It uses the *PassThru* parameter to create an object representing the new variable, and it uses the pipeline operator (|) to pass the object to the Format-List cmdlet.</span></span>
<span data-ttu-id="f2f27-118">Elle utilise le paramètre *Property* de Format-List avec la valeur All (\*) pour afficher toutes les propriétés de la variable nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="f2f27-118">It uses the *Property* parameter of Format-List with a value of all (\*) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="f2f27-119">La valeur, « (Get-Process) », est placée entre parenthèses pour qu'elle soit exécutée avant d'être stockée dans la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-119">The value, "(Get-Process)", is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span>
<span data-ttu-id="f2f27-120">Sinon, la variable contient les mots « Get-Process ».</span><span class="sxs-lookup"><span data-stu-id="f2f27-120">Otherwise, the variable contains the words "Get-Process".</span></span>

### <span data-ttu-id="f2f27-121">Exemple 3 : comprendre les variables publiques et les variables privées</span><span class="sxs-lookup"><span data-stu-id="f2f27-121">Example 3: Understand public vs. private variables</span></span>

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

<span data-ttu-id="f2f27-122">Cette commande montre comment modifier la visibilité d’une variable en private.</span><span class="sxs-lookup"><span data-stu-id="f2f27-122">This command shows how to change the visibility of a variable to Private.</span></span>
<span data-ttu-id="f2f27-123">Cette variable peut être lue et modifiée par les scripts avec les autorisations requises, mais elle n'est pas visible par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2f27-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

<span data-ttu-id="f2f27-124">L'exemple de sortie montre la différence de comportement entre les variables publiques et les variables privées.</span><span class="sxs-lookup"><span data-stu-id="f2f27-124">The sample output shows the difference in the behavior of public and private variables.</span></span>

## <span data-ttu-id="f2f27-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2f27-125">PARAMETERS</span></span>

### <span data-ttu-id="f2f27-126">Description</span><span class="sxs-lookup"><span data-stu-id="f2f27-126">-Description</span></span>

<span data-ttu-id="f2f27-127">Spécifie la description de la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-127">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="f2f27-128">-Exclude</span><span class="sxs-lookup"><span data-stu-id="f2f27-128">-Exclude</span></span>

<span data-ttu-id="f2f27-129">Spécifie un tableau d’éléments que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="f2f27-129">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="f2f27-130">La valeur de ce paramètre qualifie le paramètre *Path* .</span><span class="sxs-lookup"><span data-stu-id="f2f27-130">The value of this parameter qualifies the *Path* parameter.</span></span>
<span data-ttu-id="f2f27-131">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f2f27-131">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="f2f27-132">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f2f27-132">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f2f27-133">-Force</span><span class="sxs-lookup"><span data-stu-id="f2f27-133">-Force</span></span>

<span data-ttu-id="f2f27-134">Vous permet de créer une variable portant le même nom qu'une variable en lecture seule existante ou de modifier la valeur d'une variable en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="f2f27-134">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="f2f27-135">Par défaut, vous pouvez remplacer une variable, sauf si la variable a la valeur d’option ReadOnly ou constant.</span><span class="sxs-lookup"><span data-stu-id="f2f27-135">By default, you can overwrite a variable, unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="f2f27-136">Pour plus d’informations, consultez le paramètre *option* .</span><span class="sxs-lookup"><span data-stu-id="f2f27-136">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="f2f27-137">-Include</span><span class="sxs-lookup"><span data-stu-id="f2f27-137">-Include</span></span>

<span data-ttu-id="f2f27-138">Spécifie un tableau d’éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="f2f27-138">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="f2f27-139">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="f2f27-139">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="f2f27-140">Entrez un nom ou un modèle de nom, tel que `c*` .</span><span class="sxs-lookup"><span data-stu-id="f2f27-140">Enter a name or name pattern, such as `c*`.</span></span>
<span data-ttu-id="f2f27-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f2f27-141">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f2f27-142">-Name</span><span class="sxs-lookup"><span data-stu-id="f2f27-142">-Name</span></span>

<span data-ttu-id="f2f27-143">Spécifie le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-143">Specifies the variable name.</span></span>

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

### <span data-ttu-id="f2f27-144">-Option</span><span class="sxs-lookup"><span data-stu-id="f2f27-144">-Option</span></span>

<span data-ttu-id="f2f27-145">Spécifie la valeur de la propriété **options** de la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-145">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="f2f27-146">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="f2f27-146">Valid values are:</span></span>

- <span data-ttu-id="f2f27-147">None : ne définit aucune option.</span><span class="sxs-lookup"><span data-stu-id="f2f27-147">None: Sets no options.</span></span> <span data-ttu-id="f2f27-148">(« None » est la valeur par défaut.)</span><span class="sxs-lookup"><span data-stu-id="f2f27-148">("None" is the default.)</span></span>
- <span data-ttu-id="f2f27-149">ReadOnly : peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="f2f27-149">ReadOnly: Can be deleted.</span></span> <span data-ttu-id="f2f27-150">Ne peut pas être modifié, sauf en utilisant le paramètre force.</span><span class="sxs-lookup"><span data-stu-id="f2f27-150">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="f2f27-151">Constante : ne peut pas être supprimé ou modifié.</span><span class="sxs-lookup"><span data-stu-id="f2f27-151">Constant: Cannot be deleted or changed.</span></span> <span data-ttu-id="f2f27-152">« Constant » est valide uniquement quand vous créez une variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-152">"Constant" is valid only when you are creating a variable.</span></span> <span data-ttu-id="f2f27-153">Vous ne pouvez pas remplacer les options d'une variable existante par « Constant ».</span><span class="sxs-lookup"><span data-stu-id="f2f27-153">You cannot change the options of an existing variable to "Constant".</span></span>
- <span data-ttu-id="f2f27-154">Privé : la variable est disponible uniquement dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2f27-154">Private: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="f2f27-155">Options AllScope : la variable est copiée vers toutes les nouvelles étendues créées.</span><span class="sxs-lookup"><span data-stu-id="f2f27-155">AllScope: The variable is copied to any new scopes that are created.</span></span>

<span data-ttu-id="f2f27-156">Pour afficher la propriété **options** de toutes les variables dans la session, tapez `Get-Variable | Format-Table -Property name, options -Autosize` .</span><span class="sxs-lookup"><span data-stu-id="f2f27-156">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -Autosize`.</span></span>

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

### <span data-ttu-id="f2f27-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f2f27-157">-PassThru</span></span>
<span data-ttu-id="f2f27-158">Retourne un objet représentant la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-158">Returns an object representing the new variable.</span></span>
<span data-ttu-id="f2f27-159">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="f2f27-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f2f27-160">-Étendue</span><span class="sxs-lookup"><span data-stu-id="f2f27-160">-Scope</span></span>

<span data-ttu-id="f2f27-161">Spécifie l’étendue de la variable. Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2f27-161">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f2f27-162">Global</span><span class="sxs-lookup"><span data-stu-id="f2f27-162">Global</span></span>
- <span data-ttu-id="f2f27-163">Local</span><span class="sxs-lookup"><span data-stu-id="f2f27-163">Local</span></span>
- <span data-ttu-id="f2f27-164">Script</span><span class="sxs-lookup"><span data-stu-id="f2f27-164">Script</span></span>
- <span data-ttu-id="f2f27-165">Privées</span><span class="sxs-lookup"><span data-stu-id="f2f27-165">Private</span></span>
- <span data-ttu-id="f2f27-166">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent).</span><span class="sxs-lookup"><span data-stu-id="f2f27-166">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="f2f27-167">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2f27-167">Local is the default.</span></span>

<span data-ttu-id="f2f27-168">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="f2f27-168">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

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

### <span data-ttu-id="f2f27-169">-Value</span><span class="sxs-lookup"><span data-stu-id="f2f27-169">-Value</span></span>

<span data-ttu-id="f2f27-170">Spécifie la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-170">Specifies the value of the variable.</span></span>

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

### <span data-ttu-id="f2f27-171">-Visibilité</span><span class="sxs-lookup"><span data-stu-id="f2f27-171">-Visibility</span></span>

<span data-ttu-id="f2f27-172">Détermine si la variable est visible en dehors de la session dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="f2f27-172">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="f2f27-173">Ce paramètre est conçu pour une utilisation dans les scripts et les commandes qui seront remis à d'autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f2f27-173">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="f2f27-174">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="f2f27-174">Valid values are:</span></span>

- <span data-ttu-id="f2f27-175">Public : la variable est visible.</span><span class="sxs-lookup"><span data-stu-id="f2f27-175">Public:  The variable is visible.</span></span> <span data-ttu-id="f2f27-176">(« Public » est la valeur par défaut.)</span><span class="sxs-lookup"><span data-stu-id="f2f27-176">("Public" is the default.)</span></span>
- <span data-ttu-id="f2f27-177">Privé : la variable n’est pas visible.</span><span class="sxs-lookup"><span data-stu-id="f2f27-177">Private: The variable is not visible.</span></span>

<span data-ttu-id="f2f27-178">Quand une variable est privée, elle n'apparaît pas dans les listes de variables, telles que celles retournées par Get-Variable, ni dans les affichages du lecteur Variable:.</span><span class="sxs-lookup"><span data-stu-id="f2f27-178">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="f2f27-179">Les commandes pour lire ou modifier la valeur d'une variable privée retournent une erreur.</span><span class="sxs-lookup"><span data-stu-id="f2f27-179">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="f2f27-180">Toutefois, l'utilisateur peut exécuter des commandes qui utilisent une variable privée si les commandes ont été écrites dans la session dans laquelle la variable a été définie.</span><span class="sxs-lookup"><span data-stu-id="f2f27-180">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="f2f27-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f2f27-181">-Confirm</span></span>
<span data-ttu-id="f2f27-182">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2f27-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f2f27-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f2f27-183">-WhatIf</span></span>

<span data-ttu-id="f2f27-184">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2f27-184">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f2f27-185">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="f2f27-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f2f27-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2f27-186">CommonParameters</span></span>

<span data-ttu-id="f2f27-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2f27-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2f27-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f2f27-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2f27-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f2f27-189">INPUTS</span></span>

### <span data-ttu-id="f2f27-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="f2f27-190">System.Object</span></span>

<span data-ttu-id="f2f27-191">Vous pouvez diriger un objet qui représente la valeur de la variable vers **Set-variable** .</span><span class="sxs-lookup"><span data-stu-id="f2f27-191">You can pipe an object that represents the value of the variable to **Set-Variable** .</span></span>

## <span data-ttu-id="f2f27-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f2f27-192">OUTPUTS</span></span>

### <span data-ttu-id="f2f27-193">None ou System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="f2f27-193">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="f2f27-194">Quand vous utilisez le paramètre *PassThru* , **Set-variable** génère un objet **System. Management. Automation. PSVariable** qui représente la variable nouvelle ou modifiée.</span><span class="sxs-lookup"><span data-stu-id="f2f27-194">When you use the *PassThru* parameter, **Set-Variable** generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="f2f27-195">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="f2f27-195">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f2f27-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f2f27-196">NOTES</span></span>

## <span data-ttu-id="f2f27-197">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f2f27-197">RELATED LINKS</span></span>

[<span data-ttu-id="f2f27-198">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="f2f27-198">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="f2f27-199">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="f2f27-199">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="f2f27-200">New-Variable</span><span class="sxs-lookup"><span data-stu-id="f2f27-200">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="f2f27-201">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="f2f27-201">Remove-Variable</span></span>](Remove-Variable.md)
