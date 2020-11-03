---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: e89efb5363df5843e536a9c58db331291c07b7b0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204206"
---
# <span data-ttu-id="efc20-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="efc20-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="efc20-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="efc20-104">SYNOPSIS</span></span>
<span data-ttu-id="efc20-105">Active le débogage sur instances d’exécution où un point d’arrêt est conservé jusqu’à ce qu’un débogueur soit attaché.</span><span class="sxs-lookup"><span data-stu-id="efc20-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="efc20-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="efc20-106">SYNTAX</span></span>

### <span data-ttu-id="efc20-107">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="efc20-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="efc20-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="efc20-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="efc20-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="efc20-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="efc20-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="efc20-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="efc20-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="efc20-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="efc20-112">Description</span><span class="sxs-lookup"><span data-stu-id="efc20-112">DESCRIPTION</span></span>

<span data-ttu-id="efc20-113">L' `Enable-RunspaceDebug` applet de commande active le débogage sur instances d’exécution où un point d’arrêt est conservé jusqu’à ce qu’un débogueur soit attaché.</span><span class="sxs-lookup"><span data-stu-id="efc20-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="efc20-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="efc20-114">EXAMPLES</span></span>

### <span data-ttu-id="efc20-115">1 : activer le débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="efc20-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="efc20-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efc20-116">PARAMETERS</span></span>

### <span data-ttu-id="efc20-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="efc20-117">-AppDomainName</span></span>

<span data-ttu-id="efc20-118">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efc20-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="efc20-119">-BreakAll</span></span>

<span data-ttu-id="efc20-120">Entraîne l’arrêt d’une commande ou d’un script en cours d’exécution dans l’instance d’exécution, qu’un débogueur soit actuellement attaché ou non.</span><span class="sxs-lookup"><span data-stu-id="efc20-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="efc20-121">Le script ou la commande restera arrêté jusqu’à ce qu’un débogueur soit attaché pour déboguer le point d’arrêt actuel.</span><span class="sxs-lookup"><span data-stu-id="efc20-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-122">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="efc20-122">-ProcessName</span></span>

<span data-ttu-id="efc20-123">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efc20-123">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-124">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="efc20-124">-Runspace</span></span>

<span data-ttu-id="efc20-125">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="efc20-125">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="efc20-126">-RunspaceId</span></span>

<span data-ttu-id="efc20-127">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="efc20-127">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="efc20-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="efc20-129">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="efc20-129">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="efc20-130">-RunspaceName</span></span>

<span data-ttu-id="efc20-131">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="efc20-131">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efc20-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efc20-132">CommonParameters</span></span>

<span data-ttu-id="efc20-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="efc20-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efc20-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="efc20-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efc20-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="efc20-135">INPUTS</span></span>

## <span data-ttu-id="efc20-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="efc20-136">OUTPUTS</span></span>

## <span data-ttu-id="efc20-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="efc20-137">NOTES</span></span>

## <span data-ttu-id="efc20-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="efc20-138">RELATED LINKS</span></span>

[<span data-ttu-id="efc20-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="efc20-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="efc20-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="efc20-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

