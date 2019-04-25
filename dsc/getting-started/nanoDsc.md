---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079725"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="37eb5-103">Utilisation de DSC sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="37eb5-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="37eb5-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="37eb5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="37eb5-105">**DSC sur Nano Server** est un package facultatif dans le dossier `NanoServer\Packages` du support Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="37eb5-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="37eb5-106">Le package peut être installé lorsque vous créez un disque dur virtuel pour Nano Server en spécifiant **Microsoft-NanoServer-DSC-Package** comme valeur du paramètre **Packages** de la fonction **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="37eb5-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="37eb5-107">Par exemple, si vous créez un disque dur virtuel pour une machine virtuelle, la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="37eb5-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="37eb5-108">Pour plus d’informations sur l’installation et l’utilisation de Nano Server, ainsi que sur le mode de gestion de Nano Server avec la communication à distance PowerShell, voir [Prise en main de Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="37eb5-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="37eb5-109">Fonctionnalités DSC disponibles sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="37eb5-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="37eb5-110">Comme Nano Server ne prend en charge qu’un ensemble limité d’API par rapport à une version complète de Windows Server, DSC sur Nano Server n’a pas exactement les mêmes fonctionnalités que DSC exécuté sur les références complètes pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="37eb5-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="37eb5-111">En effet, DSC sur Nano Server est en cours de développement et ne dispose pas encore de toutes les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="37eb5-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="37eb5-112">Les fonctionnalités DSC suivantes sont actuellement disponibles sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="37eb5-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="37eb5-113">Modes par envoi et par extraction</span><span class="sxs-lookup"><span data-stu-id="37eb5-113">Both push and pull modes</span></span>

