---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 791b500660ed536eb1bd7ba4d6f37e8211078a0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204426"
---
# <span data-ttu-id="8e19f-103">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="8e19f-103">Set-Alias</span></span>

## <span data-ttu-id="8e19f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8e19f-104">SYNOPSIS</span></span>
<span data-ttu-id="8e19f-105">Crée ou modifie un alias pour une applet de commande ou une autre commande dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-105">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="8e19f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8e19f-106">SYNTAX</span></span>

### <span data-ttu-id="8e19f-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8e19f-107">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8e19f-108">Description</span><span class="sxs-lookup"><span data-stu-id="8e19f-108">DESCRIPTION</span></span>

<span data-ttu-id="8e19f-109">L' `Set-Alias` applet de commande crée ou modifie un alias pour une applet de commande ou une commande, telle qu’une fonction, un script, un fichier ou un autre exécutable.</span><span class="sxs-lookup"><span data-stu-id="8e19f-109">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="8e19f-110">Un alias est un autre nom qui fait référence à une applet de commande ou à une commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-110">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="8e19f-111">Par exemple, `sal` est l’alias de l' `Set-Alias` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-111">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="8e19f-112">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="8e19f-112">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="8e19f-113">Une applet de commande peut avoir plusieurs alias, mais un alias ne peut être associé qu’à une seule applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-113">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="8e19f-114">Vous pouvez utiliser `Set-Alias` pour réassigner un alias existant à une autre applet de commande ou modifier les propriétés d’un alias, telles que la description.</span><span class="sxs-lookup"><span data-stu-id="8e19f-114">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="8e19f-115">Un alias créé ou modifié par `Set-Alias` n’est pas permanent et n’est disponible que pendant la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-115">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="8e19f-116">Une fois la session PowerShell fermée, l’alias est supprimé.</span><span class="sxs-lookup"><span data-stu-id="8e19f-116">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="8e19f-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8e19f-117">EXAMPLES</span></span>

### <span data-ttu-id="8e19f-118">Exemple 1 : créer un alias pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="8e19f-118">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="8e19f-119">Cette commande crée un alias pour une applet de commande dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-119">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="8e19f-120">L' `Set-Alias` applet de commande crée un alias dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-120">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="8e19f-121">Le paramètre **Name** spécifie le nom de l’alias, `list` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-121">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="8e19f-122">Le paramètre **value** spécifie l’applet de commande exécutée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-122">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="8e19f-123">Pour exécuter l’alias, tapez `list` sur la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e19f-123">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="8e19f-124">Exemple 2 : réaffecter un alias existant à une autre applet de commande</span><span class="sxs-lookup"><span data-stu-id="8e19f-124">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="8e19f-125">Cette commande réaffecte un alias existant pour exécuter une applet de commande différente.</span><span class="sxs-lookup"><span data-stu-id="8e19f-125">This command reassigns an existing alias to run a different cmdlet.</span></span>

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

<span data-ttu-id="8e19f-126">L' `Get-Alias` applet de commande utilise le paramètre **Name** pour afficher l' `list` alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-126">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="8e19f-127">L' `list` alias est associé à l' `Get-ChildItem` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-127">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="8e19f-128">Lorsque l' `list` alias est exécuté, les éléments du répertoire actif s’affichent.</span><span class="sxs-lookup"><span data-stu-id="8e19f-128">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="8e19f-129">L' `Set-Alias` applet de commande utilise le paramètre **Name** pour spécifier l' `list` alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-129">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="8e19f-130">Le paramètre **value** associe l’alias à l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-130">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="8e19f-131">L' `Get-Alias` applet de commande utilise le paramètre **Name** pour afficher l' `list` alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-131">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="8e19f-132">L' `list` alias est associé à l' `Get-Location` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-132">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="8e19f-133">Lorsque l' `list` alias est exécuté, l’emplacement du répertoire actif est affiché.</span><span class="sxs-lookup"><span data-stu-id="8e19f-133">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="8e19f-134">Exemple 3 : créer et modifier un alias en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8e19f-134">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="8e19f-135">Cette commande crée un alias en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="8e19f-135">This command creates a read-only alias.</span></span> <span data-ttu-id="8e19f-136">L’option en lecture seule empêche toute modification involontaire d’un alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-136">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="8e19f-137">Pour modifier ou supprimer un alias en lecture seule, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-137">To change or delete a read-only alias, use the **Force** parameter.</span></span>

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

