---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="8c8c0-102">Séparation des ID de nœud et de configuration</span><span class="sxs-lookup"><span data-stu-id="8c8c0-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="8c8c0-103">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="8c8c0-103">Overview</span></span>

<span data-ttu-id="8c8c0-104">Afin d’offrir une expérience plus flexible et rationalisée lors de l’utilisation de DSC en mode par extraction, nous avons ajouté un certain nombre de fonctionnalités dans cette version.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="8c8c0-105">Ces fonctionnalités ont pour but de vous aider à configurer et à déployer des configurations sur plusieurs nœuds de manière simple et flexible, tout en assurant le suivi et en fournissant des informations pour chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="8c8c0-106">Il s’agit des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c8c0-106">These features are as follows:</span></span>

* <span data-ttu-id="8c8c0-107">Un nom de configuration qui identifie la configuration d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="8c8c0-108">Ce nom peut être partagé par plusieurs nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="8c8c0-109">Un ID d’agent qui identifie de façon unique un nœud unique.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="8c8c0-110">Une étape d’inscription qui est exécutée uniquement la première fois qu’un nœud cible se connecte à un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="8c8c0-111">**Remarque :** Ces fonctionnalités ont été ajoutées et ne remplacent pas les fonctionnalités et les concepts d’extraction existants.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="8c8c0-112">Vous pouvez utiliser ces nouvelles fonctionnalités ou les anciennes avec le nouveau serveur collecteur fourni avec cette version.</span><span class="sxs-lookup"><span data-stu-id="8c8c0-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="8c8c0-113">Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide du nom de configuration](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).</span><span class="sxs-lookup"><span data-stu-id="8c8c0-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>