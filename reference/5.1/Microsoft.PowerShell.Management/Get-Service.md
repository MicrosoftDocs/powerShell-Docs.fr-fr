---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203989"
---
# <span data-ttu-id="35960-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="35960-103">Get-Service</span></span>

## <span data-ttu-id="35960-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="35960-104">SYNOPSIS</span></span>
<span data-ttu-id="35960-105">Obtient les services présents sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="35960-105">Gets the services on a local or remote computer.</span></span>

## <span data-ttu-id="35960-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35960-106">SYNTAX</span></span>

### <span data-ttu-id="35960-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="35960-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="35960-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="35960-108">DisplayName</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="35960-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="35960-109">InputObject</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="35960-110">Description</span><span class="sxs-lookup"><span data-stu-id="35960-110">DESCRIPTION</span></span>

<span data-ttu-id="35960-111">L’applet de commande **obtenir-service** obtient les objets qui représentent les services sur un ordinateur local ou sur un ordinateur distant, y compris les services en cours d’exécution et arrêtés.</span><span class="sxs-lookup"><span data-stu-id="35960-111">The **Get-Service** cmdlet gets objects that represent the services on a local computer or on a remote computer, including running and stopped services.</span></span>

<span data-ttu-id="35960-112">Vous pouvez demander à cette applet de commande d’obtenir uniquement des services particuliers en spécifiant le nom de service ou le nom d’affichage des services, ou vous pouvez diriger les objets de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35960-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="35960-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="35960-113">EXAMPLES</span></span>

### <span data-ttu-id="35960-114">Exemple 1 : récupération de tous les services sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="35960-114">Example 1: Get all services on the computer</span></span>

```powershell
Get-Service
```

<span data-ttu-id="35960-115">Cette commande obtient tous les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35960-115">This command gets all of the services on the computer.</span></span>
<span data-ttu-id="35960-116">Il se comporte comme si vous aviez tapé `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="35960-116">It behaves as though you typed `Get-Service *`.</span></span>
<span data-ttu-id="35960-117">L’affichage par défaut répertorie l’état, le nom et le nom d’affichage de chaque service.</span><span class="sxs-lookup"><span data-stu-id="35960-117">The default display shows the status, service name, and display name of each service.</span></span>

### <span data-ttu-id="35960-118">Exemple 2 : obtenir les services qui commencent par une chaîne de recherche</span><span class="sxs-lookup"><span data-stu-id="35960-118">Example 2: Get services that begin with a search string</span></span>

```powershell
Get-Service "wmi*"
```

<span data-ttu-id="35960-119">Cette commande récupère des services dont le nom de service commence par WMI (l’acronyme de Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="35960-119">This command retrieves services with service names that begin with WMI (the acronym for Windows Management Instrumentation).</span></span>

### <span data-ttu-id="35960-120">Exemple 3 : afficher les services qui incluent une chaîne de recherche</span><span class="sxs-lookup"><span data-stu-id="35960-120">Example 3: Display services that include a search string</span></span>

```powershell
Get-Service -Displayname "*network*"
```

<span data-ttu-id="35960-121">Cette commande affiche les services dont le nom d’affichage comprend le mot réseau.</span><span class="sxs-lookup"><span data-stu-id="35960-121">This command displays services with a display name that includes the word network.</span></span>
<span data-ttu-id="35960-122">La recherche du nom d’affichage permet de rechercher des services associés au réseau, y compris lorsque leur nom n’inclut pas le mot « Net » (xmlprov, le service d’approvisionnement réseau, par exemple).</span><span class="sxs-lookup"><span data-stu-id="35960-122">Searching the display name finds network-related services even when the service name does not include "Net", such as xmlprov, the Network Provisioning Service.</span></span>

### <span data-ttu-id="35960-123">Exemple 4 : obtenir des services qui commencent par une chaîne de recherche et une exclusion</span><span class="sxs-lookup"><span data-stu-id="35960-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

<span data-ttu-id="35960-124">Ces commandes obtiennent uniquement les services dont les noms de service commencent par Win, à l’exception du service WinRM.</span><span class="sxs-lookup"><span data-stu-id="35960-124">These commands get only the services with service names that begin with win, except for the WinRM service.</span></span>

### <span data-ttu-id="35960-125">Exemple 5 : afficher les services actuellement actifs</span><span class="sxs-lookup"><span data-stu-id="35960-125">Example 5: Display services that are currently active</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="35960-126">Cette commande affiche uniquement les services qui sont actuellement actifs.</span><span class="sxs-lookup"><span data-stu-id="35960-126">This command displays only the services that are currently active.</span></span>
<span data-ttu-id="35960-127">Elle utilise l’applet de commande **obten-service** pour récupérer tous les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35960-127">It uses the **Get-Service** cmdlet to get all of the services on the computer.</span></span>
<span data-ttu-id="35960-128">L’opérateur de pipeline (|) passe les résultats à l’applet de commande Where-Object, qui sélectionne uniquement les services dont la propriété Status est égale à Running.</span><span class="sxs-lookup"><span data-stu-id="35960-128">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects only the services with a Status property that equals Running.</span></span>

<span data-ttu-id="35960-129">Status n’est qu’une des propriétés des objets Service.</span><span class="sxs-lookup"><span data-stu-id="35960-129">Status is only one property of service objects.</span></span>
<span data-ttu-id="35960-130">Pour afficher toutes les propriétés, tapez `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="35960-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="35960-131">Exemple 6 : obtenir les services sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="35960-131">Example 6: Get the services on a remote computer</span></span>

