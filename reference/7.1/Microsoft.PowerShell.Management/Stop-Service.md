---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: fae0ac83c86bb6e1767bcc9b48ce492e8068139c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347565"
---
# <span data-ttu-id="bd295-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-103">Stop-Service</span></span>

## <span data-ttu-id="bd295-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bd295-104">SYNOPSIS</span></span>
<span data-ttu-id="bd295-105">Arrête un ou plusieurs services en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="bd295-105">Stops one or more running services.</span></span>

## <span data-ttu-id="bd295-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bd295-106">SYNTAX</span></span>

### <span data-ttu-id="bd295-107">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="bd295-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bd295-108">Default</span><span class="sxs-lookup"><span data-stu-id="bd295-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bd295-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bd295-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bd295-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bd295-110">DESCRIPTION</span></span>

<span data-ttu-id="bd295-111">L' `Stop-Service` applet de commande envoie un message d’arrêt au contrôleur de services Windows pour chacun des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bd295-111">The `Stop-Service` cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="bd295-112">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente le service que vous souhaitez arrêter.</span><span class="sxs-lookup"><span data-stu-id="bd295-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="bd295-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bd295-113">EXAMPLES</span></span>

### <span data-ttu-id="bd295-114">Exemple 1 : arrêter un service sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="bd295-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="bd295-115">Cette commande arrête le service Journaux et alertes de performance (SysmonLog) sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bd295-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="bd295-116">Exemple 2 : arrêter un service à l’aide du nom complet</span><span class="sxs-lookup"><span data-stu-id="bd295-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="bd295-117">Cette commande arrête le service Telnet sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bd295-117">This command stops the Telnet service on the local computer.</span></span> <span data-ttu-id="bd295-118">La commande utilise `Get-Service` pour récupérer un objet qui représente le service Telnet.</span><span class="sxs-lookup"><span data-stu-id="bd295-118">The command uses `Get-Service` to get an object that represents the Telnet service.</span></span> <span data-ttu-id="bd295-119">L’opérateur de pipeline ( `|` ) dirige l’objet vers `Stop-Service` , qui arrête le service.</span><span class="sxs-lookup"><span data-stu-id="bd295-119">The pipeline operator (`|`) pipes the object to `Stop-Service`, which stops the service.</span></span>

### <span data-ttu-id="bd295-120">Exemple 3 : arrêter un service qui a des services dépendants</span><span class="sxs-lookup"><span data-stu-id="bd295-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="bd295-121">Cet exemple arrête le service IISAdmin sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bd295-121">This example stops the IISAdmin service on the local computer.</span></span> <span data-ttu-id="bd295-122">Étant donné que l’arrêt de ce service arrête également les services qui dépendent du service IISAdmin, il est préférable de faire précéder d' `Stop-Service` une commande qui répertorie les services qui dépendent du service IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="bd295-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede `Stop-Service` with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="bd295-123">La première commande répertorie les services qui dépendent d’IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="bd295-123">The first command lists the services that depend on IISAdmin.</span></span> <span data-ttu-id="bd295-124">Elle utilise `Get-Service` pour récupérer un objet qui représente le service IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="bd295-124">It uses `Get-Service` to get an object that represents the IISAdmin service.</span></span> <span data-ttu-id="bd295-125">L’opérateur de pipeline ( `|` ) transmet le résultat à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="bd295-125">The pipeline operator (`|`) passes the result to the `Format-List` cmdlet.</span></span> <span data-ttu-id="bd295-126">La commande utilise le paramètre **Property** de `Format-List` pour répertorier uniquement les propriétés **Name** et **DependentServices** du service.</span><span class="sxs-lookup"><span data-stu-id="bd295-126">The command uses the **Property** parameter of `Format-List` to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="bd295-127">La deuxième commande arrête le service IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="bd295-127">The second command stops the IISAdmin service.</span></span> <span data-ttu-id="bd295-128">Le paramètre **force** est requis pour arrêter un service qui a des services dépendants.</span><span class="sxs-lookup"><span data-stu-id="bd295-128">The **Force** parameter is required to stop a service that has dependent services.</span></span> <span data-ttu-id="bd295-129">La commande utilise le paramètre **Confirm** pour demander la confirmation de l’utilisateur avant d’arrêter chaque service.</span><span class="sxs-lookup"><span data-stu-id="bd295-129">The command uses the **Confirm** parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="bd295-130">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="bd295-130">PARAMETERS</span></span>

### <span data-ttu-id="bd295-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="bd295-131">-DisplayName</span></span>

