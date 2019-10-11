---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager, classe
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953266"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a><span data-ttu-id="b95b7-103">MSFT_DSCLocalConfigurationManager, classe</span><span class="sxs-lookup"><span data-stu-id="b95b7-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b95b7-104">Gestionnaire de configuration local qui contrôle les états des fichiers de configuration et utilise l’agent de configuration pour appliquer les configurations.</span><span class="sxs-lookup"><span data-stu-id="b95b7-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="b95b7-105">La syntaxe suivante est simplifiée par rapport au code MOF (Managed Object Format) et inclut toutes les propriétés héritées.</span><span class="sxs-lookup"><span data-stu-id="b95b7-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="b95b7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b95b7-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="b95b7-107">Members</span><span class="sxs-lookup"><span data-stu-id="b95b7-107">Members</span></span>

<span data-ttu-id="b95b7-108">La classe **MSFT_DSCLocalConfigurationManager** comprend les membres suivants :</span><span class="sxs-lookup"><span data-stu-id="b95b7-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="b95b7-109">[Méthodes][]</span><span class="sxs-lookup"><span data-stu-id="b95b7-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="b95b7-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b95b7-110">Methods</span></span>

<span data-ttu-id="b95b7-111">La classe **MSFT_DSCLocalConfigurationManager** comprend les méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b95b7-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="b95b7-112">Méthode</span><span class="sxs-lookup"><span data-stu-id="b95b7-112">Method</span></span> |<span data-ttu-id="b95b7-113">Description</span><span class="sxs-lookup"><span data-stu-id="b95b7-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="b95b7-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="b95b7-115">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="b95b7-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="b95b7-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="b95b7-117">Désactive le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="b95b7-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="b95b7-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="b95b7-119">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="b95b7-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="b95b7-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="b95b7-121">Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="b95b7-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="b95b7-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="b95b7-123">Obtient la sortie de l’agent de configuration associée à un travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="b95b7-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="b95b7-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b95b7-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="b95b7-125">Obtenez l’historique des états de la configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="b95b7-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="b95b7-127">Obtient les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="b95b7-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b95b7-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="b95b7-129">Démarre la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="b95b7-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="b95b7-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="b95b7-131">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="b95b7-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="b95b7-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="b95b7-133">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="b95b7-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="b95b7-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="b95b7-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="b95b7-135">Appelle directement la méthode **Set** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="b95b7-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="b95b7-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="b95b7-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="b95b7-137">Appelle directement la méthode **Test** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="b95b7-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="b95b7-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="b95b7-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="b95b7-139">Restaure une configuration précédente.</span><span class="sxs-lookup"><span data-stu-id="b95b7-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="b95b7-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="b95b7-141">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="b95b7-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="b95b7-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="b95b7-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="b95b7-143">Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="b95b7-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="b95b7-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="b95b7-145">Envoyez le document de configuration au nœud géré et commencez à utiliser l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="b95b7-146">Utilisez GetConfigurationResultOutput pour récupérer la sortie du résultat.</span><span class="sxs-lookup"><span data-stu-id="b95b7-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="b95b7-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="b95b7-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="b95b7-148">Définit les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="b95b7-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="b95b7-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="b95b7-150">Arrête la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="b95b7-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="b95b7-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="b95b7-152">Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.</span><span class="sxs-lookup"><span data-stu-id="b95b7-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="b95b7-153">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b95b7-153">Requirements</span></span>

<span data-ttu-id="b95b7-154">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b95b7-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b95b7-155">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b95b7-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
