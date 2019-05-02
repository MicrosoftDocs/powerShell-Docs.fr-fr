---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: Désinstaller Accès Web Windows PowerShell
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058135"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="95ca0-103">désinstaller Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95ca0-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="95ca0-104">Mise à jour : 24 juin 2013</span><span class="sxs-lookup"><span data-stu-id="95ca0-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="95ca0-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="95ca0-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="95ca0-106">Les étapes décrites dans cette rubrique suppriment le site web Accès Web Windows PowerShell et l’application correspondante du serveur de passerelle où elle est installée.</span><span class="sxs-lookup"><span data-stu-id="95ca0-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="95ca0-107">Notifier les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="95ca0-107">Notify users</span></span>

<span data-ttu-id="95ca0-108">Avant de commencer, informez les utilisateurs de la console Web de la suppression du site web.</span><span class="sxs-lookup"><span data-stu-id="95ca0-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="95ca0-109">La désinstallation d’Accès Web Windows PowerShell ne désinstalle pas IIS ni d’autres fonctionnalités automatiquement installées, car Accès Web Windows PowerShell en a besoin pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="95ca0-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="95ca0-110">Le processus de désinstallation laisse les fonctionnalités installées dont dépendait Accès Web Windows PowerShell ; vous pouvez désinstaller ces fonctionnalités séparément si besoin.</span><span class="sxs-lookup"><span data-stu-id="95ca0-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="95ca0-111">Désinstallation (rapide) recommandée</span><span class="sxs-lookup"><span data-stu-id="95ca0-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="95ca0-112">Les procédures de cette section vous permettent de désinstaller :</span><span class="sxs-lookup"><span data-stu-id="95ca0-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="95ca0-113">l’application Accès Web Windows PowerShell et</span><span class="sxs-lookup"><span data-stu-id="95ca0-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="95ca0-114">la fonctionnalité Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95ca0-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="95ca0-115">à l’aide d’applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95ca0-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="95ca0-116">Étape 1 : Supprimer l’application web à l’aide d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="95ca0-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="95ca0-117">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95ca0-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="95ca0-118">Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="95ca0-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="95ca0-119">Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="95ca0-120">Tapez `Uninstall-PswaWebApplication` puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="95ca0-121">Si vous avez défini un nom de site web personnalisé, ajoutez le paramètre `-WebsiteName` à votre commande et spécifiez le nom du site web.</span><span class="sxs-lookup"><span data-stu-id="95ca0-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="95ca0-122">Si vous avez utilisé une application web personnalisée (et non pas l’application par défaut, **pswa**), ajoutez le paramètre `-WebApplicationName` à votre commande et spécifiez le nom de l’application web.</span><span class="sxs-lookup"><span data-stu-id="95ca0-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="95ca0-123">Si vous utilisez un certificat de test, ajoutez le paramètre `DeleteTestCertificate` à l’applet de commande, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="95ca0-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="95ca0-124">Étape 2 : Désinstaller Accès Web Windows PowerShell à l’aide d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="95ca0-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="95ca0-125">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="95ca0-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="95ca0-126">Si une session est déjà ouverte, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="95ca0-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="95ca0-127">Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="95ca0-128">Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="95ca0-129">Tapez ce qui suit, puis appuyez sur **Entrée**, où *computer_name* représente le nom de l’ordinateur distant sur lequel vous souhaitez installer Accès Web Windows PowerShell, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="95ca0-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="95ca0-130">Le paramètre `-Restart` redémarre automatiquement les serveurs de destination si la suppression l’exige.</span><span class="sxs-lookup"><span data-stu-id="95ca0-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="95ca0-131">Pour installer des rôles et fonctionnalités sur un disque dur virtuel hors connexion, vous devez ajouter les paramètres `-ComputerName` et `-VHD` .</span><span class="sxs-lookup"><span data-stu-id="95ca0-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="95ca0-132">Le paramètre `-ComputerName` contient le nom du serveur sur lequel monter le disque dur virtuel tandis que le paramètre `-VHD` contient le chemin d’accès au fichier VHD sur le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="95ca0-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="95ca0-133">Une fois l’installation terminée, vérifiez que vous avez bien supprimé Accès Web Windows PowerShell. Pour cela, ouvrez la page **Tous les serveurs** dans le Gestionnaire de serveur, sélectionnez un serveur sur lequel vous avez installé la fonctionnalité, puis examinez la vignette **Rôles et fonctionnalités** dans la page du serveur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="95ca0-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="95ca0-134">Vous pouvez également exécuter l’applet de commande `Get-WindowsFeature` ciblée sur le serveur sélectionné (Get-WindowsFeature -ComputerName &lt;*nom_ordinateur*&gt;) pour afficher la liste des rôles et des fonctionnalités installés sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="95ca0-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="95ca0-135">Désinstallation personnalisée</span><span class="sxs-lookup"><span data-stu-id="95ca0-135">Custom uninstallation</span></span>

