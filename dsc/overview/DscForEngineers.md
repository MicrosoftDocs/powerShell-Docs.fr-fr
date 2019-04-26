---
ms.date: 10/13/2017
keywords: dsc,powershell,configuration,setup
title: Présentation de la configuration de l’état souhaité pour les ingénieurs
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079970"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="a4568-103">Présentation de la configuration de l’état souhaité pour les ingénieurs</span><span class="sxs-lookup"><span data-stu-id="a4568-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="a4568-104">Ce document est destiné à faire découvrir aux développeurs et équipes opérationnelles les avantages de la configuration d’état souhaité (DSC) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4568-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="a4568-105">Pour une vision plus globale des avantages offerts par DSC, consultez la section [Présentation de la configuration de l’état souhaité pour les décideurs](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="a4568-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="a4568-106">Avantages de la configuration de l’état souhaité</span><span class="sxs-lookup"><span data-stu-id="a4568-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="a4568-107">Objectifs de DSC :</span><span class="sxs-lookup"><span data-stu-id="a4568-107">DSC exists to:</span></span>

- <span data-ttu-id="a4568-108">Réduire la complexité des scripts dans Windows</span><span class="sxs-lookup"><span data-stu-id="a4568-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="a4568-109">Accélérer la vitesse d’itération</span><span class="sxs-lookup"><span data-stu-id="a4568-109">Increase the speed of iteration</span></span>

<span data-ttu-id="a4568-110">Le concept de « déploiement continu » gagne en importance.</span><span class="sxs-lookup"><span data-stu-id="a4568-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="a4568-111">Grâce au déploiement continu, il est possible de procéder à des déploiements fréquents, potentiellement plusieurs fois par jour.</span><span class="sxs-lookup"><span data-stu-id="a4568-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="a4568-112">L’objectif de ces déploiements n’est pas de réparer quoi que ce soit, mais de permettre des publications plus rapides.</span><span class="sxs-lookup"><span data-stu-id="a4568-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="a4568-113">En développant de nouvelles fonctionnalités et en les rendant opérationnelles aussi rapidement et efficacement que possible, vous accélérez le retour sur investissement de cette nouvelle logique métier.</span><span class="sxs-lookup"><span data-stu-id="a4568-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="a4568-114">Le passage au cloud computing implique une solution de déploiement qui utilise un modèle « déclaratif », où un environnement final est déclaré en tant que texte et publié sur un moteur de déploiement.</span><span class="sxs-lookup"><span data-stu-id="a4568-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="a4568-115">Cette technique de déploiement permet des modifications rapides à grande échelle, avec une résilience contre les menaces de défaillance, puisque le déploiement peut être répété à tout moment de manière cohérente pour garantir un état final.</span><span class="sxs-lookup"><span data-stu-id="a4568-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="a4568-116">La création d’outils et de services prenant en charge ce type d’opérations par le biais de l’automatisation est une réponse à ces modifications.</span><span class="sxs-lookup"><span data-stu-id="a4568-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="a4568-117">DSC est une plateforme assurant des opérations de déploiement, de configuration et de conformité déclaratives et idempotentes (reproductibles).</span><span class="sxs-lookup"><span data-stu-id="a4568-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="a4568-118">La plateforme DSC permet de garantir que les composants de votre centre de données sont configurés correctement, ce qui évite des erreurs et de coûteux échecs de déploiement.</span><span class="sxs-lookup"><span data-stu-id="a4568-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="a4568-119">En traitant les configurations DSC dans le cadre du code de l’application, DSC permet un déploiement continu.</span><span class="sxs-lookup"><span data-stu-id="a4568-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="a4568-120">La configuration DSC doit être mise à jour directement dans l’application, en veillant à ce que les données nécessaires au déploiement de l’application soient toujours à jour et prêtes à être utilisées.</span><span class="sxs-lookup"><span data-stu-id="a4568-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="a4568-121">« Je dispose de PowerShell, pourquoi ai-je besoin de la configuration de l’état souhaité ? »</span><span class="sxs-lookup"><span data-stu-id="a4568-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="a4568-122">Les configurations DSC font la distinction entre l’intention (« Ce que je veux effectuer » et l’exécution (« Comment je veux l’effectuer »).</span><span class="sxs-lookup"><span data-stu-id="a4568-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="a4568-123">Cela signifie que la logique d’exécution est contenue dans les ressources.</span><span class="sxs-lookup"><span data-stu-id="a4568-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="a4568-124">Les utilisateurs n’ont pas besoin de savoir implémenter ou déployer une fonctionnalité lorsqu’une ressource DSC pour cette fonctionnalité est disponible.</span><span class="sxs-lookup"><span data-stu-id="a4568-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="a4568-125">Cela permet à l’utilisateur de se concentrer sur la structure de son déploiement.</span><span class="sxs-lookup"><span data-stu-id="a4568-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="a4568-126">Par exemple, les scripts PowerShell doivent ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="a4568-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="a4568-127">Ce script est simple, aisément compréhensible et direct.</span><span class="sxs-lookup"><span data-stu-id="a4568-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="a4568-128">Toutefois, si vous tentez de mettre ce script en production, vous rencontrerez plusieurs problèmes.</span><span class="sxs-lookup"><span data-stu-id="a4568-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="a4568-129">Que se passe-t-il si ce script est exécuté deux fois de suite ?</span><span class="sxs-lookup"><span data-stu-id="a4568-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="a4568-130">Que se passe-t-il si Bob avait précédemment un accès complet au partage ?</span><span class="sxs-lookup"><span data-stu-id="a4568-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="a4568-131">Pour compenser ces problèmes, une version « réelle » du script ressemblera davantage à ceci :</span><span class="sxs-lookup"><span data-stu-id="a4568-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="a4568-132">Ce script est plus complexe, avec une grande quantité de logiques et d’erreurs à gérer.</span><span class="sxs-lookup"><span data-stu-id="a4568-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="a4568-133">Le script est plus complexe, car vous n’indiquez plus ce que vous voulez effectuer, mais *comment l’effectuer*.</span><span class="sxs-lookup"><span data-stu-id="a4568-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="a4568-134">DSC vous permet de dire ce que vous voulez effectuer, et il est fait abstraction de la logique sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="a4568-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="a4568-135">Ce script est mis en forme proprement et facile à lire.</span><span class="sxs-lookup"><span data-stu-id="a4568-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="a4568-136">Les chemins d’accès logiques et la gestion des erreurs sont toujours présents dans l’implémentation des [ressources](../resources/resources.md), mais invisibles pour le créateur du script.</span><span class="sxs-lookup"><span data-stu-id="a4568-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="a4568-137">Distinction entre environnement et structure</span><span class="sxs-lookup"><span data-stu-id="a4568-137">Separating Environment from Structure</span></span>

<span data-ttu-id="a4568-138">Dans DevOps, un schéma fréquent consiste à disposer de plusieurs environnements pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="a4568-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="a4568-139">Par exemple, un environnement de développement peut être utilisé pour créer rapidement le prototype d’un nouveau code.</span><span class="sxs-lookup"><span data-stu-id="a4568-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="a4568-140">Le code de l’environnement de développement se retrouve dans un environnement de test, où d’autres personnes vérifient les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="a4568-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="a4568-141">Enfin, le code passe en production, autrement dit dans l’environnement de production du site en ligne.</span><span class="sxs-lookup"><span data-stu-id="a4568-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="a4568-142">Les configurations DSC s’adaptent à ce système développement-test-production par l’utilisation des [données de configuration](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="a4568-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="a4568-143">Cela précise encore davantage la distinction entre la structure de la configuration et les nœuds gérés.</span><span class="sxs-lookup"><span data-stu-id="a4568-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="a4568-144">Par exemple, vous pouvez définir une configuration qui nécessite un serveur SQL, un serveur IIS et un serveur de couche intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="a4568-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="a4568-145">Quels que soient les nœuds qui reçoivent les différents éléments de cette configuration, ces trois éléments seront toujours présents.</span><span class="sxs-lookup"><span data-stu-id="a4568-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="a4568-146">Vous pouvez utiliser des données de configuration pour pointer les trois éléments vers le même ordinateur d’un environnement de développement, séparer ces trois éléments sur trois ordinateurs différents d’un environnement de test et enfin transférer l’ensemble de vos serveurs de production pour l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="a4568-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="a4568-147">Pour effectuer un déploiement sur les différents environnements, vous pouvez appeler **Start-DscConfiguration** avec les données de configuration appropriées à l’environnement que vous souhaitez cibler.</span><span class="sxs-lookup"><span data-stu-id="a4568-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4568-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4568-148">See Also</span></span>

[<span data-ttu-id="a4568-149">Configurations</span><span class="sxs-lookup"><span data-stu-id="a4568-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="a4568-150">Données de configuration</span><span class="sxs-lookup"><span data-stu-id="a4568-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="a4568-151">Ressources</span><span class="sxs-lookup"><span data-stu-id="a4568-151">Resources</span></span>](../resources/resources.md)
