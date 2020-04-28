---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Création d’un pipeline d’intégration continue et de déploiement continu avec DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954236"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Création d’un pipeline d’intégration continue et de déploiement continu avec DSC

Cet exemple montre comment créer un pipeline d’intégration continue/déploiement continu (CI/CD) à l’aide de PowerShell, DSC, Pester et Visual Studio Team Foundation Server (TFS).

Une fois le pipeline est créé et configuré, vous pouvez l’utiliser pour totalement déployer, configurer et tester un serveur DNS et ses enregistrements d’hôte associés.
Ce processus simule la première partie d’un pipeline qui sera utilisée dans un environnement de développement.

Un pipeline CI/CD automatisé vous permet de mettre à jour les logiciels avec plus de rapidité et de fiabilité, garantissant que tout le code est testé et qu’une version actuelle de votre code est disponible à tout moment.

## <a name="prerequisites"></a>Prérequis

Pour utiliser cet exemple, vous devez maîtriser les éléments suivants :

- Les concepts CI-CD. Le [modèle de pipeline de mise en production](https://aka.ms/thereleasepipelinemodelpdf) constitue une bonne référence.
- Contrôle de source [Git](https://git-scm.com/)
- L’infrastructure de test [Pester](https://github.com/pester/Pester)
- [Team Foundation Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin

Pour générer et exécuter cet exemple, vous aurez besoin d’un environnement comportant plusieurs ordinateurs et/ou machines virtuelles.

### <a name="client"></a>Client

Il s’agit de l’ordinateur sur lequel vous allez effectuer toutes les tâches pour configurer et exécuter l’exemple.

L’ordinateur client doit être un ordinateur Windows avec les éléments suivants :

- [Git](https://git-scm.com/)
- référentiel git local cloné à partir de https://github.com/PowerShell/Demo_CI
- un éditeur de texte, par exemple [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

L’ordinateur qui héberge le serveur TFS sur lequel vous allez définir votre build et votre version.
[Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) doit être installé sur cet ordinateur.

### <a name="buildagent"></a>BuildAgent

L’ordinateur qui exécute l’agent de build Windows qui crée le projet.
Un agent de build doit être installé et en cours d’exécution sur cet ordinateur.
Consultez [Déployer un agent sur Windows](/azure/devops/pipelines/agents/v2-windows) pour savoir comment installer et exécuter un agent de build Windows.

Vous devez également installer les modules DSC `xDnsServer` et `xNetworking` sur cet ordinateur.

### <a name="testagent1"></a>TestAgent1

Il s’agit de l’ordinateur configuré comme serveur DNS par la configuration DSC dans cet exemple.
L’ordinateur doit exécuter [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Il s’agit de l’ordinateur qui héberge le site Web que cet exemple configure.
L’ordinateur doit exécuter [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Ajouter le code à TFS

Nous commencerons par créer un référentiel Git dans TFS, puis nous importerons le code de votre référentiel local vers l’ordinateur client.
Si vous n’avez pas déjà cloné le référentiel Demo_CI sur votre ordinateur client, faites-le maintenant en exécutant la commande git suivante :

`git clone https://github.com/PowerShell/Demo_CI`

1. Sur votre ordinateur client, accédez à votre serveur TFS dans un navigateur web.
1. Dans TFS, [créez un nouveau projet d’équipe](/azure/devops/organizations/projects/create-project) intitulé Demo_CI.

   Assurez-vous que l’option **Contrôle de version** est définie sur **Git**.
1. Sur votre ordinateur client, ajoutez un accès à distance au référentiel que vous venez de créer dans TFS avec la commande suivante :

   `git remote add tfs <YourTFSRepoURL>`

   Où `<YourTFSRepoURL>` est le clone de l’URL dans le référentiel TFS que vous avez créé à l’étape précédente.

   Si vous ne savez pas où trouver cette URL, consultez [Cloner un référentiel Git existant](/azure/devops/repos/git/clone).
1. Transmettez le code de votre référentiel local à votre référentiel TFS avec la commande suivante :

   `git push tfs --all`
1. Le référentiel TFS contiendra le code Demo_CI.

> [!NOTE]
> Cet exemple utilise le code de la branche `ci-cd-example` du dépôt Git.
> Veillez à spécifier cette branche en tant que branche par défaut dans votre projet TFS, et pour les déclencheurs CI/CD que vous créez.

## <a name="understanding-the-code"></a>Présentation du code

Avant de créer les pipelines de build et de déploiement, examinons le code pour comprendre ce qui se passe.
Sur votre ordinateur client, ouvrez votre éditeur de texte favori et accédez à la racine de votre référentiel Git Demo_CI.

### <a name="the-dsc-configuration"></a>La configuration DSC

Ouvrez le fichier `DNSServer.ps1` (depuis la racine du référentiel local Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`).

Ce fichier contient la configuration DSC qui configure le serveur DNS. Le voici dans son intégralité :

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Notez l’instruction `Node` :

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Elle recherche tous les nœuds qui ont été définis comme ayant un rôle de `DNSServer` dans les [données de configuration](../configurations/configData.md), créées par le script `DevEnv.ps1`.

Vous pouvez en savoir plus sur la méthode `Where` dans [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

Il est important d’utiliser les données de configuration pour définir des nœuds lors de l’opération CI car les informations sur les nœuds sont susceptibles de changer entre les environnements, et ces données de configuration vous permet de modifier facilement les informations des nœuds sans modifier le code de la configuration.

Dans le premier bloc de ressources, la configuration appelle **WindowsFeature** pour s’assurer que la fonctionnalité DNS est activée.
Les blocs de ressources qui suivent appellent des ressources à partir du module [xDnsServer](https://github.com/PowerShell/xDnsServer) pour configurer la zone principale et les enregistrements DNS.

Notez que les deux blocs `xDnsRecord` sont encapsulés dans des boucles `foreach` qui forment une itération via des tableaux dans les données de configuration.
Là encore, les données de configuration sont créées par le script `DevEnv.ps1`, ce que allons examiner maintenant.

### <a name="configuration-data"></a>Données de configuration

Le fichier `DevEnv.ps1` (depuis la racine du référentiel local Demo_CI, `./InfraDNS/DevEnv.ps1`) spécifie les données de configuration spécifiques à l’environnement dans une table de hachage, puis passe cette table de hachage à un appel à la fonction `New-DscConfigurationDataDocument`, définie dans `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

Le fichier `DevEnv.ps1` :

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

La fonction `New-DscConfigurationDataDocument` (définie dans `\Assets\DscPipelineTools\DscPipelineTools.psm1`) crée par programmation un document de données de configuration à partir de la table de hachage (données du nœud) et un tableau (données non-nœud), qui sont transmis comme les paramètres `RawEnvData` et `OtherEnvData`.

Dans notre cas, seul le paramètre `RawEnvData` est utilisé.

### <a name="the-psake-build-script"></a>Le script de build psake

Le script de build [psake](https://github.com/psake/psake) défini dans `Build.ps1` (depuis la racine du référentiel Demo_CI, `./InfraDNS/Build.ps1`) définit les tâches qui font partie de la build.
Il définit également les autres tâches dont dépend chaque tâche.
Lorsqu’il est appelé, le script psake garantit que la tâche spécifiée (ou la tâche nommée `Default` si aucune tâche n’est spécifiée) s’exécute et que toutes les dépendances s’exécutent également (cette opération est récursive afin que les dépendances de dépendances s’exécutent, et ainsi de suite).

Dans cet exemple, la tâche `Default` est définie ainsi :

```powershell
Task Default -depends UnitTests
```

La tâche `Default` n’a aucune implémentation elle-même, mais a une dépendance sur la tâche `CompileConfigs`.
La chaîne de dépendances de tâches qui en résulte garantit l’exécution de toutes les tâches figurant dans le script de build.

Dans cet exemple, le script psake est appelé par un appel à `Invoke-PSake` dans le fichier `Initiate.ps1` (situé à la racine du référentiel Demo_CI) :

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Lorsque nous créons la définition de build pour notre exemple dans TFS, nous fournissons notre fichier de script psake comme paramètre `fileName` pour ce script.

Le script de build définit les tâches suivantes :

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Exécute `DevEnv.ps1`, qui génère le fichier de données de configuration.

#### <a name="installmodules"></a>InstallModules

Installe les modules requis par la configuration `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Appelle [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Exécute les tests unitaires [Pester](https://github.com/pester/Pester/wiki).

#### <a name="compileconfigs"></a>CompileConfigs

Compile la configuration (`DNSServer.ps1`) dans un fichier MOF, en utilisant les données de configuration générées par la tâche `GenerateEnvironmentFiles`.

#### <a name="clean"></a>Clean

Crée les dossiers utilisés pour l’exemple, puis supprime les résultats des tests, les fichiers de données de configuration et les modules des exécutions précédentes.

### <a name="the-psake-deploy-script"></a>Le script de déploiement psake

Le script de déploiement [psake](https://github.com/psake/psake) défini dans `Deploy.ps1` (depuis la racine du référentiel Demo_CI, `./InfraDNS/Deploy.ps1`) définit les tâches qui déploient et exécutent la configuration.

`Deploy.ps1` définit les tâches suivantes :

#### <a name="deploymodules"></a>DeployModules

Démarre une session PowerShell sur `TestAgent1` et installe les modules contenant les ressources DSC requises pour la configuration.

#### <a name="deployconfigs"></a>DeployConfigs

Appelle l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) pour exécuter la configuration sur `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Exécute les tests d’intégration [Pester](https://github.com/pester/Pester/wiki).

#### <a name="acceptancetests"></a>AcceptanceTests

Exécute les tests d’acceptation [Pester](https://github.com/pester/Pester/wiki).

#### <a name="clean"></a>Clean

Supprime tous les modules installés lors des exécutions précédentes et garantit l’existence du dossier de résultats de test.

### <a name="test-scripts"></a>Scripts de tests

Les tests d’acceptation, d’intégration et unitaires sont définis dans les scripts du dossier `Tests` (depuis la racine du référentiel Demo_CI, `./InfraDNS/Tests`), puis placés dans des fichiers nommés `DNSServer.tests.ps1` dans leurs dossiers respectifs.

Les scripts de test utilisent la syntaxe [Pester](https://github.com/pester/Pester/wiki) et [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="unit-tests"></a>Tests unitaires

Les tests unitaires testent les configurations DSC elles-mêmes pour s’assurer que les configurations exécuteront les tâches prévues.
Le script de test unitaire utilise la syntaxe [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Tests d’intégration

Les tests d’intégration testent la configuration du système pour s’assurer, le système est configuré comme prévu lors de son intégration avec d’autres composants. Ces tests sont exécutés sur le nœud cible après que ce dernier a été configuré avec DSC.
Le script de test d’intégration utilise une combinaison des syntaxes [Pester](https://github.com/pester/Pester/wiki) et [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="acceptance-tests"></a>Tests d’acceptation

Les tests d’acceptation testent le système pour s’assurer qu’il se comporte comme prévu.
Par exemple, ils vérifient qu'une page web renvoie les informations appropriées lorsqu’elle est interrogée.
Ces tests sont exécutés à distance à partir du nœud cible afin de tester des scénarios en conditions réelles.
Le script de test d’intégration utilise une combinaison des syntaxes [Pester](https://github.com/pester/Pester/wiki) et [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

## <a name="define-the-build"></a>Définir la build

Maintenant que nous avons chargé notre code sur TFS et examiné son comportement, nous allons définir notre build.

Ici, nous aborderons uniquement les étapes de build que vous ajouterez à la build. Pour obtenir des instructions sur la création d’une définition de build dans TFS, consultez [Créer et mettre en file d’attente une définition de build](/azure/devops/pipelines/create-first-pipeline).

Créez une définition de build (sélectionnez le modèle **vide**) nommée « InfraDNS ».
Ajoutez les étapes suivantes à votre définition de build :

- script PowerShell
- Publier les résultats des tests
- Copier les fichiers
- Publier l’artefact

Après avoir ajouté ces étapes de build, modifiez les propriétés de chaque étape comme suit :

### <a name="powershell-script"></a>script PowerShell

1. Définissez la propriété **Type** sur `File Path`.
1. Définissez la propriété **Chemin d'accès du script** sur `initiate.ps1`.
1. Ajoutez la valeur `-fileName build` à la propriété **Arguments**.

Cette étape de la build exécute le fichier `initiate.ps1`, qui appelle le script de build psake.

### <a name="publish-test-results"></a>Publier les résultats des tests

1. Définissez **Format des résultats des tests** sur `NUnit`
1. Définissez **Fichiers des résultats des tests** sur `InfraDNS/Tests/Results/*.xml`
1. Définissez **Titre de la série de tests** sur `Unit`.
1. Vérifiez que les cases **Options de contrôle** **Activé** et **Toujours exécuter** sont cochées.

Cette étape de build exécute des tests unitaires dans le script Pester que nous avons examiné précédemment, puis stocke les résultats dans le dossier `InfraDNS/Tests/Results/*.xml`.

### <a name="copy-files"></a>Copier les fichiers

1. Ajoutez chacune des lignes suivantes à **Contents** :

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Définissez **TargetFolder** sur `$(Build.ArtifactStagingDirectory)\`

Cette étape copie la build et les scripts de test dans le répertoire intermédiaire afin de pouvoir publier ces éléments comme des artefacts de build à l’étape suivante.

### <a name="publish-artifact"></a>Publier l’artefact

1. Définissez **Chemin d'accès à publier** sur `$(Build.ArtifactStagingDirectory)\`
1. Définissez **Nom de l'artefact** sur `Deploy`
1. Définissez **Type d'artefact** sur `Server`
1. Sélectionnez `Enabled` dans **Options de contrôle**

## <a name="enable-continuous-integration"></a>Activer l’intégration continue

Nous allons maintenant configurer un déclencheur qui génère le projet chaque fois qu’une modification est apportée à la branche `ci-cd-example` du référentiel git.

1. Dans TFS, cliquez sur l’onglet **Build et version**
1. Sélectionnez la définition de build `DNS Infra`, puis cliquez sur **Modifier**
1. Cliquez sur l’onglet **Déclencheurs**
1. Sélectionnez **Continuous integration (CI)** , puis `refs/heads/ci-cd-example` dans la liste déroulante de la branche
1. Cliquez sur **Enregistrer**, puis sur **OK**

Désormais, chaque modification apportée au référentiel git TFS génère une build automatisée.

## <a name="create-the-release-definition"></a>Créer la définition de version

Nous allons créer une définition de version afin de déployer le projet dans l’environnement de développement à chaque ajout de code.

Pour ce faire, ajoutez une nouvelle définition de version associée à la définition de build `InfraDNS` que vous avez créée précédemment.
Veillez à sélectionner **Continuous deployment** afin de déclencher une nouvelle version chaque fois qu’une nouvelle build est terminée.
([Que sont les pipelines de mise en production ? ](/azure/devops/pipelines/release/)) et configurez-la comme suit :

Ajoutez les étapes suivantes à la définition de version :

- script PowerShell
- Publier les résultats des tests
- Publier les résultats des tests

Modifiez les étapes comme suit :

### <a name="powershell-script"></a>script PowerShell

1. Définissez le champ **Chemin d'accès du script** sur `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Définissez le champ **Arguments** sur `-fileName Deploy`

### <a name="first-publish-test-results"></a>Première publication des résultats des tests

1. Sélectionnez `NUnit` pour le champ **Format des résultats des tests**
1. Définissez le champ **Fichiers des résultats des tests** sur `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Définissez le champ **Titre de la série de tests** sur `Integration`
1. Sous **Options de contrôle**, cochez la case **Toujours exécuter**

### <a name="second-publish-test-results"></a>Seconde publication des résultats des tests

1. Sélectionnez `NUnit` pour le champ **Format des résultats des tests**
1. Définissez le champ **Fichiers des résultats des tests** sur `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Définissez le champ **Titre de la série de tests** sur `Acceptance`
1. Sous **Options de contrôle**, cochez la case **Toujours exécuter**

## <a name="verify-your-results"></a>Vérifier les résultats

Désormais, chaque fois que vous transmettez des modifications de la branche `ci-cd-example` vers TFS, une nouvelle build démarre.
Si la build se termine correctement, un nouveau déploiement est déclenché.

Vous pouvez vérifier le résultat du déploiement en ouvrant un navigateur sur l’ordinateur client, puis en accédant à `www.contoso.com`.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple configure le serveur DNS `TestAgent1` afin que l’URL `www.contoso.com` soit résolue en `TestAgent2`, mais il ne déploie pas réellement un site Web.
Le schéma pour effectuer cette opération est fourni dans le référentiel, sous le dossier `WebApp`.
Vous pouvez utiliser les stubs fournis pour créer des scripts psake, des tests Pester et des configurations DSC afin de déployer votre propre site Web.
