---
title: Installation de PowerShell Core sous Windows
description: Informations sur l’installation de PowerShell Core sur Windows
ms.date: 08/06/2018
ms.openlocfilehash: c06eba06e376c3f795ab9c0fae9270cf6cf8f2ce
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444463"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="5c4b3-103">Installation de PowerShell Core sous Windows</span><span class="sxs-lookup"><span data-stu-id="5c4b3-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="5c4b3-104">Il existe plusieurs façons d’installer PowerShell Core dans Windows.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="5c4b3-105">Si vous avez déjà installé le kit [SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant qu’[outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="5c4b3-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5c4b3-106">Prerequisites</span></span>

<span data-ttu-id="5c4b3-107">Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="5c4b3-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="5c4b3-108">Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="5c4b3-109">Il est disponible par téléchargement direct ou sur Windows Update.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="5c4b3-110">Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="5c4b3-111">Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="5c4b3-112">Pour plus d’informations sur WMF, voir [Vue d’ensemble de WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-112">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="5c4b3-113"><a id="msi" />Installation du package MSI</span><span class="sxs-lookup"><span data-stu-id="5c4b3-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="5c4b3-114">Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2, et versions ultérieures), téléchargez le package MSI à partir de notre page de [versions][releases] GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="5c4b3-115">Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="5c4b3-116">Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="5c4b3-117">Le fichier MSI ressemble à ceci : `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="5c4b3-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="5c4b3-118">Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="5c4b3-119">Le programme d’installation crée un raccourci dans le menu Démarrer de Windows.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="5c4b3-120">Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="5c4b3-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="5c4b3-121">Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="5c4b3-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="5c4b3-122">Installation administrative à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="5c4b3-122">Administrative install from the command line</span></span>

<span data-ttu-id="5c4b3-123">Les packages MSI peuvent être installés à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="5c4b3-124">Cela permet aux administrateurs de déployer des packages sans l’intervention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="5c4b3-125">Le package MSI pour PowerShell inclut les propriétés suivantes pour contrôler les options d’installation :</span><span class="sxs-lookup"><span data-stu-id="5c4b3-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="5c4b3-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : cette propriété contrôle l’option permettant d’ajouter l’élément **Ouvrir PowerShell** au menu contextuel dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="5c4b3-127">**ENABLE_PSREMOTING** : cette propriété contrôle l’option permettant d’activer la communication à distance PowerShell pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="5c4b3-128">**REGISTER_MANIFEST** : cette propriété contrôle l’option permettant d’enregistrer le manifeste de journalisation des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="5c4b3-129">Les exemples suivants montrent comment installer PowerShell Core sans assistance avec toutes les options d’installation activées.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="5c4b3-130">Pour obtenir une liste complète des options de ligne de commande pour Msiexec.exe, consultez [Options de ligne de commande](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="5c4b3-131"><a id="zip" />Installation du package ZIP</span><span class="sxs-lookup"><span data-stu-id="5c4b3-131"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="5c4b3-132">Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-132">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="5c4b3-133">Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-133">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="5c4b3-134">Pour que la communication à distance via WSMan fonctionne correctement, vérifiez que vous respectez bien les [prérequis](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-134">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="5c4b3-135">Déploiement sur Windows IoT</span><span class="sxs-lookup"><span data-stu-id="5c4b3-135">Deploying on Windows IoT</span></span>

<span data-ttu-id="5c4b3-136">Windows IoT est déjà équipé de Windows PowerShell que nous utiliserons pour déployer PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-136">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="5c4b3-137">Créez `PSSession` sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="5c4b3-137">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="5c4b3-138">Copiez le fichier ZIP sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="5c4b3-138">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="5c4b3-139">Connectez-vous à l’appareil et développez l’archive</span><span class="sxs-lookup"><span data-stu-id="5c4b3-139">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="5c4b3-140">Configurez la communication à distance avec PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="5c4b3-140">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="5c4b3-141">Connectez-vous au point de terminaison PowerShell Core 6 sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="5c4b3-141">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="5c4b3-142">Déploiement sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="5c4b3-142">Deploying on Nano Server</span></span>

<span data-ttu-id="5c4b3-143">Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-143">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="5c4b3-144">Nano Server est un système d’exploitation « administré à distance ».</span><span class="sxs-lookup"><span data-stu-id="5c4b3-144">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="5c4b3-145">Les binaires Core peuvent être déployés à l’aide de deux méthodes différentes.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-145">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="5c4b3-146">Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-146">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="5c4b3-147">En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-147">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="5c4b3-148">Dans les deux cas, vous avez besoin du package de la version ZIP Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="5c4b3-148">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="5c4b3-149">Déploiement hors connexion de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5c4b3-149">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="5c4b3-150">Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-150">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="5c4b3-151">Démontez l’image et démarrez-la.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-151">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="5c4b3-152">Connectez-vous à l’instance de boîte de réception de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-152">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="5c4b3-153">Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-153">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="5c4b3-154">Déploiement en ligne de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5c4b3-154">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="5c4b3-155">La procédure suivante vous guide tout au long du déploiement de PowerShell Core sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-155">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="5c4b3-156">Connectez-vous à l’instance de boîte de réception de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c4b3-156">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="5c4b3-157">Copiez le fichier sur l’instance de Nano Server</span><span class="sxs-lookup"><span data-stu-id="5c4b3-157">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="5c4b3-158">Entrez dans la session</span><span class="sxs-lookup"><span data-stu-id="5c4b3-158">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="5c4b3-159">Extrayez le fichier ZIP</span><span class="sxs-lookup"><span data-stu-id="5c4b3-159">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="5c4b3-160">Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5c4b3-160">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="5c4b3-161">Comment créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="5c4b3-161">How to create a remoting endpoint</span></span>

<span data-ttu-id="5c4b3-162">PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH.</span><span class="sxs-lookup"><span data-stu-id="5c4b3-162">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="5c4b3-163">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="5c4b3-163">For more information, see:</span></span>

- <span data-ttu-id="5c4b3-164">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="5c4b3-164">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="5c4b3-165">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="5c4b3-165">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
