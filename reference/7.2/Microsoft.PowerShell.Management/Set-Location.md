---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: ec6f69d1d4a0b382ceec26b9409d01501edb814f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598173"
---
# <span data-ttu-id="48148-102">Set-Location</span><span class="sxs-lookup"><span data-stu-id="48148-102">Set-Location</span></span>

## <span data-ttu-id="48148-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="48148-103">SYNOPSIS</span></span>
<span data-ttu-id="48148-104">Définit l'emplacement de travail actif sur un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="48148-104">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="48148-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="48148-105">SYNTAX</span></span>

### <span data-ttu-id="48148-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="48148-106">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="48148-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="48148-107">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="48148-108">Pile</span><span class="sxs-lookup"><span data-stu-id="48148-108">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="48148-109">Description</span><span class="sxs-lookup"><span data-stu-id="48148-109">DESCRIPTION</span></span>

<span data-ttu-id="48148-110">L' `Set-Location` applet de commande définit l’emplacement de travail à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="48148-110">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="48148-111">Cet emplacement peut être un répertoire, un sous-répertoire, un emplacement du registre ou n’importe quel chemin d’accès du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="48148-111">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="48148-112">PowerShell 6,2 a ajouté la prise en charge de `-` et `+` en tant que valeurs pour le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="48148-112">PowerShell 6.2 added support for `-` and `+` as a values for the **Path** parameter.</span></span> <span data-ttu-id="48148-113">PowerShell conserve un historique des 20 derniers emplacements accessibles avec `-` et `+` .</span><span class="sxs-lookup"><span data-stu-id="48148-113">PowerShell maintains a history of the last 20 locations that can be accessed with `-` and `+`.</span></span> <span data-ttu-id="48148-114">Cette liste est indépendante de la pile d’emplacements accessible à l’aide du paramètre **StackName** .</span><span class="sxs-lookup"><span data-stu-id="48148-114">This list is independent from the location stack that is accessed using the **StackName** parameter.</span></span>

## <span data-ttu-id="48148-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="48148-115">EXAMPLES</span></span>

### <span data-ttu-id="48148-116">Exemple 1 : définir l’emplacement actuel</span><span class="sxs-lookup"><span data-stu-id="48148-116">Example 1: Set the current location</span></span>

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

