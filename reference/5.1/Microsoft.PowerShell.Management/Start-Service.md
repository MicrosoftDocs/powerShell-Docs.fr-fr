---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: a7436e1b32beb968f37944021d7f702bd1f1918c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203485"
---
# <span data-ttu-id="cca5c-103">Start-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-103">Start-Service</span></span>

## <span data-ttu-id="cca5c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cca5c-104">SYNOPSIS</span></span>
<span data-ttu-id="cca5c-105">Démarre un ou plusieurs services arrêtés.</span><span class="sxs-lookup"><span data-stu-id="cca5c-105">Starts one or more stopped services.</span></span>

## <span data-ttu-id="cca5c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cca5c-106">SYNTAX</span></span>

### <span data-ttu-id="cca5c-107">InputObject (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="cca5c-107">InputObject (Default)</span></span>

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cca5c-108">Default</span><span class="sxs-lookup"><span data-stu-id="cca5c-108">Default</span></span>

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cca5c-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cca5c-109">DisplayName</span></span>

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cca5c-110">Description</span><span class="sxs-lookup"><span data-stu-id="cca5c-110">DESCRIPTION</span></span>

<span data-ttu-id="cca5c-111">L' `Start-Service` applet de commande envoie un message de démarrage au contrôleur de services Windows pour chacun des services spécifiés.</span><span class="sxs-lookup"><span data-stu-id="cca5c-111">The `Start-Service` cmdlet sends a start message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="cca5c-112">Si un service est déjà en cours d'exécution, le message est ignoré sans erreur.</span><span class="sxs-lookup"><span data-stu-id="cca5c-112">If a service is already running, the message is ignored without error.</span></span> <span data-ttu-id="cca5c-113">Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour fournir un objet de service qui représente les services que vous souhaitez démarrer.</span><span class="sxs-lookup"><span data-stu-id="cca5c-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to supply a service object that represents the services that you want to start.</span></span>

## <span data-ttu-id="cca5c-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cca5c-114">EXAMPLES</span></span>

### <span data-ttu-id="cca5c-115">Exemple 1 : démarrer un service à l’aide de son nom</span><span class="sxs-lookup"><span data-stu-id="cca5c-115">Example 1: Start a service by using its name</span></span>

<span data-ttu-id="cca5c-116">Cet exemple démarre le service EventLog sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="cca5c-116">This example starts the EventLog service on the local computer.</span></span> <span data-ttu-id="cca5c-117">Le paramètre **Name** identifie le service par son nom de service.</span><span class="sxs-lookup"><span data-stu-id="cca5c-117">The **Name** parameter identifies the service by its service name.</span></span>

```powershell
Start-Service -Name "eventlog"
```

### <span data-ttu-id="cca5c-118">Exemple 2 : afficher des informations sans démarrer un service</span><span class="sxs-lookup"><span data-stu-id="cca5c-118">Example 2: Display information without starting a service</span></span>

<span data-ttu-id="cca5c-119">Cet exemple montre ce qui se produit si vous avez démarré les services dont le nom d’affichage comprend « Remote ».</span><span class="sxs-lookup"><span data-stu-id="cca5c-119">This example shows what would occur if you started the services that have a display name that includes "remote".</span></span>

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

<span data-ttu-id="cca5c-120">Le paramètre **DisplayName** identifie les services par leur nom d’affichage au lieu de leur nom de service.</span><span class="sxs-lookup"><span data-stu-id="cca5c-120">The **DisplayName** parameter identifies the services by their display name instead of their service name.</span></span> <span data-ttu-id="cca5c-121">Le paramètre **WhatIf** permet à l’applet de commande d’afficher ce qui se passerait lorsque vous exécuterez la commande sans apporter de modifications.</span><span class="sxs-lookup"><span data-stu-id="cca5c-121">The **WhatIf** parameter causes the cmdlet to display what would happen when you run the command but does not make changes.</span></span>

### <span data-ttu-id="cca5c-122">Exemple 3 : démarrer un service et enregistrer l’action dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="cca5c-122">Example 3: Start a service and record the action in a text file</span></span>

<span data-ttu-id="cca5c-123">Cet exemple démarre le service Windows Management Instrumentation (WMI) sur l’ordinateur et ajoute un enregistrement de l’action au fichier services.txt.</span><span class="sxs-lookup"><span data-stu-id="cca5c-123">This example starts the Windows Management Instrumentation (WMI) service on the computer and adds a record of the action to the services.txt file.</span></span>

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

