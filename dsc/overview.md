---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell"
ms.openlocfilehash: 154a3c78a9bf2a029577ca6862f333b6bfe69878
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="ea57d-103">Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea57d-103">Windows PowerShell Desired State Configuration Overview</span></span> 

> <span data-ttu-id="ea57d-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ea57d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ea57d-105">DSC est une plateforme de gestion dans PowerShell qui vous permet de gérer votre infrastructure informatique et de développement avec la configuration en tant que code.</span><span class="sxs-lookup"><span data-stu-id="ea57d-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="ea57d-106">Pour une vue d’ensemble des avantages métier de DSC, consultez [Présentation de la configuration de l’état souhaité pour les décideurs](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="ea57d-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="ea57d-107">Pour une vue d’ensemble des avantages de l’utilisation de DSC en termes d’ingénierie, consultez [Présentation de la configuration de l’état souhaité pour les ingénieurs](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="ea57d-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="ea57d-108">Pour commencer à utiliser rapidement DSC, consultez [Démarrage rapide avec DSC](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="ea57d-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="ea57d-109">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="ea57d-109">Key Concepts</span></span>

<span data-ttu-id="ea57d-110">DSC est une plateforme déclarative employée pour la configuration, le déploiement et la gestion des systèmes.</span><span class="sxs-lookup"><span data-stu-id="ea57d-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="ea57d-111">Elle réunit trois composants principaux :</span><span class="sxs-lookup"><span data-stu-id="ea57d-111">It consists of three primary components:</span></span>

- <span data-ttu-id="ea57d-112">Les [configurations](configurations.md) sont des scripts PowerShell déclaratifs qui définissent et configurent des instances de ressources.</span><span class="sxs-lookup"><span data-stu-id="ea57d-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="ea57d-113">Quand une configuration est exécutée, DSC (et toutes les ressources appelées par cette configuration) « fait simplement en sorte » que le système se trouve dans l’état souhaité défini par la configuration.</span><span class="sxs-lookup"><span data-stu-id="ea57d-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span> 
    <span data-ttu-id="ea57d-114">Les configurations DSC sont également idempotent, c’est-à-dire que le Gestionnaire de configuration local (ou « LCM ») s’assure en permanence que les machines restent configurées dans l’état déclaré dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ea57d-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="ea57d-115">Les [ressources](resources.md) constituent la base de DSC.</span><span class="sxs-lookup"><span data-stu-id="ea57d-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="ea57d-116">Elles contiennent le code qui place et conserve la cible d’une configuration dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="ea57d-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span> 
    <span data-ttu-id="ea57d-117">Les ressources sont stockées dans les modules PowerShell et peuvent être créées pour modéliser des éléments généraux, comme un fichier ou un processus Windows, ou des éléments plus spécifiques, tels qu’un serveur IIS ou une machine virtuelle Azure.</span><span class="sxs-lookup"><span data-stu-id="ea57d-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="ea57d-118">Le [LCM](metaConfig.md) est le moteur utilisé par DSC pour faciliter les interactions entre les ressources et les configurations.</span><span class="sxs-lookup"><span data-stu-id="ea57d-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span> 
    <span data-ttu-id="ea57d-119">Le LCM interroge régulièrement le système, via le flux de contrôle implémenté par les ressources, pour s’assurer que le système est dans l’état déclaré dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="ea57d-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span> 
    <span data-ttu-id="ea57d-120">Si le système n’est pas dans l’état souhaité, le LCM effectue des appels aux code dans les ressources pour « faire en sorte » qu’il soit conforme à l’état déclaré dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ea57d-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span> 

## <a name="see-also"></a><span data-ttu-id="ea57d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea57d-121">See Also</span></span>

- [<span data-ttu-id="ea57d-122">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="ea57d-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ea57d-123">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="ea57d-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="ea57d-124">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="ea57d-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

