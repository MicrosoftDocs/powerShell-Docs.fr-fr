---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Conditions préalables pour JEA
ms.openlocfilehash: 92a74d89a0e982e9f45e69d92b261756de33c038
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="prerequisites"></a><span data-ttu-id="20abc-103">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="20abc-103">Prerequisites</span></span>

> <span data-ttu-id="20abc-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="20abc-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="20abc-105">Just Enough Administration est une fonctionnalité incluse dans Windows PowerShell 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="20abc-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="20abc-106">Cette rubrique décrit les conditions préalables à satisfaire pour pouvoir commencer à utiliser JEA.</span><span class="sxs-lookup"><span data-stu-id="20abc-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="20abc-107">Installer JEA</span><span class="sxs-lookup"><span data-stu-id="20abc-107">Install JEA</span></span>

<span data-ttu-id="20abc-108">JEA est disponible avec Windows PowerShell 5.0 et versions ultérieures. Mais, pour les fonctionnalités complètes, il est recommandé d’installer la dernière version de PowerShell disponible pour votre système.</span><span class="sxs-lookup"><span data-stu-id="20abc-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="20abc-109">Le tableau suivant décrit la disponibilité de JEA sur Windows Server :</span><span class="sxs-lookup"><span data-stu-id="20abc-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="20abc-110">Système d’exploitation serveur</span><span class="sxs-lookup"><span data-stu-id="20abc-110">Server Operating System</span></span>   | <span data-ttu-id="20abc-111">Disponibilité de JEA</span><span class="sxs-lookup"><span data-stu-id="20abc-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="20abc-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="20abc-112">Windows Server 2016</span></span>       | <span data-ttu-id="20abc-113">Préinstallé</span><span class="sxs-lookup"><span data-stu-id="20abc-113">Preinstalled</span></span>
<span data-ttu-id="20abc-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="20abc-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="20abc-115">Fonctionnalité complète avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="20abc-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="20abc-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="20abc-116">Windows Server 2012</span></span>       | <span data-ttu-id="20abc-117">Fonctionnalité complète avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="20abc-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="20abc-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="20abc-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="20abc-119">Fonctionnalités réduites<sup>1</sup> avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="20abc-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="20abc-120">Vous pouvez également utiliser JEA sur un ordinateur personnel ou professionnel :</span><span class="sxs-lookup"><span data-stu-id="20abc-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="20abc-121">Système d’exploitation client</span><span class="sxs-lookup"><span data-stu-id="20abc-121">Client Operating System</span></span>   | <span data-ttu-id="20abc-122">Disponibilité de JEA</span><span class="sxs-lookup"><span data-stu-id="20abc-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="20abc-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="20abc-123">Windows 10 1607+</span></span>          | <span data-ttu-id="20abc-124">Préinstallé</span><span class="sxs-lookup"><span data-stu-id="20abc-124">Preinstalled</span></span>
<span data-ttu-id="20abc-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="20abc-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="20abc-126">Préinstallé, avec des fonctionnalités réduites<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="20abc-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="20abc-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="20abc-127">Windows 10 1507</span></span>           | <span data-ttu-id="20abc-128">Non disponible</span><span class="sxs-lookup"><span data-stu-id="20abc-128">Not available</span></span>
<span data-ttu-id="20abc-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="20abc-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="20abc-130">Fonctionnalité complète avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="20abc-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="20abc-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="20abc-131">Windows 7</span></span>                 | <span data-ttu-id="20abc-132">Fonctionnalités réduites<sup>1</sup> avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="20abc-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="20abc-133"><sup>1</sup> Vous ne pouvez pas configurer JEA pour utiliser des comptes de service géré de groupe sur Windows Server 2008 R2 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="20abc-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="20abc-134">Les comptes virtuels et les autres fonctionnalités JEA *sont* pris en charge.</span><span class="sxs-lookup"><span data-stu-id="20abc-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="20abc-135"><sup>2</sup> Les versions Windows 10 1511 et 1603 ne prennent pas en charge les fonctionnalités JEA suivantes : exécution en tant que compte de service administré de groupe, les règles d’accès conditionnel dans des configurations de session, le lecteur utilisateur et l’octroi de l’accès à des comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="20abc-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="20abc-136">Pour obtenir un support pour ces fonctionnalités, vous devez mettre à jour Windows à la version 1607 (Mise à jour anniversaire) ou à une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="20abc-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="20abc-137">Vérifier la version de PowerShell installée.</span><span class="sxs-lookup"><span data-stu-id="20abc-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="20abc-138">Pour vérifier la version de PowerShell installée sur votre système, consultez la variable `$PSVersionTable` dans une invite de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20abc-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="20abc-139">Vous êtes prêt à utiliser JEA si la version *principale* est supérieure ou égale à **5**.</span><span class="sxs-lookup"><span data-stu-id="20abc-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="20abc-140">Pour optimiser l’expérience et accéder à toutes les fonctionnalités les plus récentes, il est recommandé de mettre à niveau vers la version de PowerShell **5.1** lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="20abc-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="20abc-141">Installer Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="20abc-141">Install Windows Management Framework</span></span>

