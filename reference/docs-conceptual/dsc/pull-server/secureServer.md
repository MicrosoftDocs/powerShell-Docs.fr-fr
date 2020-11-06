---
ms.date: 06/12/2017
description: Ce document fournit les meilleures pratiques pour aider les ingénieurs qui déploient le serveur collecteur DSC.
keywords: dsc,powershell,configuration,installation
title: Bonnes pratiques pour le serveur collecteur
ms.openlocfilehash: 0021baa219a0936405eccf2cc7741e042f8bf09f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664319"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="c46f4-104">Bonnes pratiques pour le serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="c46f4-104">Pull server best practices</span></span>

<span data-ttu-id="c46f4-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c46f4-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c46f4-106">Le serveur collecteur (fonctionnalité Windows *Service DSC* ) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c46f4-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="c46f4-107">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="c46f4-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="c46f4-108">Résumé : Ce document vise à fournir une procédure et une extensibilité pour aider les ingénieurs qui préparent la solution.</span><span class="sxs-lookup"><span data-stu-id="c46f4-108">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="c46f4-109">Les informations qu’il contient indiquent les bonnes pratiques identifiées par les clients puis validées par l’équipe du produit qui garantit que les recommandations sont innovantes et considérées comme stables.</span><span class="sxs-lookup"><span data-stu-id="c46f4-109">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

- <span data-ttu-id="c46f4-110">Auteur : Michael Greene</span><span class="sxs-lookup"><span data-stu-id="c46f4-110">Author: Michael Greene</span></span>
- <span data-ttu-id="c46f4-111">Réviseurs : Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="c46f4-111">Reviewers: Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
- <span data-ttu-id="c46f4-112">Date de publication : Avril 2015</span><span class="sxs-lookup"><span data-stu-id="c46f4-112">Published: April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="c46f4-113">Résumé</span><span class="sxs-lookup"><span data-stu-id="c46f4-113">Abstract</span></span>

<span data-ttu-id="c46f4-114">Ce document a pour but de fournir des conseils officiels à toute personne planifiant l’implémentation d’un serveur collecteur Windows PowerShell DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="c46f4-114">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="c46f4-115">Un serveur collecteur est un service simple dont le déploiement ne devrait prendre que quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="c46f4-115">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="c46f4-116">Bien que ce document propose des procédures techniques pouvant être utilisées dans un déploiement, il est surtout une référence de bonnes pratiques et de points à prendre en compte avant d’effectuer un déploiement.</span><span class="sxs-lookup"><span data-stu-id="c46f4-116">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span> <span data-ttu-id="c46f4-117">Les lecteurs doivent avoir une connaissance de base de DSC et des termes utilisés pour décrire les composants inclus dans un déploiement DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-117">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="c46f4-118">Pour plus d’informations, consultez la rubrique [Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](/powershell/scripting/dsc/overview/overview).</span><span class="sxs-lookup"><span data-stu-id="c46f4-118">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) topic.</span></span> <span data-ttu-id="c46f4-119">Étant donné que DSC est supposé évoluer à la cadence du cloud, la technologie sous-jacente qui inclut le serveur collecteur devrait également évoluer et introduire de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c46f4-119">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="c46f4-120">L’annexe de ce document comprend un tableau de versions qui fournit des références aux versions précédentes et aux solutions novatrices pour encourager les conceptions innovantes.</span><span class="sxs-lookup"><span data-stu-id="c46f4-120">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="c46f4-121">Les deux principales sections de ce document sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c46f4-121">The two major sections of this document:</span></span>

- <span data-ttu-id="c46f4-122">Planification de la configuration</span><span class="sxs-lookup"><span data-stu-id="c46f4-122">Configuration Planning</span></span>
- <span data-ttu-id="c46f4-123">Guide d'installation</span><span class="sxs-lookup"><span data-stu-id="c46f4-123">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="c46f4-124">Versions de Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="c46f4-124">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="c46f4-125">Les informations contenues dans ce document s’appliquent à Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="c46f4-125">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="c46f4-126">Même si WMF 5.0 n’est pas nécessaire au déploiement et au fonctionnement d’un serveur collecteur, elle est la version ciblée par ce document.</span><span class="sxs-lookup"><span data-stu-id="c46f4-126">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="c46f4-127">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="c46f4-127">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="c46f4-128">DSC (Desired State Configuration) est une plateforme de gestion qui permet de déployer et de gérer les données de configuration à l’aide d’une syntaxe nommée MOF (Managed Object Format) pour décrire le modèle CIM (Common Information Model).</span><span class="sxs-lookup"><span data-stu-id="c46f4-128">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="c46f4-129">Un projet open source, OMI (Open Management Infrastructure), existe pour pousser le développement de ces normes sur les plateformes comme les systèmes d’exploitation Linux et de matériel réseau.</span><span class="sxs-lookup"><span data-stu-id="c46f4-129">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="c46f4-130">Pour plus d’informations, consultez la [page DMTF proposant des liens vers les spécifications MOF](https://www.dmtf.org/standards/cim) et la page relative aux [documents et la source OMI](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="c46f4-130">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="c46f4-131">Windows PowerShell fournit un ensemble d’extensions de langage pour DSC que vous pouvez utiliser pour créer et gérer des configurations déclaratives.</span><span class="sxs-lookup"><span data-stu-id="c46f4-131">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="c46f4-132">Rôle serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="c46f4-132">Pull server role</span></span>