```powershell
Get-Service -ComputerName "Server02"
```

<span data-ttu-id="35960-132">Cette commande obtient les services présents sur l’ordinateur distant Server02.</span><span class="sxs-lookup"><span data-stu-id="35960-132">This command gets the services on the Server02 remote computer.</span></span>

<span data-ttu-id="35960-133">Étant donné que le paramètre *ComputerName* de la fenêtre **obtenir le service** n’utilise pas la communication à distance Windows PowerShell, vous pouvez utiliser ce paramètre même si l’ordinateur n’est pas configuré pour la communication à distance dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35960-133">Because the *ComputerName* parameter of **Get-Service** does not use Windows PowerShell remoting, you can use this parameter even if the computer is not configured for remoting in Windows PowerShell.</span></span>

### <span data-ttu-id="35960-134">Exemple 7 : répertorier les services sur l’ordinateur local qui ont des services dépendants</span><span class="sxs-lookup"><span data-stu-id="35960-134">Example 7: List the services on the local computer that have dependent services</span></span>

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

<span data-ttu-id="35960-135">La première commande utilise l’applet de commande **obten-service** pour récupérer les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35960-135">The first command uses the **Get-Service** cmdlet to get the services on the computer.</span></span>
<span data-ttu-id="35960-136">Un opérateur de pipeline (|) envoie les services à l’applet de commande **Where-Object** , qui sélectionne les services dont la propriété **DependentServices** n’a pas la valeur null.</span><span class="sxs-lookup"><span data-stu-id="35960-136">A pipeline operator (|) sends the services to the **Where-Object** cmdlet, which selects the services whose **DependentServices** property is not null.</span></span>

<span data-ttu-id="35960-137">Un autre opérateur de pipeline envoie les résultats à l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="35960-137">Another pipeline operator sends the results to the Format-List cmdlet.</span></span>
<span data-ttu-id="35960-138">La commande utilise son paramètre *Property* pour afficher le nom du service, le nom des services dépendants et une propriété calculée qui affiche le nombre de services dépendants de chaque service.</span><span class="sxs-lookup"><span data-stu-id="35960-138">The command uses its *Property* parameter to display the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services that each service has.</span></span>

### <span data-ttu-id="35960-139">Exemple 8 : trier les services par valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="35960-139">Example 8: Sort services by property value</span></span>

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

