---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204033"
---
# <span data-ttu-id="8c955-103">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="8c955-103">Enable-ComputerRestore</span></span>

## <span data-ttu-id="8c955-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8c955-104">SYNOPSIS</span></span>
<span data-ttu-id="8c955-105">Active la fonctionnalité Restauration du système sur le lecteur du système de fichiers spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c955-105">Enables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="8c955-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c955-106">SYNTAX</span></span>

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8c955-107">Description</span><span class="sxs-lookup"><span data-stu-id="8c955-107">DESCRIPTION</span></span>
<span data-ttu-id="8c955-108">L’applet de commande **Enable-ComputerRestore** active la fonctionnalité Restauration du système sur un ou plusieurs lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8c955-108">The **Enable-ComputerRestore** cmdlet turns on the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="8c955-109">Vous pouvez par conséquent utiliser des outils (applet de commande Restore-Computer, par exemple) pour restaurer l’état précédent de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8c955-109">As a result, you can use tools, such as the Restore-Computer cmdlet, to restore the computer to a previous state.</span></span>

<span data-ttu-id="8c955-110">Par défaut, la fonctionnalité Restauration du système est activée sur tous les lecteurs concernés, mais vous pouvez la désactiver (à l’aide de l’applet de commande Disable-ComputerRestore, par exemple).</span><span class="sxs-lookup"><span data-stu-id="8c955-110">By default, System Restore is enabled on all eligible drives, but you can disable it, such as by using the Disable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="8c955-111">Pour activer (ou réactiver) la fonctionnalité Restauration du système sur un lecteur, celle-ci doit d’abord être activée sur le lecteur système.</span><span class="sxs-lookup"><span data-stu-id="8c955-111">To enable (or re-enable) System Restore on any drive, it must be enabled on the system drive, either first or concurrently.</span></span>
<span data-ttu-id="8c955-112">Pour rechercher l’état de la fonctionnalité Restauration du système pour chaque lecteur, utilisez Rstrui.exe.</span><span class="sxs-lookup"><span data-stu-id="8c955-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="8c955-113">Les points de restauration système et les applets de commande ComputerRestore ne sont pris en charge que sur les systèmes d’exploitation clients, tels que Windows 7, Windows Vista et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="8c955-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="8c955-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8c955-114">EXAMPLES</span></span>

### <span data-ttu-id="8c955-115">Exemple 1 : activer la restauration du système sur le lecteur spécifié</span><span class="sxs-lookup"><span data-stu-id="8c955-115">Example 1: Enable System Restore on the specified drive</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="8c955-116">Cette commande active la fonctionnalité Restauration du système sur le lecteur C: de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8c955-116">This command enables System Restore on the C: drive of the local computer.</span></span>

### <span data-ttu-id="8c955-117">Exemple 2 : activer la restauration du système sur plusieurs lecteurs</span><span class="sxs-lookup"><span data-stu-id="8c955-117">Example 2: Enable System Restore on multiple drives</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

<span data-ttu-id="8c955-118">Cette commande active la fonctionnalité Restauration du système sur les lecteurs C: et D: de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8c955-118">This command enables System Restore on the C: and D: drives of the local computer.</span></span>

## <span data-ttu-id="8c955-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c955-119">PARAMETERS</span></span>

### <span data-ttu-id="8c955-120">-Lecteur</span><span class="sxs-lookup"><span data-stu-id="8c955-120">-Drive</span></span>
<span data-ttu-id="8c955-121">Spécifie les lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8c955-121">Specifies the file system drives.</span></span>
<span data-ttu-id="8c955-122">Entrez une ou plusieurs lettres de lecteur du système de fichiers, chacune suivie d’un signe deux-points et d’une barre oblique inverse, entre guillemets, par exemple C:\ ou D:\.</span><span class="sxs-lookup"><span data-stu-id="8c955-122">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="8c955-123">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8c955-123">This parameter is required.</span></span>

<span data-ttu-id="8c955-124">Vous ne pouvez pas utiliser cette applet de commande pour activer la fonctionnalité Restauration du système sur un lecteur réseau distant, même si ce lecteur est mappé à l’ordinateur local. Vous ne pouvez pas non plus activer la fonctionnalité Restauration du système sur les lecteurs qui ne sont pas concernés par la fonctionnalité Restauration du système (lecteurs externes, par exemple).</span><span class="sxs-lookup"><span data-stu-id="8c955-124">You cannot use this cmdlet to enable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot enable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="8c955-125">Pour activer la fonctionnalité Restauration du système sur un lecteur, celle-ci doit d’abord être activée sur le lecteur système.</span><span class="sxs-lookup"><span data-stu-id="8c955-125">To enable System Restore on any drive, System Restore must be enabled on the system drive, either before or concurrently.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c955-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8c955-126">-Confirm</span></span>
<span data-ttu-id="8c955-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8c955-127">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c955-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8c955-128">-WhatIf</span></span>
<span data-ttu-id="8c955-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8c955-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8c955-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8c955-130">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c955-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c955-131">CommonParameters</span></span>
<span data-ttu-id="8c955-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c955-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c955-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c955-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c955-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8c955-134">INPUTS</span></span>

### <span data-ttu-id="8c955-135">Aucun</span><span class="sxs-lookup"><span data-stu-id="8c955-135">None</span></span>
<span data-ttu-id="8c955-136">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8c955-136">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="8c955-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8c955-137">OUTPUTS</span></span>

### <span data-ttu-id="8c955-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="8c955-138">None</span></span>
<span data-ttu-id="8c955-139">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8c955-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8c955-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8c955-140">NOTES</span></span>

* <span data-ttu-id="8c955-141">Pour exécuter cette applet de commande sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="8c955-141">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="8c955-142">Pour rechercher les lecteurs de système de fichiers éligibles à la restauration du système, dans le panneau de configuration système, consultez l’onglet protection du système. Pour ouvrir cet onglet dans Windows PowerShell, tapez `SystemPropertiesProtection` .</span><span class="sxs-lookup"><span data-stu-id="8c955-142">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="8c955-143">Cette applet Windows Management Instrumentation de commande utilise la classe **SystemRestore** (WMI).</span><span class="sxs-lookup"><span data-stu-id="8c955-143">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="8c955-144">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8c955-144">RELATED LINKS</span></span>

[<span data-ttu-id="8c955-145">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="8c955-145">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="8c955-146">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="8c955-146">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="8c955-147">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="8c955-147">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="8c955-148">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="8c955-148">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="8c955-149">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="8c955-149">Restore-Computer</span></span>](Restore-Computer.md)
