---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99599143"
---
# Module PackageManagement

## Description

Cette rubrique affiche les rubriques d’aide pour les applets de commande Package Management.

> [!IMPORTANT]
> Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS). Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.

## Applets de commande PackageManagement

### [Find-Package](Find-Package.md)
Recherche les packages de logiciels dans les sources de package disponibles.

### [Find-PackageProvider](Find-PackageProvider.md)
Retourne une liste de Package Management fournisseurs de packages disponibles pour l’installation.

### [Get-Package](Get-Package.md)
Retourne une liste de tous les packages logiciels qui ont été installés avec **PackageManagement**.

### [Get-PackageProvider](Get-PackageProvider.md)
Retourne une liste des fournisseurs de packages qui sont connectés à Package Management.

### [Get-PackageSource](Get-PackageSource.md)
Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.

### [Import-PackageProvider](Import-PackageProvider.md)
Ajoute Package Management fournisseurs de package à la session active.

### [Install-Package](Install-Package.md)
Installe un ou plusieurs packages logiciels.

### [Install-PackageProvider](Install-PackageProvider.md)
Installe un ou plusieurs fournisseurs de packages Package Management.

### [Register-PackageSource](Register-PackageSource.md)
Ajoute une source de package pour un fournisseur de package spécifié.

### [Save-Package](Save-Package.md)
Enregistre les packages sur l’ordinateur local sans les installer.

### [Set-PackageSource](Set-PackageSource.md)
Remplace une source de package pour un fournisseur de package spécifié.

### [Uninstall-Package](Uninstall-Package.md)
Désinstalle un ou plusieurs packages logiciels.

### [Unregister-PackageSource](Unregister-PackageSource.md)
Supprime une source de package inscrite.
