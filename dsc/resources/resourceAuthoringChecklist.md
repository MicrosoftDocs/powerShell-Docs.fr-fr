---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Liste de vérification de création de ressources
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401563"
---
# <a name="resource-authoring-checklist"></a>Liste de vérification de création de ressources

Cette liste de vérification est une liste de bonnes pratiques lors de la création d’une ressource DSC.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Le module de ressources contient le fichier .psd1 et schema.mof pour chaque ressource

Vérifiez que votre ressource a une structure correcte et qu’elle contient tous les fichiers nécessaires. Chaque module de ressources doit contenir un fichier .psd1 et toutes les ressources non composites doivent avoir un fichier schema.mof. Les ressources qui ne contiennent pas de schéma ne seront pas répertoriées par `Get-DscResource` et les utilisateurs ne pourront pas utiliser Intellisense lors de l’écriture de code impliquant ces modules dans ISE.
La structure de répertoires de la ressource xRemoteFile, qui fait partie du [module de ressources xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), se présente comme suit :

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>La ressource et le schéma sont corrects

Vérifiez le fichier de schéma de ressource (*.schema.mof). Vous pouvez utiliser le [Concepteur de ressources DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) pour développer et tester votre schéma.
Vérifiez que :

- Les types de propriétés sont corrects (par exemple, n’utilisez pas String pour les propriétés qui acceptent des valeurs numériques ; utilisez plutôt UInt32 ou d’autres types numériques).
- Les attributs de propriétés sont spécifiés correctement en tant que ([key], [required], [write], [read])
- Au moins un paramètre dans le schéma doit être marqué comme [key].
- La propriété [read] ne coexiste pas avec [required], [key] ni [write]
- Si plusieurs qualificateurs sont spécifiés, à l’exception de [read], [key] est prioritaire.
- Si [write] et [required] sont spécifiés, [required] est prioritaire.
- ValueMap est spécifié, le cas échéant. Exemple :

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Le nom convivial est spécifié et conforme aux conventions d’affectation de noms DSC.

  Exemple : `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Chaque champ a une description explicite. Le dépôt GitHub de PowerShell présente des exemples intéressants, tel que [le fichier .schema.mof pour xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Vous devez aussi utiliser les applets de commande **Test-xDscResource** et **Test-xDscSchema** à partir du [Concepteur de ressources DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) pour vérifier automatiquement la ressource et le schéma :

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Par exemple :

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>La ressource se charge sans erreur

Vérifiez si le module de ressources peut être chargé.
Vous pouvez le faire soit manuellement, en exécutant `Import-Module <resource_module> -force` et en vérifiant qu’aucune erreur ne s’est produite, soit en écrivant une automatisation de test. Dans le deuxième cas, vous pouvez suivre cette structure dans votre cas de test :

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>La ressource est idempotent dans le cas positif

Une des caractéristiques fondamentales des ressources de DSC est l’idempotence. Cela signifie que l’application d’une configuration DSC contenant cette ressource plusieurs fois aboutit toujours au même résultat. Par exemple, si nous créons une configuration qui contient la ressource de fichier suivante :

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Après une première application, le fichier test.txt doit apparaître dans le dossier `C:\test`. Toutefois, les exécutions suivantes de la même configuration ne doivent pas changer l’état de l’ordinateur (par exemple, aucune copie du fichier `test.txt` ne doit être créée).
Pour vérifier qu’une ressource est idempotente, vous pouvez appeler `Set-TargetResource` à plusieurs reprises lors de tests directs de la ressource, ou appeler `Start-DscConfiguration` à plusieurs reprises lors de tests de bout en bout. Le résultat doit être le même après chaque exécution.

## <a name="test-user-modification-scenario"></a>Scénario de modification par l’utilisateur de test

En changeant l’état de l’ordinateur, puis en réexécutant DSC, vous pouvez vérifier que `Set-TargetResource` et `Test-TargetResource` fonctionnent correctement. Voici les étapes à suivre :

1. Commencez avec la ressource qui n’est pas à l’état souhaité.
2. Exécutez la configuration avec votre ressource.
3. Vérifiez que `Test-DscConfiguration` retourne la valeur True.
4. Modifiez l’élément configuré pour qu’il ne soit plus dans l’état souhaité
5. Vérifiez que `Test-DscConfiguration` retourne la valeur False.

Voici un exemple plus concret à l’aide de la ressource de Registre :

1. Commencez avec la clé de Registre qui n’est pas à l’état souhaité.
2. Exécutez `Start-DscConfiguration` avec une configuration pour la faire basculer à l’état souhaité et vérifiez que l’opération réussit.
3. Exécutez `Test-DscConfiguration` et vérifiez qu’elle retourne la valeur True.
4. Modifiez la valeur de la clé pour qu’elle ne soit pas à l’état souhaité.
5. Exécutez `Test-DscConfiguration` et vérifiez qu’elle retourne la valeur False.
6. La fonctionnalité `Get-TargetResource` a été vérifiée à l’aide de `Get-DscConfiguration`.

`Get-TargetResource` doit retourner des détails sur l’état actuel de la ressource. Testez-la en appelant `Get-DscConfiguration` après avoir appliqué la configuration et en vérifiant que la sortie reflète fidèlement l’état actuel de l’ordinateur. Il est important de la tester séparément, car les problèmes dans cette zone ne s’affichent pas lors de l’appel de `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Appelez les fonctions **Get/Set/Test-TargetResource** directement