<span data-ttu-id="20abc-142">Si vous exécutez une version antérieure de PowerShell, vous devez mettre à jour votre système avec la dernière mise à jour de Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="20abc-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="20abc-143">Les packages de mise à jour et un lien vers les dernières notes de publication de WMF sont disponibles dans le [Centre de téléchargement](https://aka.ms/WMF5).</span><span class="sxs-lookup"><span data-stu-id="20abc-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="20abc-144">Il est fortement recommandé de tester la compatibilité de votre charge de travail avec WMF avant de mettre à niveau tous vos serveurs.</span><span class="sxs-lookup"><span data-stu-id="20abc-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="20abc-145">Les utilisateurs Windows 10 doivent installer les dernières mises à jour de la fonctionnalité pour obtenir la version actuelle de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20abc-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="20abc-146">Activer la communication à distance de PowerShell</span><span class="sxs-lookup"><span data-stu-id="20abc-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="20abc-147">La communication à distance PowerShell est la base de JEA.</span><span class="sxs-lookup"><span data-stu-id="20abc-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="20abc-148">Il est donc important d’assurer que la communication à distance PowerShell est activée et [correctement sécurisée](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) sur votre système avant de pouvoir utiliser JEA.</span><span class="sxs-lookup"><span data-stu-id="20abc-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="20abc-149">La communication à distance PowerShell est activée par défaut dans Windows Server 2012, 2012 R2 et 2016.</span><span class="sxs-lookup"><span data-stu-id="20abc-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="20abc-150">Vous pouvez activer la communication à distance PowerShell en exécutant la commande suivante dans une fenêtre PowerShell élevée.</span><span class="sxs-lookup"><span data-stu-id="20abc-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="20abc-151">Activer la journalisation des modules PowerShell et des blocs de script (facultatif)</span><span class="sxs-lookup"><span data-stu-id="20abc-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="20abc-152">Les étapes suivantes activent la journalisation de toutes les actions PowerShell sur votre système.</span><span class="sxs-lookup"><span data-stu-id="20abc-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="20abc-153">La journalisation des modules PowerShell n’est pas obligatoire pour JEA. Cependant, il est fortement recommandé de l’activer afin de vous assurer que les commandes utilisées par les utilisateurs sont journalisées dans un emplacement central.</span><span class="sxs-lookup"><span data-stu-id="20abc-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="20abc-154">Vous pouvez configurer la stratégie de journalisation des modules PowerShell à l’aide de la stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="20abc-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="20abc-155">Ouvrez l’éditeur d'objets de stratégie de groupe local sur une station de travail ou un objet de stratégie de groupe dans la console de gestion des stratégies de groupe sur un contrôleur de domaine Active Directory</span><span class="sxs-lookup"><span data-stu-id="20abc-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="20abc-156">Accédez à **Configuration ordinateur\\Modèles d’administration\\Composants Windows\\Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="20abc-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="20abc-157">Double cliquez sur **Activer l’enregistrement des modules**.</span><span class="sxs-lookup"><span data-stu-id="20abc-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="20abc-158">Cliquez sur **Activé**.</span><span class="sxs-lookup"><span data-stu-id="20abc-158">Click **Enabled**</span></span>
5. <span data-ttu-id="20abc-159">Dans la section Options, cliquez sur **Afficher** en regard des noms de module.</span><span class="sxs-lookup"><span data-stu-id="20abc-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="20abc-160">Tapez « **\*** » dans la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="20abc-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="20abc-161">Cette commande ordonne à PowerShell de journaliser les commandes de tous les modules.</span><span class="sxs-lookup"><span data-stu-id="20abc-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="20abc-162">Cliquez sur **OK** pour définir la stratégie.</span><span class="sxs-lookup"><span data-stu-id="20abc-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="20abc-163">Double-cliquez sur **Activer la journalisation de blocs de scripts PowerShell**</span><span class="sxs-lookup"><span data-stu-id="20abc-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="20abc-164">Cliquez sur **Activé**.</span><span class="sxs-lookup"><span data-stu-id="20abc-164">Click **Enabled**</span></span>
10. <span data-ttu-id="20abc-165">Cliquez sur **OK** pour définir la stratégie.</span><span class="sxs-lookup"><span data-stu-id="20abc-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="20abc-166">(sur les ordinateurs joints à un domaine uniquement). Exécutez **gpupdate** ou attendez que la stratégie de groupe traite la stratégie mise à jour et applique les paramètres.</span><span class="sxs-lookup"><span data-stu-id="20abc-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="20abc-167">Vous pouvez également activer la transcription PowerShell à l’échelle du système par le biais de la stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="20abc-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="20abc-168">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="20abc-168">Next steps</span></span>

- [<span data-ttu-id="20abc-169">Créer un fichier de fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="20abc-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="20abc-170">Créer un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="20abc-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="20abc-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20abc-171">See also</span></span>

- [<span data-ttu-id="20abc-172">Informations supplémentaires sur la sécurité de la communication à distance PowerShell et WinRM</span><span class="sxs-lookup"><span data-stu-id="20abc-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="20abc-173">*PowerShell ♥ the Blue Team*, billet de blog sur la sécurité</span><span class="sxs-lookup"><span data-stu-id="20abc-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)