<span data-ttu-id="95ca0-136">Les procédures de cette section vous permettent de désinstaller l’application web Accès Web Windows PowerShell et la fonctionnalité Accès Web Windows PowerShell en utilisant l’Assistant Suppression de rôles et de fonctionnalités dans le Gestionnaire de serveur et la console du Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="95ca0-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="95ca0-137">Étape 1 : Supprimer l’application web à l’aide du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="95ca0-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="95ca0-138">Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="95ca0-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="95ca0-139">Si elle est déjà ouverte, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="95ca0-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="95ca0-140">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="95ca0-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="95ca0-141">Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="95ca0-142">Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="95ca0-143">Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="95ca0-144">Dans le volet de l’arborescence du Gestionnaire des services Internet, sélectionnez le site web qui exécute l’application web Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95ca0-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="95ca0-145">Dans le volet **Actions**, sous **Gérer le site web**, cliquez sur **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="95ca0-146">Dans le volet de l’arborescence, cliquez avec le bouton droit sur l’application web dans le site web qui exécute l’application web Accès Web Windows PowerShell, puis cliquez sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="95ca0-147">Dans le volet de l’arborescence, sélectionnez **Pools d’applications**, sélectionnez le dossier du pool d’applications Accès Web Windows PowerShell, cliquez sur **Arrêter** dans le volet **Actions**, puis cliquez sur **Supprimer** dans le volet de contenu.</span><span class="sxs-lookup"><span data-stu-id="95ca0-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="95ca0-148">Fermez le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="95ca0-148">Close IIS Manager.</span></span>

> <span data-ttu-id="95ca0-149">![Avertissement](images/SecurityNote.jpeg)**Remarque** :</span><span class="sxs-lookup"><span data-stu-id="95ca0-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="95ca0-150">Le certificat n’est pas supprimé durant la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="95ca0-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="95ca0-151">Si vous avez créé un certificat auto-signé ou utilisé un certificat de test et que vous souhaitez le supprimer, supprimez le certificat dans le Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="95ca0-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="95ca0-152">Étape 2 : Désinstaller Accès Web Windows PowerShell à l’aide de l’Assistant Suppression de rôles et de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="95ca0-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="95ca0-153">Si le Gestionnaire de serveur est déjà ouvert, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="95ca0-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="95ca0-154">S’il n’est pas déjà ouvert, ouvrez-le en effectuant l’une des opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="95ca0-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="95ca0-155">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="95ca0-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="95ca0-156">Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="95ca0-157">Dans le menu **Gérer**, cliquez sur **Supprimer des rôles et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="95ca0-158">Dans la page **Sélectionner le serveur de destination**, sélectionnez le serveur ou le disque dur virtuel hors connexion sur lequel vous souhaitez supprimer la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="95ca0-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="95ca0-159">Pour sélectionner un disque dur virtuel hors connexion, choisissez d’abord le serveur sur lequel monter le disque dur virtuel, puis sélectionnez le fichier VHD.</span><span class="sxs-lookup"><span data-stu-id="95ca0-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="95ca0-160">Une fois que vous avez sélectionné le serveur de destination, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="95ca0-161">Cliquez de nouveau sur **Suivant** pour passer à la page **Supprimer des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="95ca0-162">Décochez la case **Accès Web Windows PowerShell**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="95ca0-163">Dans la page **Confirmer les sélections pour la suppression**, cliquez sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="95ca0-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="95ca0-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95ca0-164">See Also</span></span>

- [<span data-ttu-id="95ca0-165">Installer et utiliser Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95ca0-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="95ca0-166">Aide du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="95ca0-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)