<span data-ttu-id="8e19f-138">L' `Set-Alias` applet de commande crée un alias dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-138">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="8e19f-139">Le paramètre **Name** spécifie le nom de l’alias, `loc` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-139">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="8e19f-140">Le paramètre **value** spécifie l' `Get-Location` applet de commande exécutée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-140">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="8e19f-141">Le paramètre **option** spécifie la valeur **ReadOnly** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-141">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="8e19f-142">Le paramètre **PassThru** représente l’objet alias et envoie l’objet dans le pipeline à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-142">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8e19f-143">`Format-List` utilise le paramètre **Property** avec un astérisque ( `*` ) pour que toutes les propriétés soient affichées.</span><span class="sxs-lookup"><span data-stu-id="8e19f-143">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="8e19f-144">L’exemple de sortie montre une liste partielle de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="8e19f-144">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="8e19f-145">L' `loc` alias est modifié avec l’ajout de deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="8e19f-145">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="8e19f-146">**Description** ajoute du texte pour expliquer l’objectif de l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-146">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="8e19f-147">Le paramètre **force** est nécessaire, car l' `loc` alias est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="8e19f-147">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="8e19f-148">Si le paramètre **force** n’est pas utilisé, la modification échoue.</span><span class="sxs-lookup"><span data-stu-id="8e19f-148">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="8e19f-149">Exemple 4 : créer un alias pour un fichier exécutable</span><span class="sxs-lookup"><span data-stu-id="8e19f-149">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="8e19f-150">Cet exemple crée un alias pour un fichier exécutable sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8e19f-150">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="8e19f-151">L' `Set-Alias` applet de commande crée un alias dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-151">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="8e19f-152">Le paramètre **Name** spécifie le nom de l’alias, `np` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-152">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="8e19f-153">Le paramètre **value** spécifie le chemin d’accès et le nom de l’application **C:\Windows\notepad.exe** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-153">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe** .</span></span> <span data-ttu-id="8e19f-154">L' `Get-Alias` applet de commande utilise le paramètre **Name** pour indiquer que l' `np` alias est associé à **notepad.exe** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-154">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe** .</span></span>

<span data-ttu-id="8e19f-155">Pour exécuter l’alias, tapez `np` sur la ligne de commande PowerShell pour ouvrir **notepad.exe** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-155">To run the alias, type `np` on the PowerShell command line to open **notepad.exe** .</span></span>

### <span data-ttu-id="8e19f-156">Exemple 5 : créer un alias pour une commande avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="8e19f-156">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="8e19f-157">Cet exemple montre comment assigner un alias à une commande avec des paramètres.</span><span class="sxs-lookup"><span data-stu-id="8e19f-157">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="8e19f-158">Vous pouvez créer un alias pour une applet de commande, telle que `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-158">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="8e19f-159">Vous ne pouvez pas créer un alias pour une commande avec des paramètres et des valeurs, tels que `Set-Location -Path C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-159">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="8e19f-160">Pour créer un alias pour une commande, créez une fonction qui inclut la commande, puis créez un alias pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="8e19f-160">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="8e19f-161">Pour plus d’informations, consultez [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span><span class="sxs-lookup"><span data-stu-id="8e19f-161">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="8e19f-162">Une fonction nommée `CD32` est créée.</span><span class="sxs-lookup"><span data-stu-id="8e19f-162">A function named `CD32` is created.</span></span> <span data-ttu-id="8e19f-163">La fonction utilise l' `Set-Location` applet de commande avec le paramètre **path** pour spécifier le répertoire, **C:\Windows\System32** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-163">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, **C:\Windows\System32** .</span></span>

<span data-ttu-id="8e19f-164">L' `Set-Alias` applet de commande crée un alias pour la fonction dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8e19f-164">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="8e19f-165">Le paramètre **Name** spécifie le nom de l’alias, `Go` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-165">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="8e19f-166">Le paramètre **value** spécifie le nom de la fonction, `CD32` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-166">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="8e19f-167">Pour exécuter l’alias, tapez `Go` sur la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e19f-167">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="8e19f-168">La `CD32` fonction s’exécute et passe au répertoire **C:\Windows\System32** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-168">The `CD32` function runs and changes to the directory **C:\Windows\System32** .</span></span>

## <span data-ttu-id="8e19f-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8e19f-169">PARAMETERS</span></span>

### <span data-ttu-id="8e19f-170">Description</span><span class="sxs-lookup"><span data-stu-id="8e19f-170">-Description</span></span>

