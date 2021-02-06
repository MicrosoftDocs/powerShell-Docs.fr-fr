---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: c77eb9c64022d028c3c4b2de6bf4551886b940e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595904"
---
# <span data-ttu-id="c3c42-102">New-Variable</span><span class="sxs-lookup"><span data-stu-id="c3c42-102">New-Variable</span></span>

## <span data-ttu-id="c3c42-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c3c42-103">SYNOPSIS</span></span>
<span data-ttu-id="c3c42-104">Crée une variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-104">Creates a new variable.</span></span>

## <span data-ttu-id="c3c42-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c3c42-105">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="c3c42-106">Description</span><span class="sxs-lookup"><span data-stu-id="c3c42-106">DESCRIPTION</span></span>
<span data-ttu-id="c3c42-107">L’applet **de commande New-variable** crée une variable dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3c42-107">The **New-Variable** cmdlet creates a new variable in PowerShell.</span></span>
<span data-ttu-id="c3c42-108">Vous pouvez assigner une valeur à la variable durant sa création, ou changer sa valeur après sa création.</span><span class="sxs-lookup"><span data-stu-id="c3c42-108">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="c3c42-109">Vous pouvez utiliser les paramètres de **New-variable** pour définir les propriétés de la variable, définir l’étendue d’une variable et déterminer si les variables sont publiques ou privées.</span><span class="sxs-lookup"><span data-stu-id="c3c42-109">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="c3c42-110">En général, vous créez une variable en tapant le nom de la variable et sa valeur, tel que `$Var = 3` , mais vous pouvez utiliser l’applet de commande **New-variable** pour utiliser ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="c3c42-110">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="c3c42-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c3c42-111">EXAMPLES</span></span>

### <span data-ttu-id="c3c42-112">Exemple 1 : créer une variable</span><span class="sxs-lookup"><span data-stu-id="c3c42-112">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="c3c42-113">Cette commande crée une variable nommée Days.</span><span class="sxs-lookup"><span data-stu-id="c3c42-113">This command creates a new variable named days.</span></span>
<span data-ttu-id="c3c42-114">Vous n’êtes pas obligé de taper le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="c3c42-114">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="c3c42-115">Exemple 2 : créer une variable et lui assigner une valeur</span><span class="sxs-lookup"><span data-stu-id="c3c42-115">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="c3c42-116">Cette commande crée une variable nommée zipcode et lui attribue la valeur 98033.</span><span class="sxs-lookup"><span data-stu-id="c3c42-116">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="c3c42-117">Exemple 3 : créer une variable avec l’option ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c3c42-117">Example 3: Create a variable with the ReadOnly option</span></span>

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

<span data-ttu-id="c3c42-118">Cet exemple montre comment utiliser l’option ReadOnly de **New-variable** pour empêcher une variable d’être remplacée.</span><span class="sxs-lookup"><span data-stu-id="c3c42-118">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="c3c42-119">La première commande crée une variable nommée Max et lui affecte la valeur 256.</span><span class="sxs-lookup"><span data-stu-id="c3c42-119">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="c3c42-120">Elle utilise le paramètre *option* avec la valeur ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="c3c42-120">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="c3c42-121">La deuxième commande tente de créer une deuxième variable portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="c3c42-121">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="c3c42-122">Cette commande retourne une erreur, car l'option lecture seule est définie sur la variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-122">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="c3c42-123">La troisième commande utilise le paramètre *force* pour remplacer la protection en lecture seule sur la variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-123">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="c3c42-124">Dans ce cas, la commande qui permet de créer une variable portant le même nom aboutit.</span><span class="sxs-lookup"><span data-stu-id="c3c42-124">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="c3c42-125">Exemple 4 : créer une variable privée</span><span class="sxs-lookup"><span data-stu-id="c3c42-125">Example 4: Create a private variable</span></span>

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

<span data-ttu-id="c3c42-126">Cette commande montre le comportement d'une variable privée dans un module.</span><span class="sxs-lookup"><span data-stu-id="c3c42-126">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="c3c42-127">Le module contient l’applet de commande Get-Counter, qui comporte une variable privée nommée Counter.</span><span class="sxs-lookup"><span data-stu-id="c3c42-127">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="c3c42-128">La commande utilise le paramètre *Visibility* avec la valeur Private pour créer la variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-128">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="c3c42-129">L'exemple de sortie montre le comportement d'une variable privée.</span><span class="sxs-lookup"><span data-stu-id="c3c42-129">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="c3c42-130">L'utilisateur qui a chargé le module ne peut pas afficher ou changer la valeur de la variable Counter. Toutefois, la variable Counter peut être lue et changée par les commandes du module.</span><span class="sxs-lookup"><span data-stu-id="c3c42-130">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="c3c42-131">Exemple 5 : créer une variable avec un espace</span><span class="sxs-lookup"><span data-stu-id="c3c42-131">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="c3c42-132">Cette commande montre que les variables avec des espaces peuvent être créées.</span><span class="sxs-lookup"><span data-stu-id="c3c42-132">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="c3c42-133">Vous pouvez accéder aux variables à l’aide de l’applet de commande **« obtenir-variable »** ou directement en délimitant une variable à l’aide d’accolades.</span><span class="sxs-lookup"><span data-stu-id="c3c42-133">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="c3c42-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3c42-134">PARAMETERS</span></span>

