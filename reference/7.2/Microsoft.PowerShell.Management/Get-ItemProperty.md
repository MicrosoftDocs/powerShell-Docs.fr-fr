---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: 20116c12f09d6a9a36f33b656a36e30c2096db70
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597992"
---
# <span data-ttu-id="0936b-102">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-102">Get-ItemProperty</span></span>

## <span data-ttu-id="0936b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0936b-103">SYNOPSIS</span></span>
<span data-ttu-id="0936b-104">Obtient les propriétés de l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="0936b-104">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="0936b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0936b-105">SYNTAX</span></span>

### <span data-ttu-id="0936b-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0936b-106">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="0936b-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0936b-107">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="0936b-108">Description</span><span class="sxs-lookup"><span data-stu-id="0936b-108">DESCRIPTION</span></span>

<span data-ttu-id="0936b-109">L' `Get-ItemProperty` applet de commande obtient les propriétés des éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0936b-109">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="0936b-110">Par exemple, vous pouvez utiliser cette applet de commande pour obtenir la valeur de la propriété LastAccessTime d’un objet fichier.</span><span class="sxs-lookup"><span data-stu-id="0936b-110">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span> <span data-ttu-id="0936b-111">Vous pouvez également utiliser cette applet de commande pour afficher les entrées de Registre et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="0936b-111">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="0936b-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0936b-112">EXAMPLES</span></span>

### <span data-ttu-id="0936b-113">Exemple 1 : obtenir des informations sur un répertoire spécifique</span><span class="sxs-lookup"><span data-stu-id="0936b-113">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="0936b-114">Cette commande obtient des informations sur le `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="0936b-114">This command gets information about the `C:\Windows` directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="0936b-115">Exemple 2 : obtenir les propriétés d’un fichier spécifique</span><span class="sxs-lookup"><span data-stu-id="0936b-115">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="0936b-116">Cette commande obtient les propriétés du `C:\Test\Weather.xls` fichier.</span><span class="sxs-lookup"><span data-stu-id="0936b-116">This command gets the properties of the `C:\Test\Weather.xls` file.</span></span>
<span data-ttu-id="0936b-117">Le résultat est dirigé vers l' `Format-List` applet de commande pour afficher la sortie sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="0936b-117">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="0936b-118">Exemple 3 : afficher le nom de la valeur et les données des entrées de Registre dans une sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="0936b-118">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="0936b-119">Cette commande affiche le nom de la valeur et les données de chacune des entrées de Registre contenues dans la sous-clé de Registre « CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="0936b-119">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> <span data-ttu-id="0936b-120">Cette commande requiert l’existence d’un lecteur PowerShell nommé `HKLM:` qui est mappé à la ruche « HKEY_LOCAL_MACHINE » du Registre.</span><span class="sxs-lookup"><span data-stu-id="0936b-120">This command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
>
> <span data-ttu-id="0936b-121">Un lecteur avec ce nom et ce mappage est disponible dans PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="0936b-121">A drive with that name and mapping is available in PowerShell by default.</span></span>
> <span data-ttu-id="0936b-122">Le chemin d'accès à cette sous-clé de Registre peut également être spécifié à l'aide du chemin d'accès suivant, commençant par le nom du fournisseur suivi de deux deux-points :</span><span class="sxs-lookup"><span data-stu-id="0936b-122">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>
>
> <span data-ttu-id="0936b-123">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="0936b-123">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

### <span data-ttu-id="0936b-124">Exemple 4 : obtenir le nom de la valeur et les données d’une entrée de Registre dans une sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="0936b-124">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="0936b-125">Cette commande obtient le nom et les données de la valeur de l’entrée de Registre « ProgramFilesDir figurant » dans la sous-clé de Registre « CurrentVersion ».</span><span class="sxs-lookup"><span data-stu-id="0936b-125">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="0936b-126">Le **chemin d’accès** spécifie la sous-clé et le paramètre **Name** spécifie le nom de la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="0936b-126">The **Path** specifies the subkey and the **Name** parameter specifies the value name of the entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="0936b-127">Exemple 5 : obtenir les noms de valeur et les données des entrées de Registre dans une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="0936b-127">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="0936b-128">Cette commande obtient les noms de valeur et les données des entrées de Registre dans la clé de Registre « PowerShellEngine ».</span><span class="sxs-lookup"><span data-stu-id="0936b-128">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span> <span data-ttu-id="0936b-129">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="0936b-129">The results are shown in the following sample output.</span></span>

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

