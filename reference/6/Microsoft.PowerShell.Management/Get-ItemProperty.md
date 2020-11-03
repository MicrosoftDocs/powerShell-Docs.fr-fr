---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: abf6a5ef365a606b6ca501e9cb924528763a8754
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204453"
---
# <span data-ttu-id="9697e-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-103">Get-ItemProperty</span></span>

## <span data-ttu-id="9697e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9697e-104">SYNOPSIS</span></span>
<span data-ttu-id="9697e-105">Obtient les propriétés de l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="9697e-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="9697e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9697e-106">SYNTAX</span></span>

### <span data-ttu-id="9697e-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9697e-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="9697e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9697e-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="9697e-109">Description</span><span class="sxs-lookup"><span data-stu-id="9697e-109">DESCRIPTION</span></span>

<span data-ttu-id="9697e-110">L' `Get-ItemProperty` applet de commande obtient les propriétés des éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9697e-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="9697e-111">Par exemple, vous pouvez utiliser cette applet de commande pour obtenir la valeur de la propriété LastAccessTime d’un objet fichier.</span><span class="sxs-lookup"><span data-stu-id="9697e-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span> <span data-ttu-id="9697e-112">Vous pouvez également utiliser cette applet de commande pour afficher les entrées de Registre et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="9697e-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="9697e-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9697e-113">EXAMPLES</span></span>

### <span data-ttu-id="9697e-114">Exemple 1 : obtenir des informations sur un répertoire spécifique</span><span class="sxs-lookup"><span data-stu-id="9697e-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="9697e-115">Cette commande obtient des informations sur le `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="9697e-115">This command gets information about the `C:\Windows` directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="9697e-116">Exemple 2 : obtenir les propriétés d’un fichier spécifique</span><span class="sxs-lookup"><span data-stu-id="9697e-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="9697e-117">Cette commande obtient les propriétés du `C:\Test\Weather.xls` fichier.</span><span class="sxs-lookup"><span data-stu-id="9697e-117">This command gets the properties of the `C:\Test\Weather.xls` file.</span></span>
<span data-ttu-id="9697e-118">Le résultat est dirigé vers l' `Format-List` applet de commande pour afficher la sortie sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="9697e-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="9697e-119">Exemple 3 : afficher le nom de la valeur et les données des entrées de Registre dans une sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="9697e-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="9697e-120">Cette commande affiche le nom de la valeur et les données de chacune des entrées de Registre contenues dans la sous-clé de Registre « CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="9697e-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> <span data-ttu-id="9697e-121">Cette commande requiert l’existence d’un lecteur PowerShell nommé `HKLM:` qui est mappé à la ruche « HKEY_LOCAL_MACHINE » du Registre.</span><span class="sxs-lookup"><span data-stu-id="9697e-121">This command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
>
> <span data-ttu-id="9697e-122">Un lecteur avec ce nom et ce mappage est disponible dans PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="9697e-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
> <span data-ttu-id="9697e-123">Le chemin d'accès à cette sous-clé de Registre peut également être spécifié à l'aide du chemin d'accès suivant, commençant par le nom du fournisseur suivi de deux deux-points :</span><span class="sxs-lookup"><span data-stu-id="9697e-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>
>
> <span data-ttu-id="9697e-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="9697e-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

### <span data-ttu-id="9697e-125">Exemple 4 : obtenir le nom de la valeur et les données d’une entrée de Registre dans une sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="9697e-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="9697e-126">Cette commande obtient le nom et les données de la valeur de l’entrée de Registre « ProgramFilesDir figurant » dans la sous-clé de Registre « CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="9697e-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="9697e-127">Le **chemin d’accès** spécifie la sous-clé et le paramètre **Name** spécifie le nom de la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="9697e-127">The **Path** specifies the subkey and the **Name** parameter specifies the value name of the entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="9697e-128">Exemple 5 : obtenir les noms de valeur et les données des entrées de Registre dans une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="9697e-128">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="9697e-129">Cette commande obtient les noms de valeur et les données des entrées de Registre dans la clé de Registre « PowerShellEngine ».</span><span class="sxs-lookup"><span data-stu-id="9697e-129">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span> <span data-ttu-id="9697e-130">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="9697e-130">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

