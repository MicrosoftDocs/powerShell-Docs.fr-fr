---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 9515f524df38813817b3fefd1437a3e2df296392
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595731"
---
# <span data-ttu-id="ad02a-102">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-102">Suspend-Service</span></span>

## <span data-ttu-id="ad02a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ad02a-103">SYNOPSIS</span></span>
<span data-ttu-id="ad02a-104">Interrompt (suspend) un ou plusieurs services en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="ad02a-104">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="ad02a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ad02a-105">SYNTAX</span></span>

### <span data-ttu-id="ad02a-106">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="ad02a-106">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad02a-107">Default</span><span class="sxs-lookup"><span data-stu-id="ad02a-107">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ad02a-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ad02a-108">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ad02a-109">Description</span><span class="sxs-lookup"><span data-stu-id="ad02a-109">DESCRIPTION</span></span>

<span data-ttu-id="ad02a-110">L' `Suspend-Service` applet de commande envoie un message d’interruption au contrôleur de services Windows pour chacun des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad02a-110">The `Suspend-Service` cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="ad02a-111">Pendant l’interruption, le service est toujours en cours d’exécution, mais son action est arrêtée jusqu’à sa reprise, par exemple par l’applet de commande objet `Resume-Service` .</span><span class="sxs-lookup"><span data-stu-id="ad02a-111">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe `Resume-Service` cmdlet.</span></span> <span data-ttu-id="ad02a-112">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente les services que vous souhaitez suspendre.</span><span class="sxs-lookup"><span data-stu-id="ad02a-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="ad02a-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ad02a-113">EXAMPLES</span></span>

### <span data-ttu-id="ad02a-114">Exemple 1 : suspendre un service</span><span class="sxs-lookup"><span data-stu-id="ad02a-114">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="ad02a-115">Cette commande interrompt le service Telnet (Tlntsvr) sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ad02a-115">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="ad02a-116">Exemple 2 : afficher ce qui se passerait si vous suspendez des services</span><span class="sxs-lookup"><span data-stu-id="ad02a-116">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="ad02a-117">Cette commande indique ce qui se passerait si vous suspendiez les services dont le nom de service commence par LANMAN.</span><span class="sxs-lookup"><span data-stu-id="ad02a-117">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span> <span data-ttu-id="ad02a-118">Pour interrompre les services, réexécutez la commande sans le paramètre **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-118">To suspend the services, rerun the command without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="ad02a-119">Exemple 3 : obtenir et suspendre un service</span><span class="sxs-lookup"><span data-stu-id="ad02a-119">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="ad02a-120">Cette commande utilise l' `Get-Service` applet de commande pour récupérer un objet qui représente le service Planificateur de tâches (planification) sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad02a-120">This command uses the `Get-Service` cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span> <span data-ttu-id="ad02a-121">L’opérateur de pipeline ( `|` ) passe le résultat à `Suspend-Service` , qui suspend le service.</span><span class="sxs-lookup"><span data-stu-id="ad02a-121">The pipeline operator (`|`) passes the result to `Suspend-Service`, which suspends the service.</span></span>

### <span data-ttu-id="ad02a-122">Exemple 4 : suspendre tous les services qui peuvent être suspendus</span><span class="sxs-lookup"><span data-stu-id="ad02a-122">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="ad02a-123">Cette commande interrompt tous les services pouvant être interrompus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad02a-123">This command suspends all of the services on the computer that can be suspended.</span></span> <span data-ttu-id="ad02a-124">Elle utilise `Get-Service` pour récupérer des objets qui représentent les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad02a-124">It uses `Get-Service` to get objects that represent the services on the computer.</span></span> <span data-ttu-id="ad02a-125">L’opérateur de pipeline passe les résultats à l’applet de commande `Where-Object` , qui sélectionne uniquement les services dont `$True` la valeur est pour la propriété **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-125">The pipeline operator passes the results to the `Where-Object` cmdlet, which selects only the services that have a value of `$True` for the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="ad02a-126">Un autre opérateur de pipeline passe les résultats à `Suspend-Service` .</span><span class="sxs-lookup"><span data-stu-id="ad02a-126">Another pipeline operator passes the results to `Suspend-Service`.</span></span> <span data-ttu-id="ad02a-127">Le paramètre **Confirm** vous invite à confirmer l’interruption de chaque service.</span><span class="sxs-lookup"><span data-stu-id="ad02a-127">The **Confirm** parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="ad02a-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad02a-128">PARAMETERS</span></span>

