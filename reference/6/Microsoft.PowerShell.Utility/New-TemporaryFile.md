---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 566a8bf22815e55457da430a02af391bb308b50c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204570"
---
# <span data-ttu-id="6960c-103">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6960c-103">New-TemporaryFile</span></span>

## <span data-ttu-id="6960c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6960c-104">SYNOPSIS</span></span>
<span data-ttu-id="6960c-105">Crée un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="6960c-105">Creates a temporary file.</span></span>

## <span data-ttu-id="6960c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6960c-106">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6960c-107">Description</span><span class="sxs-lookup"><span data-stu-id="6960c-107">DESCRIPTION</span></span>

<span data-ttu-id="6960c-108">Cette applet de commande crée des fichiers temporaires que vous pouvez utiliser dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="6960c-108">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="6960c-109">L' `New-TemporaryFile` applet de commande crée un fichier vide qui a l' `.tmp` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="6960c-109">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="6960c-110">Cette applet de commande nomme le fichier `tmp<NNNN>.tmp` , où `<NNNN>` est un nombre hexadécimal aléatoire.</span><span class="sxs-lookup"><span data-stu-id="6960c-110">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="6960c-111">L’applet de commande crée le fichier dans votre dossier **temp** .</span><span class="sxs-lookup"><span data-stu-id="6960c-111">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="6960c-112">Cette applet de commande utilise la méthode [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) pour rechercher votre dossier **temp** .</span><span class="sxs-lookup"><span data-stu-id="6960c-112">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="6960c-113">Cette méthode vérifie l’existence de variables d’environnement dans l’ordre suivant et utilise le premier chemin d’accès trouvé :</span><span class="sxs-lookup"><span data-stu-id="6960c-113">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="6960c-114">Sur les plateformes Windows :</span><span class="sxs-lookup"><span data-stu-id="6960c-114">On Windows platforms:</span></span>

  1. <span data-ttu-id="6960c-115">Chemin d’accès spécifié par la variable d’environnement TMP.</span><span class="sxs-lookup"><span data-stu-id="6960c-115">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="6960c-116">Chemin d’accès spécifié par la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="6960c-116">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="6960c-117">Chemin d’accès spécifié par la variable d’environnement USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="6960c-117">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="6960c-118">Répertoire Windows.</span><span class="sxs-lookup"><span data-stu-id="6960c-118">The Windows directory.</span></span>

- <span data-ttu-id="6960c-119">Sur les plateformes non-Windows : utilise le chemin d’accès spécifié par la variable d’environnement TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="6960c-119">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="6960c-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6960c-120">EXAMPLES</span></span>

### <span data-ttu-id="6960c-121">Exemple 1 : créer un fichier temporaire</span><span class="sxs-lookup"><span data-stu-id="6960c-121">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="6960c-122">Cette commande génère un `.tmp` fichier dans votre dossier temporaire, puis stocke une référence au fichier dans la `$TempFile` variable.</span><span class="sxs-lookup"><span data-stu-id="6960c-122">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="6960c-123">Vous pouvez utiliser ce fichier plus tard dans votre script.</span><span class="sxs-lookup"><span data-stu-id="6960c-123">You can use this file later in your script.</span></span>

## <span data-ttu-id="6960c-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6960c-124">PARAMETERS</span></span>

### <span data-ttu-id="6960c-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6960c-125">-Confirm</span></span>

<span data-ttu-id="6960c-126">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6960c-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6960c-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6960c-127">-WhatIf</span></span>

<span data-ttu-id="6960c-128">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6960c-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6960c-129">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6960c-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6960c-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6960c-130">CommonParameters</span></span>

<span data-ttu-id="6960c-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6960c-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6960c-132">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6960c-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6960c-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6960c-133">INPUTS</span></span>

## <span data-ttu-id="6960c-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6960c-134">OUTPUTS</span></span>

### <span data-ttu-id="6960c-135">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="6960c-135">System.IO.FileInfo</span></span>

<span data-ttu-id="6960c-136">Cette applet de commande retourne un objet **FileInfo** qui représente le fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="6960c-136">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="6960c-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6960c-137">NOTES</span></span>

## <span data-ttu-id="6960c-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6960c-138">RELATED LINKS</span></span>