<span data-ttu-id="48148-117">Cette commande définit l’emplacement actuel à la racine du `HKLM:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="48148-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="48148-118">Exemple 2 : définir l’emplacement actuel et afficher cet emplacement</span><span class="sxs-lookup"><span data-stu-id="48148-118">Example 2: Set the current location and display that location</span></span>

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="48148-119">Cette commande définit l’emplacement actuel à la racine du `Env:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="48148-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="48148-120">Elle utilise le paramètre **PassThru** pour indiquer à PowerShell de retourner un objet **PathInfo** qui représente l' `Env:\` emplacement.</span><span class="sxs-lookup"><span data-stu-id="48148-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="48148-121">Exemple 3 : définir l’emplacement actuel sur le lecteur C :</span><span class="sxs-lookup"><span data-stu-id="48148-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="48148-122">La première commande définit l’emplacement à la racine du `HKLM:` lecteur dans le fournisseur de registre.</span><span class="sxs-lookup"><span data-stu-id="48148-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="48148-123">La deuxième commande définit l’emplacement à l’emplacement actuel du `C:` lecteur dans le fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="48148-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="48148-124">Lorsque le nom du lecteur est spécifié sous la forme `<DriveName>:` (sans barre oblique inverse), l’applet de commande définit l’emplacement à l’emplacement actuel dans le PSDrive.</span><span class="sxs-lookup"><span data-stu-id="48148-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="48148-125">Pour accéder à l’emplacement actuel dans la commande PSDrive use `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="48148-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="48148-126">Exemple 4 : définir l’emplacement actuel sur une pile nommée</span><span class="sxs-lookup"><span data-stu-id="48148-126">Example 4: Set the current location to a named stack</span></span>

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="48148-127">La première commande ajoute l’emplacement actuel à la pile de chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="48148-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="48148-128">La deuxième commande permet à l’emplacement des chemins d’accès de la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="48148-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="48148-129">La troisième commande affiche les emplacements dans la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="48148-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="48148-130">Les `*-Location` applets de commande utilisent la pile d’emplacements active, sauf si une pile d’emplacements différente est spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="48148-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="48148-131">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="48148-131">For information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="48148-132">Exemple 5 : naviguer dans l’historique des emplacements à l’aide `+` de ou `-`</span><span class="sxs-lookup"><span data-stu-id="48148-132">Example 5: Navigate location history using `+` or `-`</span></span>

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

<span data-ttu-id="48148-133">À l’aide de l’alias, `cd -` ou `cd +` est un moyen simple de naviguer dans votre historique d’emplacement dans votre terminal.</span><span class="sxs-lookup"><span data-stu-id="48148-133">Using the alias, `cd -` or `cd +` is an easy way to navigate through your location history while in your terminal.</span></span> <span data-ttu-id="48148-134">Pour plus d’informations sur la navigation dans `-` / `+` , consultez le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="48148-134">For more information on navigating with `-`/`+`, see the **Path** parameter.</span></span>

## <span data-ttu-id="48148-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="48148-135">PARAMETERS</span></span>

### <span data-ttu-id="48148-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="48148-136">-LiteralPath</span></span>

<span data-ttu-id="48148-137">Spécifie le chemin d’accès de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="48148-137">Specifies a path of the location.</span></span> <span data-ttu-id="48148-138">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="48148-138">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="48148-139">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="48148-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="48148-140">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="48148-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="48148-141">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="48148-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="48148-142">-PassThru</span><span class="sxs-lookup"><span data-stu-id="48148-142">-PassThru</span></span>

<span data-ttu-id="48148-143">Retourne un objet **PathInfo** qui représente l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="48148-143">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="48148-144">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="48148-144">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="48148-145">-Path</span><span class="sxs-lookup"><span data-stu-id="48148-145">-Path</span></span>

<span data-ttu-id="48148-146">Spécifiez le chemin d’accès d’un nouvel emplacement de travail.</span><span class="sxs-lookup"><span data-stu-id="48148-146">Specify the path of a new working location.</span></span> <span data-ttu-id="48148-147">Si aucun chemin d’accès n’est fourni, `Set-Location` le répertoire de démarrage de l’utilisateur actuel est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="48148-147">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="48148-148">Lorsque des caractères génériques sont utilisés, l’applet de commande choisit le premier chemin d’accès qui correspond au modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="48148-148">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

<span data-ttu-id="48148-149">PowerShell conserve un historique des 20 derniers emplacements que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="48148-149">PowerShell keeps a history of the last 20 locations you have set.</span></span> <span data-ttu-id="48148-150">Si la valeur du paramètre **path** est le `-` caractère, le nouvel emplacement de travail sera l’emplacement de travail précédent dans l’historique (s’il existe).</span><span class="sxs-lookup"><span data-stu-id="48148-150">If the **Path** parameter value is the `-` character, then the new working location will be the previous working location in history (if it exists).</span></span> <span data-ttu-id="48148-151">De même, si la valeur est le `+` caractère, le nouvel emplacement de travail sera l’emplacement de travail suivant dans l’historique (s’il existe).</span><span class="sxs-lookup"><span data-stu-id="48148-151">Similarly, if the value is the `+` character, then the new working location will be the next working location in history (if it exists).</span></span> <span data-ttu-id="48148-152">Cette approche est similaire à l’utilisation de et, à `Pop-Location` `Push-Location` la différence près que l’historique est une liste, et non une pile, et qu’elle est suivie implicitement, et non pas manuellement.</span><span class="sxs-lookup"><span data-stu-id="48148-152">This is similar to using `Pop-Location` and `Push-Location` except that the history is a list, not a stack, and is implicitly tracked, not manually controlled.</span></span> <span data-ttu-id="48148-153">Actuellement, il n’existe aucun moyen d’afficher la liste de l’historique.</span><span class="sxs-lookup"><span data-stu-id="48148-153">Currently, there is no way to view the history list.</span></span>

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

### <span data-ttu-id="48148-154">-StackName</span><span class="sxs-lookup"><span data-stu-id="48148-154">-StackName</span></span>

<span data-ttu-id="48148-155">Spécifie le nom existant de la pile d’emplacements que cette applet de commande établit avec la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="48148-155">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="48148-156">Entrez un nom de pile d'emplacements.</span><span class="sxs-lookup"><span data-stu-id="48148-156">Enter a location stack name.</span></span> <span data-ttu-id="48148-157">Pour indiquer la pile d’emplacements par défaut sans nom, tapez `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="48148-157">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="48148-158">Les `*-Location` applets de commande agissent sur la pile active, sauf si vous utilisez le paramètre **StackName** pour spécifier une autre pile.</span><span class="sxs-lookup"><span data-stu-id="48148-158">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span> <span data-ttu-id="48148-159">Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).</span><span class="sxs-lookup"><span data-stu-id="48148-159">For more information about location stacks, see the [Notes](#notes).</span></span>

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

### <span data-ttu-id="48148-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48148-160">CommonParameters</span></span>

<span data-ttu-id="48148-161">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48148-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48148-162">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="48148-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48148-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="48148-163">INPUTS</span></span>

### <span data-ttu-id="48148-164">System.String</span><span class="sxs-lookup"><span data-stu-id="48148-164">System.String</span></span>

<span data-ttu-id="48148-165">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="48148-165">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="48148-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="48148-166">OUTPUTS</span></span>

### <span data-ttu-id="48148-167">Aucun, System. Management. Automation. PathInfo, System. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="48148-167">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="48148-168">Cette applet de commande ne génère pas de sortie, sauf si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="48148-168">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="48148-169">L’utilisation de **PassThru** avec **path** ou **LiteralPath** génère un objet **PathInfo** qui représente le nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="48148-169">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="48148-170">L’utilisation de **PassThru** avec **StackName** génère un objet **PathInfoStack** qui représente le nouveau contexte de pile.</span><span class="sxs-lookup"><span data-stu-id="48148-170">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="48148-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="48148-171">NOTES</span></span>

<span data-ttu-id="48148-172">PowerShell prend en charge plusieurs instances d’exécution par processus.</span><span class="sxs-lookup"><span data-stu-id="48148-172">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="48148-173">Chaque instance d’exécution a son propre _répertoire actif_.</span><span class="sxs-lookup"><span data-stu-id="48148-173">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="48148-174">Ce n’est pas le même que `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="48148-174">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="48148-175">Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.</span><span class="sxs-lookup"><span data-stu-id="48148-175">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="48148-176">Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="48148-176">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="48148-177">Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="48148-177">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="48148-178">L' `Set-Location` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="48148-178">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="48148-179">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="48148-179">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="48148-180">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="48148-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="48148-181">Une pile est une liste de dernier et premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.</span><span class="sxs-lookup"><span data-stu-id="48148-181">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="48148-182">Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="48148-182">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="48148-183">PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="48148-183">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="48148-184">PowerShell crée une pile d’emplacements par défaut sans nom.</span><span class="sxs-lookup"><span data-stu-id="48148-184">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="48148-185">Vous pouvez créer plusieurs piles d’emplacements nommées.</span><span class="sxs-lookup"><span data-stu-id="48148-185">You can create multiple named location stacks.</span></span> <span data-ttu-id="48148-186">Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="48148-186">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="48148-187">Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.</span><span class="sxs-lookup"><span data-stu-id="48148-187">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="48148-188">Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="48148-188">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="48148-189">Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="48148-189">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="48148-190">Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="48148-190">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="48148-191">Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="48148-191">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="48148-192">Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="48148-192">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="48148-193">Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="48148-193">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="48148-194">Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.</span><span class="sxs-lookup"><span data-stu-id="48148-194">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="48148-195">Pour faire d’une pile d’emplacements la pile d’emplacements active, utilisez le paramètre **StackName** de `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="48148-195">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="48148-196">La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.</span><span class="sxs-lookup"><span data-stu-id="48148-196">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="48148-197">Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom.</span><span class="sxs-lookup"><span data-stu-id="48148-197">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="48148-198">Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="48148-198">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="48148-199">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="48148-199">RELATED LINKS</span></span>

[<span data-ttu-id="48148-200">Get-Location</span><span class="sxs-lookup"><span data-stu-id="48148-200">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="48148-201">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="48148-201">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="48148-202">Push-Location</span><span class="sxs-lookup"><span data-stu-id="48148-202">Push-Location</span></span>](Push-Location.md)

