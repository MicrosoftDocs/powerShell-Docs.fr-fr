---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 1c66cd3b1cc2fccc58cd75c367b41c445deb1e72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596929"
---
# <span data-ttu-id="4965b-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="4965b-102">New-TemporaryFile</span></span>

## <span data-ttu-id="4965b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4965b-103">SYNOPSIS</span></span>
<span data-ttu-id="4965b-104">Crée un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="4965b-104">Creates a temporary file.</span></span>

## <span data-ttu-id="4965b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4965b-105">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4965b-106">Description</span><span class="sxs-lookup"><span data-stu-id="4965b-106">DESCRIPTION</span></span>

<span data-ttu-id="4965b-107">Cette applet de commande crée des fichiers temporaires que vous pouvez utiliser dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="4965b-107">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="4965b-108">L' `New-TemporaryFile` applet de commande crée un fichier vide qui a l' `.tmp` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="4965b-108">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="4965b-109">Cette applet de commande nomme le fichier `tmp<NNNN>.tmp` , où `<NNNN>` est un nombre hexadécimal aléatoire.</span><span class="sxs-lookup"><span data-stu-id="4965b-109">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="4965b-110">L’applet de commande crée le fichier dans votre dossier **temp** .</span><span class="sxs-lookup"><span data-stu-id="4965b-110">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="4965b-111">Cette applet de commande utilise la méthode [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) pour rechercher votre dossier **temp** .</span><span class="sxs-lookup"><span data-stu-id="4965b-111">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="4965b-112">Cette méthode vérifie l’existence de variables d’environnement dans l’ordre suivant et utilise le premier chemin d’accès trouvé :</span><span class="sxs-lookup"><span data-stu-id="4965b-112">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="4965b-113">Sur les plateformes Windows :</span><span class="sxs-lookup"><span data-stu-id="4965b-113">On Windows platforms:</span></span>

  1. <span data-ttu-id="4965b-114">Chemin d’accès spécifié par la variable d’environnement TMP.</span><span class="sxs-lookup"><span data-stu-id="4965b-114">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="4965b-115">Chemin d’accès spécifié par la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="4965b-115">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="4965b-116">Chemin d’accès spécifié par la variable d’environnement USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="4965b-116">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="4965b-117">Répertoire Windows.</span><span class="sxs-lookup"><span data-stu-id="4965b-117">The Windows directory.</span></span>

- <span data-ttu-id="4965b-118">Sur les plateformes non-Windows : utilise le chemin d’accès spécifié par la variable d’environnement TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="4965b-118">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="4965b-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4965b-119">EXAMPLES</span></span>

### <span data-ttu-id="4965b-120">Exemple 1 : créer un fichier temporaire</span><span class="sxs-lookup"><span data-stu-id="4965b-120">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="4965b-121">Cette commande génère un `.tmp` fichier dans votre dossier temporaire, puis stocke une référence au fichier dans la `$TempFile` variable.</span><span class="sxs-lookup"><span data-stu-id="4965b-121">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="4965b-122">Vous pouvez utiliser ce fichier plus tard dans votre script.</span><span class="sxs-lookup"><span data-stu-id="4965b-122">You can use this file later in your script.</span></span>

## <span data-ttu-id="4965b-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4965b-123">PARAMETERS</span></span>

### <span data-ttu-id="4965b-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4965b-124">-Confirm</span></span>

<span data-ttu-id="4965b-125">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4965b-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4965b-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4965b-126">-WhatIf</span></span>

<span data-ttu-id="4965b-127">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4965b-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4965b-128">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4965b-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4965b-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4965b-129">CommonParameters</span></span>

<span data-ttu-id="4965b-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4965b-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4965b-131">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4965b-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4965b-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4965b-132">INPUTS</span></span>

## <span data-ttu-id="4965b-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4965b-133">OUTPUTS</span></span>

### <span data-ttu-id="4965b-134">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="4965b-134">System.IO.FileInfo</span></span>

<span data-ttu-id="4965b-135">Cette applet de commande retourne un objet **FileInfo** qui représente le fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="4965b-135">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="4965b-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4965b-136">NOTES</span></span>

## <span data-ttu-id="4965b-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4965b-137">RELATED LINKS</span></span>

