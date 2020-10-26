---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Conditions préalables pour JEA
description: Cet article décrit les prérequis à satisfaire pour pouvoir commencer à utiliser JEA.
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501726"
---
# <a name="prerequisites"></a><span data-ttu-id="832b6-104">Prérequis</span><span class="sxs-lookup"><span data-stu-id="832b6-104">Prerequisites</span></span>

<span data-ttu-id="832b6-105">Just Enough Administration (JEA) est une fonctionnalité incluse dans PowerShell 5.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="832b6-105">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="832b6-106">Cet article décrit les prérequis à satisfaire pour pouvoir commencer à utiliser JEA.</span><span class="sxs-lookup"><span data-stu-id="832b6-106">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>

## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="832b6-107">Vérifier la version de PowerShell installée.</span><span class="sxs-lookup"><span data-stu-id="832b6-107">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="832b6-108">Pour vérifier la version de PowerShell installée sur votre système, consultez la variable `$PSVersionTable` dans une invite de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="832b6-108">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="832b6-109">JEA est disponible avec PowerShell 5.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="832b6-109">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="832b6-110">Pour bénéficier des fonctionnalités complètes, il est recommandé d’installer la dernière version de PowerShell disponible pour votre système.</span><span class="sxs-lookup"><span data-stu-id="832b6-110">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="832b6-111">Le tableau suivant décrit la disponibilité de JEA sur Windows Server :</span><span class="sxs-lookup"><span data-stu-id="832b6-111">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="832b6-112">Système d’exploitation serveur</span><span class="sxs-lookup"><span data-stu-id="832b6-112">Server Operating System</span></span> |                <span data-ttu-id="832b6-113">Disponibilité de JEA</span><span class="sxs-lookup"><span data-stu-id="832b6-113">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="832b6-114">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="832b6-114">Windows Server 2016+</span></span>    | <span data-ttu-id="832b6-115">Préinstallé</span><span class="sxs-lookup"><span data-stu-id="832b6-115">Preinstalled</span></span>                                   |
| <span data-ttu-id="832b6-116">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="832b6-116">Windows Server 2012 R2</span></span>  | <span data-ttu-id="832b6-117">Fonctionnalité complète avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="832b6-117">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="832b6-118">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="832b6-118">Windows Server 2012</span></span>     | <span data-ttu-id="832b6-119">Fonctionnalité complète avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="832b6-119">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="832b6-120">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="832b6-120">Windows Server 2008 R2</span></span>  | <span data-ttu-id="832b6-121">Fonctionnalités réduites<sup>1</sup> avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="832b6-121">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="832b6-122">Vous pouvez également utiliser JEA sur un ordinateur personnel ou professionnel :</span><span class="sxs-lookup"><span data-stu-id="832b6-122">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="832b6-123">Système d’exploitation client</span><span class="sxs-lookup"><span data-stu-id="832b6-123">Client Operating System</span></span> |                   <span data-ttu-id="832b6-124">Disponibilité de JEA</span><span class="sxs-lookup"><span data-stu-id="832b6-124">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="832b6-125">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="832b6-125">Windows 10 1607+</span></span>        | <span data-ttu-id="832b6-126">Préinstallé</span><span class="sxs-lookup"><span data-stu-id="832b6-126">Preinstalled</span></span>                                         |
| <span data-ttu-id="832b6-127">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="832b6-127">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="832b6-128">Préinstallé, avec des fonctionnalités réduites<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="832b6-128">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="832b6-129">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="832b6-129">Windows 10 1507</span></span>         | <span data-ttu-id="832b6-130">Non disponible</span><span class="sxs-lookup"><span data-stu-id="832b6-130">Not available</span></span>                                        |
| <span data-ttu-id="832b6-131">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="832b6-131">Windows 8, 8.1</span></span>          | <span data-ttu-id="832b6-132">Fonctionnalité complète avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="832b6-132">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="832b6-133">Windows 7</span><span class="sxs-lookup"><span data-stu-id="832b6-133">Windows 7</span></span>               | <span data-ttu-id="832b6-134">Fonctionnalités réduites<sup>1</sup> avec WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="832b6-134">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="832b6-135"><sup>1</sup> Vous ne pouvez pas configurer JEA pour utiliser des comptes de service gérés de groupe sur Windows Server 2008 R2 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="832b6-135"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="832b6-136">Les comptes virtuels et les autres fonctionnalités JEA *sont* pris en charge.</span><span class="sxs-lookup"><span data-stu-id="832b6-136">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="832b6-137"><sup>2</sup> Les fonctionnalités JEA suivantes ne sont pas prises en charge sur Windows 10 versions 1511 et 1603 :</span><span class="sxs-lookup"><span data-stu-id="832b6-137"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="832b6-138">Exécution en tant que compte de service géré de groupe</span><span class="sxs-lookup"><span data-stu-id="832b6-138">Running as a group-managed service account</span></span>
  - <span data-ttu-id="832b6-139">Règles d’accès conditionnel dans les configurations de session</span><span class="sxs-lookup"><span data-stu-id="832b6-139">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="832b6-140">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="832b6-140">The user drive</span></span>
  - <span data-ttu-id="832b6-141">Octroi de l’accès aux comptes d’utilisateurs locaux</span><span class="sxs-lookup"><span data-stu-id="832b6-141">Granting access to local user accounts</span></span>

  <span data-ttu-id="832b6-142">Pour obtenir un support pour ces fonctionnalités, vous devez mettre à jour Windows à la version 1607 (Mise à jour anniversaire) ou à une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="832b6-142">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="832b6-143">Installer Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="832b6-143">Install Windows Management Framework</span></span>

