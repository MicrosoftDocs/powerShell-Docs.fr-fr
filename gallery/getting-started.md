---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Prendre en main PowerShell Gallery
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225673"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Bien démarrer avec PowerShell Gallery

Le meilleur moyen d’installer des packages à partir de PowerShell Gallery est d’utiliser les cmdlets du module [PowerShellGet](/powershell/module/powershellget). Il est inutile de se connecter pour télécharger des éléments de PowerShell Gallery.

> [!NOTE]
> Il est possible de télécharger un package directement à partir de PowerShell Gallery, mais cela est déconseillé.
> Pour plus d’informations, consultez [Téléchargement manuel de package](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Détecter des packages sur PowerShell Gallery

Pour rechercher des packages sur PowerShell Gallery, vous pouvez utiliser le contrôle **Rechercher** sur ce site web, ou parcourir les pages Modules et Scripts. Une autre possibilité consiste à exécuter les cmdlets [Find-Module][] et [Find-Script][], selon le type d’élément, avec `-Repository PSGallery`.

Vous pouvez filtrer les résultats de la galerie avec les paramètres suivants :

- Name
- AllVersions
- MinimumVersion
- RequiredVersion
- Légende
- Includes
- DscResource
- RoleCapability
- Commande
- Filtre

Si vous êtes uniquement intéressé par la détection de ressources DSC spécifiques dans PowerShell Gallery, vous pouvez exécuter l’applet de commande [Find-DscResource]. Find-DscResource retourne des données sur les ressources DSC contenues dans la galerie.
Étant donné que les ressources DSC sont toujours transmises dans le cadre d’un module, vous devez toujours exécuter [Install-Module][] pour installer ces ressources DSC.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>En savoir plus sur les packages de PowerShell Gallery

Maintenant que vous avez identifié un package qui vous intéresse, vous voulez probablement en savoir plus à son sujet. Pour cela, examinez la page correspondante sur PowerShell Gallery. Elle présente toutes les métadonnées chargées avec le package. Ces métadonnées, fournies par l’auteur du package, ne sont pas vérifiées par Microsoft. Le propriétaire du package est fortement associé au compte PowerShell Gallery utilisé pour publier le package ; il est plus fiable que le champ Auteur.

Si vous découvrez un package publié qui vous semble suspect, cliquez sur **Signaler un abus** sur la page du package.

Si vous exécutez [Find-Module][] ou [Find-Script][], vous pouvez afficher ces données dans l’objet PSGetModuleInfo retourné. Par exemple, l’exécution de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
retourne des données dans le module PSReadLine dans PowerShell Gallery.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Télécharger des packages de PowerShell Gallery

Nous conseillons le processus suivant pour télécharger des packages de PowerShell Gallery :

### <a name="inspect"></a>Inspecter

Pour télécharger un package de PowerShell Gallery à des fins d’inspection, exécutez la cmdlet [Save-Module][] ou la cmdlet [Save-Script][], selon le type de package. Elles permettent d’enregistrer le package localement sans l’installer et d’inspecter son contenu. N’oubliez pas de supprimer manuellement le package enregistré.

Certains de ces packages sont créés par Microsoft, d’autres par la communauté PowerShell.
Microsoft recommande de passer en revue le contenu et le code des packages de cette galerie avant de les installer.

Si vous découvrez un package publié qui vous semble suspect, cliquez sur **Signaler un abus** sur la page du package.

### <a name="install"></a>Installer

Pour installer un package de PowerShell Gallery à des fins d’utilisation, exécutez la cmdlet [Install-Module][] ou la cmdlet [Install-Script][], selon le type de package.

[Install-Module][] installe le module dans `$env:ProgramFiles\WindowsPowerShell\Modules` par défaut.
Cette opération nécessite un compte d’administrateur. Si vous ajoutez le paramètre `-Scope CurrentUser`, le module est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] installe le script dans `$env:ProgramFiles\WindowsPowerShell\Scripts` par défaut.
Cette opération nécessite un compte d’administrateur. Si vous ajoutez le paramètre `-Scope CurrentUser`, le script est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Par défaut, [Install-Module][] et [Install-Script][] installent la dernière version du package.
Pour installer une version antérieure, ajoutez le paramètre `-RequiredVersion`.

### <a name="deploy"></a>Déployez

Pour déployer un package de PowerShell Gallery sur Azure Automation, cliquez sur **Déployer sur Azure Automation** sur la page de détails du package. Le Portail de gestion Azure s’affiche : connectez-vous à l’aide de vos informations d’identification de compte Azure. Notez que le déploiement de packages comportant des dépendances a pour effet de déployer toutes les dépendances sur Azure Automation. Pour désactiver le bouton « Déployer sur Azure Automation », ajoutez la balise **AzureAutomationNotSupported** aux métadonnées du package.

Pour plus d’informations sur Azure Automation, consultez la documentation [Azure Automation](/azure/automation).

## <a name="updating-packages-from-the-powershell-gallery"></a>Mettre à jour des packages de PowerShell Gallery

Pour mettre à jour des packages installés sur PowerShell Gallery, exécutez la cmdlet [Update-Module][] ou la cmdlet [Update-Script][]. Quand elle est exécutée sans paramètre supplémentaire, [Update-Module][] tente de mettre à jour chaque module installé en exécutant [Install-Module][]. Pour mettre à jour les modules de façon sélective, ajoutez le paramètre `-Name`.

De même, quand elle est exécutée sans paramètre supplémentaire, [Update-Script][] tente également de mettre à jour chaque script installé en exécutant [Install-Script][]. Pour mettre à jour les scripts de façon sélective, ajoutez le paramètre `-Name`.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Lister les packages installés sur PowerShell Gallery

Pour connaître les modules que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledModule][]. Cette commande répertorie tous les modules qui ont été installés directement à partir de PowerShell Gallery sur votre système.

De même, pour connaître les scripts que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledScript][]. Cette commande répertorie tous les scripts qui ont été installés directement à partir de PowerShell Gallery sur votre système.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
