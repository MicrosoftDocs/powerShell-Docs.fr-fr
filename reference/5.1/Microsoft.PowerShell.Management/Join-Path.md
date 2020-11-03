---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: bcba432fb52b327695b61a4475d4a93903a688a5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203621"
---
# <span data-ttu-id="3cd22-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="3cd22-103">Join-Path</span></span>

## <span data-ttu-id="3cd22-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3cd22-104">SYNOPSIS</span></span>
<span data-ttu-id="3cd22-105">Combine un chemin d’accès et un chemin d’accès d’enfant en un seul chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cd22-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="3cd22-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3cd22-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="3cd22-107">Description</span><span class="sxs-lookup"><span data-stu-id="3cd22-107">DESCRIPTION</span></span>

<span data-ttu-id="3cd22-108">L’applet de commande combine un chemin d’accès et un chemin d’accès `Join-Path` enfant dans un chemin d’accès unique.</span><span class="sxs-lookup"><span data-stu-id="3cd22-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="3cd22-109">Le fournisseur fournit les séparateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cd22-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="3cd22-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3cd22-110">EXAMPLES</span></span>

### <span data-ttu-id="3cd22-111">Exemple 1 : combiner un chemin d’accès avec un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="3cd22-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="3cd22-112">Cette commande utilise `Join-Path` pour combiner un chemin d’accès à un childpath.</span><span class="sxs-lookup"><span data-stu-id="3cd22-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="3cd22-113">Étant donné que la commande est exécutée à partir du `FileSystem` fournisseur, elle fournit le `\` délimiteur pour joindre les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cd22-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="3cd22-114">Exemple 2 : combiner des chemins qui contiennent déjà des séparateurs de répertoire</span><span class="sxs-lookup"><span data-stu-id="3cd22-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="3cd22-115">Séparateurs de répertoire existants `\` et gérés pour qu’il n’y ait qu’un seul séparateur entre `Path` et `ChildPath`</span><span class="sxs-lookup"><span data-stu-id="3cd22-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="3cd22-116">Exemple 3 : afficher des fichiers et des dossiers en joignant un chemin d’accès à un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="3cd22-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="3cd22-117">Cette commande affiche les fichiers et les dossiers qui sont référencés en joignant le \* chemin d’accès C:\win et le \* chemin d’accès enfant système.</span><span class="sxs-lookup"><span data-stu-id="3cd22-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="3cd22-118">Elle affiche les mêmes fichiers et dossiers que `Get-ChildItem` , mais elle affiche le chemin d’accès complet à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3cd22-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="3cd22-119">Dans cette commande, les `Path` `ChildPath` noms de paramètres facultatifs et sont omis.</span><span class="sxs-lookup"><span data-stu-id="3cd22-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="3cd22-120">Exemple 4 : utiliser Join-Path avec le fournisseur de Registre PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cd22-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="3cd22-121">Cette commande affiche les clés de Registre dans la `HKLM\System` sous-clé de Registre qui inclut `ControlSet` .</span><span class="sxs-lookup"><span data-stu-id="3cd22-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="3cd22-122">Le `Resolve` paramètre tente de résoudre le chemin d’accès joint, y compris les caractères génériques du chemin d’accès du fournisseur actuel `HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="3cd22-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="3cd22-123">Exemple 5 : combiner plusieurs racines de chemin d’accès avec un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="3cd22-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="3cd22-124">Cette commande utilise `Join-Path` pour combiner plusieurs racines de chemin d’accès avec un chemin d’accès enfant.</span><span class="sxs-lookup"><span data-stu-id="3cd22-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="3cd22-125">Les lecteurs spécifiés par `Path` doivent exister ou la jointure de cette entrée échouera.</span><span class="sxs-lookup"><span data-stu-id="3cd22-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="3cd22-126">Exemple 6 : combiner les racines d’un lecteur du système de fichiers avec un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="3cd22-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="3cd22-127">Cette commande combine les racines de chaque lecteur du système de fichiers PowerShell dans la console avec le chemin d’accès enfant subdir.</span><span class="sxs-lookup"><span data-stu-id="3cd22-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="3cd22-128">La commande utilise l' `Get-PSDrive` applet de commande pour récupérer les lecteurs PowerShell pris en charge par le fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="3cd22-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="3cd22-129">L' `ForEach-Object` instruction sélectionne uniquement la propriété racine des `PSDriveInfo` objets et la combine avec le chemin d’accès enfant spécifié.</span><span class="sxs-lookup"><span data-stu-id="3cd22-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="3cd22-130">La sortie indique que les lecteurs PowerShell sur l’ordinateur incluaient un lecteur mappé au répertoire C:\Program Files.</span><span class="sxs-lookup"><span data-stu-id="3cd22-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

