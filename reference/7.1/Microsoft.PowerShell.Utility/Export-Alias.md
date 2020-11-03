---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 1ea81eb6875fa01d12899dffb4f99cbf910c14c9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204205"
---
# <span data-ttu-id="b6970-103">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="b6970-103">Export-Alias</span></span>

## <span data-ttu-id="b6970-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b6970-104">SYNOPSIS</span></span>
<span data-ttu-id="b6970-105">Exporte des informations sur les alias actuellement définis dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-105">Exports information about currently defined aliases to a file.</span></span>

## <span data-ttu-id="b6970-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b6970-106">SYNTAX</span></span>

### <span data-ttu-id="b6970-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b6970-107">ByPath (Default)</span></span>

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b6970-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b6970-108">ByLiteralPath</span></span>

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b6970-109">Description</span><span class="sxs-lookup"><span data-stu-id="b6970-109">DESCRIPTION</span></span>

<span data-ttu-id="b6970-110">L' `Export-Alias` applet de commande exporte les alias dans la session active dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-110">The `Export-Alias` cmdlet exports the aliases in the current session to a file.</span></span>
<span data-ttu-id="b6970-111">Si le fichier de sortie n'existe pas, l'applet de commande le crée.</span><span class="sxs-lookup"><span data-stu-id="b6970-111">If the output file does not exist, the cmdlet will create it.</span></span>

<span data-ttu-id="b6970-112">`Export-Alias` peut exporter les alias dans une étendue particulière ou toutes les étendues, il peut générer les données au format CSV ou sous la forme d’une série de commandes de Set-Alias que vous pouvez ajouter à une session ou à un profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6970-112">`Export-Alias` can export the aliases in a particular scope or all scopes, it can generate the data in CSV format or as a series of Set-Alias commands that you can add to a session or to a PowerShell profile.</span></span>

## <span data-ttu-id="b6970-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b6970-113">EXAMPLES</span></span>

### <span data-ttu-id="b6970-114">Exemple 1 : exporter un alias</span><span class="sxs-lookup"><span data-stu-id="b6970-114">Example 1: Export an alias</span></span>

```powershell
Export-Alias -Path "alias.csv"
```

<span data-ttu-id="b6970-115">Cette commande exporte les informations d'alias actuelles dans un fichier nommé Alias.csv dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="b6970-115">This command exports current alias information to a file named Alias.csv in the current directory.</span></span>

### <span data-ttu-id="b6970-116">Exemple 2 : exporter un alias à moins que le fichier d’exportation existe déjà</span><span class="sxs-lookup"><span data-stu-id="b6970-116">Example 2: Export an alias unless the export file already exists</span></span>

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

<span data-ttu-id="b6970-117">Cette commande exporte les alias dans la session active dans un fichier Alias.csv.</span><span class="sxs-lookup"><span data-stu-id="b6970-117">This command exports the aliases in the current session to an Alias.csv file.</span></span>

<span data-ttu-id="b6970-118">Étant donné que le paramètre **NoClobber** est spécifié, la commande échoue si un fichier Alias.csv existe déjà dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="b6970-118">Because the **NoClobber** parameter is specified, the command will fail if an Alias.csv file already exists in the current directory.</span></span>

### <span data-ttu-id="b6970-119">Exemple 3 : ajouter des alias à un fichier</span><span class="sxs-lookup"><span data-stu-id="b6970-119">Example 3: Append aliases to a file</span></span>

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

<span data-ttu-id="b6970-120">Cette commande ajoute les alias dans la session active au fichier Alias.csv.</span><span class="sxs-lookup"><span data-stu-id="b6970-120">This command appends the aliases in the current session to the Alias.csv file.</span></span>

<span data-ttu-id="b6970-121">La commande utilise le paramètre **Description** pour ajouter une description aux commentaires en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-121">The command uses the **Description** parameter to add a description to the comments at the top of the file.</span></span>

<span data-ttu-id="b6970-122">La commande utilise également le paramètre **force** pour remplacer les fichiers Alias.csv existants, même s’ils ont l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b6970-122">The command also uses the **Force** parameter to overwrite any existing Alias.csv files, even if they have the read-only attribute.</span></span>

### <span data-ttu-id="b6970-123">Exemple 4 : exporter des alias en tant que script</span><span class="sxs-lookup"><span data-stu-id="b6970-123">Example 4: Export aliases as a script</span></span>

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

