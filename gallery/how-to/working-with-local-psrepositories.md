---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery, powershell, applet de commande, psgallery, psget
title: Utilisation de PSRepositories local
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619196"
---
# <a name="working-with-local-powershellget-repositories"></a>Utilisation des référentiels PowerShellGet locaux

Les référentiels de prise en charge du module PowerShellGet autre que PowerShell Gallery.
Ces applets de commande permettent les scénarios suivants :

- Prend en charge un ensemble de modules PowerShell approuvé et validé préalable pour une utilisation dans votre environnement
- Un pipeline CI/CD qui génère des modules PowerShell ou des scripts de test
- Envoyer des scripts et modules PowerShell aux systèmes qui ne peut pas accéder à internet

Cet article décrit comment configurer un référentiel PowerShell local. Cet article décrit également la [OfflinePowerShellGetDeploy][] module disponible à partir de PowerShell Gallery. Ce module contient des applets de commande pour installer la dernière version de PowerShellGet dans votre référentiel local.

## <a name="local-repository-types"></a>Types de référentiel local

Il existe deux façons de créer un PSRepository local : NuGet serveur ou partage de fichiers. Chaque type présente des avantages et des inconvénients :

Serveur NuGet

| Avantages| Inconvénients |
| --- | --- |
| Reproduit fidèlement les fonctionnalités de PowerShell Gallery | Application multiniveau requiert la planification des opérations et support |
| NuGet s’intègre à Visual Studio, les autres outils | Modèle d’authentification et de gestion des comptes NuGet nécessité |
| NuGet prend en charge les métadonnées dans `.Nupkg` packages | Publication nécessite la gestion de la clé d’API et de maintenance |
| Fournit la recherche, administration de package, etc. | |

Partage de fichiers

| Avantages| Inconvénients |
| --- | --- |
| Facile à configurer, sauvegarder et mettre à jour | Métadonnées utilisées par PowerShellGet n’est pas disponible |
| Modèle de sécurité simple - autorisations utilisateur sur le partage | Aucune interface utilisateur au-delà de partage de fichiers de base |
| Aucune contrainte telles que le remplacement des éléments existants | Une sécurité limitée et aucun enregistrement de qui ce qui met à jour |

PowerShellGet fonctionne avec le type et prend en charge la localisation des versions et l’installation de dépendance.
Toutefois, certaines fonctionnalités de PowerShell Gallery ne sont pas disponibles pour les serveurs de base de NuGet ou des partages de fichiers.

- Tout est un package - aucune distinction des scripts, modules, les ressources DSC, capacités de rôle.
- Serveurs de partage de fichiers ne peut pas voir les métadonnées du package, y compris les balises.

## <a name="creating-a-local-repository"></a>Création d’un référentiel local

L’article suivant répertorie les étapes pour configurer votre propre serveur NuGet.

- [NuGet.Server][]

