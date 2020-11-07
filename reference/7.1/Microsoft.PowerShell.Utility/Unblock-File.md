---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 56fe7affdc6b64af53f179b438375fcec8f01227
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344131"
---
# <span data-ttu-id="ab3c2-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="ab3c2-103">Unblock-File</span></span>

## <span data-ttu-id="ab3c2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ab3c2-104">SYNOPSIS</span></span>
<span data-ttu-id="ab3c2-105">Débloque les fichiers téléchargés depuis Internet.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="ab3c2-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ab3c2-106">SYNTAX</span></span>

### <span data-ttu-id="ab3c2-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ab3c2-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ab3c2-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="ab3c2-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ab3c2-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ab3c2-109">DESCRIPTION</span></span>

<span data-ttu-id="ab3c2-110">L' `Unblock-File` applet de commande vous permet d’ouvrir des fichiers qui ont été téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-110">The `Unblock-File` cmdlet lets you open files that were downloaded from the Internet.</span></span> <span data-ttu-id="ab3c2-111">Il débloque les fichiers de script PowerShell qui ont été téléchargés à partir d’Internet afin que vous puissiez les exécuter, même lorsque la stratégie d’exécution de PowerShell est **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="ab3c2-112">Par défaut, ces fichiers sont bloqués pour protéger l'ordinateur contre les fichiers non approuvés.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="ab3c2-113">Avant d’utiliser l’applet de commande `Unblock-File` , examinez le fichier et sa source, puis vérifiez qu’il peut être ouvert en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-113">Before using the `Unblock-File` cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="ab3c2-114">En interne, l' `Unblock-File` applet de commande supprime le flux de données de remplacement de la zone. identifier, qui a la valeur « 3 » pour indiquer qu’il a été téléchargé à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-114">Internally, the `Unblock-File` cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="ab3c2-115">Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="ab3c2-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="ab3c2-116">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ab3c2-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ab3c2-117">EXAMPLES</span></span>

### <span data-ttu-id="ab3c2-118">Exemple 1 : débloquer un fichier</span><span class="sxs-lookup"><span data-stu-id="ab3c2-118">Example 1: Unblock a file</span></span>

<span data-ttu-id="ab3c2-119">Cette commande débloque le fichier PowerShellTips.chm.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-119">This command unblocks the PowerShellTips.chm file.</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### <span data-ttu-id="ab3c2-120">Exemple 2 : débloquer plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="ab3c2-120">Example 2: Unblock multiple files</span></span>

<span data-ttu-id="ab3c2-121">Cette commande débloque tous les fichiers du `C:\Downloads` répertoire dont les noms incluent « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="ab3c2-121">This command unblocks all of the files in the `C:\Downloads` directory whose names include "PowerShell".</span></span> <span data-ttu-id="ab3c2-122">N'exécutez pas une commande similaire à celle-ci tant que vous n'avez pas vérifié que tous les fichiers étaient sûrs.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### <span data-ttu-id="ab3c2-123">Exemple 3 : Rechercher et débloquer des scripts</span><span class="sxs-lookup"><span data-stu-id="ab3c2-123">Example 3: Find and unblock scripts</span></span>

<span data-ttu-id="ab3c2-124">Cette commande montre comment rechercher et débloquer des scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-124">This command shows how to find and unblock PowerShell scripts.</span></span>

<span data-ttu-id="ab3c2-125">La première commande utilise le paramètre **Stream** de l’applet de commande *obten-Item* pour récupérer les fichiers avec le flux de zone. identifier.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-125">The first command uses the **Stream** parameter of the *Get-Item* cmdlet get files with the Zone.Identifier stream.</span></span>

<span data-ttu-id="ab3c2-126">La deuxième commande montre ce qui se passe lorsque vous exécutez un script bloqué dans une session PowerShell dans laquelle la stratégie d’exécution est **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-126">The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="ab3c2-127">La stratégie RemoteSigned vous empêche d'exécuter des scripts qui sont téléchargés à partir d'Internet, sauf s'ils sont signés numériquement.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-127">The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.</span></span>

<span data-ttu-id="ab3c2-128">La troisième commande utilise l' `Unblock-File` applet de commande pour débloquer le script afin qu’il puisse s’exécuter dans la session.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-128">The third command uses the `Unblock-File` cmdlet to unblock the script so it can run in the session.</span></span>

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## <span data-ttu-id="ab3c2-129">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="ab3c2-129">PARAMETERS</span></span>

### <span data-ttu-id="ab3c2-130">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ab3c2-130">-LiteralPath</span></span>

<span data-ttu-id="ab3c2-131">Spécifie les fichiers à débloquer.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-131">Specifies the files to unblock.</span></span> <span data-ttu-id="ab3c2-132">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-132">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="ab3c2-133">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-133">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ab3c2-134">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-134">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ab3c2-135">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-135">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ab3c2-136">-Path</span><span class="sxs-lookup"><span data-stu-id="ab3c2-136">-Path</span></span>

<span data-ttu-id="ab3c2-137">Spécifie les fichiers à débloquer.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-137">Specifies the files to unblock.</span></span> <span data-ttu-id="ab3c2-138">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-138">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ab3c2-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab3c2-139">-Confirm</span></span>

<span data-ttu-id="ab3c2-140">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab3c2-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab3c2-141">-WhatIf</span></span>

<span data-ttu-id="ab3c2-142">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ab3c2-143">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ab3c2-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab3c2-144">CommonParameters</span></span>

<span data-ttu-id="ab3c2-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab3c2-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ab3c2-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab3c2-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ab3c2-147">INPUTS</span></span>

### <span data-ttu-id="ab3c2-148">System.String</span><span class="sxs-lookup"><span data-stu-id="ab3c2-148">System.String</span></span>

<span data-ttu-id="ab3c2-149">Vous pouvez diriger un chemin de fichier vers `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="ab3c2-149">You can pipe a file path to `Unblock-File`.</span></span>

## <span data-ttu-id="ab3c2-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ab3c2-150">OUTPUTS</span></span>

### <span data-ttu-id="ab3c2-151">Aucun</span><span class="sxs-lookup"><span data-stu-id="ab3c2-151">None</span></span>

<span data-ttu-id="ab3c2-152">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ab3c2-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ab3c2-153">NOTES</span></span>

- <span data-ttu-id="ab3c2-154">La prise en charge de macOS a été ajoutée dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-154">Support for macOS was added in PowerShell 7.</span></span>
- <span data-ttu-id="ab3c2-155">L' `Unblock-File` applet de commande fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-155">The `Unblock-File` cmdlet works only in file system drives.</span></span>
- <span data-ttu-id="ab3c2-156">`Unblock-File` effectue la même opération que le bouton **débloquer** de la boîte de dialogue **Propriétés** de l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-156">`Unblock-File` performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
- <span data-ttu-id="ab3c2-157">Si vous utilisez l' `Unblock-File` applet de commande sur un fichier qui n’est pas bloqué, la commande n’a aucun effet sur le fichier débloqué et l’applet de commande ne génère pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="ab3c2-157">If you use the `Unblock-File` cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="ab3c2-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ab3c2-158">RELATED LINKS</span></span>

[<span data-ttu-id="ab3c2-159">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="ab3c2-159">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="ab3c2-160">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ab3c2-160">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="ab3c2-161">Out-File</span><span class="sxs-lookup"><span data-stu-id="ab3c2-161">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="ab3c2-162">Fournisseur FileSystem</span><span class="sxs-lookup"><span data-stu-id="ab3c2-162">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
