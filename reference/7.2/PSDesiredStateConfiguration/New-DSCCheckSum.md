---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 8b8d0c545cdb36b6184a0670a52a5a30aa33a465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598355"
---
# <span data-ttu-id="4c1e2-102">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="4c1e2-102">New-DscChecksum</span></span>

## <span data-ttu-id="4c1e2-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4c1e2-103">SYNOPSIS</span></span>
<span data-ttu-id="4c1e2-104">Crée des fichiers de somme de contrôle pour les documents DSC et les ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-104">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="4c1e2-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4c1e2-105">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4c1e2-106">Description</span><span class="sxs-lookup"><span data-stu-id="4c1e2-106">DESCRIPTION</span></span>

<span data-ttu-id="4c1e2-107">L’applet **de commande New-DSCCheckSum** génère des fichiers de somme de contrôle pour les documents DSC (Desired State Configuration) PowerShell et les ressources DSC compressées.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-107">The **New-DSCCheckSum** cmdlet generates checksum files for PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="4c1e2-108">Cette applet de commande génère un fichier de somme de contrôle pour chaque configuration et ressource à utiliser en mode par extraction.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-108">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="4c1e2-109">Le service DSC utilise les sommes de contrôle pour s’assurer que la configuration et les ressources correctes existent sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-109">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="4c1e2-110">Placez les sommes de contrôle avec les documents DSC associés et les ressources DSC compressées dans le magasin de services DSC.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-110">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="4c1e2-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4c1e2-111">EXAMPLES</span></span>

### <span data-ttu-id="4c1e2-112">Exemple 1 : créer des fichiers de somme de contrôle pour toutes les configurations dans un chemin d’accès spécifique</span><span class="sxs-lookup"><span data-stu-id="4c1e2-112">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="4c1e2-113">Cette commande crée des fichiers de somme de contrôle pour toutes les configurations dans le chemin d'accès C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-113">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="4c1e2-114">Tous les fichiers de somme de contrôle qui existent déjà sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-114">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="4c1e2-115">Exemple 2 : créer des fichiers de somme de contrôle pour toutes les configurations dans un chemin d’accès spécifique et remplacer les fichiers de somme de contrôle existants</span><span class="sxs-lookup"><span data-stu-id="4c1e2-115">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="4c1e2-116">Cette commande crée des fichiers de somme de contrôle pour toutes les configurations dans le chemin d'accès C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-116">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="4c1e2-117">Si vous spécifiez le paramètre *force* , la commande remplace les fichiers de somme de contrôle qui existent déjà.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-117">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="4c1e2-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4c1e2-118">PARAMETERS</span></span>

### <span data-ttu-id="4c1e2-119">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c1e2-119">-Confirm</span></span>

<span data-ttu-id="4c1e2-120">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-120">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4c1e2-121">-Force</span><span class="sxs-lookup"><span data-stu-id="4c1e2-121">-Force</span></span>

<span data-ttu-id="4c1e2-122">Indique que l'applet de commande remplace le fichier de sortie spécifié s'il existe déjà.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-122">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="4c1e2-123">-Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="4c1e2-123">-OutPath</span></span>

<span data-ttu-id="4c1e2-124">Spécifie le chemin d'accès et le nom de fichier de somme de contrôle de sortie.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-124">Specifies the path and file name of the output checksum file.</span></span>

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

### <span data-ttu-id="4c1e2-125">-Path</span><span class="sxs-lookup"><span data-stu-id="4c1e2-125">-Path</span></span>

<span data-ttu-id="4c1e2-126">Spécifie le chemin d’accès du fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-126">Specifies the path of the input file.</span></span>

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

### <span data-ttu-id="4c1e2-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c1e2-127">-WhatIf</span></span>

<span data-ttu-id="4c1e2-128">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4c1e2-129">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4c1e2-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c1e2-130">CommonParameters</span></span>

<span data-ttu-id="4c1e2-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4c1e2-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c1e2-132">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4c1e2-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c1e2-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4c1e2-133">INPUTS</span></span>

### <span data-ttu-id="4c1e2-134">None</span><span class="sxs-lookup"><span data-stu-id="4c1e2-134">None</span></span>

## <span data-ttu-id="4c1e2-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4c1e2-135">OUTPUTS</span></span>

### <span data-ttu-id="4c1e2-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="4c1e2-136">System.Object</span></span>

## <span data-ttu-id="4c1e2-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4c1e2-137">NOTES</span></span>

## <span data-ttu-id="4c1e2-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4c1e2-138">RELATED LINKS</span></span>

[<span data-ttu-id="4c1e2-139">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c1e2-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

