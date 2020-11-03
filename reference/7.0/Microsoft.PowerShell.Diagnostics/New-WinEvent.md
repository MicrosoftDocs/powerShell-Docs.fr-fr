---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 8e64c3e3a782fadf1669f1310d1615f3a014ccee
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201289"
---
# <span data-ttu-id="83adb-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="83adb-103">New-WinEvent</span></span>

## <span data-ttu-id="83adb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="83adb-104">SYNOPSIS</span></span>
<span data-ttu-id="83adb-105">Crée un événement Windows pour le fournisseur d'événements spécifié.</span><span class="sxs-lookup"><span data-stu-id="83adb-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="83adb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="83adb-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="83adb-107">Description</span><span class="sxs-lookup"><span data-stu-id="83adb-107">DESCRIPTION</span></span>

<span data-ttu-id="83adb-108">L'applet de commande **New-WinEvent** crée un événement du Suivi des événements pour Windows (ETW) pour un fournisseur d'événements.</span><span class="sxs-lookup"><span data-stu-id="83adb-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="83adb-109">Vous pouvez utiliser cette applet de commande pour ajouter des événements aux canaux ETW à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83adb-109">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="83adb-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="83adb-110">EXAMPLES</span></span>

### <span data-ttu-id="83adb-111">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="83adb-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="83adb-112">Cette commande utilise l'applet de commande **New-WinEvent** pour créer un événement 45090 pour le fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83adb-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="83adb-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="83adb-113">PARAMETERS</span></span>

### <span data-ttu-id="83adb-114">-Id</span><span class="sxs-lookup"><span data-stu-id="83adb-114">-Id</span></span>

<span data-ttu-id="83adb-115">Spécifie un ID d'événement enregistré via un manifeste d'instrumentation.</span><span class="sxs-lookup"><span data-stu-id="83adb-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

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

### <span data-ttu-id="83adb-116">-Charge utile</span><span class="sxs-lookup"><span data-stu-id="83adb-116">-Payload</span></span>

<span data-ttu-id="83adb-117">Spécifie le message de l'événement.</span><span class="sxs-lookup"><span data-stu-id="83adb-117">Specifies the message for the event.</span></span> <span data-ttu-id="83adb-118">Quand l'événement est écrit dans un journal d'événements, la charge utile est stockée dans la propriété **Message** de l'objet d'événement.</span><span class="sxs-lookup"><span data-stu-id="83adb-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="83adb-119">Quand la charge utile spécifiée ne correspond pas à la charge utile dans la définition d’événement, PowerShell génère un avertissement, mais la commande est toujours réussie.</span><span class="sxs-lookup"><span data-stu-id="83adb-119">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

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

### <span data-ttu-id="83adb-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="83adb-120">-ProviderName</span></span>

<span data-ttu-id="83adb-121">Spécifie le fournisseur d'événements qui écrit l'événement dans un journal d'événements, comme « Microsoft Windows PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="83adb-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="83adb-122">Un fournisseur d'événements ETW est une entité logique qui écrit des événements dans des sessions ETW.</span><span class="sxs-lookup"><span data-stu-id="83adb-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

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

### <span data-ttu-id="83adb-123">-Version</span><span class="sxs-lookup"><span data-stu-id="83adb-123">-Version</span></span>

<span data-ttu-id="83adb-124">Spécifie le numéro de version de l'événement.</span><span class="sxs-lookup"><span data-stu-id="83adb-124">Specifies the version number of the event.</span></span> <span data-ttu-id="83adb-125">Tapez le numéro d'événement.</span><span class="sxs-lookup"><span data-stu-id="83adb-125">Type the event number.</span></span> <span data-ttu-id="83adb-126">PowerShell convertit le nombre en type d’octet requis.</span><span class="sxs-lookup"><span data-stu-id="83adb-126">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="83adb-127">Ce paramètre vous permet de spécifier un événement quand des versions différentes du même événement sont définies.</span><span class="sxs-lookup"><span data-stu-id="83adb-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

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

### <span data-ttu-id="83adb-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="83adb-128">CommonParameters</span></span>

<span data-ttu-id="83adb-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="83adb-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="83adb-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="83adb-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="83adb-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="83adb-131">INPUTS</span></span>

### <span data-ttu-id="83adb-132">Aucun</span><span class="sxs-lookup"><span data-stu-id="83adb-132">None</span></span>

<span data-ttu-id="83adb-133">Cette applet de commande n'accepte pas d'entrée provenant du pipeline.</span><span class="sxs-lookup"><span data-stu-id="83adb-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="83adb-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="83adb-134">OUTPUTS</span></span>

### <span data-ttu-id="83adb-135">Aucun</span><span class="sxs-lookup"><span data-stu-id="83adb-135">None</span></span>

<span data-ttu-id="83adb-136">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="83adb-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="83adb-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="83adb-137">NOTES</span></span>

* <span data-ttu-id="83adb-138">Une fois que le fournisseur a écrit le même dans un journal des événements, vous pouvez utiliser l’applet de commande Get-WinEvent pour récupérer l’événement à partir du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="83adb-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="83adb-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="83adb-139">RELATED LINKS</span></span>

[<span data-ttu-id="83adb-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="83adb-140">Get-WinEvent</span></span>](Get-WinEvent.md)
