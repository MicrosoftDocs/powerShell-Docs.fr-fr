---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: cd784c5adac3aeeabc8e4cf9f5f4b0b67e9a000c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203941"
---
# <span data-ttu-id="98783-103">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="98783-103">New-DscChecksum</span></span>

## <span data-ttu-id="98783-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="98783-104">SYNOPSIS</span></span>
<span data-ttu-id="98783-105">Crée des fichiers de somme de contrôle pour les documents DSC et les ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="98783-105">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="98783-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98783-106">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="98783-107">Description</span><span class="sxs-lookup"><span data-stu-id="98783-107">DESCRIPTION</span></span>
<span data-ttu-id="98783-108">L’applet **de commande New-DSCCheckSum** génère des fichiers de somme de contrôle pour les documents DSC (Desired State Configuration) Windows PowerShell et les ressources DSC compressées.</span><span class="sxs-lookup"><span data-stu-id="98783-108">The **New-DSCCheckSum** cmdlet generates checksum files for Windows PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="98783-109">Cette applet de commande génère un fichier de somme de contrôle pour chaque configuration et ressource à utiliser en mode par extraction.</span><span class="sxs-lookup"><span data-stu-id="98783-109">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="98783-110">Le service DSC utilise les sommes de contrôle pour s’assurer que la configuration et les ressources correctes existent sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="98783-110">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="98783-111">Placez les sommes de contrôle avec les documents DSC associés et les ressources DSC compressées dans le magasin de services DSC.</span><span class="sxs-lookup"><span data-stu-id="98783-111">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="98783-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="98783-112">EXAMPLES</span></span>

### <span data-ttu-id="98783-113">Exemple 1 : créer des fichiers de somme de contrôle pour toutes les configurations dans un chemin d’accès spécifique</span><span class="sxs-lookup"><span data-stu-id="98783-113">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="98783-114">Cette commande crée des fichiers de somme de contrôle pour toutes les configurations dans le chemin d'accès C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="98783-114">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="98783-115">Tous les fichiers de somme de contrôle qui existent déjà sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="98783-115">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="98783-116">Exemple 2 : créer des fichiers de somme de contrôle pour toutes les configurations dans un chemin d’accès spécifique et remplacer les fichiers de somme de contrôle existants</span><span class="sxs-lookup"><span data-stu-id="98783-116">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="98783-117">Cette commande crée des fichiers de somme de contrôle pour toutes les configurations dans le chemin d'accès C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="98783-117">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="98783-118">Si vous spécifiez le paramètre *force* , la commande remplace les fichiers de somme de contrôle qui existent déjà.</span><span class="sxs-lookup"><span data-stu-id="98783-118">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="98783-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98783-119">PARAMETERS</span></span>

### <span data-ttu-id="98783-120">-Force</span><span class="sxs-lookup"><span data-stu-id="98783-120">-Force</span></span>
<span data-ttu-id="98783-121">Indique que l'applet de commande remplace le fichier de sortie spécifié s'il existe déjà.</span><span class="sxs-lookup"><span data-stu-id="98783-121">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="98783-122">-Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="98783-122">-OutPath</span></span>
<span data-ttu-id="98783-123">Spécifie le chemin d'accès et le nom de fichier de somme de contrôle de sortie.</span><span class="sxs-lookup"><span data-stu-id="98783-123">Specifies the path and file name of the output checksum file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98783-124">-Path</span><span class="sxs-lookup"><span data-stu-id="98783-124">-Path</span></span>
<span data-ttu-id="98783-125">Spécifie le chemin d’accès du fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="98783-125">Specifies the path of the input file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98783-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="98783-126">-Confirm</span></span>
<span data-ttu-id="98783-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98783-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="98783-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="98783-128">-WhatIf</span></span>
<span data-ttu-id="98783-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98783-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="98783-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="98783-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="98783-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98783-131">CommonParameters</span></span>
<span data-ttu-id="98783-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98783-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98783-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98783-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98783-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="98783-134">INPUTS</span></span>

## <span data-ttu-id="98783-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="98783-135">OUTPUTS</span></span>

## <span data-ttu-id="98783-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="98783-136">NOTES</span></span>

## <span data-ttu-id="98783-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="98783-137">RELATED LINKS</span></span>

[<span data-ttu-id="98783-138">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="98783-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)
