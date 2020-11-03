---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 06b1596366c9c9e20857b55aa9a17342bab07028
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206062"
---
# <span data-ttu-id="0a8ff-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="0a8ff-103">Set-Location</span></span>

## <span data-ttu-id="0a8ff-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0a8ff-104">SYNOPSIS</span></span>
<span data-ttu-id="0a8ff-105">Définit l'emplacement de travail actif sur un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="0a8ff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a8ff-106">SYNTAX</span></span>

### <span data-ttu-id="0a8ff-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0a8ff-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="0a8ff-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0a8ff-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="0a8ff-109">Pile</span><span class="sxs-lookup"><span data-stu-id="0a8ff-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="0a8ff-110">Description</span><span class="sxs-lookup"><span data-stu-id="0a8ff-110">DESCRIPTION</span></span>

<span data-ttu-id="0a8ff-111">L' `Set-Location` applet de commande définit l’emplacement de travail à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="0a8ff-112">Cet emplacement peut être un répertoire, un sous-répertoire, un emplacement du registre ou n’importe quel chemin d’accès du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="0a8ff-113">Vous pouvez également utiliser le paramètre **StackName** pour faire d’une pile d’emplacements nommée la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-113">You can also use the **StackName** parameter to make a named location stack the current location stack.</span></span> <span data-ttu-id="0a8ff-114">Pour plus d'informations sur les piles d'emplacements, consultez les remarques.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-114">For more information about location stacks, see the Notes.</span></span>

## <span data-ttu-id="0a8ff-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0a8ff-115">EXAMPLES</span></span>

### <span data-ttu-id="0a8ff-116">Exemple 1 : définir l’emplacement actuel</span><span class="sxs-lookup"><span data-stu-id="0a8ff-116">Example 1: Set the current location</span></span>

```powershell
PS C:\> Set-Location -Path "HKLM:\"
```

```output
PS HKLM:\>
```

<span data-ttu-id="0a8ff-117">Cette commande définit l’emplacement actuel à la racine du `HKLM:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="0a8ff-118">Exemple 2 : définir l’emplacement actuel et afficher cet emplacement</span><span class="sxs-lookup"><span data-stu-id="0a8ff-118">Example 2: Set the current location and display that location</span></span>

```powershell
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="0a8ff-119">Cette commande définit l’emplacement actuel à la racine du `Env:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="0a8ff-120">Elle utilise le paramètre **PassThru** pour indiquer à PowerShell de retourner un objet **PathInfo** qui représente l' `Env:\` emplacement.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="0a8ff-121">Exemple 3 : définir l’emplacement actuel sur le lecteur C :</span><span class="sxs-lookup"><span data-stu-id="0a8ff-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="0a8ff-122">La première commande définit l’emplacement à la racine du `HKLM:` lecteur dans le fournisseur de registre.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="0a8ff-123">La deuxième commande définit l’emplacement à l’emplacement actuel du `C:` lecteur dans le fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="0a8ff-124">Lorsque le nom du lecteur est spécifié sous la forme `<DriveName>:` (sans barre oblique inverse), l’applet de commande définit l’emplacement à l’emplacement actuel dans le PSDrive.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="0a8ff-125">Pour accéder à l’emplacement actuel dans la commande PSDrive use `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="0a8ff-126">Exemple 4 : définir l’emplacement actuel sur une pile nommée</span><span class="sxs-lookup"><span data-stu-id="0a8ff-126">Example 4: Set the current location to a named stack</span></span>

