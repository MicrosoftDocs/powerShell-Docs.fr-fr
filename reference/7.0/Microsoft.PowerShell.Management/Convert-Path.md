---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: fa66e42e182a7dea830ab30373682e4d1e6601e3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201601"
---
# <span data-ttu-id="e21ad-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="e21ad-103">Convert-Path</span></span>

## <span data-ttu-id="e21ad-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e21ad-104">SYNOPSIS</span></span>
<span data-ttu-id="e21ad-105">Convertit un chemin d’accès PowerShell en chemin d’accès du fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e21ad-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="e21ad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e21ad-106">SYNTAX</span></span>

### <span data-ttu-id="e21ad-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e21ad-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e21ad-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e21ad-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="e21ad-109">Description</span><span class="sxs-lookup"><span data-stu-id="e21ad-109">DESCRIPTION</span></span>

<span data-ttu-id="e21ad-110">L' `Convert-Path` applet de commande convertit un chemin d’accès PowerShell en chemin d’accès du fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e21ad-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="e21ad-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e21ad-111">EXAMPLES</span></span>

### <span data-ttu-id="e21ad-112">Exemple 1 : convertir le répertoire de travail en chemin d’accès au système de fichiers standard</span><span class="sxs-lookup"><span data-stu-id="e21ad-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="e21ad-113">Cet exemple convertit le répertoire de travail actuel, représenté par un point ( `.` ), en chemin d’accès standard au système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e21ad-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="e21ad-114">Exemple 2 : convertir un chemin d’accès de fournisseur en chemin d’accès au registre standard</span><span class="sxs-lookup"><span data-stu-id="e21ad-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="e21ad-115">Cet exemple convertit le chemin d’accès du fournisseur PowerShell en chemin d’accès au registre standard.</span><span class="sxs-lookup"><span data-stu-id="e21ad-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="e21ad-116">Exemple 3 : convertir un chemin en chaîne</span><span class="sxs-lookup"><span data-stu-id="e21ad-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="e21ad-117">Cet exemple convertit le chemin d’accès au répertoire de départ du fournisseur actuel, qui est le fournisseur FileSystem, en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e21ad-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="e21ad-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e21ad-118">PARAMETERS</span></span>

### <span data-ttu-id="e21ad-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e21ad-119">-LiteralPath</span></span>

<span data-ttu-id="e21ad-120">Spécifie, sous la forme d’un tableau de chaînes, le chemin d’accès à convertir.</span><span class="sxs-lookup"><span data-stu-id="e21ad-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="e21ad-121">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="e21ad-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="e21ad-122">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="e21ad-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e21ad-123">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e21ad-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e21ad-124">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="e21ad-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e21ad-125">-Path</span><span class="sxs-lookup"><span data-stu-id="e21ad-125">-Path</span></span>

<span data-ttu-id="e21ad-126">Spécifie le chemin d’accès PowerShell à convertir.</span><span class="sxs-lookup"><span data-stu-id="e21ad-126">Specifies the PowerShell path to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e21ad-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e21ad-127">CommonParameters</span></span>

<span data-ttu-id="e21ad-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e21ad-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e21ad-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e21ad-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e21ad-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e21ad-130">INPUTS</span></span>

### <span data-ttu-id="e21ad-131">System.String</span><span class="sxs-lookup"><span data-stu-id="e21ad-131">System.String</span></span>

<span data-ttu-id="e21ad-132">Vous pouvez diriger un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e21ad-132">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="e21ad-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e21ad-133">OUTPUTS</span></span>

### <span data-ttu-id="e21ad-134">System.String</span><span class="sxs-lookup"><span data-stu-id="e21ad-134">System.String</span></span>

<span data-ttu-id="e21ad-135">Cette applet de commande retourne une chaîne qui contient le chemin d’accès converti.</span><span class="sxs-lookup"><span data-stu-id="e21ad-135">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="e21ad-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e21ad-136">NOTES</span></span>

<span data-ttu-id="e21ad-137">Les applets de commande qui contiennent le nom de chemin d’accès manipulent les noms de chemin d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="e21ad-137">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="e21ad-138">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="e21ad-138">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="e21ad-139">Utilisez-les de la même façon que vous utilisez **dirname** , **Normpath** , **realpath** , **join** ou d’autres manipulateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="e21ad-139">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="e21ad-140">Vous pouvez utiliser les applets de commande Path avec plusieurs fournisseurs, notamment les fournisseurs de système de fichiers, de Registre et de certificats.</span><span class="sxs-lookup"><span data-stu-id="e21ad-140">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="e21ad-141">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e21ad-141">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e21ad-142">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="e21ad-142">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="e21ad-143">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="e21ad-143">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="e21ad-144">`Convert-Path` convertit uniquement les chemins d’accès existants.</span><span class="sxs-lookup"><span data-stu-id="e21ad-144">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="e21ad-145">Elle ne peut pas être utilisée pour convertir un emplacement qui n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="e21ad-145">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="e21ad-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e21ad-146">RELATED LINKS</span></span>

[<span data-ttu-id="e21ad-147">Join-Path</span><span class="sxs-lookup"><span data-stu-id="e21ad-147">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="e21ad-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="e21ad-148">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="e21ad-149">Split-Path</span><span class="sxs-lookup"><span data-stu-id="e21ad-149">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="e21ad-150">Test-Path</span><span class="sxs-lookup"><span data-stu-id="e21ad-150">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="e21ad-151">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e21ad-151">Get-PSProvider</span></span>](Get-PSProvider.md)
