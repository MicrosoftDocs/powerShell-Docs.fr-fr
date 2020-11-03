---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 5a38fd45ff1f645df7004452b5a3c16c6f5cb74a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201862"
---
# <span data-ttu-id="bb27e-103">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="bb27e-103">Clear-Content</span></span>

## <span data-ttu-id="bb27e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bb27e-104">SYNOPSIS</span></span>
<span data-ttu-id="bb27e-105">Supprime le contenu d'un élément, mais ne supprime pas l'élément.</span><span class="sxs-lookup"><span data-stu-id="bb27e-105">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="bb27e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb27e-106">SYNTAX</span></span>

### <span data-ttu-id="bb27e-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="bb27e-107">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="bb27e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bb27e-108">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="bb27e-109">Description</span><span class="sxs-lookup"><span data-stu-id="bb27e-109">DESCRIPTION</span></span>

<span data-ttu-id="bb27e-110">L' `Clear-Content` applet de commande supprime le contenu d’un élément, tel que la suppression du texte d’un fichier, mais il ne supprime pas l’élément.</span><span class="sxs-lookup"><span data-stu-id="bb27e-110">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="bb27e-111">En conséquence, l'élément existe, mais il est vide.</span><span class="sxs-lookup"><span data-stu-id="bb27e-111">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="bb27e-112">`Clear-Content`Est semblable à `Clear-Item` , mais il fonctionne sur des éléments avec du contenu, au lieu d’éléments avec des valeurs.</span><span class="sxs-lookup"><span data-stu-id="bb27e-112">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="bb27e-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bb27e-113">EXAMPLES</span></span>

### <span data-ttu-id="bb27e-114">Exemple 1 : supprimer tout le contenu d’un répertoire</span><span class="sxs-lookup"><span data-stu-id="bb27e-114">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="bb27e-115">Cette commande supprime tout le contenu des fichiers « init.txt » dans l'ensemble des sous-répertoires du répertoire SmpUsers.</span><span class="sxs-lookup"><span data-stu-id="bb27e-115">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="bb27e-116">Les fichiers ne sont pas supprimés, mais ils sont vides.</span><span class="sxs-lookup"><span data-stu-id="bb27e-116">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="bb27e-117">Exemple 2 : supprimer le contenu de tous les fichiers avec un caractère générique</span><span class="sxs-lookup"><span data-stu-id="bb27e-117">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="bb27e-118">Cette commande supprime le contenu de tous les fichiers du répertoire actif dont le nom est doté de l'extension « .log », y compris les fichiers en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="bb27e-118">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span>
<span data-ttu-id="bb27e-119">L’astérisque ( \* ) dans le chemin d’accès représente tous les éléments du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="bb27e-119">The asterisk (\*) in the path represents all items in the current directory.</span></span>
<span data-ttu-id="bb27e-120">Le paramètre **force** rend la commande effective sur les fichiers en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="bb27e-120">The **Force** parameter makes the command effective on read-only files.</span></span>
<span data-ttu-id="bb27e-121">L’utilisation d’un filtre pour limiter la commande aux fichiers avec l’extension de nom de fichier. log au lieu de spécifier \* . log dans le chemin rend l’opération plus rapide.</span><span class="sxs-lookup"><span data-stu-id="bb27e-121">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="bb27e-122">Exemple 3 : effacer toutes les données d’un flux</span><span class="sxs-lookup"><span data-stu-id="bb27e-122">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="bb27e-123">Cet exemple montre comment l' `Clear-Content` applet de commande efface le contenu d’un autre flux de données tout en laissant intact le flux.</span><span class="sxs-lookup"><span data-stu-id="bb27e-123">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="bb27e-124">La première commande utilise l' `Get-Content` applet de commande pour récupérer le contenu du flux de zone. identificateur dans le fichier Copy-Script.ps1, qui a été téléchargé à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="bb27e-124">The first command uses the `Get-Content` cmdlet to get the content of the Zone.Identifier stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="bb27e-125">La deuxième commande utilise l' `Clear-Content` applet de commande pour effacer le contenu.</span><span class="sxs-lookup"><span data-stu-id="bb27e-125">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="bb27e-126">La troisième commande répète la première commande.</span><span class="sxs-lookup"><span data-stu-id="bb27e-126">The third command repeats the first command.</span></span> <span data-ttu-id="bb27e-127">Il vérifie que le contenu est effacé, mais le flux de données est conservé.</span><span class="sxs-lookup"><span data-stu-id="bb27e-127">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="bb27e-128">Si le flux a été supprimé, la commande génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="bb27e-128">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="bb27e-129">Vous pouvez utiliser une méthode telle que celle-ci pour effacer le contenu d’un flux de données de remplacement.</span><span class="sxs-lookup"><span data-stu-id="bb27e-129">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="bb27e-130">Elle ne constitue cependant pas un moyen recommandé pour éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d'Internet.</span><span class="sxs-lookup"><span data-stu-id="bb27e-130">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="bb27e-131">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bb27e-131">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="bb27e-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb27e-132">PARAMETERS</span></span>

