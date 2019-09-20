---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Problèmes connus dans WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147739"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="55557-103">Problèmes connus dans WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="55557-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="55557-104">Les raccourcis PowerShell sont rompus lors de la première utilisation</span><span class="sxs-lookup"><span data-stu-id="55557-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="55557-105">**Résolution :** Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="55557-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="55557-106">Cliquez avec le bouton droit sur le raccourci PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55557-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="55557-107">Sélectionnez « Windows PowerShell » pour le lancer sans élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="55557-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="55557-108">Cliquez avec le bouton droit sur le raccourci PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55557-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="55557-109">Cliquez avec le bouton droit sur « Windows PowerShell » et sélectionnez « Exécuter en tant qu’administrateur » pour le lancer avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="55557-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="55557-110">Les raccourcis PowerShell fonctionneront une fois que vous aurez effectué l’une des actions ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="55557-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="55557-111">Vous ne devez effectuer ces actions qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="55557-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="55557-112">Les modules PowerShell et les ressources DSC signalent des erreurs concernant ExecutionPolicy sur Windows 7</span><span class="sxs-lookup"><span data-stu-id="55557-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="55557-113">Sur Windows 7, l’utilisation de modules PowerShell et de ressources DSC risque de provoquer des erreurs liées à ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="55557-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="55557-114">**Résolution :** Donnez la valeur **RemoteSigned** à ExecutionPolicy en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="55557-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="55557-115">La connexion à un ancien point de terminaison Exchange distant provoque un blocage</span><span class="sxs-lookup"><span data-stu-id="55557-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="55557-116">L’ancien point de terminaison Exchange redirige vers un nouveau point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="55557-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="55557-117">Un bogue dans la logique de redirection provoque un blocage.</span><span class="sxs-lookup"><span data-stu-id="55557-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="55557-118">**Résolution :** Connectez-vous directement au nouveau point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="55557-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="55557-119">La fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation de WMF 5.0 sur Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="55557-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="55557-120">Quand vous installez WMF 5.0 sur un ordinateur Windows Server 2012 R2 qui exécute déjà SIL, la fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation.</span><span class="sxs-lookup"><span data-stu-id="55557-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="55557-121">**Résolution :** Exécutez une fois la cmdlet `Start-SilLogging` après l’installation de WMF, car le processus d’installation arrête la fonctionnalité de Journalisation de l’inventaire logiciel de façon non contrôlée.</span><span class="sxs-lookup"><span data-stu-id="55557-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="55557-122">`Get-ChildItem` ne fonctionne pas si -LiteralPath et -Recurse sont utilisés ensemble</span><span class="sxs-lookup"><span data-stu-id="55557-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="55557-123">Si un nom de répertoire contient un caractère non valide, `Get-ChildItem` ne génère pas les résultats attendus quand -LiteralPath et -Recurse sont utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="55557-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="55557-124">**Résolution :** La solution de contournement actuelle, qui n’est pas idéale, consiste à implémenter la récursivité dans le script plutôt que de se fier à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="55557-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="55557-125">Sysprep échoue après l’installation de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="55557-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="55557-126">Il existe deux solutions de contournement pour résoudre ce problème, selon la version de Windows Server que vous exécutez.</span><span class="sxs-lookup"><span data-stu-id="55557-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="55557-127">**Résolution :**</span><span class="sxs-lookup"><span data-stu-id="55557-127">**Resolution:**</span></span>

- <span data-ttu-id="55557-128">Pour les systèmes exécutant **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="55557-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="55557-129">Ouvrez PowerShell en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="55557-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="55557-130">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="55557-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="55557-131">Exécutez la commande et ignorez les erreurs, qui sont normales.</span><span class="sxs-lookup"><span data-stu-id="55557-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="55557-132">Supprimez les fichiers du répertoire \Windows\System32\Logfiles\SIL\.</span><span class="sxs-lookup"><span data-stu-id="55557-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="55557-133">Installez toutes les mises à jour Windows importantes disponibles et lancez l’opération Sysprep normalement.</span><span class="sxs-lookup"><span data-stu-id="55557-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="55557-134">Pour les systèmes exécutant **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="55557-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="55557-135">Après avoir installé WMF 5.0 sur le serveur sur lequel Sysprep sera exécuté, connectez-vous en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="55557-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="55557-136">Copiez Generize.xml du répertoire `\Windows\System32\Sysprep\ActionFiles\` vers un emplacement en dehors du répertoire Windows, par exemple `C:\`.</span><span class="sxs-lookup"><span data-stu-id="55557-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="55557-137">Ouvrez votre copie de Generalize.xml avec le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="55557-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="55557-138">Recherchez et supprimez les lignes suivantes. Une instance de chaque doit être supprimée (elles se trouvent vers la fin du document).</span><span class="sxs-lookup"><span data-stu-id="55557-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="55557-139">Enregistrez la copie modifiée de Generalize.xml et fermez le fichier.</span><span class="sxs-lookup"><span data-stu-id="55557-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="55557-140">Ouvrez une invite de commandes en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="55557-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="55557-141">Exécutez la commande suivante pour prendre possession du fichier Generalize.xml dans le dossier system32 :</span><span class="sxs-lookup"><span data-stu-id="55557-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="55557-142">Exécutez la commande suivante pour définir l’autorisation appropriée sur le fichier :</span><span class="sxs-lookup"><span data-stu-id="55557-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="55557-143">Répondez Oui à l’invite de confirmation.</span><span class="sxs-lookup"><span data-stu-id="55557-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="55557-144">Notez que `<AdministratorUserName>` doit être remplacé par le nom d’utilisateur qui est administrateur sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55557-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="55557-145">Par exemple, « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="55557-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="55557-146">Copiez le fichier que vous avez modifié et enregistré dans le répertoire Sysprep à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="55557-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="55557-147">Répondez Oui pour remplacer (vérifiez le chemin entré en l’absence d’invite de remplacement).</span><span class="sxs-lookup"><span data-stu-id="55557-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="55557-148">Cette commande suppose que votre copie modifiée de Generalize.xml a été copiée dans C:\.</span><span class="sxs-lookup"><span data-stu-id="55557-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="55557-149">Generalize.XML est désormais mis à jour grâce à la solution de contournement.</span><span class="sxs-lookup"><span data-stu-id="55557-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="55557-150">Exécutez Sysprep avec l’option generalize activée.</span><span class="sxs-lookup"><span data-stu-id="55557-150">Please run Sysprep with the generalize option enabled.</span></span>