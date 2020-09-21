---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Présentation du rôle de DSC dans un pipeline CI/CD
ms.openlocfilehash: 6df621f45caed3ac8a8b4dd1afa575d413259e0d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783107"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="198a6-103">Présentation du rôle de DSC dans un pipeline CI/CD</span><span class="sxs-lookup"><span data-stu-id="198a6-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="198a6-104">Cet article décrit les différents types d’approches disponibles pour combiner des configurations et des ressources.</span><span class="sxs-lookup"><span data-stu-id="198a6-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="198a6-105">Dans chaque scénario, l’objectif est le même : réduire la complexité quand plusieurs configurations préférées existent pour parvenir à un état de fin de déploiement de serveur.</span><span class="sxs-lookup"><span data-stu-id="198a6-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span> <span data-ttu-id="198a6-106">Pour illustrer cela, citons par exemple un déploiement de serveur auquel participent plusieurs équipes, avec un propriétaire d’application qui gère l’état de l’application et une équipe centrale chargée de publier les modifications apportées aux bases de référence de sécurité.</span><span class="sxs-lookup"><span data-stu-id="198a6-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span> <span data-ttu-id="198a6-107">Les nuances de chaque approche, notamment les avantages et les risques qui leur sont associés, sont détaillés ici.</span><span class="sxs-lookup"><span data-stu-id="198a6-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Flux de processus d’un pipeline CI/CD](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="198a6-109">Types de techniques de création collaborative</span><span class="sxs-lookup"><span data-stu-id="198a6-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="198a6-110">Deux solutions intégrées au gestionnaire de configuration local permettent de mettre en œuvre ce concept :</span><span class="sxs-lookup"><span data-stu-id="198a6-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

|        <span data-ttu-id="198a6-111">Concept</span><span class="sxs-lookup"><span data-stu-id="198a6-111">Concept</span></span>         |                    <span data-ttu-id="198a6-112">Informations détaillées</span><span class="sxs-lookup"><span data-stu-id="198a6-112">Detailed Information</span></span>                     |
| ---------------------- | ----------------------------------------------------------- |
| <span data-ttu-id="198a6-113">Configurations partielles</span><span class="sxs-lookup"><span data-stu-id="198a6-113">Partial Configurations</span></span> | [<span data-ttu-id="198a6-114">Documentation</span><span class="sxs-lookup"><span data-stu-id="198a6-114">Documentation</span></span>](../pull-server/partialConfigs.md)           |
| <span data-ttu-id="198a6-115">Ressources composites</span><span class="sxs-lookup"><span data-stu-id="198a6-115">Composite Resources</span></span>    | [<span data-ttu-id="198a6-116">Documentation</span><span class="sxs-lookup"><span data-stu-id="198a6-116">Documentation</span></span>](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="198a6-117">Comprendre l’impact de chaque approche</span><span class="sxs-lookup"><span data-stu-id="198a6-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="198a6-118">Chacune de ces solutions permet de gérer l’issue d’un déploiement de serveur.</span><span class="sxs-lookup"><span data-stu-id="198a6-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span> <span data-ttu-id="198a6-119">Cependant, chaque approche a un impact très différent.</span><span class="sxs-lookup"><span data-stu-id="198a6-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="198a6-120">Configurations partielles</span><span class="sxs-lookup"><span data-stu-id="198a6-120">Partial Configurations</span></span>

<span data-ttu-id="198a6-121">Quand vous utilisez des configurations partielles, le gestionnaire de configuration local est configuré pour gérer plusieurs configurations de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="198a6-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span> <span data-ttu-id="198a6-122">Les configurations sont compilées de manière indépendante avant d’être affectées au nœud.</span><span class="sxs-lookup"><span data-stu-id="198a6-122">Configurations are compiled independently and then assigned to the node.</span></span> <span data-ttu-id="198a6-123">Le gestionnaire de configuration local doit pour cela être configuré à l’avance avec le nom de chaque configuration.</span><span class="sxs-lookup"><span data-stu-id="198a6-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![Diagramme des configurations partielles](media/authoringAdvanced/PartialConfiguration.jpg)

<span data-ttu-id="198a6-125">Les configurations partielles permettent à deux équipes ou plus de contrôler entièrement la configuration d’un serveur, souvent sans l’avantage de la communication ou de la collaboration.</span><span class="sxs-lookup"><span data-stu-id="198a6-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="198a6-126">Des clients nous ont affirmé que cela pouvait occasionner des conflits de ressources, des remplacements involontaires et en fin de compte une véritable perte de contrôle de la configuration de la ressource.</span><span class="sxs-lookup"><span data-stu-id="198a6-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="198a6-127">De plus, en utilisant ce modèle, les modifications de configuration des équipes de contrôle ont peu de chances d’être entièrement testées via un pipeline de mise en production, ce qui conduit à des résultats inattendus en production.</span><span class="sxs-lookup"><span data-stu-id="198a6-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="198a6-128">**Il est très important d’utiliser un seul pipeline pour évaluer si toutes les modifications sont publiées sur les serveurs.**</span><span class="sxs-lookup"><span data-stu-id="198a6-128">**It is critical that a single pipeline be used to evaluate all changes released to servers.**</span></span>

<span data-ttu-id="198a6-129">Dans l’illustration ci-dessous, l’équipe B transmet sa configuration partielle à l’équipe A. L’équipe A exécute alors ses tests sur un serveur en appliquant les deux configurations.</span><span class="sxs-lookup"><span data-stu-id="198a6-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span> <span data-ttu-id="198a6-130">Dans ce modèle, une seule autorité est autorisée à apporter des modifications en production.</span><span class="sxs-lookup"><span data-stu-id="198a6-130">In this model, only one authority has permission to make changes in production.</span></span>

![Diagramme d’un pipeline unique partiel](media/authoringAdvanced/PartialSinglePipeline.jpg)

<span data-ttu-id="198a6-132">Quand l’équipe B réclame des modifications, elle doit envoyer une demande de tirage (pull request) à l’environnement de contrôle de code source de l’équipe A.</span><span class="sxs-lookup"><span data-stu-id="198a6-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span> <span data-ttu-id="198a6-133">L’équipe A examine alors les modifications à l’aide de l’automation de test et les met en production dès qu’elle a l’assurance que les modifications n’entraîneront pas d’erreurs dans les applications ou les services hébergés par le serveur.</span><span class="sxs-lookup"><span data-stu-id="198a6-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="198a6-134">Ressources composites</span><span class="sxs-lookup"><span data-stu-id="198a6-134">Composite Resources</span></span>

<span data-ttu-id="198a6-135">Une ressource composite consiste simplement en une configuration DSC empaquetée comme ressource.</span><span class="sxs-lookup"><span data-stu-id="198a6-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span> <span data-ttu-id="198a6-136">Il n’existe aucune exigence de configuration particulière pour faire accepter les ressources composites au gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="198a6-136">There are no special requirements for configuring LCM to accept composite resources.</span></span> <span data-ttu-id="198a6-137">Celle-ci sont utilisées dans une nouvelle configuration et chaque compilation génère un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="198a6-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![Diagramme d’une ressource composite](media/authoringAdvanced/CompositeResource.jpg)

<span data-ttu-id="198a6-139">Il existe deux scénarios courants pour les ressources composites.</span><span class="sxs-lookup"><span data-stu-id="198a6-139">There are two common scenarios for composite resources.</span></span> <span data-ttu-id="198a6-140">Le premier vise à réduire la complexité et les concepts uniques et abstraits.</span><span class="sxs-lookup"><span data-stu-id="198a6-140">The first is to reduce complexity and abstract unique concepts.</span></span> <span data-ttu-id="198a6-141">Le deuxième vise à permettre l’empaquetage des bases de référence pour que l’équipe d’une application puisse la déployer en toute sécurité via son pipeline de mise en production une fois que tous les tests ont réussi.</span><span class="sxs-lookup"><span data-stu-id="198a6-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

<span data-ttu-id="198a6-142">Les ressources composites facilitent la composition et la collaboration au moyen d’un pipeline tout en développant la maturité opérationnelle.</span><span class="sxs-lookup"><span data-stu-id="198a6-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity.</span></span>

<span data-ttu-id="198a6-143">Vous utilisez peut-être déjà des ressources composites sans le savoir.</span><span class="sxs-lookup"><span data-stu-id="198a6-143">You might be already using composite resources without realizing it.</span></span> <span data-ttu-id="198a6-144">**ServiceSet** en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="198a6-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="198a6-145">Cette ressource gère l’état de plusieurs services Windows sans les mentionner individuellement.</span><span class="sxs-lookup"><span data-stu-id="198a6-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span> <span data-ttu-id="198a6-146">La propriété Name accepte un tableau de chaînes pour fournir le nom de chaque service.</span><span class="sxs-lookup"><span data-stu-id="198a6-146">The Name property accepts an array of strings to provide the name of each service.</span></span> <span data-ttu-id="198a6-147">Une fois la configuration compilée, le fichier MOF contient une section Service pour chaque nom communiqué à ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="198a6-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="198a6-148">Les organisations peuvent avoir des « agents » ou des « intergiciels (middleware) » à installer sur chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="198a6-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span> <span data-ttu-id="198a6-149">Une ressource composite est la meilleure réponse pour gérer les dépendances, l’installation et la configuration de ces outils et utilitaires.</span><span class="sxs-lookup"><span data-stu-id="198a6-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="198a6-150">La personne ou l’équipe en charge des solutions qui englobent plusieurs serveurs crée une configuration qui intègre leurs exigences.</span><span class="sxs-lookup"><span data-stu-id="198a6-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span> <span data-ttu-id="198a6-151">Ensuite, la configuration est empaquetée sous forme de ressource composite selon les instructions fournies dans la documentation sur les ressources composites.</span><span class="sxs-lookup"><span data-stu-id="198a6-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span> <span data-ttu-id="198a6-152">Enfin, la nouvelle ressource composite doit être publiée à un emplacement, par exemple dans un partage de fichiers ou un flux NuGet, d’où elle peut être utilisée dans les configurations des équipes de l’application.</span><span class="sxs-lookup"><span data-stu-id="198a6-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="198a6-153">Chaque fois qu’une équipe publie une nouvelle version, elle incrémente le numéro de version dans le manifeste de module de leur ressource composite.</span><span class="sxs-lookup"><span data-stu-id="198a6-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span> <span data-ttu-id="198a6-154">Les équipes de l’application incluent la ressource composite dans la configuration qu’elles créent pour gérer les dépendances de l’application.</span><span class="sxs-lookup"><span data-stu-id="198a6-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span> <span data-ttu-id="198a6-155">Quand les équipes en charge des opérations et/ou de la sécurité publient une nouvelle version de leur ressource, elles adressent une notification aux équipes de l’application pour les informer de la nouvelle modification.</span><span class="sxs-lookup"><span data-stu-id="198a6-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="198a6-156">Les équipes de l’application peuvent déclencher une mise en production si la modification porte uniquement sur les bases de référence.</span><span class="sxs-lookup"><span data-stu-id="198a6-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="198a6-157">Cependant, cela donne l’occasion d’évaluer l’impact sur l’application avant de risquer une interruption de service.</span><span class="sxs-lookup"><span data-stu-id="198a6-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

> [!NOTE]
> <span data-ttu-id="198a6-158">L’utilisation des ressources composites a fait l’objet de commentaires critiques eu égard à la nécessité de compiler et de publier un nouveau fichier MOF à la suite de modifications.</span><span class="sxs-lookup"><span data-stu-id="198a6-158">Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span> <span data-ttu-id="198a6-159">C'est la procédure normale.</span><span class="sxs-lookup"><span data-stu-id="198a6-159">This is by design.</span></span> <span data-ttu-id="198a6-160">Chaque publication d’une nouvelle version doit inclure une référence statique à une version spécifique de chaque ressource et doit être validée par des tests avant d’être transmise aux nœuds du serveur de production.</span><span class="sxs-lookup"><span data-stu-id="198a6-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span> <span data-ttu-id="198a6-161">Le processus de test et de publication des modifications à partir du contrôle de code source crée un environnement sécurisé pour publier les modifications par lots de petite taille mais fréquents.</span><span class="sxs-lookup"><span data-stu-id="198a6-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="198a6-162">Pour plus d’informations sur l’utilisation des pipelines de mise en production pour gérer l’infrastructure de base, consultez le livre blanc [The Release Pipeline Model](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="198a6-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
