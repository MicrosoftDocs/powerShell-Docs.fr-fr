---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203494"
---
# <span data-ttu-id="3ad5b-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-103">Set-Service</span></span>

## <span data-ttu-id="3ad5b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3ad5b-104">SYNOPSIS</span></span>
<span data-ttu-id="3ad5b-105">Démarre, arrête et interrompt un service, puis modifie ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="3ad5b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ad5b-106">SYNTAX</span></span>

### <span data-ttu-id="3ad5b-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3ad5b-107">Name (Default)</span></span>

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3ad5b-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="3ad5b-108">InputObject</span></span>

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3ad5b-109">Description</span><span class="sxs-lookup"><span data-stu-id="3ad5b-109">DESCRIPTION</span></span>

<span data-ttu-id="3ad5b-110">L' `Set-Service` applet de commande modifie les propriétés d’un service, telles que l' **État** , la **Description** , **DisplayName** et **startupType** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType** .</span></span> <span data-ttu-id="3ad5b-111">`Set-Service` permet de démarrer, d’arrêter, de suspendre ou de suspendre un service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="3ad5b-112">Pour identifier un service, entrez son nom de service ou envoyez un objet de service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="3ad5b-113">Ou, envoyez un nom de service ou un objet de service dans le pipeline à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="3ad5b-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3ad5b-114">EXAMPLES</span></span>

### <span data-ttu-id="3ad5b-115">Exemple 1 : modifier un nom complet</span><span class="sxs-lookup"><span data-stu-id="3ad5b-115">Example 1: Change a display name</span></span>

<span data-ttu-id="3ad5b-116">Dans cet exemple, le nom complet d’un service est modifié.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="3ad5b-117">Pour afficher le nom d’affichage d’origine, utilisez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="3ad5b-118">`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **LanmanWorkstation** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation** .</span></span> <span data-ttu-id="3ad5b-119">Le paramètre **DisplayName** spécifie le nouveau nom complet, la **station de travail LanMan** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation** .</span></span>

### <span data-ttu-id="3ad5b-120">Exemple 2 : modifier le type de démarrage des services</span><span class="sxs-lookup"><span data-stu-id="3ad5b-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="3ad5b-121">Cet exemple montre comment modifier le type de démarrage d’un service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="3ad5b-122">`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **bits** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS** .</span></span> <span data-ttu-id="3ad5b-123">Le paramètre **startupType** définit le service sur **Automatic** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-123">The **StartupType** parameter sets the service to **Automatic** .</span></span>

<span data-ttu-id="3ad5b-124">`Get-Service` utilise le paramètre **Name** pour spécifier le service **bits** et envoie l’objet vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="3ad5b-125">`Select-Object` utilise le paramètre **Property** pour afficher l’état du service **bits** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="3ad5b-126">Exemple 3 : modifier la description d’un service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="3ad5b-127">Cet exemple modifie la description du service BITS et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="3ad5b-128">L' `Get-CimInstance` applet de commande est utilisée car elle retourne un objet **Win32_Service** qui comprend la **Description** du service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description** .</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="3ad5b-129">`Get-CimInstance` envoie l’objet dans le pipeline à `Format-List` et affiche le nom et la description du service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="3ad5b-130">À des fins de comparaison, la commande est exécutée avant et après la mise à jour de la description.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="3ad5b-131">`Set-Service` utilise le paramètre **Name** pour spécifier le service **bits** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="3ad5b-132">Le paramètre **Description** spécifie le texte mis à jour pour la description des services.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="3ad5b-133">Exemple 4 : démarrer un service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-133">Example 4: Start a service</span></span>

<span data-ttu-id="3ad5b-134">Dans cet exemple, un service est démarré.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="3ad5b-135">`Set-Service` utilise le paramètre **Name** pour spécifier le service, **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM** .</span></span> <span data-ttu-id="3ad5b-136">Le paramètre **Status** utilise la valeur **en cours d’exécution** pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="3ad5b-137">Le paramètre **PassThru** génère un objet **ServiceController** qui affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="3ad5b-138">Exemple 5 : suspendre un service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="3ad5b-139">Cet exemple utilise le pipeline pour suspendre le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="3ad5b-140">`Get-Service` utilise le paramètre **Name** pour spécifier le service de **planification** et envoie l’objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="3ad5b-141">`Set-Service` utilise le paramètre **Status** pour définir le service comme étant **suspendu** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-141">`Set-Service` uses the **Status** parameter to set the service to **Paused** .</span></span>