```powershell
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="0a8ff-127">La première commande ajoute l’emplacement actuel à la pile de chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="0a8ff-128">La deuxième commande permet à l’emplacement des chemins d’accès de la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="0a8ff-129">La troisième commande affiche les emplacements dans la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="0a8ff-130">Les `*-Location` applets de commande utilisent la pile d’emplacements active, sauf si une pile d’emplacements différente est spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="0a8ff-131">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="0a8ff-131">For information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="0a8ff-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a8ff-132">PARAMETERS</span></span>

### <span data-ttu-id="0a8ff-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0a8ff-133">-LiteralPath</span></span>

<span data-ttu-id="0a8ff-134">Spécifie le chemin d’accès de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-134">Specifies a path of the location.</span></span> <span data-ttu-id="0a8ff-135">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-135">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="0a8ff-136">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="0a8ff-137">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0a8ff-138">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="0a8ff-139">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-139">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0a8ff-140">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0a8ff-140">-PassThru</span></span>

<span data-ttu-id="0a8ff-141">Retourne un objet **PathInfo** qui représente l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-141">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="0a8ff-142">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="0a8ff-143">-Path</span><span class="sxs-lookup"><span data-stu-id="0a8ff-143">-Path</span></span>

<span data-ttu-id="0a8ff-144">Spécifiez le chemin d’accès d’un nouvel emplacement de travail.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-144">Specify the path of a new working location.</span></span> <span data-ttu-id="0a8ff-145">Si aucun chemin d’accès n’est fourni, `Set-Location` le répertoire de démarrage de l’utilisateur actuel est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-145">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="0a8ff-146">Lorsque des caractères génériques sont utilisés, l’applet de commande choisit le premier chemin d’accès qui correspond au modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-146">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0a8ff-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="0a8ff-147">-StackName</span></span>

<span data-ttu-id="0a8ff-148">Spécifie le nom existant de la pile d’emplacements que cette applet de commande établit avec la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-148">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="0a8ff-149">Entrez un nom de pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-149">Enter a location stack name.</span></span> <span data-ttu-id="0a8ff-150">Pour indiquer la pile d’emplacements par défaut sans nom, tapez `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="0a8ff-150">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="0a8ff-151">Les `*-Location` applets de commande agissent sur la pile active, sauf si vous utilisez le paramètre **StackName** pour spécifier une autre pile.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-151">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span>

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0a8ff-152">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="0a8ff-152">-UseTransaction</span></span>

<span data-ttu-id="0a8ff-153">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-153">Includes the command in the active transaction.</span></span>
<span data-ttu-id="0a8ff-154">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-154">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="0a8ff-155">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-155">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="0a8ff-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a8ff-156">CommonParameters</span></span>

<span data-ttu-id="0a8ff-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a8ff-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0a8ff-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a8ff-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0a8ff-159">INPUTS</span></span>

### <span data-ttu-id="0a8ff-160">System.String</span><span class="sxs-lookup"><span data-stu-id="0a8ff-160">System.String</span></span>

<span data-ttu-id="0a8ff-161">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-161">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="0a8ff-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0a8ff-162">OUTPUTS</span></span>

### <span data-ttu-id="0a8ff-163">Aucun, System. Management. Automation. PathInfo, System. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="0a8ff-163">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="0a8ff-164">Cette applet de commande ne génère pas de sortie, sauf si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-164">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="0a8ff-165">L’utilisation de **PassThru** avec **path** ou **LiteralPath** génère un objet **PathInfo** qui représente le nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-165">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="0a8ff-166">L’utilisation de **PassThru** avec **StackName** génère un objet **PathInfoStack** qui représente le nouveau contexte de pile.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-166">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="0a8ff-167">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0a8ff-167">NOTES</span></span>

<span data-ttu-id="0a8ff-168">PowerShell prend en charge plusieurs instances d’exécution par processus.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-168">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="0a8ff-169">Chaque instance d’exécution a son propre _répertoire actif_ .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-169">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="0a8ff-170">Ce n’est pas le même que `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-170">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="0a8ff-171">Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-171">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="0a8ff-172">Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-172">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="0a8ff-173">Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-173">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="0a8ff-174">L' `Set-Location` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-174">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0a8ff-175">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="0a8ff-176">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0a8ff-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="0a8ff-177">Une pile est une liste de dernier et premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-177">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="0a8ff-178">Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="0a8ff-179">PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-179">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="0a8ff-180">PowerShell crée une pile d’emplacements par défaut sans nom.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-180">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="0a8ff-181">Vous pouvez créer plusieurs piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-181">You can create multiple named location stacks.</span></span> <span data-ttu-id="0a8ff-182">Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-182">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="0a8ff-183">Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-183">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="0a8ff-184">Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="0a8ff-184">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="0a8ff-185">Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-185">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="0a8ff-186">Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-186">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="0a8ff-187">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-187">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="0a8ff-188">Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-188">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="0a8ff-189">Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-189">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="0a8ff-190">Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-190">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="0a8ff-191">Pour faire d’une pile d’emplacements la pile d’emplacements active, utilisez le paramètre **StackName** de `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="0a8ff-191">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="0a8ff-192">La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-192">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="0a8ff-193">Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom.</span><span class="sxs-lookup"><span data-stu-id="0a8ff-193">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="0a8ff-194">Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="0a8ff-194">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="0a8ff-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0a8ff-195">RELATED LINKS</span></span>

[<span data-ttu-id="0a8ff-196">Get-Location</span><span class="sxs-lookup"><span data-stu-id="0a8ff-196">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="0a8ff-197">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="0a8ff-197">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="0a8ff-198">Push-Location</span><span class="sxs-lookup"><span data-stu-id="0a8ff-198">Push-Location</span></span>](Push-Location.md)