<span data-ttu-id="b6970-124">Cet exemple montre comment utiliser le format de fichier de script `Export-Alias` généré par.</span><span class="sxs-lookup"><span data-stu-id="b6970-124">This example shows how to use the script file format that `Export-Alias` generates.</span></span>

<span data-ttu-id="b6970-125">La première commande exporte les alias dans la session dans le fichier Alias.ps1.</span><span class="sxs-lookup"><span data-stu-id="b6970-125">The first command exports the aliases in the session to the Alias.ps1 file.</span></span>
<span data-ttu-id="b6970-126">Elle utilise le paramètre **As** avec la valeur script pour générer un fichier qui contient une commande Set-Alias pour chaque alias.</span><span class="sxs-lookup"><span data-stu-id="b6970-126">It uses the **As** parameter with a value of Script to generate a file that contains a Set-Alias command for each alias.</span></span>

<span data-ttu-id="b6970-127">La deuxième commande ajoute les alias dans le fichier Alias.ps1 au profil CurrentUser CurrentHost.</span><span class="sxs-lookup"><span data-stu-id="b6970-127">The second command adds the aliases in the Alias.ps1 file to the CurrentUser-CurrentHost profile.</span></span>
<span data-ttu-id="b6970-128">Le chemin d’accès au profil est enregistré dans la `$Profile` variable.</span><span class="sxs-lookup"><span data-stu-id="b6970-128">The path to the profile is saved in the `$Profile` variable.</span></span>
<span data-ttu-id="b6970-129">La commande utilise l' `Get-Content` applet de commande pour récupérer les alias à partir du fichier Alias.ps1 et de l' `Add-Content` applet de commande pour les ajouter au profil.</span><span class="sxs-lookup"><span data-stu-id="b6970-129">The command uses the `Get-Content` cmdlet to get the aliases from the Alias.ps1 file and the `Add-Content` cmdlet to add them to the profile.</span></span>
<span data-ttu-id="b6970-130">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="b6970-130">For more information, see about_Profiles.</span></span>

<span data-ttu-id="b6970-131">Les troisième et quatrième commandes ajoutent les alias dans le fichier Alias.ps1 à une session à distance sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b6970-131">The third and fourth commands add the aliases in the Alias.ps1 file to a remote session on the Server01 computer.</span></span>
<span data-ttu-id="b6970-132">La troisième commande utilise l' `New-PSSession` applet de commande pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="b6970-132">The third command uses the `New-PSSession` cmdlet to create the session.</span></span>
<span data-ttu-id="b6970-133">La quatrième commande utilise le paramètre **filePath** de l' `Invoke-Command` applet de commande pour exécuter le fichier Alias.ps1 dans la nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="b6970-133">The fourth command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run the Alias.ps1 file in the new session.</span></span>

## <span data-ttu-id="b6970-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6970-134">PARAMETERS</span></span>

### <span data-ttu-id="b6970-135">-Append</span><span class="sxs-lookup"><span data-stu-id="b6970-135">-Append</span></span>

<span data-ttu-id="b6970-136">Indique que cette applet de commande ajoute la sortie au fichier spécifié, au lieu de remplacer le contenu existant de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-136">Indicates that this cmdlet appends the output to the specified file, rather than overwriting the existing contents of that file.</span></span>

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

### <span data-ttu-id="b6970-137">-As</span><span class="sxs-lookup"><span data-stu-id="b6970-137">-As</span></span>

