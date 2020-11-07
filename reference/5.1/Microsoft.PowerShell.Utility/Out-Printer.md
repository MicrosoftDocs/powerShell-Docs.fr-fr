---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: babe054f6ee643bc721b210556c46ed15dcdc00c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344658"
---
# <span data-ttu-id="4549e-103">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="4549e-103">Out-Printer</span></span>

## <span data-ttu-id="4549e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4549e-104">SYNOPSIS</span></span>
<span data-ttu-id="4549e-105">Envoie la sortie vers une imprimante.</span><span class="sxs-lookup"><span data-stu-id="4549e-105">Sends output to a printer.</span></span>

## <span data-ttu-id="4549e-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4549e-106">SYNTAX</span></span>

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="4549e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4549e-107">DESCRIPTION</span></span>

<span data-ttu-id="4549e-108">L' `Out-Printer` applet de commande envoie la sortie vers l’imprimante par défaut ou vers une autre imprimante, si celle-ci est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4549e-108">The `Out-Printer` cmdlet sends output to the default printer or to an alternate printer, if one is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="4549e-109">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="4549e-109">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="4549e-110">Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="4549e-110">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="4549e-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4549e-111">EXAMPLES</span></span>

### <span data-ttu-id="4549e-112">Exemple 1 : envoyer un fichier à imprimer sur l’imprimante par défaut</span><span class="sxs-lookup"><span data-stu-id="4549e-112">Example 1 - Send a file to be printed on the default printer</span></span>

<span data-ttu-id="4549e-113">Cet exemple montre comment imprimer un fichier, même si `Out-Printer` n’a pas de paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="4549e-113">This example shows how to print a file, even though `Out-Printer` does not have a **Path** parameter.</span></span>

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

<span data-ttu-id="4549e-114">`Get-Content`Obtient le contenu du `readme.txt` fichier dans le répertoire actif et le `Out-Printer` dirige vers, ce qui l’envoie à l’imprimante par défaut.</span><span class="sxs-lookup"><span data-stu-id="4549e-114">`Get-Content`gets the contents of the `readme.txt` file in the current directory and pipes it to `Out-Printer`, which sends it to the default printer.</span></span>

### <span data-ttu-id="4549e-115">Exemple 2 : imprimer une chaîne sur une imprimante distante</span><span class="sxs-lookup"><span data-stu-id="4549e-115">Example 2: Print a string to a remote printer</span></span>

<span data-ttu-id="4549e-116">Cet exemple imprime `Hello, World` sur l’imprimante de **couleur PRT-6B** sur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="4549e-116">This example prints `Hello, World` to the **Prt-6B Color** printer on Server01.</span></span>

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

<span data-ttu-id="4549e-117">Le paramètre **Name** sélectionne une imprimante spécifique, plutôt que la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4549e-117">The **Name** parameter selects a specific printer, rather than the default.</span></span>

### <span data-ttu-id="4549e-118">Exemple 3 : imprimer une rubrique d’aide sur l’imprimante par défaut</span><span class="sxs-lookup"><span data-stu-id="4549e-118">Example 3 - Print a help topic to the default printer</span></span>

<span data-ttu-id="4549e-119">Cet exemple imprime la version complète de la rubrique d’aide pour `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="4549e-119">This example prints the full version of the Help topic for `Get-CimInstance`.</span></span>

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

<span data-ttu-id="4549e-120">`Get-Help` Obtient la version complète de la rubrique d’aide de `Get-CimInstance` et la stocke dans la `$H` variable.</span><span class="sxs-lookup"><span data-stu-id="4549e-120">`Get-Help` gets the full version of the Help topic for `Get-CimInstance` and stores it in the `$H` variable.</span></span> <span data-ttu-id="4549e-121">Le paramètre **InputObject** passe la valeur de `$H` à `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="4549e-121">The **InputObject** parameter passes the value of `$H` to `Out-Printer`.</span></span>

## <span data-ttu-id="4549e-122">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="4549e-122">PARAMETERS</span></span>

### <span data-ttu-id="4549e-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4549e-123">-InputObject</span></span>

<span data-ttu-id="4549e-124">Spécifie les objets à envoyer à l'imprimante.</span><span class="sxs-lookup"><span data-stu-id="4549e-124">Specifies the objects to be sent to the printer.</span></span> <span data-ttu-id="4549e-125">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="4549e-125">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4549e-126">-Name</span><span class="sxs-lookup"><span data-stu-id="4549e-126">-Name</span></span>

<span data-ttu-id="4549e-127">Envoie la sortie vers l’imprimante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4549e-127">Sends the output to the specified printer.</span></span> <span data-ttu-id="4549e-128">Le **nom du paramètre est facultatif** .</span><span class="sxs-lookup"><span data-stu-id="4549e-128">The parameter name **Name** is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4549e-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4549e-129">CommonParameters</span></span>

<span data-ttu-id="4549e-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4549e-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4549e-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4549e-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4549e-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4549e-132">INPUTS</span></span>

### <span data-ttu-id="4549e-133">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4549e-133">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4549e-134">Vous pouvez diriger n’importe quel objet vers `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="4549e-134">You can pipe any object to `Out-Printer`.</span></span>

## <span data-ttu-id="4549e-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4549e-135">OUTPUTS</span></span>

### <span data-ttu-id="4549e-136">Aucun</span><span class="sxs-lookup"><span data-stu-id="4549e-136">None</span></span>

<span data-ttu-id="4549e-137">`Out-Printer` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="4549e-137">`Out-Printer` does not return any objects.</span></span>

## <span data-ttu-id="4549e-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4549e-138">NOTES</span></span>

<span data-ttu-id="4549e-139">Les applets de commande qui contiennent le `Out` verbe ne mettent pas en forme les objets.</span><span class="sxs-lookup"><span data-stu-id="4549e-139">The cmdlets that contain the `Out` verb do not format objects.</span></span> <span data-ttu-id="4549e-140">Ils les affichent et les envoient à la destination d’affichage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4549e-140">They just render them and send them to the specified display destination.</span></span> <span data-ttu-id="4549e-141">Si vous envoyez un objet non mis en forme à une applet de commande `Out` , l’applet de commande l’envoie à une applet de commande de mise en forme avant de le restituer.</span><span class="sxs-lookup"><span data-stu-id="4549e-141">If you send an unformatted object to an `Out` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="4549e-142">`Out-Printer` envoie des données à l’imprimante, mais n’émet pas d’objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="4549e-142">`Out-Printer` sends data to the printer, but does not emit any output objects to the pipeline.</span></span> <span data-ttu-id="4549e-143">Si vous dirigez la sortie de `Out-Printer` vers `Get-Member` , `Get-Member` signale qu’aucun objet n’a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="4549e-143">If you pipe the output of `Out-Printer` to `Get-Member`, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="4549e-144">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4549e-144">RELATED LINKS</span></span>

[<span data-ttu-id="4549e-145">Out-File</span><span class="sxs-lookup"><span data-stu-id="4549e-145">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="4549e-146">Out-String</span><span class="sxs-lookup"><span data-stu-id="4549e-146">Out-String</span></span>](Out-String.md)
