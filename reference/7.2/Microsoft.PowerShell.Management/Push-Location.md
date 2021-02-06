---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: eaa7622e29680de4228579f8b77a6c829a586bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598367"
---
# <span data-ttu-id="11680-102">Push-Location</span><span class="sxs-lookup"><span data-stu-id="11680-102">Push-Location</span></span>

## <span data-ttu-id="11680-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="11680-103">SYNOPSIS</span></span>
<span data-ttu-id="11680-104">Ajoute l'emplacement actuel au sommet d'une liste d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="11680-104">Adds the current location to the top of a location stack.</span></span>

## <span data-ttu-id="11680-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="11680-105">SYNTAX</span></span>

### <span data-ttu-id="11680-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="11680-106">Path (Default)</span></span>

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### <span data-ttu-id="11680-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="11680-107">LiteralPath</span></span>

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="11680-108">Description</span><span class="sxs-lookup"><span data-stu-id="11680-108">DESCRIPTION</span></span>

<span data-ttu-id="11680-109">L' `Push-Location` applet de commande ajoute (« push ») l’emplacement actuel sur une pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="11680-109">The `Push-Location` cmdlet adds ("pushes") the current location onto a location stack.</span></span> <span data-ttu-id="11680-110">Si vous spécifiez un chemin d’accès, `Push-Location` exécute un push de l’emplacement actuel sur une pile d’emplacements, puis modifie l’emplacement actuel à l’emplacement spécifié par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="11680-110">If you specify a path, `Push-Location` pushes the current location onto a location stack and then changes the current location to the location specified by the path.</span></span> <span data-ttu-id="11680-111">Vous pouvez utiliser l' `Pop-Location` applet de commande pour récupérer les emplacements de la pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="11680-111">You can use the `Pop-Location` cmdlet to get locations from the location stack.</span></span>

<span data-ttu-id="11680-112">Par défaut, l' `Push-Location` applet de commande exécute un push de l’emplacement actuel dans la pile d’emplacements active, mais vous pouvez utiliser le paramètre **StackName** pour spécifier une autre pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="11680-112">By default, the `Push-Location` cmdlet pushes the current location onto the current location stack, but you can use the **StackName** parameter to specify an alternate location stack.</span></span> <span data-ttu-id="11680-113">Si la pile n’existe pas, la `Push-Location` crée.</span><span class="sxs-lookup"><span data-stu-id="11680-113">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="11680-114">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="11680-114">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="11680-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="11680-115">EXAMPLES</span></span>

### <span data-ttu-id="11680-116">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="11680-116">Example 1</span></span>

