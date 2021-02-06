---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: dbc036562da0172dc4406f169891d2cd1c5e4098
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595722"
---
# <span data-ttu-id="3622a-102">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="3622a-102">Get-DscResource</span></span>

## <span data-ttu-id="3622a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3622a-103">SYNOPSIS</span></span>
<span data-ttu-id="3622a-104">Obtient les ressources DSC (Desired State Configuration) présentes sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3622a-104">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="3622a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3622a-105">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="3622a-106">Description</span><span class="sxs-lookup"><span data-stu-id="3622a-106">DESCRIPTION</span></span>

<span data-ttu-id="3622a-107">L' `Get-DscResource` applet de commande récupère les ressources DSC PowerShell présentes sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3622a-107">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="3622a-108">Cette applet de commande Découvre uniquement les ressources installées dans le PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="3622a-108">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="3622a-109">Il présente les détails des fournisseurs intégrés et personnalisés, qui sont créés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3622a-109">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="3622a-110">Cette applet de commande affiche également des détails sur les ressources composites, qui sont des configurations qui sont empaquetées sous forme de module ou créées au moment de l’exécution dans la session.</span><span class="sxs-lookup"><span data-stu-id="3622a-110">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="3622a-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3622a-111">EXAMPLES</span></span>

### <span data-ttu-id="3622a-112">Exemple 1 : récupération de toutes les ressources sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="3622a-112">Example 1: Get all resources on the local computer</span></span>

```powershell
Get-DscResource
```

<span data-ttu-id="3622a-113">Cette commande obtient toutes les ressources sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3622a-113">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="3622a-114">Exemple 2 : obtenir une ressource en spécifiant le nom</span><span class="sxs-lookup"><span data-stu-id="3622a-114">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="3622a-115">Cette commande obtient la ressource WindowsFeature.</span><span class="sxs-lookup"><span data-stu-id="3622a-115">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="3622a-116">Exemple 3 : obtenir toutes les ressources d’un module</span><span class="sxs-lookup"><span data-stu-id="3622a-116">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="3622a-117">Cette commande obtient toutes les ressources du module xHyper-V.</span><span class="sxs-lookup"><span data-stu-id="3622a-117">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="3622a-118">Exemple 4 : obtenir une ressource à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="3622a-118">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="3622a-119">Cette commande obtient toutes les ressources qui correspondent au modèle de caractère générique spécifié par le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="3622a-119">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="3622a-120">Exemple 5 : obtenir une syntaxe de ressource</span><span class="sxs-lookup"><span data-stu-id="3622a-120">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="3622a-121">Cette commande obtient la ressource WindowsFeature et affiche sa syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3622a-121">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="3622a-122">Exemple 6 : obtenir toutes les propriétés d’une ressource</span><span class="sxs-lookup"><span data-stu-id="3622a-122">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="3622a-123">Cette commande obtient la ressource User, puis utilise l'opérateur pipeline pour retourner toutes ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="3622a-123">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="3622a-124">Exemple 7 : obtenir toutes les ressources d’un module spécifié avec une version spécifiée</span><span class="sxs-lookup"><span data-stu-id="3622a-124">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="3622a-125">Cette commande obtient toutes les ressources du module xHyper-V avec la version 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="3622a-125">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="3622a-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3622a-126">PARAMETERS</span></span>

### <span data-ttu-id="3622a-127">-Module</span><span class="sxs-lookup"><span data-stu-id="3622a-127">-Module</span></span>

<span data-ttu-id="3622a-128">Spécifie le nom ou le nom complet du module pour lequel afficher la ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="3622a-128">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3622a-129">-Name</span><span class="sxs-lookup"><span data-stu-id="3622a-129">-Name</span></span>

<span data-ttu-id="3622a-130">Spécifie un tableau de noms de la ressource DSC à afficher.</span><span class="sxs-lookup"><span data-stu-id="3622a-130">Specifies an array of names of the DSC resource to view.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3622a-131">-Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3622a-131">-Syntax</span></span>

<span data-ttu-id="3622a-132">Indique que l’applet de commande retourne la vue de la syntaxe des ressources DSC spécifiées.</span><span class="sxs-lookup"><span data-stu-id="3622a-132">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="3622a-133">La syntaxe retournée montre comment utiliser les ressources dans un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3622a-133">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3622a-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3622a-134">CommonParameters</span></span>

<span data-ttu-id="3622a-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3622a-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3622a-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3622a-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3622a-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3622a-137">INPUTS</span></span>

### <span data-ttu-id="3622a-138">System.String[]</span><span class="sxs-lookup"><span data-stu-id="3622a-138">System.String[]</span></span>

### <span data-ttu-id="3622a-139">System.Object</span><span class="sxs-lookup"><span data-stu-id="3622a-139">System.Object</span></span>

## <span data-ttu-id="3622a-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3622a-140">OUTPUTS</span></span>

### <span data-ttu-id="3622a-141">Microsoft. PowerShell. DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="3622a-141">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="3622a-142">string[]</span><span class="sxs-lookup"><span data-stu-id="3622a-142">string[]</span></span>

## <span data-ttu-id="3622a-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3622a-143">NOTES</span></span>

## <span data-ttu-id="3622a-144">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3622a-144">RELATED LINKS</span></span>

[<span data-ttu-id="3622a-145">Vue d’ensemble de la configuration d’état souhaité PowerShell</span><span class="sxs-lookup"><span data-stu-id="3622a-145">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="3622a-146">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="3622a-146">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

