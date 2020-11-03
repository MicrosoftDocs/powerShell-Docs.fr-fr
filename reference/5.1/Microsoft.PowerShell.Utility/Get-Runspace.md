---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: fb1076e7bb0843fe7208d00e51e19063c27dfa68
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203257"
---
# <span data-ttu-id="e5e99-103">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="e5e99-103">Get-Runspace</span></span>

## <span data-ttu-id="e5e99-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e5e99-104">SYNOPSIS</span></span>
<span data-ttu-id="e5e99-105">Obtient les instances d’exécution actifs dans un processus hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5e99-105">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="e5e99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e5e99-106">SYNTAX</span></span>

### <span data-ttu-id="e5e99-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e5e99-107">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e5e99-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e5e99-108">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="e5e99-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e5e99-109">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="e5e99-110">Description</span><span class="sxs-lookup"><span data-stu-id="e5e99-110">DESCRIPTION</span></span>

<span data-ttu-id="e5e99-111">L' `Get-Runspace` applet de commande obtient les instances d’exécution actifs dans un processus hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5e99-111">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="e5e99-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e5e99-112">EXAMPLES</span></span>

### <span data-ttu-id="e5e99-113">Exemple 1 : accéder à instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="e5e99-113">Example 1: Get runspaces</span></span>

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### <span data-ttu-id="e5e99-114">Exemple 2 : récupération de l’instance d’exécution par ID</span><span class="sxs-lookup"><span data-stu-id="e5e99-114">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="e5e99-115">Exemple 3 : récupération de l’instance d’exécution par nom</span><span class="sxs-lookup"><span data-stu-id="e5e99-115">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="e5e99-116">Exemple 4 : récupération de l’instance d’exécution par InstanceId</span><span class="sxs-lookup"><span data-stu-id="e5e99-116">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="e5e99-117">Dans cet exemple, nous identifions une instance d’exécution disponible à l’aide du `Name` paramètre et stockons l’objet de retour dans la variable `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="e5e99-117">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="e5e99-118">Cela vous permet d’utiliser les propriétés de l' **instance d’exécution** dans les exécutions suivantes de `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="e5e99-118">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="e5e99-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e5e99-119">PARAMETERS</span></span>

### <span data-ttu-id="e5e99-120">-Id</span><span class="sxs-lookup"><span data-stu-id="e5e99-120">-Id</span></span>

<span data-ttu-id="e5e99-121">Spécifie l’ID d’une instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="e5e99-121">Specifies the Id of a runspace</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5e99-122">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e5e99-122">-InstanceId</span></span>

<span data-ttu-id="e5e99-123">Spécifie le GUID de l’ID d’instance d’un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e5e99-123">Specifies the instance ID GUID of a running job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5e99-124">-Name</span><span class="sxs-lookup"><span data-stu-id="e5e99-124">-Name</span></span>

<span data-ttu-id="e5e99-125">Spécifie le nom d’une instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="e5e99-125">Specifies the Name of a runspace</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5e99-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e5e99-126">CommonParameters</span></span>

<span data-ttu-id="e5e99-127">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e5e99-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e5e99-128">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e5e99-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e5e99-129">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e5e99-129">INPUTS</span></span>

## <span data-ttu-id="e5e99-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e5e99-130">OUTPUTS</span></span>

### <span data-ttu-id="e5e99-131">System. Management. Automation. instances d’exécution. Runspace</span><span class="sxs-lookup"><span data-stu-id="e5e99-131">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="e5e99-132">Vous pouvez diriger les résultats d’une `Get-Runspace` commande vers `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="e5e99-132">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="e5e99-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e5e99-133">NOTES</span></span>

## <span data-ttu-id="e5e99-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e5e99-134">RELATED LINKS</span></span>

[<span data-ttu-id="e5e99-135">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="e5e99-135">Debug-Runspace</span></span>](Debug-Runspace.md)
