---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 0024bb83b983d0b13e2fbfafb24505849acf15f6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202826"
---
# <span data-ttu-id="0043e-103">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="0043e-103">Get-FormatData</span></span>

## <span data-ttu-id="0043e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0043e-104">SYNOPSIS</span></span>
<span data-ttu-id="0043e-105">Obtient les données de mise en forme de la session active.</span><span class="sxs-lookup"><span data-stu-id="0043e-105">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="0043e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0043e-106">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="0043e-107">Description</span><span class="sxs-lookup"><span data-stu-id="0043e-107">DESCRIPTION</span></span>

<span data-ttu-id="0043e-108">L' `Get-FormatData` applet de commande obtient les données de mise en forme de la session active.</span><span class="sxs-lookup"><span data-stu-id="0043e-108">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="0043e-109">Les données de mise en forme de la session incluent la mise en forme des données des `Format.ps1xml` fichiers de mise en forme, tels que ceux de l' `$PSHOME` annuaire, la mise en forme des données des modules que vous importez dans la session et la mise en forme des données pour les commandes que vous importez dans votre session à l’aide de l’applet de commande `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="0043e-109">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="0043e-110">Vous pouvez utiliser cette applet de commande pour examiner les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0043e-110">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="0043e-111">Ensuite, vous pouvez utiliser l' `Export-FormatData` applet de commande pour sérialiser les objets, les convertir en XML et les enregistrer dans des `Format.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="0043e-111">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="0043e-112">Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="0043e-112">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="0043e-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0043e-113">EXAMPLES</span></span>

### <span data-ttu-id="0043e-114">Exemple 1 : récupération de toutes les données de mise en forme</span><span class="sxs-lookup"><span data-stu-id="0043e-114">Example 1: Get all formatting data</span></span>

<span data-ttu-id="0043e-115">Cet exemple obtient toutes les données de mise en forme de la session.</span><span class="sxs-lookup"><span data-stu-id="0043e-115">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="0043e-116">Exemple 2 : récupérer les données de mise en forme par nom de type</span><span class="sxs-lookup"><span data-stu-id="0043e-116">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="0043e-117">Cet exemple obtient les éléments de données de mise en forme dont les noms commencent par `System.Management.Automation.Cmd` .</span><span class="sxs-lookup"><span data-stu-id="0043e-117">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="0043e-118">Exemple 3 : examiner un objet de données de mise en forme</span><span class="sxs-lookup"><span data-stu-id="0043e-118">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="0043e-119">Cet exemple illustre comment obtenir un objet de données de mise en forme et examiner ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="0043e-119">This example shows how to get a formatting data object and examine its properties.</span></span>

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

### <span data-ttu-id="0043e-120">Exemple 4 : récupérer des données de mise en forme et les exporter</span><span class="sxs-lookup"><span data-stu-id="0043e-120">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="0043e-121">Cet exemple montre comment utiliser `Get-FormatData` et `Export-FormatData` pour exporter les données de mise en forme ajoutées par un module.</span><span class="sxs-lookup"><span data-stu-id="0043e-121">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

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

<span data-ttu-id="0043e-122">Les quatre premières commandes utilisent les `Get-FormatData` applets de commande, `Import-Module` et `Compare-Object` pour identifier le type de format que le module **BitsTransfer** ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="0043e-122">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="0043e-123">La cinquième commande utilise l' `Get-FormatData` applet de commande pour récupérer le type de format ajouté par le module **BitsTransfer** .</span><span class="sxs-lookup"><span data-stu-id="0043e-123">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="0043e-124">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet de type de format à l’applet de commande `Export-FormatData` , qui le convertit en XML et l’enregistre dans le `format.ps1xml` fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="0043e-124">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="0043e-125">La dernière commande affiche un extrait du `format.ps1xml` contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="0043e-125">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="0043e-126">Exemple 5 : récupérer des données de mise en forme en fonction de la version spécifiée de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0043e-126">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="0043e-127">Cet exemple montre comment utiliser `Get-FormatData` pour obtenir les données de format pour un **TypeName** et une version PowerShell spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0043e-127">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="0043e-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0043e-128">PARAMETERS</span></span>

### <span data-ttu-id="0043e-129">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="0043e-129">-PowerShellVersion</span></span>

<span data-ttu-id="0043e-130">Spécifiez la version de PowerShell que cette applet de commande obtient pour les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0043e-130">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="0043e-131">Entrez un nombre à deux chiffres, séparé par un point.</span><span class="sxs-lookup"><span data-stu-id="0043e-131">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="0043e-132">Ce paramètre a été ajouté dans PowerShell 5,1 pour améliorer la compatibilité lors de la communication à distance d’ordinateurs exécutant des versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0043e-132">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

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

### <span data-ttu-id="0043e-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="0043e-133">-TypeName</span></span>

<span data-ttu-id="0043e-134">Spécifie les noms de types que cette applet de commande obtient pour les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0043e-134">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="0043e-135">Entrez les noms des types.</span><span class="sxs-lookup"><span data-stu-id="0043e-135">Enter the type names.</span></span>
<span data-ttu-id="0043e-136">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0043e-136">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="0043e-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0043e-137">CommonParameters</span></span>

<span data-ttu-id="0043e-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0043e-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0043e-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0043e-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0043e-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0043e-140">INPUTS</span></span>

### <span data-ttu-id="0043e-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="0043e-141">None</span></span>

<span data-ttu-id="0043e-142">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0043e-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0043e-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0043e-143">OUTPUTS</span></span>

### <span data-ttu-id="0043e-144">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="0043e-144">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="0043e-145">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0043e-145">NOTES</span></span>

## <span data-ttu-id="0043e-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0043e-146">RELATED LINKS</span></span>

[<span data-ttu-id="0043e-147">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="0043e-147">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="0043e-148">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="0043e-148">Update-FormatData</span></span>](Update-FormatData.md)
