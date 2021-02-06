---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: ef333edaa091e96df11a8288e9b16f133614c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598778"
---
# <span data-ttu-id="c1d2b-102">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="c1d2b-102">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="c1d2b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c1d2b-103">SYNOPSIS</span></span>
<span data-ttu-id="c1d2b-104">Démarrez une session de journalisation avec les fournisseurs WSMan et PowerShell activés.</span><span class="sxs-lookup"><span data-stu-id="c1d2b-104">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="c1d2b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c1d2b-105">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="c1d2b-106">Description</span><span class="sxs-lookup"><span data-stu-id="c1d2b-106">DESCRIPTION</span></span>

<span data-ttu-id="c1d2b-107">Cette applet de commande démarre une session de journalisation avec les fournisseurs PowerShell suivants activés :</span><span class="sxs-lookup"><span data-stu-id="c1d2b-107">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="c1d2b-108">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1d2b-108">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="c1d2b-109">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="c1d2b-109">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="c1d2b-110">La session est nommée « PSTrace ».</span><span class="sxs-lookup"><span data-stu-id="c1d2b-110">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="c1d2b-111">Cette applet de commande utilise l’applet de commande `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="c1d2b-111">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="c1d2b-112">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="c1d2b-112">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c1d2b-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c1d2b-113">EXAMPLES</span></span>

### <span data-ttu-id="c1d2b-114">Exemple 1 : démarrer une session de journalisation combinée</span><span class="sxs-lookup"><span data-stu-id="c1d2b-114">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="c1d2b-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c1d2b-115">PARAMETERS</span></span>

### <span data-ttu-id="c1d2b-116">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="c1d2b-116">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="c1d2b-117">Par défaut, les événements sont écrits dans « $pshome \Traces\PSTrace.etl ».</span><span class="sxs-lookup"><span data-stu-id="c1d2b-117">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="c1d2b-118">Lorsque ce paramètre est utilisé, l’applet de commande crée un nom de fichier unique : « $pshome \Traces\ PSTrace_ {GUID}. etl »</span><span class="sxs-lookup"><span data-stu-id="c1d2b-118">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1d2b-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1d2b-119">CommonParameters</span></span>

<span data-ttu-id="c1d2b-120">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c1d2b-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c1d2b-121">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c1d2b-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c1d2b-122">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c1d2b-122">INPUTS</span></span>

### <span data-ttu-id="c1d2b-123">None</span><span class="sxs-lookup"><span data-stu-id="c1d2b-123">None</span></span>

## <span data-ttu-id="c1d2b-124">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c1d2b-124">OUTPUTS</span></span>

### <span data-ttu-id="c1d2b-125">None</span><span class="sxs-lookup"><span data-stu-id="c1d2b-125">None</span></span>

## <span data-ttu-id="c1d2b-126">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c1d2b-126">NOTES</span></span>

## <span data-ttu-id="c1d2b-127">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c1d2b-127">RELATED LINKS</span></span>

[<span data-ttu-id="c1d2b-128">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="c1d2b-128">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c1d2b-129">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="c1d2b-129">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="c1d2b-130">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="c1d2b-130">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