Testez les fonctions **Get/Set/Test-TargetResource** implémentées dans votre ressource en les appelant directement et en vérifiant qu’elles fonctionnent comme prévu.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Effectuez une vérification de bout en bout à l’aide de **Start-DscConfiguration**

Le test des fonctions **Get/Set/Test-TargetResource** en les appelant directement est important, mais les problèmes ne sont pas tous découverts de cette façon. Vous devez axer une partie importante de vos tests sur l’utilisation de `Start-DscConfiguration` ou du serveur collecteur. En fait, c’est de cette manière que les utilisateurs se serviront de la ressource. Ne sous-estimez donc pas l’importance de ce type de test.
Types de problèmes possibles :

- Les informations d’identification ou la session peuvent se comporter différemment, car l’agent DSC s’exécute en tant que service.  Veillez à tester ici toutes les fonctionnalités de bout en bout.
- Les erreurs générées par `Start-DscConfiguration` peuvent être différentes de celles affichées quand vous appelez directement la fonction `Set-TargetResource`.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Compatibilité des tests sur toutes les plateformes prises en charge DSC

La ressource doit fonctionner sur toutes les plateformes prises en charge par DSC (Windows Server 2008 R2 et versions ultérieures). Installez la dernière version de WMF (Windows Management Framework) sur votre système d’exploitation pour obtenir la dernière version de DSC. Si la ressource ne fonctionne pas sur certaines de ces plateformes de par sa conception, un message d’erreur spécifique doit être retourné. Veillez aussi à ce que votre ressource vérifie si les applets de commande que vous appelez sont présentes sur un ordinateur particulier. Windows Server 2012 a ajouté un grand nombre de nouvelles applets de commande qui ne sont pas disponibles sur Windows Server 2008 R2, même avec WMF installé.

## <a name="verify-on-windows-client-if-applicable"></a>Effectuez une vérification sur le client Windows (le cas échéant)

L’une des erreurs courantes lors des tests consiste à vérifier la ressource uniquement sur les versions de Windows Server. De nombreuses ressources sont également conçues pour fonctionner sur des références (SKU) clientes. Si cela vous concerne, n’oubliez pas de les tester également sur ces plateformes.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource répertorie la ressource

Après le déploiement du module, un appel à `Get-DscResource` doit répertorier votre ressource parmi les autres. Si votre ressource ne figure pas dans la liste, vérifiez que le fichier schema.mof correspondant à cette ressource existe.

## <a name="resource-module-contains-examples"></a>Le module de ressource contient des exemples

La création d’exemples de qualité aidera les autres à comprendre comment l’utiliser. C’est crucial, surtout quand on sait que de nombreux utilisateurs traitent les exemples de code comme de la documentation.