<span data-ttu-id="35960-140">Cette commande montre que lorsque vous triez des services dans l’ordre croissant en fonction de la valeur de leur propriété **Status** , les services arrêtés s’affichent avant l’exécution des services.</span><span class="sxs-lookup"><span data-stu-id="35960-140">This command shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span>
<span data-ttu-id="35960-141">Cela est dû au fait que la valeur de Status est une énumération, dans laquelle Stopped a la valeur 1, et Running a la valeur 4.</span><span class="sxs-lookup"><span data-stu-id="35960-141">This happens because the value of Status is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span>

<span data-ttu-id="35960-142">Pour répertorier d’abord les services en cours d’exécution, utilisez le paramètre *décroissant* de l’applet de commande Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="35960-142">To list running services first, use the *Descending* parameter of the Sort-Object cmdlet.</span></span>

### <span data-ttu-id="35960-143">Exemple 9 : récupérer des services sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="35960-143">Example 9: Get services on multiple computers</span></span>

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

<span data-ttu-id="35960-144">Cette commande utilise l’applet de commande **obtenir-service** pour exécuter une commande Get-Service WinRM sur deux ordinateurs distants et sur l’ordinateur local (« localhost »).</span><span class="sxs-lookup"><span data-stu-id="35960-144">This command uses the **Get-Service** cmdlet to run a Get-Service Winrm command on two remote computers and the local computer ("localhost").</span></span>

<span data-ttu-id="35960-145">La commande s’exécute sur les ordinateurs distants et les résultats sont retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="35960-145">The command runs on the remote computers, and the results are returned to the local computer.</span></span>
<span data-ttu-id="35960-146">Un opérateur de pipeline (|) envoie les résultats à l’applet de commande **format-table** , qui met en forme les services sous la forme d’une table.</span><span class="sxs-lookup"><span data-stu-id="35960-146">A pipeline operator (|) sends the results to the **Format-Table** cmdlet, which formats the services as a table.</span></span>
<span data-ttu-id="35960-147">La commande **format-table** utilise le paramètre *Property* pour spécifier les propriétés affichées dans le tableau, y compris la propriété **MachineName** .</span><span class="sxs-lookup"><span data-stu-id="35960-147">The **Format-Table** command uses the *Property* parameter to specify the properties displayed in the table, including the **MachineName** property.</span></span>

### <span data-ttu-id="35960-148">Exemple 10 : obtenir les services dépendants d’un service</span><span class="sxs-lookup"><span data-stu-id="35960-148">Example 10: Get the dependent services of a service</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

<span data-ttu-id="35960-149">Cette commande obtient les services requis par le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="35960-149">This command gets the services that the WinRM service requires.</span></span>

<span data-ttu-id="35960-150">La commande retourne la valeur de la propriété **ServicesDependedOn** du service.</span><span class="sxs-lookup"><span data-stu-id="35960-150">The command returns the value of the **ServicesDependedOn** property of the service.</span></span>

### <span data-ttu-id="35960-151">Exemple 11 : obtenir un service par le biais de l’opérateur de pipeline</span><span class="sxs-lookup"><span data-stu-id="35960-151">Example 11: Get a service through the pipeline operator</span></span>

```powershell
"WinRM" | Get-Service
```

<span data-ttu-id="35960-152">Cette commande obtient le service WinRM présent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="35960-152">This command gets the WinRM service on the local computer.</span></span>
<span data-ttu-id="35960-153">Cet exemple montre que vous pouvez diriger une chaîne de nom de service (placée entre guillemets) vers **le service d’extraction** .</span><span class="sxs-lookup"><span data-stu-id="35960-153">This example shows that you can pipe a service name string (enclosed in quotation marks) to **Get-Service** .</span></span>

## <span data-ttu-id="35960-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35960-154">PARAMETERS</span></span>

### <span data-ttu-id="35960-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="35960-155">-ComputerName</span></span>

<span data-ttu-id="35960-156">Obtient les services qui s’exécutent sur les ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="35960-156">Gets the services running on the specified computers.</span></span>
<span data-ttu-id="35960-157">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="35960-157">The default is the local computer.</span></span>

