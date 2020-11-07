---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: c68b9f5d145c190cc786ee5da7a98e0fc6170ead
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347548"
---
# <span data-ttu-id="e61a3-103">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-103">Suspend-Service</span></span>

## <span data-ttu-id="e61a3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e61a3-104">SYNOPSIS</span></span>
<span data-ttu-id="e61a3-105">Interrompt (suspend) un ou plusieurs services en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="e61a3-105">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="e61a3-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e61a3-106">SYNTAX</span></span>

### <span data-ttu-id="e61a3-107">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="e61a3-107">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e61a3-108">Default</span><span class="sxs-lookup"><span data-stu-id="e61a3-108">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e61a3-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e61a3-109">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e61a3-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e61a3-110">DESCRIPTION</span></span>

<span data-ttu-id="e61a3-111">L' `Suspend-Service` applet de commande envoie un message d’interruption au contrôleur de services Windows pour chacun des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e61a3-111">The `Suspend-Service` cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="e61a3-112">Pendant l’interruption, le service est toujours en cours d’exécution, mais son action est arrêtée jusqu’à sa reprise, par exemple par l’applet de commande objet `Resume-Service` .</span><span class="sxs-lookup"><span data-stu-id="e61a3-112">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe `Resume-Service` cmdlet.</span></span> <span data-ttu-id="e61a3-113">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente les services que vous souhaitez suspendre.</span><span class="sxs-lookup"><span data-stu-id="e61a3-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="e61a3-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e61a3-114">EXAMPLES</span></span>

### <span data-ttu-id="e61a3-115">Exemple 1 : suspendre un service</span><span class="sxs-lookup"><span data-stu-id="e61a3-115">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="e61a3-116">Cette commande interrompt le service Telnet (Tlntsvr) sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e61a3-116">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="e61a3-117">Exemple 2 : afficher ce qui se passerait si vous suspendez des services</span><span class="sxs-lookup"><span data-stu-id="e61a3-117">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="e61a3-118">Cette commande indique ce qui se passerait si vous suspendiez les services dont le nom de service commence par LANMAN.</span><span class="sxs-lookup"><span data-stu-id="e61a3-118">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span> <span data-ttu-id="e61a3-119">Pour interrompre les services, réexécutez la commande sans le paramètre **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-119">To suspend the services, rerun the command without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="e61a3-120">Exemple 3 : obtenir et suspendre un service</span><span class="sxs-lookup"><span data-stu-id="e61a3-120">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="e61a3-121">Cette commande utilise l' `Get-Service` applet de commande pour récupérer un objet qui représente le service Planificateur de tâches (planification) sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e61a3-121">This command uses the `Get-Service` cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span> <span data-ttu-id="e61a3-122">L’opérateur de pipeline ( `|` ) passe le résultat à `Suspend-Service` , qui suspend le service.</span><span class="sxs-lookup"><span data-stu-id="e61a3-122">The pipeline operator (`|`) passes the result to `Suspend-Service`, which suspends the service.</span></span>

### <span data-ttu-id="e61a3-123">Exemple 4 : suspendre tous les services qui peuvent être suspendus</span><span class="sxs-lookup"><span data-stu-id="e61a3-123">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="e61a3-124">Cette commande interrompt tous les services pouvant être interrompus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e61a3-124">This command suspends all of the services on the computer that can be suspended.</span></span> <span data-ttu-id="e61a3-125">Elle utilise `Get-Service` pour récupérer des objets qui représentent les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e61a3-125">It uses `Get-Service` to get objects that represent the services on the computer.</span></span> <span data-ttu-id="e61a3-126">L’opérateur de pipeline passe les résultats à l’applet de commande `Where-Object` , qui sélectionne uniquement les services dont `$True` la valeur est pour la propriété **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-126">The pipeline operator passes the results to the `Where-Object` cmdlet, which selects only the services that have a value of `$True` for the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="e61a3-127">Un autre opérateur de pipeline passe les résultats à `Suspend-Service` .</span><span class="sxs-lookup"><span data-stu-id="e61a3-127">Another pipeline operator passes the results to `Suspend-Service`.</span></span> <span data-ttu-id="e61a3-128">Le paramètre **Confirm** vous invite à confirmer l’interruption de chaque service.</span><span class="sxs-lookup"><span data-stu-id="e61a3-128">The **Confirm** parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="e61a3-129">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="e61a3-129">PARAMETERS</span></span>

### <span data-ttu-id="e61a3-130">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="e61a3-130">-DisplayName</span></span>