### <span data-ttu-id="3ad5b-142">Exemple 6 : arrêter un service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-142">Example 6: Stop a service</span></span>

<span data-ttu-id="3ad5b-143">Cet exemple utilise une variable pour arrêter un service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="3ad5b-144">`Get-Service` utilise le paramètre **Name** pour spécifier le service, **Schedule** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule** .</span></span> <span data-ttu-id="3ad5b-145">L’objet est stocké dans la variable, `$S` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="3ad5b-146">`Set-Service` utilise le paramètre **InputObject** et spécifie l’objet stocké `$S` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="3ad5b-147">Le paramètre **Status** définit le service sur **Stopped** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-147">The **Status** parameter sets the service to **Stopped** .</span></span>

## <span data-ttu-id="3ad5b-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3ad5b-148">PARAMETERS</span></span>

### <span data-ttu-id="3ad5b-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3ad5b-149">-ComputerName</span></span>

<span data-ttu-id="3ad5b-150">Spécifie un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-150">Specifies one or more computers.</span></span> <span data-ttu-id="3ad5b-151">Pour les ordinateurs distants, tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-151">For remote computers, type the NetBIOS name, an IP address, or a fully qualified domain name.</span></span> <span data-ttu-id="3ad5b-152">Si le paramètre **ComputerName** n’est pas spécifié, la commande s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-152">If the **ComputerName** parameter isn't specified, the command runs on the local computer.</span></span>

<span data-ttu-id="3ad5b-153">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-153">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="3ad5b-154">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-154">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3ad5b-155">-Confirm</span></span>