- Tout d’abord, vous devez déterminer les exemples qui seront inclus dans le module : au minimum, vous devez couvrir les cas d’usage les plus importants pour votre ressource :
- Si votre module contient plusieurs ressources qui doivent fonctionner ensemble pour un scénario de bout en bout, l’exemple de bout en bout de base doit, dans l’idéal, être le premier.
- Les exemples initiaux doivent être très simples : prise en main de vos ressources en petits segments gérables (par exemple création d’un disque dur virtuel).
- Les exemples suivants doivent reposer sur ces exemples (création d’une machine virtuelle à partir d’un disque dur virtuel, suppression de machine virtuelle, modification de machines virtuelles, etc.) et illustrer les fonctionnalités avancées (comme la création d’une machine virtuelle avec mémoire dynamique).
- Les exemples de configuration doivent être paramétrés (toutes les valeurs doivent être passées à la configuration comme paramètres et il ne doit y avoir aucune valeur codée en dur) :

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- Il est recommandé d’inclure un exemple (en commentaire) illustrant comment appeler la configuration avec les valeurs réelles à la fin de l’exemple de script.
  Par exemple, dans la configuration ci-dessus, il n’est pas évident pour tout le monde que le meilleur moyen de spécifier UserAgent est :

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Dans ce cas, un commentaire peut clarifier l’exécution prévue de la configuration :

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Pour chaque exemple, rédigez une brève description qui explique ce qu’il fait et la signification des paramètres.
- Vérifiez que les exemples couvrent la plupart des principaux scénarios pour votre ressource et, si aucun élément ne manque, vérifiez qu’ils s’exécutent tous et qu’ils placent l’ordinateur à l’état souhaité.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Les messages d’erreur sont faciles à comprendre et aident les utilisateurs à résoudre les problèmes

Pour être efficaces, les messages d’erreur doivent être :

- Présents : Le plus gros problème avec les messages d’erreur est qu’ils n’existent pas souvent, assurez-vous qu’ils s’y.
- Facile à comprendre : Codes d’erreur humaine de lisible, n’obscurs
- Précise Décrire ce qu’est exactement le problème
- Constructifs : Conseils pour résoudre le problème
- Poli : Ne pas rendre responsable utilisateur ou rendre vous inquiétez pas

Vérifiez les erreurs dans les scénarios de bout en bout (à l’aide de `Start-DscConfiguration`), car elles peuvent différer de celles retournées lors de l’exécution directe des fonctions de ressources.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Les messages de journaux sont faciles à comprendre et informatifs (notamment les journaux –verbose, –debug et ETW)

Vérifiez que les journaux générés par la ressource sont faciles à comprendre et sont utiles à l’utilisateur. Les ressources doivent générer toutes les informations qui peuvent être utiles à l’utilisateur, mais il n’est pas toujours préférable de fournir davantage de journaux. Vous devez éviter de créer des redondances et des données qui n’apportent rien de plus. Ne forcez pas un utilisateur à parcourir des centaines d’entrées de journaux pour trouver ce qu’il cherche. Bien entendu, ne proposer aucun journal n’est pas non plus une solution acceptable pour ce problème.

Pendant les tests, vous devez aussi analyser les journaux détaillés et les journaux de débogage (en exécutant `Start-DscConfiguration` avec les commutateurs `–Verbose` et `–Debug` le cas échéant), ainsi que les journaux ETW. Pour afficher les journaux ETW de DSC, accédez à l’Observateur d’événements et ouvrez le dossier suivant : Applications et Services Microsoft - Windows - Desired State Configuration.  Par défaut le canal Opérationnel est activé, mais veillez à activer également les canaux Analyse et Débogage avant d’exécuter la configuration.
Pour activer les canaux Analyse/Débogage, vous pouvez exécuter le script ci-dessous :

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>L’implémentation de la ressource ne contient pas de chemins codés en dur

Vérifiez qu’il n’y a aucun chemin codé en dur dans l’implémentation de la ressource, en particulier s’ils définissent la langue (en-us) par supposition, ou quand des variables système peuvent être utilisées.
Si votre ressource a besoin d’accéder à des chemins spécifiques, utilisez des variables d’environnement au lieu de coder en dur le chemin, car il peut différer sur d’autres ordinateurs.

