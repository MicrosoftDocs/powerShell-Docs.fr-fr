---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203490"
---
# <span data-ttu-id="3d6e1-103">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-103">Show-EventLog</span></span>

## <span data-ttu-id="3d6e1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3d6e1-104">SYNOPSIS</span></span>
<span data-ttu-id="3d6e1-105">Affiche les journaux des événements de l'ordinateur local ou d'un ordinateur distant dans l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-105">Displays the event logs of the local or a remote computer in Event Viewer.</span></span>

## <span data-ttu-id="3d6e1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d6e1-106">SYNTAX</span></span>

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="3d6e1-107">Description</span><span class="sxs-lookup"><span data-stu-id="3d6e1-107">DESCRIPTION</span></span>
<span data-ttu-id="3d6e1-108">L’applet de commande **Show-EventLog** ouvre observateur d’événements sur l’ordinateur local et s’affiche dans tous les journaux des événements classiques sur l’ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-108">The **Show-EventLog** cmdlet opens Event Viewer on the local computer and displays in it all of the classic event logs on the local computer or a remote computer.</span></span>

<span data-ttu-id="3d6e1-109">Pour ouvrir observateur d’événements sur Windows Vista et les versions ultérieures du système d’exploitation Windows, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-109">To open Event Viewer on Windows Vista and later versions of the Windows operating system, the current user must be a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="3d6e1-110">Les applets de commande qui contiennent le nom **EventLog** (les applets de commande **EventLog** ) fonctionnent uniquement sur les journaux des événements classiques.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="3d6e1-111">Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures du système d’exploitation Windows, utilisez l’applet de commande Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="3d6e1-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3d6e1-112">EXAMPLES</span></span>

### <span data-ttu-id="3d6e1-113">Exemple 1 : afficher les journaux des événements de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="3d6e1-113">Example 1: Display event logs for the local computer</span></span>

```
PS C:\> Show-EventLog
```

<span data-ttu-id="3d6e1-114">Cette commande ouvre l'observateur d'événements et y affiche les journaux des événements classiques sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-114">This command opens Event Viewer and displays in it the classic event logs on the local computer.</span></span>

### <span data-ttu-id="3d6e1-115">Exemple 2 : afficher les journaux des événements pour un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="3d6e1-115">Example 2: Display event logs for a remote computer</span></span>

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

<span data-ttu-id="3d6e1-116">Cette commande ouvre l'observateur d'événements et y affiche les journaux des événements classiques sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-116">This command opens Event Viewer and displays in it the classic event logs on the Server01 computer.</span></span>

## <span data-ttu-id="3d6e1-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d6e1-117">PARAMETERS</span></span>

### <span data-ttu-id="3d6e1-118">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3d6e1-118">-ComputerName</span></span>
<span data-ttu-id="3d6e1-119">Spécifie un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-119">Specifies a remote computer.</span></span>
<span data-ttu-id="3d6e1-120">**Show-EventLog** affiche les journaux des événements de l’ordinateur spécifié dans observateur d’événements sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-120">**Show-EventLog** displays the event logs from the specified computer in Event Viewer on the local computer.</span></span>
<span data-ttu-id="3d6e1-121">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-121">The default is the local computer.</span></span>

<span data-ttu-id="3d6e1-122">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="3d6e1-123">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-123">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="3d6e1-124">Vous pouvez utiliser le paramètre *ComputerName* même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-124">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d6e1-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d6e1-125">CommonParameters</span></span>
<span data-ttu-id="3d6e1-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d6e1-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3d6e1-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d6e1-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3d6e1-128">INPUTS</span></span>

### <span data-ttu-id="3d6e1-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="3d6e1-129">None</span></span>
<span data-ttu-id="3d6e1-130">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3d6e1-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3d6e1-131">OUTPUTS</span></span>

### <span data-ttu-id="3d6e1-132">Aucun</span><span class="sxs-lookup"><span data-stu-id="3d6e1-132">None</span></span>
<span data-ttu-id="3d6e1-133">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-133">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3d6e1-134">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3d6e1-134">NOTES</span></span>

* <span data-ttu-id="3d6e1-135">L'invite de commandes de Windows PowerShell retourne des éléments dès que l'observateur d'événements s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-135">The Windows PowerShell command prompt returns as soon as Event Viewer opens.</span></span> <span data-ttu-id="3d6e1-136">Vous pouvez travailler dans la session active lorsque l'observateur d'événements est ouvert.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-136">You can work in the current session while Event Viewer is open.</span></span>

  <span data-ttu-id="3d6e1-137">Comme cette applet de commande requiert une interface utilisateur, elle ne fonctionne pas sur les installations minimales de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="3d6e1-137">Because this cmdlet requires a user interface, it does not work on Server Core installations of Windows Server.</span></span>

*

## <span data-ttu-id="3d6e1-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3d6e1-138">RELATED LINKS</span></span>

[<span data-ttu-id="3d6e1-139">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-139">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="3d6e1-140">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-140">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="3d6e1-141">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-141">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="3d6e1-142">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-142">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="3d6e1-143">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-143">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="3d6e1-144">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d6e1-144">Write-EventLog</span></span>](Write-EventLog.md)