- <span data-ttu-id="37eb5-114">Toutes les applets de commande DSC qui existent sur une version complète de Windows Server, y compris les suivantes :</span><span class="sxs-lookup"><span data-stu-id="37eb5-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="37eb5-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="37eb5-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="37eb5-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="37eb5-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="37eb5-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="37eb5-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="37eb5-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="37eb5-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="37eb5-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="37eb5-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="37eb5-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="37eb5-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="37eb5-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="37eb5-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="37eb5-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="37eb5-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="37eb5-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="37eb5-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="37eb5-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="37eb5-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="37eb5-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="37eb5-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="37eb5-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="37eb5-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="37eb5-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="37eb5-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="37eb5-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="37eb5-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="37eb5-132">Compilation de configurations (voir [Configurations DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="37eb5-133">**Problème :** Le chiffrement de mot de passe (voir [Sécurisation du fichier MOF](../pull-server/secureMOF.md)) pendant la compilation de la configuration ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="37eb5-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="37eb5-134">Compilation de métaconfigurations (voir [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="37eb5-135">Exécution d’une ressource sous un contexte utilisateur (voir [Exécution de DSC avec les informations d’identification de l’utilisateur (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="37eb5-136">Ressources basées sur une classe (voir [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="37eb5-137">Débogage des ressources DSC (voir [Débogage des ressources DSC](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="37eb5-138">**Problème :** Ne fonctionne pas si une ressource utilise PsDscRunAsCredential (voir [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="37eb5-139">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="37eb5-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="37eb5-140">Contrôle de version de ressources</span><span class="sxs-lookup"><span data-stu-id="37eb5-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="37eb5-141">Client collecteur (configurations et ressources) (voir [Configuration d’un client collecteur à l’aide du nom de configuration](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="37eb5-142">Configurations partielles (envoi et extraction)</span><span class="sxs-lookup"><span data-stu-id="37eb5-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="37eb5-143">Rapports au serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="37eb5-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="37eb5-144">Chiffrement de document MOF</span><span class="sxs-lookup"><span data-stu-id="37eb5-144">MOF encryption</span></span>

- <span data-ttu-id="37eb5-145">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="37eb5-145">Event logging</span></span>

- <span data-ttu-id="37eb5-146">Création de rapports DSC Azure Automation</span><span class="sxs-lookup"><span data-stu-id="37eb5-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="37eb5-147">Ressources entièrement fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="37eb5-147">Resources that are fully functional</span></span>

- <span data-ttu-id="37eb5-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="37eb5-148">**Archive**</span></span>
- <span data-ttu-id="37eb5-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="37eb5-149">**Environment**</span></span>
- <span data-ttu-id="37eb5-150">**File**</span><span class="sxs-lookup"><span data-stu-id="37eb5-150">**File**</span></span>
- <span data-ttu-id="37eb5-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="37eb5-151">**Log**</span></span>
- <span data-ttu-id="37eb5-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="37eb5-152">**ProcessSet**</span></span>
- <span data-ttu-id="37eb5-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="37eb5-153">**Registry**</span></span>
- <span data-ttu-id="37eb5-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="37eb5-154">**Script**</span></span>
- <span data-ttu-id="37eb5-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="37eb5-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="37eb5-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="37eb5-156">**WindowsProcess**</span></span>
- <span data-ttu-id="37eb5-157">**WaitForAll** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="37eb5-158">**WaitForAny** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="37eb5-159">**WaitForSome** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="37eb5-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="37eb5-160">Ressources partiellement fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="37eb5-160">Resources that are partially functional</span></span>
- <span data-ttu-id="37eb5-161">**Groupe**</span><span class="sxs-lookup"><span data-stu-id="37eb5-161">**Group**</span></span>
- <span data-ttu-id="37eb5-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="37eb5-162">**GroupSet**</span></span>

  <span data-ttu-id="37eb5-163">**Problème :** Les ressources ci-dessus échouent si une instance spécifique est appelée deux fois (exécution de la même configuration deux fois)</span><span class="sxs-lookup"><span data-stu-id="37eb5-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="37eb5-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="37eb5-164">**Service**</span></span>
- <span data-ttu-id="37eb5-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="37eb5-165">**ServiceSet**</span></span>

  <span data-ttu-id="37eb5-166">**Problème :** Fonctionne uniquement pour le démarrage/l’arrêt du service (état).</span><span class="sxs-lookup"><span data-stu-id="37eb5-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="37eb5-167">Échoue si vous essayez de modifier d’autres attributs de service, comme StartupType, les informations d’identification, la description, etc.</span><span class="sxs-lookup"><span data-stu-id="37eb5-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="37eb5-168">L’erreur levée est semblable à :</span><span class="sxs-lookup"><span data-stu-id="37eb5-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="37eb5-169">*Impossible de trouver le type [management.managementobject] : vérifiez que l’assembly contenant ce type est chargé.*</span><span class="sxs-lookup"><span data-stu-id="37eb5-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="37eb5-170">Ressources non fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="37eb5-170">Resources that are not functional</span></span>
- <span data-ttu-id="37eb5-171">**User**</span><span class="sxs-lookup"><span data-stu-id="37eb5-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="37eb5-172">Fonctionnalités DSC non disponibles sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="37eb5-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="37eb5-173">Les fonctionnalités DSC suivantes ne sont pas disponibles sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="37eb5-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="37eb5-174">Déchiffrement de documents MOF avec mots de passe cryptés</span><span class="sxs-lookup"><span data-stu-id="37eb5-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="37eb5-175">Serveur collecteur : vous ne pouvez pas configurer un serveur collecteur sur Nano Server pour le moment</span><span class="sxs-lookup"><span data-stu-id="37eb5-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="37eb5-176">Tout ce qui n’est pas dans la liste des fonctionnalités marche</span><span class="sxs-lookup"><span data-stu-id="37eb5-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="37eb5-177">Utilisation de ressources DSC personnalisées sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="37eb5-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="37eb5-178">En raison des ensembles limités d’API Windows et de bibliothèques CLR disponibles sur Nano Server, les ressources DSC qui fonctionnent sur la version CLR complète de Windows ne fonctionnent pas nécessairement sur Nano Server.</span><span class="sxs-lookup"><span data-stu-id="37eb5-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="37eb5-179">Effectuez les tests de bout en bout avant de déployer des ressources personnalisées DSC dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="37eb5-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="37eb5-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37eb5-180">See Also</span></span>

- [<span data-ttu-id="37eb5-181">Prise en main de Nano Server</span><span class="sxs-lookup"><span data-stu-id="37eb5-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
