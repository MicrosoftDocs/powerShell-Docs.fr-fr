---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Résolution des problèmes liés à DSC
ms.openlocfilehash: 1e8bfdf3540e65e3be94bf6a9b04e7d3b14ff044
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094066"
---
# <a name="troubleshooting-dsc"></a>Résolution des problèmes liés à DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Cette rubrique décrit comment résoudre les problèmes liés à DSC quand ils se produisent.

## <a name="winrm-dependency"></a>Dépendance de WinRM

La Configuration de l’état souhaité (DSC) Windows PowerShell dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7. Exécutez ```Set-WSManQuickConfig``` dans une session Windows PowerShell avec élévation des privilèges pour activer WinRM.

## <a name="using-get-dscconfigurationstatus"></a>Utilisation de l’applet de commande Get-DscConfigurationStatus

L’applet de commande, [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) obtient des informations sur l’état de configuration à partir d’un nœud cible.
Un objet enrichi est retourné. Il comprend des informations générales indiquant si l’exécution de la configuration a réussi ou échoué. Vous pouvez explorer l’objet pour obtenir des détails sur l’exécution de la configuration, notamment :

- Toutes les ressources qui ont échoué
- Toute ressource ayant demandé un redémarrage
- Les paramètres de métaconfiguration au moment de l’exécution de la configuration
- Etc.

Le jeu de paramètres suivant retourne les informations d’état pour la dernière exécution de configuration :

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
Le jeu de paramètres suivant retourne les informations d’état pour toutes les exécutions de configuration précédentes :

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a>Exemple

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :
InDesiredState          :   False
InitialState            :
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Mon script ne s’exécute pas : utilisation des journaux DSC pour diagnostiquer les erreurs de script

Comme tous les logiciels Windows, DSC enregistre les erreurs et les événements dans des [journaux](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) qui peuvent être consultés dans l’[Observateur d’événements](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). L’examen de ces journaux peut vous aider à comprendre pourquoi une opération particulière a échoué et comment éviter que cela se reproduise. L’écriture de scripts de configuration peut être compliquée. Ainsi, pour faciliter le suivi des erreurs pendant le processus de création, utilisez la ressource Log dans DSC pour suivre la progression de votre configuration dans le journal des événements d’analyse DSC.

## <a name="where-are-dsc-event-logs"></a>Où se trouvent les journaux des événements DSC ?

Dans l’Observateur d’événements, les événements DSC se trouvent dans : **Journaux des applications et des services/Microsoft/Windows/Desired State Configuration**

