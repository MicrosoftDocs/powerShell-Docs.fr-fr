---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186828"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="b0e10-102">Limitations et problèmes connus</span><span class="sxs-lookup"><span data-stu-id="b0e10-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="b0e10-103">Les raccourcis PowerShell sont rompus lors de la première utilisation</span><span class="sxs-lookup"><span data-stu-id="b0e10-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="b0e10-104">**Résolution :** Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0e10-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="b0e10-105">Cliquez avec le bouton droit sur le raccourci PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0e10-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="b0e10-106">Sélectionnez « Windows PowerShell » pour le démarrer sans autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="b0e10-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="b0e10-107">Cliquez avec le bouton droit sur le raccourci PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0e10-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="b0e10-108">Cliquez avec le bouton droit sur « Windows PowerShell » et sélectionnez « Exécuter en tant qu’administrateur » pour le démarrer en mode élevé.</span><span class="sxs-lookup"><span data-stu-id="b0e10-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="b0e10-109">Les raccourcis PowerShell fonctionneront une fois que vous aurez effectué l’une des actions ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b0e10-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="b0e10-110">Vous ne devez effectuer ces actions qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="b0e10-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="b0e10-111">Les modules PowerShell et les ressources DSC signalent des erreurs concernant ExecutionPolicy sur Windows 7</span><span class="sxs-lookup"><span data-stu-id="b0e10-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="b0e10-112">Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="b0e10-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="b0e10-113">**Résolution :** Affectez la valeur RemoteSigned à ExecutionPolicy en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="b0e10-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="b0e10-114">La connexion à un ancien point de terminaison Exchange distant provoque un blocage</span><span class="sxs-lookup"><span data-stu-id="b0e10-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="b0e10-115">L’ancien point de terminaison Exchange redirige vers un nouveau point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b0e10-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="b0e10-116">Un bogue dans la logique de redirection provoque un blocage.</span><span class="sxs-lookup"><span data-stu-id="b0e10-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="b0e10-117">**Résolution :** Connectez-vous directement au nouveau point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b0e10-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="b0e10-118">La fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation de WMF 5.0 sur Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b0e10-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="b0e10-119">Quand vous installez WMF 5.0 sur un ordinateur Windows Server 2012 R2 qui exécute déjà SIL, la fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation.</span><span class="sxs-lookup"><span data-stu-id="b0e10-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="b0e10-120">**Résolution :** Exécutez l’applet de commande Start-SilLogging une fois après l’installation de WMF, car le processus d’installation arrête la fonctionnalité de journalisation de l’inventaire logiciel de façon non contrôlée.</span><span class="sxs-lookup"><span data-stu-id="b0e10-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="b0e10-121">Get-ChildItem ne fonctionne pas si -LiteralPath et -Recurse sont utilisés ensemble</span><span class="sxs-lookup"><span data-stu-id="b0e10-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="b0e10-122">Si un nom de répertoire contient un caractère non valide, Get-ChildItem ne génère pas les résultats attendus quand -LiteralPath et -Recurse sont utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="b0e10-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="b0e10-123">**Résolution :** La solution de contournement actuelle, qui n’est pas idéale, consiste à implémenter la récursivité dans le script plutôt que de se fier à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0e10-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="b0e10-124">Sysprep échoue après l’installation de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="b0e10-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="b0e10-125">Il existe deux solutions de contournement pour résoudre ce problème, selon la version de Windows Server que vous exécutez.</span><span class="sxs-lookup"><span data-stu-id="b0e10-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="b0e10-126">**Résolution :**</span><span class="sxs-lookup"><span data-stu-id="b0e10-126">**Resolution:**</span></span>
- <span data-ttu-id="b0e10-127">Pour les systèmes exécutant **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="b0e10-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="b0e10-128">Ouvrez PowerShell en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b0e10-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="b0e10-129">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b0e10-129">Run the following command</span></span>

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="b0e10-130">Exécutez la commande et ignorez les erreurs, qui sont normales.</span><span class="sxs-lookup"><span data-stu-id="b0e10-130">Run the command and ignore the error, as they are expected.</span></span>

  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="b0e10-131">Supprimez les fichiers du répertoire \Windows\System32\Logfiles\SIL\.</span><span class="sxs-lookup"><span data-stu-id="b0e10-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="b0e10-132">Installez toutes les mises à jour Windows importantes disponibles et lancez l’opération Sysprep normalement.</span><span class="sxs-lookup"><span data-stu-id="b0e10-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="b0e10-133">Pour les systèmes exécutant **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="b0e10-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="b0e10-134">Après l’installation de WMF 5.0 sur le serveur sur lequel exécuter Sysprep, connectez-vous en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b0e10-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="b0e10-135">Copiez Generize.xml à partir du répertoire \Windows\System32\Sysprep\ActionFiles\ vers un emplacement en dehors du répertoire Windows, C:\ par exemple.</span><span class="sxs-lookup"><span data-stu-id="b0e10-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="b0e10-136">Ouvrez votre copie de Generalize.xml avec le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="b0e10-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="b0e10-137">Recherchez et supprimez les lignes suivantes. Une instance de chaque doit être supprimée (elles se trouvent vers la fin du document).</span><span class="sxs-lookup"><span data-stu-id="b0e10-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="b0e10-138">Enregistrez la copie modifiée de Generalize.xml et fermez le fichier.</span><span class="sxs-lookup"><span data-stu-id="b0e10-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="b0e10-139">Ouvrez une invite de commandes en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b0e10-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="b0e10-140">Exécutez la commande suivante pour prendre possession du fichier Generalize.xml dans le dossier system32 :</span><span class="sxs-lookup"><span data-stu-id="b0e10-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    <span data-ttu-id="b0e10-141">Exécutez la commande suivante pour définir l’autorisation appropriée sur le fichier :</span><span class="sxs-lookup"><span data-stu-id="b0e10-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * <span data-ttu-id="b0e10-142">Répondez Oui à l’invite de confirmation.</span><span class="sxs-lookup"><span data-stu-id="b0e10-142">Answer Yes at the prompt for confirmation.</span></span>
      * <span data-ttu-id="b0e10-143">Notez que `<AdministratorUserName>` doit être remplacé par le nom d’utilisateur qui est administrateur sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b0e10-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="b0e10-144">Par exemple, « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="b0e10-144">For example, "Administrator".</span></span>

  9.    <span data-ttu-id="b0e10-145">Copiez le fichier que vous avez modifié et enregistré dans le répertoire Sysprep à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b0e10-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * <span data-ttu-id="b0e10-146">Répondez Oui pour remplacer (vérifiez le chemin entré en l’absence d’invite de remplacement).</span><span class="sxs-lookup"><span data-stu-id="b0e10-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="b0e10-147">Cette commande suppose que votre copie modifiée de Generalize.xml a été copiée dans C:\.</span><span class="sxs-lookup"><span data-stu-id="b0e10-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="b0e10-148">Generalize.XML est désormais mis à jour grâce à la solution de contournement.</span><span class="sxs-lookup"><span data-stu-id="b0e10-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="b0e10-149">Exécutez Sysprep avec l’option generalize activée.</span><span class="sxs-lookup"><span data-stu-id="b0e10-149">Please run Sysprep with the generalize option enabled.</span></span>
