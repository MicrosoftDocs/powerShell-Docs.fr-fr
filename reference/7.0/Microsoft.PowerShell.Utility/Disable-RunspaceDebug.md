---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 58665cd06e39784721be9a538b70dd8b7c2a1c14
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201558"
---
# <span data-ttu-id="f7c81-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f7c81-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="f7c81-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f7c81-104">SYNOPSIS</span></span>
<span data-ttu-id="f7c81-105">Désactive le débogage sur un ou plusieurs instances d’exécution et libère tout arrêt du débogueur en attente.</span><span class="sxs-lookup"><span data-stu-id="f7c81-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="f7c81-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7c81-106">SYNTAX</span></span>

### <span data-ttu-id="f7c81-107">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f7c81-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f7c81-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7c81-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="f7c81-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7c81-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="f7c81-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7c81-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="f7c81-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7c81-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="f7c81-112">Description</span><span class="sxs-lookup"><span data-stu-id="f7c81-112">DESCRIPTION</span></span>

<span data-ttu-id="f7c81-113">L' `Disable-RunspaceDebug` applet de commande désactive le débogage sur un ou plusieurs instances d’exécution et libère l’arrêt du débogueur en attente.</span><span class="sxs-lookup"><span data-stu-id="f7c81-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="f7c81-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f7c81-114">EXAMPLES</span></span>

### <span data-ttu-id="f7c81-115">1 : désactiver le débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="f7c81-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="f7c81-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7c81-116">PARAMETERS</span></span>

### <span data-ttu-id="f7c81-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="f7c81-117">-AppDomainName</span></span>

<span data-ttu-id="f7c81-118">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7c81-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="f7c81-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="f7c81-119">-ProcessName</span></span>

<span data-ttu-id="f7c81-120">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7c81-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="f7c81-121">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="f7c81-121">-Runspace</span></span>

<span data-ttu-id="f7c81-122">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="f7c81-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="f7c81-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="f7c81-123">-RunspaceId</span></span>

<span data-ttu-id="f7c81-124">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="f7c81-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="f7c81-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="f7c81-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="f7c81-126">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="f7c81-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="f7c81-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="f7c81-127">-RunspaceName</span></span>

<span data-ttu-id="f7c81-128">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="f7c81-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="f7c81-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7c81-129">CommonParameters</span></span>

<span data-ttu-id="f7c81-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7c81-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7c81-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f7c81-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7c81-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f7c81-132">INPUTS</span></span>

## <span data-ttu-id="f7c81-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f7c81-133">OUTPUTS</span></span>

## <span data-ttu-id="f7c81-134">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f7c81-134">NOTES</span></span>

## <span data-ttu-id="f7c81-135">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f7c81-135">RELATED LINKS</span></span>

[<span data-ttu-id="f7c81-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f7c81-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="f7c81-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f7c81-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