<span data-ttu-id="3ad5b-156">Vous invite à confirmer l’exécution `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-156">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="3ad5b-157">Description</span><span class="sxs-lookup"><span data-stu-id="3ad5b-157">-Description</span></span>

<span data-ttu-id="3ad5b-158">Spécifie une nouvelle description pour le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-158">Specifies a new description for the service.</span></span>

<span data-ttu-id="3ad5b-159">La description du service s’affiche dans gestion de l' **ordinateur, services** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-159">The service description appears in **Computer Management, Services** .</span></span> <span data-ttu-id="3ad5b-160">La **Description** n’est pas une propriété de l' `Get-Service` objet **ServiceController** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-160">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="3ad5b-161">Pour afficher la description du service, utilisez `Get-CimInstance` qui retourne un objet **Win32_Service** qui représente le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-161">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-162">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="3ad5b-162">-DisplayName</span></span>

<span data-ttu-id="3ad5b-163">Spécifie le nouveau nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-163">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-164">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3ad5b-164">-InputObject</span></span>

<span data-ttu-id="3ad5b-165">Spécifie un objet **ServiceController** qui représente le service à modifier.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-165">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="3ad5b-166">Entrez une variable qui contient l’objet ou tapez une commande ou une expression qui obtient l’objet, par exemple une `Get-Service` commande.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-166">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="3ad5b-167">Vous pouvez utiliser le pipeline pour envoyer un objet de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-167">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-168">-Name</span><span class="sxs-lookup"><span data-stu-id="3ad5b-168">-Name</span></span>

<span data-ttu-id="3ad5b-169">Spécifie le nom du service à modifier.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-169">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="3ad5b-170">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-170">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="3ad5b-171">Vous pouvez utiliser le pipeline pour envoyer un nom de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-171">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-172">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3ad5b-172">-PassThru</span></span>

<span data-ttu-id="3ad5b-173">Retourne un objet **ServiceController** qui représente les services qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-173">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="3ad5b-174">Par défaut, `Set-Service` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-174">By default, `Set-Service` doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-175">-StartupType</span><span class="sxs-lookup"><span data-stu-id="3ad5b-175">-StartupType</span></span>

<span data-ttu-id="3ad5b-176">Définit le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-176">Sets the startup type of the service.</span></span> <span data-ttu-id="3ad5b-177">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="3ad5b-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3ad5b-178">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-178">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="3ad5b-179">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-179">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="3ad5b-180">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-180">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="3ad5b-181">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-181">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="3ad5b-182">**Démarrage** -indique que le service est un pilote de périphérique Démarré par le chargeur du système.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-182">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="3ad5b-183">Cette valeur est valide uniquement pour les pilotes de périphérique.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-183">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="3ad5b-184">**Système** : indique que le service est un pilote de périphérique Démarré par la fonction « IOInitSystem () ».</span><span class="sxs-lookup"><span data-stu-id="3ad5b-184">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="3ad5b-185">Cette valeur est valide uniquement pour les pilotes de périphérique.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-185">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="3ad5b-186">La valeur par défaut est **automatique** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-186">The default value is **Automatic** .</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-187">-État</span><span class="sxs-lookup"><span data-stu-id="3ad5b-187">-Status</span></span>

<span data-ttu-id="3ad5b-188">Spécifie l’état du service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-188">Specifies the status for the service.</span></span>

<span data-ttu-id="3ad5b-189">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ad5b-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3ad5b-190">**Suspendu** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-190">**Paused** .</span></span> <span data-ttu-id="3ad5b-191">suspend le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-191">Suspends the service.</span></span>
- <span data-ttu-id="3ad5b-192">**Exécution en cours** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-192">**Running** .</span></span> <span data-ttu-id="3ad5b-193">démarre le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-193">Starts the service.</span></span>
- <span data-ttu-id="3ad5b-194">**Arrêté** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-194">**Stopped** .</span></span> <span data-ttu-id="3ad5b-195">arrête le service.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-195">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ad5b-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3ad5b-196">-WhatIf</span></span>

<span data-ttu-id="3ad5b-197">Montre ce qui se passe si `Set-Service` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-197">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="3ad5b-198">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-198">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="3ad5b-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ad5b-199">CommonParameters</span></span>

<span data-ttu-id="3ad5b-200">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ad5b-201">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3ad5b-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ad5b-202">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3ad5b-202">INPUTS</span></span>

### <span data-ttu-id="3ad5b-203">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="3ad5b-203">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="3ad5b-204">Vous pouvez utiliser le pipeline pour envoyer un objet de service ou une chaîne qui contient un nom de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-204">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="3ad5b-205">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3ad5b-205">OUTPUTS</span></span>

### <span data-ttu-id="3ad5b-206">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="3ad5b-206">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="3ad5b-207">Par défaut, `Set-Service` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-207">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="3ad5b-208">Utilisez le paramètre **PassThru** pour générer un objet **ServiceController** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-208">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="3ad5b-209">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3ad5b-209">NOTES</span></span>

<span data-ttu-id="3ad5b-210">`Set-Service` requiert des autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-210">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="3ad5b-211">Utilisez l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-211">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="3ad5b-212">`Set-Service` ne peut contrôler des services que si l’utilisateur actuel dispose des autorisations nécessaires pour gérer les services.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-212">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="3ad5b-213">Si une commande ne fonctionne pas correctement, vous ne disposez peut-être pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="3ad5b-213">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="3ad5b-214">Pour rechercher le nom de service ou le nom d’affichage d’un service, utilisez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-214">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="3ad5b-215">Les noms de service figurent dans la colonne **nom** et les noms complets sont dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="3ad5b-215">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="3ad5b-216">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3ad5b-216">RELATED LINKS</span></span>

[<span data-ttu-id="3ad5b-217">Get-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-217">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="3ad5b-218">New-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-218">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="3ad5b-219">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-219">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="3ad5b-220">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-220">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="3ad5b-221">Start-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-221">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="3ad5b-222">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-222">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="3ad5b-223">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="3ad5b-223">Suspend-Service</span></span>](Suspend-Service.md)