<span data-ttu-id="11680-117">Cet exemple exécute un push de l’emplacement actuel dans la pile d’emplacements par défaut, puis modifie l’emplacement en `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="11680-117">This example pushes the current location onto the default location stack and then changes the location to `C:\Windows`.</span></span>

```
PS C:\> Push-Location C:\Windows
```

### <span data-ttu-id="11680-118">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="11680-118">Example 2</span></span>

<span data-ttu-id="11680-119">Cet exemple exécute un push de l’emplacement actuel dans la pile RegFunction, puis et modifie l’emplacement actuel à l' `HKLM:\Software\Policies` emplacement.</span><span class="sxs-lookup"><span data-stu-id="11680-119">This example pushes the current location onto the RegFunction stack and changes the current location to the `HKLM:\Software\Policies` location.</span></span>

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

<span data-ttu-id="11680-120">Vous pouvez utiliser les applets de commande location dans n’importe quel lecteur PowerShell (PSDrive).</span><span class="sxs-lookup"><span data-stu-id="11680-120">You can use the Location cmdlets in any PowerShell drive (PSDrive).</span></span>

### <span data-ttu-id="11680-121">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="11680-121">Example 3</span></span>

<span data-ttu-id="11680-122">Cette commande place l'emplacement actuel sur la pile par défaut.</span><span class="sxs-lookup"><span data-stu-id="11680-122">This command pushes the current location onto the default stack.</span></span> <span data-ttu-id="11680-123">Elle ne modifie pas l'emplacement.</span><span class="sxs-lookup"><span data-stu-id="11680-123">It does not change the location.</span></span>

```
PS C:\> Push-Location
```

### <span data-ttu-id="11680-124">Exemple 4 : créer et utiliser une pile nommée</span><span class="sxs-lookup"><span data-stu-id="11680-124">Example 4 - Create and use a named stack</span></span>

<span data-ttu-id="11680-125">Ces commandes indiquent comment créer et utiliser une pile d'emplacement nommée.</span><span class="sxs-lookup"><span data-stu-id="11680-125">These commands show how to create and use a named location stack.</span></span>

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

<span data-ttu-id="11680-126">La première commande place l’emplacement actuel sur une nouvelle pile nommée Stack2, puis modifie l’emplacement actuel dans le répertoire de départ, représenté dans la commande par le symbole de tilde ( `~` ), qui, lorsqu’il est utilisé sur un lecteur de fournisseur FileSystem, est équivalent à `$HOME` et `$env:USERPROFILE` .</span><span class="sxs-lookup"><span data-stu-id="11680-126">The first command pushes the current location onto a new stack named Stack2, and then changes the current location to the home directory, represented in the command by the tilde symbol (`~`), which when used on a FileSystem provider drives is equivalent to `$HOME` and `$env:USERPROFILE`.</span></span>

<span data-ttu-id="11680-127">Si Stack2 n’existe pas encore dans la session, le `Push-Location` crée.</span><span class="sxs-lookup"><span data-stu-id="11680-127">If Stack2 does not already exist in the session, `Push-Location` creates it.</span></span> <span data-ttu-id="11680-128">La deuxième commande utilise l' `Pop-Location` applet de commande pour dépiler l’emplacement d’origine ( `C:\` ) à partir de la pile Stack2.</span><span class="sxs-lookup"><span data-stu-id="11680-128">The second command uses the `Pop-Location` cmdlet to pop the original location (`C:\`) from the Stack2 stack.</span></span> <span data-ttu-id="11680-129">Sans le paramètre **StackName** , `Pop-Location` dépilerait l’emplacement de la pile par défaut sans nom.</span><span class="sxs-lookup"><span data-stu-id="11680-129">Without the **StackName** parameter, `Pop-Location` would pop the location from the unnamed default stack.</span></span>

<span data-ttu-id="11680-130">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="11680-130">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="11680-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="11680-131">PARAMETERS</span></span>

### <span data-ttu-id="11680-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="11680-132">-LiteralPath</span></span>

<span data-ttu-id="11680-133">Spécifie le chemin d'accès au nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="11680-133">Specifies the path to the new location.</span></span> <span data-ttu-id="11680-134">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="11680-134">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="11680-135">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="11680-135">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="11680-136">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="11680-136">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="11680-137">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="11680-137">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="11680-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="11680-138">-PassThru</span></span>

<span data-ttu-id="11680-139">Passe un objet représentant l'emplacement au pipeline.</span><span class="sxs-lookup"><span data-stu-id="11680-139">Passes an object representing the location to the pipeline.</span></span> <span data-ttu-id="11680-140">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="11680-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="11680-141">-Path</span><span class="sxs-lookup"><span data-stu-id="11680-141">-Path</span></span>

<span data-ttu-id="11680-142">Définit votre emplacement sur l'emplacement spécifié par ce chemin d'accès après avoir (ajouté) placé l'emplacement actuel au sommet de la pile.</span><span class="sxs-lookup"><span data-stu-id="11680-142">Changes your location to the location specified by this path after it adds (pushes) the current location onto the top of the stack.</span></span> <span data-ttu-id="11680-143">Entrez un chemin d'accès à n'importe quel emplacement dont le fournisseur prend en charge cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="11680-143">Enter a path to any location whose provider supports this cmdlet.</span></span> <span data-ttu-id="11680-144">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="11680-144">Wildcards are permitted.</span></span> <span data-ttu-id="11680-145">Le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="11680-145">The parameter name is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="11680-146">-StackName</span><span class="sxs-lookup"><span data-stu-id="11680-146">-StackName</span></span>

<span data-ttu-id="11680-147">Spécifie la pile d'emplacements à laquelle l'emplacement actuel est ajouté.</span><span class="sxs-lookup"><span data-stu-id="11680-147">Specifies the location stack to which the current location is added.</span></span> <span data-ttu-id="11680-148">Entrez un nom de pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="11680-148">Enter a location stack name.</span></span>
<span data-ttu-id="11680-149">Si la pile n’existe pas, la `Push-Location` crée.</span><span class="sxs-lookup"><span data-stu-id="11680-149">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="11680-150">Sans ce paramètre, `Push-Location` ajoute l’emplacement à la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="11680-150">Without this parameter, `Push-Location` adds the location to the current location stack.</span></span> <span data-ttu-id="11680-151">Par défaut, la pile d’emplacements active est la pile d’emplacements par défaut sans nom que PowerShell crée.</span><span class="sxs-lookup"><span data-stu-id="11680-151">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span>
<span data-ttu-id="11680-152">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-152">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="11680-153">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="11680-153">For more information about location stacks, see the [Notes](#notes).</span></span>

> [!NOTE]
> <span data-ttu-id="11680-154">`Push-Location` Impossible d’ajouter un emplacement à la pile par défaut sans nom, sauf s’il s’agit de la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="11680-154">`Push-Location` cannot add a location to the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="11680-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="11680-155">CommonParameters</span></span>

<span data-ttu-id="11680-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="11680-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="11680-157">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="11680-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="11680-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="11680-158">INPUTS</span></span>

### <span data-ttu-id="11680-159">System.String</span><span class="sxs-lookup"><span data-stu-id="11680-159">System.String</span></span>

<span data-ttu-id="11680-160">Vous pouvez diriger une chaîne qui contient un chemin d’accès (mais pas un chemin d’accès littéral) vers `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-160">You can pipe a string that contains a path (but not a literal path) to `Push-Location`.</span></span>

