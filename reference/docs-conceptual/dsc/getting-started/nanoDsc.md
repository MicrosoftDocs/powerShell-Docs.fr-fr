---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Utilisation de DSC sur Nano Server
description: DSC est un package facultatif qui peut être installé lorsque vous créez un disque dur virtuel pour Windows Nano Server.
ms.openlocfilehash: 18585323359abd85515d4db194dae4adbad7c3d8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647077"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="abd54-104">Utilisation de DSC sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="abd54-104">Using DSC on Nano Server</span></span>

> <span data-ttu-id="abd54-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="abd54-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="abd54-106">**DSC sur Nano Server** est un package facultatif dans le dossier `NanoServer\Packages` du support Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="abd54-106">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="abd54-107">Le package peut être installé lorsque vous créez un disque dur virtuel pour Nano Server en spécifiant **Microsoft-NanoServer-DSC-Package** comme valeur du paramètre **Packages** de la fonction **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="abd54-107">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="abd54-108">Par exemple, si vous créez un disque dur virtuel pour une machine virtuelle, la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="abd54-108">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="abd54-109">Pour plus d’informations sur l’installation et l’utilisation de Nano Server, ainsi que sur le mode de gestion de Nano Server avec la communication à distance PowerShell, voir [Prise en main de Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="abd54-109">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="abd54-110">Fonctionnalités DSC disponibles sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="abd54-110">DSC features available on Nano Server</span></span>

<span data-ttu-id="abd54-111">Comme Nano Server ne prend en charge qu’un ensemble limité d’API par rapport à une version complète de Windows Server, DSC sur Nano Server n’a pas exactement les mêmes fonctionnalités que DSC exécuté sur les références complètes pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="abd54-111">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="abd54-112">En effet, DSC sur Nano Server est en cours de développement et ne dispose pas encore de toutes les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="abd54-112">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="abd54-113">Les fonctionnalités DSC suivantes sont actuellement disponibles sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="abd54-113">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="abd54-114">Modes par envoi et par extraction</span><span class="sxs-lookup"><span data-stu-id="abd54-114">Both push and pull modes</span></span>

- <span data-ttu-id="abd54-115">Toutes les applets de commande DSC qui existent sur une version complète de Windows Server, y compris les suivantes :</span><span class="sxs-lookup"><span data-stu-id="abd54-115">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="abd54-116">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="abd54-116">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="abd54-117">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="abd54-117">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="abd54-118">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="abd54-118">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="abd54-119">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="abd54-119">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="abd54-120">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-120">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="abd54-121">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-121">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="abd54-122">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-122">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="abd54-123">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-123">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="abd54-124">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-124">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="abd54-125">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-125">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="abd54-126">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="abd54-126">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="abd54-127">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="abd54-127">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="abd54-128">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="abd54-128">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="abd54-129">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="abd54-129">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="abd54-130">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="abd54-130">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource)
- [<span data-ttu-id="abd54-131">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="abd54-131">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="abd54-132">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="abd54-132">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="abd54-133">Compilation de configurations (voir [Configurations DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-133">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="abd54-134">**Problème :** le chiffrement de mot de passe (voir [Sécurisation du fichier MOF](../pull-server/secureMOF.md)) pendant la compilation de la configuration ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="abd54-134">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="abd54-135">Compilation de métaconfigurations (voir [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-135">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="abd54-136">Exécution d’une ressource sous un contexte utilisateur (voir [Exécution de DSC avec les informations d’identification de l’utilisateur (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-136">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="abd54-137">Ressources basées sur une classe (voir [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](/previous-versions//dn948461(v=technet.10)))</span><span class="sxs-lookup"><span data-stu-id="abd54-137">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="abd54-138">Débogage des ressources DSC (voir [Débogage des ressources DSC](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-138">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="abd54-139">**Problème :** ne fonctionne pas si une ressource utilise PsDscRunAsCredential (voir [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-139">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="abd54-140">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="abd54-140">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="abd54-141">Contrôle de version de ressources</span><span class="sxs-lookup"><span data-stu-id="abd54-141">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="abd54-142">Client collecteur (configurations et ressources) (voir [Configuration d’un client collecteur à l’aide du nom de configuration](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-142">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="abd54-143">Configurations partielles (envoi et extraction)</span><span class="sxs-lookup"><span data-stu-id="abd54-143">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="abd54-144">Rapports au serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="abd54-144">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="abd54-145">Chiffrement de document MOF</span><span class="sxs-lookup"><span data-stu-id="abd54-145">MOF encryption</span></span>

- <span data-ttu-id="abd54-146">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="abd54-146">Event logging</span></span>

- <span data-ttu-id="abd54-147">Création de rapports DSC Azure Automation</span><span class="sxs-lookup"><span data-stu-id="abd54-147">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="abd54-148">Ressources entièrement fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="abd54-148">Resources that are fully functional</span></span>

  - <span data-ttu-id="abd54-149">**Archive**</span><span class="sxs-lookup"><span data-stu-id="abd54-149">**Archive**</span></span>
  - <span data-ttu-id="abd54-150">**Environment**</span><span class="sxs-lookup"><span data-stu-id="abd54-150">**Environment**</span></span>
  - <span data-ttu-id="abd54-151">**File**</span><span class="sxs-lookup"><span data-stu-id="abd54-151">**File**</span></span>
  - <span data-ttu-id="abd54-152">**Journal**</span><span class="sxs-lookup"><span data-stu-id="abd54-152">**Log**</span></span>
  - <span data-ttu-id="abd54-153">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="abd54-153">**ProcessSet**</span></span>
  - <span data-ttu-id="abd54-154">**Registre**</span><span class="sxs-lookup"><span data-stu-id="abd54-154">**Registry**</span></span>
  - <span data-ttu-id="abd54-155">**Script**</span><span class="sxs-lookup"><span data-stu-id="abd54-155">**Script**</span></span>
  - <span data-ttu-id="abd54-156">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="abd54-156">**WindowsPackageCab**</span></span>
  - <span data-ttu-id="abd54-157">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="abd54-157">**WindowsProcess**</span></span>
  - <span data-ttu-id="abd54-158">**WaitForAll** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-158">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
  - <span data-ttu-id="abd54-159">**WaitForAny** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-159">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
  - <span data-ttu-id="abd54-160">**WaitForSome** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="abd54-160">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="abd54-161">Ressources partiellement fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="abd54-161">Resources that are partially functional</span></span>

  - <span data-ttu-id="abd54-162">**Groupe**</span><span class="sxs-lookup"><span data-stu-id="abd54-162">**Group**</span></span>
  - <span data-ttu-id="abd54-163">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="abd54-163">**GroupSet**</span></span>

    <span data-ttu-id="abd54-164">**Problème :** les ressources ci-dessus échouent si une instance spécifique est appelée deux fois (exécution de la même configuration deux fois)</span><span class="sxs-lookup"><span data-stu-id="abd54-164">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  - <span data-ttu-id="abd54-165">**Service**</span><span class="sxs-lookup"><span data-stu-id="abd54-165">**Service**</span></span>
  - <span data-ttu-id="abd54-166">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="abd54-166">**ServiceSet**</span></span>

    <span data-ttu-id="abd54-167">**Problème :** fonctionne uniquement pour le démarrage/l’arrêt du service (état).</span><span class="sxs-lookup"><span data-stu-id="abd54-167">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="abd54-168">Échoue si vous essayez de modifier d’autres attributs de service, comme StartupType, les informations d’identification, la description, etc.</span><span class="sxs-lookup"><span data-stu-id="abd54-168">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="abd54-169">L’erreur levée est semblable à :</span><span class="sxs-lookup"><span data-stu-id="abd54-169">The error thrown is similar to:</span></span>

    ```
    Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.
    ```

- <span data-ttu-id="abd54-170">Ressources non fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="abd54-170">Resources that are not functional</span></span>

  - <span data-ttu-id="abd54-171">**Utilisateur**</span><span class="sxs-lookup"><span data-stu-id="abd54-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="abd54-172">Fonctionnalités DSC non disponibles sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="abd54-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="abd54-173">Les fonctionnalités DSC suivantes ne sont pas disponibles sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="abd54-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="abd54-174">Déchiffrement de documents MOF avec mots de passe cryptés</span><span class="sxs-lookup"><span data-stu-id="abd54-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="abd54-175">Serveur collecteur : vous ne pouvez pas configurer un serveur collecteur sur Nano Server pour le moment</span><span class="sxs-lookup"><span data-stu-id="abd54-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="abd54-176">Tout ce qui n’est pas dans la liste des fonctionnalités marche</span><span class="sxs-lookup"><span data-stu-id="abd54-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="abd54-177">Utilisation de ressources DSC personnalisées sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="abd54-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="abd54-178">En raison des ensembles limités d’API Windows et de bibliothèques CLR disponibles sur Nano Server, les ressources DSC qui fonctionnent sur la version CLR complète de Windows ne fonctionnent pas nécessairement sur Nano Server.</span><span class="sxs-lookup"><span data-stu-id="abd54-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="abd54-179">Effectuez les tests de bout en bout avant de déployer des ressources personnalisées DSC dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="abd54-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="abd54-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abd54-180">See Also</span></span>

- [<span data-ttu-id="abd54-181">Prise en main de Nano Server</span><span class="sxs-lookup"><span data-stu-id="abd54-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
