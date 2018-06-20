---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190245"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="ba34b-103">Utilisation de DSC sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="ba34b-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="ba34b-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ba34b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ba34b-105">**DSC sur Nano Server** est un package facultatif dans le dossier `NanoServer\Packages` du support Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="ba34b-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="ba34b-106">Le package peut être installé lorsque vous créez un disque dur virtuel pour Nano Server en spécifiant **Microsoft-NanoServer-DSC-Package** comme valeur du paramètre **Packages** de la fonction **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="ba34b-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="ba34b-107">Par exemple, si vous créez un disque dur virtuel pour une machine virtuelle, la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="ba34b-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="ba34b-108">Pour plus d’informations sur l’installation et l’utilisation de Nano Server, ainsi que sur le mode de gestion de Nano Server avec la communication à distance PowerShell, voir [Prise en main de Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="ba34b-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="ba34b-109">Fonctionnalités DSC disponibles sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="ba34b-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="ba34b-110">Comme Nano Server ne prend en charge qu’un ensemble limité d’API par rapport à une version complète de Windows Server, DSC sur Nano Server n’a pas exactement les mêmes fonctionnalités que DSC exécuté sur les références complètes pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="ba34b-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="ba34b-111">En effet, DSC sur Nano Server est en cours de développement et ne dispose pas encore de toutes les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ba34b-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

 <span data-ttu-id="ba34b-112">Les fonctionnalités DSC suivantes sont actuellement disponibles sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="ba34b-112">The following DSC features are currently available on Nano Server:</span></span>


* <span data-ttu-id="ba34b-113">Modes par envoi et par extraction</span><span class="sxs-lookup"><span data-stu-id="ba34b-113">Both push and pull modes</span></span>