### <span data-ttu-id="bb27e-133">-Stream</span><span class="sxs-lookup"><span data-stu-id="bb27e-133">-Stream</span></span>

<span data-ttu-id="bb27e-134">Spécifie un flux de données alternatif pour le contenu.</span><span class="sxs-lookup"><span data-stu-id="bb27e-134">Specifies an alternative data stream for content.</span></span>
<span data-ttu-id="bb27e-135">Si le flux n’existe pas, cette applet de commande le crée.</span><span class="sxs-lookup"><span data-stu-id="bb27e-135">If the stream does not exist, this cmdlet creates it.</span></span>
<span data-ttu-id="bb27e-136">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bb27e-136">Wildcard characters are not supported.</span></span>

<span data-ttu-id="bb27e-137">Stream est un paramètre dynamique que le fournisseur FileSystem ajoute à `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="bb27e-137">Stream is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span>
<span data-ttu-id="bb27e-138">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="bb27e-138">This parameter works only in file system drives.</span></span>

<span data-ttu-id="bb27e-139">Vous pouvez utiliser l' `Clear-Content` applet de commande pour modifier le contenu du flux de données de remplacement de la zone. identifier.</span><span class="sxs-lookup"><span data-stu-id="bb27e-139">You can use the `Clear-Content` cmdlet to change the content of the Zone.Identifier alternate data stream.</span></span>
<span data-ttu-id="bb27e-140">Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="bb27e-140">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span>
<span data-ttu-id="bb27e-141">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bb27e-141">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

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

### <span data-ttu-id="bb27e-142">-Credential</span><span class="sxs-lookup"><span data-stu-id="bb27e-142">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="bb27e-143">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb27e-143">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="bb27e-144">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="bb27e-144">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb27e-145">-Exclude</span><span class="sxs-lookup"><span data-stu-id="bb27e-145">-Exclude</span></span>

<span data-ttu-id="bb27e-146">Spécifie, sous forme de tableau de chaînes, les chaînes omises par cette applet de commande dans le chemin d’accès au contenu.</span><span class="sxs-lookup"><span data-stu-id="bb27e-146">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span>
<span data-ttu-id="bb27e-147">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="bb27e-147">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="bb27e-148">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="bb27e-148">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="bb27e-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bb27e-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="bb27e-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="bb27e-150">-Filter</span></span>

<span data-ttu-id="bb27e-151">Spécifie un filtre dans le format ou le langage du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bb27e-151">Specifies a filter in the provider's format or language.</span></span>
<span data-ttu-id="bb27e-152">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="bb27e-152">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="bb27e-153">La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bb27e-153">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span>
<span data-ttu-id="bb27e-154">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de la récupération des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="bb27e-154">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bb27e-155">-Force</span><span class="sxs-lookup"><span data-stu-id="bb27e-155">-Force</span></span>

<span data-ttu-id="bb27e-156">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bb27e-156">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="bb27e-157">-Include</span><span class="sxs-lookup"><span data-stu-id="bb27e-157">-Include</span></span>

<span data-ttu-id="bb27e-158">Spécifie, sous forme de tableau de chaînes, le contenu que cette applet de commande efface.</span><span class="sxs-lookup"><span data-stu-id="bb27e-158">Specifies, as a string array, content that this cmdlet clears.</span></span>
<span data-ttu-id="bb27e-159">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="bb27e-159">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="bb27e-160">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="bb27e-160">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="bb27e-161">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bb27e-161">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="bb27e-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bb27e-162">-LiteralPath</span></span>

<span data-ttu-id="bb27e-163">Spécifie les chemins d'accès aux éléments dont le contenu est supprimé.</span><span class="sxs-lookup"><span data-stu-id="bb27e-163">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="bb27e-164">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="bb27e-164">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="bb27e-165">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="bb27e-165">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="bb27e-166">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="bb27e-166">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="bb27e-167">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="bb27e-167">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb27e-168">-Path</span><span class="sxs-lookup"><span data-stu-id="bb27e-168">-Path</span></span>

<span data-ttu-id="bb27e-169">Spécifie les chemins d'accès aux éléments dont le contenu est supprimé.</span><span class="sxs-lookup"><span data-stu-id="bb27e-169">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="bb27e-170">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bb27e-170">Wildcards are permitted.</span></span>
<span data-ttu-id="bb27e-171">Les chemins d'accès doivent être ceux des éléments et non des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bb27e-171">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="bb27e-172">Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.</span><span class="sxs-lookup"><span data-stu-id="bb27e-172">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="bb27e-173">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bb27e-173">Wildcards are permitted.</span></span>
<span data-ttu-id="bb27e-174">Ce paramètre est obligatoire, mais le nom de paramètre (« Path ») est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb27e-174">This parameter is required, but the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="bb27e-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb27e-175">-Confirm</span></span>

<span data-ttu-id="bb27e-176">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bb27e-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb27e-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb27e-177">-WhatIf</span></span>

<span data-ttu-id="bb27e-178">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bb27e-178">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bb27e-179">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="bb27e-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bb27e-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb27e-180">CommonParameters</span></span>

<span data-ttu-id="bb27e-181">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="bb27e-181">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="bb27e-182">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="bb27e-182">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bb27e-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bb27e-183">INPUTS</span></span>

### <span data-ttu-id="bb27e-184">Aucun</span><span class="sxs-lookup"><span data-stu-id="bb27e-184">None</span></span>

<span data-ttu-id="bb27e-185">Vous ne pouvez pas diriger d’objets vers `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="bb27e-185">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="bb27e-186">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bb27e-186">OUTPUTS</span></span>

