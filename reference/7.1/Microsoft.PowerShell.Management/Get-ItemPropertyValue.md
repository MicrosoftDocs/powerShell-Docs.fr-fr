---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 96fc9ce21b320710181fe97b6a47edbab8cc65a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204242"
---
# <span data-ttu-id="776fe-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="776fe-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="776fe-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="776fe-104">SYNOPSIS</span></span>
<span data-ttu-id="776fe-105">Obtient la valeur d’une ou plusieurs propriétés d’un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="776fe-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="776fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="776fe-106">SYNTAX</span></span>

### <span data-ttu-id="776fe-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="776fe-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="776fe-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="776fe-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="776fe-109">Description</span><span class="sxs-lookup"><span data-stu-id="776fe-109">DESCRIPTION</span></span>

<span data-ttu-id="776fe-110">`Get-ItemPropertyValue`Obtient la valeur actuelle d’une propriété que vous spécifiez quand vous utilisez le paramètre *Name* , situé dans un chemin d’accès que vous spécifiez avec les paramètres *path* ou *LiteralPath* .</span><span class="sxs-lookup"><span data-stu-id="776fe-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="776fe-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="776fe-111">EXAMPLES</span></span>

### <span data-ttu-id="776fe-112">Exemple 1 : récupérer la valeur de la propriété ProductID</span><span class="sxs-lookup"><span data-stu-id="776fe-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="776fe-113">Cette commande obtient la valeur de la propriété **ProductID** de l’objet « \Software\Microsoft\Windows NT\CurrentVersion » dans le fournisseur de Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="776fe-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="776fe-114">Exemple 2 : obtenir l’heure de la dernière écriture d’un fichier ou d’un dossier</span><span class="sxs-lookup"><span data-stu-id="776fe-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="776fe-115">Cette commande obtient la valeur de la propriété **LastWriteTime** , ou la dernière heure de modification d’un fichier ou d’un dossier, à partir du dossier « C:\Users\Test\Documents\ModuleToAssembly », en travaillant dans le fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="776fe-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="776fe-116">Exemple 3 : obtenir plusieurs valeurs de propriété d’un fichier ou d’un dossier</span><span class="sxs-lookup"><span data-stu-id="776fe-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="776fe-117">Cette commande obtient les valeurs des propriétés **LastWriteTime** , **CreationTime** et **root** d’un dossier.</span><span class="sxs-lookup"><span data-stu-id="776fe-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span> <span data-ttu-id="776fe-118">Les valeurs de propriété sont retournées dans l’ordre dans lequel vous avez spécifié les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="776fe-118">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="776fe-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="776fe-119">PARAMETERS</span></span>

### <span data-ttu-id="776fe-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="776fe-120">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="776fe-121">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="776fe-121">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="776fe-122">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="776fe-122">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="776fe-123">-Exclude</span><span class="sxs-lookup"><span data-stu-id="776fe-123">-Exclude</span></span>

<span data-ttu-id="776fe-124">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="776fe-124">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="776fe-125">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="776fe-125">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="776fe-126">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="776fe-126">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="776fe-127">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="776fe-127">Wildcard characters are permitted.</span></span> <span data-ttu-id="776fe-128">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="776fe-128">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="776fe-129">-Filter</span><span class="sxs-lookup"><span data-stu-id="776fe-129">-Filter</span></span>

<span data-ttu-id="776fe-130">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="776fe-130">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="776fe-131">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="776fe-131">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="776fe-132">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="776fe-132">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="776fe-133">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="776fe-133">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="776fe-134">-Include</span><span class="sxs-lookup"><span data-stu-id="776fe-134">-Include</span></span>

<span data-ttu-id="776fe-135">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="776fe-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="776fe-136">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="776fe-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="776fe-137">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="776fe-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="776fe-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="776fe-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="776fe-139">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="776fe-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="776fe-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="776fe-140">-LiteralPath</span></span>

<span data-ttu-id="776fe-141">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="776fe-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="776fe-142">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="776fe-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="776fe-143">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="776fe-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="776fe-144">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="776fe-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="776fe-145">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="776fe-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="776fe-146">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="776fe-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="776fe-147">-Name</span><span class="sxs-lookup"><span data-stu-id="776fe-147">-Name</span></span>

<span data-ttu-id="776fe-148">Spécifie le nom des propriétés à récupérer.</span><span class="sxs-lookup"><span data-stu-id="776fe-148">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="776fe-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="776fe-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="776fe-150">-Path</span><span class="sxs-lookup"><span data-stu-id="776fe-150">-Path</span></span>

<span data-ttu-id="776fe-151">Spécifie le chemin d'accès aux éléments.</span><span class="sxs-lookup"><span data-stu-id="776fe-151">Specifies the path to the item or items.</span></span>
<span data-ttu-id="776fe-152">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="776fe-152">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="776fe-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="776fe-153">CommonParameters</span></span>

<span data-ttu-id="776fe-154">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="776fe-154">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="776fe-155">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="776fe-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="776fe-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="776fe-156">INPUTS</span></span>

### <span data-ttu-id="776fe-157">System.String</span><span class="sxs-lookup"><span data-stu-id="776fe-157">System.String</span></span>

<span data-ttu-id="776fe-158">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="776fe-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="776fe-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="776fe-159">OUTPUTS</span></span>

### <span data-ttu-id="776fe-160">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="776fe-160">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="776fe-161">Cette applet de commande retourne un objet pour chaque valeur de propriété d’élément qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="776fe-161">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="776fe-162">Le type d’objet dépend de la valeur de propriété récupérée.</span><span class="sxs-lookup"><span data-stu-id="776fe-162">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="776fe-163">Par exemple, dans un lecteur du système de fichiers, l’applet de commande peut retourner un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="776fe-163">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="776fe-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="776fe-164">NOTES</span></span>

<span data-ttu-id="776fe-165">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="776fe-165">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="776fe-166">Pour répertorier les fournisseurs disponibles dans votre session, exécutez l’applet de commande `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="776fe-166">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="776fe-167">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="776fe-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="776fe-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="776fe-168">RELATED LINKS</span></span>

[<span data-ttu-id="776fe-169">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-169">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="776fe-170">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-170">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="776fe-171">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-171">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="776fe-172">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="776fe-172">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="776fe-173">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-173">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="776fe-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-174">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="776fe-175">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-175">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="776fe-176">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-176">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="776fe-177">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="776fe-177">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="776fe-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="776fe-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

