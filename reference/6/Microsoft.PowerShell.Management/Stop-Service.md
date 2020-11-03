---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: fac6369859c3f8e3181a9044d381d01c12fea062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202409"
---
# <span data-ttu-id="1201b-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-103">Stop-Service</span></span>

## <span data-ttu-id="1201b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1201b-104">SYNOPSIS</span></span>
<span data-ttu-id="1201b-105">Arrête un ou plusieurs services en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="1201b-105">Stops one or more running services.</span></span>

## <span data-ttu-id="1201b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1201b-106">SYNTAX</span></span>

### <span data-ttu-id="1201b-107">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="1201b-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1201b-108">Default</span><span class="sxs-lookup"><span data-stu-id="1201b-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1201b-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1201b-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1201b-110">Description</span><span class="sxs-lookup"><span data-stu-id="1201b-110">DESCRIPTION</span></span>

<span data-ttu-id="1201b-111">L’applet de commande **Stop-service** envoie un message d’arrêt au contrôleur de services Windows pour chacun des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1201b-111">The **Stop-Service** cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="1201b-112">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente le service que vous souhaitez arrêter.</span><span class="sxs-lookup"><span data-stu-id="1201b-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="1201b-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1201b-113">EXAMPLES</span></span>

### <span data-ttu-id="1201b-114">Exemple 1 : arrêter un service sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="1201b-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="1201b-115">Cette commande arrête le service Journaux et alertes de performance (SysmonLog) sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1201b-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="1201b-116">Exemple 2 : arrêter un service à l’aide du nom complet</span><span class="sxs-lookup"><span data-stu-id="1201b-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="1201b-117">Cette commande arrête le service Telnet sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1201b-117">This command stops the Telnet service on the local computer.</span></span>
<span data-ttu-id="1201b-118">La commande utilise la commande de **service** pour récupérer un objet représentant le service Telnet.</span><span class="sxs-lookup"><span data-stu-id="1201b-118">The command uses **Get-Service** to get an object that represents the Telnet service.</span></span>
<span data-ttu-id="1201b-119">L’opérateur de pipeline (|) dirige l’objet vers **Stop-service** , ce qui arrête le service.</span><span class="sxs-lookup"><span data-stu-id="1201b-119">The pipeline operator (|) pipes the object to **Stop-Service** , which stops the service.</span></span>

### <span data-ttu-id="1201b-120">Exemple 3 : arrêter un service qui a des services dépendants</span><span class="sxs-lookup"><span data-stu-id="1201b-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="1201b-121">Cet exemple arrête le service IISAdmin sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1201b-121">This example stops the IISAdmin service on the local computer.</span></span>
<span data-ttu-id="1201b-122">Étant donné que l’arrêt de ce service arrête également les services qui dépendent du service IISAdmin, il est préférable de faire précéder le service **Stop-service** d’une commande qui répertorie les services qui dépendent du service IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="1201b-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede **Stop-Service** with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="1201b-123">La première commande répertorie les services qui dépendent d’IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="1201b-123">The first command lists the services that depend on IISAdmin.</span></span>
<span data-ttu-id="1201b-124">Elle utilise le **service d’accès aux services** pour récupérer un objet qui représente le service IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="1201b-124">It uses **Get-Service** to get an object that represents the IISAdmin service.</span></span>
<span data-ttu-id="1201b-125">L’opérateur de pipeline (|) passe le résultat à l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="1201b-125">The pipeline operator (|) passes the result to the Format-List cmdlet.</span></span>
<span data-ttu-id="1201b-126">La commande utilise le paramètre *Property* de **format-list** pour répertorier uniquement les propriétés **Name** et **DependentServices** du service.</span><span class="sxs-lookup"><span data-stu-id="1201b-126">The command uses the *Property* parameter of **Format-List** to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="1201b-127">La deuxième commande arrête le service IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="1201b-127">The second command stops the IISAdmin service.</span></span>
<span data-ttu-id="1201b-128">Le paramètre *force* est requis pour arrêter un service qui a des services dépendants.</span><span class="sxs-lookup"><span data-stu-id="1201b-128">The *Force* parameter is required to stop a service that has dependent services.</span></span>
<span data-ttu-id="1201b-129">La commande utilise le paramètre *Confirm* pour demander la confirmation de l’utilisateur avant d’arrêter chaque service.</span><span class="sxs-lookup"><span data-stu-id="1201b-129">The command uses the *Confirm* parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="1201b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1201b-130">PARAMETERS</span></span>

