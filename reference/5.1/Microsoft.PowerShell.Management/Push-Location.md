---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: abc40f3ae388a915c9df42d0c2df24f848e45e73
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205878"
---
# <span data-ttu-id="c0669-103">Push-Location</span><span class="sxs-lookup"><span data-stu-id="c0669-103">Push-Location</span></span>

## <span data-ttu-id="c0669-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c0669-104">SYNOPSIS</span></span>
<span data-ttu-id="c0669-105">Ajoute l'emplacement actuel au sommet d'une liste d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0669-105">Adds the current location to the top of a location stack.</span></span>

## <span data-ttu-id="c0669-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0669-106">SYNTAX</span></span>

### <span data-ttu-id="c0669-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c0669-107">Path (Default)</span></span>

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="c0669-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0669-108">LiteralPath</span></span>

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="c0669-109">Description</span><span class="sxs-lookup"><span data-stu-id="c0669-109">DESCRIPTION</span></span>

<span data-ttu-id="c0669-110">L' `Push-Location` applet de commande ajoute (« push ») l’emplacement actuel sur une pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0669-110">The `Push-Location` cmdlet adds ("pushes") the current location onto a location stack.</span></span> <span data-ttu-id="c0669-111">Si vous spécifiez un chemin d’accès, `Push-Location` exécute un push de l’emplacement actuel sur une pile d’emplacements, puis modifie l’emplacement actuel à l’emplacement spécifié par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="c0669-111">If you specify a path, `Push-Location` pushes the current location onto a location stack and then changes the current location to the location specified by the path.</span></span> <span data-ttu-id="c0669-112">Vous pouvez utiliser l' `Pop-Location` applet de commande pour récupérer les emplacements de la pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0669-112">You can use the `Pop-Location` cmdlet to get locations from the location stack.</span></span>

<span data-ttu-id="c0669-113">Par défaut, l' `Push-Location` applet de commande exécute un push de l’emplacement actuel dans la pile d’emplacements active, mais vous pouvez utiliser le paramètre **StackName** pour spécifier une autre pile d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0669-113">By default, the `Push-Location` cmdlet pushes the current location onto the current location stack, but you can use the **StackName** parameter to specify an alternate location stack.</span></span> <span data-ttu-id="c0669-114">Si la pile n’existe pas, la `Push-Location` crée.</span><span class="sxs-lookup"><span data-stu-id="c0669-114">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="c0669-115">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="c0669-115">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="c0669-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c0669-116">EXAMPLES</span></span>

### <span data-ttu-id="c0669-117">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="c0669-117">Example 1</span></span>

