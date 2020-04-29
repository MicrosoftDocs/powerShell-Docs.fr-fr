---
title: Installation de PowerShell sur Windows
description: Informations sur l’installation de PowerShell sur Windows
ms.date: 08/06/2018
ms.openlocfilehash: a8543a91ad503364c5346a11c9c9d9f910547278
ms.sourcegitcommit: b80ce0396550d0896189d0205d6c4b4372ac2015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141378"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="93489-103">Installation de PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="93489-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="93489-104">Il existe plusieurs façons d’installer PowerShell Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="93489-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93489-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="93489-105">Prerequisites</span></span>

<span data-ttu-id="93489-106">La dernière version de PowerShell est prise en charge sur Windows 7 SP1, Server 2008 R2 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="93489-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="93489-107">Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="93489-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="93489-108">Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.</span><span class="sxs-lookup"><span data-stu-id="93489-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="93489-109">Il est disponible par téléchargement direct ou sur Windows Update.</span><span class="sxs-lookup"><span data-stu-id="93489-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="93489-110">Ce package est déjà installé sur les systèmes où tous les correctifs sont installés.</span><span class="sxs-lookup"><span data-stu-id="93489-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="93489-111">Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="93489-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="93489-112">Pour plus d’informations sur WMF, voir [Vue d’ensemble de WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="93489-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="93489-113">Télécharger le package du programme d’installation</span><span class="sxs-lookup"><span data-stu-id="93489-113">Download the installer package</span></span>

<span data-ttu-id="93489-114">Pour installer PowerShell sur Windows, téléchargez le package d’installation à partir de notre page de [versions][releases] GitHub.</span><span class="sxs-lookup"><span data-stu-id="93489-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="93489-115">Faites défiler jusqu'à la section **Ressources** de la page de versions.</span><span class="sxs-lookup"><span data-stu-id="93489-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="93489-116">Il est possible que la section **Ressources** soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="93489-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="93489-117"><a id="msi" />Installation du package MSI</span><span class="sxs-lookup"><span data-stu-id="93489-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="93489-118">Le fichier MSI ressemble à `PowerShell-<version>-win-<os-arch>.msi`.</span><span class="sxs-lookup"><span data-stu-id="93489-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="93489-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="93489-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="93489-120">Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="93489-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="93489-121">Le programme d’installation crée un raccourci dans le menu Démarrer de Windows.</span><span class="sxs-lookup"><span data-stu-id="93489-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="93489-122">Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="93489-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="93489-123">Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="93489-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="93489-124">PowerShell 7 s’installe dans un nouveau répertoire et s’exécute côte à côte avec Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="93489-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="93489-125">Pour PowerShell Core 6.x, PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="93489-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="93489-126">PowerShell 7 est installé sur `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="93489-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="93489-127">Le dossier `$env:ProgramFiles\PowerShell\7` est ajouté à `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="93489-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="93489-128">Le dossier `$env:ProgramFiles\PowerShell\6` est supprimé</span><span class="sxs-lookup"><span data-stu-id="93489-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="93489-129">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [d’installation ZIP](#zip).</span><span class="sxs-lookup"><span data-stu-id="93489-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="93489-130">Installation administrative à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="93489-130">Administrative install from the command line</span></span>

<span data-ttu-id="93489-131">Les packages MSI peuvent être installés à partir de la ligne de commande, ce qui permet aux administrateurs de déployer des packages sans interaction de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93489-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="93489-132">Le package MSI inclut les propriétés suivantes pour contrôler les options d’installation :</span><span class="sxs-lookup"><span data-stu-id="93489-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="93489-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : cette propriété contrôle l’option permettant d’ajouter l’élément **Ouvrir PowerShell** au menu contextuel dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="93489-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="93489-134">**ENABLE_PSREMOTING** : cette propriété contrôle l’option permettant d’activer la communication à distance PowerShell pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="93489-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="93489-135">**REGISTER_MANIFEST** : cette propriété contrôle l’option permettant d’enregistrer le manifeste de journalisation des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="93489-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="93489-136">L’exemple suivant montre comment installer PowerShell sans assistance avec toutes les options d’installation activées.</span><span class="sxs-lookup"><span data-stu-id="93489-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="93489-137">Pour obtenir une liste complète des options de ligne de commande pour `Msiexec.exe`, consultez [Options de ligne de commande](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="93489-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="93489-138"><a id="msix" />Installation du package MSIX</span><span class="sxs-lookup"><span data-stu-id="93489-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="93489-139">Pour installer manuellement le package MSIX sur un client Windows 10, téléchargez le package MSIX à partir de notre page des [versions][releases] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="93489-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="93489-140">Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="93489-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="93489-141">Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.</span><span class="sxs-lookup"><span data-stu-id="93489-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="93489-142">Le fichier MSIX se présente ainsi : `PowerShell-<version>-win-<os-arch>.msix`.</span><span class="sxs-lookup"><span data-stu-id="93489-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="93489-143">Pour installer le package, vous devez utiliser la cmdlet `Add-AppxPackage`.</span><span class="sxs-lookup"><span data-stu-id="93489-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="93489-144">Le package MSIX n’a pas encore été publié.</span><span class="sxs-lookup"><span data-stu-id="93489-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="93489-145">Une fois publié, le package sera disponible dans le Microsoft Store et à partir de la page de [versions][releases] GitHub.</span><span class="sxs-lookup"><span data-stu-id="93489-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="93489-146"><a id="zip" />Installation du package ZIP</span><span class="sxs-lookup"><span data-stu-id="93489-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="93489-147">Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="93489-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="93489-148">Contrairement aux packages MSI, l’installation de l’archive ZIP ne vérifie pas les prérequis.</span><span class="sxs-lookup"><span data-stu-id="93489-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="93489-149">Téléchargez l’archive ZIP à partir de la page des [mises en production][releases].</span><span class="sxs-lookup"><span data-stu-id="93489-149">Download the ZIP archive from the [releases][releases] page.</span></span> <span data-ttu-id="93489-150">Selon la façon dont vous téléchargez le fichier, vous devrez peut-être débloquer le fichier avec l’applet de commande `Unblock-File`.</span><span class="sxs-lookup"><span data-stu-id="93489-150">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="93489-151">Décompressez le contenu à l’emplacement de votre choix et exécutez `pwsh.exe` à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="93489-151">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="93489-152">Pour que la communication à distance via WSMan fonctionne correctement, vérifiez que vous respectez bien les [prérequis](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="93489-152">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="93489-153">Déploiement sur Windows 10 IoT Entreprise</span><span class="sxs-lookup"><span data-stu-id="93489-153">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="93489-154">Windows 10 IoT Entreprise contient Windows PowerShell, que l’on peut utiliser pour déployer PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="93489-154">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="93489-155">Créez `PSSession` sur l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="93489-155">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="93489-156">Copiez le fichier ZIP sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="93489-156">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="93489-157">Connectez-vous à l’appareil et développez l’archive</span><span class="sxs-lookup"><span data-stu-id="93489-157">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="93489-158">Configurez la communication à distance avec PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="93489-158">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="93489-159">Connectez-vous au point de terminaison PowerShell 7 sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="93489-159">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```
## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="93489-160">Déploiement sur Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="93489-160">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="93489-161">Windows 10 IoT Core ajoute Windows PowerShell lorsque vous incluez la fonctionnalité *IOT_POWERSHELL*, que nous pouvons utiliser pour déployer PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="93489-161">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="93489-162">Les étapes définies ci-dessus pour Windows 10 IoT Entreprise peuvent également être suivies pour IoT Core.</span><span class="sxs-lookup"><span data-stu-id="93489-162">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="93489-163">Pour ajouter la dernière version de PowerShell dans l’image d’expédition, utilisez la commande [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) pour inclure le package dans la zone de travail et ajouter la fonctionnalité *OPENSRC_POWERSHELL* à votre image.</span><span class="sxs-lookup"><span data-stu-id="93489-163">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="93489-164">Pour l’architecture ARM64, Windows PowerShell n’est pas ajouté lorsque vous incluez *IOT_POWERSHELL*.</span><span class="sxs-lookup"><span data-stu-id="93489-164">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="93489-165">L’installation basée sur zip ne fonctionne donc pas.</span><span class="sxs-lookup"><span data-stu-id="93489-165">So the zip based install will not work.</span></span>
> <span data-ttu-id="93489-166">Vous devrez utiliser la commande Import-PSCoreRelease pour l’ajouter dans l’image.</span><span class="sxs-lookup"><span data-stu-id="93489-166">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="93489-167">Déploiement sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="93489-167">Deploying on Nano Server</span></span>

<span data-ttu-id="93489-168">Ces instructions partent du principe que Nano Server est un système d’exploitation sans périphériques de contrôle (« headless ») sur lequel une version de PowerShell est déjà en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="93489-168">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="93489-169">Pour plus d’informations, consultez la documentation [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="93489-169">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="93489-170">Il existe deux façons différentes de déployer des binaires PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93489-170">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="93489-171">Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.</span><span class="sxs-lookup"><span data-stu-id="93489-171">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="93489-172">En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="93489-172">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="93489-173">Dans les deux cas, vous avez besoin du package ZIP de la version de Windows 10 x64.</span><span class="sxs-lookup"><span data-stu-id="93489-173">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="93489-174">Exécutez les commandes dans une instance « Administrateur » de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93489-174">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="93489-175">Déploiement hors connexion de PowerShell</span><span class="sxs-lookup"><span data-stu-id="93489-175">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="93489-176">Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.</span><span class="sxs-lookup"><span data-stu-id="93489-176">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="93489-177">Démontez l’image et démarrez-la.</span><span class="sxs-lookup"><span data-stu-id="93489-177">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="93489-178">Connectez-vous à l’instance de boîte de réception de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93489-178">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="93489-179">Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="93489-179">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="93489-180">Déploiement en ligne de PowerShell</span><span class="sxs-lookup"><span data-stu-id="93489-180">Online Deployment of PowerShell</span></span>

<span data-ttu-id="93489-181">Déployez PowerShell sur Nano Server en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="93489-181">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="93489-182">Connectez-vous à l’instance de boîte de réception de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="93489-182">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="93489-183">Copiez le fichier sur l’instance de Nano Server</span><span class="sxs-lookup"><span data-stu-id="93489-183">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="93489-184">Entrez dans la session</span><span class="sxs-lookup"><span data-stu-id="93489-184">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="93489-185">Extrayez le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="93489-185">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="93489-186">Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="93489-186">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="93489-187">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="93489-187">Install as a .NET Global tool</span></span>

<span data-ttu-id="93489-188">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="93489-188">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="93489-189">Le programme d’installation de l’outil dotnet ajoute `$env:USERPROFILE\dotnet\tools` à votre variable d’environnement `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="93489-189">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="93489-190">Toutefois, le `$env:PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="93489-190">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="93489-191">Vous pouvez démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="93489-191">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="93489-192">Comment créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="93489-192">How to create a remoting endpoint</span></span>

<span data-ttu-id="93489-193">PowerShell prend en charge le protocole de communication à distance PowerShell (PSRP) sur WSMan et SSH.</span><span class="sxs-lookup"><span data-stu-id="93489-193">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="93489-194">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="93489-194">For more information, see:</span></span>

- <span data-ttu-id="93489-195">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="93489-195">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="93489-196">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="93489-196">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
