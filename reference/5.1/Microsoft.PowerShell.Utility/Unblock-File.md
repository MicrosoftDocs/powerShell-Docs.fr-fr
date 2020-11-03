---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 1f56dce193cc3c7c8b6af3a7854021b420107255
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203109"
---
# <span data-ttu-id="73070-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="73070-103">Unblock-File</span></span>

## <span data-ttu-id="73070-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="73070-104">SYNOPSIS</span></span>
<span data-ttu-id="73070-105">Débloque les fichiers téléchargés depuis Internet.</span><span class="sxs-lookup"><span data-stu-id="73070-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="73070-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="73070-106">SYNTAX</span></span>

### <span data-ttu-id="73070-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="73070-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="73070-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="73070-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="73070-109">Description</span><span class="sxs-lookup"><span data-stu-id="73070-109">DESCRIPTION</span></span>

<span data-ttu-id="73070-110">L'applet de commande **Unblock-File** vous permet d'ouvrir des fichiers téléchargés depuis Internet.</span><span class="sxs-lookup"><span data-stu-id="73070-110">The **Unblock-File** cmdlet lets you open files that were downloaded from the Internet.</span></span>
<span data-ttu-id="73070-111">Il débloque les fichiers de script PowerShell qui ont été téléchargés à partir d’Internet afin que vous puissiez les exécuter, même lorsque la stratégie d’exécution de PowerShell est **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="73070-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned** .</span></span>
<span data-ttu-id="73070-112">Par défaut, ces fichiers sont bloqués pour protéger l'ordinateur contre les fichiers non approuvés.</span><span class="sxs-lookup"><span data-stu-id="73070-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="73070-113">Avant d'utiliser l'applet de commande **Unblock-File** , vérifiez le fichier et sa source, puis assurez-vous qu'il peut s'ouvrir sans risque.</span><span class="sxs-lookup"><span data-stu-id="73070-113">Before using the **Unblock-File** cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="73070-114">En interne, l'applet de commande **Unblock-File** supprime le flux de données alternatif Zone.Identifier, dont la valeur est égale à « 3 » pour indiquer qu'il a été téléchargé à partir d'Internet.</span><span class="sxs-lookup"><span data-stu-id="73070-114">Internally, the **Unblock-File** cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="73070-115">Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="73070-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="73070-116">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="73070-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="73070-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="73070-117">EXAMPLES</span></span>

### <span data-ttu-id="73070-118">Exemple 1 : débloquer un fichier</span><span class="sxs-lookup"><span data-stu-id="73070-118">Example 1: Unblock a file</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

<span data-ttu-id="73070-119">Cette commande débloque le fichier PowerShellTips.chm.</span><span class="sxs-lookup"><span data-stu-id="73070-119">This command unblocks the PowerShellTips.chm file.</span></span>

### <span data-ttu-id="73070-120">Exemple 2 : débloquer plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="73070-120">Example 2: Unblock multiple files</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

<span data-ttu-id="73070-121">Cette commande débloque tous les fichiers du répertoire C:\Downloads dont le nom contient « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="73070-121">This command unblocks all of the files in the C:\Downloads directory whose names include "PowerShell".</span></span>
<span data-ttu-id="73070-122">N'exécutez pas une commande similaire à celle-ci tant que vous n'avez pas vérifié que tous les fichiers étaient sûrs.</span><span class="sxs-lookup"><span data-stu-id="73070-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

### <span data-ttu-id="73070-123">Exemple 3 : Rechercher et débloquer des scripts</span><span class="sxs-lookup"><span data-stu-id="73070-123">Example 3: Find and unblock scripts</span></span>

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

<span data-ttu-id="73070-124">Cette commande montre comment rechercher et débloquer des scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73070-124">This command shows how to find and unblock PowerShell scripts.</span></span>

## <span data-ttu-id="73070-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73070-125">PARAMETERS</span></span>

### <span data-ttu-id="73070-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="73070-126">-LiteralPath</span></span>
<span data-ttu-id="73070-127">Spécifie les fichiers à débloquer.</span><span class="sxs-lookup"><span data-stu-id="73070-127">Specifies the files to unblock.</span></span>
<span data-ttu-id="73070-128">Contrairement au paramètre *Path* , la valeur du paramètre *LiteralPath* est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="73070-128">Unlike *Path* , the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="73070-129">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="73070-129">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="73070-130">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="73070-130">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="73070-131">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="73070-131">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="73070-132">-Path</span><span class="sxs-lookup"><span data-stu-id="73070-132">-Path</span></span>
<span data-ttu-id="73070-133">Spécifie les fichiers à débloquer.</span><span class="sxs-lookup"><span data-stu-id="73070-133">Specifies the files to unblock.</span></span>
<span data-ttu-id="73070-134">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="73070-134">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="73070-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="73070-135">-Confirm</span></span>

<span data-ttu-id="73070-136">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73070-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="73070-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="73070-137">-WhatIf</span></span>

<span data-ttu-id="73070-138">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73070-138">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="73070-139">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="73070-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="73070-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73070-140">CommonParameters</span></span>

<span data-ttu-id="73070-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73070-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73070-142">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="73070-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73070-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="73070-143">INPUTS</span></span>

### <span data-ttu-id="73070-144">System.String</span><span class="sxs-lookup"><span data-stu-id="73070-144">System.String</span></span>

<span data-ttu-id="73070-145">Vous pouvez diriger un chemin d'accès vers **Unblock-File** .</span><span class="sxs-lookup"><span data-stu-id="73070-145">You can pipe a file path to **Unblock-File** .</span></span>

## <span data-ttu-id="73070-146">SORTIES</span><span class="sxs-lookup"><span data-stu-id="73070-146">OUTPUTS</span></span>

### <span data-ttu-id="73070-147">Aucun</span><span class="sxs-lookup"><span data-stu-id="73070-147">None</span></span>

<span data-ttu-id="73070-148">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="73070-148">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="73070-149">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="73070-149">NOTES</span></span>

* <span data-ttu-id="73070-150">L'applet de commande **Unblock-File** ne fonctionne que dans les lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="73070-150">The **Unblock-File** cmdlet works only in file system drives.</span></span>
* <span data-ttu-id="73070-151">**Unblock-file** effectue la même opération que le bouton **débloquer** de la boîte de dialogue **Propriétés** dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="73070-151">**Unblock-File** performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
* <span data-ttu-id="73070-152">Si vous utilisez l'applet de commande **Unblock-File** sur un fichier qui n'est pas bloqué, la commande n'a aucun effet sur le fichier débloqué et l'applet de commande ne génère pas d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="73070-152">If you use the **Unblock-File** cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="73070-153">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="73070-153">RELATED LINKS</span></span>

[<span data-ttu-id="73070-154">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="73070-154">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="73070-155">Get-Item</span><span class="sxs-lookup"><span data-stu-id="73070-155">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="73070-156">Out-File</span><span class="sxs-lookup"><span data-stu-id="73070-156">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="73070-157">Fournisseur FileSystem</span><span class="sxs-lookup"><span data-stu-id="73070-157">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
