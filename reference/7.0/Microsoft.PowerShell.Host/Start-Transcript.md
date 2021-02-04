---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: d4b777202474ead8f944cd2f751b116d9273e728
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860726"
---
# <span data-ttu-id="33183-103">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="33183-103">Start-Transcript</span></span>

## <span data-ttu-id="33183-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="33183-104">Synopsis</span></span>
<span data-ttu-id="33183-105">Crée un enregistrement de tout ou partie d’une session PowerShell dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="33183-105">Creates a record of all or part of a PowerShell session to a text file.</span></span>

## <span data-ttu-id="33183-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33183-106">Syntax</span></span>

### <span data-ttu-id="33183-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="33183-107">ByPath (Default)</span></span>

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="33183-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="33183-108">ByLiteralPath</span></span>

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="33183-109">ByOutputDirectory</span><span class="sxs-lookup"><span data-stu-id="33183-109">ByOutputDirectory</span></span>

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="33183-110">Description</span><span class="sxs-lookup"><span data-stu-id="33183-110">Description</span></span>

<span data-ttu-id="33183-111">L' `Start-Transcript` applet de commande crée un enregistrement de tout ou partie d’une session PowerShell dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="33183-111">The `Start-Transcript` cmdlet creates a record of all or part of a PowerShell session to a text file.</span></span> <span data-ttu-id="33183-112">La transcription inclut toutes les commandes que l'utilisateur saisit et toutes les sorties qui s'affichent sur la console.</span><span class="sxs-lookup"><span data-stu-id="33183-112">The transcript includes all command that the user types and all output that appears on the console.</span></span>

<span data-ttu-id="33183-113">À compter de Windows PowerShell 5,0, `Start-Transcript` comprend le nom d’hôte dans le nom de fichier généré de toutes les transcriptions.</span><span class="sxs-lookup"><span data-stu-id="33183-113">Starting in Windows PowerShell 5.0, `Start-Transcript` includes the hostname in the generated file name of all transcripts.</span></span> <span data-ttu-id="33183-114">Cela s’avère particulièrement utile lorsque la journalisation de votre entreprise est centralisée.</span><span class="sxs-lookup"><span data-stu-id="33183-114">This is especially useful when your enterprise's logging is centralized.</span></span>
<span data-ttu-id="33183-115">Les fichiers créés par l’applet de commande `Start-Transcript` incluent des caractères aléatoires dans les noms pour éviter les remplacements ou les doublons potentiels lorsque deux transcriptions ou plus sont démarrées simultanément.</span><span class="sxs-lookup"><span data-stu-id="33183-115">Files that are created by the `Start-Transcript` cmdlet include random characters in names to prevent potential overwrites or duplication when two or more transcripts are started simultaneously.</span></span>
<span data-ttu-id="33183-116">Cela empêche également la découverte non autorisée des transcriptions stockées dans un partage de fichiers centralisé.</span><span class="sxs-lookup"><span data-stu-id="33183-116">This also prevents unauthorized discovery of transcripts that are stored in a centralized file share.</span></span>

<span data-ttu-id="33183-117">Lors de l’utilisation du paramètre **Append** , si le fichier cible n’a pas de marque d’ordre d’octet (BOM) `Start-Transcript` par défaut pour `ASCII` l’encodage dans le fichier cible.</span><span class="sxs-lookup"><span data-stu-id="33183-117">When using the **Append** parameter, if the target file doesn't have a Byte Order Mark (BOM) `Start-Transcript` defaults to `ASCII` encoding in the target file.</span></span> <span data-ttu-id="33183-118">Ce comportement peut entraîner un encodage incorrect des caractères mulitbyte dans la transcription.</span><span class="sxs-lookup"><span data-stu-id="33183-118">This behavior can result in improper encoding of mulitbyte characters in the transcript.</span></span>

## <span data-ttu-id="33183-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="33183-119">Examples</span></span>

### <span data-ttu-id="33183-120">Exemple 1 : démarrer un fichier de transcription avec les paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="33183-120">Example 1: Start a transcript file with default settings</span></span>

```powershell
Start-Transcript
```