<span data-ttu-id="8e19f-171">Spécifie une description de l'alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-171">Specifies a description of the alias.</span></span> <span data-ttu-id="8e19f-172">Vous pouvez entrer n'importe quelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="8e19f-172">You can type any string.</span></span> <span data-ttu-id="8e19f-173">Si la description comprend des espaces, placez-la entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="8e19f-173">If the description includes spaces, enclose it single quotation marks.</span></span>

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

### <span data-ttu-id="8e19f-174">-Force</span><span class="sxs-lookup"><span data-stu-id="8e19f-174">-Force</span></span>

<span data-ttu-id="8e19f-175">Utilisez le paramètre **force** pour modifier ou supprimer un alias dont le paramètre **option** a la valeur **ReadOnly** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-175">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly** .</span></span>

<span data-ttu-id="8e19f-176">Le paramètre **force** ne peut pas modifier ou supprimer un alias avec le paramètre **option** défini sur **constant** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-176">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant** .</span></span>

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

### <span data-ttu-id="8e19f-177">-Name</span><span class="sxs-lookup"><span data-stu-id="8e19f-177">-Name</span></span>

<span data-ttu-id="8e19f-178">Spécifie le nom d’un nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-178">Specifies the name of a new alias.</span></span> <span data-ttu-id="8e19f-179">Un nom d’alias peut contenir des caractères alphanumériques et des traits d’Union.</span><span class="sxs-lookup"><span data-stu-id="8e19f-179">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="8e19f-180">Les noms d’alias ne peuvent pas être numériques, par exemple 123.</span><span class="sxs-lookup"><span data-stu-id="8e19f-180">Alias names cannot be numeric, such as 123.</span></span>

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

### <span data-ttu-id="8e19f-181">-Option</span><span class="sxs-lookup"><span data-stu-id="8e19f-181">-Option</span></span>

<span data-ttu-id="8e19f-182">Définit la valeur de la propriété **option** de l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-182">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="8e19f-183">Les valeurs telles que **ReadOnly** et **constant** protègent un alias des modifications inattendues.</span><span class="sxs-lookup"><span data-stu-id="8e19f-183">Values such as **ReadOnly** and **Constant** protect an alias from unintended changes.</span></span> <span data-ttu-id="8e19f-184">Pour afficher la propriété **option** de tous les alias dans la session, tapez `Get-Alias | Format-Table -Property Name, Options -Autosize` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-184">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="8e19f-185">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e19f-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="8e19f-186">**Options AllScope** L’alias est copié dans toutes les nouvelles étendues créées.</span><span class="sxs-lookup"><span data-stu-id="8e19f-186">**AllScope** The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="8e19f-187">**Constante** Ne peut pas être modifié ou supprimé.</span><span class="sxs-lookup"><span data-stu-id="8e19f-187">**Constant** Cannot be changed or deleted.</span></span>
- <span data-ttu-id="8e19f-188">**Aucun** Ne définit aucune option et est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8e19f-188">**None** Sets no options and is the default.</span></span>
- <span data-ttu-id="8e19f-189">**Privé** L’alias est uniquement disponible dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="8e19f-189">**Private** The alias is available only in the current scope.</span></span>
- <span data-ttu-id="8e19f-190">**Lecture seule** Ne peut pas être modifié ou supprimé, sauf si le paramètre **force** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8e19f-190">**ReadOnly** Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- <span data-ttu-id="8e19f-191">**Unspecified**</span><span class="sxs-lookup"><span data-stu-id="8e19f-191">**Unspecified**</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e19f-192">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8e19f-192">-PassThru</span></span>

<span data-ttu-id="8e19f-193">Retourne un objet qui représente l'alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-193">Returns an object that represents the alias.</span></span> <span data-ttu-id="8e19f-194">Utilisez une applet de commande format telle que `Format-List` pour afficher l’objet.</span><span class="sxs-lookup"><span data-stu-id="8e19f-194">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="8e19f-195">Par défaut, `Set-Alias` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="8e19f-195">By default, `Set-Alias` does not generate any output.</span></span>

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

### <span data-ttu-id="8e19f-196">-Étendue</span><span class="sxs-lookup"><span data-stu-id="8e19f-196">-Scope</span></span>

<span data-ttu-id="8e19f-197">Spécifie l'étendue dans laquelle cet alias est valide.</span><span class="sxs-lookup"><span data-stu-id="8e19f-197">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="8e19f-198">La valeur par défaut est **local** .</span><span class="sxs-lookup"><span data-stu-id="8e19f-198">The default value is **Local** .</span></span> <span data-ttu-id="8e19f-199">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="8e19f-199">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="8e19f-200">Les valeurs acceptables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e19f-200">The acceptable values are as follows:</span></span>