<span data-ttu-id="c46f4-133">Un serveur collecteur fournit un service centralisé pour stocker des configurations qui seront accessibles aux nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="c46f4-133">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="c46f4-134">Vous pouvez déployer le rôle serveur collecteur comme instance de serveur web ou partage de fichiers SMB.</span><span class="sxs-lookup"><span data-stu-id="c46f4-134">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="c46f4-135">La fonctionnalité de serveur web inclut une interface OData et peut éventuellement inclure des fonctionnalités permettant aux nœuds cibles d’envoyer une confirmation de réussite ou d’échec quand les configurations sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="c46f4-135">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="c46f4-136">Cette fonctionnalité est utile dans les environnements comportant un grand nombre de nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="c46f4-136">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="c46f4-137">Après avoir configuré un nœud cible (également appelé « client ») pour pointer vers le serveur collecteur, téléchargez et appliquez les données de configuration les plus récentes et tous les scripts nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c46f4-137">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="c46f4-138">Vous pouvez effectuer ces opérations en un seul déploiement ou comme une tâche récurrente qui considère aussi le serveur collecteur comme important pour gérer les changements au besoin.</span><span class="sxs-lookup"><span data-stu-id="c46f4-138">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="c46f4-139">Pour plus d’informations, consultez [Serveurs collecteurs Windows PowerShell DSC](pullserver.md) et [Modes de configuration d’émission et de collecte](pullserver.md).</span><span class="sxs-lookup"><span data-stu-id="c46f4-139">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](pullserver.md) and [Push and Pull Configuration Modes](pullserver.md).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="c46f4-140">Planification de la configuration</span><span class="sxs-lookup"><span data-stu-id="c46f4-140">Configuration planning</span></span>

<span data-ttu-id="c46f4-141">Si vous voulez déployer des logiciels d’entreprise, vous pouvez collecter certaines informations à l’avance pour faciliter la planification de l’architecture appropriée et vous préparer aux étapes nécessaires pour effectuer le déploiement.</span><span class="sxs-lookup"><span data-stu-id="c46f4-141">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="c46f4-142">Les sections suivantes fournissent des informations sur la préparation et sur les connexions d’organisation qui devront probablement être établies à l’avance.</span><span class="sxs-lookup"><span data-stu-id="c46f4-142">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="c46f4-143">Configuration logicielle requise</span><span class="sxs-lookup"><span data-stu-id="c46f4-143">Software requirements</span></span>

<span data-ttu-id="c46f4-144">Pour déployer un serveur collecteur, la fonctionnalité Service DSC de Windows Server est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c46f4-144">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="c46f4-145">Cette fonctionnalité a été introduite dans Windows Server 2012 et a été mise à jour au fil des versions de WMF (Windows Management Framework).</span><span class="sxs-lookup"><span data-stu-id="c46f4-145">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="c46f4-146">Téléchargements de logiciels</span><span class="sxs-lookup"><span data-stu-id="c46f4-146">Software downloads</span></span>

<span data-ttu-id="c46f4-147">Outre l’installation du contenu le plus récent à partir de Windows Update, deux téléchargements sont considérés comme une bonne pratique pour déployer un serveur collecteur DSC : la dernière version de Windows Management Framework et un module DSC permettant d’automatiser la configuration des serveurs collecteurs.</span><span class="sxs-lookup"><span data-stu-id="c46f4-147">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="c46f4-148">WMF</span><span class="sxs-lookup"><span data-stu-id="c46f4-148">WMF</span></span>

