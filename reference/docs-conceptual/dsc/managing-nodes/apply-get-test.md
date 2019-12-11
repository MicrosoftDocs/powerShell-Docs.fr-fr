---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Appliquer, obtenir et tester des configurations sur un nœud
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953836"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Appliquer, obtenir et tester des configurations sur un nœud

Ce guide vous explique comment utiliser des configurations sur un nœud cible. Ce guide se compose des étapes suivantes :

## <a name="apply-a-configuration"></a>Appliquer une configuration

Pour appliquer et gérer une configuration, nous devons générer un fichier « .mof ». Le code suivant représentera une configuration simple qui sera utilisée tout au long de ce guide.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

La compilation de cette configuration générera deux fichiers « .mof ».

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Pour appliquer une configuration, utilisez l’applet de commande [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). Le paramètre `-Path` spécifie un répertoire où se trouvent les fichiers « .mof ». Si aucune valeur `-Computername` n’est spécifiée, `Start-DSCConfiguration` tentera d’appliquer chaque configuration au nom d’ordinateur spécifié par le nom du fichier « .mof » (\<computername\>.mof). Définissez `-Verbose` sur `Start-DSCConfiguration` pour afficher un résultat plus détaillé.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Si la valeur `-Wait` n’est pas spécifiée, une tâche est créée. La tâche créée aura une propriété **ChildJob** pour chaque fichier « .mof » traité par `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Si l’exécution d’une configuration prend trop de temps et que vous souhaitez l’arrêter, vous pouvez utiliser [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) pour arrêter l’application sur le nœud local.

```powershell
Stop-DSCConfiguration -Force
```

Une fois l’opération terminée, vous pouvez afficher l’état des tâches via l’objet de tâche retourné par [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Pour afficher le résultat **Détaillé**, utilisez les commandes suivantes pour afficher le flux **Détaillé** pour chaque **ChildJob**. Pour plus d’informations sur les tâches PowerShell, consultez [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

À compter de PowerShell 5.0, le paramètre `-UseExisting` a été ajouté à `Start-DSCConfiguration`. En spécifiant `-UseExisting`, vous demandez à l’applet de commande d’utiliser la configuration appliquée existante au lieu de celle spécifiée par le paramètre `-Path`.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Tester une configuration

Vous pouvez tester une configuration actuellement appliquée à l’aide de [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` retournera `True` si le nœud est conforme, et `False` dans le cas contraire.

```powershell
Test-DSCConfiguration
```

À compter de PowerShell 5.0, le paramètre `-Detailed` a été ajouté et retourne un objet avec des collections pour **ResourcesInDesiredState** et **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

À compter de PowerShell 5.0, vous pouvez tester une configuration sans l’appliquer. Le paramètre `-ReferenceConfiguration` accepte le chemin d’accès d’un fichier « .mof » pour tester le nœud. Aucune action de type **Set** n’est appliquée au nœud. PowerShell 4.0 propose des solutions de contournement pour tester une configuration sans l’appliquer, mais elles ne sont pas présentées ici.

## <a name="get-configuration-values"></a>Obtenir les valeurs de la configuration

L’applet de commande [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) renvoie les valeurs actuelles de toutes les ressources configurées dans la configuration actuellement appliquée.

```powershell
Get-DSCConfiguration
```

Le résultat de notre exemple de configuration ressemblerait à ceci si cette configuration est appliquée avec succès.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Obtenir l’état de la configuration

À compter de PowerShell 5.0, l’applet de commande [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) vous permet de consulter l’historique des configurations appliquées au nœud. PowerShell DSC effectue le suivi des {{N}} dernières configurations appliquées en mpde **Push** ou **Pull**. Cela inclut toutes les vérifications de *cohérence* exécutées par le gestionnaire de configuration local (LCM). Par défaut, `Get-DSCConfigurationStatus` vous montre uniquement la dernière entrée de l’historique.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Utilisez le paramètre `-All` pour afficher tout l’historique des états de la configuration.

> [!NOTE]
> Le résultat est tronqué par souci de concision.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Gérer des documents de configuration

Le LCM gère la configuration du nœud à l’aide de **documents de configuration**. Ces fichiers « .mof » se trouvent dans le répertoire "C:\Windows\System32\Configuration".

À compter de PowerShell 5.0, [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) vous permet de supprimer les fichiers « .mof » pour arrêter les futures vérifications de cohérence ou pour supprimer une configuration dont l’application entraîne des erreurs. Le paramètre `-Stage` permet de spécifier le fichier « .mof » que vous souhaitez supprimer.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> Dans PowerShell 4.0, vous pouvez toujours supprimer ces fichiers « .mof » directement à l’aide de [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publier les configurations

À compter de PowerShell 5.0, l’applet de commande [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) a été ajoutée. Cette applet de commande vous permet de publier un fichier « .mof » sur des ordinateurs distants, sans l’appliquer.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Voir aussi

- [Méthodes Get, Test et Set](../resources/get-test-set.md)