<span data-ttu-id="e61a3-131">Spécifie les noms d’affichage des services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="e61a3-131">Specifies the display names of the services to be suspended.</span></span> <span data-ttu-id="e61a3-132">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e61a3-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e61a3-133">-Exclude</span><span class="sxs-lookup"><span data-stu-id="e61a3-133">-Exclude</span></span>

<span data-ttu-id="e61a3-134">Spécifie les services à omettre des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e61a3-134">Specifies services to omit from the specified services.</span></span> <span data-ttu-id="e61a3-135">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-135">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e61a3-136">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="e61a3-136">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="e61a3-137">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e61a3-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e61a3-138">-Include</span><span class="sxs-lookup"><span data-stu-id="e61a3-138">-Include</span></span>

<span data-ttu-id="e61a3-139">Spécifie les services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="e61a3-139">Specifies services to suspend.</span></span> <span data-ttu-id="e61a3-140">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e61a3-141">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="e61a3-141">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="e61a3-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e61a3-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e61a3-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e61a3-143">-InputObject</span></span>

<span data-ttu-id="e61a3-144">Spécifie les objets **ServiceController** qui représentent les services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="e61a3-144">Specifies **ServiceController** objects that represent the services to suspend.</span></span> <span data-ttu-id="e61a3-145">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="e61a3-145">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="e61a3-146">-Name</span><span class="sxs-lookup"><span data-stu-id="e61a3-146">-Name</span></span>

<span data-ttu-id="e61a3-147">Spécifie les noms des services à interrompre.</span><span class="sxs-lookup"><span data-stu-id="e61a3-147">Specifies the service names of the services to suspend.</span></span> <span data-ttu-id="e61a3-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e61a3-148">Wildcard characters are permitted.</span></span>

<span data-ttu-id="e61a3-149">Le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e61a3-149">The parameter name is optional.</span></span> <span data-ttu-id="e61a3-150">Vous pouvez utiliser **Name** ou son alias, **ServiceName** ou omettre le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="e61a3-150">You can use **Name** or its alias, **ServiceName** , or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="e61a3-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e61a3-151">-PassThru</span></span>

<span data-ttu-id="e61a3-152">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e61a3-152">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="e61a3-153">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="e61a3-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e61a3-154">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e61a3-154">-Confirm</span></span>

<span data-ttu-id="e61a3-155">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e61a3-155">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e61a3-156">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e61a3-156">-WhatIf</span></span>

<span data-ttu-id="e61a3-157">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e61a3-157">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e61a3-158">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e61a3-158">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e61a3-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e61a3-159">CommonParameters</span></span>

<span data-ttu-id="e61a3-160">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e61a3-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e61a3-161">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e61a3-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e61a3-162">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e61a3-162">INPUTS</span></span>

### <span data-ttu-id="e61a3-163">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="e61a3-163">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="e61a3-164">Vous pouvez diriger un objet de service ou une chaîne qui contient un nom de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e61a3-164">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="e61a3-165">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e61a3-165">OUTPUTS</span></span>

### <span data-ttu-id="e61a3-166">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e61a3-166">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="e61a3-167">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-167">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="e61a3-168">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e61a3-168">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e61a3-169">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e61a3-169">NOTES</span></span>

<span data-ttu-id="e61a3-170">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="e61a3-170">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="e61a3-171">`Suspend-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="e61a3-171">`Suspend-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="e61a3-172">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="e61a3-172">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="e61a3-173">`Suspend-Service` peut suspendre uniquement les services qui prennent en charge l’interruption et la reprise.</span><span class="sxs-lookup"><span data-stu-id="e61a3-173">`Suspend-Service` can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="e61a3-174">Pour déterminer si un service particulier peut être interrompu, utilisez l' `Get-Service` applet de commande avec la propriété **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-174">To determine whether a particular service can be suspended, use the `Get-Service` cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="e61a3-175">Par exemple, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span><span class="sxs-lookup"><span data-stu-id="e61a3-175">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="e61a3-176">Pour rechercher tous les services sur l’ordinateur qui peuvent être suspendus, tapez `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .</span><span class="sxs-lookup"><span data-stu-id="e61a3-176">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
- <span data-ttu-id="e61a3-177">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="e61a3-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="e61a3-178">Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="e61a3-178">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="e61a3-179">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e61a3-179">RELATED LINKS</span></span>

[<span data-ttu-id="e61a3-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="e61a3-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="e61a3-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="e61a3-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="e61a3-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="e61a3-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="e61a3-186">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-186">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="e61a3-187">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="e61a3-187">Remove-Service</span></span>](Remove-Service.md)
