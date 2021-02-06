---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 34843894cb6253e3d8e89072cf79cb9237d4fc19
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595926"
---
# <span data-ttu-id="90730-102">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="90730-102">Get-Runspace</span></span>

## <span data-ttu-id="90730-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="90730-103">SYNOPSIS</span></span>
<span data-ttu-id="90730-104">Obtient les instances d’exécution actifs dans un processus hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90730-104">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="90730-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="90730-105">SYNTAX</span></span>

### <span data-ttu-id="90730-106">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="90730-106">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="90730-107">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="90730-107">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="90730-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="90730-108">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="90730-109">Description</span><span class="sxs-lookup"><span data-stu-id="90730-109">DESCRIPTION</span></span>

<span data-ttu-id="90730-110">L' `Get-Runspace` applet de commande obtient les instances d’exécution actifs dans un processus hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90730-110">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="90730-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="90730-111">EXAMPLES</span></span>

### <span data-ttu-id="90730-112">Exemple 1 : accéder à instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="90730-112">Example 1: Get runspaces</span></span>

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

### <span data-ttu-id="90730-113">Exemple 2 : récupération de l’instance d’exécution par ID</span><span class="sxs-lookup"><span data-stu-id="90730-113">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="90730-114">Exemple 3 : récupération de l’instance d’exécution par nom</span><span class="sxs-lookup"><span data-stu-id="90730-114">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="90730-115">Exemple 4 : récupération de l’instance d’exécution par InstanceId</span><span class="sxs-lookup"><span data-stu-id="90730-115">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="90730-116">Dans cet exemple, nous identifions une instance d’exécution disponible à l’aide du `Name` paramètre et stockons l’objet de retour dans la variable `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="90730-116">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="90730-117">Cela vous permet d’utiliser les propriétés de l' **instance d’exécution** dans les exécutions suivantes de `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="90730-117">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="90730-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90730-118">PARAMETERS</span></span>

### <span data-ttu-id="90730-119">-Id</span><span class="sxs-lookup"><span data-stu-id="90730-119">-Id</span></span>

<span data-ttu-id="90730-120">Spécifie l’ID d’une instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="90730-120">Specifies the Id of a runspace</span></span>

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

### <span data-ttu-id="90730-121">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="90730-121">-InstanceId</span></span>

<span data-ttu-id="90730-122">Spécifie le GUID de l’ID d’instance d’un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="90730-122">Specifies the instance ID GUID of a running job.</span></span>

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

### <span data-ttu-id="90730-123">-Name</span><span class="sxs-lookup"><span data-stu-id="90730-123">-Name</span></span>

<span data-ttu-id="90730-124">Spécifie le nom d’une instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="90730-124">Specifies the Name of a runspace</span></span>

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

### <span data-ttu-id="90730-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90730-125">CommonParameters</span></span>

<span data-ttu-id="90730-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="90730-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90730-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="90730-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="90730-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="90730-128">INPUTS</span></span>

## <span data-ttu-id="90730-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="90730-129">OUTPUTS</span></span>

### <span data-ttu-id="90730-130">System. Management. Automation. instances d’exécution. Runspace</span><span class="sxs-lookup"><span data-stu-id="90730-130">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="90730-131">Vous pouvez diriger les résultats d’une `Get-Runspace` commande vers `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="90730-131">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="90730-132">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="90730-132">NOTES</span></span>

## <span data-ttu-id="90730-133">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="90730-133">RELATED LINKS</span></span>

[<span data-ttu-id="90730-134">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="90730-134">Debug-Runspace</span></span>](Debug-Runspace.md)