<span data-ttu-id="832b6-144">Si vous exécutez une version antérieure de PowerShell, il peut être nécessaire de mettre à jour votre système avec la dernière mise à jour de Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="832b6-144">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="832b6-145">Pour plus d’informations, consultez la [Documentation WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="832b6-145">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="832b6-146">Il est recommandé de tester la compatibilité de votre charge de travail avec WMF avant de mettre à niveau tous vos serveurs.</span><span class="sxs-lookup"><span data-stu-id="832b6-146">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="832b6-147">Les utilisateurs Windows 10 doivent installer les dernières mises à jour de la fonctionnalité pour obtenir la version actuelle de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="832b6-147">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="832b6-148">Activer la communication à distance de PowerShell</span><span class="sxs-lookup"><span data-stu-id="832b6-148">Enable PowerShell Remoting</span></span>

<span data-ttu-id="832b6-149">La communication à distance PowerShell est la base de JEA.</span><span class="sxs-lookup"><span data-stu-id="832b6-149">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="832b6-150">Il est nécessaire de vérifier que la communication à distance PowerShell est activée et correctement sécurisée avant de pouvoir utiliser JEA.</span><span class="sxs-lookup"><span data-stu-id="832b6-150">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="832b6-151">Pour plus d’informations, consultez [Sécurité de WinRM](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="832b6-151">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="832b6-152">La communication à distance PowerShell est activée par défaut dans Windows Server 2012, 2012 R2 et 2016.</span><span class="sxs-lookup"><span data-stu-id="832b6-152">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="832b6-153">Vous pouvez activer la communication à distance PowerShell en exécutant la commande suivante dans une fenêtre PowerShell élevée.</span><span class="sxs-lookup"><span data-stu-id="832b6-153">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="832b6-154">Activer la journalisation des modules PowerShell et des blocs de script (facultatif)</span><span class="sxs-lookup"><span data-stu-id="832b6-154">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="832b6-155">Les étapes suivantes activent la journalisation de toutes les actions PowerShell sur votre système.</span><span class="sxs-lookup"><span data-stu-id="832b6-155">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="832b6-156">La journalisation des modules PowerShell n’est pas obligatoire pour JEA. Cependant, il est recommandé de l’activer afin de garantir que les commandes exécutées par les utilisateurs sont journalisées à un emplacement central.</span><span class="sxs-lookup"><span data-stu-id="832b6-156">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="832b6-157">Vous pouvez configurer la stratégie de journalisation des modules PowerShell à l’aide de la stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="832b6-157">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="832b6-158">Ouvrez l’éditeur d'objets de stratégie de groupe local sur une station de travail ou un objet de stratégie de groupe dans la console de gestion des stratégies de groupe sur un contrôleur de domaine Active Directory</span><span class="sxs-lookup"><span data-stu-id="832b6-158">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="832b6-159">Accédez à **Configuration ordinateur\\Modèles d’administration\\Composants Windows\\Windows PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="832b6-159">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="832b6-160">Double cliquez sur **Activer l’enregistrement des modules** .</span><span class="sxs-lookup"><span data-stu-id="832b6-160">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="832b6-161">Cliquez sur **Activé** .</span><span class="sxs-lookup"><span data-stu-id="832b6-161">Click **Enabled**</span></span>
5. <span data-ttu-id="832b6-162">Dans la section Options, cliquez sur **Afficher** en regard des noms de module.</span><span class="sxs-lookup"><span data-stu-id="832b6-162">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="832b6-163">Tapez `*` dans la fenêtre contextuelle pour journaliser les commandes de tous les modules.</span><span class="sxs-lookup"><span data-stu-id="832b6-163">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="832b6-164">Cliquez sur **OK** pour définir la stratégie.</span><span class="sxs-lookup"><span data-stu-id="832b6-164">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="832b6-165">Double-cliquez sur **Activer la journalisation de blocs de scripts PowerShell**</span><span class="sxs-lookup"><span data-stu-id="832b6-165">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="832b6-166">Cliquez sur **Activé** .</span><span class="sxs-lookup"><span data-stu-id="832b6-166">Click **Enabled**</span></span>
10. <span data-ttu-id="832b6-167">Cliquez sur **OK** pour définir la stratégie.</span><span class="sxs-lookup"><span data-stu-id="832b6-167">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="832b6-168">(Sur les ordinateurs joints à un domaine uniquement) Exécutez `gpupdate` ou attendez que la stratégie de groupe traite la stratégie mise à jour et applique les paramètres.</span><span class="sxs-lookup"><span data-stu-id="832b6-168">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="832b6-169">Vous pouvez également activer la transcription PowerShell à l’échelle du système par le biais de la stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="832b6-169">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="832b6-170">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="832b6-170">Next steps</span></span>

[<span data-ttu-id="832b6-171">Créer un fichier de fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="832b6-171">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="832b6-172">Créer un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="832b6-172">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="832b6-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="832b6-173">See also</span></span>

[<span data-ttu-id="832b6-174">Sécurité de WinRM</span><span class="sxs-lookup"><span data-stu-id="832b6-174">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="832b6-175">PowerShell ♥ the Blue Team</span><span class="sxs-lookup"><span data-stu-id="832b6-175">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