Suivez les étapes jusqu’au moment de l’ajout de packages. Les étapes pour [publication d’un package](#publishing-to-a-local-repository) sont traités plus loin dans cet article.

Pour un référentiel sur le partage de fichiers, assurez-vous que vos utilisateurs disposent des autorisations pour accéder au partage de fichier.

## <a name="registering-a-local-repository"></a>L’inscription d’un référentiel local

Avant de pouvoir utiliser un référentiel, elle doit être inscrite à l’aide de la `Register-PSRepository` commande.
Dans les exemples ci-dessous, le **InstallationPolicy** a la valeur *approuvé*, sur l’hypothèse que vous faites confiance à votre propre référentiel.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Prenez note de la différence entre la façon dont les deux commandes gérer **ScriptSourceLocation**. Un fichier sur le partage de référentiels, les **SourceLocation** et **ScriptSourceLocation** doivent correspondre. Pour un référentiel sur le web, ils doivent être différents, c’est le cas dans cet exemple terminer par un « / » est ajouté à la **SourceLocation**.

Si vous souhaitez PSRepository nouvellement créé soit le référentiel par défaut, vous devez annuler l’inscription de tous les autres PSRepositories. Par exemple :

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Le nom de référentiel 'PSGallery' est réservé pour une utilisation par PowerShell Gallery. Vous pouvez annuler l’inscription PSGallery, mais vous ne pouvez pas réutiliser le nom PSGallery pour un autre référentiel.

Si vous devez restaurer le référentiel PSGallery, exécutez la commande suivante :

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publication sur un dépôt local

Une fois que vous avez inscrit PSRepository local, vous pouvez publier sur votre PSRepository local. Il existe deux principaux scénarios de publication : publication de votre propre module et publication d’un module à partir de la PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publication d’un module que vous avez créés

Utilisez `Publish-Module` et `Publish-Script` pour publier votre module sur votre PSRepository local la même façon que vous le feriez pour PowerShell Gallery.

- Spécifier l’emplacement de votre code
- Fournir une clé d’API
- Spécifiez le nom du référentiel. Par exemple, `-PSRepository LocalPSRepo`.

> [!NOTE]
> Vous devez créer un compte dans le serveur NuGet, puis connectez-vous à générer et enregistrer la clé API.
> Un partage de fichiers, utilisez n’importe quelle chaîne non vide pour la valeur NuGetApiKey.

Exemples :

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Pour garantir la sécurité, les clés de l’API ne doivent pas être codées en dur dans les scripts. Utilisez un système de gestion sécurisée des clés.

### <a name="publishing-a-module-from-the-psgallery"></a>Publication d’un module à partir de la PSGallery

Pour publier un module à partir de la PSGallery sur votre PSRepository local, vous pouvez utiliser l’applet de commande « Save-Package ».

- Spécifiez le nom du Package
- Spécifiez 'NuGet' en tant que le fournisseur
- Spécifiez l’emplacement de PSGallery en tant que le (source)https://www.powershellgallery.com/api/v2)
- Spécifiez le chemin d’accès à votre référentiel local

Exemple :

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Si votre PSRepository local est basé sur le web, il nécessite une étape supplémentaire qui utilise nuget.exe pour publier.

Consultez la documentation relative à l’aide de [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installation de PowerShellGet sur un système déconnecté

Déploiement de PowerShellGet est difficile dans les environnements qui requièrent des systèmes à être déconnecté d’internet. PowerShellGet a un processus d’amorçage qui installe la dernière version de la première fois, qu'il est utilisé. Le module OfflinePowerShellGetDeploy dans PowerShell Gallery fournit des applets de commande qui prennent en charge ce processus d’amorçage.

Pour démarrer un déploiement hors connexion, vous devez :

- Téléchargez et installez le système OfflinePowerShellGetDeploy votre connecté à internet et vos systèmes déconnectés
- Télécharger PowerShellGet et ses dépendances sur le système connecté à internet à l’aide de la `Save-PowerShellGetForOffline` applet de commande
- Copiez PowerShellGet et ses dépendances à partir du système connecté à internet au système déconnecté
- Utilisez le `Install-PowerShellGetOffline` sur le système déconnecté pour placer PowerShellGet et ses dépendances dans les dossiers appropriés

Ces commandes utilisent `Save-PowerShellGetForOffline` à placer tous les composants dans un dossier `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

À ce stade, vous devez apporter le contenu de `F:\OfflinePowerShellGet` disponible à vos systèmes déconnectés. Exécutez le `Install-PowerShellGetOffline` applet de commande pour installer PowerShellGet sur le système déconnecté.

> [!NOTE]
> Il est important que vous n’exécutez pas PowerShellGet dans la session PowerShell avant d’exécuter ces commandes. Une fois que PowerShellGet est chargé dans la session, les composants ne peuvent pas être mis à jour. Si vous ne démarrez pas par erreur PowerShellGet, quittez et redémarrez PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Après avoir exécuté ces commandes, vous êtes prêt à publier PowerShellGet dans votre référentiel local.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Pour garantir la sécurité, les clés de l’API ne doivent pas être codées en dur dans les scripts. Utilisez un système de gestion sécurisée des clés.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[NuGet.exe]: /nuget/tools/nuget-exe-cli-reference
