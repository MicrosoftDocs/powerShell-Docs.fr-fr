---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f67b5d9fe8da48cca5fd4ec7d2056a4702d3ff16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203057"
---
# <span data-ttu-id="f0eba-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="f0eba-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="f0eba-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f0eba-104">SYNOPSIS</span></span>
<span data-ttu-id="f0eba-105">Démarrez une session de journalisation avec les fournisseurs WSMan et PowerShell activés.</span><span class="sxs-lookup"><span data-stu-id="f0eba-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="f0eba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0eba-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="f0eba-107">Description</span><span class="sxs-lookup"><span data-stu-id="f0eba-107">DESCRIPTION</span></span>

<span data-ttu-id="f0eba-108">Cette applet de commande démarre une session de journalisation avec les fournisseurs PowerShell suivants activés :</span><span class="sxs-lookup"><span data-stu-id="f0eba-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="f0eba-109">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0eba-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="f0eba-110">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="f0eba-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="f0eba-111">La session est nommée « PSTrace ».</span><span class="sxs-lookup"><span data-stu-id="f0eba-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="f0eba-112">Cette applet de commande utilise l’applet de commande `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="f0eba-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="f0eba-113">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f0eba-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f0eba-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f0eba-114">EXAMPLES</span></span>

### <span data-ttu-id="f0eba-115">Exemple 1 : démarrer une session de journalisation combinée</span><span class="sxs-lookup"><span data-stu-id="f0eba-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="f0eba-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0eba-116">PARAMETERS</span></span>

### <span data-ttu-id="f0eba-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="f0eba-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="f0eba-118">Par défaut, les événements sont écrits dans « $pshome \Traces\PSTrace.etl ».</span><span class="sxs-lookup"><span data-stu-id="f0eba-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="f0eba-119">Lorsque ce paramètre est utilisé, l’applet de commande crée un nom de fichier unique : « $pshome \Traces\ PSTrace_ {GUID}. etl »</span><span class="sxs-lookup"><span data-stu-id="f0eba-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0eba-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0eba-120">CommonParameters</span></span>

<span data-ttu-id="f0eba-121">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0eba-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0eba-122">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0eba-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0eba-123">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f0eba-123">INPUTS</span></span>

### <span data-ttu-id="f0eba-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="f0eba-124">None</span></span>

## <span data-ttu-id="f0eba-125">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f0eba-125">OUTPUTS</span></span>

### <span data-ttu-id="f0eba-126">System.Object</span><span class="sxs-lookup"><span data-stu-id="f0eba-126">System.Object</span></span>

## <span data-ttu-id="f0eba-127">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f0eba-127">NOTES</span></span>

## <span data-ttu-id="f0eba-128">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f0eba-128">RELATED LINKS</span></span>

[<span data-ttu-id="f0eba-129">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="f0eba-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="f0eba-130">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="f0eba-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="f0eba-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="f0eba-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
