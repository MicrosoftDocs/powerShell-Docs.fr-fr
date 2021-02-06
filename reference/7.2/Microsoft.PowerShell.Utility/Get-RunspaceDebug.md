---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598784"
---
# <span data-ttu-id="72cef-102">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="72cef-102">Get-RunspaceDebug</span></span>

## <span data-ttu-id="72cef-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="72cef-103">SYNOPSIS</span></span>
<span data-ttu-id="72cef-104">Affiche les options de débogage d’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="72cef-104">Shows runspace debugging options.</span></span>

## <span data-ttu-id="72cef-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="72cef-105">SYNTAX</span></span>

### <span data-ttu-id="72cef-106">RunspaceNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="72cef-106">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="72cef-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="72cef-107">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="72cef-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="72cef-108">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="72cef-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="72cef-109">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="72cef-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="72cef-110">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="72cef-111">Description</span><span class="sxs-lookup"><span data-stu-id="72cef-111">DESCRIPTION</span></span>

<span data-ttu-id="72cef-112">L' `Get-RunspaceDebug` applet de commande affiche les options de débogage d’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="72cef-112">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="72cef-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="72cef-113">EXAMPLES</span></span>

### <span data-ttu-id="72cef-114">1 : afficher l’état du débogueur d’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="72cef-114">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="72cef-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72cef-115">PARAMETERS</span></span>

### <span data-ttu-id="72cef-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="72cef-116">-AppDomainName</span></span>

<span data-ttu-id="72cef-117">Nom du domaine d’application qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72cef-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="72cef-118">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="72cef-118">-ProcessName</span></span>

<span data-ttu-id="72cef-119">Nom du processus qui héberge l’instance d’exécution PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72cef-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="72cef-120">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="72cef-120">-Runspace</span></span>

<span data-ttu-id="72cef-121">Un ou plusieurs objets d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="72cef-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="72cef-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="72cef-122">-RunspaceId</span></span>

<span data-ttu-id="72cef-123">Un ou plusieurs numéros d’ID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="72cef-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="72cef-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="72cef-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="72cef-125">Un ou plusieurs GUID d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="72cef-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="72cef-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="72cef-126">-RunspaceName</span></span>

<span data-ttu-id="72cef-127">Un ou plusieurs noms d' **instance d’exécution** à désactiver.</span><span class="sxs-lookup"><span data-stu-id="72cef-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="72cef-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72cef-128">CommonParameters</span></span>

<span data-ttu-id="72cef-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72cef-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72cef-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="72cef-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72cef-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="72cef-131">INPUTS</span></span>

## <span data-ttu-id="72cef-132">SORTIES</span><span class="sxs-lookup"><span data-stu-id="72cef-132">OUTPUTS</span></span>

## <span data-ttu-id="72cef-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="72cef-133">NOTES</span></span>

## <span data-ttu-id="72cef-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="72cef-134">RELATED LINKS</span></span>

[<span data-ttu-id="72cef-135">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="72cef-135">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="72cef-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="72cef-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