## <span data-ttu-id="9697e-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9697e-131">PARAMETERS</span></span>

### <span data-ttu-id="9697e-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="9697e-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9697e-133">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9697e-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9697e-134">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="9697e-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9697e-135">-Exclude</span><span class="sxs-lookup"><span data-stu-id="9697e-135">-Exclude</span></span>

<span data-ttu-id="9697e-136">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="9697e-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9697e-137">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="9697e-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9697e-138">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="9697e-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9697e-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9697e-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="9697e-140">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="9697e-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9697e-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="9697e-141">-Filter</span></span>

<span data-ttu-id="9697e-142">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="9697e-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9697e-143">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="9697e-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="9697e-144">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="9697e-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="9697e-145">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="9697e-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="9697e-146">-Include</span><span class="sxs-lookup"><span data-stu-id="9697e-146">-Include</span></span>

<span data-ttu-id="9697e-147">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="9697e-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9697e-148">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="9697e-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9697e-149">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="9697e-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="9697e-150">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9697e-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="9697e-151">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="9697e-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9697e-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9697e-152">-LiteralPath</span></span>

<span data-ttu-id="9697e-153">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="9697e-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9697e-154">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="9697e-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="9697e-155">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="9697e-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9697e-156">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="9697e-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9697e-157">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="9697e-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9697e-158">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="9697e-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="9697e-159">-Name</span><span class="sxs-lookup"><span data-stu-id="9697e-159">-Name</span></span>

<span data-ttu-id="9697e-160">Spécifie le nom des propriétés à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9697e-160">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="9697e-161">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9697e-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9697e-162">-Path</span><span class="sxs-lookup"><span data-stu-id="9697e-162">-Path</span></span>

<span data-ttu-id="9697e-163">Spécifie le chemin d'accès aux éléments.</span><span class="sxs-lookup"><span data-stu-id="9697e-163">Specifies the path to the item or items.</span></span>
<span data-ttu-id="9697e-164">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9697e-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9697e-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9697e-165">CommonParameters</span></span>

<span data-ttu-id="9697e-166">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="9697e-166">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9697e-167">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="9697e-167">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9697e-168">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9697e-168">INPUTS</span></span>

### <span data-ttu-id="9697e-169">System.String</span><span class="sxs-lookup"><span data-stu-id="9697e-169">System.String</span></span>

<span data-ttu-id="9697e-170">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="9697e-170">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="9697e-171">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9697e-171">OUTPUTS</span></span>

### <span data-ttu-id="9697e-172">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="9697e-172">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="9697e-173">`Get-ItemProperty` retourne un objet pour chaque propriété d’élément qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="9697e-173">`Get-ItemProperty` returns an object for each item property that it gets.</span></span> <span data-ttu-id="9697e-174">Le type d'objet dépend de l'objet récupéré.</span><span class="sxs-lookup"><span data-stu-id="9697e-174">The object type depends on the object that is retrieved.</span></span> <span data-ttu-id="9697e-175">Par exemple, dans un lecteur du système de fichiers, un fichier ou un dossier peut être retourné.</span><span class="sxs-lookup"><span data-stu-id="9697e-175">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="9697e-176">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9697e-176">NOTES</span></span>

<span data-ttu-id="9697e-177">L' `Get-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9697e-177">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9697e-178">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="9697e-178">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="9697e-179">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="9697e-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9697e-180">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9697e-180">RELATED LINKS</span></span>

[<span data-ttu-id="9697e-181">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-181">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="9697e-182">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-182">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="9697e-183">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-183">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="9697e-184">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-184">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="9697e-185">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-185">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="9697e-186">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-186">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="9697e-187">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9697e-187">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="9697e-188">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9697e-188">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
