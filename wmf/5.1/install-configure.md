---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
contributor: keithb
title: Installer et configurer WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055984"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="d79d8-103">Installer et configurer WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d79d8-103">Install and Configure WMF 5.1</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="d79d8-104">Télécharger et installer le package WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d79d8-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="d79d8-105">Téléchargez le package WMF 5.1 correspondant au système d’exploitation et à l’architecture sur lesquels vous souhaitez installer :</span><span class="sxs-lookup"><span data-stu-id="d79d8-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="d79d8-106">Système d'exploitation</span><span class="sxs-lookup"><span data-stu-id="d79d8-106">Operating System</span></span>       | <span data-ttu-id="d79d8-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d79d8-107">Prerequisites</span></span>           | <span data-ttu-id="d79d8-108">Liens de package</span><span class="sxs-lookup"><span data-stu-id="d79d8-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="d79d8-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d79d8-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="d79d8-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="d79d8-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d79d8-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="d79d8-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="d79d8-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d79d8-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="d79d8-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="d79d8-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="d79d8-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d79d8-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="d79d8-117">**x64 :** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="d79d8-118">**x86 :** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="d79d8-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d79d8-119">Windows 7 SP1</span></span>          | <span data-ttu-id="d79d8-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="d79d8-121">**x64 :** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="d79d8-122">**x86 :** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="d79d8-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="d79d8-129">Installer WMF 5.1 pour Windows Server 2008 R2 et Windows 7</span><span class="sxs-lookup"><span data-stu-id="d79d8-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="d79d8-130">Les instructions d’installation pour Windows Server 2008 R2 et Windows 7 ont été modifiées et diffèrent désormais de celles des autres packages.</span><span class="sxs-lookup"><span data-stu-id="d79d8-130">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="d79d8-131">Les instructions d’installation pour Windows Server 2012 R2, Windows Server 2012 et Windows 8.1 sont indiquées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d79d8-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="d79d8-132">**Installation de WMF 5.1 sur Windows Server 2008 R2 et Windows 7**</span><span class="sxs-lookup"><span data-stu-id="d79d8-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="d79d8-133">Accédez au dossier dans lequel vous avez téléchargé le fichier ZIP.</span><span class="sxs-lookup"><span data-stu-id="d79d8-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="d79d8-134">Cliquez avec le bouton droit sur le fichier ZIP, puis sélectionnez « Extraire tout ».</span><span class="sxs-lookup"><span data-stu-id="d79d8-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="d79d8-135">Le fichier ZIP contient 2 fichiers : un fichier MSU et le fichier de script Install-WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="d79d8-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="d79d8-136">Une fois le fichier ZIP décompressé, vous pouvez copier le contenu sur n’importe quel ordinateur exécutant Windows 7 ou Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="d79d8-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="d79d8-137">Après avoir extrait le contenu du fichier ZIP, ouvrez PowerShell en tant qu’administrateur, puis accédez au dossier dans lequel figure le contenu du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="d79d8-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="d79d8-138">Exécutez le script Install-Wmf5.1.ps1 dans ce dossier et suivez les instructions.</span><span class="sxs-lookup"><span data-stu-id="d79d8-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="d79d8-139">Ce script vérifie les prérequis sur l’ordinateur local et, s’ils sont respectés, installe WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="d79d8-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="d79d8-140">Les prérequis sont répertoriés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d79d8-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="d79d8-141">Install-WMF5.1.ps1 accepte les paramètres suivants pour faciliter l’automatisation de l’installation sur Windows Server 2008 R2 et Windows 7 :</span><span class="sxs-lookup"><span data-stu-id="d79d8-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="d79d8-142">AcceptEula : quand ce paramètre est inclus, le CLUF est accepté automatiquement et n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="d79d8-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="d79d8-143">AllowRestart : ce paramètre peut être utilisé uniquement si AcceptEula est spécifié.</span><span class="sxs-lookup"><span data-stu-id="d79d8-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="d79d8-144">Si ce paramètre est inclus et qu’un redémarrage est nécessaire après l’installation de WMF 5.1, l’ordinateur redémarre sans invite dès l’installation terminée.</span><span class="sxs-lookup"><span data-stu-id="d79d8-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="d79d8-145">**Prérequis à l’installation de WMF 5.1 sur Windows Server 2008 R2 SP1 et Windows 7 SP1**</span><span class="sxs-lookup"><span data-stu-id="d79d8-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="d79d8-146">L’installation de WMF 5.1 sur Windows Server 2008 R2 SP1 ou Windows 7 SP1 nécessite ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d79d8-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="d79d8-147">Le dernier Service Pack doit est installé.</span><span class="sxs-lookup"><span data-stu-id="d79d8-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="d79d8-148">WMF 3.0 **ne doit pas** être installé.</span><span class="sxs-lookup"><span data-stu-id="d79d8-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="d79d8-149">L’installation de WMF 5.1 sur WMF 3.0 entraîne la perte de PSModulePath, ce qui peut provoquer l’échec d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="d79d8-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="d79d8-150">Avant d’installer WMF 5.1, vous devez soit désinstaller WMF 3.0, soit enregistrer PSModulePath et le restaurer manuellement au terme de l’installation de WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="d79d8-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="d79d8-151">WMF 5.1 nécessite au moins [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="d79d8-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="d79d8-152">Vous pouvez installer Microsoft .NET Framework 4.5.2 en suivant les instructions à l’emplacement du téléchargement.</span><span class="sxs-lookup"><span data-stu-id="d79d8-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="d79d8-153">**Dépendance de WinRM**</span><span class="sxs-lookup"><span data-stu-id="d79d8-153">**WinRM Dependency**</span></span>

<span data-ttu-id="d79d8-154">Windows PowerShell Desired State Configuration (DSC) dépend de WinRM.</span><span class="sxs-lookup"><span data-stu-id="d79d8-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="d79d8-155">WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7.</span><span class="sxs-lookup"><span data-stu-id="d79d8-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="d79d8-156">Exécutez `Set-WSManQuickConfig` dans une session Windows PowerShell avec élévation des privilèges pour activer WinRM.</span><span class="sxs-lookup"><span data-stu-id="d79d8-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="d79d8-157">Installer WMF 5.1 pour Windows Server 2012 R2, Windows Server 2012 et Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d79d8-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

<span data-ttu-id="d79d8-158">**Installer à partir de l’Explorateur Windows (ou de l’Explorateur de fichiers dans Windows Server 2012 R2 ou Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="d79d8-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="d79d8-159">Accédez au dossier dans lequel vous avez téléchargé le fichier MSU.</span><span class="sxs-lookup"><span data-stu-id="d79d8-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="d79d8-160">Double-cliquez sur le fichier MSU pour l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d79d8-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="d79d8-161">**Installation à partir de l’invite de commandes**</span><span class="sxs-lookup"><span data-stu-id="d79d8-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="d79d8-162">Après avoir téléchargé le package correspondant à l’architecture de votre ordinateur, ouvrez une fenêtre d’invite de commandes avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="d79d8-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="d79d8-163">Dans les options d’installation Server Core de Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, une invite de commandes s’ouvre avec des droits d’utilisateur avec élévation de privilèges par défaut.</span><span class="sxs-lookup"><span data-stu-id="d79d8-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="d79d8-164">Accédez au dossier dans lequel vous avez téléchargé ou copié le package d’installation WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="d79d8-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="d79d8-165">Exécutez l’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d79d8-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="d79d8-166">Sur les ordinateurs qui exécutent Windows Server 2012 R2 ou Windows 8.1 x64, exécutez `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="d79d8-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="d79d8-167">Sur les ordinateurs qui exécutent Windows Server 2012, exécutez `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="d79d8-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="d79d8-168">Sur les ordinateurs qui exécutent Windows 8.1 x86, exécutez `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="d79d8-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="d79d8-169">L’installation de WMF 5.1 nécessite un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="d79d8-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="d79d8-170">L’option `/quiet` redémarre le système sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="d79d8-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="d79d8-171">Utilisez l’option `/norestart` pour éviter le redémarrage.</span><span class="sxs-lookup"><span data-stu-id="d79d8-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="d79d8-172">Toutefois, WMF 5.1 ne sera pas installé tant que vous n’avez pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="d79d8-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
