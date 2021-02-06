---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 91d0274e485573de96d9960fa49f6d327156a79a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603664"
---
# <span data-ttu-id="17ebd-102">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="17ebd-102">Update-FormatData</span></span>

## <span data-ttu-id="17ebd-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="17ebd-103">SYNOPSIS</span></span>
<span data-ttu-id="17ebd-104">Met à jour les données de mise en forme dans la session active.</span><span class="sxs-lookup"><span data-stu-id="17ebd-104">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="17ebd-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="17ebd-105">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="17ebd-106">Description</span><span class="sxs-lookup"><span data-stu-id="17ebd-106">DESCRIPTION</span></span>

<span data-ttu-id="17ebd-107">L' `Update-FormatData` applet de commande recharge les données de mise en forme des fichiers de mise en forme dans la session active.</span><span class="sxs-lookup"><span data-stu-id="17ebd-107">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="17ebd-108">Cette applet de commande vous permet de mettre à jour les données de mise en forme sans redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17ebd-108">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="17ebd-109">Sans paramètres, `Update-FormatData` recharge les fichiers de mise en forme qu’il a chargés précédemment.</span><span class="sxs-lookup"><span data-stu-id="17ebd-109">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="17ebd-110">Vous pouvez utiliser les paramètres de `Update-FormatData` pour ajouter de nouveaux fichiers de mise en forme à la session.</span><span class="sxs-lookup"><span data-stu-id="17ebd-110">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="17ebd-111">Les fichiers de mise en forme sont des fichiers texte au format XML avec l' `format.ps1xml` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="17ebd-111">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="17ebd-112">Les données de mise en forme des fichiers définissent l'affichage des objets Microsoft .NET Framework dans la session.</span><span class="sxs-lookup"><span data-stu-id="17ebd-112">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="17ebd-113">Lorsque PowerShell démarre, il charge les données de format à partir du code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17ebd-113">When PowerShell starts, it loads the format data from the PowerShell source code.</span></span> <span data-ttu-id="17ebd-114">Toutefois, vous pouvez créer des fichiers format.ps1XML personnalisés pour mettre à jour la mise en forme dans la session active.</span><span class="sxs-lookup"><span data-stu-id="17ebd-114">However, you can create custom format.ps1xml files to update formatting in the current session.</span></span> <span data-ttu-id="17ebd-115">Vous pouvez utiliser `Update-FormatData` pour recharger les données de mise en forme dans la session active sans redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17ebd-115">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="17ebd-116">Cela est utile quand vous avez ajouté ou modifié un fichier de mise en forme et que vous ne voulez pas interrompre la session.</span><span class="sxs-lookup"><span data-stu-id="17ebd-116">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="17ebd-117">Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="17ebd-117">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="17ebd-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="17ebd-118">EXAMPLES</span></span>

### <span data-ttu-id="17ebd-119">Exemple 1 : recharger les fichiers de mise en forme déjà chargés</span><span class="sxs-lookup"><span data-stu-id="17ebd-119">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="17ebd-120">Cette commande recharge les fichiers de mise en forme déjà chargés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-120">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="17ebd-121">Exemple 2 : recharger les fichiers de mise en forme et les fichiers de mise en forme de trace et de journalisation</span><span class="sxs-lookup"><span data-stu-id="17ebd-121">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="17ebd-122">Cette commande recharge les fichiers de mise en forme dans la session, y compris deux nouveaux fichiers, Trace.format.ps1xml et Log.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="17ebd-122">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="17ebd-123">Étant donné que la commande utilise le paramètre **AppendPath** , les données de mise en forme des nouveaux fichiers sont chargées après les données de mise en forme des fichiers intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-123">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="17ebd-124">Le paramètre **AppendPath** est utilisé, car les nouveaux fichiers contiennent des données de mise en forme pour les objets qui ne sont pas référencés dans les fichiers intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-124">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="17ebd-125">Exemple 3 : modifier un fichier de mise en forme et le recharger</span><span class="sxs-lookup"><span data-stu-id="17ebd-125">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="17ebd-126">Cet exemple illustre comment recharger un fichier de mise en forme une fois que vous l'avez modifié.</span><span class="sxs-lookup"><span data-stu-id="17ebd-126">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="17ebd-127">La première commande ajoute le fichier NewFiles.format.ps1xml à la session.</span><span class="sxs-lookup"><span data-stu-id="17ebd-127">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="17ebd-128">Elle utilise le paramètre **prependpath** , car le fichier contient des données de mise en forme pour les objets qui sont référencés dans les fichiers intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-128">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="17ebd-129">Après avoir ajouté le fichier XML NewFiles.format.ps1et l’avoir testé dans ces sessions, l’auteur modifie le fichier.</span><span class="sxs-lookup"><span data-stu-id="17ebd-129">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="17ebd-130">La deuxième commande utilise l' `Update-FormatData` applet de commande pour recharger les fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="17ebd-130">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="17ebd-131">Étant donné que le fichier XML NewFiles.format.ps1a été précédemment chargé, le `Update-FormatData` recharge automatiquement sans utiliser de paramètres.</span><span class="sxs-lookup"><span data-stu-id="17ebd-131">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="17ebd-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="17ebd-132">PARAMETERS</span></span>