<span data-ttu-id="35960-158">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="35960-158">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="35960-159">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="35960-159">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="35960-160">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35960-160">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="35960-161">Vous pouvez utiliser le paramètre *ComputerName* de la commande **par procuration de service** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="35960-161">You can use the *ComputerName* parameter of **Get-Service** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35960-162">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="35960-162">-DependentServices</span></span>

<span data-ttu-id="35960-163">Indique que cette applet de commande obtient uniquement les services qui dépendent du service spécifié.</span><span class="sxs-lookup"><span data-stu-id="35960-163">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

<span data-ttu-id="35960-164">Par défaut, cette applet de commande obtient tous les services.</span><span class="sxs-lookup"><span data-stu-id="35960-164">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35960-165">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="35960-165">-DisplayName</span></span>

<span data-ttu-id="35960-166">Spécifie, sous forme de tableau de chaînes, les noms d’affichage des services à récupérer.</span><span class="sxs-lookup"><span data-stu-id="35960-166">Specifies, as a string array, the display names of services to be retrieved.</span></span>
<span data-ttu-id="35960-167">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="35960-167">Wildcards are permitted.</span></span>
<span data-ttu-id="35960-168">Par défaut, cette applet de commande obtient tous les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35960-168">By default, this cmdlet gets all services on the computer.</span></span>

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

### <span data-ttu-id="35960-169">-Exclude</span><span class="sxs-lookup"><span data-stu-id="35960-169">-Exclude</span></span>

<span data-ttu-id="35960-170">Spécifie, sous forme de tableau de chaînes, un ou des services que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="35960-170">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="35960-171">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="35960-171">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="35960-172">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="35960-172">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="35960-173">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="35960-173">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="35960-174">-Include</span><span class="sxs-lookup"><span data-stu-id="35960-174">-Include</span></span>

<span data-ttu-id="35960-175">Spécifie, sous la forme d’un tableau de chaînes, un ou des services inclus dans l’opération par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35960-175">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="35960-176">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="35960-176">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="35960-177">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="35960-177">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="35960-178">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="35960-178">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="35960-179">-InputObject</span><span class="sxs-lookup"><span data-stu-id="35960-179">-InputObject</span></span>

<span data-ttu-id="35960-180">Spécifie les objets **ServiceController** représentant les services à récupérer.</span><span class="sxs-lookup"><span data-stu-id="35960-180">Specifies **ServiceController** objects representing the services to be retrieved.</span></span>
<span data-ttu-id="35960-181">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="35960-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>
<span data-ttu-id="35960-182">Vous pouvez également diriger un objet service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35960-182">You can also pipe a service object to this cmdlet.</span></span>

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

### <span data-ttu-id="35960-183">-Name</span><span class="sxs-lookup"><span data-stu-id="35960-183">-Name</span></span>

<span data-ttu-id="35960-184">Spécifie les noms des services à récupérer.</span><span class="sxs-lookup"><span data-stu-id="35960-184">Specifies the service names of services to be retrieved.</span></span>
<span data-ttu-id="35960-185">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="35960-185">Wildcards are permitted.</span></span>
<span data-ttu-id="35960-186">Par défaut, cette applet de commande obtient tous les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35960-186">By default, this cmdlet gets all of the services on the computer.</span></span>

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

### <span data-ttu-id="35960-187">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="35960-187">-RequiredServices</span></span>

<span data-ttu-id="35960-188">Indique que cette applet de commande obtient uniquement les services dont ce service a besoin.</span><span class="sxs-lookup"><span data-stu-id="35960-188">Indicates that this cmdlet gets only the services that this service requires.</span></span>

<span data-ttu-id="35960-189">Ce paramètre obtient la valeur de la propriété **ServicesDependedOn** du service.</span><span class="sxs-lookup"><span data-stu-id="35960-189">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>
<span data-ttu-id="35960-190">Par défaut, cette applet de commande obtient tous les services.</span><span class="sxs-lookup"><span data-stu-id="35960-190">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="35960-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35960-191">CommonParameters</span></span>

