---
title: Installation de PowerShell sur Windows
description: Informations sur l’installation de PowerShell sur Windows
ms.date: 08/06/2018
ms.openlocfilehash: bb0971b6c4ac99bde70b226da2becf2f4ed82083
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082775"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="a8bf5-103">Installation de PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="a8bf5-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="a8bf5-104">Il existe plusieurs façons d’installer PowerShell Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8bf5-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a8bf5-105">Prerequisites</span></span>

<span data-ttu-id="a8bf5-106">Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="a8bf5-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="a8bf5-107">Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="a8bf5-108">Il est disponible par téléchargement direct ou sur Windows Update.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="a8bf5-109">Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="a8bf5-110">Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="a8bf5-111">Pour plus d’informations sur WMF, voir [Vue d’ensemble de WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-111">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="a8bf5-112"><a id="msi" />Installation du package MSI</span><span class="sxs-lookup"><span data-stu-id="a8bf5-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="a8bf5-113">Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2, et versions ultérieures), téléchargez le package MSI à partir de notre page de [versions][releases] GitHub.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="a8bf5-114">Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="a8bf5-115">Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="a8bf5-116">Le fichier MSI ressemble à ceci : `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="a8bf5-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>

<span data-ttu-id="a8bf5-117">Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="a8bf5-118">Le programme d’installation crée un raccourci dans le menu Démarrer de Windows.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="a8bf5-119">Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="a8bf5-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="a8bf5-120">Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="a8bf5-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="a8bf5-121">PowerShell 7 s’installe dans un nouveau répertoire et s’exécute côte à côte avec Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-121">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="a8bf5-122">Pour PowerShell Core 6.x, PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-122">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="a8bf5-123">PowerShell 7 est installé sur `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="a8bf5-123">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
> - <span data-ttu-id="a8bf5-124">Le dossier `%programfiles%\PowerShell\7` est ajouté à `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="a8bf5-124">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="a8bf5-125">Le dossier `%programfiles%\PowerShell\6` est supprimé</span><span class="sxs-lookup"><span data-stu-id="a8bf5-125">The `%programfiles%\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="a8bf5-126">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [d’installation ZIP](#zip).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-126">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="a8bf5-127">Installation administrative à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a8bf5-127">Administrative install from the command line</span></span>

<span data-ttu-id="a8bf5-128">Les packages MSI peuvent être installés à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-128">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="a8bf5-129">Cela permet aux administrateurs de déployer des packages sans l’intervention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-129">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="a8bf5-130">Le package MSI pour PowerShell inclut les propriétés suivantes pour contrôler les options d’installation :</span><span class="sxs-lookup"><span data-stu-id="a8bf5-130">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="a8bf5-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : cette propriété contrôle l’option permettant d’ajouter l’élément **Ouvrir PowerShell** au menu contextuel dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="a8bf5-132">**ENABLE_PSREMOTING** : cette propriété contrôle l’option permettant d’activer la communication à distance PowerShell pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-132">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="a8bf5-133">**REGISTER_MANIFEST** : cette propriété contrôle l’option permettant d’enregistrer le manifeste de journalisation des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-133">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="a8bf5-134">Les exemples suivants montrent comment installer PowerShell sans assistance avec toutes les options d’installation activées.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-134">The following examples shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="a8bf5-135">Pour obtenir une liste complète des options de ligne de commande pour Msiexec.exe, consultez [Options de ligne de commande](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-135">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="a8bf5-136"><a id="msix" />Installation du package MSIX</span><span class="sxs-lookup"><span data-stu-id="a8bf5-136"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="a8bf5-137">Pour installer manuellement le package MSIX sur un client Windows 10, téléchargez le package MSIX à partir de notre page des [versions][releases] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-137">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="a8bf5-138">Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-138">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="a8bf5-139">Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-139">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="a8bf5-140">Le fichier MSIX se présente ainsi : `PowerShell-<version>-win-<os-arch>.msix`.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-140">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="a8bf5-141">Une fois téléchargé, vous ne pouvez pas simplement double-cliquer sur le programme d’installation, car ce package requiert l’utilisation de ressources non virtualisées.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-141">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="a8bf5-142">Pour installer, vous devez utiliser la cmdlet `Add-AppxPackage` :</span><span class="sxs-lookup"><span data-stu-id="a8bf5-142">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><span data-ttu-id="a8bf5-143"><a id="zip" />Installation du package ZIP</span><span class="sxs-lookup"><span data-stu-id="a8bf5-143"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="a8bf5-144">Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-144">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="a8bf5-145">Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-145">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="a8bf5-146">Pour que la communication à distance via WSMan fonctionne correctement, vérifiez que vous respectez bien les [prérequis](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-146">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="a8bf5-147">Déploiement sur Windows IoT</span><span class="sxs-lookup"><span data-stu-id="a8bf5-147">Deploying on Windows IoT</span></span>

<span data-ttu-id="a8bf5-148">Windows IoT est déjà équipé de Windows PowerShell, que l’on peut utiliser pour déployer PowerShell Core 7.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-148">Windows IoT already comes with Windows PowerShell which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="a8bf5-149">Créez `PSSession` sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="a8bf5-149">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="a8bf5-150">Copiez le fichier ZIP sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="a8bf5-150">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="a8bf5-151">Connectez-vous à l’appareil et développez l’archive</span><span class="sxs-lookup"><span data-stu-id="a8bf5-151">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="a8bf5-152">Configurez la communication à distance avec PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="a8bf5-152">Setup remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="a8bf5-153">Connectez-vous au point de terminaison PowerShell 7 sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="a8bf5-153">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="a8bf5-154">Déploiement sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="a8bf5-154">Deploying on Nano Server</span></span>

<span data-ttu-id="a8bf5-155">Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-155">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="a8bf5-156">Nano Server est un système d’exploitation « administré à distance ».</span><span class="sxs-lookup"><span data-stu-id="a8bf5-156">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="a8bf5-157">Il existe deux façons différentes de déployer des binaires PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-157">PowerShell binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="a8bf5-158">Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-158">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="a8bf5-159">En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-159">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="a8bf5-160">Dans les deux cas, vous avez besoin du package de la version ZIP Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="a8bf5-160">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="a8bf5-161">Déploiement hors connexion de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8bf5-161">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="a8bf5-162">Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-162">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="a8bf5-163">Démontez l’image et démarrez-la.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-163">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="a8bf5-164">Connectez-vous à l’instance de boîte de réception de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-164">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="a8bf5-165">Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-165">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="a8bf5-166">Déploiement en ligne de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8bf5-166">Online Deployment of PowerShell</span></span>

<span data-ttu-id="a8bf5-167">La procédure suivante décrit le déploiement de PowerShell sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-167">The following steps guide you through the deployment of PowerShell to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="a8bf5-168">Connectez-vous à l’instance de boîte de réception de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8bf5-168">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="a8bf5-169">Copiez le fichier sur l’instance de Nano Server</span><span class="sxs-lookup"><span data-stu-id="a8bf5-169">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="a8bf5-170">Entrez dans la session</span><span class="sxs-lookup"><span data-stu-id="a8bf5-170">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="a8bf5-171">Extrayez le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-171">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="a8bf5-172">Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-172">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="a8bf5-173">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="a8bf5-173">Install as a .NET Global tool</span></span>

<span data-ttu-id="a8bf5-174">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="a8bf5-174">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="a8bf5-175">Le programme d’installation de l’outil dotnet ajoute `$env:USERPROFILE\dotnet\tools` à votre variable d’environnement `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-175">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="a8bf5-176">Toutefois, le `$env:PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-176">However, the currently running shell does not have the updated `$env:PATH`.</span></span> <span data-ttu-id="a8bf5-177">Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-177">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="a8bf5-178">Comment créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="a8bf5-178">How to create a remoting endpoint</span></span>

<span data-ttu-id="a8bf5-179">PowerShell prend en charge le protocole de communication à distance PowerShell (PSRP) sur WSMan et SSH.</span><span class="sxs-lookup"><span data-stu-id="a8bf5-179">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="a8bf5-180">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8bf5-180">For more information, see:</span></span>

- <span data-ttu-id="a8bf5-181">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="a8bf5-181">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="a8bf5-182">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="a8bf5-182">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