### <span data-ttu-id="1201b-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="1201b-131">-DisplayName</span></span>

<span data-ttu-id="1201b-132">Spécifie les noms d’affichage des services à arrêter.</span><span class="sxs-lookup"><span data-stu-id="1201b-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="1201b-133">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1201b-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="1201b-134">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1201b-134">-Exclude</span></span>

<span data-ttu-id="1201b-135">Spécifie les services que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="1201b-135">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="1201b-136">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="1201b-136">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="1201b-137">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="1201b-137">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="1201b-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1201b-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="1201b-139">-Force</span><span class="sxs-lookup"><span data-stu-id="1201b-139">-Force</span></span>

<span data-ttu-id="1201b-140">Force l’applet de commande à arrêter un service même si ce service a des services dépendants.</span><span class="sxs-lookup"><span data-stu-id="1201b-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="1201b-141">-Include</span><span class="sxs-lookup"><span data-stu-id="1201b-141">-Include</span></span>

<span data-ttu-id="1201b-142">Spécifie les services que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="1201b-142">Specifies services that this cmdlet stops.</span></span>
<span data-ttu-id="1201b-143">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="1201b-143">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="1201b-144">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="1201b-144">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="1201b-145">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1201b-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="1201b-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1201b-146">-InputObject</span></span>

<span data-ttu-id="1201b-147">Spécifie les objets **ServiceController** qui représentent les services à arrêter.</span><span class="sxs-lookup"><span data-stu-id="1201b-147">Specifies **ServiceController** objects that represent the services to stop.</span></span>
<span data-ttu-id="1201b-148">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="1201b-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="1201b-149">-Name</span><span class="sxs-lookup"><span data-stu-id="1201b-149">-Name</span></span>

<span data-ttu-id="1201b-150">Spécifie les noms des services à arrêter.</span><span class="sxs-lookup"><span data-stu-id="1201b-150">Specifies the service names of the services to stop.</span></span>
<span data-ttu-id="1201b-151">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1201b-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="1201b-152">-NOWAIT</span><span class="sxs-lookup"><span data-stu-id="1201b-152">-NoWait</span></span>

<span data-ttu-id="1201b-153">Indique que cette applet de commande utilise l’option no Wait.</span><span class="sxs-lookup"><span data-stu-id="1201b-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="1201b-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1201b-154">-PassThru</span></span>

<span data-ttu-id="1201b-155">Retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="1201b-155">Returns an object that represents the service.</span></span>
<span data-ttu-id="1201b-156">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="1201b-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1201b-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1201b-157">-Confirm</span></span>

<span data-ttu-id="1201b-158">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1201b-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1201b-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1201b-159">-WhatIf</span></span>

<span data-ttu-id="1201b-160">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1201b-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1201b-161">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1201b-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1201b-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1201b-162">CommonParameters</span></span>

<span data-ttu-id="1201b-163">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1201b-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1201b-164">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1201b-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1201b-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1201b-165">INPUTS</span></span>

### <span data-ttu-id="1201b-166">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="1201b-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="1201b-167">Vous pouvez diriger un objet de service ou une chaîne qui contient le nom d’un service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1201b-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="1201b-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1201b-168">OUTPUTS</span></span>

### <span data-ttu-id="1201b-169">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="1201b-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="1201b-170">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous utilisez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="1201b-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="1201b-171">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1201b-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1201b-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1201b-172">NOTES</span></span>

* <span data-ttu-id="1201b-173">Vous pouvez également faire référence à **Stop-service** par son alias intégré, **spsv** .</span><span class="sxs-lookup"><span data-stu-id="1201b-173">You can also refer to **Stop-Service** by its built-in alias, **spsv** .</span></span> <span data-ttu-id="1201b-174">Pour plus d'informations, consultez about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="1201b-174">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="1201b-175">**Stop-service** peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="1201b-175">**Stop-Service** can control services only when the current user has permission to do this.</span></span>
<span data-ttu-id="1201b-176">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="1201b-176">If a command does not work correctly, you might not have the required permissions.</span></span>

  <span data-ttu-id="1201b-177">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="1201b-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
<span data-ttu-id="1201b-178">Les noms de service s’affichent dans la colonne **nom** et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="1201b-178">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

*

## <span data-ttu-id="1201b-179">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1201b-179">RELATED LINKS</span></span>

[<span data-ttu-id="1201b-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="1201b-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="1201b-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="1201b-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="1201b-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="1201b-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="1201b-186">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-186">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="1201b-187">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="1201b-187">Remove-Service</span></span>](Remove-Service.md)
