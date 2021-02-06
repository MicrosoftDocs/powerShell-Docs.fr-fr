---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598971"
---
# <span data-ttu-id="f1fdd-102">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="f1fdd-102">Get-FormatData</span></span>

## <span data-ttu-id="f1fdd-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f1fdd-103">SYNOPSIS</span></span>
<span data-ttu-id="f1fdd-104">Obtient les données de mise en forme de la session active.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-104">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="f1fdd-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f1fdd-105">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="f1fdd-106">Description</span><span class="sxs-lookup"><span data-stu-id="f1fdd-106">DESCRIPTION</span></span>

<span data-ttu-id="f1fdd-107">L' `Get-FormatData` applet de commande obtient les données de mise en forme de la session active.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-107">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="f1fdd-108">Les données de mise en forme de la session incluent la mise en forme des données des `Format.ps1xml` fichiers de mise en forme, tels que ceux de l' `$PSHOME` annuaire, la mise en forme des données des modules que vous importez dans la session et la mise en forme des données pour les commandes que vous importez dans votre session à l’aide de l’applet de commande `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f1fdd-108">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="f1fdd-109">Vous pouvez utiliser cette applet de commande pour examiner les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-109">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="f1fdd-110">Ensuite, vous pouvez utiliser l' `Export-FormatData` applet de commande pour sérialiser les objets, les convertir en XML et les enregistrer dans des `Format.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-110">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="f1fdd-111">Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="f1fdd-111">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="f1fdd-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f1fdd-112">EXAMPLES</span></span>

### <span data-ttu-id="f1fdd-113">Exemple 1 : récupération de toutes les données de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f1fdd-113">Example 1: Get all formatting data</span></span>

<span data-ttu-id="f1fdd-114">Cet exemple obtient toutes les données de mise en forme de la session.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-114">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="f1fdd-115">Exemple 2 : récupérer les données de mise en forme par nom de type</span><span class="sxs-lookup"><span data-stu-id="f1fdd-115">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="f1fdd-116">Cet exemple obtient les éléments de données de mise en forme dont les noms commencent par `System.Management.Automation.Cmd` .</span><span class="sxs-lookup"><span data-stu-id="f1fdd-116">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="f1fdd-117">Exemple 3 : examiner un objet de données de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f1fdd-117">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="f1fdd-118">Cet exemple illustre comment obtenir un objet de données de mise en forme et examiner ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-118">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### <span data-ttu-id="f1fdd-119">Exemple 4 : récupérer des données de mise en forme et les exporter</span><span class="sxs-lookup"><span data-stu-id="f1fdd-119">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="f1fdd-120">Cet exemple montre comment utiliser `Get-FormatData` et `Export-FormatData` pour exporter les données de mise en forme ajoutées par un module.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-120">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

<span data-ttu-id="f1fdd-121">Les quatre premières commandes utilisent les `Get-FormatData` applets de commande, `Import-Module` et `Compare-Object` pour identifier le type de format que le module **BitsTransfer** ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-121">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="f1fdd-122">La cinquième commande utilise l' `Get-FormatData` applet de commande pour récupérer le type de format ajouté par le module **BitsTransfer** .</span><span class="sxs-lookup"><span data-stu-id="f1fdd-122">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="f1fdd-123">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet de type de format à l’applet de commande `Export-FormatData` , qui le convertit en XML et l’enregistre dans le `format.ps1xml` fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-123">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="f1fdd-124">La dernière commande affiche un extrait du `format.ps1xml` contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-124">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="f1fdd-125">Exemple 5 : récupérer des données de mise en forme en fonction de la version spécifiée de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1fdd-125">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="f1fdd-126">Cet exemple montre comment utiliser `Get-FormatData` pour obtenir les données de format pour un **TypeName** et une version PowerShell spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-126">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="f1fdd-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f1fdd-127">PARAMETERS</span></span>

### <span data-ttu-id="f1fdd-128">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="f1fdd-128">-PowerShellVersion</span></span>

<span data-ttu-id="f1fdd-129">Spécifiez la version de PowerShell que cette applet de commande obtient pour les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-129">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="f1fdd-130">Entrez un nombre à deux chiffres, séparé par un point.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-130">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="f1fdd-131">Ce paramètre a été ajouté dans PowerShell 5,1 pour améliorer la compatibilité lors de la communication à distance d’ordinateurs exécutant des versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-131">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1fdd-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="f1fdd-132">-TypeName</span></span>

<span data-ttu-id="f1fdd-133">Spécifie les noms de types que cette applet de commande obtient pour les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-133">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="f1fdd-134">Entrez les noms des types.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-134">Enter the type names.</span></span>
<span data-ttu-id="f1fdd-135">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-135">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f1fdd-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f1fdd-136">CommonParameters</span></span>

<span data-ttu-id="f1fdd-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f1fdd-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f1fdd-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f1fdd-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f1fdd-139">INPUTS</span></span>

### <span data-ttu-id="f1fdd-140">None</span><span class="sxs-lookup"><span data-stu-id="f1fdd-140">None</span></span>

<span data-ttu-id="f1fdd-141">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f1fdd-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f1fdd-142">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f1fdd-142">OUTPUTS</span></span>

### <span data-ttu-id="f1fdd-143">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="f1fdd-143">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="f1fdd-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f1fdd-144">NOTES</span></span>

## <span data-ttu-id="f1fdd-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f1fdd-145">RELATED LINKS</span></span>

[<span data-ttu-id="f1fdd-146">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="f1fdd-146">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="f1fdd-147">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="f1fdd-147">Update-FormatData</span></span>](Update-FormatData.md)
