---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204026"
---
# <span data-ttu-id="75b87-103">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="75b87-103">Get-ComputerRestorePoint</span></span>

## <span data-ttu-id="75b87-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="75b87-104">SYNOPSIS</span></span>
<span data-ttu-id="75b87-105">Obtient les points de restauration présents sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="75b87-105">Gets the restore points on the local computer.</span></span>

## <span data-ttu-id="75b87-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75b87-106">SYNTAX</span></span>

### <span data-ttu-id="75b87-107">ID (par défaut)</span><span class="sxs-lookup"><span data-stu-id="75b87-107">ID (Default)</span></span>

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="75b87-108">LastStatus</span><span class="sxs-lookup"><span data-stu-id="75b87-108">LastStatus</span></span>

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## <span data-ttu-id="75b87-109">Description</span><span class="sxs-lookup"><span data-stu-id="75b87-109">DESCRIPTION</span></span>

<span data-ttu-id="75b87-110">L' `Get-ComputerRestorePoint` applet de commande obtient les points de restauration système de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="75b87-110">The `Get-ComputerRestorePoint` cmdlet gets the local computer's system restore points.</span></span> <span data-ttu-id="75b87-111">De plus, il peut afficher l’état de la dernière tentative de restauration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75b87-111">And, it can display the status of the most recent attempt to restore the computer.</span></span>

<span data-ttu-id="75b87-112">Vous pouvez utiliser les informations de `Get-ComputerRestorePoint` pour sélectionner un point de restauration.</span><span class="sxs-lookup"><span data-stu-id="75b87-112">You can use the information from `Get-ComputerRestorePoint` to select a restore point.</span></span> <span data-ttu-id="75b87-113">Par exemple, utilisez un numéro de séquence pour identifier un point de restauration pour l’applet de commande `Restore-Computer` .</span><span class="sxs-lookup"><span data-stu-id="75b87-113">For example, use a sequence number to identify a restore point for the `Restore-Computer` cmdlet.</span></span>

<span data-ttu-id="75b87-114">Les points de restauration système et l' `Get-ComputerRestorePoint` applet de commande sont pris en charge uniquement sur les systèmes d’exploitation clients tels que Windows 10, Windows 7, Windows Vista et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="75b87-114">System restore points and the `Get-ComputerRestorePoint` cmdlet are supported only on client operating systems such as Windows 10, Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="75b87-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="75b87-115">EXAMPLES</span></span>

### <span data-ttu-id="75b87-116">Exemple 1 : récupération de tous les points de restauration du système</span><span class="sxs-lookup"><span data-stu-id="75b87-116">Example 1: Get all system restore points</span></span>

<span data-ttu-id="75b87-117">Dans cet exemple, `Get-ComputerRestorePoint` obtient tous les points de restauration du système de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="75b87-117">In this example, `Get-ComputerRestorePoint` gets all the local computer's system restore points.</span></span>

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### <span data-ttu-id="75b87-118">Exemple 2 : récupérer des numéros de séquence spécifiques</span><span class="sxs-lookup"><span data-stu-id="75b87-118">Example 2: Get specific sequence numbers</span></span>

<span data-ttu-id="75b87-119">Cet exemple obtient les points de restauration du système pour des numéros de séquence spécifiques.</span><span class="sxs-lookup"><span data-stu-id="75b87-119">This example gets system restore points for specific sequence numbers.</span></span>

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

<span data-ttu-id="75b87-120">`Get-ComputerRestorePoint` utilise le paramètre **RestorePoint** pour spécifier un tableau de numéros séquentiels séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="75b87-120">`Get-ComputerRestorePoint` uses the **RestorePoint** parameter to specify a comma-separated array of sequence numbers.</span></span>

### <span data-ttu-id="75b87-121">Exemple 3 : afficher l’état d’une restauration du système</span><span class="sxs-lookup"><span data-stu-id="75b87-121">Example 3: Display the status of a system restore</span></span>

<span data-ttu-id="75b87-122">Cet exemple affiche l’état de la restauration système la plus récente sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="75b87-122">This example displays the status of the most recent system restore on the local computer.</span></span>

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

