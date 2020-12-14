---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,applet de commande
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 577dc9a56da98d975b777e6cd48ecdcaafd3128d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892367"
---
# Module PowerShellGet

## Description

PowerShellGet est un module avec des commandes permettant de détecter, d’installer, de mettre à jour et de publier des artefacts PowerShell tels que des modules, des ressources DSC, des fonctionnalités de rôle et des scripts.

> [!IMPORTANT]
> Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security). Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.

## Applets de commande PowerShellGet

### [Find-Command](Find-Command.md)
Recherche des commandes PowerShell dans des modules.

### [Find-DscResource](Find-DscResource.md)
Recherche les ressources de configuration d’état souhaité (DSC).

### [Find-Module](Find-Module.md)
Recherche les modules dans un référentiel qui correspondent aux critères spécifiés.

### [Find-RoleCapability](Find-RoleCapability.md)
Recherche les capacités de rôle dans des modules.

### [Find-Script](Find-Script.md)
Recherche un script.

### [Get-InstalledModule](Get-InstalledModule.md)
Obtient une liste de modules sur l’ordinateur qui ont été installés par PowerShellGet.

### [Get-InstalledScript](Get-InstalledScript.md)
Obtient un script installé.

### [Get-PSRepository](Get-PSRepository.md)
Obtient les référentiels PowerShell.

### [Install-Module](Install-Module.md)
Télécharge un ou plusieurs modules à partir d’un référentiel et les installe sur l’ordinateur local.

### [Install-Script](Install-Script.md)
Installe un script.

### [New-ScriptFileInfo](New-ScriptFileInfo.md)
Crée un fichier de script avec des métadonnées.

### [Publish-Module](Publish-Module.md)
Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.

### [Publish-Script](Publish-Script.md)
Publie un script.

### [Register-PSRepository](Register-PSRepository.md)
Inscrit un référentiel PowerShell.

### [Save-Module](Save-Module.md)
Enregistre un module et ses dépendances sur l’ordinateur local, mais n’installe pas le module.

### [Save-Script](Save-Script.md)
Enregistre un script.

### [Set-PSRepository](Set-PSRepository.md)
Définit des valeurs pour un dépôt inscrit.

### [Test-ScriptFileInfo](Test-ScriptFileInfo.md)
Valide un bloc de commentaires pour un script.

### [Uninstall-Module](Uninstall-Module.md)
Désinstalle un module.

### [Uninstall-Script](Uninstall-Script.md)
Désinstalle un script.

### [Unregister-PSRepository](Unregister-PSRepository.md)
Annule l’enregistrement d’un référentiel.

### [Update-Module](Update-Module.md)
Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.

### [Update-ModuleManifest](Update-ModuleManifest.md)
Met à jour un fichier manifeste de module.

### [Update-Script](Update-Script.md)
Met à jour un script.

### [Update-ScriptFileInfo](Update-ScriptFileInfo.md)
Met à jour les informations d’un script.
