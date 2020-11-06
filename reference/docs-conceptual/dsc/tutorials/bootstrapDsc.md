---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Configurer une machine virtuelle au démarrage initial à l’aide de DSC
description: Cet article explique comment configurer une machine virtuelle au démarrage initial à l’aide de DSC
ms.openlocfilehash: 9fa8c4a21486aaef87e1c0a3097e5983a378d98d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656198"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="e3b7d-104">Configurer une machine virtuelle au démarrage initial à l’aide de DSC</span><span class="sxs-lookup"><span data-stu-id="e3b7d-104">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3b7d-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e3b7d-105">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="e3b7d-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e3b7d-106">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="e3b7d-107">La clé de Registre **DSCAutomationHostEnabled** décrite dans cette rubrique n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-107">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span> <span data-ttu-id="e3b7d-108">Pour plus d’informations sur la configuration de nouvelles machines virtuelles au démarrage initial dans PowerShell 4.0, consultez [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="e3b7d-108">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="e3b7d-109">Pour exécuter ces exemples, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-109">To run these examples, you will need:</span></span>

- <span data-ttu-id="e3b7d-110">Un disque dur virtuel démarrable avec lequel travailler.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-110">A bootable VHD to work with.</span></span> <span data-ttu-id="e3b7d-111">Vous pouvez télécharger une image ISO avec une copie d’évaluation de Windows Server 2016 auprès du [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-111">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="e3b7d-112">Vous trouverez des instructions sur la création d’un disque dur virtuel à partir d’une image ISO dans [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-112">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="e3b7d-113">Un ordinateur hôte où Hyper-V est activé.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-113">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="e3b7d-114">Pour plus d’informations, consultez [Vue d’ensemble d’Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-114">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="e3b7d-115">À l’aide de DSC, vous pouvez automatiser l’installation et la configuration de logiciels d’un ordinateur au démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-115">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span> <span data-ttu-id="e3b7d-116">Pour cela, vous injectez un document MOF de configuration ou une métaconfiguration dans un média démarrable (comme un disque dur virtuel) afin qu’ils soient exécutés lors du processus de démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-116">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span> <span data-ttu-id="e3b7d-117">Ce comportement est spécifié par la [clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) sous `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-117">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="e3b7d-118">Par défaut, la valeur de cette clé est 2, ce qui permet à DSC de s’exécuter au moment du démarrage.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-118">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="e3b7d-119">Si vous ne voulez pas que DSC s’exécute au démarrage, définissez la valeur de la [clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) sur 0.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-119">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="e3b7d-120">Injecter un document MOF de configuration dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="e3b7d-120">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="e3b7d-121">Injecter une métaconfiguration DSC dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="e3b7d-121">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="e3b7d-122">Désactiver DSC au démarrage</span><span class="sxs-lookup"><span data-stu-id="e3b7d-122">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="e3b7d-123">Vous pouvez injecter à la fois `Pending.mof` et `MetaConfig.mof` dans un ordinateur en même temps.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-123">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="e3b7d-124">Si les deux fichiers sont présents, les paramètres spécifiés dans `MetaConfig.mof` sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-124">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="e3b7d-125">Injecter un document MOF de configuration dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="e3b7d-125">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="e3b7d-126">Pour promulguer une configuration au démarrage initial, vous pouvez injecter un document MOF de configuration compilé dans le disque dur virtuel sous la forme de son fichier `Pending.mof`.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-126">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span> <span data-ttu-id="e3b7d-127">Si la clé de Registre **DSCAutomationHostEnabled** est définie sur 2 (la valeur par défaut), DSC applique la configuration définie par `Pending.mof` quand l’ordinateur démarre pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-127">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="e3b7d-128">Pour cet exemple, nous utilisons la configuration suivante, qui installe IIS sur le nouvel ordinateur :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-128">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="e3b7d-129">Pour injecter le document MOF de configuration sur le disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="e3b7d-129">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="e3b7d-130">Montez le disque dur virtuel dans lequel vous voulez injecter la configuration en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-130">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="e3b7d-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-131">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="e3b7d-132">Sur un ordinateur exécutant PowerShell 5.0 ou ultérieur, enregistrez la configuration ci-dessus ( **SampleIISInstall** ) dans un fichier de script PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-132">On a computer running PowerShell 5.0 or later, save the above configuration ( **SampleIISInstall** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="e3b7d-133">Dans une console PowerShell, accédez au dossier où vous avez enregistré le fichier .ps1.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-133">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="e3b7d-134">Exécutez les commandes PowerShell suivantes pour compiler le document MOF. Pour plus d’informations sur la compilation des configurations DSC, consultez [Configurations DSC](../configurations/configurations.md) :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-134">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. <span data-ttu-id="e3b7d-135">Cette opération crée un fichier `localhost.mof` dans un nouveau dossier nommé `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-135">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span> <span data-ttu-id="e3b7d-136">Renommez le fichier en `Pending.mof` et déplacez-le à l’emplacement approprié sur le disque dur virtuel en utilisant l’applet de commande [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-136">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="e3b7d-137">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-137">For example:</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. <span data-ttu-id="e3b7d-138">Démontez le disque dur virtuel en appelant l’applet de commande [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-138">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="e3b7d-139">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-139">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="e3b7d-140">Créez une machine virtuelle en utilisant le disque dur virtuel où vous avez installé le document MOF DSC.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-140">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="e3b7d-141">Après le démarrage initial et l’installation du système d’exploitation, IIS est installé.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-141">After initial boot-up and operating system installation, IIS will be installed.</span></span> <span data-ttu-id="e3b7d-142">Vous pouvez le vérifier en appelant l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-142">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="e3b7d-143">Injecter une métaconfiguration DSC dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="e3b7d-143">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="e3b7d-144">Vous pouvez également configurer un ordinateur pour extraire une configuration au démarrage initial en injectant une métaconfiguration (consultez [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md)) dans le disque dur virtuel sous la forme de son fichier `MetaConfig.mof`.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-144">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span> <span data-ttu-id="e3b7d-145">Si la clé de Registre **DSCAutomationHostEnabled** est définie sur 2 (la valeur par défaut), DSC applique la métaconfiguration définie par `MetaConfig.mof` au gestionnaire de configuration local quand l’ordinateur démarre pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-145">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span> <span data-ttu-id="e3b7d-146">Si la métaconfiguration spécifie que le Gestionnaire de configuration local doit extraire les configurations à partir d’un serveur Pull, l’ordinateur tente d’extraire une configuration auprès de ce serveur Pull au démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-146">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span> <span data-ttu-id="e3b7d-147">Pour plus d’informations sur la configuration d’un serveur collecteur DSC, consultez [Configuration d’un serveur collecteur web DSC](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-147">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="e3b7d-148">Pour cet exemple, nous utilisons la configuration décrite dans la section précédente ( **SampleIISInstall** ) et la métaconfiguration suivante :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-148">For this example, we will use both the configuration described in the previous section ( **SampleIISInstall** ), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="e3b7d-149">Pour injecter le document MOF de métaconfiguration sur le disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="e3b7d-149">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="e3b7d-150">Montez le disque dur virtuel dans lequel vous voulez injecter la métaconfiguration en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-150">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="e3b7d-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-151">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="e3b7d-152">[Configurez un serveur Pull web DSC](../pull-server/pullServer.md), puis enregistrez la configuration **SampleIISInstall** dans le dossier approprié.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-152">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

1. <span data-ttu-id="e3b7d-153">Sur un ordinateur exécutant PowerShell 5.0 ou ultérieur, enregistrez la métaconfiguration ci-dessus ( **PullClientBootstrap** ) dans un fichier de script PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-153">On a computer running PowerShell 5.0 or later, save the above metaconfiguration ( **PullClientBootstrap** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="e3b7d-154">Dans une console PowerShell, accédez au dossier où vous avez enregistré le fichier .ps1.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-154">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="e3b7d-155">Exécutez les commandes PowerShell suivantes pour compiler le document MOF de métaconfiguration (pour plus d’informations sur la compilation des configurations DSC, consultez [Configurations DSC](../configurations/configurations.md) :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-155">Run the following PowerShell commands to compile the metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. <span data-ttu-id="e3b7d-156">Cette opération crée un fichier `localhost.meta.mof` dans un nouveau dossier nommé `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-156">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span> <span data-ttu-id="e3b7d-157">Renommez le fichier en `MetaConfig.mof` et déplacez-le à l’emplacement approprié sur le disque dur virtuel en utilisant l’applet de commande [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-157">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. <span data-ttu-id="e3b7d-158">Démontez le disque dur virtuel en appelant l’applet de commande [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-158">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="e3b7d-159">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-159">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="e3b7d-160">Créez une machine virtuelle en utilisant le disque dur virtuel où vous avez installé le document MOF DSC.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-160">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="e3b7d-161">Après le démarrage initial et l’installation du système d’exploitation, DSC extrait la configuration auprès du serveur Pull, et IIS est installé.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-161">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span> <span data-ttu-id="e3b7d-162">Vous pouvez le vérifier en appelant l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-162">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="e3b7d-163">Désactiver DSC au démarrage</span><span class="sxs-lookup"><span data-stu-id="e3b7d-163">Disable DSC at boot time</span></span>

<span data-ttu-id="e3b7d-164">Par défaut, la valeur de la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span><span class="sxs-lookup"><span data-stu-id="e3b7d-164">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span></span>
<span data-ttu-id="e3b7d-165">est définie sur 2, ce qui permet à une configuration DSC de s’exécuter si l’ordinateur est en état d’attente ou actif.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-165">key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="e3b7d-166">Si vous ne voulez pas qu’une configuration s’exécute au démarrage initial, vous devez définir la valeur de cette clé sur 0 :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-166">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="e3b7d-167">Montez le disque dur virtuel en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="e3b7d-167">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="e3b7d-168">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-168">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="e3b7d-169">Chargez la sous-clé `HKLM\Software` du Registre à partir du disque dur virtuel en appelant `reg load`.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-169">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

1. <span data-ttu-id="e3b7d-170">Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` à l’aide du fournisseur de Registre de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-170">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

1. <span data-ttu-id="e3b7d-171">Remplacez la valeur de `DSCAutomationHostEnabled` par 0.</span><span class="sxs-lookup"><span data-stu-id="e3b7d-171">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="e3b7d-172">Déchargez le Registre en exécutant les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e3b7d-172">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="e3b7d-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3b7d-173">See Also</span></span>

[<span data-ttu-id="e3b7d-174">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="e3b7d-174">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="e3b7d-175">Clé de Registre DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="e3b7d-175">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="e3b7d-176">Configuration du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="e3b7d-176">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="e3b7d-177">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="e3b7d-177">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
