---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Prendre en main PowerShell Gallery
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523031"
---
# <a name="get-started-with-the-powershell-gallery"></a>Prendre en main PowerShell Gallery

Le meilleur moyen d’installer des éléments à partir de PowerShell Gallery est d’utiliser les applets de commande dans le module [PowerShellGet](/powershell/module/powershellget). Il est inutile de se connecter pour télécharger des éléments de PowerShell Gallery.

> [!NOTE]
> Il est possible de télécharger un package directement à partir de PowerShell Gallery, mais cela est déconseillé. Pour plus d’informations, consultez [Téléchargement manuel de package](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).  


## <a name="discovering-items-from-the-powershell-gallery"></a>Détection d’éléments dans PowerShell Gallery

Vous pouvez rechercher des éléments dans PowerShell Gallery à l’aide du contrôle **Rechercher** sur ce site web, ou en parcourant les pages des modules et des scripts. Vous pouvez également rechercher des éléments dans PowerShell Gallery en exécutant les applets de commande [Find-Module][] et [Find-Script][], selon le type d’élément, avec `-Repository PSGallery`.

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

## <a name="learning-about-items-in-the-powershell-gallery"></a>En savoir plus sur les éléments de PowerShell Gallery

Une fois que vous avez identifié un élément qui vous intéresse, vous pouvez en savoir plus à son sujet. Pour cela, examinez la page spécifique de cet élément dans PowerShell Gallery. Dans cette page, vous serez en mesure de voir toutes les métadonnées chargées avec l’élément. Ces métadonnées associées à un élément sont fournies par l’auteur de l’élément et ne sont pas vérifiées par Microsoft. Le propriétaire de l’élément est fortement associé au compte PowerShell Gallery utilisé pour publier l’élément et est plus fiable que le champ Auteur.

Si vous détectez un élément publié qui vous semble suspect, cliquez sur **Signaler un abus** dans la page de l’élément.

Si vous exécutez [Find-Module][] ou [Find-Script][], vous pouvez afficher ces données dans l’objet PSGetModuleInfo retourné. Par exemple, l’exécution de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
retourne des données dans le module PSReadLine dans PowerShell Gallery.

## <a name="downloading-items-from-the-powershell-gallery"></a>Téléchargement d’éléments de PowerShell Gallery

Nous conseillons le processus suivant lors du téléchargement des éléments de PowerShell Gallery :

### <a name="inspect"></a>Inspecter

Pour télécharger un élément de PowerShell Gallery pour inspection, exécutez l’applet de commande [Save-Module][] ou [Save-Script][], selon le type d’élément. Cela vous permet d’enregistrer l’élément localement sans l’installer et d’inspecter son contenu. N’oubliez pas de supprimer l’élément enregistré manuellement.

Certains de ces éléments sont créés par Microsoft et d’autres sont créés par la communauté PowerShell.
Microsoft recommande de passer en revue le contenu et le code des éléments de cette galerie avant l’installation.

Si vous détectez un élément publié qui vous semble suspect, cliquez sur **Signaler un abus** dans la page de l’élément.

### <a name="install"></a>Installer

Pour installer un élément de PowerShell Gallery à utiliser, exécutez l’applet de commande [Install-Module][] ou [Install-Script][], selon le type d’élément.

[Install-Module][] installe le module dans `$env:ProgramFiles\WindowsPowerShell\Modules` par défaut.
Cette opération nécessite un compte d’administrateur. Si vous ajoutez le paramètre `-Scope CurrentUser`, le module est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] installe le script dans `$env:ProgramFiles\WindowsPowerShell\Scripts` par défaut.
Cette opération nécessite un compte d’administrateur. Si vous ajoutez le paramètre `-Scope CurrentUser`, le script est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Par défaut, [Install-Module][] et [Install-Script][] installent la version la plus récente d’un élément.
Pour installer une version antérieure de l’élément, ajoutez le paramètre `-RequiredVersion`.

### <a name="deploy"></a>Déployez

Pour déployer un élément de PowerShell Gallery sur Azure Automation, cliquez sur **Déployer sur Azure Automation** dans la page de détails de l’élément. Vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure. Notez que le déploiement d’éléments avec des dépendances va déployer toutes les dépendances sur Azure Automation. Le bouton « Déployer sur Azure Automation » peut être désactivé en ajoutant la balise **AzureAutomationNotSupported** aux métadonnées de l’élément.

Pour plus d’informations sur Azure Automation, consultez la documentation [Azure Automation](/azure/automation).

## <a name="updating-items-from-the-powershell-gallery"></a>Mise à jour d’éléments de PowerShell Gallery

Pour mettre à jour les éléments installés à partir de PowerShell Gallery, exécutez l’applet de commande [Update-Module][] ou [Update-Script][]. Quand elle est exécutée sans paramètre supplémentaire, [Update-Module][] tente de mettre à jour chaque module installé en exécutant [Install-Module][]. Pour mettre à jour les modules de façon sélective, ajoutez le paramètre `-Name`.

De même, quand elle est exécutée sans paramètre supplémentaire, [Update-Script][] tente également de mettre à jour chaque script installé en exécutant [Install-Script][]. Pour mettre à jour les scripts de façon sélective, ajoutez le paramètre `-Name`.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Répertorier les éléments que vous avez installés à partir de PowerShell Gallery

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