<span data-ttu-id="c0669-118">Cet exemple exécute un push de l’emplacement actuel dans la pile d’emplacements par défaut, puis modifie l’emplacement en `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="c0669-118">This example pushes the current location onto the default location stack and then changes the location to `C:\Windows`.</span></span>

```
PS C:\> Push-Location C:\Windows
```

### <span data-ttu-id="c0669-119">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="c0669-119">Example 2</span></span>

<span data-ttu-id="c0669-120">Cet exemple exécute un push de l’emplacement actuel dans la pile RegFunction, puis et modifie l’emplacement actuel à l' `HKLM:\Software\Policies` emplacement.</span><span class="sxs-lookup"><span data-stu-id="c0669-120">This example pushes the current location onto the RegFunction stack and changes the current location to the `HKLM:\Software\Policies` location.</span></span>

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

<span data-ttu-id="c0669-121">Vous pouvez utiliser les applets de commande location dans n’importe quel lecteur PowerShell (PSDrive).</span><span class="sxs-lookup"><span data-stu-id="c0669-121">You can use the Location cmdlets in any PowerShell drive (PSDrive).</span></span>

### <span data-ttu-id="c0669-122">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="c0669-122">Example 3</span></span>

<span data-ttu-id="c0669-123">Cette commande place l'emplacement actuel sur la pile par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0669-123">This command pushes the current location onto the default stack.</span></span> <span data-ttu-id="c0669-124">Elle ne modifie pas l'emplacement.</span><span class="sxs-lookup"><span data-stu-id="c0669-124">It does not change the location.</span></span>

```
PS C:\> Push-Location
```

### <span data-ttu-id="c0669-125">Exemple 4 : créer et utiliser une pile nommée</span><span class="sxs-lookup"><span data-stu-id="c0669-125">Example 4 - Create and use a named stack</span></span>

<span data-ttu-id="c0669-126">Ces commandes indiquent comment créer et utiliser une pile d'emplacement nommée.</span><span class="sxs-lookup"><span data-stu-id="c0669-126">These commands show how to create and use a named location stack.</span></span>

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

<span data-ttu-id="c0669-127">La première commande place l’emplacement actuel sur une nouvelle pile nommée Stack2, puis modifie l’emplacement actuel dans le répertoire de départ, représenté dans la commande par le symbole de tilde ( `~` ), qui, lorsqu’il est utilisé sur un lecteur de fournisseur FileSystem, est équivalent à `$HOME` et `$env:USERPROFILE` .</span><span class="sxs-lookup"><span data-stu-id="c0669-127">The first command pushes the current location onto a new stack named Stack2, and then changes the current location to the home directory, represented in the command by the tilde symbol (`~`), which when used on a FileSystem provider drives is equivalent to `$HOME` and `$env:USERPROFILE`.</span></span>

<span data-ttu-id="c0669-128">Si Stack2 n’existe pas encore dans la session, le `Push-Location` crée.</span><span class="sxs-lookup"><span data-stu-id="c0669-128">If Stack2 does not already exist in the session, `Push-Location` creates it.</span></span> <span data-ttu-id="c0669-129">La deuxième commande utilise l' `Pop-Location` applet de commande pour dépiler l’emplacement d’origine ( `C:\` ) à partir de la pile Stack2.</span><span class="sxs-lookup"><span data-stu-id="c0669-129">The second command uses the `Pop-Location` cmdlet to pop the original location (`C:\`) from the Stack2 stack.</span></span> <span data-ttu-id="c0669-130">Sans le paramètre **StackName** , `Pop-Location` dépilerait l’emplacement de la pile par défaut sans nom.</span><span class="sxs-lookup"><span data-stu-id="c0669-130">Without the **StackName** parameter, `Pop-Location` would pop the location from the unnamed default stack.</span></span>

<span data-ttu-id="c0669-131">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="c0669-131">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="c0669-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0669-132">PARAMETERS</span></span>

### <span data-ttu-id="c0669-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0669-133">-LiteralPath</span></span>

<span data-ttu-id="c0669-134">Spécifie le chemin d'accès au nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="c0669-134">Specifies the path to the new location.</span></span> <span data-ttu-id="c0669-135">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="c0669-135">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="c0669-136">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="c0669-136">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c0669-137">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="c0669-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c0669-138">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="c0669-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c0669-139">-PassThru</span><span class="sxs-lookup"><span data-stu-id="c0669-139">-PassThru</span></span>

<span data-ttu-id="c0669-140">Passe un objet représentant l'emplacement au pipeline.</span><span class="sxs-lookup"><span data-stu-id="c0669-140">Passes an object representing the location to the pipeline.</span></span> <span data-ttu-id="c0669-141">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="c0669-141">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c0669-142">-Path</span><span class="sxs-lookup"><span data-stu-id="c0669-142">-Path</span></span>

<span data-ttu-id="c0669-143">Définit votre emplacement sur l'emplacement spécifié par ce chemin d'accès après avoir (ajouté) placé l'emplacement actuel au sommet de la pile.</span><span class="sxs-lookup"><span data-stu-id="c0669-143">Changes your location to the location specified by this path after it adds (pushes) the current location onto the top of the stack.</span></span> <span data-ttu-id="c0669-144">Entrez un chemin d'accès à n'importe quel emplacement dont le fournisseur prend en charge cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c0669-144">Enter a path to any location whose provider supports this cmdlet.</span></span> <span data-ttu-id="c0669-145">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c0669-145">Wildcards are permitted.</span></span> <span data-ttu-id="c0669-146">Le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c0669-146">The parameter name is optional.</span></span>

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

### <span data-ttu-id="c0669-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="c0669-147">-StackName</span></span>

<span data-ttu-id="c0669-148">Spécifie la pile d'emplacements à laquelle l'emplacement actuel est ajouté.</span><span class="sxs-lookup"><span data-stu-id="c0669-148">Specifies the location stack to which the current location is added.</span></span> <span data-ttu-id="c0669-149">Entrez un nom de pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0669-149">Enter a location stack name.</span></span>
<span data-ttu-id="c0669-150">Si la pile n’existe pas, la `Push-Location` crée.</span><span class="sxs-lookup"><span data-stu-id="c0669-150">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="c0669-151">Sans ce paramètre, `Push-Location` ajoute l’emplacement à la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="c0669-151">Without this parameter, `Push-Location` adds the location to the current location stack.</span></span> <span data-ttu-id="c0669-152">Par défaut, la pile d’emplacements active est la pile d’emplacements par défaut sans nom que PowerShell crée.</span><span class="sxs-lookup"><span data-stu-id="c0669-152">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span>
<span data-ttu-id="c0669-153">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-153">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="c0669-154">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="c0669-154">For more information about location stacks, see the [Notes](#notes).</span></span>

> [!NOTE]
> <span data-ttu-id="c0669-155">`Push-Location` Impossible d’ajouter un emplacement à la pile par défaut sans nom, sauf s’il s’agit de la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="c0669-155">`Push-Location` cannot add a location to the unnamed default stack unless it is the current location stack.</span></span>

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

### <span data-ttu-id="c0669-156">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="c0669-156">-UseTransaction</span></span>

<span data-ttu-id="c0669-157">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="c0669-157">Includes the command in the active transaction.</span></span> <span data-ttu-id="c0669-158">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="c0669-158">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="c0669-159">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_transactions.md).</span><span class="sxs-lookup"><span data-stu-id="c0669-159">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0669-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0669-160">CommonParameters</span></span>

<span data-ttu-id="c0669-161">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0669-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0669-162">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c0669-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0669-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c0669-163">INPUTS</span></span>

### <span data-ttu-id="c0669-164">System.String</span><span class="sxs-lookup"><span data-stu-id="c0669-164">System.String</span></span>

<span data-ttu-id="c0669-165">Vous pouvez diriger une chaîne qui contient un chemin d’accès (mais pas un chemin d’accès littéral) vers `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-165">You can pipe a string that contains a path (but not a literal path) to `Push-Location`.</span></span>

