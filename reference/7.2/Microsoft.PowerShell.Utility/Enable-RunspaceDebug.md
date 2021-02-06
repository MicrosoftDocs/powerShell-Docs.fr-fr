---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 26ab9b9135eedafa0238eab5c07aa7abb7880ed4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597546"
---
# <span data-ttu-id="2aedf-102">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2aedf-102">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="2aedf-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2aedf-103">SYNOPSIS</span></span>
<span data-ttu-id="2aedf-104">Active le débogage sur instances d’exécution où un point d’arrêt est conservé jusqu’à ce qu’un débogueur soit attaché.</span><span class="sxs-lookup"><span data-stu-id="2aedf-104">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="2aedf-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2aedf-105">SYNTAX</span></span>

### <span data-ttu-id="2aedf-106">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2aedf-106">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2aedf-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="2aedf-107">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="2aedf-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2aedf-108">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="2aedf-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2aedf-109">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="2aedf-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="2aedf-110">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2aedf-111">Description</span><span class="sxs-lookup"><span data-stu-id="2aedf-111">DESCRIPTION</span></span>

<span data-ttu-id="2aedf-112">L' `Enable-RunspaceDebug` applet de commande active le débogage sur instances d’exécution où un point d’arrêt est conservé jusqu’à ce qu’un débogueur soit attaché.</span><span class="sxs-lookup"><span data-stu-id="2aedf-112">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="2aedf-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2aedf-113">EXAMPLES</span></span>

### <span data-ttu-id="2aedf-114">1 : activer le débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="2aedf-114">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="2aedf-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2aedf-115">PARAMETERS</span></span>

### <span data-ttu-id="2aedf-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="2aedf-116">-AppDomainName</span></span>

<span data-ttu-id="2aedf-117">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2aedf-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="2aedf-118">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="2aedf-118">-BreakAll</span></span>

<span data-ttu-id="2aedf-119">Entraîne l’arrêt d’une commande ou d’un script en cours d’exécution dans l’instance d’exécution, qu’un débogueur soit actuellement attaché ou non.</span><span class="sxs-lookup"><span data-stu-id="2aedf-119">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="2aedf-120">Le script ou la commande restera arrêté jusqu’à ce qu’un débogueur soit attaché pour déboguer le point d’arrêt actuel.</span><span class="sxs-lookup"><span data-stu-id="2aedf-120">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

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

### <span data-ttu-id="2aedf-121">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="2aedf-121">-ProcessName</span></span>

<span data-ttu-id="2aedf-122">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2aedf-122">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="2aedf-123">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="2aedf-123">-Runspace</span></span>

<span data-ttu-id="2aedf-124">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="2aedf-124">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="2aedf-125">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="2aedf-125">-RunspaceId</span></span>

<span data-ttu-id="2aedf-126">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="2aedf-126">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="2aedf-127">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="2aedf-127">-RunspaceInstanceId</span></span>

<span data-ttu-id="2aedf-128">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="2aedf-128">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="2aedf-129">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="2aedf-129">-RunspaceName</span></span>

<span data-ttu-id="2aedf-130">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="2aedf-130">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="2aedf-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2aedf-131">CommonParameters</span></span>

<span data-ttu-id="2aedf-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2aedf-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2aedf-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2aedf-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2aedf-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2aedf-134">INPUTS</span></span>

## <span data-ttu-id="2aedf-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2aedf-135">OUTPUTS</span></span>

## <span data-ttu-id="2aedf-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2aedf-136">NOTES</span></span>

## <span data-ttu-id="2aedf-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2aedf-137">RELATED LINKS</span></span>

[<span data-ttu-id="2aedf-138">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2aedf-138">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="2aedf-139">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2aedf-139">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