## <span data-ttu-id="0936b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0936b-130">PARAMETERS</span></span>

### <span data-ttu-id="0936b-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="0936b-131">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="0936b-132">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0936b-132">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="0936b-133">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="0936b-133">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="0936b-134">-Exclude</span><span class="sxs-lookup"><span data-stu-id="0936b-134">-Exclude</span></span>

<span data-ttu-id="0936b-135">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="0936b-135">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="0936b-136">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="0936b-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0936b-137">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0936b-137">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0936b-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0936b-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="0936b-139">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="0936b-139">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0936b-140">-Filter</span><span class="sxs-lookup"><span data-stu-id="0936b-140">-Filter</span></span>

<span data-ttu-id="0936b-141">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="0936b-141">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="0936b-142">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="0936b-142">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="0936b-143">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="0936b-143">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="0936b-144">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="0936b-144">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="0936b-145">-Include</span><span class="sxs-lookup"><span data-stu-id="0936b-145">-Include</span></span>

<span data-ttu-id="0936b-146">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="0936b-146">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="0936b-147">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="0936b-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0936b-148">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="0936b-148">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="0936b-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0936b-149">Wildcard characters are permitted.</span></span> <span data-ttu-id="0936b-150">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="0936b-150">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0936b-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0936b-151">-LiteralPath</span></span>

<span data-ttu-id="0936b-152">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="0936b-152">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0936b-153">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="0936b-153">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="0936b-154">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="0936b-154">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0936b-155">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="0936b-155">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0936b-156">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="0936b-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="0936b-157">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="0936b-157">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="0936b-158">-Name</span><span class="sxs-lookup"><span data-stu-id="0936b-158">-Name</span></span>

<span data-ttu-id="0936b-159">Spécifie le nom des propriétés à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0936b-159">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="0936b-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0936b-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="0936b-161">-Path</span><span class="sxs-lookup"><span data-stu-id="0936b-161">-Path</span></span>

<span data-ttu-id="0936b-162">Spécifie le chemin d'accès aux éléments.</span><span class="sxs-lookup"><span data-stu-id="0936b-162">Specifies the path to the item or items.</span></span>
<span data-ttu-id="0936b-163">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0936b-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="0936b-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0936b-164">CommonParameters</span></span>

<span data-ttu-id="0936b-165">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="0936b-165">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="0936b-166">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0936b-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0936b-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0936b-167">INPUTS</span></span>

### <span data-ttu-id="0936b-168">System.String</span><span class="sxs-lookup"><span data-stu-id="0936b-168">System.String</span></span>

<span data-ttu-id="0936b-169">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="0936b-169">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="0936b-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0936b-170">OUTPUTS</span></span>

### <span data-ttu-id="0936b-171">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="0936b-171">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="0936b-172">`Get-ItemProperty` retourne un objet pour chaque propriété d’élément qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="0936b-172">`Get-ItemProperty` returns an object for each item property that it gets.</span></span> <span data-ttu-id="0936b-173">Le type d'objet dépend de l'objet récupéré.</span><span class="sxs-lookup"><span data-stu-id="0936b-173">The object type depends on the object that is retrieved.</span></span> <span data-ttu-id="0936b-174">Par exemple, dans un lecteur du système de fichiers, un fichier ou un dossier peut être retourné.</span><span class="sxs-lookup"><span data-stu-id="0936b-174">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="0936b-175">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0936b-175">NOTES</span></span>

<span data-ttu-id="0936b-176">L' `Get-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0936b-176">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0936b-177">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="0936b-177">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="0936b-178">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0936b-178">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="0936b-179">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0936b-179">RELATED LINKS</span></span>

[<span data-ttu-id="0936b-180">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-180">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="0936b-181">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-181">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="0936b-182">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-182">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="0936b-183">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-183">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="0936b-184">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-184">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="0936b-185">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-185">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="0936b-186">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0936b-186">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="0936b-187">about_Providers</span><span class="sxs-lookup"><span data-stu-id="0936b-187">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

