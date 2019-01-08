---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401444"
---
# <a name="get-test-set"></a><span data-ttu-id="2e3ed-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="2e3ed-103">Get-Test-Set</span></span>

><span data-ttu-id="2e3ed-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2e3ed-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Méthodes Get, Test et Set](/media/get-test-set.png)

<span data-ttu-id="2e3ed-106">PowerShell Desired State Configuration est construit autour d’un **obtenir**, **Test**, et **définir** processus.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="2e3ed-107">DSC [ressources](resources.md) chacun contient des méthodes pour effectuer chacune de ces opérations.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="2e3ed-108">Dans un [Configuration](../configurations/configurations.md), vous définissez des blocs de ressources pour renseigner les clés qui deviennent des paramètres pour la ressource **obtenir**, **Test**, et **définir** méthodes.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="2e3ed-109">Voici la syntaxe pour une **Service** bloc de ressources.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="2e3ed-110">Le **Service** ressource configure les services Windows.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-110">The **Service** resource configures Windows services.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="2e3ed-111">Le **obtenir**, **Test**, et **définir** méthodes de la **Service** ressource auront des blocs de paramètres qui acceptent ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> <span data-ttu-id="2e3ed-112">La méthode utilisée pour définir la ressource de langue et détermine comment la **obtenir**, **Test**, et **définir** méthodes seront définis.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="2e3ed-113">Étant donné que le **Service** ressource a uniquement une clé requise (`Name`), un **Service** bloc ressource peut être aussi simple que cela :</span><span class="sxs-lookup"><span data-stu-id="2e3ed-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

<span data-ttu-id="2e3ed-114">Lorsque vous compilez la Configuration ci-dessus, les valeurs que vous spécifiez pour une clé sont stockées dans le fichier « .mof » qui est généré.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="2e3ed-115">Pour plus d’informations, consultez [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="2e3ed-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

<span data-ttu-id="2e3ed-116">Lorsqu’il est appliqué, le [Gestionnaire de Configuration Local](../managing-nodes/metaConfig.md) lit la valeur « Spooler » à partir du fichier « .mof » et transmettez-le à la `-Name` paramètre de la **obtenir**, **Test**, et **définir** méthodes pour l’instance « MyService » de la **Service** ressource.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="2e3ed-117">Get</span><span class="sxs-lookup"><span data-stu-id="2e3ed-117">Get</span></span>

<span data-ttu-id="2e3ed-118">Le **obtenir** méthode d’une ressource, récupère l’état de la ressource car elle est configurée sur la nœud cible.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="2e3ed-119">Cet état est retourné comme un [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="2e3ed-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="2e3ed-120">Les clés de la **hashtable** seront les valeurs configurables, ou des paramètres, accepte la ressource.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="2e3ed-121">Le **obtenir** méthode mappe directement à la [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="2e3ed-122">Lorsque vous appelez `Get-DSCConfiguration`, l’exécution du Gestionnaire de configuration local les **obtenir** (méthode) de chaque ressource dans la configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="2e3ed-123">Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » en tant que paramètres à chaque instance de ressource correspondante.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="2e3ed-124">Il s’agit d’exemple de sortie à partir d’un **Service** ressource qui configure le service « Spooler ».</span><span class="sxs-lookup"><span data-stu-id="2e3ed-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

<span data-ttu-id="2e3ed-125">La sortie indique les propriétés actuelles de la valeur configurable par le **Service** ressource.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a><span data-ttu-id="2e3ed-126">Test</span><span class="sxs-lookup"><span data-stu-id="2e3ed-126">Test</span></span>

<span data-ttu-id="2e3ed-127">Le **Test** méthode d’une ressource détermine si le nœud cible est actuellement conforme à la ressource *l’état souhaité*.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="2e3ed-128">Le **Test** retourne de la méthode `$True` ou `$False` uniquement pour indiquer si le nœud est conforme.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="2e3ed-129">Lorsque vous appelez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), les appels du Gestionnaire de configuration local les **Test** (méthode) de chaque ressource dans la configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="2e3ed-130">Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » en tant que paramètres à chaque instance de ressource correspondante.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="2e3ed-131">Si le résultat de toute ressource **Test** est `$False`, `Test-DSCConfiguration` retourne `$False` indiquant que le nœud n’est pas conforme.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="2e3ed-132">Si de toutes les ressources **Test** méthodes retournent `$True`, `Test-DSCConfiguration` retourne `$True` pour indiquer que le nœud est conforme.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="2e3ed-133">À compter de PowerShell 5.0, le `-Detailed` paramètre a été ajouté.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="2e3ed-134">Spécification `-Detailed` provoque `Test-DSCConfiguration` pour retourner un objet qui contient des ensembles de résultats pour les ressources conformes et non conformes.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="2e3ed-135">Pour plus d’informations, consultez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="2e3ed-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="2e3ed-136">Set</span><span class="sxs-lookup"><span data-stu-id="2e3ed-136">Set</span></span>

<span data-ttu-id="2e3ed-137">Le **définir** (méthode) d’une ressource tente de forcer le nœud pour être compatibles avec la ressource *l’état souhaité*.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="2e3ed-138">Le **définir** méthode est prévue pour être **idempotent**, ce qui signifie que **définir** peut être exécuté plusieurs fois et toujours obtenir le même résultat sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="2e3ed-139">Lorsque vous exécutez [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), les cycles de gestionnaire de configuration local via chaque ressource dans la configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="2e3ed-140">Le LCM récupère les valeurs de clés pour l’instance actuelle de la ressource à partir du fichier « .mof » et les utilise en tant que paramètres pour le **Test** (méthode).</span><span class="sxs-lookup"><span data-stu-id="2e3ed-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="2e3ed-141">Si le **Test** retourne de la méthode `$True`, le nœud est conforme à la ressource actuelle et le **définir** méthode est ignorée.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="2e3ed-142">Si le **Test** retourne `$False`, le nœud n’est pas conforme.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="2e3ed-143">Le LCM transmet la ressource de valeurs de clé de l’instance en tant que paramètres à la ressource **définir** méthode, la restauration du nœud à la conformité.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="2e3ed-144">En spécifiant le `-Verbose` et `-Wait` paramètres, vous pouvez surveiller la progression de la `Start-DSCConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="2e3ed-145">Dans cet exemple, le nœud est déjà conforme.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="2e3ed-146">Le `Verbose` sortie indique que le **définir** méthode a été ignorée.</span><span class="sxs-lookup"><span data-stu-id="2e3ed-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a><span data-ttu-id="2e3ed-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e3ed-147">See also</span></span>

- [<span data-ttu-id="2e3ed-148">Vue d’ensemble d’Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="2e3ed-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="2e3ed-149">Configuration d’un serveur collecteur SMB</span><span class="sxs-lookup"><span data-stu-id="2e3ed-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="2e3ed-150">Configuration d’un client d’extraction</span><span class="sxs-lookup"><span data-stu-id="2e3ed-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
