---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurer une machine virtuelle au démarrage initial à l’aide de DSC
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954606"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="cf7e5-103">Configurer une machine virtuelle au démarrage initial à l’aide de DSC</span><span class="sxs-lookup"><span data-stu-id="cf7e5-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf7e5-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cf7e5-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="cf7e5-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf7e5-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="cf7e5-106">La clé de Registre **DSCAutomationHostEnabled** décrite dans cette rubrique n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="cf7e5-107">Pour plus d’informations sur la configuration de nouvelles machines virtuelles au démarrage initial dans PowerShell 4.0, consultez [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="cf7e5-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="cf7e5-108">Pour exécuter ces exemples, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="cf7e5-109">Un disque dur virtuel démarrable avec lequel travailler.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-109">A bootable VHD to work with.</span></span> <span data-ttu-id="cf7e5-110">Vous pouvez télécharger une image ISO avec une copie d’évaluation de Windows Server 2016 auprès du [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="cf7e5-111">Vous trouverez des instructions sur la création d’un disque dur virtuel à partir d’une image ISO dans [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="cf7e5-112">Un ordinateur hôte où Hyper-V est activé.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="cf7e5-113">Pour plus d’informations, consultez [Vue d’ensemble d’Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="cf7e5-114">À l’aide de DSC, vous pouvez automatiser l’installation et la configuration de logiciels d’un ordinateur au démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="cf7e5-115">Pour cela, vous injectez un document MOF de configuration ou une métaconfiguration dans un média démarrable (comme un disque dur virtuel) afin qu’ils soient exécutés lors du processus de démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="cf7e5-116">Ce comportement est spécifié par la [clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) sous `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="cf7e5-117">Par défaut, la valeur de cette clé est 2, ce qui permet à DSC de s’exécuter au moment du démarrage.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="cf7e5-118">Si vous ne voulez pas que DSC s’exécute au démarrage, définissez la valeur de la [clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) sur 0.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="cf7e5-119">Injecter un document MOF de configuration dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="cf7e5-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="cf7e5-120">Injecter une métaconfiguration DSC dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="cf7e5-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="cf7e5-121">Désactiver DSC au démarrage</span><span class="sxs-lookup"><span data-stu-id="cf7e5-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="cf7e5-122">Vous pouvez injecter à la fois `Pending.mof` et `MetaConfig.mof` dans un ordinateur en même temps.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="cf7e5-123">Si les deux fichiers sont présents, les paramètres spécifiés dans `MetaConfig.mof` sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="cf7e5-124">Injecter un document MOF de configuration dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="cf7e5-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="cf7e5-125">Pour promulguer une configuration au démarrage initial, vous pouvez injecter un document MOF de configuration compilé dans le disque dur virtuel sous la forme de son fichier `Pending.mof`.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="cf7e5-126">Si la clé de Registre **DSCAutomationHostEnabled** est définie sur 2 (la valeur par défaut), DSC applique la configuration définie par `Pending.mof` quand l’ordinateur démarre pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="cf7e5-127">Pour cet exemple, nous utilisons la configuration suivante, qui installe IIS sur le nouvel ordinateur :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="cf7e5-128">Pour injecter le document MOF de configuration sur le disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="cf7e5-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="cf7e5-129">Montez le disque dur virtuel dans lequel vous voulez injecter la configuration en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="cf7e5-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="cf7e5-131">Sur un ordinateur exécutant PowerShell 5.0 ou ultérieur, enregistrez la configuration ci-dessus (**SampleIISInstall**) dans un fichier de script PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="cf7e5-132">Dans une console PowerShell, accédez au dossier où vous avez enregistré le fichier .ps1.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="cf7e5-133">Exécutez les commandes PowerShell suivantes pour compiler le document MOF. Pour plus d’informations sur la compilation des configurations DSC, consultez [Configurations DSC](../configurations/configurations.md) :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="cf7e5-134">Cette opération crée un fichier `localhost.mof` dans un nouveau dossier nommé `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="cf7e5-135">Renommez le fichier en `Pending.mof` et déplacez-le à l’emplacement approprié sur le disque dur virtuel en utilisant l’applet de commande [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="cf7e5-136">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="cf7e5-137">Démontez le disque dur virtuel en appelant l’applet de commande [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="cf7e5-138">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="cf7e5-139">Créez une machine virtuelle en utilisant le disque dur virtuel où vous avez installé le document MOF DSC.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="cf7e5-140">Après le démarrage initial et l’installation du système d’exploitation, IIS est installé.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="cf7e5-141">Vous pouvez le vérifier en appelant l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="cf7e5-142">Injecter une métaconfiguration DSC dans un disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="cf7e5-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="cf7e5-143">Vous pouvez également configurer un ordinateur pour extraire une configuration au démarrage initial en injectant une métaconfiguration (consultez [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md)) dans le disque dur virtuel sous la forme de son fichier `MetaConfig.mof`.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="cf7e5-144">Si la clé de Registre **DSCAutomationHostEnabled** est définie sur 2 (la valeur par défaut), DSC applique la métaconfiguration définie par `MetaConfig.mof` au gestionnaire de configuration local quand l’ordinateur démarre pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="cf7e5-145">Si la métaconfiguration spécifie que le Gestionnaire de configuration local doit extraire les configurations à partir d’un serveur Pull, l’ordinateur tente d’extraire une configuration auprès de ce serveur Pull au démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="cf7e5-146">Pour plus d’informations sur la configuration d’un serveur collecteur DSC, consultez [Configuration d’un serveur collecteur web DSC](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="cf7e5-147">Pour cet exemple, nous utilisons la configuration décrite dans la section précédente (**SampleIISInstall**) et la métaconfiguration suivante :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="cf7e5-148">Pour injecter le document MOF de métaconfiguration sur le disque dur virtuel</span><span class="sxs-lookup"><span data-stu-id="cf7e5-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="cf7e5-149">Montez le disque dur virtuel dans lequel vous voulez injecter la métaconfiguration en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="cf7e5-150">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="cf7e5-151">[Configurez un serveur Pull web DSC](../pull-server/pullServer.md), puis enregistrez la configuration **SampleIISInstall** dans le dossier approprié.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="cf7e5-152">Sur un ordinateur exécutant PowerShell 5.0 ou ultérieur, enregistrez la métaconfiguration ci-dessus (**PullClientBootstrap**) dans un fichier de script PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="cf7e5-153">Dans une console PowerShell, accédez au dossier où vous avez enregistré le fichier .ps1.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="cf7e5-154">Exécutez les commandes PowerShell suivantes pour compiler le document MOF de métaconfiguration (pour plus d’informations sur la compilation des configurations DSC, consultez [Configurations DSC](../configurations/configurations.md) :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="cf7e5-155">Cette opération crée un fichier `localhost.meta.mof` dans un nouveau dossier nommé `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="cf7e5-156">Renommez le fichier en `MetaConfig.mof` et déplacez-le à l’emplacement approprié sur le disque dur virtuel en utilisant l’applet de commande [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="cf7e5-157">Démontez le disque dur virtuel en appelant l’applet de commande [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="cf7e5-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="cf7e5-159">Créez une machine virtuelle en utilisant le disque dur virtuel où vous avez installé le document MOF DSC.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="cf7e5-160">Après le démarrage initial et l’installation du système d’exploitation, DSC extrait la configuration auprès du serveur Pull, et IIS est installé.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="cf7e5-161">Vous pouvez le vérifier en appelant l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="cf7e5-162">Désactiver DSC au démarrage</span><span class="sxs-lookup"><span data-stu-id="cf7e5-162">Disable DSC at boot time</span></span>

<span data-ttu-id="cf7e5-163">Par défaut, la valeur de la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` est définie sur 2, ce qui permet à une configuration DSC de exécuter si l’ordinateur est en état d’attente ou actif.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="cf7e5-164">Si vous ne voulez pas qu’une configuration s’exécute au démarrage initial, vous devez définir la valeur de cette clé sur 0 :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="cf7e5-165">Montez le disque dur virtuel en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="cf7e5-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="cf7e5-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="cf7e5-167">Chargez la sous-clé `HKLM\Software` du Registre à partir du disque dur virtuel en appelant `reg load`.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="cf7e5-168">Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` à l’aide du fournisseur de Registre de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="cf7e5-169">Remplacez la valeur de `DSCAutomationHostEnabled` par 0.</span><span class="sxs-lookup"><span data-stu-id="cf7e5-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="cf7e5-170">Déchargez le Registre en exécutant les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cf7e5-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="cf7e5-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf7e5-171">See Also</span></span>

[<span data-ttu-id="cf7e5-172">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="cf7e5-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="cf7e5-173">Clé de Registre DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="cf7e5-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="cf7e5-174">Configuration du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="cf7e5-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="cf7e5-175">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="cf7e5-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
