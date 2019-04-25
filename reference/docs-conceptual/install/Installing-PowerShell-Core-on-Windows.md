---
title: Installation de PowerShell Core sous Windows
description: Informations sur l’installation de PowerShell Core sur Windows
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058027"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="22bd5-103">Installation de PowerShell Core sous Windows</span><span class="sxs-lookup"><span data-stu-id="22bd5-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="22bd5-104">Il existe plusieurs façons d’installer PowerShell Core dans Windows.</span><span class="sxs-lookup"><span data-stu-id="22bd5-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22bd5-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="22bd5-105">Prerequisites</span></span>

<span data-ttu-id="22bd5-106">Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="22bd5-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="22bd5-107">Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.</span><span class="sxs-lookup"><span data-stu-id="22bd5-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="22bd5-108">Il est disponible par téléchargement direct ou sur Windows Update.</span><span class="sxs-lookup"><span data-stu-id="22bd5-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="22bd5-109">Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).</span><span class="sxs-lookup"><span data-stu-id="22bd5-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="22bd5-110">Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="22bd5-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="22bd5-111"><a id="msi" />Installation du package MSI</span><span class="sxs-lookup"><span data-stu-id="22bd5-111"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="22bd5-112">Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2 et les versions ultérieures), téléchargez le package MSI sur notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="22bd5-112">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="22bd5-113">Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="22bd5-113">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="22bd5-114">Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="22bd5-114">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="22bd5-115">Le fichier MSI ressemble à ceci : `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="22bd5-115">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="22bd5-116">Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="22bd5-116">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="22bd5-117">Le programme d’installation crée un raccourci dans le menu Démarrer de Windows.</span><span class="sxs-lookup"><span data-stu-id="22bd5-117">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="22bd5-118">Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="22bd5-118">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="22bd5-119">Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="22bd5-119">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="22bd5-120">Installation administrative à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="22bd5-120">Administrative install from the command line</span></span>

<span data-ttu-id="22bd5-121">Les packages MSI peuvent être installés à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="22bd5-121">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="22bd5-122">Cela permet aux administrateurs de déployer des packages sans l’intervention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="22bd5-122">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="22bd5-123">Le package MSI pour PowerShell inclut les propriétés suivantes pour contrôler les options d’installation :</span><span class="sxs-lookup"><span data-stu-id="22bd5-123">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="22bd5-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : cette propriété contrôle l’option permettant d’ajouter l’élément **Ouvrir PowerShell** au menu contextuel dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="22bd5-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="22bd5-125">**ENABLE_PSREMOTING** : cette propriété contrôle l’option permettant d’activer la communication à distance PowerShell pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="22bd5-125">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="22bd5-126">**REGISTER_MANIFEST** : cette propriété contrôle l’option permettant d’enregistrer le manifeste de journalisation des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="22bd5-126">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="22bd5-127">Les exemples suivants montrent comment installer PowerShell Core sans assistance avec toutes les options d’installation activées.</span><span class="sxs-lookup"><span data-stu-id="22bd5-127">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="22bd5-128">Pour obtenir une liste complète des options de ligne de commande pour Msiexec.exe, consultez [Options de ligne de commande](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="22bd5-128">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="22bd5-129"><a id="zip" />Installation du package ZIP</span><span class="sxs-lookup"><span data-stu-id="22bd5-129"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="22bd5-130">Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="22bd5-130">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="22bd5-131">Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.</span><span class="sxs-lookup"><span data-stu-id="22bd5-131">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="22bd5-132">Pour que la communication à distance via WSMan fonctionne correctement, vérifiez que vous respectez bien les [conditions préalables](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="22bd5-132">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="22bd5-133">Déploiement sur Windows IoT</span><span class="sxs-lookup"><span data-stu-id="22bd5-133">Deploying on Windows IoT</span></span>

<span data-ttu-id="22bd5-134">Windows IoT est déjà équipé de Windows PowerShell que nous utiliserons pour déployer PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="22bd5-134">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="22bd5-135">Créez `PSSession` sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="22bd5-135">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="22bd5-136">Copiez le fichier ZIP sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="22bd5-136">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="22bd5-137">Connectez-vous à l’appareil et développez l’archive</span><span class="sxs-lookup"><span data-stu-id="22bd5-137">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="22bd5-138">Configurez la communication à distance avec PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="22bd5-138">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="22bd5-139">Connectez-vous au point de terminaison PowerShell Core 6 sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="22bd5-139">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="22bd5-140">Déploiement sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="22bd5-140">Deploying on Nano Server</span></span>

<span data-ttu-id="22bd5-141">Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="22bd5-141">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="22bd5-142">Nano Server est un système d’exploitation « administré à distance ».</span><span class="sxs-lookup"><span data-stu-id="22bd5-142">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="22bd5-143">Les binaires Core peuvent être déployés à l’aide de deux méthodes différentes.</span><span class="sxs-lookup"><span data-stu-id="22bd5-143">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="22bd5-144">Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.</span><span class="sxs-lookup"><span data-stu-id="22bd5-144">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="22bd5-145">En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="22bd5-145">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="22bd5-146">Dans les deux cas, vous avez besoin du package de la version ZIP Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="22bd5-146">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="22bd5-147">Déploiement hors connexion de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="22bd5-147">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="22bd5-148">Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.</span><span class="sxs-lookup"><span data-stu-id="22bd5-148">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="22bd5-149">Démontez l’image et démarrez-la.</span><span class="sxs-lookup"><span data-stu-id="22bd5-149">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="22bd5-150">Connectez-vous à l’instance de boîte de réception de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22bd5-150">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="22bd5-151">Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="22bd5-151">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="22bd5-152">Déploiement en ligne de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="22bd5-152">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="22bd5-153">La procédure suivante vous guide tout au long du déploiement de PowerShell Core sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="22bd5-153">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="22bd5-154">Connectez-vous à l’instance de boîte de réception de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="22bd5-154">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="22bd5-155">Copiez le fichier sur l’instance de Nano Server</span><span class="sxs-lookup"><span data-stu-id="22bd5-155">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="22bd5-156">Entrez dans la session</span><span class="sxs-lookup"><span data-stu-id="22bd5-156">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="22bd5-157">Extrayez le fichier ZIP</span><span class="sxs-lookup"><span data-stu-id="22bd5-157">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="22bd5-158">Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="22bd5-158">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="22bd5-159">Comment créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="22bd5-159">How to create a remoting endpoint</span></span>

<span data-ttu-id="22bd5-160">PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH.</span><span class="sxs-lookup"><span data-stu-id="22bd5-160">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="22bd5-161">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="22bd5-161">For more information, see:</span></span>

- <span data-ttu-id="22bd5-162">[Accès distant SSH dans PowerShell Core] [ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="22bd5-162">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="22bd5-163">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="22bd5-163">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
<span data-ttu-id="22bd5-164">[versions] : https://github.com/PowerShell/PowerShell/releases [ssh-remoting] : ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting] : ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor] : https://ci.appveyor.com/project/PowerShell/powershell</span><span class="sxs-lookup"><span data-stu-id="22bd5-164">[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span></span>