## <span data-ttu-id="11680-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="11680-161">OUTPUTS</span></span>

### <span data-ttu-id="11680-162">None ou System. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="11680-162">None or System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="11680-163">Quand vous utilisez le paramètre **PassThru** , `Push-Location` génère un objet **System. Management. Automation. PathInfo** qui représente l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="11680-163">When you use the **PassThru** parameter, `Push-Location` generates a **System.Management.Automation.PathInfo** object that represents the location.</span></span> <span data-ttu-id="11680-164">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="11680-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="11680-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="11680-165">NOTES</span></span>

<span data-ttu-id="11680-166">PowerShell prend en charge plusieurs instances d’exécution par processus.</span><span class="sxs-lookup"><span data-stu-id="11680-166">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="11680-167">Chaque instance d’exécution a son propre _répertoire actif_.</span><span class="sxs-lookup"><span data-stu-id="11680-167">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="11680-168">Ce n’est pas le même que `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="11680-168">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="11680-169">Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.</span><span class="sxs-lookup"><span data-stu-id="11680-169">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="11680-170">Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="11680-170">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="11680-171">Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="11680-171">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="11680-172">Une pile est une liste de dernier sorti, premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.</span><span class="sxs-lookup"><span data-stu-id="11680-172">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span>
<span data-ttu-id="11680-173">Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="11680-173">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="11680-174">PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="11680-174">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="11680-175">PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="11680-175">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="11680-176">Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="11680-176">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="11680-177">Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="11680-177">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="11680-178">Pour gérer les piles d’emplacements, utilisez les applets de commande PowerShell location, comme suit.</span><span class="sxs-lookup"><span data-stu-id="11680-178">To manage location stacks, use the PowerShell Location cmdlets, as follows.</span></span>

- <span data-ttu-id="11680-179">Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-179">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="11680-180">Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-180">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="11680-181">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-181">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="11680-182">Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-182">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="11680-183">Pour créer une nouvelle pile d’emplacements, utilisez le paramètre StackName de l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-183">To create a new location stack, use the StackName parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="11680-184">Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.</span><span class="sxs-lookup"><span data-stu-id="11680-184">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="11680-185">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre StackName de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="11680-185">To make a location stack the current location stack, use the StackName parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="11680-186">La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.</span><span class="sxs-lookup"><span data-stu-id="11680-186">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="11680-187">Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom.</span><span class="sxs-lookup"><span data-stu-id="11680-187">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="11680-188">Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="11680-188">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="11680-189">Vous pouvez également faire référence à `Push-Location` par son alias intégré, `pushd` .</span><span class="sxs-lookup"><span data-stu-id="11680-189">You can also refer to `Push-Location` by its built-in alias, `pushd`.</span></span> <span data-ttu-id="11680-190">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="11680-190">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="11680-191">L' `Push-Location` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="11680-191">The `Push-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="11680-192">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="11680-192">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="11680-193">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="11680-193">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="11680-194">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="11680-194">RELATED LINKS</span></span>

[<span data-ttu-id="11680-195">Get-Location</span><span class="sxs-lookup"><span data-stu-id="11680-195">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="11680-196">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="11680-196">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="11680-197">Set-Location</span><span class="sxs-lookup"><span data-stu-id="11680-197">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="11680-198">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="11680-198">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="11680-199">about_Providers</span><span class="sxs-lookup"><span data-stu-id="11680-199">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
