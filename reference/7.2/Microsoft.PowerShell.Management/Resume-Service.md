---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 8ce2182117167d93c8f7abd86eeb2c79abdf09c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596329"
---
# <span data-ttu-id="9f076-102">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-102">Resume-Service</span></span>

## <span data-ttu-id="9f076-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9f076-103">SYNOPSIS</span></span>
<span data-ttu-id="9f076-104">Reprend un ou plusieurs services interrompus (suspendus).</span><span class="sxs-lookup"><span data-stu-id="9f076-104">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="9f076-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="9f076-105">SYNTAX</span></span>

### <span data-ttu-id="9f076-106">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="9f076-106">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9f076-107">Default</span><span class="sxs-lookup"><span data-stu-id="9f076-107">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="9f076-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9f076-108">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9f076-109">Description</span><span class="sxs-lookup"><span data-stu-id="9f076-109">DESCRIPTION</span></span>

<span data-ttu-id="9f076-110">L' `Resume-Service` applet de commande envoie un message de reprise au contrôleur de services Windows pour chacun des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9f076-110">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="9f076-111">Si un service est suspendu, il reprend.</span><span class="sxs-lookup"><span data-stu-id="9f076-111">If a service is suspended, it resumes.</span></span> <span data-ttu-id="9f076-112">S’il est en cours d’exécution, le message est ignoré.</span><span class="sxs-lookup"><span data-stu-id="9f076-112">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="9f076-113">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente les services que vous souhaitez reprendre.</span><span class="sxs-lookup"><span data-stu-id="9f076-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="9f076-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9f076-114">EXAMPLES</span></span>

### <span data-ttu-id="9f076-115">Exemple 1 : reprendre un service sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="9f076-115">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="9f076-116">Cette commande reprend le service de notification d’événements système sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9f076-116">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="9f076-117">Le nom du service est représenté dans la commande par sens.</span><span class="sxs-lookup"><span data-stu-id="9f076-117">The service name is represented in the command by sens.</span></span> <span data-ttu-id="9f076-118">La commande utilise le paramètre **Name** pour spécifier le nom de service du service, mais la commande omet le nom de paramètre, car le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="9f076-118">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="9f076-119">Exemple 2 : reprendre tous les services interrompus</span><span class="sxs-lookup"><span data-stu-id="9f076-119">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="9f076-120">Cette commande reprend tous les services interrompus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9f076-120">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="9f076-121">La `Get-Service` commande d’applet de commande obtient tous les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9f076-121">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="9f076-122">L’opérateur de pipeline ( `|` ) passe les résultats à l' `Where-Object` applet de commande, qui sélectionne les services dont la propriété **Status** a la valeur Paused.</span><span class="sxs-lookup"><span data-stu-id="9f076-122">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="9f076-123">L’opérateur de pipeline suivant envoie les résultats à `Resume-Service` , qui reprend les services suspendus.</span><span class="sxs-lookup"><span data-stu-id="9f076-123">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="9f076-124">Dans la pratique, vous utiliseriez le paramètre **WhatIf** pour déterminer l’effet de la commande avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="9f076-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="9f076-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f076-125">PARAMETERS</span></span>

### <span data-ttu-id="9f076-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="9f076-126">-DisplayName</span></span>

<span data-ttu-id="9f076-127">Spécifie les noms d’affichage des services à reprendre.</span><span class="sxs-lookup"><span data-stu-id="9f076-127">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="9f076-128">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9f076-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9f076-129">-Exclude</span><span class="sxs-lookup"><span data-stu-id="9f076-129">-Exclude</span></span>

<span data-ttu-id="9f076-130">Spécifie les services que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="9f076-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="9f076-131">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="9f076-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="9f076-132">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="9f076-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="9f076-133">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9f076-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9f076-134">-Include</span><span class="sxs-lookup"><span data-stu-id="9f076-134">-Include</span></span>

<span data-ttu-id="9f076-135">Spécifie les services à reprendre.</span><span class="sxs-lookup"><span data-stu-id="9f076-135">Specifies services to resume.</span></span> <span data-ttu-id="9f076-136">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="9f076-136">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="9f076-137">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="9f076-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="9f076-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9f076-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9f076-139">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9f076-139">-InputObject</span></span>

<span data-ttu-id="9f076-140">Spécifie les objets **ServiceController** qui représentent les services à reprendre.</span><span class="sxs-lookup"><span data-stu-id="9f076-140">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="9f076-141">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="9f076-141">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="9f076-142">-Name</span><span class="sxs-lookup"><span data-stu-id="9f076-142">-Name</span></span>

<span data-ttu-id="9f076-143">Spécifie les noms des services à reprendre.</span><span class="sxs-lookup"><span data-stu-id="9f076-143">Specifies the service names of the services to be resumed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9f076-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9f076-144">-PassThru</span></span>

<span data-ttu-id="9f076-145">Retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="9f076-145">Returns an object that represents the service.</span></span> <span data-ttu-id="9f076-146">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="9f076-146">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9f076-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9f076-147">-Confirm</span></span>

<span data-ttu-id="9f076-148">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9f076-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9f076-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9f076-149">-WhatIf</span></span>

<span data-ttu-id="9f076-150">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9f076-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9f076-151">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9f076-151">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9f076-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f076-152">CommonParameters</span></span>

<span data-ttu-id="9f076-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f076-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f076-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9f076-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f076-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9f076-155">INPUTS</span></span>

### <span data-ttu-id="9f076-156">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="9f076-156">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="9f076-157">Vous pouvez diriger un objet de service ou une chaîne qui contient un nom de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9f076-157">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="9f076-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9f076-158">OUTPUTS</span></span>

### <span data-ttu-id="9f076-159">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="9f076-159">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="9f076-160">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service repris, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="9f076-160">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="9f076-161">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="9f076-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9f076-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9f076-162">NOTES</span></span>

<span data-ttu-id="9f076-163">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="9f076-163">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="9f076-164">L’état des services qui ont été interrompus est suspendu.</span><span class="sxs-lookup"><span data-stu-id="9f076-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="9f076-165">Lorsque les services reprennent, leur état est Running.</span><span class="sxs-lookup"><span data-stu-id="9f076-165">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="9f076-166">`Resume-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="9f076-166">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="9f076-167">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="9f076-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="9f076-168">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="9f076-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="9f076-169">Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="9f076-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="9f076-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9f076-170">RELATED LINKS</span></span>

[<span data-ttu-id="9f076-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="9f076-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="9f076-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="9f076-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="9f076-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="9f076-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="9f076-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="9f076-178">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="9f076-178">Remove-Service</span></span>](Remove-Service.md)
