---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Ressources DSC intégrées pour Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Ressources DSC intégrées pour Linux

Les ressources sont des blocs de construction que vous pouvez utiliser pour écrire un script DSC PowerShell. DSC pour Linux est fourni avec un ensemble de fonctionnalités intégrées pour la configuration des ressources, telles que des fichiers et des dossiers, des packages, des variables d’environnement, des services et des processus.

## <a name="built-in-resources"></a>Ressources intégrées 

Le tableau suivant fournit la liste de ces ressources, ainsi que des liens vers les rubriques qui expliquent ces ressources en détail.

* [Ressource nxArchive](lnxArchiveResource.md) : fournit un mécanisme permettant de décompresser les fichiers d’archive (.tar, .zip) à un emplacement spécifique.
* [Ressource nxEnvironment](lnxEnvironmentResource.md) : gère les variables d’environnement des nœuds cibles. 
* [Ressource nxFile](lnxFileResource.md) : gère les fichiers et les répertoires Linux. 
* [Ressource nxFileLine](lnxFileLineResource.md) : gère des lignes d’un fichier Linux. 
* [Ressource nxGroup](lnxGroupResource.md) : gère les groupes Linux locaux. 
* [Ressource nxPackage](lnxPackageResource.md) : gère les packages des nœuds Linux.
* [Ressources nxScript](lnxScriptResource.md) : exécute des scripts sur les nœuds cibles.
* [Ressource nxService](lnxServiceResource.md) : gère les services (démons) Linux.
* [Ressource nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md) : gère des clés ssh publiques pour un utilisateur Linux. 
* [Ressource nxUser](lnxUserResource.md) : gère les utilisateurs Linux locaux. 
  