### <span data-ttu-id="ad02a-129">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="ad02a-129">-DisplayName</span></span>

<span data-ttu-id="ad02a-130">Spécifie les noms d’affichage des services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="ad02a-130">Specifies the display names of the services to be suspended.</span></span> <span data-ttu-id="ad02a-131">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ad02a-131">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ad02a-132">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ad02a-132">-Exclude</span></span>

<span data-ttu-id="ad02a-133">Spécifie les services à omettre des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad02a-133">Specifies services to omit from the specified services.</span></span> <span data-ttu-id="ad02a-134">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-134">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="ad02a-135">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="ad02a-135">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="ad02a-136">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ad02a-136">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ad02a-137">-Include</span><span class="sxs-lookup"><span data-stu-id="ad02a-137">-Include</span></span>

<span data-ttu-id="ad02a-138">Spécifie les services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="ad02a-138">Specifies services to suspend.</span></span> <span data-ttu-id="ad02a-139">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="ad02a-140">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="ad02a-140">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="ad02a-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ad02a-141">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ad02a-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ad02a-142">-InputObject</span></span>

<span data-ttu-id="ad02a-143">Spécifie les objets **ServiceController** qui représentent les services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="ad02a-143">Specifies **ServiceController** objects that represent the services to suspend.</span></span> <span data-ttu-id="ad02a-144">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="ad02a-144">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ad02a-145">-Name</span><span class="sxs-lookup"><span data-stu-id="ad02a-145">-Name</span></span>

<span data-ttu-id="ad02a-146">Spécifie les noms des services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="ad02a-146">Specifies the service names of the services to suspend.</span></span> <span data-ttu-id="ad02a-147">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ad02a-147">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ad02a-148">Le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad02a-148">The parameter name is optional.</span></span> <span data-ttu-id="ad02a-149">Vous pouvez utiliser **Name** ou son alias, **ServiceName** ou omettre le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="ad02a-149">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ad02a-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ad02a-150">-PassThru</span></span>

<span data-ttu-id="ad02a-151">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="ad02a-151">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="ad02a-152">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="ad02a-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ad02a-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ad02a-153">-Confirm</span></span>

<span data-ttu-id="ad02a-154">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad02a-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ad02a-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ad02a-155">-WhatIf</span></span>

<span data-ttu-id="ad02a-156">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad02a-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ad02a-157">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ad02a-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ad02a-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad02a-158">CommonParameters</span></span>

<span data-ttu-id="ad02a-159">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ad02a-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad02a-160">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ad02a-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad02a-161">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ad02a-161">INPUTS</span></span>

### <span data-ttu-id="ad02a-162">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="ad02a-162">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="ad02a-163">Vous pouvez diriger un objet de service ou une chaîne qui contient un nom de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad02a-163">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="ad02a-164">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ad02a-164">OUTPUTS</span></span>

### <span data-ttu-id="ad02a-165">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="ad02a-165">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="ad02a-166">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-166">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="ad02a-167">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ad02a-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ad02a-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ad02a-168">NOTES</span></span>

<span data-ttu-id="ad02a-169">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="ad02a-169">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="ad02a-170">`Suspend-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="ad02a-170">`Suspend-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="ad02a-171">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="ad02a-171">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="ad02a-172">`Suspend-Service` peut suspendre uniquement les services qui prennent en charge l’interruption et la reprise.</span><span class="sxs-lookup"><span data-stu-id="ad02a-172">`Suspend-Service` can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="ad02a-173">Pour déterminer si un service particulier peut être interrompu, utilisez l' `Get-Service` applet de commande avec la propriété **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-173">To determine whether a particular service can be suspended, use the `Get-Service` cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="ad02a-174">Par exemple, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span><span class="sxs-lookup"><span data-stu-id="ad02a-174">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="ad02a-175">Pour rechercher tous les services sur l’ordinateur qui peuvent être suspendus, tapez `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .</span><span class="sxs-lookup"><span data-stu-id="ad02a-175">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
- <span data-ttu-id="ad02a-176">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="ad02a-176">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="ad02a-177">Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="ad02a-177">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="ad02a-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ad02a-178">RELATED LINKS</span></span>

[<span data-ttu-id="ad02a-179">Get-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-179">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="ad02a-180">New-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-180">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="ad02a-181">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-181">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="ad02a-182">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-182">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="ad02a-183">Set-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-183">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="ad02a-184">Start-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-184">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="ad02a-185">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-185">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="ad02a-186">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="ad02a-186">Remove-Service</span></span>](Remove-Service.md)
