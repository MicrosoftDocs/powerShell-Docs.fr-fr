---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: ''
schema: 2.0.0
ms.openlocfilehash: 34998e7c4a6876821df949019970dc1d87297397
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208550"
---
# <span data-ttu-id="2d1a5-101">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="2d1a5-101">Get-PSSubsystem</span></span>

## <span data-ttu-id="2d1a5-102">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2d1a5-102">SYNOPSIS</span></span>
<span data-ttu-id="2d1a5-103">Récupère des informations sur les sous-systèmes enregistrés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-103">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="2d1a5-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2d1a5-104">SYNTAX</span></span>

### <span data-ttu-id="2d1a5-105">GetAllSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2d1a5-105">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="2d1a5-106">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="2d1a5-106">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="2d1a5-107">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="2d1a5-107">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="2d1a5-108">Description</span><span class="sxs-lookup"><span data-stu-id="2d1a5-108">DESCRIPTION</span></span>

<span data-ttu-id="2d1a5-109">Récupère des informations sur les sous-systèmes enregistrés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-109">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="2d1a5-110">Il s’agit d’une fonctionnalité expérimentale.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-110">This is an experimental feature.</span></span> <span data-ttu-id="2d1a5-111">Cette applet de commande est disponible uniquement lorsque la `PSSubsystemPluginModel` fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-111">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="2d1a5-112">Pour plus d’informations, consultez [utilisation des fonctionnalités expérimentales](/powershell/scripting/learn/experimental-features).</span><span class="sxs-lookup"><span data-stu-id="2d1a5-112">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="2d1a5-113">La fonctionnalité permet de diviser les composants de `System.Management.Automation.dll` en sous-systèmes individuels qui résident dans leur propre assembly.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-113">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="2d1a5-114">Cette division réduit l’encombrement de disque du moteur PowerShell principal et permet à ces composants de devenir des fonctionnalités facultatives pour une installation PowerShell minimale.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-114">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="2d1a5-115">Actuellement, seul le sous-système **CommandPredictor** est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-115">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="2d1a5-116">Ce sous-système est utilisé avec le module PSReadLine pour fournir des plug-ins de prédiction personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-116">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="2d1a5-117">À l’avenir, **Job** , **CommandCompleter** , **Remoting** et d’autres composants pourraient être divisés en assemblys de sous-système en dehors de `System.Management.Automation.dll`.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-117">In future, **Job** , **CommandCompleter** , **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="2d1a5-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2d1a5-118">EXAMPLES</span></span>

### <span data-ttu-id="2d1a5-119">Exemple 1 : afficher tous les sous-systèmes disponibles</span><span class="sxs-lookup"><span data-stu-id="2d1a5-119">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="2d1a5-120">Exemple 2 : afficher tous les sous-systèmes disponibles d’un type spécifique</span><span class="sxs-lookup"><span data-stu-id="2d1a5-120">Example 2 - Display all available subsystems of a specific kind</span></span>

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

## <span data-ttu-id="2d1a5-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d1a5-121">PARAMETERS</span></span>

### <span data-ttu-id="2d1a5-122">-Genre</span><span class="sxs-lookup"><span data-stu-id="2d1a5-122">-Kind</span></span>


<span data-ttu-id="2d1a5-123">Spécifie le type de sous-système à retourner.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-123">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="2d1a5-124">Les valeurs valides sont : `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="2d1a5-124">Valid values are: `CommandPredictor`.</span></span>

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

### <span data-ttu-id="2d1a5-125">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="2d1a5-125">-SubsystemType</span></span>

<span data-ttu-id="2d1a5-126">Spécifie le type de sous-système à retourner.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-126">Specifies the type of subsystem to be returned.</span></span>

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

### <span data-ttu-id="2d1a5-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d1a5-127">CommonParameters</span></span>

<span data-ttu-id="2d1a5-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2d1a5-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d1a5-129">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2d1a5-129">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d1a5-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2d1a5-130">INPUTS</span></span>

### <span data-ttu-id="2d1a5-131">System. Management. Automation. Subsystem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="2d1a5-131">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="2d1a5-132">System.Type</span><span class="sxs-lookup"><span data-stu-id="2d1a5-132">System.Type</span></span>

## <span data-ttu-id="2d1a5-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2d1a5-133">OUTPUTS</span></span>

### <span data-ttu-id="2d1a5-134">System. Management. Automation. Subsystem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="2d1a5-134">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="2d1a5-135">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2d1a5-135">NOTES</span></span>

## <span data-ttu-id="2d1a5-136">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2d1a5-136">RELATED LINKS</span></span>

[<span data-ttu-id="2d1a5-137">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="2d1a5-137">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="2d1a5-138">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="2d1a5-138">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="2d1a5-139">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="2d1a5-139">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="2d1a5-140">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="2d1a5-140">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="2d1a5-141">Utilisation des fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="2d1a5-141">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
