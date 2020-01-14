---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery, powershell, applet de commande, psgallery, psget
title: Travailler avec des PSRepository locaux
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415820"
---
# <a name="working-with-private-powershellget-repositories"></a>Utilisation des référentiels PowerShellGet privés

Le module PowerShellGet prend en charge des référentiels autres que PowerShell Gallery.
Ces cmdlets gèrent les cas suivants :

- prise en charge d’un ensemble approuvé et prévalidé de modules PowerShell dans l’environnement ;
- test d’un pipeline CI/CD qui génère des modules ou des scripts PowerShell ;
- envoi de scripts et de modules PowerShell aux systèmes qui n’ont pas accès à Internet.
- Fournir des scripts et des modules PowerShell accessibles uniquement à votre organisation

Cet article explique comment configurer un référentiel PowerShell local. Il aborde également le module [OfflinePowerShellGetDeploy][] disponible sur PowerShell Gallery. Ce module contient des cmdlets permettant d’installer la dernière version de PowerShellGet dans un référentiel local.

## <a name="local-repository-types"></a>Types de référentiels locaux

Il existe deux moyens de créer un PSRepository local : un serveur NuGet ou un partage de fichiers. Chacun présente des avantages et des inconvénients :

### <a name="nuget-server"></a>Serveur NuGet

| Avantages| Inconvénients |
| --- | --- |
| Reproduction fidèle des fonctionnalités de PowerShell Gallery | Application multiniveau exigeant planification des opérations et support |
| Intégration de NuGet à Visual Studio, autres outils | Modèle d’authentification et gestion des comptes NuGet nécessaires |
| NuGet prend en charge les métadonnées dans les packages `.Nupkg` | Gestion de clés API et maintenance nécessaires à la publication |
| Fonctionnalités de recherche, d’administration de packages, etc. | |

### <a name="file-share"></a>Partage de fichiers

| Avantages| Inconvénients |
| --- | --- |
| Facilité de configuration, de sauvegarde et de maintenance | Indisponibilité des métadonnées utilisées par PowerShellGet |
| Simplicité du modèle de sécurité (autorisations utilisateur sur le partage) | Pas d’interface utilisateur au-delà du partage de fichiers de base |
| Pas de contraintes comme le remplacement des éléments existants | Sécurité limitée et pas d’enregistrement de l’auteur des mises à jour |

PowerShellGet fonctionne avec les deux types et prend en charge la localisation des versions et l’installation des dépendances.
Toutefois, certaines fonctionnalités compatibles avec PowerShell Gallery ne sont pas disponibles pour les partages de fichiers et les serveurs NuGet de base.

- Tout est un package : pas de différentiation des scripts, modules, ressources DSC ou capacités de rôle.
- Les serveurs de partage de fichiers ne voient pas les métadonnées des packages, et notamment les balises.

## <a name="creating-a-local-repository"></a>Créer un référentiel local

L’article suivant présente les étapes de configuration d’un serveur NuGet.

- [NuGet.Server][]

