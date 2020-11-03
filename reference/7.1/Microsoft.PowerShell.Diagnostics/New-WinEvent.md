---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 8605782176a96fa1901af352ceda8b453d2f1af8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204925"
---
# <span data-ttu-id="107d4-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="107d4-103">New-WinEvent</span></span>

## <span data-ttu-id="107d4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="107d4-104">SYNOPSIS</span></span>
<span data-ttu-id="107d4-105">Crée un événement Windows pour le fournisseur d'événements spécifié.</span><span class="sxs-lookup"><span data-stu-id="107d4-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="107d4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="107d4-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="107d4-107">Description</span><span class="sxs-lookup"><span data-stu-id="107d4-107">DESCRIPTION</span></span>

<span data-ttu-id="107d4-108">L'applet de commande **New-WinEvent** crée un événement du Suivi des événements pour Windows (ETW) pour un fournisseur d'événements.</span><span class="sxs-lookup"><span data-stu-id="107d4-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="107d4-109">Vous pouvez utiliser cette applet de commande pour ajouter des événements aux canaux ETW à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="107d4-109">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="107d4-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="107d4-110">EXAMPLES</span></span>

### <span data-ttu-id="107d4-111">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="107d4-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="107d4-112">Cette commande utilise l'applet de commande **New-WinEvent** pour créer un événement 45090 pour le fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="107d4-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="107d4-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="107d4-113">PARAMETERS</span></span>

### <span data-ttu-id="107d4-114">-Id</span><span class="sxs-lookup"><span data-stu-id="107d4-114">-Id</span></span>

<span data-ttu-id="107d4-115">Spécifie un ID d'événement enregistré via un manifeste d'instrumentation.</span><span class="sxs-lookup"><span data-stu-id="107d4-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="107d4-116">-Charge utile</span><span class="sxs-lookup"><span data-stu-id="107d4-116">-Payload</span></span>

<span data-ttu-id="107d4-117">Spécifie le message de l'événement.</span><span class="sxs-lookup"><span data-stu-id="107d4-117">Specifies the message for the event.</span></span> <span data-ttu-id="107d4-118">Quand l'événement est écrit dans un journal d'événements, la charge utile est stockée dans la propriété **Message** de l'objet d'événement.</span><span class="sxs-lookup"><span data-stu-id="107d4-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="107d4-119">Quand la charge utile spécifiée ne correspond pas à la charge utile dans la définition d’événement, PowerShell génère un avertissement, mais la commande est toujours réussie.</span><span class="sxs-lookup"><span data-stu-id="107d4-119">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="107d4-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="107d4-120">-ProviderName</span></span>

<span data-ttu-id="107d4-121">Spécifie le fournisseur d'événements qui écrit l'événement dans un journal d'événements, comme « Microsoft Windows PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="107d4-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="107d4-122">Un fournisseur d'événements ETW est une entité logique qui écrit des événements dans des sessions ETW.</span><span class="sxs-lookup"><span data-stu-id="107d4-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="107d4-123">-Version</span><span class="sxs-lookup"><span data-stu-id="107d4-123">-Version</span></span>

<span data-ttu-id="107d4-124">Spécifie le numéro de version de l'événement.</span><span class="sxs-lookup"><span data-stu-id="107d4-124">Specifies the version number of the event.</span></span> <span data-ttu-id="107d4-125">Tapez le numéro d'événement.</span><span class="sxs-lookup"><span data-stu-id="107d4-125">Type the event number.</span></span> <span data-ttu-id="107d4-126">PowerShell convertit le nombre en type d’octet requis.</span><span class="sxs-lookup"><span data-stu-id="107d4-126">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="107d4-127">Ce paramètre vous permet de spécifier un événement quand des versions différentes du même événement sont définies.</span><span class="sxs-lookup"><span data-stu-id="107d4-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="107d4-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="107d4-128">CommonParameters</span></span>

<span data-ttu-id="107d4-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="107d4-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="107d4-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="107d4-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="107d4-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="107d4-131">INPUTS</span></span>

### <span data-ttu-id="107d4-132">Aucun</span><span class="sxs-lookup"><span data-stu-id="107d4-132">None</span></span>

<span data-ttu-id="107d4-133">Cette applet de commande n'accepte pas d'entrée provenant du pipeline.</span><span class="sxs-lookup"><span data-stu-id="107d4-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="107d4-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="107d4-134">OUTPUTS</span></span>

### <span data-ttu-id="107d4-135">Aucun</span><span class="sxs-lookup"><span data-stu-id="107d4-135">None</span></span>

<span data-ttu-id="107d4-136">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="107d4-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="107d4-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="107d4-137">NOTES</span></span>

* <span data-ttu-id="107d4-138">Une fois que le fournisseur a écrit le même dans un journal des événements, vous pouvez utiliser l’applet de commande Get-WinEvent pour récupérer l’événement à partir du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="107d4-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="107d4-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="107d4-139">RELATED LINKS</span></span>

[<span data-ttu-id="107d4-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="107d4-140">Get-WinEvent</span></span>](Get-WinEvent.md)