<span data-ttu-id="b6970-138">Spécifie le format de sortie.</span><span class="sxs-lookup"><span data-stu-id="b6970-138">Specifies the output format.</span></span>
<span data-ttu-id="b6970-139">CSV est le format par défaut.</span><span class="sxs-lookup"><span data-stu-id="b6970-139">CSV is the default.</span></span>
<span data-ttu-id="b6970-140">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b6970-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b6970-141">CSV.</span><span class="sxs-lookup"><span data-stu-id="b6970-141">CSV.</span></span>
<span data-ttu-id="b6970-142">Format de valeurs séparées par des virgules (CSV).</span><span class="sxs-lookup"><span data-stu-id="b6970-142">Comma-separated value (CSV) format.</span></span>
- <span data-ttu-id="b6970-143">Script.</span><span class="sxs-lookup"><span data-stu-id="b6970-143">Script.</span></span>
<span data-ttu-id="b6970-144">Crée une `Set-Alias` commande pour chaque alias exporté.</span><span class="sxs-lookup"><span data-stu-id="b6970-144">Creates a `Set-Alias` command for each exported alias.</span></span>
<span data-ttu-id="b6970-145">Si vous nommez le fichier de sortie avec une extension de nom de fichier .ps1, vous pouvez l'exécuter comme un script pour ajouter les alias à toute session.</span><span class="sxs-lookup"><span data-stu-id="b6970-145">If you name the output file with a .ps1 file name extension, you can run it as a script to add the aliases to any session.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6970-146">Description</span><span class="sxs-lookup"><span data-stu-id="b6970-146">-Description</span></span>

<span data-ttu-id="b6970-147">Spécifie la description du fichier exporté.</span><span class="sxs-lookup"><span data-stu-id="b6970-147">Specifies the description of the exported file.</span></span>
<span data-ttu-id="b6970-148">La description s'affiche en tant que commentaire en haut du fichier, après les informations d'en-tête.</span><span class="sxs-lookup"><span data-stu-id="b6970-148">The description appears as a comment at the top of the file, following the header information.</span></span>

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

### <span data-ttu-id="b6970-149">-Force</span><span class="sxs-lookup"><span data-stu-id="b6970-149">-Force</span></span>

<span data-ttu-id="b6970-150">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6970-150">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="b6970-151">Remplace le fichier de sortie, même si l'attribut en lecture seule est défini sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-151">Overwrites the output file, even if the read-only attribute is set on the file.</span></span>

<span data-ttu-id="b6970-152">Par défaut, `Export-Alias` remplace les fichiers sans avertissement, sauf si l’attribut en lecture seule ou masqué est défini ou si le paramètre **NoClobber** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="b6970-152">By default, `Export-Alias` overwrites files without warning, unless the read-only or hidden attribute is set or the **NoClobber** parameter is used in the command.</span></span>
<span data-ttu-id="b6970-153">Le paramètre **NoClobber** est prioritaire sur le paramètre **force** quand les deux sont utilisés dans une commande.</span><span class="sxs-lookup"><span data-stu-id="b6970-153">The **NoClobber** parameter takes precedence over the **Force** parameter when both are used in a command.</span></span>

<span data-ttu-id="b6970-154">Le paramètre **force** ne peut pas forcer le `Export-Alias` remplacement des fichiers par l’attribut Hidden.</span><span class="sxs-lookup"><span data-stu-id="b6970-154">The **Force** parameter cannot force `Export-Alias` to overwrite files with the hidden attribute.</span></span>

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

### <span data-ttu-id="b6970-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b6970-155">-LiteralPath</span></span>

<span data-ttu-id="b6970-156">Spécifie le chemin d'accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="b6970-156">Specifies the path to the output file.</span></span>
<span data-ttu-id="b6970-157">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="b6970-157">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="b6970-158">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="b6970-158">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="b6970-159">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="b6970-159">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="b6970-160">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b6970-160">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b6970-161">-Name</span><span class="sxs-lookup"><span data-stu-id="b6970-161">-Name</span></span>

<span data-ttu-id="b6970-162">Spécifie les noms sous la forme d’un tableau des alias à exporter.</span><span class="sxs-lookup"><span data-stu-id="b6970-162">Specifies the names as an array of the aliases to export.</span></span>
<span data-ttu-id="b6970-163">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b6970-163">Wildcards are permitted.</span></span>

<span data-ttu-id="b6970-164">Par défaut, `Export-Alias` exporte tous les alias dans la session ou l’étendue.</span><span class="sxs-lookup"><span data-stu-id="b6970-164">By default, `Export-Alias` exports all aliases in the session or scope.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="b6970-165">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="b6970-165">-NoClobber</span></span>

<span data-ttu-id="b6970-166">Indique que cette applet `Export-Alias` de commande empêche de remplacer les fichiers, même si le paramètre **force** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="b6970-166">Indicates that this cmdlet prevents `Export-Alias` from overwriting any files, even if the **Force** parameter is used in the command.</span></span>

