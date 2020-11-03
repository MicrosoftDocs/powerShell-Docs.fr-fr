---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 196b9bc1cb1e318e334e4002e83d73a466b6578d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201934"
---
# <span data-ttu-id="7ee99-103">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="7ee99-103">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="7ee99-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7ee99-104">SYNOPSIS</span></span>
<span data-ttu-id="7ee99-105">Obtient des informations sur le traitement de l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ee99-105">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="7ee99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7ee99-106">SYNTAX</span></span>

### <span data-ttu-id="7ee99-107">ProcessNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7ee99-107">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="7ee99-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="7ee99-108">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="7ee99-109">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="7ee99-109">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="7ee99-110">Description</span><span class="sxs-lookup"><span data-stu-id="7ee99-110">DESCRIPTION</span></span>

<span data-ttu-id="7ee99-111">L' `Get-PSHostProcessInfo` applet de commande obtient des informations sur les processus hôtes PowerShell en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7ee99-111">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="7ee99-112">À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="7ee99-112">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="7ee99-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7ee99-113">EXAMPLES</span></span>

### <span data-ttu-id="7ee99-114">1 : obtenir la liste des hôtes PowerShell en cours d’exécution sur le système</span><span class="sxs-lookup"><span data-stu-id="7ee99-114">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### <span data-ttu-id="7ee99-115">2 : obtenir les informations de l’hôte PowerShell pour un nom de processus spécifique</span><span class="sxs-lookup"><span data-stu-id="7ee99-115">2: Get PowerShell host information for a specific process name</span></span>

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## <span data-ttu-id="7ee99-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7ee99-116">PARAMETERS</span></span>

### <span data-ttu-id="7ee99-117">-Id</span><span class="sxs-lookup"><span data-stu-id="7ee99-117">-Id</span></span>

<span data-ttu-id="7ee99-118">Spécifie un processus par l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="7ee99-118">Specifies a process by the process ID.</span></span> <span data-ttu-id="7ee99-119">Pour obtenir un ID de processus, exécutez l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="7ee99-119">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ee99-120">-Name</span><span class="sxs-lookup"><span data-stu-id="7ee99-120">-Name</span></span>

<span data-ttu-id="7ee99-121">Spécifie un processus par le nom du processus.</span><span class="sxs-lookup"><span data-stu-id="7ee99-121">Specifies a process by the process name.</span></span> <span data-ttu-id="7ee99-122">Pour obtenir un nom de processus, exécutez l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="7ee99-122">To get a process name, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ee99-123">-Processus</span><span class="sxs-lookup"><span data-stu-id="7ee99-123">-Process</span></span>

<span data-ttu-id="7ee99-124">Spécifie un processus par l’objet processus.</span><span class="sxs-lookup"><span data-stu-id="7ee99-124">Specifies a process by the process object.</span></span> <span data-ttu-id="7ee99-125">La façon la plus simple d’utiliser ce paramètre consiste à enregistrer les résultats d’une `Get-Process` commande qui retourne le processus que vous souhaitez entrer dans une variable, puis à spécifier la variable comme valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="7ee99-125">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7ee99-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ee99-126">CommonParameters</span></span>

<span data-ttu-id="7ee99-127">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7ee99-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7ee99-128">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7ee99-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7ee99-129">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7ee99-129">INPUTS</span></span>

### <span data-ttu-id="7ee99-130">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="7ee99-130">System.Diagnostics.Process</span></span>

<span data-ttu-id="7ee99-131">Vous pouvez diriger un objet **processus** de `Get-Process` vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7ee99-131">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="7ee99-132">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7ee99-132">OUTPUTS</span></span>

### <span data-ttu-id="7ee99-133">Microsoft. PowerShell. Commands. PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="7ee99-133">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="7ee99-134">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7ee99-134">NOTES</span></span>

## <span data-ttu-id="7ee99-135">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7ee99-135">RELATED LINKS</span></span>

[<span data-ttu-id="7ee99-136">Get-Process</span><span class="sxs-lookup"><span data-stu-id="7ee99-136">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)
