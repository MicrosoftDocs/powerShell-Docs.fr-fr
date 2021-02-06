---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 589c8cb36a91de510ffc30973fe70729700ad020
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597974"
---
# <span data-ttu-id="8d000-102">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8d000-102">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="8d000-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8d000-103">SYNOPSIS</span></span>
<span data-ttu-id="8d000-104">Désactive le débogage sur un ou plusieurs instances d’exécution et libère tout arrêt du débogueur en attente.</span><span class="sxs-lookup"><span data-stu-id="8d000-104">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="8d000-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8d000-105">SYNTAX</span></span>

### <span data-ttu-id="8d000-106">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8d000-106">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8d000-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="8d000-107">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="8d000-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="8d000-108">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="8d000-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="8d000-109">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="8d000-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="8d000-110">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8d000-111">Description</span><span class="sxs-lookup"><span data-stu-id="8d000-111">DESCRIPTION</span></span>

<span data-ttu-id="8d000-112">L' `Disable-RunspaceDebug` applet de commande désactive le débogage sur un ou plusieurs instances d’exécution et libère l’arrêt du débogueur en attente.</span><span class="sxs-lookup"><span data-stu-id="8d000-112">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="8d000-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8d000-113">EXAMPLES</span></span>

### <span data-ttu-id="8d000-114">1 : désactiver le débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="8d000-114">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="8d000-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8d000-115">PARAMETERS</span></span>

### <span data-ttu-id="8d000-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="8d000-116">-AppDomainName</span></span>

<span data-ttu-id="8d000-117">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d000-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="8d000-118">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="8d000-118">-ProcessName</span></span>

<span data-ttu-id="8d000-119">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d000-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="8d000-120">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="8d000-120">-Runspace</span></span>

<span data-ttu-id="8d000-121">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="8d000-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="8d000-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="8d000-122">-RunspaceId</span></span>

<span data-ttu-id="8d000-123">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="8d000-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="8d000-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="8d000-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="8d000-125">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="8d000-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="8d000-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="8d000-126">-RunspaceName</span></span>

<span data-ttu-id="8d000-127">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="8d000-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="8d000-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d000-128">CommonParameters</span></span>

<span data-ttu-id="8d000-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8d000-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8d000-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8d000-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8d000-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8d000-131">INPUTS</span></span>

## <span data-ttu-id="8d000-132">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8d000-132">OUTPUTS</span></span>

## <span data-ttu-id="8d000-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8d000-133">NOTES</span></span>

## <span data-ttu-id="8d000-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8d000-134">RELATED LINKS</span></span>

[<span data-ttu-id="8d000-135">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8d000-135">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="8d000-136">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8d000-136">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

