---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Get-Test-Set
ms.openlocfilehash: f7b7e947a85832365a783e40c25a25bfaa9fff8d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771513"
---
# <a name="get-test-set"></a><span data-ttu-id="6c32b-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="6c32b-103">Get-Test-Set</span></span>

><span data-ttu-id="6c32b-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6c32b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6c32b-105">PowerShell Desired State Configuration est construit autour d’un processus **Get**, **Test** et **Set**.</span><span class="sxs-lookup"><span data-stu-id="6c32b-105">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="6c32b-106">Chaque [ressource](resources.md) DSC contient des méthodes pour effectuer chacune de ces opérations.</span><span class="sxs-lookup"><span data-stu-id="6c32b-106">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span>
<span data-ttu-id="6c32b-107">Dans une [configuration](../configurations/configurations.md), vous définissez des blocs de ressources pour renseigner des clés qui deviennent des paramètres pour les méthodes **Get**, **Test** et **Set** d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="6c32b-107">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="6c32b-108">Voici la syntaxe d’un bloc de ressources **Service**.</span><span class="sxs-lookup"><span data-stu-id="6c32b-108">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="6c32b-109">La ressource **Service** configure les services Windows.</span><span class="sxs-lookup"><span data-stu-id="6c32b-109">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="6c32b-110">Les méthodes **Get**, **Test** et **Set** de la ressource **Service** incluront des blocs de paramètres qui acceptent ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="6c32b-110">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="6c32b-111">Le langage et la méthode utilisés pour définir la ressource déterminent comment les méthodes **Get**, **Test** et **Set** seront définies.</span><span class="sxs-lookup"><span data-stu-id="6c32b-111">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="6c32b-112">Comme la ressource **Service** contient uniquement une clé requise (`Name`), une ressource de bloc **Service** peut être aussi simple que cela :</span><span class="sxs-lookup"><span data-stu-id="6c32b-112">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="6c32b-113">Lorsque vous compilez la configuration ci-dessus, les valeurs que vous spécifiez pour une clé sont stockées dans le fichier `.mof` généré.</span><span class="sxs-lookup"><span data-stu-id="6c32b-113">When you compile the Configuration above, the values you specify for a key are stored in the `.mof` file that is generated.</span></span> <span data-ttu-id="6c32b-114">Pour plus d’informations, consultez [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="6c32b-114">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="6c32b-115">Lorsqu’il est utilisé, le [gestionnaire de configuration local](../managing-nodes/metaConfig.md) lit la valeur « Spooler » du fichier `.mof` et la transmet au paramètre **Name** des méthodes **Get**, **Test** et **Set** pour l’instance « MyService » de la ressource **Service**.</span><span class="sxs-lookup"><span data-stu-id="6c32b-115">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the `.mof` file, and pass it to the **Name** parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="6c32b-116">Obtenir</span><span class="sxs-lookup"><span data-stu-id="6c32b-116">Get</span></span>

<span data-ttu-id="6c32b-117">La méthode **Get** d’une ressource récupère l’état de la ressource telle qu’elle est configurée sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="6c32b-117">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="6c32b-118">Cet état est retourné sous la forme d’une [table de hachage](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="6c32b-118">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>
<span data-ttu-id="6c32b-119">Les clés de la **table de hachage** sont les valeurs configurables, ou paramètres, que la ressource accepte.</span><span class="sxs-lookup"><span data-stu-id="6c32b-119">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="6c32b-120">La méthode **Get** est directement mappée à l’applet de commande [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="6c32b-120">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="6c32b-121">Lorsque vous appelez `Get-DSCConfiguration`, le LCM exécute la méthode **Get** de chaque ressource dans la configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="6c32b-121">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="6c32b-122">Le LCM utilise les valeurs de clé stockées dans le fichier `.mof` comme paramètres pour chaque instance de ressource correspondante.</span><span class="sxs-lookup"><span data-stu-id="6c32b-122">The LCM uses the key values stored in the `.mof` file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="6c32b-123">Voici un exemple de résultat provenant d’une ressource **Service** qui configure le service « Spooler ».</span><span class="sxs-lookup"><span data-stu-id="6c32b-123">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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
                       this service, you won't be able to print or see your printers.
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

<span data-ttu-id="6c32b-124">Le résultat indique les propriétés de valeurs actuelles configurables par la ressource **Service**.</span><span class="sxs-lookup"><span data-stu-id="6c32b-124">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="6c32b-125">Test</span><span class="sxs-lookup"><span data-stu-id="6c32b-125">Test</span></span>

<span data-ttu-id="6c32b-126">La méthode **Test** d’une ressource détermine si le nœud cible est actuellement conforme à l’_état souhaité_ de la ressource.</span><span class="sxs-lookup"><span data-stu-id="6c32b-126">The **Test** method of a resource determines if the target node is currently compliant with the resource's _desired state_.</span></span> <span data-ttu-id="6c32b-127">La méthode **Test** retourne `$true` ou `$false` uniquement pour indiquer si le nœud est conforme.</span><span class="sxs-lookup"><span data-stu-id="6c32b-127">The **Test** method returns `$true` or `$false` only to indicate whether the Node is compliant.</span></span> <span data-ttu-id="6c32b-128">Lorsque vous appelez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), le LCM appelle la méthode **Test** de chaque ressource dans la configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="6c32b-128">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="6c32b-129">Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » comme paramètres pour chaque instance de ressource correspondante.</span><span class="sxs-lookup"><span data-stu-id="6c32b-129">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="6c32b-130">Si le résultat du **test** d’une ressource individuelle affiche `$false`, `Test-DSCConfiguration` retourne `$false` indiquant que le nœud n’est pas conforme.</span><span class="sxs-lookup"><span data-stu-id="6c32b-130">If the result of any individual resource's **Test** is `$false`, `Test-DSCConfiguration` returns `$false` indicating that the Node is not compliant.</span></span> <span data-ttu-id="6c32b-131">Si toutes les méthodes **Test** d’une ressource retournent `$true`, `Test-DSCConfiguration` retourne `$true` pour indiquer que le nœud est conforme.</span><span class="sxs-lookup"><span data-stu-id="6c32b-131">If all resource's **Test** methods return `$true`, `Test-DSCConfiguration` returns `$true` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="6c32b-132">À compter de PowerShell 5.0, le paramètre **Detailed** a été ajouté.</span><span class="sxs-lookup"><span data-stu-id="6c32b-132">Beginning in PowerShell 5.0, the **Detailed** parameter was added.</span></span> <span data-ttu-id="6c32b-133">En spécifiant **Detailed**, `Test-DSCConfiguration` retourne un objet contenant des ensembles de résultats pour les ressources conformes et non conformes.</span><span class="sxs-lookup"><span data-stu-id="6c32b-133">Specifying **Detailed** causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="6c32b-134">Pour plus d’informations, consultez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="6c32b-134">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="6c32b-135">Définissez</span><span class="sxs-lookup"><span data-stu-id="6c32b-135">Set</span></span>

<span data-ttu-id="6c32b-136">La méthode **Set** d’une ressource tente de forcer le nœud à être conforme avec l’*état souhaité* de la ressource.</span><span class="sxs-lookup"><span data-stu-id="6c32b-136">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="6c32b-137">La méthode **Set** est prévue pour être **idempotente**, ce qui signifie que **Set** peut être exécutée plusieurs fois et générer toujours le même résultat sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="6c32b-137">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span> <span data-ttu-id="6c32b-138">Lorsque vous exécutez [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), le LCM est appliqué en boucle sur chaque ressource dans la configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="6c32b-138">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="6c32b-139">Le LCM récupère les valeurs des clés pour l’instance actuelle de la ressource à partir du fichier « .mof » et les utilise comme paramètres pour la méthode **Test**.</span><span class="sxs-lookup"><span data-stu-id="6c32b-139">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="6c32b-140">Si la méthode **Test** retourne `$true`, le nœud est conforme à la ressource actuelle et la méthode **Set** est ignorée.</span><span class="sxs-lookup"><span data-stu-id="6c32b-140">If the **Test** method returns `$true`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="6c32b-141">Si le **test** retourne `$false`, le nœud n’est pas conforme.</span><span class="sxs-lookup"><span data-stu-id="6c32b-141">If the **Test** returns `$false`, the Node is non-compliant.</span></span> <span data-ttu-id="6c32b-142">Le LCM transmet les valeurs de clés de l’instance la ressource en tant que paramètres à la méthode **Set** de la ressource, restaurant ainsi la conformité du nœud.</span><span class="sxs-lookup"><span data-stu-id="6c32b-142">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="6c32b-143">En spécifiant les paramètres **Verbose** et **Wait**, vous pouvez surveiller la progression de l’applet de commande `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="6c32b-143">By specifying the **Verbose** and **Wait** parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="6c32b-144">Dans cet exemple, le nœud est déjà conforme.</span><span class="sxs-lookup"><span data-stu-id="6c32b-144">In this example, the Node is already compliant.</span></span> <span data-ttu-id="6c32b-145">Le résultat `Verbose` indique que la méthode **Set** a été ignorée.</span><span class="sxs-lookup"><span data-stu-id="6c32b-145">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6c32b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c32b-146">See also</span></span>

- [<span data-ttu-id="6c32b-147">Vue d’ensemble d’Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="6c32b-147">Azure Automation DSC Overview</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="6c32b-148">Configuration d’un serveur collecteur SMB</span><span class="sxs-lookup"><span data-stu-id="6c32b-148">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="6c32b-149">Configuration d’un client d’extraction</span><span class="sxs-lookup"><span data-stu-id="6c32b-149">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
