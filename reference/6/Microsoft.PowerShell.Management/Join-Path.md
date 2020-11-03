---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 7752688a04057861fffdbc7b30c293239acb132e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202882"
---
# <span data-ttu-id="72387-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="72387-103">Join-Path</span></span>

## <span data-ttu-id="72387-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="72387-104">SYNOPSIS</span></span>
<span data-ttu-id="72387-105">Combine un chemin d’accès et un chemin d’accès d’enfant en un seul chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="72387-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="72387-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="72387-107">Description</span><span class="sxs-lookup"><span data-stu-id="72387-107">DESCRIPTION</span></span>

<span data-ttu-id="72387-108">L’applet de commande combine un chemin d’accès et un chemin d’accès `Join-Path` enfant dans un chemin d’accès unique.</span><span class="sxs-lookup"><span data-stu-id="72387-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="72387-109">Le fournisseur fournit les séparateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="72387-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="72387-110">EXAMPLES</span></span>

### <span data-ttu-id="72387-111">Exemple 1 : combiner un chemin d’accès avec un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="72387-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="72387-112">Cette commande utilise `Join-Path` pour combiner un chemin d’accès à un childpath.</span><span class="sxs-lookup"><span data-stu-id="72387-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="72387-113">Étant donné que la commande est exécutée à partir du `FileSystem` fournisseur, elle fournit le `\` délimiteur pour joindre les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="72387-114">Exemple 2 : combiner des chemins qui contiennent déjà des séparateurs de répertoire</span><span class="sxs-lookup"><span data-stu-id="72387-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="72387-115">Séparateurs de répertoire existants `\` et gérés pour qu’il n’y ait qu’un seul séparateur entre `Path` et `ChildPath`</span><span class="sxs-lookup"><span data-stu-id="72387-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="72387-116">Exemple 3 : afficher des fichiers et des dossiers en joignant un chemin d’accès à un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="72387-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="72387-117">Cette commande affiche les fichiers et les dossiers qui sont référencés en joignant le \* chemin d’accès C:\win et le \* chemin d’accès enfant système.</span><span class="sxs-lookup"><span data-stu-id="72387-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="72387-118">Elle affiche les mêmes fichiers et dossiers que `Get-ChildItem` , mais elle affiche le chemin d’accès complet à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="72387-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="72387-119">Dans cette commande, les `Path` `ChildPath` noms de paramètres facultatifs et sont omis.</span><span class="sxs-lookup"><span data-stu-id="72387-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="72387-120">Exemple 4 : utiliser Join-Path avec le fournisseur de Registre PowerShell</span><span class="sxs-lookup"><span data-stu-id="72387-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="72387-121">Cette commande affiche les clés de Registre dans la `HKLM\System` sous-clé de Registre qui inclut `ControlSet` .</span><span class="sxs-lookup"><span data-stu-id="72387-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="72387-122">Le `Resolve` paramètre tente de résoudre le chemin d’accès joint, y compris les caractères génériques du chemin d’accès du fournisseur actuel `HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="72387-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="72387-123">Exemple 5 : combiner plusieurs racines de chemin d’accès avec un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="72387-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="72387-124">Cette commande utilise `Join-Path` pour combiner plusieurs racines de chemin d’accès avec un chemin d’accès enfant.</span><span class="sxs-lookup"><span data-stu-id="72387-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="72387-125">Les lecteurs spécifiés par `Path` doivent exister ou la jointure de cette entrée échouera.</span><span class="sxs-lookup"><span data-stu-id="72387-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="72387-126">Exemple 6 : combiner les racines d’un lecteur du système de fichiers avec un chemin d’accès enfant</span><span class="sxs-lookup"><span data-stu-id="72387-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="72387-127">Cette commande combine les racines de chaque lecteur du système de fichiers PowerShell dans la console avec le chemin d’accès enfant subdir.</span><span class="sxs-lookup"><span data-stu-id="72387-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="72387-128">La commande utilise l' `Get-PSDrive` applet de commande pour récupérer les lecteurs PowerShell pris en charge par le fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="72387-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="72387-129">L' `ForEach-Object` instruction sélectionne uniquement la propriété racine des `PSDriveInfo` objets et la combine avec le chemin d’accès enfant spécifié.</span><span class="sxs-lookup"><span data-stu-id="72387-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="72387-130">La sortie indique que les lecteurs PowerShell sur l’ordinateur incluaient un lecteur mappé au répertoire C:\Program Files.</span><span class="sxs-lookup"><span data-stu-id="72387-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

### <span data-ttu-id="72387-131">Exemple 7 : combiner un nombre indéfini de chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="72387-131">Example 7: Combine an indefinite number of paths</span></span>

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

<span data-ttu-id="72387-132">Le `AdditionalChildPath` paramètre permet de joindre un nombre illimité de chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-132">The `AdditionalChildPath` parameter allows the joining of an unlimited number of paths.</span></span>

<span data-ttu-id="72387-133">Dans cet exemple, aucun nom de paramètre n’est utilisé. par conséquent, « a » est lié à `Path` , « b » `ChildPath` et « c-g » à `AdditionalChildPath`</span><span class="sxs-lookup"><span data-stu-id="72387-133">In this example, no parameter names are used, thus "a" binds to `Path`, "b" to `ChildPath` and "c-g" to `AdditionalChildPath`</span></span>

