---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204034"
---
# <span data-ttu-id="75c0a-103">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="75c0a-103">Disable-ComputerRestore</span></span>

## <span data-ttu-id="75c0a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="75c0a-104">SYNOPSIS</span></span>
<span data-ttu-id="75c0a-105">Désactive la fonctionnalité Restauration du système sur le lecteur du système de fichiers spécifié.</span><span class="sxs-lookup"><span data-stu-id="75c0a-105">Disables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="75c0a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75c0a-106">SYNTAX</span></span>

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="75c0a-107">Description</span><span class="sxs-lookup"><span data-stu-id="75c0a-107">DESCRIPTION</span></span>
<span data-ttu-id="75c0a-108">L’applet de commande **Disable-ComputerRestore** désactive la fonctionnalité Restauration du système sur un ou plusieurs lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="75c0a-108">The **Disable-ComputerRestore** cmdlet turns off the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="75c0a-109">Le lecteur spécifié n’est par conséquent pas concerné en cas de tentative de restauration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75c0a-109">As a result, attempts to restore the computer do not affect the specified drive.</span></span>

<span data-ttu-id="75c0a-110">Pour désactiver la fonctionnalité Restauration du système sur un lecteur, celle-ci doit d’abord être désactivée sur le lecteur système.</span><span class="sxs-lookup"><span data-stu-id="75c0a-110">To disable System Restore on any drive, it must be disabled on the system drive, either first or concurrently.</span></span>

<span data-ttu-id="75c0a-111">Pour réactiver la fonctionnalité Restauration du système, utilisez l’applet de commande Enable-ComputerRestore.</span><span class="sxs-lookup"><span data-stu-id="75c0a-111">To re-enable System Restore, use the Enable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="75c0a-112">Pour rechercher l’état de la fonctionnalité Restauration du système pour chaque lecteur, utilisez Rstrui.exe.</span><span class="sxs-lookup"><span data-stu-id="75c0a-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="75c0a-113">Les points de restauration système et les applets de commande ComputerRestore ne sont pris en charge que sur les systèmes d’exploitation clients, tels que Windows 7, Windows Vista et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="75c0a-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="75c0a-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="75c0a-114">EXAMPLES</span></span>

### <span data-ttu-id="75c0a-115">Exemple 1 : désactiver la restauration du système sur le lecteur spécifié</span><span class="sxs-lookup"><span data-stu-id="75c0a-115">Example 1: Disable System Restore on the specified drive</span></span>

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="75c0a-116">Cette commande désactive la fonctionnalité Restauration du système sur le lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="75c0a-116">This command disables System Restore on the C: drive.</span></span>

### <span data-ttu-id="75c0a-117">Exemple 2 : désactiver la restauration du système sur plusieurs lecteurs</span><span class="sxs-lookup"><span data-stu-id="75c0a-117">Example 2: Disable System Restore on multiple drives</span></span>

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

<span data-ttu-id="75c0a-118">Cette commande désactive la fonctionnalité Restauration du système sur les lecteurs C: et D:.</span><span class="sxs-lookup"><span data-stu-id="75c0a-118">This command disables System Restore on the C: and D: drives.</span></span>
<span data-ttu-id="75c0a-119">La commande utilise le paramètre *Drive* , mais omet le nom du paramètre Drive.</span><span class="sxs-lookup"><span data-stu-id="75c0a-119">The command uses the *Drive* parameter, but it omits the Drive parameter name.</span></span>

## <span data-ttu-id="75c0a-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75c0a-120">PARAMETERS</span></span>

### <span data-ttu-id="75c0a-121">-Lecteur</span><span class="sxs-lookup"><span data-stu-id="75c0a-121">-Drive</span></span>
<span data-ttu-id="75c0a-122">Spécifie les lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="75c0a-122">Specifies the file system drives.</span></span>
<span data-ttu-id="75c0a-123">Entrez une ou plusieurs lettres de lecteur du système de fichiers, chacune suivie d’un signe deux-points et d’une barre oblique inverse, entre guillemets, par exemple C:\ ou D:\.</span><span class="sxs-lookup"><span data-stu-id="75c0a-123">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="75c0a-124">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="75c0a-124">This parameter is required.</span></span>

<span data-ttu-id="75c0a-125">Vous ne pouvez pas utiliser cette applet de commande pour désactiver la fonctionnalité Restauration du système sur un lecteur réseau distant, même si ce lecteur est mappé à l’ordinateur local. Vous ne pouvez pas non plus désactiver la fonctionnalité Restauration du système sur les lecteurs qui ne sont pas concernés par la fonctionnalité Restauration du système (lecteurs externes, par exemple).</span><span class="sxs-lookup"><span data-stu-id="75c0a-125">You cannot use this cmdlet to disable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot disable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="75c0a-126">Pour désactiver la fonctionnalité Restauration du système sur un lecteur, celle-ci doit d’abord être désactivée sur le lecteur système.</span><span class="sxs-lookup"><span data-stu-id="75c0a-126">To disable System Restore on any drive, System Restore must be disabled on the system drive, either before or concurrently.</span></span>

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

### <span data-ttu-id="75c0a-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="75c0a-127">-Confirm</span></span>
<span data-ttu-id="75c0a-128">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75c0a-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="75c0a-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="75c0a-129">-WhatIf</span></span>
<span data-ttu-id="75c0a-130">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75c0a-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="75c0a-131">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="75c0a-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="75c0a-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75c0a-132">CommonParameters</span></span>
<span data-ttu-id="75c0a-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75c0a-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75c0a-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="75c0a-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75c0a-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="75c0a-135">INPUTS</span></span>

### <span data-ttu-id="75c0a-136">Aucun</span><span class="sxs-lookup"><span data-stu-id="75c0a-136">None</span></span>
<span data-ttu-id="75c0a-137">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75c0a-137">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="75c0a-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="75c0a-138">OUTPUTS</span></span>

### <span data-ttu-id="75c0a-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="75c0a-139">None</span></span>
<span data-ttu-id="75c0a-140">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="75c0a-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="75c0a-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="75c0a-141">NOTES</span></span>

* <span data-ttu-id="75c0a-142">Pour exécuter cette applet de commande sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="75c0a-142">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="75c0a-143">Pour rechercher les lecteurs de système de fichiers éligibles à la restauration du système, dans le panneau de configuration système, consultez l’onglet protection du système. Pour ouvrir cet onglet dans Windows PowerShell, tapez `SystemPropertiesProtection` .</span><span class="sxs-lookup"><span data-stu-id="75c0a-143">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="75c0a-144">Cette applet Windows Management Instrumentation de commande utilise la classe **SystemRestore** (WMI).</span><span class="sxs-lookup"><span data-stu-id="75c0a-144">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="75c0a-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="75c0a-145">RELATED LINKS</span></span>

[<span data-ttu-id="75c0a-146">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="75c0a-146">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="75c0a-147">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="75c0a-147">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="75c0a-148">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="75c0a-148">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="75c0a-149">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="75c0a-149">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="75c0a-150">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="75c0a-150">Restore-Computer</span></span>](Restore-Computer.md)
