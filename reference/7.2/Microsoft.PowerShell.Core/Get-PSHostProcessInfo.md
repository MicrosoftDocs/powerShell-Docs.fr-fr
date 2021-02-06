---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 6528d25ea706ac63927ef3d23cf661489caae8aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598159"
---
# <span data-ttu-id="a3655-102">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="a3655-102">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="a3655-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a3655-103">SYNOPSIS</span></span>
<span data-ttu-id="a3655-104">Obtient des informations sur le traitement de l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3655-104">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="a3655-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a3655-105">SYNTAX</span></span>

### <span data-ttu-id="a3655-106">ProcessNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a3655-106">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="a3655-107">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="a3655-107">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="a3655-108">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="a3655-108">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="a3655-109">Description</span><span class="sxs-lookup"><span data-stu-id="a3655-109">DESCRIPTION</span></span>

<span data-ttu-id="a3655-110">L' `Get-PSHostProcessInfo` applet de commande obtient des informations sur les processus hôtes PowerShell en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a3655-110">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="a3655-111">À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="a3655-111">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="a3655-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a3655-112">EXAMPLES</span></span>

### <span data-ttu-id="a3655-113">1 : obtenir la liste des hôtes PowerShell en cours d’exécution sur le système</span><span class="sxs-lookup"><span data-stu-id="a3655-113">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### <span data-ttu-id="a3655-114">2 : obtenir les informations de l’hôte PowerShell pour un nom de processus spécifique</span><span class="sxs-lookup"><span data-stu-id="a3655-114">2: Get PowerShell host information for a specific process name</span></span>

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## <span data-ttu-id="a3655-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3655-115">PARAMETERS</span></span>

### <span data-ttu-id="a3655-116">-Id</span><span class="sxs-lookup"><span data-stu-id="a3655-116">-Id</span></span>

<span data-ttu-id="a3655-117">Spécifie un processus par l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="a3655-117">Specifies a process by the process ID.</span></span> <span data-ttu-id="a3655-118">Pour obtenir un ID de processus, exécutez l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="a3655-118">To get a process ID, run the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="a3655-119">-Name</span><span class="sxs-lookup"><span data-stu-id="a3655-119">-Name</span></span>

<span data-ttu-id="a3655-120">Spécifie un processus par le nom du processus.</span><span class="sxs-lookup"><span data-stu-id="a3655-120">Specifies a process by the process name.</span></span> <span data-ttu-id="a3655-121">Pour obtenir un nom de processus, exécutez l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="a3655-121">To get a process name, run the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="a3655-122">-Processus</span><span class="sxs-lookup"><span data-stu-id="a3655-122">-Process</span></span>

<span data-ttu-id="a3655-123">Spécifie un processus par l’objet processus.</span><span class="sxs-lookup"><span data-stu-id="a3655-123">Specifies a process by the process object.</span></span> <span data-ttu-id="a3655-124">La façon la plus simple d’utiliser ce paramètre consiste à enregistrer les résultats d’une `Get-Process` commande qui retourne le processus que vous souhaitez entrer dans une variable, puis à spécifier la variable comme valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3655-124">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

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

### <span data-ttu-id="a3655-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3655-125">CommonParameters</span></span>

<span data-ttu-id="a3655-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3655-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3655-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a3655-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3655-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a3655-128">INPUTS</span></span>

### <span data-ttu-id="a3655-129">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="a3655-129">System.Diagnostics.Process</span></span>

<span data-ttu-id="a3655-130">Vous pouvez diriger un objet **processus** de `Get-Process` vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3655-130">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="a3655-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a3655-131">OUTPUTS</span></span>

### <span data-ttu-id="a3655-132">Microsoft. PowerShell. Commands. PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="a3655-132">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="a3655-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a3655-133">NOTES</span></span>

## <span data-ttu-id="a3655-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a3655-134">RELATED LINKS</span></span>

[<span data-ttu-id="a3655-135">Get-Process</span><span class="sxs-lookup"><span data-stu-id="a3655-135">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)

