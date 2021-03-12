---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssubsystem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSubsystem
ms.openlocfilehash: 1e08715562ab5a5b52193dacdd2c48cacb4540e8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195530"
---
# <span data-ttu-id="677de-102">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="677de-102">Get-PSSubsystem</span></span>

## <span data-ttu-id="677de-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="677de-103">SYNOPSIS</span></span>
<span data-ttu-id="677de-104">Récupère des informations sur les sous-systèmes enregistrés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="677de-104">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="677de-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="677de-105">SYNTAX</span></span>

### <span data-ttu-id="677de-106">GetAllSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="677de-106">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="677de-107">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="677de-107">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="677de-108">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="677de-108">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="677de-109">Description</span><span class="sxs-lookup"><span data-stu-id="677de-109">DESCRIPTION</span></span>

<span data-ttu-id="677de-110">Récupère des informations sur les sous-systèmes enregistrés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="677de-110">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="677de-111">Il s’agit d’une fonctionnalité expérimentale.</span><span class="sxs-lookup"><span data-stu-id="677de-111">This is an experimental feature.</span></span> <span data-ttu-id="677de-112">Cette applet de commande est disponible uniquement lorsque la `PSSubsystemPluginModel` fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="677de-112">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="677de-113">Pour plus d’informations, consultez [Utilisation des fonctionnalités expérimentales](/powershell/scripting/learn/experimental-features).</span><span class="sxs-lookup"><span data-stu-id="677de-113">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="677de-114">La fonctionnalité permet de diviser les composants de `System.Management.Automation.dll` en sous-systèmes individuels qui résident dans leur propre assembly.</span><span class="sxs-lookup"><span data-stu-id="677de-114">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="677de-115">Cette division réduit l’encombrement de disque du moteur PowerShell principal et permet à ces composants de devenir des fonctionnalités facultatives pour une installation PowerShell minimale.</span><span class="sxs-lookup"><span data-stu-id="677de-115">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="677de-116">Actuellement, seul le sous-système **CommandPredictor** est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="677de-116">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="677de-117">Ce sous-système est utilisé avec le module PSReadLine pour fournir des plug-ins de prédiction personnalisés.</span><span class="sxs-lookup"><span data-stu-id="677de-117">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="677de-118">À l’avenir, **Job**, **CommandCompleter**, **Remoting** et d’autres composants pourraient être divisés en assemblys de sous-système en dehors de `System.Management.Automation.dll`.</span><span class="sxs-lookup"><span data-stu-id="677de-118">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="677de-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="677de-119">EXAMPLES</span></span>

### <span data-ttu-id="677de-120">Exemple 1 : afficher tous les sous-systèmes disponibles</span><span class="sxs-lookup"><span data-stu-id="677de-120">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="677de-121">Exemple 2 : afficher tous les sous-systèmes disponibles d’un type spécifique</span><span class="sxs-lookup"><span data-stu-id="677de-121">Example 2 - Display all available subsystems of a specific kind</span></span>

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## <span data-ttu-id="677de-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="677de-122">PARAMETERS</span></span>

### <span data-ttu-id="677de-123">-Genre</span><span class="sxs-lookup"><span data-stu-id="677de-123">-Kind</span></span>


<span data-ttu-id="677de-124">Spécifie le type de sous-système à retourner.</span><span class="sxs-lookup"><span data-stu-id="677de-124">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="677de-125">Les valeurs valides sont : `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="677de-125">Valid values are: `CommandPredictor`.</span></span>

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="677de-126">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="677de-126">-SubsystemType</span></span>

<span data-ttu-id="677de-127">Spécifie le type de sous-système à retourner.</span><span class="sxs-lookup"><span data-stu-id="677de-127">Specifies the type of subsystem to be returned.</span></span>

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="677de-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="677de-128">CommonParameters</span></span>

<span data-ttu-id="677de-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="677de-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="677de-130">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="677de-130">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="677de-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="677de-131">INPUTS</span></span>

### <span data-ttu-id="677de-132">System. Management. Automation. Subsystem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="677de-132">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="677de-133">System.Type</span><span class="sxs-lookup"><span data-stu-id="677de-133">System.Type</span></span>

## <span data-ttu-id="677de-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="677de-134">OUTPUTS</span></span>

### <span data-ttu-id="677de-135">System. Management. Automation. Subsystem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="677de-135">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="677de-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="677de-136">NOTES</span></span>

## <span data-ttu-id="677de-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="677de-137">RELATED LINKS</span></span>

[<span data-ttu-id="677de-138">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="677de-138">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="677de-139">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="677de-139">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="677de-140">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="677de-140">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="677de-141">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="677de-141">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="677de-142">Utilisation des fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="677de-142">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