<span data-ttu-id="35960-192">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="35960-192">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35960-193">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="35960-193">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35960-194">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="35960-194">INPUTS</span></span>

### <span data-ttu-id="35960-195">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="35960-195">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="35960-196">Vous pouvez diriger un objet de service ou un nom de service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35960-196">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="35960-197">SORTIES</span><span class="sxs-lookup"><span data-stu-id="35960-197">OUTPUTS</span></span>

### <span data-ttu-id="35960-198">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="35960-198">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="35960-199">Cette applet de commande retourne des objets qui représentent les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35960-199">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="35960-200">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="35960-200">NOTES</span></span>

<span data-ttu-id="35960-201">Vous pouvez également faire référence à la mise en **service** à l’aide de son alias intégré, « GSV ».</span><span class="sxs-lookup"><span data-stu-id="35960-201">You can also refer to **Get-Service** by its built-in alias, "gsv".</span></span> <span data-ttu-id="35960-202">Pour plus d'informations, consultez about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="35960-202">For more information, see about_Aliases.</span></span>

<span data-ttu-id="35960-203">Cette applet de commande peut afficher les services uniquement lorsque l’utilisateur actuel a l’autorisation de les afficher.</span><span class="sxs-lookup"><span data-stu-id="35960-203">This cmdlet can display services only when the current user has permission to see them.</span></span>
<span data-ttu-id="35960-204">Si cette applet de commande n’affiche pas de services, vous n’avez peut-être pas l’autorisation de les afficher.</span><span class="sxs-lookup"><span data-stu-id="35960-204">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="35960-205">Pour rechercher le nom du service et le nom d’affichage de chaque service sur votre système, tapez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="35960-205">To find the service name and display name of each service on your system, type `Get-Service`.</span></span>
<span data-ttu-id="35960-206">Les noms de service figurent dans la colonne Name et les noms d'affichage apparaissent dans la colonne DisplayName.</span><span class="sxs-lookup"><span data-stu-id="35960-206">The service names appear in the Name column, and the display names appear in the DisplayName column.</span></span>

<span data-ttu-id="35960-207">Lorsque vous procédez à un tri dans l’ordre croissant en fonction de la valeur d’état, les services arrêtés (Stopped) apparaissent avant les services en cours d’exécution (Running).</span><span class="sxs-lookup"><span data-stu-id="35960-207">When you sort in ascending order by status value, "Stopped" services appear before "Running" services.</span></span>
<span data-ttu-id="35960-208">La propriété Status d’un service est une valeur énumérée dans laquelle le nom des états représente des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="35960-208">The Status property of a service is an enumerated value in which the names of the statuses represent integer values.</span></span>
<span data-ttu-id="35960-209">Le tri repose sur la valeur entière, et non sur le nom.</span><span class="sxs-lookup"><span data-stu-id="35960-209">The sort is based on the integer value, not the name.</span></span>
<span data-ttu-id="35960-210">« Running » apparaît avant « Stopped », car « Stopped » a la valeur « 1 » et « Running » a la valeur « 4 ».</span><span class="sxs-lookup"><span data-stu-id="35960-210">"Running" appears before "Stopped" because "Stopped" has a value of "1", and "Running" has a value of "4".</span></span>

## <span data-ttu-id="35960-211">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="35960-211">RELATED LINKS</span></span>

[<span data-ttu-id="35960-212">New-Service</span><span class="sxs-lookup"><span data-stu-id="35960-212">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="35960-213">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="35960-213">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="35960-214">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="35960-214">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="35960-215">Set-Service</span><span class="sxs-lookup"><span data-stu-id="35960-215">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="35960-216">Start-Service</span><span class="sxs-lookup"><span data-stu-id="35960-216">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="35960-217">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="35960-217">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="35960-218">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="35960-218">Suspend-Service</span></span>](Suspend-Service.md)
