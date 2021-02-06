---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: f88e07e36ec7c6adf7f24e2c6e57ae5864eb1a60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596319"
---
# <span data-ttu-id="d784c-102">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-102">Restart-Service</span></span>

## <span data-ttu-id="d784c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d784c-103">SYNOPSIS</span></span>
<span data-ttu-id="d784c-104">Arrête, puis démarre un ou plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="d784c-104">Stops and then starts one or more services.</span></span>

## <span data-ttu-id="d784c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d784c-105">SYNTAX</span></span>

### <span data-ttu-id="d784c-106">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="d784c-106">InputObject (Default)</span></span>

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d784c-107">Default</span><span class="sxs-lookup"><span data-stu-id="d784c-107">Default</span></span>

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d784c-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d784c-108">DisplayName</span></span>

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d784c-109">Description</span><span class="sxs-lookup"><span data-stu-id="d784c-109">DESCRIPTION</span></span>

<span data-ttu-id="d784c-110">L' `Restart-Service` applet de commande envoie un message d’arrêt, puis un message de démarrage au contrôleur de services Windows pour un service spécifié.</span><span class="sxs-lookup"><span data-stu-id="d784c-110">The `Restart-Service` cmdlet sends a stop message and then a start message to the Windows Service Controller for a specified service.</span></span> <span data-ttu-id="d784c-111">Si un service est déjà arrêté, il est démarré sans notification d'erreur.</span><span class="sxs-lookup"><span data-stu-id="d784c-111">If a service was already stopped, it is started without notifying you of an error.</span></span> <span data-ttu-id="d784c-112">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet qui représente chaque service que vous souhaitez redémarrer.</span><span class="sxs-lookup"><span data-stu-id="d784c-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass an object that represents each service that you want to restart.</span></span>

## <span data-ttu-id="d784c-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d784c-113">EXAMPLES</span></span>

### <span data-ttu-id="d784c-114">Exemple 1 : redémarrer un service sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="d784c-114">Example 1: Restart a service on the local computer</span></span>

```powershell
PS C:\> Restart-Service -Name winmgmt
```

<span data-ttu-id="d784c-115">Cette commande redémarre le service WMI (Windows Management Instrumentation) WinMgmt sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d784c-115">This command restarts the Windows Management Instrumentation service (WinMgmt) on the local computer.</span></span>

### <span data-ttu-id="d784c-116">Exemple 2 : exclure un service</span><span class="sxs-lookup"><span data-stu-id="d784c-116">Example 2: Exclude a service</span></span>

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

<span data-ttu-id="d784c-117">Cette commande redémarre les services dont le nom d’affichage commence par net, à l’exception du service d’ouverture de session réseau.</span><span class="sxs-lookup"><span data-stu-id="d784c-117">This command restarts the services that have a display name that starts with Net, except for the Net Logon service.</span></span>

### <span data-ttu-id="d784c-118">Exemple 3 : démarrer tous les services réseau arrêtés</span><span class="sxs-lookup"><span data-stu-id="d784c-118">Example 3: Start all stopped network services</span></span>

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

<span data-ttu-id="d784c-119">Cette commande démarre tous les services réseau arrêtés sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d784c-119">This command starts all of the stopped network services on the computer.</span></span>