### <span data-ttu-id="17ebd-133">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="17ebd-133">-AppendPath</span></span>

<span data-ttu-id="17ebd-134">Spécifie les fichiers de mise en forme que cette applet de commande ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="17ebd-134">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="17ebd-135">Les fichiers sont chargés après que PowerShell a chargé les fichiers de mise en forme intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-135">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="17ebd-136">Lors de la mise en forme d’objets .NET, PowerShell utilise la première définition de mise en forme qu’il trouve pour chaque type .NET.</span><span class="sxs-lookup"><span data-stu-id="17ebd-136">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="17ebd-137">Si vous utilisez le paramètre **AppendPath** , PowerShell recherche les données à partir des fichiers intégrés avant de rencontrer les données de mise en forme que vous ajoutez.</span><span class="sxs-lookup"><span data-stu-id="17ebd-137">If you use the **AppendPath** parameter, PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="17ebd-138">Utilisez ce paramètre pour ajouter un fichier mettant en forme un objet .NET qui n'est pas référencé dans les fichiers de mise en forme intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-138">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17ebd-139">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="17ebd-139">-PrependPath</span></span>

<span data-ttu-id="17ebd-140">Spécifie les fichiers de mise en forme que cette applet de commande ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="17ebd-140">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="17ebd-141">Les fichiers sont chargés avant que PowerShell ne charge les fichiers de mise en forme intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-141">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="17ebd-142">Lors de la mise en forme d’objets .NET, PowerShell utilise la première définition de mise en forme qu’il trouve pour chaque type .NET.</span><span class="sxs-lookup"><span data-stu-id="17ebd-142">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="17ebd-143">Si vous utilisez le paramètre **prependpath** , PowerShell recherche les données à partir des fichiers que vous ajoutez avant de rencontrer les données de mise en forme des fichiers intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-143">If you use the **PrependPath** parameter, PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="17ebd-144">Utilisez ce paramètre pour ajouter un fichier mettant en forme un objet .NET qui est également référencé dans les fichiers de mise en forme intégrés.</span><span class="sxs-lookup"><span data-stu-id="17ebd-144">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17ebd-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="17ebd-145">-Confirm</span></span>

<span data-ttu-id="17ebd-146">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="17ebd-146">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="17ebd-147">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="17ebd-147">-WhatIf</span></span>

<span data-ttu-id="17ebd-148">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="17ebd-148">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="17ebd-149">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="17ebd-149">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="17ebd-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17ebd-150">CommonParameters</span></span>

<span data-ttu-id="17ebd-151">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17ebd-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17ebd-152">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="17ebd-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17ebd-153">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="17ebd-153">INPUTS</span></span>

### <span data-ttu-id="17ebd-154">System.String</span><span class="sxs-lookup"><span data-stu-id="17ebd-154">System.String</span></span>

<span data-ttu-id="17ebd-155">Vous pouvez diriger une chaîne qui contient le chemin d’accès d’ajout vers `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="17ebd-155">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="17ebd-156">SORTIES</span><span class="sxs-lookup"><span data-stu-id="17ebd-156">OUTPUTS</span></span>

### <span data-ttu-id="17ebd-157">None</span><span class="sxs-lookup"><span data-stu-id="17ebd-157">None</span></span>

<span data-ttu-id="17ebd-158">L'applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="17ebd-158">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="17ebd-159">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="17ebd-159">NOTES</span></span>

- <span data-ttu-id="17ebd-160">`Update-FormatData` met également à jour les données de mise en forme pour les commandes de la session qui ont été importées à partir de modules.</span><span class="sxs-lookup"><span data-stu-id="17ebd-160">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="17ebd-161">Si le fichier de mise en forme d’un module est modifié, vous pouvez exécuter une `Update-FormatData` commande pour mettre à jour les données de mise en forme des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="17ebd-161">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="17ebd-162">Il est inutile de réimporter le module.</span><span class="sxs-lookup"><span data-stu-id="17ebd-162">You do not need to import the module again.</span></span>

## <span data-ttu-id="17ebd-163">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="17ebd-163">RELATED LINKS</span></span>

[<span data-ttu-id="17ebd-164">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="17ebd-164">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="17ebd-165">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="17ebd-165">Export-FormatData</span></span>](Export-FormatData.md)