## <span data-ttu-id="3cd22-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3cd22-131">PARAMETERS</span></span>

### <span data-ttu-id="3cd22-132">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="3cd22-132">-ChildPath</span></span>

<span data-ttu-id="3cd22-133">Spécifie les éléments à ajouter à la valeur du `Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3cd22-133">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="3cd22-134">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="3cd22-134">Wildcards are permitted.</span></span>
<span data-ttu-id="3cd22-135">Le `ChildPath` paramètre est obligatoire, bien que le nom du paramètre (« ChildPath ») soit facultatif.</span><span class="sxs-lookup"><span data-stu-id="3cd22-135">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="3cd22-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="3cd22-136">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="3cd22-137">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3cd22-137">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="3cd22-138">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="3cd22-138">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3cd22-139">-Path</span><span class="sxs-lookup"><span data-stu-id="3cd22-139">-Path</span></span>

<span data-ttu-id="3cd22-140">Spécifie les chemins d’accès principaux auxquels le chemin d’accès enfant est ajouté.</span><span class="sxs-lookup"><span data-stu-id="3cd22-140">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="3cd22-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="3cd22-141">Wildcards are permitted.</span></span>

<span data-ttu-id="3cd22-142">La valeur de `Path` détermine quel fournisseur joint les chemins d’accès et ajoute les séparateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cd22-142">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="3cd22-143">Le `Path` paramètre est obligatoire, bien que le nom du paramètre (« Path ») soit facultatif.</span><span class="sxs-lookup"><span data-stu-id="3cd22-143">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3cd22-144">-Résoudre</span><span class="sxs-lookup"><span data-stu-id="3cd22-144">-Resolve</span></span>

<span data-ttu-id="3cd22-145">Indique que cette applet de commande doit tenter de résoudre le chemin d’accès joint à partir du fournisseur actuel.</span><span class="sxs-lookup"><span data-stu-id="3cd22-145">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="3cd22-146">Si des caractères génériques sont utilisés, l’applet de commande retourne tous les chemins qui correspondent au chemin d’accès joint.</span><span class="sxs-lookup"><span data-stu-id="3cd22-146">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="3cd22-147">Si **aucun** caractère générique n’est utilisé, l’applet de commande génère une erreur si le chemin d’accès n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="3cd22-147">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="3cd22-148">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="3cd22-148">-UseTransaction</span></span>

<span data-ttu-id="3cd22-149">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="3cd22-149">Includes the command in the active transaction.</span></span>
<span data-ttu-id="3cd22-150">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="3cd22-150">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="3cd22-151">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="3cd22-151">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="3cd22-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3cd22-152">CommonParameters</span></span>

<span data-ttu-id="3cd22-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3cd22-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3cd22-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3cd22-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3cd22-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3cd22-155">INPUTS</span></span>

### <span data-ttu-id="3cd22-156">System.String</span><span class="sxs-lookup"><span data-stu-id="3cd22-156">System.String</span></span>

<span data-ttu-id="3cd22-157">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3cd22-157">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="3cd22-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3cd22-158">OUTPUTS</span></span>

### <span data-ttu-id="3cd22-159">System.String</span><span class="sxs-lookup"><span data-stu-id="3cd22-159">System.String</span></span>

<span data-ttu-id="3cd22-160">Cette applet de commande retourne une chaîne qui contient le chemin d’accès résultant.</span><span class="sxs-lookup"><span data-stu-id="3cd22-160">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="3cd22-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3cd22-161">NOTES</span></span>

<span data-ttu-id="3cd22-162">Les applets de commande qui contiennent le nom du chemin d’accès (les applets de commande Path) manipulent les noms de chemin d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="3cd22-162">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="3cd22-163">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="3cd22-163">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="3cd22-164">Utilisez-les comme Dirname, Normpath, Realpath, Join ou tout autre manipulateur de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3cd22-164">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="3cd22-165">Vous pouvez utiliser les applets de commande Path avec plusieurs fournisseurs, notamment les `FileSystem` `Registry` fournisseurs, et `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="3cd22-165">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="3cd22-166">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3cd22-166">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="3cd22-167">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="3cd22-167">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="3cd22-168">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3cd22-168">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="3cd22-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3cd22-169">RELATED LINKS</span></span>

[<span data-ttu-id="3cd22-170">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="3cd22-170">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="3cd22-171">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="3cd22-171">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="3cd22-172">Split-Path</span><span class="sxs-lookup"><span data-stu-id="3cd22-172">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="3cd22-173">Test-Path</span><span class="sxs-lookup"><span data-stu-id="3cd22-173">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="3cd22-174">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="3cd22-174">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="3cd22-175">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="3cd22-175">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="3cd22-176">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="3cd22-176">Get-PSDrive</span></span>](Get-PSDrive.md)
