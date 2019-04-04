---
title: Installation de PowerShell Core sous Windows
description: Informations sur l’installation de PowerShell Core sur Windows
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748956"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="07898-103">Installation de PowerShell Core sous Windows</span><span class="sxs-lookup"><span data-stu-id="07898-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="07898-104">MSI</span><span class="sxs-lookup"><span data-stu-id="07898-104">MSI</span></span>

<span data-ttu-id="07898-105">Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2, et versions ultérieures), téléchargez le package MSI à partir de notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="07898-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="07898-106">Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="07898-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="07898-107">Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="07898-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="07898-108">Le fichier MSI ressemble à ceci : `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="07898-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="07898-109">Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="07898-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="07898-110">Un raccourci est placé dans le menu Démarrer lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="07898-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="07898-111">Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="07898-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="07898-112">Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="07898-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="07898-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="07898-113">Prerequisites</span></span>

<span data-ttu-id="07898-114">Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="07898-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="07898-115">Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.</span><span class="sxs-lookup"><span data-stu-id="07898-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="07898-116">Il est disponible par téléchargement direct ou sur Windows Update.</span><span class="sxs-lookup"><span data-stu-id="07898-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="07898-117">Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).</span><span class="sxs-lookup"><span data-stu-id="07898-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="07898-118">Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="07898-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="07898-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="07898-119">ZIP</span></span>

<span data-ttu-id="07898-120">Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="07898-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="07898-121">Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.</span><span class="sxs-lookup"><span data-stu-id="07898-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="07898-122">Ainsi, pour que la communication à distance via WSMan puisse fonctionner correctement sur les versions de Windows antérieures à Windows 10, vous devez vérifier que ces [conditions préalables](#prerequisites) sont remplies.</span><span class="sxs-lookup"><span data-stu-id="07898-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="07898-123">Déploiement sur Windows IoT</span><span class="sxs-lookup"><span data-stu-id="07898-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="07898-124">Windows IoT est déjà équipé de Windows PowerShell que nous utiliserons pour déployer PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="07898-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="07898-125">Créez `PSSession` sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="07898-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="07898-126">Copiez le fichier ZIP sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="07898-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="07898-127">Connectez-vous à l’appareil et développez l’archive</span><span class="sxs-lookup"><span data-stu-id="07898-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="07898-128">Configurez la communication à distance avec PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="07898-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="07898-129">Connectez-vous au point de terminaison PowerShell Core 6 sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="07898-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="07898-130">Déploiement sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="07898-130">Deploying on Nano Server</span></span>

<span data-ttu-id="07898-131">Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="07898-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="07898-132">Nano Server est un système d’exploitation « administré à distance ».</span><span class="sxs-lookup"><span data-stu-id="07898-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="07898-133">Les binaires Core peuvent être déployés à l’aide de deux méthodes différentes.</span><span class="sxs-lookup"><span data-stu-id="07898-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="07898-134">Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.</span><span class="sxs-lookup"><span data-stu-id="07898-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="07898-135">En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="07898-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="07898-136">Dans les deux cas, vous avez besoin du package de la version ZIP Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="07898-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="07898-137">Déploiement hors connexion de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="07898-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="07898-138">Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.</span><span class="sxs-lookup"><span data-stu-id="07898-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="07898-139">Démontez l’image et démarrez-la.</span><span class="sxs-lookup"><span data-stu-id="07898-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="07898-140">Connectez-vous à l’instance de boîte de réception de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07898-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="07898-141">Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="07898-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="07898-142">Déploiement en ligne de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="07898-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="07898-143">La procédure suivante vous guide tout au long du déploiement de PowerShell Core sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="07898-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="07898-144">Connectez-vous à l’instance de boîte de réception de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07898-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="07898-145">Copiez le fichier sur l’instance de Nano Server</span><span class="sxs-lookup"><span data-stu-id="07898-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="07898-146">Entrez dans la session</span><span class="sxs-lookup"><span data-stu-id="07898-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="07898-147">Extrayez le fichier ZIP</span><span class="sxs-lookup"><span data-stu-id="07898-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="07898-148">Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="07898-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="07898-149">Instructions pour créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="07898-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="07898-150">PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH.</span><span class="sxs-lookup"><span data-stu-id="07898-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="07898-151">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="07898-151">For more information, see:</span></span>

- <span data-ttu-id="07898-152">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="07898-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="07898-153">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="07898-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="07898-154">Instructions d’installation des artefacts</span><span class="sxs-lookup"><span data-stu-id="07898-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="07898-155">Nous publions une archive avec des bits CoreCLR sur chaque build CI avec [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="07898-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="07898-156">Pour installer PowerShell Core à partir de l’artefact CoreCLR :</span><span class="sxs-lookup"><span data-stu-id="07898-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="07898-157">Téléchargez le package ZIP à partir de l’onglet des **artefacts** de la build spécifique.</span><span class="sxs-lookup"><span data-stu-id="07898-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="07898-158">Débloquez le fichier ZIP : cliquez avec le bouton droit dans l’Explorateur de fichiers -> Propriétés -> cochez la case Débloquer -> Appliquer</span><span class="sxs-lookup"><span data-stu-id="07898-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="07898-159">Extrayez le fichier zip dans le répertoire `bin`</span><span class="sxs-lookup"><span data-stu-id="07898-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[versions]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
