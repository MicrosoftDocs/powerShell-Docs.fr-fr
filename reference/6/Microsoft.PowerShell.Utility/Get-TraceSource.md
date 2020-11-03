---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: d136dd46eaceb65b5c512e3ff5c98e13d685d45e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204605"
---
# <span data-ttu-id="8add4-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="8add4-103">Get-TraceSource</span></span>

## <span data-ttu-id="8add4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8add4-104">SYNOPSIS</span></span>
<span data-ttu-id="8add4-105">Obtient les composants PowerShell instrumentés pour le suivi.</span><span class="sxs-lookup"><span data-stu-id="8add4-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="8add4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8add4-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8add4-107">Description</span><span class="sxs-lookup"><span data-stu-id="8add4-107">DESCRIPTION</span></span>

<span data-ttu-id="8add4-108">L’applet de commande **obtenir-TraceSource** obtient les sources de suivi pour les composants PowerShell en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="8add4-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="8add4-109">Vous pouvez utiliser les données pour déterminer les composants PowerShell que vous pouvez tracer.</span><span class="sxs-lookup"><span data-stu-id="8add4-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="8add4-110">Pendant le suivi, le composant génère des messages détaillés sur chaque étape du traitement interne.</span><span class="sxs-lookup"><span data-stu-id="8add4-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="8add4-111">Les développeurs utilisent les données de suivi pour surveiller les flux de données, l'exécution des programmes et les erreurs.</span><span class="sxs-lookup"><span data-stu-id="8add4-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="8add4-112">Les applets de commande de suivi ont été conçues pour les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8add4-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="8add4-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8add4-113">EXAMPLES</span></span>

### <span data-ttu-id="8add4-114">Exemple 1 : récupérer les sources de suivi par nom</span><span class="sxs-lookup"><span data-stu-id="8add4-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="8add4-115">Cette commande obtient toutes les sources de suivi dont le nom inclut le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="8add4-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="8add4-116">Exemple 2 : récupération de toutes les sources de suivi</span><span class="sxs-lookup"><span data-stu-id="8add4-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="8add4-117">Cette commande obtient tous les composants PowerShell qui peuvent être suivis.</span><span class="sxs-lookup"><span data-stu-id="8add4-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="8add4-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8add4-118">PARAMETERS</span></span>

### <span data-ttu-id="8add4-119">-Name</span><span class="sxs-lookup"><span data-stu-id="8add4-119">-Name</span></span>

<span data-ttu-id="8add4-120">Spécifie les sources de suivi à récupérer.</span><span class="sxs-lookup"><span data-stu-id="8add4-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="8add4-121">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8add4-121">Wildcards are permitted.</span></span>
<span data-ttu-id="8add4-122">Le *nom du paramètre est facultatif* .</span><span class="sxs-lookup"><span data-stu-id="8add4-122">The parameter name *Name* is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8add4-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8add4-123">CommonParameters</span></span>

<span data-ttu-id="8add4-124">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8add4-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8add4-125">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8add4-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8add4-126">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8add4-126">INPUTS</span></span>

### <span data-ttu-id="8add4-127">System.String</span><span class="sxs-lookup"><span data-stu-id="8add4-127">System.String</span></span>

<span data-ttu-id="8add4-128">Vous pouvez diriger une chaîne qui contient le nom d’une source de suivi vers **obtenir-TraceSource** .</span><span class="sxs-lookup"><span data-stu-id="8add4-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource** .</span></span>

## <span data-ttu-id="8add4-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8add4-129">OUTPUTS</span></span>

### <span data-ttu-id="8add4-130">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="8add4-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="8add4-131">La méthode **obten-TraceSource retourne des** objets qui représentent les sources de suivi.</span><span class="sxs-lookup"><span data-stu-id="8add4-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="8add4-132">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8add4-132">NOTES</span></span>

## <span data-ttu-id="8add4-133">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8add4-133">RELATED LINKS</span></span>

[<span data-ttu-id="8add4-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="8add4-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="8add4-135">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="8add4-135">Trace-Command</span></span>](Trace-Command.md)
