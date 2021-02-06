---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: c196d00359c9b20b5dc1fefc0ab2b94655703f6f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599166"
---
# <span data-ttu-id="14b98-102">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="14b98-102">Get-TraceSource</span></span>

## <span data-ttu-id="14b98-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="14b98-103">SYNOPSIS</span></span>
<span data-ttu-id="14b98-104">Obtient les composants PowerShell instrumentés pour le suivi.</span><span class="sxs-lookup"><span data-stu-id="14b98-104">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="14b98-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="14b98-105">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="14b98-106">Description</span><span class="sxs-lookup"><span data-stu-id="14b98-106">DESCRIPTION</span></span>

<span data-ttu-id="14b98-107">L’applet de commande **obtenir-TraceSource** obtient les sources de suivi pour les composants PowerShell en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="14b98-107">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="14b98-108">Vous pouvez utiliser les données pour déterminer les composants PowerShell que vous pouvez tracer.</span><span class="sxs-lookup"><span data-stu-id="14b98-108">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="14b98-109">Pendant le suivi, le composant génère des messages détaillés sur chaque étape du traitement interne.</span><span class="sxs-lookup"><span data-stu-id="14b98-109">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="14b98-110">Les développeurs utilisent les données de suivi pour surveiller les flux de données, l'exécution des programmes et les erreurs.</span><span class="sxs-lookup"><span data-stu-id="14b98-110">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="14b98-111">Les applets de commande de suivi ont été conçues pour les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="14b98-111">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="14b98-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="14b98-112">EXAMPLES</span></span>

### <span data-ttu-id="14b98-113">Exemple 1 : récupérer les sources de suivi par nom</span><span class="sxs-lookup"><span data-stu-id="14b98-113">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="14b98-114">Cette commande obtient toutes les sources de suivi dont le nom inclut le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="14b98-114">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="14b98-115">Exemple 2 : récupération de toutes les sources de suivi</span><span class="sxs-lookup"><span data-stu-id="14b98-115">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="14b98-116">Cette commande obtient tous les composants PowerShell qui peuvent être suivis.</span><span class="sxs-lookup"><span data-stu-id="14b98-116">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="14b98-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="14b98-117">PARAMETERS</span></span>

### <span data-ttu-id="14b98-118">-Name</span><span class="sxs-lookup"><span data-stu-id="14b98-118">-Name</span></span>

<span data-ttu-id="14b98-119">Spécifie les sources de suivi à récupérer.</span><span class="sxs-lookup"><span data-stu-id="14b98-119">Specifies the trace sources to get.</span></span>
<span data-ttu-id="14b98-120">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="14b98-120">Wildcards are permitted.</span></span>
<span data-ttu-id="14b98-121">Le *nom du paramètre est facultatif* .</span><span class="sxs-lookup"><span data-stu-id="14b98-121">The parameter name *Name* is optional.</span></span>

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

### <span data-ttu-id="14b98-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14b98-122">CommonParameters</span></span>

<span data-ttu-id="14b98-123">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14b98-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14b98-124">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14b98-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14b98-125">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="14b98-125">INPUTS</span></span>

### <span data-ttu-id="14b98-126">System.String</span><span class="sxs-lookup"><span data-stu-id="14b98-126">System.String</span></span>

<span data-ttu-id="14b98-127">Vous pouvez diriger une chaîne qui contient le nom d’une source de suivi vers **obtenir-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="14b98-127">You can pipe a string that contains the name of a trace source to **Get-TraceSource**.</span></span>

## <span data-ttu-id="14b98-128">SORTIES</span><span class="sxs-lookup"><span data-stu-id="14b98-128">OUTPUTS</span></span>

### <span data-ttu-id="14b98-129">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="14b98-129">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="14b98-130">La méthode **obten-TraceSource retourne des** objets qui représentent les sources de suivi.</span><span class="sxs-lookup"><span data-stu-id="14b98-130">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="14b98-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="14b98-131">NOTES</span></span>

## <span data-ttu-id="14b98-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="14b98-132">RELATED LINKS</span></span>

[<span data-ttu-id="14b98-133">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="14b98-133">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="14b98-134">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="14b98-134">Trace-Command</span></span>](Trace-Command.md)