L’applet de commande PowerShell correspondante [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx) peut également être exécutée pour afficher les journaux des événements :

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Comme indiqué ci-dessus, le nom du journal DSC principal est **Microsoft->Windows->DSC** (les autres noms de journal sous Windows ne sont pas cités ici, par souci de concision). Le nom principal est ajouté au nom du canal pour créer le nom complet du journal. Le moteur DSC écrit principalement dans trois types de journaux : [journaux des opérations, d’analyse et de débogage](https://technet.microsoft.com/library/cc722404.aspx). Les journaux d’analyse et de débogage étant désactivés par défaut, vous devez les activer dans l’Observateur d’événements. Pour ce faire, ouvrez l’Observateur d’événements en tapant Show-EventLog dans Windows PowerShell ou cliquez sur le bouton **Démarrer**, sur **Panneau de configuration**, **Outils d’administration**, puis **Observateur d’événements**. Dans le menu **Affichage** de l’Observateur d’événements, cliquez sur **Afficher les journaux d’analyse et de débogage**. Le nom du journal du canal d’analyse est **Microsoft-Windows-Dsc/Analytic** et celui du canal de débogage est **Microsoft-Windows-Dsc/Debug**. Vous pouvez également utiliser l’utilitaire [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) pour activer les journaux, comme l’illustre l’exemple suivant.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Que contiennent les journaux DSC ?

Les journaux DSC sont répartis sur les trois canaux de journal en fonction de l’importance du message. Le journal des opérations dans DSC contient tous les messages d’erreur et peut être utilisé pour identifier un problème. Le journal d’analyse contient un plus grand volume d’événements et peut identifier où se sont produites les erreurs. Ce canal contient également des messages détaillés (le cas échéant). Le journal de débogage contient des journaux qui peuvent vous aider à comprendre comment les erreurs se sont produites. Les messages d’événement DSC sont structurés de telle sorte que chaque message d’événement commence par un ID de tâche représentant de façon unique une opération DSC. L’exemple ci-dessous tente d’obtenir le message du premier événement enregistré dans le journal des opérations DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

Les événements DSC sont enregistrés dans une structure particulière qui permet à l’utilisateur de regrouper les événements d’une seule tâche DSC. La structure est la suivante :

**ID de travail : \<Guid\>**
**\<Event Message\>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Collecte des événements d’une seule opération DSC

Les journaux des événements DSC contiennent des événements générés par diverses opérations DSC. Toutefois, vous êtes généralement intéressé par les détails d’une seule opération en particulier. Tous les journaux DSC peuvent être regroupés par la propriété d’ID de tâche, qui est unique pour chaque opération DSC. L’ID de tâche est affiché comme première valeur de propriété de tous les événements DSC. Les étapes suivantes décrivent comment regrouper tous les événements dans une structure de tableau groupée.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

Ici, la variable `$SeparateDscOperations` contient les journaux regroupés par ID de tâche. Chaque élément du tableau de cette variable représente un groupe d’événements enregistrés par une opération DSC différente, ce qui donne accès à davantage d’informations sur les journaux.

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

Vous pouvez extraire les données de la variable `$SeparateDscOperations` à l’aide de [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Voici cinq scénarios dans lesquels vous pouvez extraire les données pour résoudre les problèmes liés à DSC :

### <a name="1-operations-failures"></a>1 : échecs d’opérations

Tous les événements sont associés à des [niveaux de gravité](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Ces informations peuvent être utilisées pour identifier les événements d’erreur :

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2 : détails des opérations exécutées au cours de la dernière demi-heure

`TimeCreated`, une propriété de chaque événement Windows, indique l’heure de création de l’événement. Vous pouvez comparer cette propriété avec un objet date/heure particulier pour filtrer tous les événements :

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3 : messages de la dernière opération

La dernière opération est stockée dans le premier index du groupe de tableaux `$SeparateDscOperations`. L’interrogation des messages du groupe pour l’index 0 retourne tous les messages de la dernière opération :

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4 : messages d’erreur enregistrés pour les dernières opérations ayant échoué

`$SeparateDscOperations[0].Group` contient un ensemble d’événements pour la dernière opération. Exécutez l’applet de commande `Where-Object` pour filtrer les événements selon le nom d’affichage du niveau. Les résultats sont stockés dans la variable `$myFailedEvent`, qui peut être examinée pour obtenir le message d’événement :

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5 : tous les événements générés pour un ID de tâche en particulier.

`$SeparateDscOperations` est un tableau de groupes, chacun d’eux a comme nom l’ID de tâche unique. En exécutant l’applet de commande `Where-Object`, vous pouvez extraire les groupes d’événements qui ont un ID de tâche particulier :

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Utilisation de xDscDiagnostics pour analyser les journaux DSC

**xDscDiagnostics** est un module PowerShell qui se compose de plusieurs fonctions permettant d’analyser les échecs DSC sur votre ordinateur. Ces fonctions peuvent vous aider à identifier tous les événements locaux des dernières opérations DSC ou les événements DSC sur des ordinateurs distants (avec des informations d’identification valides). Ici, le terme opération DSC est utilisé pour définir une exécution DSC unique du début à la fin. Par exemple, `Test-DscConfiguration` est une opération DSC à part entière. De même, chaque autre applet de commande dans DSC (telle que `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) peut être identifiée comme une opération DSC à part entière. Les fonctions sont expliquées dans [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).
Vous accédez à l’aide en exécutant `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Obtention de détails des opérations DSC

La fonction `Get-xDscOperation` vous permet de rechercher les résultats des opérations DSC qui s’exécutent sur un ou plusieurs ordinateurs, et de retourner un objet qui contient la collection d’événements produits par chaque opération DSC.
Par exemple, dans la sortie suivante, trois commandes ont été exécutées. La première a réussi et les deux autres ont échoué. Ces résultats sont résumés dans la sortie de `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

Vous pouvez également spécifier que vous voulez uniquement les résultats des opérations les plus récentes à l’aide du paramètre `Newest` :

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>Obtention des détails des événements DSC

L’applet de commande `Trace-xDscOperation`retourne un objet qui contient une collection d’événements, leur type et la sortie de message générée à partir d’une opération DSC particulière. En règle générale, quand vous trouvez une erreur dans une opération à l’aide de `Get-xDscOperation`, vous tracez l’opération pour déterminer lequel des événements a entraîné un échec.

Utilisez le paramètre `SequenceID` pour obtenir les événements d’une opération spécifique d’un ordinateur spécifique. Par exemple, si vous spécifiez une valeur de 9 pour `SequenceID`, `Trace-xDscOperaion` obtient la trace de la neuvième opération DSC à partir de la dernière opération :

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

Passez le **GUID** affecté à une opération DSC spécifique (comme retourné par l’applet de commande `Get-xDscOperation`) pour obtenir les détails de l’événement pour cette opération DSC :

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

Notez qu’étant donné que `Trace-xDscOperation` regroupe les événements des journaux d’analyse, de débogage et des opérations, vous êtes invité à activer ces journaux comme décrit ci-dessus.

Vous pouvez aussi collecter des informations sur les événements en enregistrant la sortie de `Trace-xDscOperation` dans une variable. Vous pouvez utiliser les commandes suivantes pour afficher tous les événements d’une opération DSC particulière.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Cette commande génère les mêmes résultats que l’applet de commande `Get-WinEvent`, comme dans la sortie ci-dessous :

```powershell
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

Idéalement, commencez par utiliser `Get-xDscOperation` pour répertorier les dernières exécutions de configuration DSC sur vos ordinateurs. Ensuite, vous pouvez examiner chaque opération (à l’aide de son ID de séquence ou de tâche) avec `Trace-xDscOperation` pour découvrir ce qu’elle a effectué en arrière-plan.

### <a name="getting-events-for-a-remote-computer"></a>Obtention des événements d’un ordinateur distant

Utilisez le paramètre `ComputerName` de l’applet de commande `Trace-xDscOperation` pour obtenir les détails des événements d’un ordinateur distant. Avant cela, vous devez créer une règle de pare-feu pour autoriser l’administration à distance sur l’ordinateur distant :

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Vous pouvez maintenant spécifier cet ordinateur dans votre appel à `Trace-xDscOperation` :

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Mes ressources ne sont pas mises à jour : comment réinitialiser le cache

Le moteur DSC met en cache les ressources implémentées comme module PowerShell pour des raisons d’efficacité. Toutefois, cela peut entraîner des problèmes quand vous créez et testez une ressource simultanément, car DSC charge la version mise en cache tant que le processus n’est pas redémarré. La seule façon pour que DSC charge la version la plus récente est d’arrêter explicitement le processus qui héberge le moteur DSC.

De même, quand vous exécutez `Start-DscConfiguration`, une fois que vous avez ajouté et modifié une ressource personnalisée, la modification peut ne pas s’exécuter tant que l’ordinateur n’est pas redémarré. Ce comportement s’explique par le fait que DSC s’exécute dans le processus hôte du fournisseur WMI (WmiPrvSE) et qu’en général, il existe plusieurs instances de WmiPrvSE qui s’exécutent simultanément. Quand vous redémarrez, le processus hôte est redémarré et le cache est effacé.

Pour recycler la configuration et effacer le cache sans redémarrer l’ordinateur, vous devez arrêter, puis redémarrer le processus hôte. Vous pouvez le faire pour chaque instance : vous identifiez le processus, l’arrêtez et le redémarrez. Vous pouvez également utiliser `DebugMode`, comme illustré ci-dessous, pour recharger la ressource DSC PowerShell.

Pour identifier le processus qui héberge le moteur DSC et l’arrêter pour chaque instance, vous pouvez répertorier les ID de processus de WmiPrvSE, qui héberge le moteur DSC. Ensuite, pour mettre à jour le fournisseur, arrêtez le processus WmiPrvSE à l’aide des commandes ci-dessous, puis exécutez **Start-DscConfiguration** de nouveau.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a>Utilisation de DebugMode

Vous pouvez configurer le gestionnaire de configuration local DSC de façon à utiliser `DebugMode` pour toujours effacer le cache lors du redémarrage du processus hôte. Quand la valeur est **TRUE**, elle force le moteur à toujours recharger la ressource DSC PowerShell. Une fois que vous avez écrit votre ressource, vous pouvez la redéfinir avec la valeur **FALSE** pour que le moteur mette de nouveau en cache les modules.

La démonstration suivante explique comment `DebugMode` peut actualiser le cache de façon automatique. Tout d’abord, examinons la configuration par défaut :

```
PS C:\> Get-DscLocalConfigurationManager


AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : False
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

Vous pouvez voir que `DebugMode` a la valeur **FALSE**.

Pour configurer la démonstration de `DebugMode`, utilisez la ressource PowerShell suivante :

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

Maintenant, créez une configuration à l’aide de la ressource ci-dessus et appelez-la `TestProviderDebugMode` :

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Le contenu du fichier : «  **$env:SystemDrive\OutputFromTestProviderDebugMode.txt** » est **1**.

Ensuite, mettez à jour le code du fournisseur à l’aide du script suivant :

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Ce script génère un nombre aléatoire et met à jour le code du fournisseur en conséquence. Quand `DebugMode` a la valeur false, le contenu du fichier «  **$env:SystemDrive\OutputFromTestProviderDebugMode.txt** » est toujours le même.

À présent, définissez `DebugMode` avec la valeur **TRUE** dans votre script de configuration :

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

Quand vous réexécutez le script ci-dessus, le contenu du fichier change à chaque fois. (Vous pouvez exécuter `Get-DscConfiguration` pour le vérifier.) Voici le résultat de deux exécutions supplémentaires (les résultats peuvent être différents quand vous exécutez le script) :

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a>Voir aussi

### <a name="reference"></a>Référence

- [Ressource Log dans DSC](logResource.md)

### <a name="concepts"></a>Concepts

- [Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell](authoringResource.md)

### <a name="other-resources"></a>Autres ressources

- [Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)