<span data-ttu-id="c46f4-149">Windows Server 2012 R2 inclut une fonctionnalité appelée « Service DSC ».</span><span class="sxs-lookup"><span data-stu-id="c46f4-149">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="c46f4-150">Service DSC fournit les fonctionnalités de serveur collecteur, notamment les fichiers binaires qui prennent en charge le point de terminaison OData.</span><span class="sxs-lookup"><span data-stu-id="c46f4-150">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="c46f4-151">WMF est inclus dans Windows Server et est mis à jour en continu entre les versions de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c46f4-151">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span>
<span data-ttu-id="c46f4-152">Les [nouvelles versions de WMF 5.0](https://www.microsoft.com/download/details.aspx?id=54616) peuvent inclure des mises à jour de la fonctionnalité Service DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-152">[New versions of WMF 5.0](https://www.microsoft.com/download/details.aspx?id=54616) can include updates to the DSC Service feature.</span></span> <span data-ttu-id="c46f4-153">C’est pourquoi il est recommandé de télécharger la dernière version de WMF et de consulter les notes de publication afin de déterminer si la version inclut une mise à jour de la fonctionnalité Service DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-153">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="c46f4-154">Vous devez également examiner la section des notes de publication qui indique si l’état de conception d’un scénario ou d’une mise à jour est répertorié comme stable ou expérimental.</span><span class="sxs-lookup"><span data-stu-id="c46f4-154">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="c46f4-155">Pour avoir un cycle de versions en continu, des fonctionnalités peuvent être déclarées stables, ce qui signifie qu’elles sont prêtes à être utilisées dans un environnement de production, même si WMF est publié en préversion.</span><span class="sxs-lookup"><span data-stu-id="c46f4-155">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span> <span data-ttu-id="c46f4-156">Autres fonctionnalités qui ont déjà été mises à jour par des versions de WMF (voir les Notes de publication de WMF pour plus d’informations) :</span><span class="sxs-lookup"><span data-stu-id="c46f4-156">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="c46f4-157">Windows PowerShell Environnement d’écriture de scripts intégré (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c46f4-157">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="c46f4-158">Services web Windows PowerShell (Extension IIS Management OData)</span><span class="sxs-lookup"><span data-stu-id="c46f4-158">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="c46f4-159">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="c46f4-159">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="c46f4-160">WinRM (Windows Remote Management) WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="c46f4-160">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="c46f4-161">Ressource DSC</span><span class="sxs-lookup"><span data-stu-id="c46f4-161">DSC resource</span></span>

<span data-ttu-id="c46f4-162">Un déploiement de serveur collecteur peut être simplifié en configurant le service à l’aide d’un script de configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-162">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="c46f4-163">Ce document présente des scripts de configuration qui peuvent être utilisés pour déployer un nœud de serveur prêt pour la production.</span><span class="sxs-lookup"><span data-stu-id="c46f4-163">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="c46f4-164">Pour utiliser des scripts de configuration, un module DSC est obligatoire mais il n’est pas inclus dans Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c46f4-164">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="c46f4-165">Ce module obligatoire, appelé **xPSDesiredStateConfiguration** , inclut la ressource DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="c46f4-165">The required module name is **xPSDesiredStateConfiguration** , which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="c46f4-166">Vous pouvez télécharger le module xPSDesiredStateConfiguration [ici](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="c46f4-166">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="c46f4-167">Utilisez l’applet de commande `Install-Module` à partir du module **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="c46f4-167">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="c46f4-168">Le module **PowerShellGet** télécharge le module dans :</span><span class="sxs-lookup"><span data-stu-id="c46f4-168">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="c46f4-169">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-169">Planning task</span></span>

- <span data-ttu-id="c46f4-170">Avez-vous accès aux fichiers d’installation de Windows Server 2012 R2 ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-170">Do you have access to the installation files for Windows Server 2012 R2?</span></span>
- <span data-ttu-id="c46f4-171">L’environnement de déploiement disposera-t-il d’un accès à Internet pour télécharger WMF et le module à partir de la galerie en ligne ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-171">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>
- <span data-ttu-id="c46f4-172">Comment allez-vous installer les dernières mises à jour de sécurité après l’installation du système d’exploitation ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-172">How will you install the latest security updates after installing the operating system?</span></span>
- <span data-ttu-id="c46f4-173">L’environnement disposera-t-il d’un accès à Internet pour obtenir les mises à jour ou d’un serveur WSUS (Windows Server Update Services) local ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-173">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>
- <span data-ttu-id="c46f4-174">Avez-vous accès aux fichiers d’installation de Windows Server qui contiennent déjà les mises à jour par l’intermédiaire de l’injection hors connexion ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-174">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>

### <a name="hardware-requirements"></a><span data-ttu-id="c46f4-175">Configuration matérielle requise</span><span class="sxs-lookup"><span data-stu-id="c46f4-175">Hardware requirements</span></span>

<span data-ttu-id="c46f4-176">Les déploiements de serveurs collecteurs sont pris en charge sur les serveurs physiques et virtuels.</span><span class="sxs-lookup"><span data-stu-id="c46f4-176">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="c46f4-177">La configuration requise du serveur collecteur s’aligne sur celle de Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="c46f4-177">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

- <span data-ttu-id="c46f4-178">Unité centrale : processeur 1,4 GHz 64 bits</span><span class="sxs-lookup"><span data-stu-id="c46f4-178">CPU: 1.4 GHz 64-bit processor</span></span>
- <span data-ttu-id="c46f4-179">Mémoire : 512 Mo</span><span class="sxs-lookup"><span data-stu-id="c46f4-179">Memory: 512 MB</span></span>
- <span data-ttu-id="c46f4-180">Espace disque : 32 Go</span><span class="sxs-lookup"><span data-stu-id="c46f4-180">Disk Space: 32 GB</span></span>
- <span data-ttu-id="c46f4-181">Réseau : Carte Gigabit Ethernet</span><span class="sxs-lookup"><span data-stu-id="c46f4-181">Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="c46f4-182">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-182">Planning task</span></span>

- <span data-ttu-id="c46f4-183">Effectuerez-vous le déploiement sur du matériel physique ou sur une plateforme de virtualisation ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>
- <span data-ttu-id="c46f4-184">Quelle est la procédure pour demander un nouveau serveur dans votre environnement cible ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-184">What is the process to request a new server for your target environment?</span></span>
- <span data-ttu-id="c46f4-185">Combien de temps faut-il en moyenne pour rendre un serveur disponible ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-185">What is the average turnaround time for a server to become available?</span></span>
- <span data-ttu-id="c46f4-186">Un serveur de quelle taille demandez-vous ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-186">What size server will you request?</span></span>

### <a name="accounts"></a><span data-ttu-id="c46f4-187">Comptes</span><span class="sxs-lookup"><span data-stu-id="c46f4-187">Accounts</span></span>

<span data-ttu-id="c46f4-188">Aucun compte de service en particulier n’est exigé pour déployer une instance de serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c46f4-188">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="c46f4-189">Toutefois, dans certains scénarios, le site web peut s’exécuter dans le contexte d’un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="c46f4-189">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="c46f4-190">Par exemple, s’il est nécessaire d’accéder à un partage de stockage pour du contenu de site web et que le serveur Windows Server ou l’appareil hébergeant le partage de stockage ne sont pas joints à un domaine.</span><span class="sxs-lookup"><span data-stu-id="c46f4-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="c46f4-191">Enregistrements DNS</span><span class="sxs-lookup"><span data-stu-id="c46f4-191">DNS records</span></span>

<span data-ttu-id="c46f4-192">Lors de la configuration de clients, vous aurez besoin d’un nom de serveur pour utiliser un environnement de serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c46f4-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="c46f4-193">Dans les environnements de test, on utilise généralement le nom d’hôte du serveur. On peut aussi utiliser l’adresse IP du serveur si la résolution de noms DNS n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="c46f4-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="c46f4-194">Dans les environnements de production ou dans un environnement lab destiné à représenter un déploiement de production, il est conseillé de créer un enregistrement DNS CNAME.</span><span class="sxs-lookup"><span data-stu-id="c46f4-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="c46f4-195">Un CNAME DNS vous permet de créer un alias pour faire référence à votre enregistrement d’hôte (A).</span><span class="sxs-lookup"><span data-stu-id="c46f4-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="c46f4-196">L’objectif d’avoir un enregistrement de nom supplémentaire est d’augmenter la flexibilité dans le cas où une modification s’avérerait nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c46f4-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="c46f4-197">Un CNAME permet d’isoler la configuration du client afin que les modifications apportées à l’environnement de serveur, telles que le remplacement d’un serveur collecteur ou l’ajout de serveurs collecteurs supplémentaires, ne nécessitent pas une modification correspondante dans la configuration du client.</span><span class="sxs-lookup"><span data-stu-id="c46f4-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="c46f4-198">Quand vous choisissez un nom pour l’enregistrement DNS, gardez à l’esprit l’architecture de la solution.</span><span class="sxs-lookup"><span data-stu-id="c46f4-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span> <span data-ttu-id="c46f4-199">Si vous utilisez l’équilibrage de charge, le certificat servant à sécuriser le trafic sur HTTPS doit partager le même nom que l’enregistrement DNS.</span><span class="sxs-lookup"><span data-stu-id="c46f4-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

|       <span data-ttu-id="c46f4-200">Scénario</span><span class="sxs-lookup"><span data-stu-id="c46f4-200">Scenario</span></span>        |                                                                                         <span data-ttu-id="c46f4-201">Bonne pratique</span><span class="sxs-lookup"><span data-stu-id="c46f4-201">Best Practice</span></span>
|:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|<span data-ttu-id="c46f4-202">Environnement de test</span><span class="sxs-lookup"><span data-stu-id="c46f4-202">Test Environment</span></span>       | <span data-ttu-id="c46f4-203">Reproduisez l’environnement de production planifié, si possible.</span><span class="sxs-lookup"><span data-stu-id="c46f4-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="c46f4-204">Un nom d’hôte de serveur convient aux configurations simples.</span><span class="sxs-lookup"><span data-stu-id="c46f4-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="c46f4-205">Si DNS n’est pas disponible, une adresse IP peut être utilisée à la place d’un nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="c46f4-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>
|<span data-ttu-id="c46f4-206">Déploiement à nœud unique</span><span class="sxs-lookup"><span data-stu-id="c46f4-206">Single Node Deployment</span></span> | <span data-ttu-id="c46f4-207">Créez un enregistrement DNS CNAME qui pointe vers le nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="c46f4-207">Create a DNS CNAME record that points to the server hostname.</span></span>

<span data-ttu-id="c46f4-208">Pour plus d’informations, consultez [Configuration du tourniquet (round robin) DNS dans Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="c46f4-208">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="c46f4-209">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-209">Planning task</span></span>

- <span data-ttu-id="c46f4-210">Savez-vous qui contacter pour créer et modifier des enregistrements DNS ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-210">Do you know who to contact to have DNS records created and changed?</span></span>
- <span data-ttu-id="c46f4-211">Combien de temps faut-il en moyenne pour demander un enregistrement DNS ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-211">What is the average turnaround for a request for a DNS record?</span></span>
- <span data-ttu-id="c46f4-212">Avez-vous besoin de demander des enregistrements de nom d’hôte (A) statiques pour les serveurs ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-212">Do you need to request static Hostname (A) records for servers?</span></span>
- <span data-ttu-id="c46f4-213">Que demanderez-vous comme CNAME ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-213">What will you request as a CNAME?</span></span>
- <span data-ttu-id="c46f4-214">Le cas échéant, quel type de solution d’équilibrage de charge utiliserez-vous ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="c46f4-215">(pour plus d’informations, voir la section intitulée « Équilibrage de la charge »)</span><span class="sxs-lookup"><span data-stu-id="c46f4-215">(see section titled Load Balancing for details)</span></span>

### <a name="public-key-infrastructure"></a><span data-ttu-id="c46f4-216">Infrastructure à clé publique (PKI)</span><span class="sxs-lookup"><span data-stu-id="c46f4-216">Public Key Infrastructure</span></span>

<span data-ttu-id="c46f4-217">Aujourd’hui, la plupart des organisations exigent que le trafic réseau, en particulier le trafic qui inclut des données sensibles comme le mode de configuration des serveurs, soit validé et/ou chiffré pendant le transit.</span><span class="sxs-lookup"><span data-stu-id="c46f4-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="c46f4-218">Bien qu’il soit possible de déployer un serveur collecteur à l’aide de HTTP, ce qui facilite les demandes des clients en texte en clair, il est recommandé de sécuriser le trafic à l’aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c46f4-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="c46f4-219">Vous pouvez configurer le service pour utiliser HTTPS à l’aide d’un ensemble de paramètres dans la ressource DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="c46f4-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="c46f4-220">Les critères de certificat pour sécuriser le trafic HTTPS pour le serveur collecteur ne sont pas différents de ceux pour sécuriser un site web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c46f4-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="c46f4-221">Le modèle de **serveur web** dans un service de certificats Windows Server est conforme aux fonctionnalités demandées.</span><span class="sxs-lookup"><span data-stu-id="c46f4-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="c46f4-222">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-222">Planning task</span></span>

- <span data-ttu-id="c46f4-223">Si les demandes de certificats ne sont pas automatisées, qui devrez-vous contacter pour demander un certificat ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>
- <span data-ttu-id="c46f4-224">Combien de temps faut-il en moyenne pour la demande ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-224">What is the average turnaround for the request?</span></span>
- <span data-ttu-id="c46f4-225">Comment le fichier de certificat vous sera-t-il transféré ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-225">How will the certificate file be transferred to you?</span></span>
- <span data-ttu-id="c46f4-226">Comment la clé privée de certificat vous sera-t-elle transférée ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-226">How will the certificate private key be transferred to you?</span></span>
- <span data-ttu-id="c46f4-227">Quelle est la durée d’expiration par défaut ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-227">How long is the default expiration time?</span></span>
- <span data-ttu-id="c46f4-228">Avez-vous choisi, pour l’environnement de serveur collecteur, un nom DNS que vous pouvez utiliser comme nom du certificat ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>

### <a name="choosing-an-architecture"></a><span data-ttu-id="c46f4-229">Choix d’une architecture</span><span class="sxs-lookup"><span data-stu-id="c46f4-229">Choosing an architecture</span></span>

<span data-ttu-id="c46f4-230">Vous pouvez déployer un serveur collecteur à l’aide d’un service web hébergé sur IIS ou d’un partage de fichiers SMB.</span><span class="sxs-lookup"><span data-stu-id="c46f4-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="c46f4-231">Dans la plupart des cas, l’option de service web offre une plus grande souplesse.</span><span class="sxs-lookup"><span data-stu-id="c46f4-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="c46f4-232">Il n’est pas rare que le trafic HTTPS traverse les limites du réseau, tandis que le trafic SMB est souvent filtré ou bloqué entre les réseaux.</span><span class="sxs-lookup"><span data-stu-id="c46f4-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="c46f4-233">Le service web offre également la possibilité d’inclure un serveur de mise en conformité ou Web Reporting Manager (ces deux sujets seront traités dans une future version de ce document) qui fournissent un mécanisme permettant aux clients de signaler l’état à un serveur pour une visibilité centralisée.</span><span class="sxs-lookup"><span data-stu-id="c46f4-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="c46f4-234">SMB fournit une option pour les environnements où la stratégie indique qu’un serveur web ne doit pas être utilisé et pour les autres exigences liées à l’environnement qui font qu’un rôle serveur web n’est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="c46f4-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="c46f4-235">Dans les deux cas, n’oubliez pas d’évaluer les exigences de signature et de chiffrement du trafic.</span><span class="sxs-lookup"><span data-stu-id="c46f4-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="c46f4-236">HTTPS, la signature SMB et les stratégies IPSEC sont toutes des options qui méritent d’être examinées.</span><span class="sxs-lookup"><span data-stu-id="c46f4-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="c46f4-237">Équilibrage de la charge</span><span class="sxs-lookup"><span data-stu-id="c46f4-237">Load balancing</span></span>

<span data-ttu-id="c46f4-238">Les clients qui interagissent avec le service web adressent une demande d’informations qui sont retournées dans une réponse unique.</span><span class="sxs-lookup"><span data-stu-id="c46f4-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="c46f4-239">Aucune demande séquentielle n’est nécessaire. La plateforme d’équilibrage de charge n’a donc pas besoin de garantir la conservation des sessions sur un serveur unique à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="c46f4-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="c46f4-240">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-240">Planning task</span></span>

- <span data-ttu-id="c46f4-241">Quelle solution sera utilisée pour le trafic d’équilibrage de charge entre les serveurs ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-241">What solution will be used for load balancing traffic across servers?</span></span>
- <span data-ttu-id="c46f4-242">Si vous utilisez un programme d’équilibrage de charge matérielle, qui acceptera une demande d’ajout d’une nouvelle configuration à l’appareil ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>
- <span data-ttu-id="c46f4-243">Combien de temps faut-il en moyenne pour faire une demande de configuration d’un nouveau service web à charge équilibrée ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>
- <span data-ttu-id="c46f4-244">Quelles informations seront nécessaires pour la demande ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-244">What information will be required for the request?</span></span>
- <span data-ttu-id="c46f4-245">Devrez-vous demander une adresse IP supplémentaire ou l’équipe responsable de l’équilibrage de charge gérera-t-elle ce point ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>
- <span data-ttu-id="c46f4-246">Avez-vous des enregistrements DNS obligatoires, et seront-ils exigés par l’équipe responsable de la configuration de la solution d’équilibrage de charge ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>
- <span data-ttu-id="c46f4-247">La solution d’équilibrage de charge exige-t-elle que l’infrastructure à clé publique (PKI) soit gérée par l’appareil ou peut-elle équilibrer la charge du trafic HTTPS tant qu’il n’y a aucune exigence liée à la session ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="c46f4-248">Configurations et modules intermédiaires sur le serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="c46f4-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="c46f4-249">Dans le cadre de la planification de la configuration, vous devez réfléchir aux modules et configurations DSC qui seront hébergés par le serveur.</span><span class="sxs-lookup"><span data-stu-id="c46f4-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="c46f4-250">Pour les besoins de la planification de la configuration, il est important de comprendre le mode de préparation et de déploiement du contenu sur un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c46f4-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="c46f4-251">Cette section sera prochainement développée et incluse dans un Guide des opérations du serveur collecteur DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span> <span data-ttu-id="c46f4-252">Ce guide décrira le processus de gestion des configurations et des modules avec l’automatisation jour après jour.</span><span class="sxs-lookup"><span data-stu-id="c46f4-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="c46f4-253">Modules DSC</span><span class="sxs-lookup"><span data-stu-id="c46f4-253">DSC modules</span></span>

<span data-ttu-id="c46f4-254">Les clients qui demandent une configuration doivent disposer des modules DSC obligatoires.</span><span class="sxs-lookup"><span data-stu-id="c46f4-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="c46f4-255">Le serveur collecteur dispose d’une fonctionnalité qui permet d’automatiser la distribution sur demande des modules DSC aux clients.</span><span class="sxs-lookup"><span data-stu-id="c46f4-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="c46f4-256">Si vous déployez un serveur collecteur pour la première fois, peut-être dans le cadre d’un laboratoire ou à des fins de démonstration de concept, vous allez probablement dépendre des modules DSC qui sont disponibles à partir de dépôts publics tels que PowerShell Gallery ou des dépôts GitHub PowerShell.org pour les modules DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="c46f4-257">Il est essentiel de se rappeler que même pour les sources en ligne approuvées telles que PowerShell Gallery, tout module téléchargé à partir d’un dépôt public doit être vérifié par quelqu’un disposant d’une expérience PowerShell et d’une connaissance de l’environnement dans lequel les modules seront utilisés avant de les utiliser en production.</span><span class="sxs-lookup"><span data-stu-id="c46f4-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="c46f4-258">Profitez de l’exécution de cette tâche pour rechercher dans le module tout contenu pouvant être supprimé, telle que la documentation et les exemples de script.</span><span class="sxs-lookup"><span data-stu-id="c46f4-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="c46f4-259">Vous réduisez ainsi la bande passante réseau par client lors de leur première demande, quand les modules sont téléchargés sur le réseau à partir du serveur vers le client.</span><span class="sxs-lookup"><span data-stu-id="c46f4-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="c46f4-260">Chaque module doit être empaqueté dans un format spécifique, un fichier ZIP nommé NomModule_Version.zip, qui comprend le contenu du module.</span><span class="sxs-lookup"><span data-stu-id="c46f4-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="c46f4-261">Une fois le fichier copié sur le serveur, un fichier de somme de contrôle doit être créé.</span><span class="sxs-lookup"><span data-stu-id="c46f4-261">After the file is copied to the server a checksum file must be created.</span></span>
<span data-ttu-id="c46f4-262">Quand les clients se connectent au serveur, la somme de contrôle est utilisée pour vérifier que le contenu du module DSC n’a pas changé depuis sa publication.</span><span class="sxs-lookup"><span data-stu-id="c46f4-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="c46f4-263">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-263">Planning task</span></span>

- <span data-ttu-id="c46f4-264">Si vous planifiez un environnement de test ou de laboratoire, quels scénarios sont essentiels pour la validation ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>
- <span data-ttu-id="c46f4-265">Existe-t-il des modules à la disposition du public qui contiennent des ressources permettant de couvrir tout ce dont vous avez besoin ou devrez-vous créer vos propres ressources ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>
- <span data-ttu-id="c46f4-266">Votre environnement aura-t-il accès à Internet pour récupérer les modules publics ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-266">Will your environment have Internet access to retrieve public modules?</span></span>
- <span data-ttu-id="c46f4-267">Qui sera chargé de la vérification des modules DSC ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-267">Who will be responsible for reviewing DSC modules?</span></span>
- <span data-ttu-id="c46f4-268">Si vous planifiez un environnement de production, qu’allez-vous utiliser comme dépôt local pour le stockage des modules DSC ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>
- <span data-ttu-id="c46f4-269">Une équipe centrale acceptera-t-elle les modules DSC des équipes d’application ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="c46f4-270">Quelle sera la procédure ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-270">What will the process be?</span></span>
- <span data-ttu-id="c46f4-271">Automatiserez-vous l’empaquetage, la copie et la création d’une somme de contrôle pour les modules DSC prêts pour la production sur le serveur, à partir de votre dépôt source ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>
- <span data-ttu-id="c46f4-272">Votre équipe sera-t-elle également responsable de la gestion de la plateforme d’automatisation ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-272">Will your team be responsible for managing the automation platform as well?</span></span>

#### <a name="dsc-configurations"></a><span data-ttu-id="c46f4-273">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="c46f4-273">DSC configurations</span></span>

<span data-ttu-id="c46f4-274">Le rôle d’un serveur collecteur est de fournir un mécanisme centralisé pour la distribution des configurations DSC aux nœuds du client.</span><span class="sxs-lookup"><span data-stu-id="c46f4-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="c46f4-275">Les configurations sont stockées sur le serveur sous la forme de documents MOF.</span><span class="sxs-lookup"><span data-stu-id="c46f4-275">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="c46f4-276">Chaque document est nommé avec un **Guid** unique.</span><span class="sxs-lookup"><span data-stu-id="c46f4-276">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="c46f4-277">Quand les clients sont configurés pour se connecter à un serveur Pull, ils reçoivent également le **Guid** pour la configuration qu’ils doivent demander.</span><span class="sxs-lookup"><span data-stu-id="c46f4-277">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="c46f4-278">Ce système de référencement des configurations par **Guid** garantit que chaque configuration est unique. Il offre aussi une flexibilité certaine, car il permet d’appliquer aussi bien une configuration avec une granularité spécifique par nœud qu’une configuration de rôle englobant plusieurs serveurs qui doivent avoir des configurations identiques.</span><span class="sxs-lookup"><span data-stu-id="c46f4-278">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="c46f4-279">Guids</span><span class="sxs-lookup"><span data-stu-id="c46f4-279">Guids</span></span>

<span data-ttu-id="c46f4-280">Il convient d’apporter une attention supplémentaire à la planification des **Guids** de configuration lors de l’examen détaillé du déploiement d’un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="c46f4-280">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="c46f4-281">Il n’existe aucune exigence spécifique concernant la façon de gérer les **Guids** , et il est probable que le processus sera propre à chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="c46f4-281">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="c46f4-282">Le processus peut aller du simple au complexe : un fichier CSV stocké de manière centralisée, une table SQL simple, une base de données de gestion des configurations (CMDB) ou une solution complexe nécessitant l’intégration à un autre outil ou une autre solution logicielle.</span><span class="sxs-lookup"><span data-stu-id="c46f4-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="c46f4-283">Il existe deux approches générales :</span><span class="sxs-lookup"><span data-stu-id="c46f4-283">There are two general approaches:</span></span>

- <span data-ttu-id="c46f4-284">**Affectation de Guids par serveur** : fournit un moyen de garantir que chaque configuration de serveur est contrôlée individuellement.</span><span class="sxs-lookup"><span data-stu-id="c46f4-284">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="c46f4-285">Cette approche fournit un niveau de précision autour des mises à jour et peut fonctionner correctement dans les environnements comportant peu de serveurs.</span><span class="sxs-lookup"><span data-stu-id="c46f4-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="c46f4-286">**Affectation de Guids par rôle serveur** : tous les serveurs qui exécutent la même fonction, tels que les serveurs web, utilisent le même GUID pour référencer les données de configuration nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c46f4-286">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span> <span data-ttu-id="c46f4-287">Sachez que si de nombreux serveurs partagent le même GUID, tous sont mis à jour simultanément quand la configuration change.</span><span class="sxs-lookup"><span data-stu-id="c46f4-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="c46f4-288">Le GUID doit être considéré comme une donnée sensible, car il peut être exploité par une personne ayant des intentions malveillantes pour recueillir des informations sur la façon dont les serveurs sont déployés et configurés dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="c46f4-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="c46f4-289">Pour plus d’informations, consultez [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://devblogs.microsoft.com/powershell/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Allocation de Guids de manière sécurisée dans la configuration de l’état désiré de PowerShell en mode Pull).</span><span class="sxs-lookup"><span data-stu-id="c46f4-289">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://devblogs.microsoft.com/powershell/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="c46f4-290">Tâche de planification</span><span class="sxs-lookup"><span data-stu-id="c46f4-290">Planning task</span></span>

- <span data-ttu-id="c46f4-291">Qui sera chargé de la copie des configurations dans le dossier des serveurs collecteurs quand elles seront prêtes ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>
- <span data-ttu-id="c46f4-292">Si les configurations sont créées par une équipe d’application, quelle sera la procédure pour les transmettre ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>
- <span data-ttu-id="c46f4-293">Allez-vous exploiter un dépôt pour stocker les configurations à mesure qu’elles seront créées, entre les équipes ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>
- <span data-ttu-id="c46f4-294">Allez-vous automatiser le processus de copie des configurations sur le serveur et de création d’une somme de contrôle quand elles seront prêtes ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>
- <span data-ttu-id="c46f4-295">Comment mapperez-vous les Guids à des serveurs ou des rôles, et où seront-ils stockés ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-295">How will you map Guids to servers or roles, and where will this be stored?</span></span>
- <span data-ttu-id="c46f4-296">Quel processus allez-vous utiliser pour configurer les machines clients et comment s’intégreront-elles à votre processus de création et de stockage de Guids de configuration ?</span><span class="sxs-lookup"><span data-stu-id="c46f4-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>

## <a name="installation-guide"></a><span data-ttu-id="c46f4-297">Guide d'installation</span><span class="sxs-lookup"><span data-stu-id="c46f4-297">Installation Guide</span></span>

<span data-ttu-id="c46f4-298">*Les scripts fournis dans ce document sont des exemples stables. Examinez toujours attentivement les scripts avant de les exécuter dans un environnement de production.*</span><span class="sxs-lookup"><span data-stu-id="c46f4-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c46f4-299">Prérequis</span><span class="sxs-lookup"><span data-stu-id="c46f4-299">Prerequisites</span></span>

<span data-ttu-id="c46f4-300">Pour vérifier la version de PowerShell installée sur votre serveur, utilisez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c46f4-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="c46f4-301">Si possible, effectuez une mise à niveau avec la version la plus récente de Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="c46f4-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span> <span data-ttu-id="c46f4-302">Téléchargez ensuite le module `xPsDesiredStateConfiguration` à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c46f4-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="c46f4-303">La commande vous demande votre approbation avant de télécharger le module.</span><span class="sxs-lookup"><span data-stu-id="c46f4-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="c46f4-304">Installation et configuration de scripts</span><span class="sxs-lookup"><span data-stu-id="c46f4-304">Installation and configuration scripts</span></span>

<span data-ttu-id="c46f4-305">La meilleure méthode pour déployer un serveur collecteur DSC consiste à utiliser un script de configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="c46f4-306">Ce document présente les scripts, notamment les paramètres de base permettant de configurer uniquement le service web DSC et les paramètres avancés permettant de configurer de bout en bout Windows Server comprenant un service web DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f4-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="c46f4-307">Remarque : Actuellement, le module DSC `xPSDesiredStateConfiguration` exige que le serveur utilise les paramètres régionaux en-US.</span><span class="sxs-lookup"><span data-stu-id="c46f4-307">Note: Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="c46f4-308">Configuration de base pour Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c46f4-308">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="c46f4-309">Configuration avancée pour Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c46f4-309">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="c46f4-310">Vérifier les fonctionnalités du serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="c46f4-310">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="c46f4-311">Configurer les clients</span><span class="sxs-lookup"><span data-stu-id="c46f4-311">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="c46f4-312">Références, extraits de code et exemples supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c46f4-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="c46f4-313">Cet exemple montre comment démarrer manuellement une connexion au client (nécessitant WMF5) pour les tests.</span><span class="sxs-lookup"><span data-stu-id="c46f4-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="c46f4-314">L’applet de commande [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) est utilisée pour ajouter un enregistrement CNAME de type à une zone DNS.</span><span class="sxs-lookup"><span data-stu-id="c46f4-314">The [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="c46f4-315">La fonction PowerShell permettant de [créer une somme de contrôle et de publier un document MOF DSC sur un serveur collecteur SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) génère automatiquement la somme de contrôle exigée, puis copie les fichiers de configuration MOF et de somme de contrôle sur le serveur collecteur SMB.</span><span class="sxs-lookup"><span data-stu-id="c46f4-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="c46f4-316">Annexe - Présentation des types de fichiers de données du service ODATA</span><span class="sxs-lookup"><span data-stu-id="c46f4-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="c46f4-317">Un fichier de données est stocké pour créer des informations pendant le déploiement d’un serveur collecteur qui inclut le service web OData.</span><span class="sxs-lookup"><span data-stu-id="c46f4-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="c46f4-318">Le type de fichier dépend du système d’exploitation, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c46f4-318">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="c46f4-319">**Windows Server 2012** - Le type de fichier est toujours `.mdb`</span><span class="sxs-lookup"><span data-stu-id="c46f4-319">**Windows Server 2012** - The file type will always be `.mdb`</span></span>
- <span data-ttu-id="c46f4-320">**Windows Server 2012 R2** - Le type de fichier est `.edb` par défaut, sauf si le type `.mdb` est spécifié dans la configuration</span><span class="sxs-lookup"><span data-stu-id="c46f4-320">**Windows Server 2012 R2** - The file type will default to `.edb` unless a `.mdb` is specified in the configuration</span></span>

<span data-ttu-id="c46f4-321">Dans l’[exemple de script avancé](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) d’installation un serveur collecteur, vous trouverez également un exemple de la façon de contrôler automatiquement les paramètres du fichier web.config pour empêcher tout risque d’erreur provoquée par le type de fichier.</span><span class="sxs-lookup"><span data-stu-id="c46f4-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