<span data-ttu-id="cca5c-124">Tout d’abord, nous utilisons `Get-Service` pour récupérer un objet qui représente le service WMI et le stocker dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="cca5c-124">First we use `Get-Service` to get an object that represent the WMI service and store it in the `$s` variable.</span></span> <span data-ttu-id="cca5c-125">Ensuite, nous démarrons le service.</span><span class="sxs-lookup"><span data-stu-id="cca5c-125">Next, we start the service.</span></span> <span data-ttu-id="cca5c-126">Sans le paramètre **PassThru** , `Start-Service` ne crée aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="cca5c-126">Without the **PassThru** parameter, `Start-Service` does not create any output.</span></span> <span data-ttu-id="cca5c-127">L’opérateur de pipeline (|) passe la sortie de l’objet à `Start-Service` l’applet de commande `Format-List` pour mettre en forme l’objet sous la forme d’une liste de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="cca5c-127">The pipeline operator (|) passes the object output by `Start-Service` to the `Format-List` cmdlet to format the object as a list of its properties.</span></span> <span data-ttu-id="cca5c-128">L’opérateur de redirection d’ajout ( \> \> ) redirige la sortie vers le fichier services.txt.</span><span class="sxs-lookup"><span data-stu-id="cca5c-128">The append redirection operator (\>\>) redirects the output to the services.txt file.</span></span> <span data-ttu-id="cca5c-129">La sortie est ajoutée à la fin du fichier existant.</span><span class="sxs-lookup"><span data-stu-id="cca5c-129">The output is added to the end of the existing file.</span></span>

### <span data-ttu-id="cca5c-130">Exemple 4 : démarrer un service désactivé</span><span class="sxs-lookup"><span data-stu-id="cca5c-130">Example 4: Start a disabled service</span></span>

<span data-ttu-id="cca5c-131">Cet exemple montre comment démarrer un service lorsque le type de démarrage du service est **désactivé** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-131">This example shows how to start a service when the start type of the service is **Disabled** .</span></span>

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

<span data-ttu-id="cca5c-132">La première tentative de démarrage du service Telnet (tlntsvr) échoue.</span><span class="sxs-lookup"><span data-stu-id="cca5c-132">The first attempt to start the Telnet service (tlntsvr) fails.</span></span> <span data-ttu-id="cca5c-133">La `Get-CimInstance` commande indique que la propriété **startMode** du service tlntsvr est **désactivée** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-133">The `Get-CimInstance` command shows that the **StartMode** property of the Tlntsvr service is **Disabled** .</span></span> <span data-ttu-id="cca5c-134">L' `Set-Service` applet de commande change le type de démarrage en **Manuel** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-134">The `Set-Service` cmdlet changes the start type to **Manual** .</span></span> <span data-ttu-id="cca5c-135">Nous pouvons à présent soumettre à nouveau la `Start-Service` commande.</span><span class="sxs-lookup"><span data-stu-id="cca5c-135">Now, we can resubmit the `Start-Service` command.</span></span> <span data-ttu-id="cca5c-136">Cette fois, elle réussit.</span><span class="sxs-lookup"><span data-stu-id="cca5c-136">This time, the command succeeds.</span></span> <span data-ttu-id="cca5c-137">Pour vérifier que la commande a réussi, exécutez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="cca5c-137">To verify that the command succeeded, run `Get-Service`.</span></span>

## <span data-ttu-id="cca5c-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cca5c-138">PARAMETERS</span></span>

### <span data-ttu-id="cca5c-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="cca5c-139">-DisplayName</span></span>

<span data-ttu-id="cca5c-140">Spécifie les noms d’affichage des services à démarrer.</span><span class="sxs-lookup"><span data-stu-id="cca5c-140">Specifies the display names of the services to start.</span></span> <span data-ttu-id="cca5c-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cca5c-141">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="cca5c-142">-Exclude</span><span class="sxs-lookup"><span data-stu-id="cca5c-142">-Exclude</span></span>

<span data-ttu-id="cca5c-143">Spécifie les services que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="cca5c-143">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="cca5c-144">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-144">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="cca5c-145">Entrez un élément ou un modèle de nom, tel que `s*` .</span><span class="sxs-lookup"><span data-stu-id="cca5c-145">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="cca5c-146">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cca5c-146">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="cca5c-147">-Include</span><span class="sxs-lookup"><span data-stu-id="cca5c-147">-Include</span></span>

<span data-ttu-id="cca5c-148">Spécifie les services que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="cca5c-148">Specifies services that this cmdlet starts.</span></span> <span data-ttu-id="cca5c-149">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-149">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="cca5c-150">Entrez un élément ou un modèle de nom, tel que `s*` .</span><span class="sxs-lookup"><span data-stu-id="cca5c-150">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="cca5c-151">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cca5c-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="cca5c-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cca5c-152">-InputObject</span></span>

<span data-ttu-id="cca5c-153">Spécifie les objets **ServiceController** représentant les services à démarrer.</span><span class="sxs-lookup"><span data-stu-id="cca5c-153">Specifies **ServiceController** objects representing the services to be started.</span></span> <span data-ttu-id="cca5c-154">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="cca5c-154">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="cca5c-155">-Name</span><span class="sxs-lookup"><span data-stu-id="cca5c-155">-Name</span></span>

<span data-ttu-id="cca5c-156">Spécifie le nom de service du service à démarrer.</span><span class="sxs-lookup"><span data-stu-id="cca5c-156">Specifies the service names for the service to be started.</span></span>

