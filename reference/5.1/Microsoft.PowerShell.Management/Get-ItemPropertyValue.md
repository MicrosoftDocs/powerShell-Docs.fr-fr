---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203994"
---
# <span data-ttu-id="d80fc-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="d80fc-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="d80fc-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d80fc-104">SYNOPSIS</span></span>
<span data-ttu-id="d80fc-105">Obtient la valeur d’une ou plusieurs propriétés d’un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="d80fc-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="d80fc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d80fc-106">SYNTAX</span></span>

### <span data-ttu-id="d80fc-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d80fc-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="d80fc-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d80fc-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="d80fc-109">Description</span><span class="sxs-lookup"><span data-stu-id="d80fc-109">DESCRIPTION</span></span>

<span data-ttu-id="d80fc-110">`Get-ItemPropertyValue`Obtient la valeur actuelle d’une propriété que vous spécifiez quand vous utilisez le paramètre *Name* , situé dans un chemin d’accès que vous spécifiez avec les paramètres *path* ou *LiteralPath* .</span><span class="sxs-lookup"><span data-stu-id="d80fc-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="d80fc-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d80fc-111">EXAMPLES</span></span>

### <span data-ttu-id="d80fc-112">Exemple 1 : récupérer la valeur de la propriété ProductID</span><span class="sxs-lookup"><span data-stu-id="d80fc-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="d80fc-113">Cette commande obtient la valeur de la propriété **ProductID** de l’objet « \Software\Microsoft\Windows NT\CurrentVersion » dans le fournisseur de Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="d80fc-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="d80fc-114">Exemple 2 : obtenir l’heure de la dernière écriture d’un fichier ou d’un dossier</span><span class="sxs-lookup"><span data-stu-id="d80fc-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="d80fc-115">Cette commande obtient la valeur de la propriété **LastWriteTime** , ou la dernière heure de modification d’un fichier ou d’un dossier, à partir du dossier « C:\Users\Test\Documents\ModuleToAssembly », en travaillant dans le fournisseur FileSystem.</span><span class="sxs-lookup"><span data-stu-id="d80fc-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="d80fc-116">Exemple 3 : obtenir plusieurs valeurs de propriété d’un fichier ou d’un dossier</span><span class="sxs-lookup"><span data-stu-id="d80fc-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="d80fc-117">Cette commande obtient les valeurs des propriétés **LastWriteTime** , **CreationTime** et **root** d’un dossier.</span><span class="sxs-lookup"><span data-stu-id="d80fc-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span>
<span data-ttu-id="d80fc-118">Les valeurs de propriété sont retournées dans l’ordre dans lequel vous avez spécifié les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="d80fc-118">The property values are returned in the order in which you specified the property names.</span></span>

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

## <span data-ttu-id="d80fc-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d80fc-119">PARAMETERS</span></span>

### <span data-ttu-id="d80fc-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="d80fc-120">-Credential</span></span>

<span data-ttu-id="d80fc-121">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="d80fc-121">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="d80fc-122">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d80fc-122">The default is the current user.</span></span>

<span data-ttu-id="d80fc-123">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="d80fc-123">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="d80fc-124">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d80fc-124">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="d80fc-125">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d80fc-125">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="d80fc-126">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d80fc-126">-Exclude</span></span>

<span data-ttu-id="d80fc-127">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="d80fc-127">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="d80fc-128">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="d80fc-128">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d80fc-129">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="d80fc-129">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d80fc-130">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d80fc-130">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d80fc-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="d80fc-131">-Filter</span></span>

<span data-ttu-id="d80fc-132">Spécifie un filtre dans le format ou la langue du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d80fc-132">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="d80fc-133">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="d80fc-133">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="d80fc-134">La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d80fc-134">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="d80fc-135">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="d80fc-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d80fc-136">-Include</span><span class="sxs-lookup"><span data-stu-id="d80fc-136">-Include</span></span>

<span data-ttu-id="d80fc-137">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="d80fc-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="d80fc-138">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="d80fc-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d80fc-139">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="d80fc-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d80fc-140">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d80fc-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d80fc-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d80fc-141">-LiteralPath</span></span>

<span data-ttu-id="d80fc-142">Spécifie le chemin d’accès à l’emplacement actuel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d80fc-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="d80fc-143">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="d80fc-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="d80fc-144">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="d80fc-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d80fc-145">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="d80fc-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="d80fc-146">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d80fc-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="d80fc-147">-Name</span><span class="sxs-lookup"><span data-stu-id="d80fc-147">-Name</span></span>

<span data-ttu-id="d80fc-148">Spécifie le nom des propriétés à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d80fc-148">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d80fc-149">-Path</span><span class="sxs-lookup"><span data-stu-id="d80fc-149">-Path</span></span>

<span data-ttu-id="d80fc-150">Spécifie le chemin d'accès aux éléments.</span><span class="sxs-lookup"><span data-stu-id="d80fc-150">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d80fc-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="d80fc-151">-UseTransaction</span></span>

<span data-ttu-id="d80fc-152">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="d80fc-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="d80fc-153">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="d80fc-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="d80fc-154">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="d80fc-154">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="d80fc-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d80fc-155">CommonParameters</span></span>

<span data-ttu-id="d80fc-156">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="d80fc-156">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d80fc-157">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="d80fc-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d80fc-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d80fc-158">INPUTS</span></span>

### <span data-ttu-id="d80fc-159">System.String</span><span class="sxs-lookup"><span data-stu-id="d80fc-159">System.String</span></span>

<span data-ttu-id="d80fc-160">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d80fc-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="d80fc-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d80fc-161">OUTPUTS</span></span>

### <span data-ttu-id="d80fc-162">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="d80fc-162">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="d80fc-163">Cette applet de commande retourne un objet pour chaque valeur de propriété d’élément qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="d80fc-163">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="d80fc-164">Le type d’objet dépend de la valeur de propriété récupérée.</span><span class="sxs-lookup"><span data-stu-id="d80fc-164">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="d80fc-165">Par exemple, dans un lecteur du système de fichiers, l’applet de commande peut retourner un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="d80fc-165">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="d80fc-166">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d80fc-166">NOTES</span></span>

<span data-ttu-id="d80fc-167">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d80fc-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d80fc-168">Pour répertorier les fournisseurs disponibles dans votre session, exécutez l’applet de commande `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="d80fc-168">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="d80fc-169">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="d80fc-169">For more information, see about_Providers.</span></span>

## <span data-ttu-id="d80fc-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d80fc-170">RELATED LINKS</span></span>

[<span data-ttu-id="d80fc-171">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-171">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="d80fc-172">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-172">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="d80fc-173">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-173">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="d80fc-174">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-174">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="d80fc-175">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-175">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="d80fc-176">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-176">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="d80fc-177">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-177">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="d80fc-178">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d80fc-178">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="d80fc-179">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d80fc-179">Get-PSProvider</span></span>](Get-PSProvider.md)
