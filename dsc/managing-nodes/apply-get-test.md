---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Appliquer, obtenir et tester des configurations sur un nœud
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401725"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Appliquer, obtenir et tester des configurations sur un nœud

Ce guide vous explique comment travailler avec des Configurations sur une nœud cible. Ce guide est divisé en les étapes suivantes :

## <a name="apply-a-configuration"></a>Appliquer une Configuration

Pour appliquer et gérer une Configuration, nous devons générer un fichier « .mof ». Le code suivant représente une Configuration simple qui sera utilisée tout au long de ce guide.

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

Compilation de cette configuration génère deux fichiers « .mof ».

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Pour appliquer une Configuration, utilisez le [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) applet de commande. Le `-Path` paramètre spécifie un répertoire où se trouvent les fichiers « .mof ». Si aucun `-Computername` est spécifié, `Start-DSCConfiguration` tentera d’appliquer chaque Configuration pour le nom d’ordinateur spécifié par le nom du fichier « .mof » (\<computername\>.mof). Spécifiez `-Verbose` à `Start-DSCConfiguration` pour voir une sortie plus détaillée.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Si `-Wait` n’est pas spécifié, vous voyez un travail créé. Le travail créé aura une **ChildJob** pour chaque fichier « .mof » traitées par `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Si une Configuration est trop de temps et que vous souhaitez l’arrêter, vous pouvez utiliser [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) à arrêter l’application sur le nœud local.

```powershell
Stop-DSCConfiguration -Force
```

Une fois terminé, vous pouvez afficher l’état des tâches via l’objet de tâche retourné par [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

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

Pour voir les **Verbose** de sortie, utilisez les commandes suivantes pour afficher le **Verbose** stream pour chaque **ChildJob**. Pour plus d’informations sur les tâches PowerShell, consultez [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

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

À compter de PowerShell 5.0, le `-UseExisting` paramètre a été ajouté à `Start-DSCConfiguration`. En spécifiant `-UseExisting`, vous demander à l’applet de commande à utiliser la Configuration appliquée existante au lieu de celle spécifiée par la `-Path` paramètre.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Tester une Configuration

Vous pouvez tester une Configuration actuellement appliquée à l’aide [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` retournera `True` si le nœud est conforme, et `False` si elle n’est pas.

```powershell
Test-DSCConfiguration
```

À compter de PowerShell 5.0, le `-Detailed` paramètre a été ajouté, qui retourne un objet avec des collections de **ResourcesInDesiredState** et **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

À compter de PowerShell 5.0, vous pouvez tester une Configuration sans l’appliquer. Le `-ReferenceConfiguration` paramètre accepte le chemin d’accès d’un fichier « .mof » pour tester le nœud par rapport. Ne **définir** actions sont effectuées sur le nœud. Dans PowerShell 4.0, il existe des solutions de contournement pour tester une Configuration sans l’appliquer, mais ils ne sont pas abordées ici.

## <a name="get-configuration-values"></a>Obtenir les valeurs de Configuration

Le [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) applet de commande renvoie les valeurs actuelles de toutes les ressources configurées dans la Configuration actuellement appliquée.

```powershell
Get-DSCConfiguration
```

Sortie à partir de notre exemple de Configuration ressemblerait à ceci si appliquées avec succès.

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

## <a name="get-configuration-status"></a>Obtenir l’état de Configuration

À compter de PowerShell 5.0 le [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) applet de commande vous permet de consulter l’historique des Configurations appliquées au nœud. PowerShell DSC effectue le suivi des {{N}} dernières Configurations appliquées dans **Push** ou **extraire** mode. Cela inclut tous *cohérence* vérifications exécutées par le Gestionnaire de configuration local. Par défaut, `Get-DSCConfigurationStatus` vous montre uniquement la dernière entrée de l’historique.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Utilisez le `-All` paramètre pour afficher tous les historique d’état de la Configuration.

> [!NOTE]
> Sortie est tronquée par souci de concision.

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

## <a name="manage-configuration-documents"></a>Gérer des Documents de Configuration

Le LCM gère la Configuration du nœud en travaillant avec **Documents de Configuration**. Ces fichiers « .mof » se trouvent dans le répertoire « C:\Windows\System32\Configuration ».

À compter de PowerShell 5.0 le [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) vous permet de supprimer les fichiers « .mof » pour arrêter les vérifications de cohérence futures ou de supprimer une Configuration qui comporte des erreurs lorsqu’il est appliqué. Le `-Stage` paramètre permet de spécifier le fichier « .mof » que vous souhaitez supprimer.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> Dans PowerShell 4.0, vous pouvez toujours supprimer ces fichiers « .mof » directement à l’aide [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publier des Configurations

À compter de PowerShell 5.0, le [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) applet de commande a été ajoutée. Cette applet de commande vous permet de publier un fichier « .mof » à des ordinateurs distants sans l’appliquer.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Voir aussi

- [Méthodes Get, Test et Set](../resources/get-test-set.md)
