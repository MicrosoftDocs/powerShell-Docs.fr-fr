---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204090"
---
# <span data-ttu-id="7b918-103">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="7b918-103">Checkpoint-Computer</span></span>

## <span data-ttu-id="7b918-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7b918-104">SYNOPSIS</span></span>
<span data-ttu-id="7b918-105">Crée un point de restauration système sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7b918-105">Creates a system restore point on the local computer.</span></span>

## <span data-ttu-id="7b918-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7b918-106">SYNTAX</span></span>

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## <span data-ttu-id="7b918-107">Description</span><span class="sxs-lookup"><span data-stu-id="7b918-107">DESCRIPTION</span></span>

<span data-ttu-id="7b918-108">L' `Checkpoint-Computer` applet de commande crée un point de restauration système sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7b918-108">The `Checkpoint-Computer` cmdlet creates a system restore point on the local computer.</span></span>

<span data-ttu-id="7b918-109">Les points de restauration système et l' `Checkpoint-Computer` applet de commande sont pris en charge uniquement sur les systèmes d’exploitation clients, tels que Windows 8, Windows 7, Windows Vista et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="7b918-109">System restore points and the `Checkpoint-Computer` cmdlet are supported only on client operating systems, such as Windows 8, Windows 7, Windows Vista, and Windows XP.</span></span>

<span data-ttu-id="7b918-110">À compter de Windows 8, `Checkpoint-Computer` ne peut pas créer plus d’un point de contrôle par jour.</span><span class="sxs-lookup"><span data-stu-id="7b918-110">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one checkpoint each day.</span></span>

## <span data-ttu-id="7b918-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7b918-111">EXAMPLES</span></span>

### <span data-ttu-id="7b918-112">Exemple 1 : créer un point de restauration système</span><span class="sxs-lookup"><span data-stu-id="7b918-112">Example 1: Create a system restore point</span></span>

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

<span data-ttu-id="7b918-113">Cette commande crée un point de restauration système appelé install MyApp.</span><span class="sxs-lookup"><span data-stu-id="7b918-113">This command creates a system restore point called Install MyApp.</span></span>
<span data-ttu-id="7b918-114">Elle utilise le type de point de restauration par défaut APPLICATION_INSTALL.</span><span class="sxs-lookup"><span data-stu-id="7b918-114">It uses the default APPLICATION_INSTALL restore point type.</span></span>

### <span data-ttu-id="7b918-115">Exemple 2 : créer un point de restauration système MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="7b918-115">Example 2: Create a system MODIFY_SETTINGS restore point</span></span>

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

<span data-ttu-id="7b918-116">Cette commande crée un point de restauration système MODIFY_SETTINGS appelé « ChangeNetSettings ».</span><span class="sxs-lookup"><span data-stu-id="7b918-116">This command creates a MODIFY_SETTINGS system restore point called "ChangeNetSettings".</span></span>

## <span data-ttu-id="7b918-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b918-117">PARAMETERS</span></span>

### <span data-ttu-id="7b918-118">Description</span><span class="sxs-lookup"><span data-stu-id="7b918-118">-Description</span></span>

<span data-ttu-id="7b918-119">Spécifie un nom descriptif pour le point de restauration.</span><span class="sxs-lookup"><span data-stu-id="7b918-119">Specifies a descriptive name for the restore point.</span></span>
<span data-ttu-id="7b918-120">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7b918-120">This parameter is required.</span></span>

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

### <span data-ttu-id="7b918-121">-RestorePointType</span><span class="sxs-lookup"><span data-stu-id="7b918-121">-RestorePointType</span></span>

<span data-ttu-id="7b918-122">Spécifie le type de point de restauration.</span><span class="sxs-lookup"><span data-stu-id="7b918-122">Specifies the type of restore point.</span></span>
<span data-ttu-id="7b918-123">La valeur par défaut est APPLICATION_INSTALL.</span><span class="sxs-lookup"><span data-stu-id="7b918-123">The default is APPLICATION_INSTALL.</span></span>

<span data-ttu-id="7b918-124">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="7b918-124">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7b918-125">APPLICATION_INSTALL</span><span class="sxs-lookup"><span data-stu-id="7b918-125">APPLICATION_INSTALL</span></span>
- <span data-ttu-id="7b918-126">APPLICATION_UNINSTALL</span><span class="sxs-lookup"><span data-stu-id="7b918-126">APPLICATION_UNINSTALL</span></span>
- <span data-ttu-id="7b918-127">DEVICE_DRIVER_INSTALL</span><span class="sxs-lookup"><span data-stu-id="7b918-127">DEVICE_DRIVER_INSTALL</span></span>
- <span data-ttu-id="7b918-128">MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="7b918-128">MODIFY_SETTINGS</span></span>
- <span data-ttu-id="7b918-129">CANCELLED_OPERATION</span><span class="sxs-lookup"><span data-stu-id="7b918-129">CANCELLED_OPERATION</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b918-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b918-130">CommonParameters</span></span>

<span data-ttu-id="7b918-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b918-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b918-132">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7b918-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7b918-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7b918-133">INPUTS</span></span>

### <span data-ttu-id="7b918-134">Aucun</span><span class="sxs-lookup"><span data-stu-id="7b918-134">None</span></span>

<span data-ttu-id="7b918-135">Vous ne pouvez pas diriger d’objets vers `Checkpoint-Computer` .</span><span class="sxs-lookup"><span data-stu-id="7b918-135">You cannot pipe objects to `Checkpoint-Computer`.</span></span>

## <span data-ttu-id="7b918-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7b918-136">OUTPUTS</span></span>

### <span data-ttu-id="7b918-137">Aucun</span><span class="sxs-lookup"><span data-stu-id="7b918-137">None</span></span>

<span data-ttu-id="7b918-138">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="7b918-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7b918-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7b918-139">NOTES</span></span>

- <span data-ttu-id="7b918-140">Cette applet de commande utilise la méthode **CreateRestorePoint** de la classe **SystemRestore** avec un événement **BEGIN_SYSTEM_CHANGE** .</span><span class="sxs-lookup"><span data-stu-id="7b918-140">This cmdlet uses the **CreateRestorePoint** method of the **SystemRestore** class with a **BEGIN_SYSTEM_CHANGE** event.</span></span>
- <span data-ttu-id="7b918-141">À compter de Windows 8, `Checkpoint-Computer` ne peut pas créer plus d’un point de restauration système par jour.</span><span class="sxs-lookup"><span data-stu-id="7b918-141">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one system restore point each day.</span></span> <span data-ttu-id="7b918-142">Si vous essayez de créer un point de restauration avant l'expiration du délai de 24 heures, Windows PowerShell génère l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="7b918-142">If you try to create a new restore point before the 24-hour period has elapsed, Windows PowerShell generates the following error:</span></span>

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## <span data-ttu-id="7b918-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7b918-143">RELATED LINKS</span></span>

[<span data-ttu-id="7b918-144">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="7b918-144">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="7b918-145">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="7b918-145">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="7b918-146">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="7b918-146">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="7b918-147">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="7b918-147">Restore-Computer</span></span>](Restore-Computer.md)