## <span data-ttu-id="c0669-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c0669-166">OUTPUTS</span></span>

### <span data-ttu-id="c0669-167">None ou System. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="c0669-167">None or System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="c0669-168">Quand vous utilisez le paramètre **PassThru** , `Push-Location` génère un objet **System. Management. Automation. PathInfo** qui représente l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="c0669-168">When you use the **PassThru** parameter, `Push-Location` generates a **System.Management.Automation.PathInfo** object that represents the location.</span></span> <span data-ttu-id="c0669-169">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c0669-169">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c0669-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c0669-170">NOTES</span></span>

<span data-ttu-id="c0669-171">PowerShell prend en charge plusieurs instances d’exécution par processus.</span><span class="sxs-lookup"><span data-stu-id="c0669-171">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="c0669-172">Chaque instance d’exécution a son propre _répertoire actif_ .</span><span class="sxs-lookup"><span data-stu-id="c0669-172">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="c0669-173">Ce n’est pas le même que `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="c0669-173">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="c0669-174">Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.</span><span class="sxs-lookup"><span data-stu-id="c0669-174">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="c0669-175">Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="c0669-175">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="c0669-176">Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="c0669-176">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="c0669-177">Une pile est une liste de dernier sorti, premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.</span><span class="sxs-lookup"><span data-stu-id="c0669-177">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span>
<span data-ttu-id="c0669-178">Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="c0669-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="c0669-179">PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0669-179">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="c0669-180">PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="c0669-180">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="c0669-181">Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="c0669-181">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="c0669-182">Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="c0669-182">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="c0669-183">Pour gérer les piles d’emplacements, utilisez les applets de commande PowerShell location, comme suit.</span><span class="sxs-lookup"><span data-stu-id="c0669-183">To manage location stacks, use the PowerShell Location cmdlets, as follows.</span></span>

- <span data-ttu-id="c0669-184">Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-184">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="c0669-185">Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-185">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="c0669-186">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-186">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="c0669-187">Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-187">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="c0669-188">Pour créer une nouvelle pile d’emplacements, utilisez le paramètre StackName de l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-188">To create a new location stack, use the StackName parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="c0669-189">Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.</span><span class="sxs-lookup"><span data-stu-id="c0669-189">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="c0669-190">Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre StackName de l’applet de commande `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="c0669-190">To make a location stack the current location stack, use the StackName parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="c0669-191">La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.</span><span class="sxs-lookup"><span data-stu-id="c0669-191">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="c0669-192">Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom.</span><span class="sxs-lookup"><span data-stu-id="c0669-192">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="c0669-193">Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="c0669-193">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="c0669-194">Vous pouvez également faire référence à `Push-Location` par son alias intégré, `pushd` .</span><span class="sxs-lookup"><span data-stu-id="c0669-194">You can also refer to `Push-Location` by its built-in alias, `pushd`.</span></span> <span data-ttu-id="c0669-195">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="c0669-195">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="c0669-196">L' `Push-Location` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c0669-196">The `Push-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c0669-197">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="c0669-197">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="c0669-198">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="c0669-198">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c0669-199">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c0669-199">RELATED LINKS</span></span>

[<span data-ttu-id="c0669-200">Get-Location</span><span class="sxs-lookup"><span data-stu-id="c0669-200">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="c0669-201">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="c0669-201">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="c0669-202">Set-Location</span><span class="sxs-lookup"><span data-stu-id="c0669-202">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="c0669-203">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="c0669-203">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="c0669-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c0669-204">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
