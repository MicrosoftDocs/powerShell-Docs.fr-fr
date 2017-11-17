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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="3a2f8-103">Ressources DSC intégrées pour Linux</span><span class="sxs-lookup"><span data-stu-id="3a2f8-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="3a2f8-104">Les ressources sont des blocs de construction que vous pouvez utiliser pour écrire un script DSC PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="3a2f8-105">DSC pour Linux est fourni avec un ensemble de fonctionnalités intégrées pour la configuration des ressources, telles que des fichiers et des dossiers, des packages, des variables d’environnement, des services et des processus.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="3a2f8-106">Ressources intégrées</span><span class="sxs-lookup"><span data-stu-id="3a2f8-106">Built-in resources</span></span> 

<span data-ttu-id="3a2f8-107">Le tableau suivant fournit la liste de ces ressources, ainsi que des liens vers les rubriques qui expliquent ces ressources en détail.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="3a2f8-108">[Ressource nxArchive](lnxArchiveResource.md) : fournit un mécanisme permettant de décompresser les fichiers d’archive (.tar, .zip) à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="3a2f8-109">[Ressource nxEnvironment](lnxEnvironmentResource.md) : gère les variables d’environnement des nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span> 
* <span data-ttu-id="3a2f8-110">[Ressource nxFile](lnxFileResource.md) : gère les fichiers et les répertoires Linux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span> 
* <span data-ttu-id="3a2f8-111">[Ressource nxFileLine](lnxFileLineResource.md) : gère des lignes d’un fichier Linux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span> 
* <span data-ttu-id="3a2f8-112">[Ressource nxGroup](lnxGroupResource.md) : gère les groupes Linux locaux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span> 
* <span data-ttu-id="3a2f8-113">[Ressource nxPackage](lnxPackageResource.md) : gère les packages des nœuds Linux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="3a2f8-114">[Ressources nxScript](lnxScriptResource.md) : exécute des scripts sur les nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="3a2f8-115">[Ressource nxService](lnxServiceResource.md) : gère les services (démons) Linux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="3a2f8-116">[Ressource nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md) : gère des clés ssh publiques pour un utilisateur Linux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span> 
* <span data-ttu-id="3a2f8-117">[Ressource nxUser](lnxUserResource.md) : gère les utilisateurs Linux locaux.</span><span class="sxs-lookup"><span data-stu-id="3a2f8-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span> 
  
