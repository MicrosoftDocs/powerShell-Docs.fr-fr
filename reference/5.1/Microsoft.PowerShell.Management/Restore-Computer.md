---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203525"
---
# <span data-ttu-id="11d4e-103">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="11d4e-103">Restore-Computer</span></span>

## <span data-ttu-id="11d4e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="11d4e-104">SYNOPSIS</span></span>
<span data-ttu-id="11d4e-105">Démarre une restauration système sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="11d4e-105">Starts a system restore on the local computer.</span></span>

## <span data-ttu-id="11d4e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="11d4e-106">SYNTAX</span></span>

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="11d4e-107">Description</span><span class="sxs-lookup"><span data-stu-id="11d4e-107">DESCRIPTION</span></span>
<span data-ttu-id="11d4e-108">L’applet de commande **Restore-Computer** restaure l’ordinateur local à partir du point de restauration système spécifié.</span><span class="sxs-lookup"><span data-stu-id="11d4e-108">The **Restore-Computer** cmdlet restores the local computer to the specified system restore point.</span></span>

<span data-ttu-id="11d4e-109">**Restore-Computer** redémarre l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="11d4e-109">**Restore-Computer** restarts the computer.</span></span>
<span data-ttu-id="11d4e-110">La restauration s'effectue pendant l'opération de redémarrage.</span><span class="sxs-lookup"><span data-stu-id="11d4e-110">The restore is completed during the restart operation.</span></span>

<span data-ttu-id="11d4e-111">Les points de restauration système et **Restore-Computer** sont pris en charge uniquement sur les systèmes d’exploitation clients, tels que Windows 7, Windows Vista et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="11d4e-111">System restore points and **Restore-Computer** are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="11d4e-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="11d4e-112">EXAMPLES</span></span>

### <span data-ttu-id="11d4e-113">Exemple 1 : restaurer l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="11d4e-113">Example 1: Restore the local computer</span></span>

```
PS C:\> Restore-Computer -RestorePoint 253
```

<span data-ttu-id="11d4e-114">Cette commande restaure l’ordinateur local au point de restauration qui a le numéro de séquence 253.</span><span class="sxs-lookup"><span data-stu-id="11d4e-114">This command restores the local computer to the restore point that has sequence number 253.</span></span>

### <span data-ttu-id="11d4e-115">Exemple 2 : restaurer l’ordinateur local à l’aide de la confirmation</span><span class="sxs-lookup"><span data-stu-id="11d4e-115">Example 2: Restore the local computer with confirmation</span></span>

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="11d4e-116">Cette commande restaure l’ordinateur local au point de restauration qui a le numéro de séquence 255.</span><span class="sxs-lookup"><span data-stu-id="11d4e-116">This command restores the local computer to the restore point that has sequence number 255.</span></span>
<span data-ttu-id="11d4e-117">Elle utilise le paramètre *Confirm* pour demander à l’utilisateur avant d’effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="11d4e-117">It uses the *Confirm* parameter to prompt the user before actually performing the operation.</span></span>

### <span data-ttu-id="11d4e-118">Exemple 3 : restaurer un ordinateur et vérifier l’État</span><span class="sxs-lookup"><span data-stu-id="11d4e-118">Example 3: Restore a computer and check the status</span></span>

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

<span data-ttu-id="11d4e-119">Ces commandes exécutent une restauration système, puis vérifient son état.</span><span class="sxs-lookup"><span data-stu-id="11d4e-119">These commands run a system restore and then check its status.</span></span>

<span data-ttu-id="11d4e-120">La première commande utilise la commande **ComputerRestorePoint** pour récupérer les points de restauration sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="11d4e-120">The first command uses **Get-ComputerRestorePoint** to get the restore points on the local computer.</span></span>

<span data-ttu-id="11d4e-121">La deuxième commande restaure l’ordinateur sur le point de restauration avec le numéro de séquence 255.</span><span class="sxs-lookup"><span data-stu-id="11d4e-121">The second command restores the computer to the restore point with sequence number 255.</span></span>

<span data-ttu-id="11d4e-122">La troisième commande utilise le paramètre *LastStatus* de l’applet de commande *ComputerRestorePoint* pour vérifier l’état de l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="11d4e-122">The third command uses the *LastStatus* parameter of *Get-ComputerRestorePoint* cmdlet to check the status of the restore operation.</span></span>
<span data-ttu-id="11d4e-123">Étant donné que **Restore-Computer** force un redémarrage, cette commande est entrée après le redémarrage de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="11d4e-123">Because **Restore-Computer** forces a restart, this command would be entered after the computer restarts.</span></span>

## <span data-ttu-id="11d4e-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="11d4e-124">PARAMETERS</span></span>

### <span data-ttu-id="11d4e-125">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="11d4e-125">-RestorePoint</span></span>
<span data-ttu-id="11d4e-126">Spécifie le numéro de séquence du point de restauration.</span><span class="sxs-lookup"><span data-stu-id="11d4e-126">Specifies the sequence number of the restore point.</span></span>
<span data-ttu-id="11d4e-127">Pour rechercher le numéro de séquence, utilisez l’applet de commande Get-ComputerRestorePoint.</span><span class="sxs-lookup"><span data-stu-id="11d4e-127">To find the sequence number, use the Get-ComputerRestorePoint cmdlet.</span></span>
<span data-ttu-id="11d4e-128">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="11d4e-128">This parameter is required.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11d4e-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="11d4e-129">-Confirm</span></span>
<span data-ttu-id="11d4e-130">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="11d4e-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="11d4e-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="11d4e-131">-WhatIf</span></span>
<span data-ttu-id="11d4e-132">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="11d4e-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="11d4e-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="11d4e-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="11d4e-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="11d4e-134">CommonParameters</span></span>
<span data-ttu-id="11d4e-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="11d4e-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="11d4e-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="11d4e-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="11d4e-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="11d4e-137">INPUTS</span></span>

### <span data-ttu-id="11d4e-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="11d4e-138">None</span></span>
<span data-ttu-id="11d4e-139">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="11d4e-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="11d4e-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="11d4e-140">OUTPUTS</span></span>

### <span data-ttu-id="11d4e-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="11d4e-141">None</span></span>
<span data-ttu-id="11d4e-142">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="11d4e-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="11d4e-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="11d4e-143">NOTES</span></span>

* <span data-ttu-id="11d4e-144">Pour exécuter une commande Restore-Computer sur Windows Vista et les versions ultérieures du système d’exploitation Windows, ouvrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="11d4e-144">To run a Restore-Computer command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="11d4e-145">Cette applet Windows Management Instrumentation de commande utilise la classe **SystemRestore** (WMI).</span><span class="sxs-lookup"><span data-stu-id="11d4e-145">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

## <span data-ttu-id="11d4e-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="11d4e-146">RELATED LINKS</span></span>

[<span data-ttu-id="11d4e-147">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="11d4e-147">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="11d4e-148">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="11d4e-148">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="11d4e-149">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="11d4e-149">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="11d4e-150">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="11d4e-150">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="11d4e-151">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="11d4e-151">Restart-Computer</span></span>](Restart-Computer.md)
