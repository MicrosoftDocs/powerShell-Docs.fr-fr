---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f6b14ea6cda7d83792f7b51b854471a2cb62bfb5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201125"
---
# <span data-ttu-id="18237-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="18237-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="18237-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="18237-104">SYNOPSIS</span></span>
<span data-ttu-id="18237-105">Démarrez une session de journalisation avec les fournisseurs WSMan et PowerShell activés.</span><span class="sxs-lookup"><span data-stu-id="18237-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="18237-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="18237-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="18237-107">Description</span><span class="sxs-lookup"><span data-stu-id="18237-107">DESCRIPTION</span></span>

<span data-ttu-id="18237-108">Cette applet de commande démarre une session de journalisation avec les fournisseurs PowerShell suivants activés :</span><span class="sxs-lookup"><span data-stu-id="18237-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="18237-109">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="18237-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="18237-110">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="18237-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="18237-111">La session est nommée « PSTrace ».</span><span class="sxs-lookup"><span data-stu-id="18237-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="18237-112">Cette applet de commande utilise l’applet de commande `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="18237-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="18237-113">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="18237-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="18237-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="18237-114">EXAMPLES</span></span>

### <span data-ttu-id="18237-115">Exemple 1 : démarrer une session de journalisation combinée</span><span class="sxs-lookup"><span data-stu-id="18237-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="18237-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="18237-116">PARAMETERS</span></span>

### <span data-ttu-id="18237-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="18237-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="18237-118">Par défaut, les événements sont écrits dans « $pshome \Traces\PSTrace.etl ».</span><span class="sxs-lookup"><span data-stu-id="18237-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="18237-119">Lorsque ce paramètre est utilisé, l’applet de commande crée un nom de fichier unique : « $pshome \Traces\ PSTrace_ {GUID}. etl »</span><span class="sxs-lookup"><span data-stu-id="18237-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="18237-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="18237-120">CommonParameters</span></span>

<span data-ttu-id="18237-121">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="18237-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="18237-122">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="18237-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="18237-123">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="18237-123">INPUTS</span></span>

### <span data-ttu-id="18237-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="18237-124">None</span></span>

## <span data-ttu-id="18237-125">SORTIES</span><span class="sxs-lookup"><span data-stu-id="18237-125">OUTPUTS</span></span>

### <span data-ttu-id="18237-126">Aucun</span><span class="sxs-lookup"><span data-stu-id="18237-126">None</span></span>

## <span data-ttu-id="18237-127">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="18237-127">NOTES</span></span>

## <span data-ttu-id="18237-128">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="18237-128">RELATED LINKS</span></span>

[<span data-ttu-id="18237-129">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="18237-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="18237-130">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="18237-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="18237-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="18237-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
