---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076597"
---
# <a name="get-test-set"></a>Get-Test-Set

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

![Méthodes Get, Test et Set](/media/get-test-set.png)

PowerShell Desired State Configuration est construit autour d’un processus **Get**, **Test** et **Set**. Chaque [ressource](resources.md) DSC contient des méthodes pour effectuer chacune de ces opérations. Dans une [configuration](../configurations/configurations.md), vous définissez des blocs de ressources pour renseigner des clés qui deviennent des paramètres pour les méthodes **Get**, **Test** et **Set** d’une ressource.

Voici la syntaxe d’un bloc de ressources **Service**. La ressource **Service** configure les services Windows.

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

Les méthodes **Get**, **Test** et **Set** de la ressource **Service** incluront des blocs de paramètres qui acceptent ces valeurs.

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
> Le langage et la méthode utilisés pour définir la ressource déterminent comment les méthodes **Get**, **Test** et **Set** seront définies.

Comme la ressource **Service** contient uniquement une clé requise (`Name`), une ressource de bloc **Service** peut être aussi simple que cela :

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

Lorsque vous compilez la configuration ci-dessus, les valeurs que vous spécifiez pour une clé sont stockées dans le fichier « .mof » généré. Pour plus d’informations, consultez [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Lorsqu’il est utilisé, le [gestionnaire de configuration local](../managing-nodes/metaConfig.md) lit la valeur « Spooler » du fichier « .mof » et la transmet au paramètre `-Name` des méthodes **Get**, **Test** et **Set** pour l’instance « MyService » de la ressource **Service**.

## <a name="get"></a>Get

La méthode **Get** d’une ressource récupère l’état de la ressource telle qu’elle est configurée sur le nœud cible. Cet état est retourné sous la forme d’une [table de hachage](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Les clés de la **table de hachage** sont les valeurs configurables, ou paramètres, que la ressource accepte.

La méthode **Get** est directement mappée à l’applet de commande [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration). Lorsque vous appelez `Get-DSCConfiguration`, le LCM exécute la méthode **Get** de chaque ressource dans la configuration actuellement appliquée. Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » comme paramètres pour chaque instance de ressource correspondante.

Voici un exemple de résultat provenant d’une ressource **Service** qui configure le service « Spooler ».

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

Le résultat indique les propriétés de valeurs actuelles configurables par la ressource **Service**.

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

## <a name="test"></a>Test

La méthode **Test** d’une ressource détermine si le nœud cible est actuellement conforme à l’*état souhaité* de la ressource. La méthode **Test** retourne `$True` ou `$False` uniquement pour indiquer si le nœud est conforme.
Lorsque vous appelez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), le LCM appelle la méthode **Test** de chaque ressource dans la configuration actuellement appliquée. Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » comme paramètres pour chaque instance de ressource correspondante.

Si le résultat du **test** d’une ressource individuelle affiche `$False`, `Test-DSCConfiguration` retourne `$False` indiquant que le nœud n’est pas conforme. Si toutes les méthodes **Test** d’une ressource retournent `$True`, `Test-DSCConfiguration` retourne `$True` pour indiquer que le nœud est conforme.

```powershell
Test-DSCConfiguration
```

```output
True
```

À compter de PowerShell 5.0, le paramètre `-Detailed` a été ajouté. En spécifiant `-Detailed`, `Test-DSCConfiguration` retourne un objet contenant des ensembles de résultats pour les ressources conformes et non conformes.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Pour plus d’informations, consultez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Set

La méthode **Set** d’une ressource tente de forcer le nœud à être conforme avec l’*état souhaité* de la ressource. La méthode **Set** est prévue pour être **idempotente**, ce qui signifie que **Set** peut être exécutée plusieurs fois et générer toujours le même résultat sans erreurs.  Lorsque vous exécutez [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), le LCM est appliqué en boucle sur chaque ressource dans la configuration actuellement appliquée. Le LCM récupère les valeurs des clés pour l’instance actuelle de la ressource à partir du fichier « .mof » et les utilise comme paramètres pour la méthode **Test**. Si la méthode **Test** retourne `$True`, le nœud est conforme à la ressource actuelle et la méthode **Set** est ignorée. Si le **test** retourne `$False`, le nœud n’est pas conforme.  Le LCM transmet les valeurs de clés de l’instance la ressource en tant que paramètres à la méthode **Set** de la ressource, restaurant ainsi la conformité du nœud.

En spécifiant les paramètres `-Verbose` et `-Wait`, vous pouvez surveiller la progression de l’applet de commande `Start-DSCConfiguration`. Dans cet exemple, le nœud est déjà conforme. Le résultat `Verbose` indique que la méthode **Set** a été ignorée.

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

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configuration d’un serveur collecteur SMB](../pull-server/pullServerSMB.md)
- [Configuration d’un client d’extraction](../pull-server/pullClientConfigID.md)
