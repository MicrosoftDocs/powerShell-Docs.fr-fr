---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: a442d8ff9f021e1ec05671d9190d35ef97ff4d72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204058"
---
# <span data-ttu-id="4de32-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="4de32-103">Convert-Path</span></span>

## <span data-ttu-id="4de32-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4de32-104">SYNOPSIS</span></span>
<span data-ttu-id="4de32-105">Convertit un chemin d’accès PowerShell en chemin d’accès du fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4de32-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="4de32-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4de32-106">SYNTAX</span></span>

### <span data-ttu-id="4de32-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4de32-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="4de32-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4de32-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="4de32-109">Description</span><span class="sxs-lookup"><span data-stu-id="4de32-109">DESCRIPTION</span></span>

<span data-ttu-id="4de32-110">L' `Convert-Path` applet de commande convertit un chemin d’accès PowerShell en chemin d’accès du fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4de32-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="4de32-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4de32-111">EXAMPLES</span></span>

### <span data-ttu-id="4de32-112">Exemple 1 : convertir le répertoire de travail en chemin d’accès au système de fichiers standard</span><span class="sxs-lookup"><span data-stu-id="4de32-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="4de32-113">Cet exemple convertit le répertoire de travail actuel, représenté par un point ( `.` ), en chemin d’accès standard au système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4de32-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="4de32-114">Exemple 2 : convertir un chemin d’accès de fournisseur en chemin d’accès au registre standard</span><span class="sxs-lookup"><span data-stu-id="4de32-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="4de32-115">Cet exemple convertit le chemin d’accès du fournisseur PowerShell en chemin d’accès au registre standard.</span><span class="sxs-lookup"><span data-stu-id="4de32-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="4de32-116">Exemple 3 : convertir un chemin en chaîne</span><span class="sxs-lookup"><span data-stu-id="4de32-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="4de32-117">Cet exemple convertit le chemin d’accès au répertoire de départ du fournisseur actuel, qui est le fournisseur FileSystem, en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="4de32-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="4de32-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4de32-118">PARAMETERS</span></span>

### <span data-ttu-id="4de32-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4de32-119">-LiteralPath</span></span>

<span data-ttu-id="4de32-120">Spécifie, sous la forme d’un tableau de chaînes, le chemin d’accès à convertir.</span><span class="sxs-lookup"><span data-stu-id="4de32-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="4de32-121">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="4de32-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="4de32-122">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="4de32-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4de32-123">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4de32-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4de32-124">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4de32-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4de32-125">-Path</span><span class="sxs-lookup"><span data-stu-id="4de32-125">-Path</span></span>

<span data-ttu-id="4de32-126">Spécifie le chemin d’accès PowerShell à convertir.</span><span class="sxs-lookup"><span data-stu-id="4de32-126">Specifies the PowerShell path to be converted.</span></span>

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

### <span data-ttu-id="4de32-127">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="4de32-127">-UseTransaction</span></span>
<span data-ttu-id="4de32-128">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="4de32-128">Includes the command in the active transaction.</span></span>
<span data-ttu-id="4de32-129">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="4de32-129">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="4de32-130">Pour plus d’informations, consultez about_transactions.</span><span class="sxs-lookup"><span data-stu-id="4de32-130">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4de32-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4de32-131">CommonParameters</span></span>

<span data-ttu-id="4de32-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4de32-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4de32-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4de32-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4de32-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4de32-134">INPUTS</span></span>

### <span data-ttu-id="4de32-135">System.String</span><span class="sxs-lookup"><span data-stu-id="4de32-135">System.String</span></span>

<span data-ttu-id="4de32-136">Vous pouvez diriger un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4de32-136">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="4de32-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4de32-137">OUTPUTS</span></span>

### <span data-ttu-id="4de32-138">System.String</span><span class="sxs-lookup"><span data-stu-id="4de32-138">System.String</span></span>

<span data-ttu-id="4de32-139">Cette applet de commande retourne une chaîne qui contient le chemin d’accès converti.</span><span class="sxs-lookup"><span data-stu-id="4de32-139">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="4de32-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4de32-140">NOTES</span></span>

<span data-ttu-id="4de32-141">Les applets de commande qui contiennent le nom de chemin d’accès manipulent les noms de chemin d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="4de32-141">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="4de32-142">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="4de32-142">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="4de32-143">Utilisez-les de la même façon que vous utilisez **dirname** , **Normpath** , **realpath** , **join** ou d’autres manipulateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4de32-143">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="4de32-144">Vous pouvez utiliser les applets de commande Path avec plusieurs fournisseurs, notamment les fournisseurs de système de fichiers, de Registre et de certificats.</span><span class="sxs-lookup"><span data-stu-id="4de32-144">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="4de32-145">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4de32-145">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4de32-146">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="4de32-146">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="4de32-147">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4de32-147">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="4de32-148">`Convert-Path` convertit uniquement les chemins d’accès existants.</span><span class="sxs-lookup"><span data-stu-id="4de32-148">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="4de32-149">Elle ne peut pas être utilisée pour convertir un emplacement qui n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="4de32-149">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="4de32-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4de32-150">RELATED LINKS</span></span>

[<span data-ttu-id="4de32-151">Join-Path</span><span class="sxs-lookup"><span data-stu-id="4de32-151">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="4de32-152">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="4de32-152">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="4de32-153">Split-Path</span><span class="sxs-lookup"><span data-stu-id="4de32-153">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="4de32-154">Test-Path</span><span class="sxs-lookup"><span data-stu-id="4de32-154">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="4de32-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="4de32-155">Get-PSProvider</span></span>](Get-PSProvider.md)