Suivez les étapes jusqu’à l’ajout de packages. La procédure de [publication d’un package](#publishing-to-a-local-repository) est traitée plus loin dans cet article.

Dans le cas d’un référentiel sur partage de fichiers, vérifiez que vos utilisateurs disposent des autorisations nécessaires pour accéder au partage de fichier.

## <a name="registering-a-local-repository"></a>Inscrire un référentiel local

Un référentiel doit être inscrit à l’aide de la commande `Register-PSRepository` pour être utilisable.
Dans les exemples ci-dessous, **InstallationPolicy** a pour valeur *Trusted*, partant du principe que vous faites confiance à votre propre référentiel.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Remarquez la différence entre les deux commandes en matière de gestion de **ScriptSourceLocation**. Pour les référentiels sur partage de fichiers, **SourceLocation** et **ScriptSourceLocation** doivent correspondre. Dans le cas d’un référentiel web, ils doivent être différents : dans cet exemple, une barre oblique « / » de fin est ajoutée à **SourceLocation**.

Pour que le nouveau PSRepository soit le référentiel par défaut, il faut annuler l’inscription de tous les autres PSRepository. Par exemple :

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Le nom de référentiel « PSGallery » est réservé à PowerShell Gallery. Il est possible d’annuler l’inscription de PSGallery, mais pas de réutiliser le nom PSGallery pour un autre référentiel.

Si vous devez restaurer PSGallery, exécutez la commande suivante :

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publier sur un référentiel local

Vous pouvez publier sur votre PSRepository local dès qu’il est inscrit. Il existe deux grands scénarios de publication : votre propre module ou un module provenant de PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publier un module créé par vos soins

Utilisez `Publish-Module` et `Publish-Script` pour publier votre module sur votre PSRepository local, comme sur PowerShell Gallery.

- Spécifiez l’emplacement de votre code.
- Indiquez une clé API.
- Spécifiez le nom du référentiel. Par exemple : `-PSRepository LocalPSRepo`

> [!NOTE]
> Vous devez créer un compte dans le serveur NuGet, puis vous connecter pour générer et enregistrer la clé API.
> Pour un partage de fichiers, utilisez une chaîne non vide comme valeur NuGetApiKey.

Exemples :

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts. Utilisez un système de gestion de clés sécurisé.

### <a name="publishing-a-module-from-the-psgallery"></a>Publier un module provenant de PSGallery

Pour publier un module provenant de PSGallery sur votre PSRepository local, vous pouvez utiliser la cmdlet « Save-Package ».

- Spécifiez le nom du package.
- Spécifiez « NuGet » comme fournisseur.
- Spécifiez l’emplacement PSGallery comme source (https://www.powershellgallery.com/api/v2).
- Spécifiez le chemin de votre référentiel local.

Exemple :

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Si votre PSRepository local est un référentiel web, la publication comporte une étape supplémentaire, qui utilise nuget.exe.

Voir la documentation sur [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installer PowerShellGet sur un système déconnecté

Il est difficile de déployer PowerShellGet dans des environnements où les systèmes doivent être déconnectés d’Internet. PowerShellGet comporte un processus de démarrage qui installe la dernière version la première fois qu’il est utilisé. Le module OfflinePowerShellGetDeploy de PowerShell Gallery fournit des cmdlets qui gèrent ce processus de démarrage.

Pour démarrer un déploiement hors connexion :

- Téléchargez et installez OfflinePowerShellGetDeploy sur votre système connecté à Internet et vos systèmes déconnectés.
- Téléchargez PowerShellGet et ses dépendances sur le système connecté à Internet avec la cmdlet `Save-PowerShellGetForOffline`.
- Copiez PowerShellGet et ses dépendances du système connecté à Internet au système déconnecté.
- Utilisez `Install-PowerShellGetOffline` sur le système déconnecté pour placer PowerShellGet et ses dépendances dans les dossiers correspondants.

Les commandes suivantes utilisent `Save-PowerShellGetForOffline` pour placer tous les composants dans un dossier `f:\OfflinePowerShellGet`.

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Rendez maintenant le contenu de `F:\OfflinePowerShellGet` accessible à vos systèmes déconnectés. Exécutez la cmdlet `Install-PowerShellGetOffline` pour installer PowerShellGet sur le système déconnecté.

> [!NOTE]
> Il est important de ne pas exécuter PowerShellGet dans la session PowerShell avant d’avoir exécuté ces commandes. Une fois PowerShellGet chargé dans la session, il n’est plus possible de mettre à jour les composants. Si vous lancez PowerShellGet par erreur, quittez et redémarrez PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Une fois que vous avez exécuté ces commandes, vous pouvez publier PowerShellGet dans votre référentiel local.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a>Utiliser des solutions de packaging pour héberger des référentiels PowerShellGet

Vous pouvez également utiliser des solutions de packaging comme Azure Artifacts pour héberger un référentiel PowerShellGet privé ou public. Pour obtenir des informations complémentaires et des instructions, consultez la [documentation Azure Artifacts](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).

> [!IMPORTANT]
> Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts. Utilisez un système de gestion de clés sécurisé.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