<span data-ttu-id="75b87-123">`Get-ComputerRestorePoint` utilise le paramètre **LastStatus** pour afficher le résultat de la restauration système la plus récente.</span><span class="sxs-lookup"><span data-stu-id="75b87-123">`Get-ComputerRestorePoint` uses the **LastStatus** parameter to display the result of the most recent system restore.</span></span>

### <span data-ttu-id="75b87-124">Exemple 4 : utiliser une expression pour convertir CreationTime</span><span class="sxs-lookup"><span data-stu-id="75b87-124">Example 4: Use an expression to convert the CreationTime</span></span>

<span data-ttu-id="75b87-125">`Get-ComputerRestorePoint` génère le **CreationTime** sous forme de chaîne de date et d’heure de Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="75b87-125">`Get-ComputerRestorePoint` outputs the **CreationTime** as a Windows Management Instrumentation (WMI) date and time string.</span></span>

<span data-ttu-id="75b87-126">Dans cet exemple, une variable stocke une expression qui convertit la chaîne **CreationTime** en un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="75b87-126">In this example, a variable stores an expression that converts the **CreationTime** string to a **DateTime** object.</span></span> <span data-ttu-id="75b87-127">Pour afficher les chaînes **CreationTime** avant qu’elles ne soient converties, utilisez une commande telle que `((Get-ComputerRestorePoint).CreationTime)` .</span><span class="sxs-lookup"><span data-stu-id="75b87-127">To view **CreationTime** strings before they're converted, use a command such as `((Get-ComputerRestorePoint).CreationTime)`.</span></span> <span data-ttu-id="75b87-128">Pour plus d’informations sur la chaîne de date et d’heure WMI, consultez [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span><span class="sxs-lookup"><span data-stu-id="75b87-128">For more information about the WMI date and time string, see [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span></span>

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

<span data-ttu-id="75b87-129">La `$date` variable stocke une table de hachage avec l’expression qui utilise la méthode **ConvertToDateTime** .</span><span class="sxs-lookup"><span data-stu-id="75b87-129">The `$date` variable stores a hash table with the expression that uses the **ConvertToDateTime** method.</span></span> <span data-ttu-id="75b87-130">L’expression convertit la valeur de la propriété **CreationTime** d’une chaîne WMI en objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="75b87-130">The expression converts the **CreationTime** property's value from a WMI string to a **DateTime** object.</span></span>

<span data-ttu-id="75b87-131">`Get-ComputerRestorePoint` envoie les objets du point de restauration système vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="75b87-131">`Get-ComputerRestorePoint` sends the system restore point objects down the pipeline.</span></span> <span data-ttu-id="75b87-132">`Select-Object` utilise le paramètre **Property** pour spécifier les propriétés à afficher.</span><span class="sxs-lookup"><span data-stu-id="75b87-132">`Select-Object` uses the **Property** parameter to specify the properties to display.</span></span> <span data-ttu-id="75b87-133">Pour chaque objet dans le pipeline, l’expression dans `$date` convertit le **CreationTime** et renvoie le résultat dans la propriété **Date** .</span><span class="sxs-lookup"><span data-stu-id="75b87-133">For each object in the pipeline, the expression in `$date` converts the **CreationTime** and outputs the result in the **Date** property.</span></span>

### <span data-ttu-id="75b87-134">Exemple 5 : utiliser une propriété pour obtenir un numéro de séquence</span><span class="sxs-lookup"><span data-stu-id="75b87-134">Example 5: Use a property to get a sequence number</span></span>

<span data-ttu-id="75b87-135">Cet exemple obtient un numéro de séquence à l’aide **de la propriété de numéro** de séquence et d’un index de tableau.</span><span class="sxs-lookup"><span data-stu-id="75b87-135">This example gets a sequence number by using the **SequenceNumber** property and an array index.</span></span> <span data-ttu-id="75b87-136">La sortie contient uniquement le numéro de séquence.</span><span class="sxs-lookup"><span data-stu-id="75b87-136">The output only contains the sequence number.</span></span>

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

<span data-ttu-id="75b87-137">`Get-ComputerRestorePoint` utilise la **propriété de l'** appel de fonction avec un index de tableau.</span><span class="sxs-lookup"><span data-stu-id="75b87-137">`Get-ComputerRestorePoint` uses the **SequenceNumber** property with an array index.</span></span> <span data-ttu-id="75b87-138">L’index de tableau de `-1` obtient le numéro de séquence le plus récent dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="75b87-138">The array index of `-1` gets the most recent sequence number in the array.</span></span>

