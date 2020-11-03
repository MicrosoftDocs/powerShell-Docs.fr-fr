---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: ad9a08b3936044ef74c83b5e0d0cff146bf43e3f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204670"
---
# <span data-ttu-id="5e49e-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5e49e-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="5e49e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5e49e-104">SYNOPSIS</span></span>
<span data-ttu-id="5e49e-105">Désactive le débogage sur un ou plusieurs instances d’exécution et libère tout arrêt du débogueur en attente.</span><span class="sxs-lookup"><span data-stu-id="5e49e-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="5e49e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e49e-106">SYNTAX</span></span>

### <span data-ttu-id="5e49e-107">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5e49e-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="5e49e-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="5e49e-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="5e49e-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5e49e-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="5e49e-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5e49e-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="5e49e-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="5e49e-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5e49e-112">Description</span><span class="sxs-lookup"><span data-stu-id="5e49e-112">DESCRIPTION</span></span>

<span data-ttu-id="5e49e-113">L' `Disable-RunspaceDebug` applet de commande désactive le débogage sur un ou plusieurs instances d’exécution et libère l’arrêt du débogueur en attente.</span><span class="sxs-lookup"><span data-stu-id="5e49e-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="5e49e-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5e49e-114">EXAMPLES</span></span>

### <span data-ttu-id="5e49e-115">1 : désactiver le débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="5e49e-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="5e49e-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5e49e-116">PARAMETERS</span></span>

### <span data-ttu-id="5e49e-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="5e49e-117">-AppDomainName</span></span>

<span data-ttu-id="5e49e-118">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e49e-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="5e49e-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="5e49e-119">-ProcessName</span></span>

<span data-ttu-id="5e49e-120">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e49e-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="5e49e-121">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="5e49e-121">-Runspace</span></span>

<span data-ttu-id="5e49e-122">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="5e49e-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="5e49e-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="5e49e-123">-RunspaceId</span></span>

<span data-ttu-id="5e49e-124">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="5e49e-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="5e49e-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="5e49e-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="5e49e-126">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="5e49e-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="5e49e-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="5e49e-127">-RunspaceName</span></span>

<span data-ttu-id="5e49e-128">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="5e49e-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="5e49e-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e49e-129">CommonParameters</span></span>

<span data-ttu-id="5e49e-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e49e-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e49e-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5e49e-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e49e-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5e49e-132">INPUTS</span></span>

## <span data-ttu-id="5e49e-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5e49e-133">OUTPUTS</span></span>

## <span data-ttu-id="5e49e-134">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5e49e-134">NOTES</span></span>

## <span data-ttu-id="5e49e-135">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5e49e-135">RELATED LINKS</span></span>

[<span data-ttu-id="5e49e-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5e49e-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="5e49e-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5e49e-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