### <span data-ttu-id="c3c42-135">Description</span><span class="sxs-lookup"><span data-stu-id="c3c42-135">-Description</span></span>
<span data-ttu-id="c3c42-136">Spécifie une description de la variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-136">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="c3c42-137">-Force</span><span class="sxs-lookup"><span data-stu-id="c3c42-137">-Force</span></span>
<span data-ttu-id="c3c42-138">Indique que l’applet de commande crée une variable portant le même nom qu’une variable en lecture seule existante.</span><span class="sxs-lookup"><span data-stu-id="c3c42-138">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="c3c42-139">Par défaut, vous pouvez remplacer une variable, sauf si elle a la valeur d'option ReadOnly ou Constant.</span><span class="sxs-lookup"><span data-stu-id="c3c42-139">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="c3c42-140">Pour plus d’informations, consultez le paramètre *option* .</span><span class="sxs-lookup"><span data-stu-id="c3c42-140">For more information, see the *Option* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3c42-141">-Name</span><span class="sxs-lookup"><span data-stu-id="c3c42-141">-Name</span></span>
<span data-ttu-id="c3c42-142">Spécifie le nom de la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-142">Specifies a name for the new variable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3c42-143">-Option</span><span class="sxs-lookup"><span data-stu-id="c3c42-143">-Option</span></span>
<span data-ttu-id="c3c42-144">Spécifie la valeur de la propriété **options** de la variable. Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3c42-144">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3c42-145">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c3c42-145">None.</span></span>
<span data-ttu-id="c3c42-146">ne définit aucune option.</span><span class="sxs-lookup"><span data-stu-id="c3c42-146">Sets no options.</span></span>
<span data-ttu-id="c3c42-147">(None est la valeur par défaut.)</span><span class="sxs-lookup"><span data-stu-id="c3c42-147">(None is the default.)</span></span>
- <span data-ttu-id="c3c42-148">Seulement.</span><span class="sxs-lookup"><span data-stu-id="c3c42-148">ReadOnly.</span></span>
<span data-ttu-id="c3c42-149">peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="c3c42-149">Can be deleted.</span></span>
<span data-ttu-id="c3c42-150">Ne peut pas être modifié, sauf en utilisant le paramètre *force* .</span><span class="sxs-lookup"><span data-stu-id="c3c42-150">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="c3c42-151">Privé.</span><span class="sxs-lookup"><span data-stu-id="c3c42-151">Private.</span></span>
<span data-ttu-id="c3c42-152">la variable est disponible uniquement dans l'étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="c3c42-152">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="c3c42-153">Options AllScope.</span><span class="sxs-lookup"><span data-stu-id="c3c42-153">AllScope.</span></span>
<span data-ttu-id="c3c42-154">la variable est copiée vers toutes les nouvelles étendues créées.</span><span class="sxs-lookup"><span data-stu-id="c3c42-154">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="c3c42-155">Constante.</span><span class="sxs-lookup"><span data-stu-id="c3c42-155">Constant.</span></span>
<span data-ttu-id="c3c42-156">ne peut pas être supprimé ni modifié.</span><span class="sxs-lookup"><span data-stu-id="c3c42-156">Cannot be deleted or changed.</span></span>
<span data-ttu-id="c3c42-157">La constante n’est valide que lorsque vous créez une variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-157">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="c3c42-158">Vous ne pouvez pas modifier les options d’une variable existante en constant.</span><span class="sxs-lookup"><span data-stu-id="c3c42-158">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="c3c42-159">Pour afficher la propriété **options** de toutes les variables dans la session, tapez `Get-Variable | Format-Table -Property name, options -autosize` .</span><span class="sxs-lookup"><span data-stu-id="c3c42-159">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="c3c42-160">-PassThru</span><span class="sxs-lookup"><span data-stu-id="c3c42-160">-PassThru</span></span>
<span data-ttu-id="c3c42-161">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="c3c42-161">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="c3c42-162">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="c3c42-162">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3c42-163">-Étendue</span><span class="sxs-lookup"><span data-stu-id="c3c42-163">-Scope</span></span>
<span data-ttu-id="c3c42-164">Spécifie la portée de la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-164">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="c3c42-165">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c3c42-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3c42-166">Généralités.</span><span class="sxs-lookup"><span data-stu-id="c3c42-166">Global.</span></span>
<span data-ttu-id="c3c42-167">Les variables créées dans l’étendue globale sont accessibles partout dans un processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3c42-167">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="c3c42-168">Local.</span><span class="sxs-lookup"><span data-stu-id="c3c42-168">Local.</span></span>
<span data-ttu-id="c3c42-169">La portée locale fait référence à l’étendue actuelle. il peut s’agir de n’importe quelle portée en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="c3c42-169">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="c3c42-170">Script.</span><span class="sxs-lookup"><span data-stu-id="c3c42-170">Script.</span></span>
<span data-ttu-id="c3c42-171">Les variables créées dans la portée du script sont accessibles uniquement dans le fichier de script ou le module dans lequel elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="c3c42-171">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="c3c42-172">Privé.</span><span class="sxs-lookup"><span data-stu-id="c3c42-172">Private.</span></span>
<span data-ttu-id="c3c42-173">Les variables créées dans l’étendue privée ne sont pas accessibles en dehors de l’étendue dans laquelle elles existent.</span><span class="sxs-lookup"><span data-stu-id="c3c42-173">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="c3c42-174">Vous pouvez utiliser une étendue privée pour créer une version privée d’un élément portant le même nom dans une autre étendue.</span><span class="sxs-lookup"><span data-stu-id="c3c42-174">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="c3c42-175">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est l’étendue actuelle, 1 est son parent, 2 le parent de l’étendue parente, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="c3c42-175">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="c3c42-176">Les nombres négatifs ne peuvent pas être utilisés.</span><span class="sxs-lookup"><span data-stu-id="c3c42-176">Negative numbers cannot be used.</span></span>