## <span data-ttu-id="75b87-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75b87-139">PARAMETERS</span></span>

### <span data-ttu-id="75b87-140">-LastStatus</span><span class="sxs-lookup"><span data-stu-id="75b87-140">-LastStatus</span></span>

<span data-ttu-id="75b87-141">Indique que `Get-ComputerRestorePoint` obtient l’état de la dernière opération de restauration du système.</span><span class="sxs-lookup"><span data-stu-id="75b87-141">Indicates that `Get-ComputerRestorePoint` gets the status of the most recent system restore operation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75b87-142">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="75b87-142">-RestorePoint</span></span>

<span data-ttu-id="75b87-143">Spécifie les numéros de séquence des points de restauration du système.</span><span class="sxs-lookup"><span data-stu-id="75b87-143">Specifies the sequence numbers of the system restore points.</span></span> <span data-ttu-id="75b87-144">Vous pouvez spécifier un numéro de séquence unique ou un tableau de numéros séquentiels séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="75b87-144">You can specify either a single sequence number or a comma-separated array of sequence numbers.</span></span>

<span data-ttu-id="75b87-145">Si le paramètre **RestorePoint** n’est pas spécifié, `Get-ComputerRestorePoint` retourne tous les points de restauration du système de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="75b87-145">If the **RestorePoint** parameter isn't specified, `Get-ComputerRestorePoint` returns all the local computer's system restore points.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75b87-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75b87-146">CommonParameters</span></span>

<span data-ttu-id="75b87-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75b87-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75b87-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="75b87-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75b87-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="75b87-149">INPUTS</span></span>

### <span data-ttu-id="75b87-150">Aucun</span><span class="sxs-lookup"><span data-stu-id="75b87-150">None</span></span>

<span data-ttu-id="75b87-151">Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Get-ComputerRestorePoint` .</span><span class="sxs-lookup"><span data-stu-id="75b87-151">You can't send objects down the pipeline to `Get-ComputerRestorePoint`.</span></span>

## <span data-ttu-id="75b87-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="75b87-152">OUTPUTS</span></span>

### <span data-ttu-id="75b87-153">System. Management. ManagementObject # root\default\SystemRestore ou chaîne</span><span class="sxs-lookup"><span data-stu-id="75b87-153">System.Management.ManagementObject#root\default\SystemRestore or String</span></span>

<span data-ttu-id="75b87-154">`Get-ComputerRestorePoint` retourne un objet **SystemRestore** , qui est une instance de la classe **SystemRestore** Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="75b87-154">`Get-ComputerRestorePoint` returns a **SystemRestore** object, which is an instance of the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

<span data-ttu-id="75b87-155">Quand vous utilisez le paramètre **LastStatus** , `Get-ComputerRestorePoint` retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="75b87-155">When you use the **LastStatus** parameter, `Get-ComputerRestorePoint` returns a string.</span></span>

## <span data-ttu-id="75b87-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="75b87-156">NOTES</span></span>

<span data-ttu-id="75b87-157">Pour exécuter une `Get-ComputerRestorePoint` commande sur Windows Vista et les versions ultérieures de Windows, ouvrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="75b87-157">To run a `Get-ComputerRestorePoint` command on Windows Vista and later versions of Windows, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="75b87-158">`Get-ComputerRestorePoint` utilise la classe WMI **SystemRestore** .</span><span class="sxs-lookup"><span data-stu-id="75b87-158">`Get-ComputerRestorePoint` uses the WMI **SystemRestore** class.</span></span>

## <span data-ttu-id="75b87-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="75b87-159">RELATED LINKS</span></span>

[<span data-ttu-id="75b87-160">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="75b87-160">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="75b87-161">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="75b87-161">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="75b87-162">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="75b87-162">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="75b87-163">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="75b87-163">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="75b87-164">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="75b87-164">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="75b87-165">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="75b87-165">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="75b87-166">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="75b87-166">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="75b87-167">SystemRestore</span><span class="sxs-lookup"><span data-stu-id="75b87-167">SystemRestore</span></span>](/windows/win32/sr/systemrestore)
