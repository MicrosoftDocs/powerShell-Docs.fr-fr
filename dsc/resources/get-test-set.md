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
# <a name="get-test-set"></a>Get-Test-Set

>S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

![Méthodes Get, Test et Set](/media/get-test-set.png)

PowerShell Desired State Configuration est construit autour d’un **obtenir**, **Test**, et **définir** processus. DSC [ressources](resources.md) chacun contient des méthodes pour effectuer chacune de ces opérations. Dans un [Configuration](../configurations/configurations.md), vous définissez des blocs de ressources pour renseigner les clés qui deviennent des paramètres pour la ressource **obtenir**, **Test**, et **définir** méthodes.

Voici la syntaxe pour une **Service** bloc de ressources. Le **Service** ressource configure les services Windows.

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

Le **obtenir**, **Test**, et **définir** méthodes de la **Service** ressource auront des blocs de paramètres qui acceptent ces valeurs.

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
> La méthode utilisée pour définir la ressource de langue et détermine comment la **obtenir**, **Test**, et **définir** méthodes seront définis.

Étant donné que le **Service** ressource a uniquement une clé requise (`Name`), un **Service** bloc ressource peut être aussi simple que cela :

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

Lorsque vous compilez la Configuration ci-dessus, les valeurs que vous spécifiez pour une clé sont stockées dans le fichier « .mof » qui est généré. Pour plus d’informations, consultez [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Lorsqu’il est appliqué, le [Gestionnaire de Configuration Local](../managing-nodes/metaConfig.md) lit la valeur « Spooler » à partir du fichier « .mof » et transmettez-le à la `-Name` paramètre de la **obtenir**, **Test**, et **définir** méthodes pour l’instance « MyService » de la **Service** ressource.

## <a name="get"></a>Get

Le **obtenir** méthode d’une ressource, récupère l’état de la ressource car elle est configurée sur la nœud cible. Cet état est retourné comme un [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Les clés de la **hashtable** seront les valeurs configurables, ou des paramètres, accepte la ressource.

Le **obtenir** méthode mappe directement à la [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) applet de commande. Lorsque vous appelez `Get-DSCConfiguration`, l’exécution du Gestionnaire de configuration local les **obtenir** (méthode) de chaque ressource dans la configuration actuellement appliquée. Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » en tant que paramètres à chaque instance de ressource correspondante.

Il s’agit d’exemple de sortie à partir d’un **Service** ressource qui configure le service « Spooler ».

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

La sortie indique les propriétés actuelles de la valeur configurable par le **Service** ressource.

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

Le **Test** méthode d’une ressource détermine si le nœud cible est actuellement conforme à la ressource *l’état souhaité*. Le **Test** retourne de la méthode `$True` ou `$False` uniquement pour indiquer si le nœud est conforme.
Lorsque vous appelez [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), les appels du Gestionnaire de configuration local les **Test** (méthode) de chaque ressource dans la configuration actuellement appliquée. Le LCM utilise les valeurs de clé stockées dans le fichier « .mof » en tant que paramètres à chaque instance de ressource correspondante.

Si le résultat de toute ressource **Test** est `$False`, `Test-DSCConfiguration` retourne `$False` indiquant que le nœud n’est pas conforme. Si de toutes les ressources **Test** méthodes retournent `$True`, `Test-DSCConfiguration` retourne `$True` pour indiquer que le nœud est conforme.

```powershell
Test-DSCConfiguration
```

```output
True
```

À compter de PowerShell 5.0, le `-Detailed` paramètre a été ajouté. Spécification `-Detailed` provoque `Test-DSCConfiguration` pour retourner un objet qui contient des ensembles de résultats pour les ressources conformes et non conformes.

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

Le **définir** (méthode) d’une ressource tente de forcer le nœud pour être compatibles avec la ressource *l’état souhaité*. Le **définir** méthode est prévue pour être **idempotent**, ce qui signifie que **définir** peut être exécuté plusieurs fois et toujours obtenir le même résultat sans erreurs.  Lorsque vous exécutez [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), les cycles de gestionnaire de configuration local via chaque ressource dans la configuration actuellement appliquée. Le LCM récupère les valeurs de clés pour l’instance actuelle de la ressource à partir du fichier « .mof » et les utilise en tant que paramètres pour le **Test** (méthode). Si le **Test** retourne de la méthode `$True`, le nœud est conforme à la ressource actuelle et le **définir** méthode est ignorée. Si le **Test** retourne `$False`, le nœud n’est pas conforme.  Le LCM transmet la ressource de valeurs de clé de l’instance en tant que paramètres à la ressource **définir** méthode, la restauration du nœud à la conformité.

En spécifiant le `-Verbose` et `-Wait` paramètres, vous pouvez surveiller la progression de la `Start-DSCConfiguration` applet de commande. Dans cet exemple, le nœud est déjà conforme. Le `Verbose` sortie indique que le **définir** méthode a été ignorée.

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

- [Vue d’ensemble d’Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Configuration d’un serveur collecteur SMB](../pull-server/pullServerSMB.md)
- [Configuration d’un client d’extraction](../pull-server/pullClientConfigID.md)