Exemple :

Au lieu de :

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Vous pouvez écrire :

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>L’implémentation de ressource ne contient pas d’informations sur l’utilisateur

Vérifiez que le code ne contient aucune adresse de messagerie, information de compte ou nom d’utilisateur.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>La ressource a été testée avec des informations d’identification valides ou non valides

Si votre ressource prend des informations d’identification en tant que paramètre :

- Vérifiez que la ressource fonctionne quand Système local (ou le compte d’ordinateur pour les ressources distantes) n’a pas accès.
- Vérifiez que la ressource fonctionne avec des informations d’identification spécifiées pour Get, Set et Test
- Si votre ressource accède à des partages, testez toutes les variantes que vous devez prendre en charge, par exemple :
  - Partages Windows standard.
  - Partages DFS.
  - Partages SAMBA (si vous souhaitez prendre en charge Linux.)

## <a name="resource-does-not-require-interactive-input"></a>La ressource ne nécessite pas d’entrée interactive

Les fonctions **Get/Set/Test-TargetResource** doivent être exécutées automatiquement et ne doivent attendre une entrée utilisateur à aucun moment de l’exécution (par exemple, vous ne devez pas utiliser `Get-Credential` à l’intérieur de ces fonctions). Si vous avez besoin de fournir une entrée utilisateur, vous devez la passer à la configuration en tant que paramètre pendant la phase de compilation.

## <a name="resource-functionality-was-thoroughly-tested"></a>La fonctionnalité de la ressource a été testée de manière approfondie

Cette liste de vérification contient des éléments qu’il est important de tester et/ou qui sont souvent oubliés. Il y aura plusieurs séries de tests, principalement des tests fonctionnels propres à la ressource que vous testez et qui ne sont pas mentionnés ici. N’oubliez pas les cas de tests négatifs.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Bonne pratique Module de ressources contient un dossier Tests avec un script ResourceDesignerTests.ps1

Il est conseillé de créer un dossier « Tests » à l’intérieur du module de ressources, de créer un fichier `ResourceDesignerTests.ps1` et d’ajouter des tests à l’aide de **Test-xDscResource** et **Test-xDscSchema** pour toutes les ressources d’un module donné.
De cette façon, vous pouvez valider rapidement les schémas de toutes les ressources des modules donnés et effectuer des tests d’intégrité avant la publication.
Pour xRemoteFile, `ResourceTests.ps1` pourrait être aussi simple que ceci :

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Bonne pratique Dossier de ressources contient le script de Concepteur de ressources pour générer le schéma

Chaque ressource doit contenir un script de concepteur de ressources qui génère un schéma mof de la ressource. Ce fichier doit être placé dans `<ResourceName>\ResourceDesignerScripts` et nommé Generate`<ResourceName>Schema.ps1`. Pour la ressource xRemoteFile, ce fichier se nommerait `GenerateXRemoteFileSchema.ps1` et contiendrait :

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a>Bonne pratique Ressource prend en charge - WhatIf

Si votre ressource effectue des opérations « dangereuses », nous vous recommandons d’implémenter une fonctionnalité `-WhatIf`. Une fois ceci effectué, vérifiez que la sortie `-WhatIf` décrit correctement les opérations qui auraient lieu si la commande était exécutée sans commutateur `-WhatIf`.
Vérifiez également que les opérations ne s’exécutent pas (l’état du nœud n’est pas modifié) quand le commutateur `–WhatIf` est présent.
Par exemple, supposons que nous testons la ressource File. Voici une configuration simple qui crée un fichier `test.txt` avec le contenu « test » :

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

Si nous compilons et exécutons la configuration avec le commutateur `-WhatIf`, la sortie nous indique exactement ce qui se passera si nous exécutons la configuration. Toutefois, la configuration proprement dite n’a pas été exécutée (le fichier `test.txt` n’a pas été créé).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Cette liste n’est pas exhaustive, mais elle traite de nombreux problèmes importants qui peuvent se poser lors de la conception, du développement et des tests des ressources DSC.