<span data-ttu-id="bd295-132">Spécifie les noms d’affichage des services à arrêter.</span><span class="sxs-lookup"><span data-stu-id="bd295-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="bd295-133">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bd295-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bd295-134">-Exclude</span><span class="sxs-lookup"><span data-stu-id="bd295-134">-Exclude</span></span>

<span data-ttu-id="bd295-135">Spécifie les services que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="bd295-135">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="bd295-136">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="bd295-136">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="bd295-137">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="bd295-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="bd295-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bd295-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bd295-139">-Force</span><span class="sxs-lookup"><span data-stu-id="bd295-139">-Force</span></span>

<span data-ttu-id="bd295-140">Force l’applet de commande à arrêter un service même si ce service a des services dépendants.</span><span class="sxs-lookup"><span data-stu-id="bd295-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="bd295-141">-Include</span><span class="sxs-lookup"><span data-stu-id="bd295-141">-Include</span></span>

<span data-ttu-id="bd295-142">Spécifie les services que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="bd295-142">Specifies services that this cmdlet stops.</span></span> <span data-ttu-id="bd295-143">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="bd295-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="bd295-144">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="bd295-144">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="bd295-145">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bd295-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bd295-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bd295-146">-InputObject</span></span>

<span data-ttu-id="bd295-147">Spécifie les objets **ServiceController** qui représentent les services à arrêter.</span><span class="sxs-lookup"><span data-stu-id="bd295-147">Specifies **ServiceController** objects that represent the services to stop.</span></span> <span data-ttu-id="bd295-148">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="bd295-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="bd295-149">-Name</span><span class="sxs-lookup"><span data-stu-id="bd295-149">-Name</span></span>

<span data-ttu-id="bd295-150">Spécifie les noms des services à arrêter.</span><span class="sxs-lookup"><span data-stu-id="bd295-150">Specifies the service names of the services to stop.</span></span> <span data-ttu-id="bd295-151">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="bd295-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bd295-152">-NOWAIT</span><span class="sxs-lookup"><span data-stu-id="bd295-152">-NoWait</span></span>

<span data-ttu-id="bd295-153">Indique que cette applet de commande utilise l’option no Wait.</span><span class="sxs-lookup"><span data-stu-id="bd295-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="bd295-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bd295-154">-PassThru</span></span>

<span data-ttu-id="bd295-155">Retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="bd295-155">Returns an object that represents the service.</span></span> <span data-ttu-id="bd295-156">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="bd295-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="bd295-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bd295-157">-Confirm</span></span>

<span data-ttu-id="bd295-158">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bd295-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bd295-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bd295-159">-WhatIf</span></span>

<span data-ttu-id="bd295-160">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bd295-160">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bd295-161">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="bd295-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bd295-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd295-162">CommonParameters</span></span>

<span data-ttu-id="bd295-163">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd295-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd295-164">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bd295-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd295-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bd295-165">INPUTS</span></span>

### <span data-ttu-id="bd295-166">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="bd295-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="bd295-167">Vous pouvez diriger un objet de service ou une chaîne qui contient le nom d’un service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bd295-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="bd295-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bd295-168">OUTPUTS</span></span>

### <span data-ttu-id="bd295-169">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="bd295-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="bd295-170">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous utilisez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="bd295-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the **PassThru** parameter.</span></span> <span data-ttu-id="bd295-171">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="bd295-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bd295-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bd295-172">NOTES</span></span>

<span data-ttu-id="bd295-173">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="bd295-173">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="bd295-174">Vous pouvez également faire référence à `Stop-Service` par son alias intégré, **spsv**.</span><span class="sxs-lookup"><span data-stu-id="bd295-174">You can also refer to `Stop-Service` by its built-in alias, **spsv**.</span></span> <span data-ttu-id="bd295-175">Pour plus d'informations, consultez about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="bd295-175">For more information, see about_Aliases.</span></span>

<span data-ttu-id="bd295-176">`Stop-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="bd295-176">`Stop-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="bd295-177">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="bd295-177">If a command does not work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="bd295-178">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="bd295-178">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="bd295-179">Les noms de service s’affichent dans la colonne **nom** et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="bd295-179">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="bd295-180">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bd295-180">RELATED LINKS</span></span>

[<span data-ttu-id="bd295-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="bd295-182">New-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-182">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="bd295-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="bd295-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="bd295-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="bd295-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="bd295-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="bd295-188">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="bd295-188">Remove-Service</span></span>](Remove-Service.md)