<span data-ttu-id="d784c-120">Cette commande utilise la `Get-Service` cmdlet pour récupérer des objets qui représentent les services dont le nom de service commence par net.</span><span class="sxs-lookup"><span data-stu-id="d784c-120">This command uses the `Get-Service` cmdlet to get objects that represent the services whose service name starts with net.</span></span> <span data-ttu-id="d784c-121">L’opérateur de pipeline ( `|` ) envoie l’objet de services à l’applet de commande `Where-Object` , qui sélectionne uniquement les services dont l’État est arrêté.</span><span class="sxs-lookup"><span data-stu-id="d784c-121">The pipeline operator (`|`) sends the services object to the `Where-Object` cmdlet, which selects only the services that have a status of stopped.</span></span> <span data-ttu-id="d784c-122">Un autre opérateur de pipeline envoie les services sélectionnés à `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="d784c-122">Another pipeline operator sends the selected services to `Restart-Service`.</span></span>

<span data-ttu-id="d784c-123">Dans la pratique, vous utiliseriez le paramètre **WhatIf** pour déterminer l’effet de la commande avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d784c-123">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="d784c-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d784c-124">PARAMETERS</span></span>

### <span data-ttu-id="d784c-125">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="d784c-125">-DisplayName</span></span>

<span data-ttu-id="d784c-126">Spécifie les noms d’affichage des services à redémarrer.</span><span class="sxs-lookup"><span data-stu-id="d784c-126">Specifies the display names of services to restarted.</span></span> <span data-ttu-id="d784c-127">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d784c-127">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d784c-128">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d784c-128">-Exclude</span></span>

<span data-ttu-id="d784c-129">Spécifie les services que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="d784c-129">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="d784c-130">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="d784c-130">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="d784c-131">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="d784c-131">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="d784c-132">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d784c-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d784c-133">-Force</span><span class="sxs-lookup"><span data-stu-id="d784c-133">-Force</span></span>

<span data-ttu-id="d784c-134">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d784c-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d784c-135">-Include</span><span class="sxs-lookup"><span data-stu-id="d784c-135">-Include</span></span>

<span data-ttu-id="d784c-136">Spécifie les services redémarrés par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d784c-136">Specifies services that this cmdlet restarts.</span></span> <span data-ttu-id="d784c-137">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="d784c-137">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="d784c-138">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="d784c-138">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="d784c-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d784c-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d784c-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d784c-140">-InputObject</span></span>

<span data-ttu-id="d784c-141">Spécifie les objets **ServiceController** qui représentent les services à redémarrer.</span><span class="sxs-lookup"><span data-stu-id="d784c-141">Specifies **ServiceController** objects that represent the services to restart.</span></span> <span data-ttu-id="d784c-142">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="d784c-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="d784c-143">-Name</span><span class="sxs-lookup"><span data-stu-id="d784c-143">-Name</span></span>

<span data-ttu-id="d784c-144">Spécifie les noms des services à redémarrer.</span><span class="sxs-lookup"><span data-stu-id="d784c-144">Specifies the service names of the services to restart.</span></span>

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

### <span data-ttu-id="d784c-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d784c-145">-PassThru</span></span>

<span data-ttu-id="d784c-146">Retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="d784c-146">Returns an object that represents the service.</span></span> <span data-ttu-id="d784c-147">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="d784c-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d784c-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d784c-148">-Confirm</span></span>

<span data-ttu-id="d784c-149">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d784c-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d784c-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d784c-150">-WhatIf</span></span>

<span data-ttu-id="d784c-151">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d784c-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d784c-152">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d784c-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d784c-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d784c-153">CommonParameters</span></span>

<span data-ttu-id="d784c-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d784c-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d784c-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d784c-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d784c-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d784c-156">INPUTS</span></span>

### <span data-ttu-id="d784c-157">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="d784c-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="d784c-158">Vous pouvez diriger un objet de service ou une chaîne qui contient un nom de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d784c-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="d784c-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d784c-159">OUTPUTS</span></span>

### <span data-ttu-id="d784c-160">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="d784c-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="d784c-161">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service redémarré, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="d784c-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the restarted service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="d784c-162">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d784c-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d784c-163">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d784c-163">NOTES</span></span>

<span data-ttu-id="d784c-164">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="d784c-164">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="d784c-165">`Restart-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="d784c-165">`Restart-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="d784c-166">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="d784c-166">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="d784c-167">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` «».</span><span class="sxs-lookup"><span data-stu-id="d784c-167">To find the service names and display names of the services on your system, type `Get-Service`".</span></span>
  <span data-ttu-id="d784c-168">Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="d784c-168">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="d784c-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d784c-169">RELATED LINKS</span></span>

[<span data-ttu-id="d784c-170">Get-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-170">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="d784c-171">New-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-171">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="d784c-172">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-172">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="d784c-173">Set-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-173">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="d784c-174">Start-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-174">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="d784c-175">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-175">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="d784c-176">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-176">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="d784c-177">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="d784c-177">Remove-Service</span></span>](Remove-Service.md)
