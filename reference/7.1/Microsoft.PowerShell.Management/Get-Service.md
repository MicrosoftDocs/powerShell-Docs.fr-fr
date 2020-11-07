---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 1cbecd37217c4c0113079dfa9ac7008dd0d91823
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342227"
---
# <span data-ttu-id="ca16b-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-103">Get-Service</span></span>

## <span data-ttu-id="ca16b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ca16b-104">SYNOPSIS</span></span>
<span data-ttu-id="ca16b-105">Obtient les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca16b-105">Gets the services on the computer.</span></span>

## <span data-ttu-id="ca16b-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ca16b-106">SYNTAX</span></span>

### <span data-ttu-id="ca16b-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ca16b-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ca16b-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ca16b-108">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ca16b-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="ca16b-109">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="ca16b-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ca16b-110">DESCRIPTION</span></span>

<span data-ttu-id="ca16b-111">L' `Get-Service` applet de commande obtient les objets qui représentent les services sur un ordinateur, y compris les services en cours d’exécution et arrêtés.</span><span class="sxs-lookup"><span data-stu-id="ca16b-111">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="ca16b-112">Par défaut, lorsque `Get-Service` est exécuté sans paramètres, tous les services de l’ordinateur local sont retournés.</span><span class="sxs-lookup"><span data-stu-id="ca16b-112">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="ca16b-113">Vous pouvez demander à cette applet de commande d’obtenir uniquement des services particuliers en spécifiant le nom de service ou le nom d’affichage des services, ou vous pouvez diriger les objets de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ca16b-113">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="ca16b-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ca16b-114">EXAMPLES</span></span>

### <span data-ttu-id="ca16b-115">Exemple 1 : récupération de tous les services sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="ca16b-115">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="ca16b-116">Cet exemple obtient tous les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca16b-116">This example gets all of the services on the computer.</span></span> <span data-ttu-id="ca16b-117">Il se comporte comme si vous aviez tapé `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-117">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="ca16b-118">L’affichage par défaut répertorie l’état, le nom et le nom d’affichage de chaque service.</span><span class="sxs-lookup"><span data-stu-id="ca16b-118">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="ca16b-119">Exemple 2 : obtenir les services qui commencent par une chaîne de recherche</span><span class="sxs-lookup"><span data-stu-id="ca16b-119">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="ca16b-120">Cet exemple récupère les services dont le nom de service commence par WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="ca16b-120">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="ca16b-121">Exemple 3 : afficher les services qui incluent une chaîne de recherche</span><span class="sxs-lookup"><span data-stu-id="ca16b-121">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="ca16b-122">Cet exemple affiche les services dont le nom d’affichage comprend le mot réseau.</span><span class="sxs-lookup"><span data-stu-id="ca16b-122">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="ca16b-123">La recherche du nom complet recherche les services liés au réseau même si le nom du service n’inclut pas net, par exemple xmlprov, le service d’approvisionnement réseau.</span><span class="sxs-lookup"><span data-stu-id="ca16b-123">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="ca16b-124">Exemple 4 : obtenir des services qui commencent par une chaîne de recherche et une exclusion</span><span class="sxs-lookup"><span data-stu-id="ca16b-124">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="ca16b-125">Cet exemple obtient uniquement les services dont les noms de service commencent par **Win** , à l’exception du service WinRM.</span><span class="sxs-lookup"><span data-stu-id="ca16b-125">This example only gets the services with service names that begin with **win** , except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="ca16b-126">Exemple 5 : afficher les services actuellement actifs</span><span class="sxs-lookup"><span data-stu-id="ca16b-126">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="ca16b-127">Cet exemple affiche uniquement les services dont l’État est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ca16b-127">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="ca16b-128">`Get-Service` Obtient tous les services sur l’ordinateur et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ca16b-128">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="ca16b-129">L' `Where-Object` applet de commande sélectionne uniquement les services dont la propriété **Status** est égale à Running.</span><span class="sxs-lookup"><span data-stu-id="ca16b-129">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="ca16b-130">Status n’est qu’une des propriétés des objets Service.</span><span class="sxs-lookup"><span data-stu-id="ca16b-130">Status is only one property of service objects.</span></span> <span data-ttu-id="ca16b-131">Pour afficher toutes les propriétés, tapez `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-131">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="ca16b-132">Exemple 6 : répertorier les services sur l’ordinateur qui ont des services dépendants</span><span class="sxs-lookup"><span data-stu-id="ca16b-132">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="ca16b-133">Cet exemple obtient les services qui ont des services dépendants.</span><span class="sxs-lookup"><span data-stu-id="ca16b-133">This example gets services that have dependent services.</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="ca16b-134">L' `Get-Service` applet de commande obtient tous les services sur l’ordinateur et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ca16b-134">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="ca16b-135">L' `Where-Object` applet de commande sélectionne les services dont la propriété **DependentServices** n’est pas null.</span><span class="sxs-lookup"><span data-stu-id="ca16b-135">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="ca16b-136">Les résultats sont envoyés dans le pipeline à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-136">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="ca16b-137">Le paramètre **Property** affiche le nom du service, le nom des services dépendants et une propriété calculée qui affiche le nombre de services dépendants pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="ca16b-137">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="ca16b-138">Exemple 7 : trier les services par valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="ca16b-138">Example 7: Sort services by property value</span></span>