- <span data-ttu-id="8e19f-201">Global</span><span class="sxs-lookup"><span data-stu-id="8e19f-201">Global</span></span>
- <span data-ttu-id="8e19f-202">Local</span><span class="sxs-lookup"><span data-stu-id="8e19f-202">Local</span></span>
- <span data-ttu-id="8e19f-203">Privées</span><span class="sxs-lookup"><span data-stu-id="8e19f-203">Private</span></span>
- <span data-ttu-id="8e19f-204">Étendues numérotées</span><span class="sxs-lookup"><span data-stu-id="8e19f-204">Numbered scopes</span></span>
- <span data-ttu-id="8e19f-205">Script</span><span class="sxs-lookup"><span data-stu-id="8e19f-205">Script</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e19f-206">-Value</span><span class="sxs-lookup"><span data-stu-id="8e19f-206">-Value</span></span>

<span data-ttu-id="8e19f-207">Spécifie le nom de l’applet de commande ou de la commande exécutée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-207">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="8e19f-208">Le paramètre **value** est la propriété de **définition** de l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-208">The **Value** parameter is the alias's **Definition** property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8e19f-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8e19f-209">-Confirm</span></span>

<span data-ttu-id="8e19f-210">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8e19f-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8e19f-211">-WhatIf</span></span>

<span data-ttu-id="8e19f-212">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8e19f-213">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8e19f-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8e19f-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8e19f-214">CommonParameters</span></span>

<span data-ttu-id="8e19f-215">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8e19f-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8e19f-216">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8e19f-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8e19f-217">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8e19f-217">INPUTS</span></span>

### <span data-ttu-id="8e19f-218">Aucun</span><span class="sxs-lookup"><span data-stu-id="8e19f-218">None</span></span>

<span data-ttu-id="8e19f-219">`Set-Alias` n’accepte pas d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="8e19f-219">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="8e19f-220">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8e19f-220">OUTPUTS</span></span>

### <span data-ttu-id="8e19f-221">None ou System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="8e19f-221">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="8e19f-222">Quand vous utilisez le paramètre **PassThru** , `Set-Alias` génère un objet **System. Management. Automation. AliasInfo** représentant l’alias.</span><span class="sxs-lookup"><span data-stu-id="8e19f-222">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="8e19f-223">Dans le cas contraire, `Set-Alias` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="8e19f-223">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="8e19f-224">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8e19f-224">NOTES</span></span>

<span data-ttu-id="8e19f-225">PowerShell comprend des alias intégrés qui sont disponibles dans chaque session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e19f-225">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="8e19f-226">L' `Get-Alias` applet de commande affiche les alias disponibles dans une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e19f-226">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="8e19f-227">Pour créer un alias, utilisez les applets de commande `Set-Alias` ou `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-227">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="8e19f-228">Dans PowerShell 6, pour supprimer un alias, utilisez l' `Remove-Alias` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8e19f-228">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="8e19f-229">`Remove-Item` est accepté pour la compatibilité descendante comme pour les scripts créés avec des versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e19f-229">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="8e19f-230">Utilisez une commande telle que `Remove-Item -Path Alias:aliasname` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-230">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="8e19f-231">Pour créer un alias qui est disponible dans chaque session PowerShell, ajoutez-le à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e19f-231">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="8e19f-232">Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8e19f-232">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="8e19f-233">Un alias peut être enregistré et réutilisé dans une autre session PowerShell en procédant à une exportation et une importation.</span><span class="sxs-lookup"><span data-stu-id="8e19f-233">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="8e19f-234">Pour enregistrer un alias dans un fichier, utilisez `Export-Alias` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-234">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="8e19f-235">Pour ajouter un alias enregistré à une nouvelle session PowerShell, utilisez `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="8e19f-235">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="8e19f-236">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8e19f-236">RELATED LINKS</span></span>

[<span data-ttu-id="8e19f-237">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="8e19f-237">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="8e19f-238">about_Functions</span><span class="sxs-lookup"><span data-stu-id="8e19f-238">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="8e19f-239">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="8e19f-239">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="8e19f-240">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="8e19f-240">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="8e19f-241">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="8e19f-241">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="8e19f-242">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="8e19f-242">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="8e19f-243">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="8e19f-243">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="8e19f-244">New-Alias</span><span class="sxs-lookup"><span data-stu-id="8e19f-244">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="8e19f-245">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="8e19f-245">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="8e19f-246">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="8e19f-246">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)