<span data-ttu-id="b6970-167">Si le paramètre **NoClobber** est omis, `Export-Alias` remplace un fichier existant sans avertissement, sauf si l’attribut en lecture seule est défini sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-167">If the **NoClobber** parameter is omitted, `Export-Alias` will overwrite an existing file without warning, unless the read-only attribute is set on the file.</span></span>
<span data-ttu-id="b6970-168">*NoClobber* est prioritaire sur le paramètre **force** , qui permet `Export-Alias` de remplacer un fichier par l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b6970-168">*NoClobber* takes precedence over the **Force** parameter, which permits `Export-Alias` to overwrite a file with the read-only attribute.</span></span>

<span data-ttu-id="b6970-169">*NoClobber* n’empêche pas le paramètre **Append** d’ajouter du contenu à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="b6970-169">*NoClobber* does not prevent the **Append** parameter from adding content to an existing file.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6970-170">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b6970-170">-PassThru</span></span>

<span data-ttu-id="b6970-171">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="b6970-171">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b6970-172">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="b6970-172">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b6970-173">-Path</span><span class="sxs-lookup"><span data-stu-id="b6970-173">-Path</span></span>

<span data-ttu-id="b6970-174">Spécifie le chemin d'accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="b6970-174">Specifies the path to the output file.</span></span>
<span data-ttu-id="b6970-175">Les caractères génériques sont autorisés, mais la valeur de chemin d'accès résultante doit être résolue en un seul nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-175">Wildcards are permitted, but the resulting path value must resolve to a single file name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b6970-176">-Étendue</span><span class="sxs-lookup"><span data-stu-id="b6970-176">-Scope</span></span>

<span data-ttu-id="b6970-177">Spécifie l'étendue à partir de laquelle les alias doivent être exportés.</span><span class="sxs-lookup"><span data-stu-id="b6970-177">Specifies the scope from which the aliases should be exported.</span></span>
<span data-ttu-id="b6970-178">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b6970-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b6970-179">Global</span><span class="sxs-lookup"><span data-stu-id="b6970-179">Global</span></span>
- <span data-ttu-id="b6970-180">Local</span><span class="sxs-lookup"><span data-stu-id="b6970-180">Local</span></span>
- <span data-ttu-id="b6970-181">Script</span><span class="sxs-lookup"><span data-stu-id="b6970-181">Script</span></span>
- <span data-ttu-id="b6970-182">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="b6970-182">A number relative to the current scope (0 through the number of scopes where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="b6970-183">La valeur par défaut est Local.</span><span class="sxs-lookup"><span data-stu-id="b6970-183">The default value is Local.</span></span>
<span data-ttu-id="b6970-184">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="b6970-184">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="b6970-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b6970-185">-Confirm</span></span>

<span data-ttu-id="b6970-186">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b6970-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b6970-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b6970-187">-WhatIf</span></span>

<span data-ttu-id="b6970-188">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b6970-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b6970-189">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b6970-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b6970-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6970-190">CommonParameters</span></span>

<span data-ttu-id="b6970-191">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6970-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6970-192">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b6970-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6970-193">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b6970-193">INPUTS</span></span>

### <span data-ttu-id="b6970-194">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b6970-194">None.</span></span>

<span data-ttu-id="b6970-195">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b6970-195">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b6970-196">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b6970-196">OUTPUTS</span></span>

### <span data-ttu-id="b6970-197">None ou System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="b6970-197">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="b6970-198">Quand vous utilisez le paramètre **PassThru** , `Export-Alias` retourne un objet **System. Management. Automation. AliasInfo** qui représente l’alias.</span><span class="sxs-lookup"><span data-stu-id="b6970-198">When you use the **Passthru** parameter, `Export-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="b6970-199">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b6970-199">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b6970-200">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b6970-200">NOTES</span></span>

* <span data-ttu-id="b6970-201">Vous pouvez uniquement exporter des alias vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="b6970-201">You can only Export-Aliases to a file.</span></span>

## <span data-ttu-id="b6970-202">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b6970-202">RELATED LINKS</span></span>

[<span data-ttu-id="b6970-203">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="b6970-203">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="b6970-204">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="b6970-204">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="b6970-205">New-Alias</span><span class="sxs-lookup"><span data-stu-id="b6970-205">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="b6970-206">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="b6970-206">Set-Alias</span></span>](Set-Alias.md)

