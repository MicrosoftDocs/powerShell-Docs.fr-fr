---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: 627b1446f37b951eb5455ca1d9b41ec5453e2cc7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201662"
---
# <span data-ttu-id="d0957-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="d0957-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="d0957-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d0957-104">SYNOPSIS</span></span>
<span data-ttu-id="d0957-105">Affiche les options de débogage d’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d0957-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="d0957-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d0957-106">SYNTAX</span></span>

### <span data-ttu-id="d0957-107">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d0957-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d0957-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="d0957-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="d0957-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d0957-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="d0957-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d0957-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="d0957-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d0957-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d0957-112">Description</span><span class="sxs-lookup"><span data-stu-id="d0957-112">DESCRIPTION</span></span>

<span data-ttu-id="d0957-113">L' `Get-RunspaceDebug` applet de commande affiche les options de débogage d’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d0957-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="d0957-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d0957-114">EXAMPLES</span></span>

### <span data-ttu-id="d0957-115">1 : afficher l’état du débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="d0957-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="d0957-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d0957-116">PARAMETERS</span></span>

### <span data-ttu-id="d0957-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="d0957-117">-AppDomainName</span></span>

<span data-ttu-id="d0957-118">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0957-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="d0957-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="d0957-119">-ProcessName</span></span>

<span data-ttu-id="d0957-120">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0957-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="d0957-121">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="d0957-121">-Runspace</span></span>

<span data-ttu-id="d0957-122">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="d0957-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="d0957-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="d0957-123">-RunspaceId</span></span>

<span data-ttu-id="d0957-124">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="d0957-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="d0957-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="d0957-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="d0957-126">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="d0957-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="d0957-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="d0957-127">-RunspaceName</span></span>

<span data-ttu-id="d0957-128">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="d0957-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="d0957-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d0957-129">CommonParameters</span></span>

<span data-ttu-id="d0957-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d0957-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d0957-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d0957-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d0957-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d0957-132">INPUTS</span></span>

## <span data-ttu-id="d0957-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d0957-133">OUTPUTS</span></span>

## <span data-ttu-id="d0957-134">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d0957-134">NOTES</span></span>

## <span data-ttu-id="d0957-135">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d0957-135">RELATED LINKS</span></span>

[<span data-ttu-id="d0957-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="d0957-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="d0957-137">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="d0957-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)