<span data-ttu-id="33183-121">Cette commande démarre une transcription à l'emplacement du fichier par défaut.</span><span class="sxs-lookup"><span data-stu-id="33183-121">This command starts a transcript in the default file location.</span></span>

### <span data-ttu-id="33183-122">Exemple 2 : démarrer un fichier de transcription à un emplacement spécifique</span><span class="sxs-lookup"><span data-stu-id="33183-122">Example 2: Start a transcript file at a specific location</span></span>

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

<span data-ttu-id="33183-123">Cette commande démarre une transcription dans le `Transcript0.txt` fichier dans `C:\transcripts` .</span><span class="sxs-lookup"><span data-stu-id="33183-123">This command starts a transcript in the `Transcript0.txt` file in `C:\transcripts`.</span></span> <span data-ttu-id="33183-124">Étant donné que le paramètre **NoClobber** est utilisé, la commande empêche tout remplacement des fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="33183-124">Since the **NoClobber** parameter is used, the command prevents any existing files from being overwritten.</span></span> <span data-ttu-id="33183-125">Si le `Transcript0.txt` fichier existe déjà, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="33183-125">If the `Transcript0.txt` file already exists, the command fails.</span></span>

## <span data-ttu-id="33183-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="33183-126">Parameters</span></span>

### <span data-ttu-id="33183-127">-Append</span><span class="sxs-lookup"><span data-stu-id="33183-127">-Append</span></span>

<span data-ttu-id="33183-128">Indique que cette applet de commande ajoute la nouvelle transcription à la fin d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="33183-128">Indicates that this cmdlet adds the new transcript to the end of an existing file.</span></span> <span data-ttu-id="33183-129">Utilisez le paramètre **path** pour spécifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="33183-129">Use the **Path** parameter to specify the file.</span></span>

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

### <span data-ttu-id="33183-130">-Force</span><span class="sxs-lookup"><span data-stu-id="33183-130">-Force</span></span>

<span data-ttu-id="33183-131">Permet à l'applet de commande d'ajouter la transcription à un fichier en lecture seule existant.</span><span class="sxs-lookup"><span data-stu-id="33183-131">Allows the cmdlet to append the transcript to an existing read-only file.</span></span> <span data-ttu-id="33183-132">Lorsqu'elle est utilisée sur un fichier en lecture seule, l'applet de commande modifie l'autorisation du fichier en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="33183-132">When used on a read-only file, the cmdlet changes the file permission to read-write.</span></span> <span data-ttu-id="33183-133">L’applet de commande ne peut pas remplacer les restrictions de sécurité lorsque ce paramètre est utilisé.</span><span class="sxs-lookup"><span data-stu-id="33183-133">The cmdlet cannot override security restrictions when this parameter is used.</span></span>

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

### <span data-ttu-id="33183-134">-IncludeInvocationHeader</span><span class="sxs-lookup"><span data-stu-id="33183-134">-IncludeInvocationHeader</span></span>

<span data-ttu-id="33183-135">Indique que cette applet de commande enregistre l’horodatage lorsque des commandes sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="33183-135">Indicates that this cmdlet logs the time stamp when commands are run.</span></span>

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

### <span data-ttu-id="33183-136">-UseMinimalHeader</span><span class="sxs-lookup"><span data-stu-id="33183-136">-UseMinimalHeader</span></span>

<span data-ttu-id="33183-137">Ajoutez un bref en-tête à la transcription, au lieu de l’en-tête détaillé inclus par défaut.</span><span class="sxs-lookup"><span data-stu-id="33183-137">Prepend a short header to the transcript, instead of the detailed header included by default.</span></span> <span data-ttu-id="33183-138">Ce paramètre a été ajouté dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="33183-138">This parameter was added in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="33183-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="33183-139">-LiteralPath</span></span>

<span data-ttu-id="33183-140">Spécifie un emplacement pour le fichier de transcription.</span><span class="sxs-lookup"><span data-stu-id="33183-140">Specifies a location to the transcript file.</span></span> <span data-ttu-id="33183-141">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="33183-141">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="33183-142">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="33183-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="33183-143">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="33183-143">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="33183-144">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="33183-144">Single quotation marks inform PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33183-145">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="33183-145">-NoClobber</span></span>

