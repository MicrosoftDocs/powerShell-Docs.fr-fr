---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Débogage des ressources DSC
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954256"
---
# <a name="debugging-dsc-resources"></a>Débogage des ressources DSC

> S’applique à : Windows PowerShell 5.0

Dans PowerShell 5.0, DSC contient une nouvelle fonctionnalité qui permet de déboguer une ressource DSC pendant qu’une configuration est appliquée.

## <a name="enabling-dsc-debugging"></a>Activation du débogage DSC
Avant de pouvoir déboguer une ressource, vous devez activer le débogage en appelant l’applet de commande [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug).
Cette applet de commande prend un paramètre obligatoire : **BreakAll**.

Vous pouvez vérifier que le débogage a été activé en examinant le résultat d’un appel à [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

La sortie PowerShell suivante montre le résultat de l’activation du débogage :


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a>Démarrage d’une configuration avec le débogage activé
Pour déboguer une ressource DSC, démarrez une configuration qui appelle cette ressource.
Pour cet exemple, nous allons étudier une configuration simple qui appelle la ressource **WindowsFeature** pour vérifier que la fonctionnalité « WindowsPowerShellWebAccess » est bien installée :

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
Après la compilation de la configuration, démarrez-la en appelant [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
La configuration s’arrête quand le gestionnaire de configuration local appelle la première ressource de la configuration.
Si vous utilisez les paramètres `-Verbose` et `-Wait`, la sortie affiche les lignes que vous devez entrer pour démarrer le débogage.

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
À ce stade, le gestionnaire de configuration local a appelé la ressource et arrive au premier point d’arrêt.
Les trois dernières lignes de la sortie vous montrent comment attacher au processus et commencer à déboguer le script de ressource.

## <a name="debugging-the-resource-script"></a>Débogage du script de la ressource

Démarrez une nouvelle instance de PowerShell ISE.
Dans le volet de la console, entrez les trois dernières lignes de la sortie de la `Start-DscConfiguration` sous forme de commandes, en remplaçant `<credentials>` par des informations d’identification valides.
Une invite du type suivant doit s’afficher :

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Le script de ressources s’ouvre dans le volet de script et le débogueur s’arrête à la première ligne de la fonction **Test-TargetResource** (la méthode **Test()** d’une ressource de classe).
Vous pouvez désormais utiliser les commandes de débogage dans l’environnement ISE pour parcourir le script de ressources, examiner les valeurs des variables, afficher la pile des appels et ainsi de suite. N’oubliez pas que chaque ligne du script de ressources (ou classe) est défini comme point d’arrêt.

## <a name="disabling-dsc-debugging"></a>Désactivation du débogage DSC

Après avoir appelé [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), tous les appels à [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) causeront des erreurs de configuration dans le débogueur. Pour permettre aux configurations de s’exécuter normalement, vous devez désactiver le débogage en appelant l’applet de commande [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug).

>**Remarque :** Le redémarrage ne modifie pas l’état de débogage du Gestionnaire de configuration local. Si le débogage est activé, le démarrage d’une configuration générera toujours des erreurs après un redémarrage.

## <a name="see-also"></a>Voir aussi

- [Écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md)
- [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](../resources/authoringResourceClass.md)