### <span data-ttu-id="bb27e-187">Aucun</span><span class="sxs-lookup"><span data-stu-id="bb27e-187">None</span></span>

<span data-ttu-id="bb27e-188">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="bb27e-188">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="bb27e-189">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bb27e-189">NOTES</span></span>

<span data-ttu-id="bb27e-190">Vous pouvez utiliser `Clear-Content` avec le fournisseur FileSystem de PowerShell et avec d’autres fournisseurs qui manipulent du contenu.</span><span class="sxs-lookup"><span data-stu-id="bb27e-190">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span>
<span data-ttu-id="bb27e-191">Pour effacer les éléments qui ne sont pas considérés comme du contenu, tels que les éléments gérés par le certificat PowerShell ou les fournisseurs de Registre, utilisez `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="bb27e-191">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="bb27e-192">L' `Clear-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bb27e-192">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="bb27e-193">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="bb27e-193">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="bb27e-194">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="bb27e-194">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="bb27e-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bb27e-195">RELATED LINKS</span></span>

[<span data-ttu-id="bb27e-196">Add-Content</span><span class="sxs-lookup"><span data-stu-id="bb27e-196">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="bb27e-197">Get-Content</span><span class="sxs-lookup"><span data-stu-id="bb27e-197">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="bb27e-198">Get-Item</span><span class="sxs-lookup"><span data-stu-id="bb27e-198">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="bb27e-199">Set-Content</span><span class="sxs-lookup"><span data-stu-id="bb27e-199">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="bb27e-200">about_Providers</span><span class="sxs-lookup"><span data-stu-id="bb27e-200">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