<span data-ttu-id="c3c42-177">Local est l’étendue par défaut lorsque le paramètre d’étendue n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="c3c42-177">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="c3c42-178">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="c3c42-178">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="c3c42-179">-Value</span><span class="sxs-lookup"><span data-stu-id="c3c42-179">-Value</span></span>
<span data-ttu-id="c3c42-180">Spécifie la valeur initiale de la variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-180">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="c3c42-181">-Visibilité</span><span class="sxs-lookup"><span data-stu-id="c3c42-181">-Visibility</span></span>
<span data-ttu-id="c3c42-182">Détermine si la variable est visible en dehors de la session dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="c3c42-182">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="c3c42-183">Ce paramètre est conçu pour une utilisation dans les scripts et les commandes qui seront remis à d'autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c3c42-183">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="c3c42-184">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c3c42-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3c42-185">Public.</span><span class="sxs-lookup"><span data-stu-id="c3c42-185">Public.</span></span>
<span data-ttu-id="c3c42-186">la variable est visible.</span><span class="sxs-lookup"><span data-stu-id="c3c42-186">The variable is visible.</span></span>
<span data-ttu-id="c3c42-187">(Public est la valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="c3c42-187">(Public is the default.)</span></span>
- <span data-ttu-id="c3c42-188">Privé.</span><span class="sxs-lookup"><span data-stu-id="c3c42-188">Private.</span></span>
<span data-ttu-id="c3c42-189">la variable n'est pas visible.</span><span class="sxs-lookup"><span data-stu-id="c3c42-189">The variable is not visible.</span></span>

<span data-ttu-id="c3c42-190">Quand une variable est privée, elle n'apparaît pas dans les listes de variables, telles que celles retournées par Get-Variable, ni dans les affichages du lecteur Variable:.</span><span class="sxs-lookup"><span data-stu-id="c3c42-190">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="c3c42-191">Les commandes pour lire ou modifier la valeur d'une variable privée retournent une erreur.</span><span class="sxs-lookup"><span data-stu-id="c3c42-191">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="c3c42-192">Toutefois, l'utilisateur peut exécuter des commandes qui utilisent une variable privée si les commandes ont été écrites dans la session dans laquelle la variable a été définie.</span><span class="sxs-lookup"><span data-stu-id="c3c42-192">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3c42-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c3c42-193">-Confirm</span></span>
<span data-ttu-id="c3c42-194">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c3c42-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c3c42-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c3c42-195">-WhatIf</span></span>
<span data-ttu-id="c3c42-196">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c3c42-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c3c42-197">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c3c42-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c3c42-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3c42-198">CommonParameters</span></span>
<span data-ttu-id="c3c42-199">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3c42-200">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c3c42-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3c42-201">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c3c42-201">INPUTS</span></span>

### <span data-ttu-id="c3c42-202">System.Object</span><span class="sxs-lookup"><span data-stu-id="c3c42-202">System.Object</span></span>
<span data-ttu-id="c3c42-203">Vous pouvez diriger une valeur vers **New-variable**.</span><span class="sxs-lookup"><span data-stu-id="c3c42-203">You can pipe a value to **New-Variable**.</span></span>

## <span data-ttu-id="c3c42-204">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c3c42-204">OUTPUTS</span></span>

### <span data-ttu-id="c3c42-205">None ou System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="c3c42-205">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="c3c42-206">Quand vous utilisez le paramètre *PassThru* , **New-variable** génère un objet **System. Management. Automation. PSVariable** représentant la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="c3c42-206">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="c3c42-207">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c3c42-207">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c3c42-208">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c3c42-208">NOTES</span></span>

## <span data-ttu-id="c3c42-209">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c3c42-209">RELATED LINKS</span></span>

[<span data-ttu-id="c3c42-210">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="c3c42-210">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="c3c42-211">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="c3c42-211">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="c3c42-212">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="c3c42-212">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="c3c42-213">Set-variable</span><span class="sxs-lookup"><span data-stu-id="c3c42-213">Set-Variable</span></span>](Set-Variable.md)