<span data-ttu-id="ca16b-139">Cet exemple montre que lorsque vous triez des services dans l’ordre croissant en fonction de la valeur de leur propriété **Status** , les services arrêtés s’affichent avant l’exécution des services.</span><span class="sxs-lookup"><span data-stu-id="ca16b-139">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="ca16b-140">La raison est que la valeur de **Status** est une énumération, dans laquelle Stopped a la valeur 1 et l’exécution a une valeur de 4.</span><span class="sxs-lookup"><span data-stu-id="ca16b-140">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="ca16b-141">Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="ca16b-141">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="ca16b-142">Pour répertorier d’abord les services en cours d’exécution, utilisez le paramètre **décroissant** de l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-142">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### <span data-ttu-id="ca16b-143">Exemple 8 : obtenir les services dépendants d’un service</span><span class="sxs-lookup"><span data-stu-id="ca16b-143">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="ca16b-144">Cet exemple obtient les services requis par le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="ca16b-144">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="ca16b-145">La valeur de la propriété **ServicesDependedOn** du service est retournée.</span><span class="sxs-lookup"><span data-stu-id="ca16b-145">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="ca16b-146">Exemple 9 : obtenir un service par le biais de l’opérateur de pipeline</span><span class="sxs-lookup"><span data-stu-id="ca16b-146">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="ca16b-147">Cet exemple obtient le service WinRM sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ca16b-147">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="ca16b-148">La chaîne de nom de service, placée entre guillemets, est envoyée dans le pipeline à `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-148">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="ca16b-149">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="ca16b-149">PARAMETERS</span></span>

### <span data-ttu-id="ca16b-150">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="ca16b-150">-DependentServices</span></span>

<span data-ttu-id="ca16b-151">Indique que cette applet de commande obtient uniquement les services qui dépendent du service spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca16b-151">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ca16b-152">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="ca16b-152">-DisplayName</span></span>

<span data-ttu-id="ca16b-153">Spécifie, sous forme de tableau de chaînes, les noms d’affichage des services à récupérer.</span><span class="sxs-lookup"><span data-stu-id="ca16b-153">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="ca16b-154">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ca16b-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ca16b-155">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ca16b-155">-Exclude</span></span>

<span data-ttu-id="ca16b-156">Spécifie, sous forme de tableau de chaînes, un ou des services que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="ca16b-156">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ca16b-157">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="ca16b-157">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="ca16b-158">Entrez un élément ou un modèle de nom, tel que `s*` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-158">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="ca16b-159">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ca16b-159">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ca16b-160">-Include</span><span class="sxs-lookup"><span data-stu-id="ca16b-160">-Include</span></span>

<span data-ttu-id="ca16b-161">Spécifie, sous la forme d’un tableau de chaînes, un ou des services inclus dans l’opération par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ca16b-161">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="ca16b-162">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="ca16b-162">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="ca16b-163">Entrez un élément ou un modèle de nom, tel que `s*` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-163">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="ca16b-164">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ca16b-164">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ca16b-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ca16b-165">-InputObject</span></span>

<span data-ttu-id="ca16b-166">Spécifie les objets **ServiceController** représentant les services à récupérer.</span><span class="sxs-lookup"><span data-stu-id="ca16b-166">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="ca16b-167">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="ca16b-167">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="ca16b-168">Vous pouvez diriger un objet de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ca16b-168">You can pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ca16b-169">-Name</span><span class="sxs-lookup"><span data-stu-id="ca16b-169">-Name</span></span>

<span data-ttu-id="ca16b-170">Spécifie les noms des services à récupérer.</span><span class="sxs-lookup"><span data-stu-id="ca16b-170">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="ca16b-171">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ca16b-171">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ca16b-172">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="ca16b-172">-RequiredServices</span></span>

<span data-ttu-id="ca16b-173">Indique que cette applet de commande obtient uniquement les services dont ce service a besoin.</span><span class="sxs-lookup"><span data-stu-id="ca16b-173">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="ca16b-174">Ce paramètre obtient la valeur de la propriété **ServicesDependedOn** du service.</span><span class="sxs-lookup"><span data-stu-id="ca16b-174">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ca16b-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ca16b-175">CommonParameters</span></span>

<span data-ttu-id="ca16b-176">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ca16b-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ca16b-177">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ca16b-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ca16b-178">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ca16b-178">INPUTS</span></span>

### <span data-ttu-id="ca16b-179">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="ca16b-179">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="ca16b-180">Vous pouvez diriger un objet de service ou un nom de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ca16b-180">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="ca16b-181">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ca16b-181">OUTPUTS</span></span>

### <span data-ttu-id="ca16b-182">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="ca16b-182">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="ca16b-183">Cette applet de commande retourne des objets qui représentent les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca16b-183">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="ca16b-184">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ca16b-184">NOTES</span></span>

<span data-ttu-id="ca16b-185">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="ca16b-185">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="ca16b-186">À compter de PowerShell 6,0, les propriétés suivantes sont ajoutées aux objets **ServiceController** : **nom d’utilisateur** , **Description** , **DelayedAutoStart** , **BinaryPathName** et **startupType** .</span><span class="sxs-lookup"><span data-stu-id="ca16b-186">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName** , **Description** , **DelayedAutoStart** , **BinaryPathName** , and **StartupType** .</span></span>

<span data-ttu-id="ca16b-187">Vous pouvez également faire référence à `Get-Service` par son alias intégré, `gsv` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-187">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="ca16b-188">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="ca16b-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="ca16b-189">Cette applet de commande peut afficher les services uniquement lorsque l’utilisateur actuel a l’autorisation de les afficher.</span><span class="sxs-lookup"><span data-stu-id="ca16b-189">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="ca16b-190">Si cette applet de commande n’affiche pas de services, vous n’avez peut-être pas l’autorisation de les afficher.</span><span class="sxs-lookup"><span data-stu-id="ca16b-190">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="ca16b-191">Pour rechercher le nom du service et le nom d’affichage de chaque service sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="ca16b-191">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="ca16b-192">Les noms de service s’affichent dans la colonne nom, et les noms d’affichage apparaissent dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="ca16b-192">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="ca16b-193">Lorsque vous triez par ordre croissant selon la valeur de la propriété **Status** , les services arrêtés s’affichent avant l’exécution des services.</span><span class="sxs-lookup"><span data-stu-id="ca16b-193">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="ca16b-194">La propriété **Status** du service est une valeur énumérée et les noms d’État représentent des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="ca16b-194">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="ca16b-195">L’ordre de tri est basé sur la valeur entière, et non sur le nom.</span><span class="sxs-lookup"><span data-stu-id="ca16b-195">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="ca16b-196">L’état arrêté s’affiche avant, car l’exécution de, car Stopped a la valeur 1, et Running a la valeur 4.</span><span class="sxs-lookup"><span data-stu-id="ca16b-196">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="ca16b-197">Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="ca16b-197">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="ca16b-198">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ca16b-198">RELATED LINKS</span></span>

[<span data-ttu-id="ca16b-199">New-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-199">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="ca16b-200">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-200">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="ca16b-201">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-201">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="ca16b-202">Set-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-202">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="ca16b-203">Start-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-203">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="ca16b-204">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-204">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="ca16b-205">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-205">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="ca16b-206">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="ca16b-206">Remove-Service</span></span>](Remove-Service.md)