<span data-ttu-id="33183-146">Indique que cette applet de commande ne remplacera pas un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="33183-146">Indicates that this cmdlet will not overwrite of an existing file.</span></span> <span data-ttu-id="33183-147">Par défaut, si un fichier de transcription existe dans le chemin d’accès spécifié, `Start-Transcript` remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="33183-147">By default, if a transcript file exists in the specified path, `Start-Transcript` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="33183-148">-OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="33183-148">-OutputDirectory</span></span>

<span data-ttu-id="33183-149">Spécifie un chemin d’accès spécifique et un dossier dans lequel enregistrer une transcription.</span><span class="sxs-lookup"><span data-stu-id="33183-149">Specifies a specific path and folder in which to save a transcript.</span></span> <span data-ttu-id="33183-150">PowerShell attribue automatiquement le nom de la transcription.</span><span class="sxs-lookup"><span data-stu-id="33183-150">PowerShell automatically assigns the transcript name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33183-151">-Path</span><span class="sxs-lookup"><span data-stu-id="33183-151">-Path</span></span>

<span data-ttu-id="33183-152">Spécifie un emplacement pour le fichier de transcription.</span><span class="sxs-lookup"><span data-stu-id="33183-152">Specifies a location to the transcript file.</span></span> <span data-ttu-id="33183-153">Entrez un chemin d’accès à un `.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="33183-153">Enter a path to a `.txt` file.</span></span> <span data-ttu-id="33183-154">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="33183-154">Wildcards are not permitted.</span></span>

<span data-ttu-id="33183-155">Si vous ne spécifiez pas de chemin d’accès, `Start-Transcript` utilise le chemin d’accès dans la valeur de la `$Transcript` variable globale.</span><span class="sxs-lookup"><span data-stu-id="33183-155">If you do not specify a path, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="33183-156">Si vous n’avez pas créé cette variable, `Start-Transcript` stocke les transcriptions dans les `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` fichiers.</span><span class="sxs-lookup"><span data-stu-id="33183-156">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` files.</span></span>

<span data-ttu-id="33183-157">Si un répertoire du chemin d'accès n'existe pas, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="33183-157">If any of the directories in the path do not exist, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33183-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="33183-158">-Confirm</span></span>

<span data-ttu-id="33183-159">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="33183-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="33183-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="33183-160">-WhatIf</span></span>

<span data-ttu-id="33183-161">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="33183-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="33183-162">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="33183-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="33183-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33183-163">CommonParameters</span></span>

<span data-ttu-id="33183-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33183-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33183-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="33183-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33183-166">Entrées</span><span class="sxs-lookup"><span data-stu-id="33183-166">Inputs</span></span>

### <span data-ttu-id="33183-167">None</span><span class="sxs-lookup"><span data-stu-id="33183-167">None</span></span>

<span data-ttu-id="33183-168">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="33183-168">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="33183-169">Sorties</span><span class="sxs-lookup"><span data-stu-id="33183-169">Outputs</span></span>

### <span data-ttu-id="33183-170">System.String</span><span class="sxs-lookup"><span data-stu-id="33183-170">System.String</span></span>

<span data-ttu-id="33183-171">Cette applet de commande retourne une chaîne qui contient un message de confirmation et le chemin d’accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="33183-171">This cmdlet returns a string that contains a confirmation message and the path to the output file.</span></span>

## <span data-ttu-id="33183-172">Remarques</span><span class="sxs-lookup"><span data-stu-id="33183-172">Notes</span></span>

<span data-ttu-id="33183-173">Pour arrêter une transcription, utilisez l' `Stop-Transcript` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="33183-173">To stop a transcript, use the `Stop-Transcript` cmdlet.</span></span>

<span data-ttu-id="33183-174">Pour enregistrer une session entière, ajoutez la `Start-Transcript` commande à votre profil.</span><span class="sxs-lookup"><span data-stu-id="33183-174">To record an entire session, add the `Start-Transcript` command to your profile.</span></span> <span data-ttu-id="33183-175">Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="33183-175">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

## <span data-ttu-id="33183-176">Liens associés</span><span class="sxs-lookup"><span data-stu-id="33183-176">Related Links</span></span>

[<span data-ttu-id="33183-177">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="33183-177">Stop-Transcript</span></span>](Stop-Transcript.md)