## <span data-ttu-id="72387-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72387-134">PARAMETERS</span></span>

### <span data-ttu-id="72387-135">-AdditionalChildPath</span><span class="sxs-lookup"><span data-stu-id="72387-135">-AdditionalChildPath</span></span>

<span data-ttu-id="72387-136">Spécifie des éléments supplémentaires à ajouter à la valeur du paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="72387-136">Specifies additional elements to append to the value of the *Path* parameter.</span></span> <span data-ttu-id="72387-137">Le `ChildPath` paramètre est toujours obligatoire et doit également être spécifié.</span><span class="sxs-lookup"><span data-stu-id="72387-137">The `ChildPath` parameter is still mandatory and must be specified as well.</span></span>

<span data-ttu-id="72387-138">Ce paramètre est spécifié avec la `ValueFromRemainingArguments` propriété qui permet de joindre un nombre indéfini de chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-138">This parameter is specified with the `ValueFromRemainingArguments` property which enables joining an indefinite number of paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="72387-139">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="72387-139">-ChildPath</span></span>

<span data-ttu-id="72387-140">Spécifie les éléments à ajouter à la valeur du `Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="72387-140">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="72387-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="72387-141">Wildcards are permitted.</span></span>
<span data-ttu-id="72387-142">Le `ChildPath` paramètre est obligatoire, bien que le nom du paramètre (« ChildPath ») soit facultatif.</span><span class="sxs-lookup"><span data-stu-id="72387-142">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

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

### <span data-ttu-id="72387-143">-Credential</span><span class="sxs-lookup"><span data-stu-id="72387-143">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="72387-144">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72387-144">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="72387-145">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="72387-145">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="72387-146">-Path</span><span class="sxs-lookup"><span data-stu-id="72387-146">-Path</span></span>

<span data-ttu-id="72387-147">Spécifie les chemins d’accès principaux auxquels le chemin d’accès enfant est ajouté.</span><span class="sxs-lookup"><span data-stu-id="72387-147">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="72387-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="72387-148">Wildcards are permitted.</span></span>

<span data-ttu-id="72387-149">La valeur de `Path` détermine quel fournisseur joint les chemins d’accès et ajoute les séparateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-149">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="72387-150">Le `Path` paramètre est obligatoire, bien que le nom du paramètre (« Path ») soit facultatif.</span><span class="sxs-lookup"><span data-stu-id="72387-150">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="72387-151">-Résoudre</span><span class="sxs-lookup"><span data-stu-id="72387-151">-Resolve</span></span>

<span data-ttu-id="72387-152">Indique que cette applet de commande doit tenter de résoudre le chemin d’accès joint à partir du fournisseur actuel.</span><span class="sxs-lookup"><span data-stu-id="72387-152">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="72387-153">Si des caractères génériques sont utilisés, l’applet de commande retourne tous les chemins qui correspondent au chemin d’accès joint.</span><span class="sxs-lookup"><span data-stu-id="72387-153">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="72387-154">Si **aucun** caractère générique n’est utilisé, l’applet de commande génère une erreur si le chemin d’accès n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="72387-154">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="72387-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72387-155">CommonParameters</span></span>

<span data-ttu-id="72387-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72387-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72387-157">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="72387-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72387-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="72387-158">INPUTS</span></span>

### <span data-ttu-id="72387-159">System.String</span><span class="sxs-lookup"><span data-stu-id="72387-159">System.String</span></span>

<span data-ttu-id="72387-160">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="72387-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="72387-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="72387-161">OUTPUTS</span></span>

### <span data-ttu-id="72387-162">System.String</span><span class="sxs-lookup"><span data-stu-id="72387-162">System.String</span></span>

<span data-ttu-id="72387-163">Cette applet de commande retourne une chaîne qui contient le chemin d’accès résultant.</span><span class="sxs-lookup"><span data-stu-id="72387-163">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="72387-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="72387-164">NOTES</span></span>

<span data-ttu-id="72387-165">Les applets de commande qui contiennent le nom du chemin d’accès (les applets de commande Path) manipulent les noms de chemin d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="72387-165">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="72387-166">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="72387-166">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="72387-167">Utilisez-les comme Dirname, Normpath, Realpath, Join ou tout autre manipulateur de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="72387-167">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="72387-168">Vous pouvez utiliser les applets de commande Path avec plusieurs fournisseurs, notamment les `FileSystem` `Registry` fournisseurs, et `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="72387-168">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="72387-169">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="72387-169">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="72387-170">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="72387-170">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="72387-171">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="72387-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="72387-172">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="72387-172">RELATED LINKS</span></span>

[<span data-ttu-id="72387-173">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="72387-173">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="72387-174">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="72387-174">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="72387-175">Split-Path</span><span class="sxs-lookup"><span data-stu-id="72387-175">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="72387-176">Test-Path</span><span class="sxs-lookup"><span data-stu-id="72387-176">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="72387-177">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="72387-177">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="72387-178">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="72387-178">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="72387-179">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="72387-179">Get-PSDrive</span></span>](Get-PSDrive.md)