* <span data-ttu-id="ba34b-114">Toutes les applets de commande DSC qui existent sur une version complète de Windows Server, y compris les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba34b-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
  * [<span data-ttu-id="ba34b-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ba34b-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="ba34b-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ba34b-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)
  * [<span data-ttu-id="ba34b-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="ba34b-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="ba34b-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="ba34b-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [<span data-ttu-id="ba34b-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba34b-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="ba34b-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba34b-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="ba34b-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba34b-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="ba34b-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba34b-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [<span data-ttu-id="ba34b-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="ba34b-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [<span data-ttu-id="ba34b-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba34b-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="ba34b-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba34b-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="ba34b-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="ba34b-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="ba34b-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="ba34b-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="ba34b-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="ba34b-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="ba34b-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="ba34b-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="ba34b-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="ba34b-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="ba34b-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="ba34b-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* <span data-ttu-id="ba34b-132">Compilation de configurations (voir [Configurations DSC](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="ba34b-133">**Problème :** le chiffrement de mot de passe (voir [Sécurisation du fichier MOF](securemof.md)) pendant la compilation de la configuration ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="ba34b-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="ba34b-134">Compilation de métaconfigurations (voir [Configuration du Gestionnaire de configuration local](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="ba34b-135">Exécution d’une ressource sous un contexte utilisateur (voir [Exécution de DSC avec les informations d’identification de l’utilisateur (RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="ba34b-136">Ressources basées sur une classe (voir [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="ba34b-137">Débogage des ressources DSC (voir [Débogage des ressources DSC](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>

  <span data-ttu-id="ba34b-138">**Problème :** ne fonctionne pas si une ressource utilise PsDscRunAsCredential (voir [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="ba34b-139">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="ba34b-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md)

* [<span data-ttu-id="ba34b-140">Contrôle de version de ressources</span><span class="sxs-lookup"><span data-stu-id="ba34b-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="ba34b-141">Client collecteur (configurations et ressources) (voir [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="ba34b-142">Configurations partielles (envoi et extraction)</span><span class="sxs-lookup"><span data-stu-id="ba34b-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="ba34b-143">Rapports au serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="ba34b-143">Reporting to pull server</span></span>](reportServer.md)

* <span data-ttu-id="ba34b-144">Chiffrement de document MOF</span><span class="sxs-lookup"><span data-stu-id="ba34b-144">MOF encryption</span></span>

* <span data-ttu-id="ba34b-145">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="ba34b-145">Event logging</span></span>

* <span data-ttu-id="ba34b-146">Création de rapports DSC Azure Automation</span><span class="sxs-lookup"><span data-stu-id="ba34b-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="ba34b-147">Ressources entièrement fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="ba34b-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="ba34b-148">Archive</span><span class="sxs-lookup"><span data-stu-id="ba34b-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="ba34b-149">Environment</span><span class="sxs-lookup"><span data-stu-id="ba34b-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="ba34b-150">File</span><span class="sxs-lookup"><span data-stu-id="ba34b-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="ba34b-151">Log</span><span class="sxs-lookup"><span data-stu-id="ba34b-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="ba34b-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="ba34b-152">ProcessSet</span></span>
  * [<span data-ttu-id="ba34b-153">Registry</span><span class="sxs-lookup"><span data-stu-id="ba34b-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="ba34b-154">Script</span><span class="sxs-lookup"><span data-stu-id="ba34b-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="ba34b-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="ba34b-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="ba34b-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="ba34b-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="ba34b-157">WaitForAll (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="ba34b-158">WaitForAny (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="ba34b-159">WaitForSome (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="ba34b-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="ba34b-160">Ressources partiellement fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="ba34b-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="ba34b-161">Groupe</span><span class="sxs-lookup"><span data-stu-id="ba34b-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="ba34b-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="ba34b-162">GroupSet</span></span>

  <span data-ttu-id="ba34b-163">**Problème :** les ressources ci-dessus échouent si une instance spécifique est appelée deux fois (exécution de la même configuration deux fois)</span><span class="sxs-lookup"><span data-stu-id="ba34b-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  * [<span data-ttu-id="ba34b-164">Service</span><span class="sxs-lookup"><span data-stu-id="ba34b-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="ba34b-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="ba34b-165">ServiceSet</span></span>

  <span data-ttu-id="ba34b-166">**Problème :** fonctionne uniquement pour le démarrage/l’arrêt du service (état).</span><span class="sxs-lookup"><span data-stu-id="ba34b-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="ba34b-167">Échoue si vous essayez de modifier d’autres attributs de service, comme StartupType, les informations d’identification, la description, etc.</span><span class="sxs-lookup"><span data-stu-id="ba34b-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="ba34b-168">L’erreur levée est semblable à :</span><span class="sxs-lookup"><span data-stu-id="ba34b-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="ba34b-169">*Impossible de trouver le type [management.managementobject] : vérifiez que l’assembly contenant ce type est chargé.*</span><span class="sxs-lookup"><span data-stu-id="ba34b-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

* <span data-ttu-id="ba34b-170">Ressources non fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="ba34b-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="ba34b-171">User</span><span class="sxs-lookup"><span data-stu-id="ba34b-171">User</span></span>](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="ba34b-172">Fonctionnalités DSC non disponibles sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="ba34b-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="ba34b-173">Les fonctionnalités DSC suivantes ne sont pas disponibles sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="ba34b-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="ba34b-174">Déchiffrement de documents MOF avec mots de passe cryptés</span><span class="sxs-lookup"><span data-stu-id="ba34b-174">Decrypting MOF document with encrypted password(s)</span></span>
* <span data-ttu-id="ba34b-175">Serveur collecteur : vous ne pouvez pas configurer un serveur collecteur sur Nano Server pour le moment</span><span class="sxs-lookup"><span data-stu-id="ba34b-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="ba34b-176">Tout ce qui n’est pas dans la liste des fonctionnalités marche</span><span class="sxs-lookup"><span data-stu-id="ba34b-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="ba34b-177">Utilisation de ressources DSC personnalisées sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="ba34b-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="ba34b-178">En raison des ensembles limités d’API Windows et de bibliothèques CLR disponibles sur Nano Server, les ressources DSC qui fonctionnent sur la version CLR complète de Windows ne fonctionnent pas nécessairement sur Nano Server.</span><span class="sxs-lookup"><span data-stu-id="ba34b-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="ba34b-179">Effectuez les tests de bout en bout avant de déployer des ressources personnalisées DSC dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="ba34b-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba34b-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba34b-180">See Also</span></span>
- [<span data-ttu-id="ba34b-181">Prise en main de Nano Server</span><span class="sxs-lookup"><span data-stu-id="ba34b-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)