<span data-ttu-id="cca5c-157">Le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="cca5c-157">The parameter name is optional.</span></span> <span data-ttu-id="cca5c-158">Vous pouvez utiliser **Name** ou son alias, **ServiceName** ou omettre le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="cca5c-158">You can use **Name** or its alias, **ServiceName** , or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="cca5c-159">-PassThru</span><span class="sxs-lookup"><span data-stu-id="cca5c-159">-PassThru</span></span>

<span data-ttu-id="cca5c-160">Retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="cca5c-160">Returns an object that represents the service.</span></span> <span data-ttu-id="cca5c-161">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="cca5c-161">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="cca5c-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cca5c-162">-Confirm</span></span>

<span data-ttu-id="cca5c-163">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cca5c-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cca5c-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cca5c-164">-WhatIf</span></span>

<span data-ttu-id="cca5c-165">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cca5c-165">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cca5c-166">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="cca5c-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cca5c-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cca5c-167">CommonParameters</span></span>

<span data-ttu-id="cca5c-168">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cca5c-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cca5c-169">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cca5c-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cca5c-170">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cca5c-170">INPUTS</span></span>

### <span data-ttu-id="cca5c-171">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="cca5c-171">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="cca5c-172">Vous pouvez diriger les objets qui représentent les services ou les chaînes qui contiennent les noms de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cca5c-172">You can pipe objects that represent the services or strings that contain the service names to this cmdlet.</span></span>

## <span data-ttu-id="cca5c-173">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cca5c-173">OUTPUTS</span></span>

### <span data-ttu-id="cca5c-174">Aucun, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="cca5c-174">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="cca5c-175">Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous spécifiez **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-175">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify **PassThru** .</span></span> <span data-ttu-id="cca5c-176">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="cca5c-176">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cca5c-177">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cca5c-177">NOTES</span></span>

* <span data-ttu-id="cca5c-178">Vous pouvez également faire référence à `Start-Service` par son alias intégré, `sasv` .</span><span class="sxs-lookup"><span data-stu-id="cca5c-178">You can also refer to `Start-Service` by its built-in alias, `sasv`.</span></span> <span data-ttu-id="cca5c-179">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="cca5c-179">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
* <span data-ttu-id="cca5c-180">`Start-Service` peut contrôler les services uniquement si l’utilisateur actuel est autorisé à le faire.</span><span class="sxs-lookup"><span data-stu-id="cca5c-180">`Start-Service` can control services only if the current user has permission to do this.</span></span> <span data-ttu-id="cca5c-181">Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="cca5c-181">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="cca5c-182">Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="cca5c-182">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="cca5c-183">Les noms de service s’affichent dans la colonne **nom** , et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="cca5c-183">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>
* <span data-ttu-id="cca5c-184">Vous pouvez uniquement démarrer les services dont le type de démarrage est manuel, automatique ou automatique (début différé).</span><span class="sxs-lookup"><span data-stu-id="cca5c-184">You can start only the services that have a start type of Manual, Automatic, or Automatic (Delayed Start).</span></span> <span data-ttu-id="cca5c-185">Vous ne pouvez pas démarrer les services dont le type de démarrage est désactivé.</span><span class="sxs-lookup"><span data-stu-id="cca5c-185">You cannot start the services that have a start type of Disabled.</span></span> <span data-ttu-id="cca5c-186">Si une `Start-Service` commande échoue avec le message `Cannot start service \<service-name\> on computer` , utilisez `Get-CimInstance` pour rechercher le type de démarrage du service et, si nécessaire, utilisez la `Set-Service` cmdlet pour modifier le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="cca5c-186">If a `Start-Service` command fails with the message `Cannot start service \<service-name\> on computer`, use `Get-CimInstance` to find the start type of the service and, if you have to, use the `Set-Service` cmdlet to change the start type of the service.</span></span>
* <span data-ttu-id="cca5c-187">Certains services, tels le service Journaux et alertes de performance (Sysmonlog), s'arrêtent automatiquement lorsqu'ils n'ont aucune tâche à exécuter.</span><span class="sxs-lookup"><span data-stu-id="cca5c-187">Some services, such as Performance Logs and Alerts (SysmonLog) stop automatically if they have no work to do.</span></span> <span data-ttu-id="cca5c-188">Lorsque PowerShell démarre un service qui s’arrête presque immédiatement, il affiche le message suivant : `Service \<display-name\> start failed.`</span><span class="sxs-lookup"><span data-stu-id="cca5c-188">When PowerShell starts a service that stops itself almost immediately, it displays the following message: `Service \<display-name\> start failed.`</span></span>

## <span data-ttu-id="cca5c-189">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cca5c-189">RELATED LINKS</span></span>

[<span data-ttu-id="cca5c-190">Get-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-190">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="cca5c-191">New-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-191">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="cca5c-192">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-192">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="cca5c-193">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-193">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="cca5c-194">Set-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-194">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="cca5c-195">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-195">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="cca5c-196">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="cca5c-196">Suspend-Service</span></span>](Suspend-Service.md)
