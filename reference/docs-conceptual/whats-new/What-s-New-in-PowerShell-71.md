---
title: Nouveautés de PowerShell 7.1
description: Nouvelles fonctionnalités et modifications de PowerShell 7.1
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577205"
---
# <a name="whats-new-in-powershell-71"></a><span data-ttu-id="5d156-103">Nouveautés de PowerShell 7.1</span><span class="sxs-lookup"><span data-stu-id="5d156-103">What's New in PowerShell 7.1</span></span>

<span data-ttu-id="5d156-104">Le 11 novembre 2020, nous avons [annoncé](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) la disponibilité générale de PowerShell 7.1.</span><span class="sxs-lookup"><span data-stu-id="5d156-104">On November 11, 2020 we [announced](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) the general availability of PowerShell 7.1.</span></span> <span data-ttu-id="5d156-105">En s'appuyant sur les bases établies dans PowerShell 7.0, nos efforts se sont concentrés sur les questions soulevées par la communauté et comprennent un certain nombre d'améliorations et de corrections.</span><span class="sxs-lookup"><span data-stu-id="5d156-105">Building on the foundation established in PowerShell 7.0, our efforts focused on community issues and include a number of improvements and fixes.</span></span> <span data-ttu-id="5d156-106">Nous nous engageons à faire en sorte que PowerShell reste une plateforme stable et performante.</span><span class="sxs-lookup"><span data-stu-id="5d156-106">We are committed to ensuring that PowerShell remains a stable and performant platform.</span></span>

<span data-ttu-id="5d156-107">PowerShell 7.1 comprend les fonctionnalités, les mises à jour et les changements cassants suivants.</span><span class="sxs-lookup"><span data-stu-id="5d156-107">PowerShell 7.1 includes the following features, updates, and breaking changes.</span></span>

- <span data-ttu-id="5d156-108">PSReadLine 2.1.0, qui comprend IntelliSense prédictif</span><span class="sxs-lookup"><span data-stu-id="5d156-108">PSReadLine 2.1.0, which includes Predictive IntelliSense</span></span>
- <span data-ttu-id="5d156-109">Publication de PowerShell 7.1 sur le Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="5d156-109">PowerShell 7.1 has been published to the Microsoft Store</span></span>
- <span data-ttu-id="5d156-110">Mise à jour des packages d’installation pour les nouvelles versions de système d’exploitation avec prise en charge d’ARM64</span><span class="sxs-lookup"><span data-stu-id="5d156-110">Installer packages updated for new OS versions with support for ARM64</span></span>
- <span data-ttu-id="5d156-111">Officialisation de 4 nouvelles fonctionnalités expérimentales et 2 fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="5d156-111">4 new experimental features and 2 experimental features promoted to mainstream</span></span>
- <span data-ttu-id="5d156-112">Divers changements cassants pour améliorer l’utilisabilité</span><span class="sxs-lookup"><span data-stu-id="5d156-112">Several breaking changes to improve usability</span></span>

<span data-ttu-id="5d156-113">Pour obtenir la liste complète des changements, consultez [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) dans le dépôt GitHub.</span><span class="sxs-lookup"><span data-stu-id="5d156-113">For a complete list of changes, see the [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in the GitHub repository.</span></span>

## <a name="psreadline-210"></a><span data-ttu-id="5d156-114">PSReadline 2.1.0</span><span class="sxs-lookup"><span data-stu-id="5d156-114">PSReadLine 2.1.0</span></span>

<span data-ttu-id="5d156-115">PowerShell 7.1 inclut également PSReadLine 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="5d156-115">PowerShell 7.1 also include PSReadLine 2.1.0.</span></span> <span data-ttu-id="5d156-116">Cette version comprend IntelliSense prédictif.</span><span class="sxs-lookup"><span data-stu-id="5d156-116">This version includes Predictive IntelliSense.</span></span> <span data-ttu-id="5d156-117">Pour plus d’informations sur la fonctionnalité IntelliSense prédictive, consultez l’[annonce](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d156-117">For more information about the Predictive IntelliSense feature, see the [announcement](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in the PowerShell blog.</span></span>

## <a name="microsoft-store-installer-package"></a><span data-ttu-id="5d156-118">Package d’installation Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="5d156-118">Microsoft Store installer package</span></span>

<span data-ttu-id="5d156-119">PowerShell 7.1 a été publié sur le Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="5d156-119">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="5d156-120">Vous trouverez la version PowerShell sur le site Web du [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) ou dans l’application Store de Windows.</span><span class="sxs-lookup"><span data-stu-id="5d156-120">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="5d156-121">Avantages du package Microsoft Store :</span><span class="sxs-lookup"><span data-stu-id="5d156-121">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="5d156-122">Mises à jour automatiques intégrées à Windows 10</span><span class="sxs-lookup"><span data-stu-id="5d156-122">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="5d156-123">S’intègre à d’autres mécanismes de distribution de logiciels comme Intune et SCCM</span><span class="sxs-lookup"><span data-stu-id="5d156-123">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

> [!NOTE]
> <span data-ttu-id="5d156-124">Les paramètres de configuration au niveau du système, stockés dans `$PSHOME`, ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="5d156-124">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="5d156-125">Cela comprend la configuration WSMAN.</span><span class="sxs-lookup"><span data-stu-id="5d156-125">This includes the WSMAN configuration.</span></span> <span data-ttu-id="5d156-126">Cette stratégie empêche les sessions à distance de se connecter aux installations basées sur le magasin de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d156-126">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="5d156-127">Les configurations au niveau de l’utilisateur et l’accès à distance SSH sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5d156-127">User-level configurations and SSH remoting are supported.</span></span>

## <a name="other-installers"></a><span data-ttu-id="5d156-128">Autres programmes d’installation</span><span class="sxs-lookup"><span data-stu-id="5d156-128">Other installers</span></span>

<span data-ttu-id="5d156-129">Pour plus d’informations à jour sur les systèmes d’exploitation pris en charge et le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="5d156-129">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

<span data-ttu-id="5d156-130">Consultez les instructions d’installation pour votre système d’exploitation par défaut :</span><span class="sxs-lookup"><span data-stu-id="5d156-130">Check the installation instructions for your preferred operating system:</span></span>

- [<span data-ttu-id="5d156-131">Windows</span><span class="sxs-lookup"><span data-stu-id="5d156-131">Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows)
- [<span data-ttu-id="5d156-132">macOS</span><span class="sxs-lookup"><span data-stu-id="5d156-132">macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos)
- [<span data-ttu-id="5d156-133">Linux</span><span class="sxs-lookup"><span data-stu-id="5d156-133">Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux)

<span data-ttu-id="5d156-134">En outre, PowerShell 7.1 prend en charge les versions ARM32 et ARM64 de Debian, Ubuntu et ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="5d156-134">Additionally, PowerShell 7.1 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="5d156-135">Bien qu’ils ne soit pas officiellement pris en charge, la communauté a également fourni des packages pour [Arch](https://aur.archlinux.org/packages/powershell/) et Kali Linux.</span><span class="sxs-lookup"><span data-stu-id="5d156-135">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="5d156-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine et Arm ne prennent actuellement pas en charge la communication à distance WinRM.</span><span class="sxs-lookup"><span data-stu-id="5d156-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine and Arm currently do not support WinRM remoting.</span></span> <span data-ttu-id="5d156-137">Pour plus d’informations sur la configuration de la communication à distance basée sur SSH, consultez [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="5d156-137">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="experimental-features"></a><span data-ttu-id="5d156-138">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="5d156-138">Experimental Features</span></span>

<span data-ttu-id="5d156-139">Pour plus d’informations sur les fonctionnalités expérimentales, consultez [Utilisation des fonctionnalités expérimentales](../learn/experimental-features.md).</span><span class="sxs-lookup"><span data-stu-id="5d156-139">For more information about the Experimental Features, see [Using Experimental Features](../learn/experimental-features.md).</span></span>

<span data-ttu-id="5d156-140">Les fonctionnalités expérimentales suivantes sont maintenant devenues des fonctionnalités standard dans cette version :</span><span class="sxs-lookup"><span data-stu-id="5d156-140">The following experimental features are now mainstream features in this release:</span></span>

- [<span data-ttu-id="5d156-141">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="5d156-141">PSNullConditionalOperators</span></span>](../learn/experimental-features.md#psnullconditionaloperators)
- [<span data-ttu-id="5d156-142">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="5d156-142">PSUnixFileStat</span></span>](../learn/experimental-features.md#psunixfilestat)

<span data-ttu-id="5d156-143">Les fonctionnalités expérimentales suivantes ont été ajoutées dans cette version :</span><span class="sxs-lookup"><span data-stu-id="5d156-143">The following experimental features were added in this release:</span></span>

- [<span data-ttu-id="5d156-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="5d156-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - <span data-ttu-id="5d156-145">PowerShell 7.1 étend cette fonctionnalité expérimentale pour ajouter le paramètre **Runspace** à toutes les applets de commande `*-PSBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="5d156-145">PowerShell 7.1 extends this experimental feature to add the **Runspace** parameter to all `*-PSBreakpoint` cmdlets.</span></span> <span data-ttu-id="5d156-146">Le paramètre **Runspace** spécifie un objet **Runspace** pour interagir avec des points d’arrêt dans l’instance d’exécution spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5d156-146">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

- <span data-ttu-id="5d156-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - Cette fonctionnalité vous permet de passer des chemins de fournisseur PowerShell à des commandes natives qui ne prennent pas en charge la syntaxe de chemin de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d156-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - This feature allows you to pass PowerShell provider paths to native commands that don't support PowerShell path syntax.</span></span>

- <span data-ttu-id="5d156-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - Lorsque l’opérande gauche dans une instruction opérateur `-replace` n’est pas une chaîne, cet opérande est converti en chaîne.</span><span class="sxs-lookup"><span data-stu-id="5d156-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span> <span data-ttu-id="5d156-149">Lorsque la fonctionnalité est activée, la conversion n’utilise pas les paramètres de culture pour la conversion de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5d156-149">With the feature enabled, the conversion does not use Culture settings for string conversion.</span></span>

- <span data-ttu-id="5d156-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) permet de prendre en charge les futurs plug-ins IntelliSense prédictif.</span><span class="sxs-lookup"><span data-stu-id="5d156-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) lays the groundwork to support future Predictive IntelliSense plug-ins.</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="5d156-151">Dernières modifications et améliorations</span><span class="sxs-lookup"><span data-stu-id="5d156-151">Breaking Changes and Improvements</span></span>

- <span data-ttu-id="5d156-152">Correction de `$?` pour ne pas être `$false` lorsque la commande native écrit dans `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span><span class="sxs-lookup"><span data-stu-id="5d156-152">Fix `$?` to not be `$false` when native command writes to `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span></span>

  <span data-ttu-id="5d156-153">Il est courant que les commandes natives écrivent dans `stderr` sans avoir à indiquer un échec.</span><span class="sxs-lookup"><span data-stu-id="5d156-153">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="5d156-154">Avec ce changement, `$?` a la valeur `$false` uniquement lorsque la commande native a également un code de sortie différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="5d156-154">With this change `$?` is set to `$false` only when the native command also has a non-zero exit code.</span></span> <span data-ttu-id="5d156-155">Ce changement n’est pas lié à la fonctionnalité expérimentale `PSNotApplyErrorActionToStderr`.</span><span class="sxs-lookup"><span data-stu-id="5d156-155">This change is unrelated to the experimental feature `PSNotApplyErrorActionToStderr`.</span></span>

- <span data-ttu-id="5d156-156">Configuration de `$ErrorActionPreference` pour ne pas affecter la sortie `stderr` des commandes natives ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span><span class="sxs-lookup"><span data-stu-id="5d156-156">Make `$ErrorActionPreference` not affect `stderr` output of native commands ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span></span>

  <span data-ttu-id="5d156-157">Il est courant que les commandes natives écrivent dans `stderr` sans avoir à indiquer un échec.</span><span class="sxs-lookup"><span data-stu-id="5d156-157">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="5d156-158">Avec ce changement, la sortie `stderr` est toujours capturée dans les objets **ErrorRecord**, mais le runtime n’applique plus `$ErrorActionPreference` si le **ErrorRecord** provient d’une commande native.</span><span class="sxs-lookup"><span data-stu-id="5d156-158">With this change, `stderr` output is still captured in **ErrorRecord** objects, but the runtime no longer applies `$ErrorActionPreference` if the **ErrorRecord** comes from a native command.</span></span>

- <span data-ttu-id="5d156-159">Renommage de `-FromUnixTime` en `-UnixTimeSeconds` sur `Get-Date` pour autoriser l’entrée de temps UNIX ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Merci @aetos382 !)</span><span class="sxs-lookup"><span data-stu-id="5d156-159">Rename `-FromUnixTime` to `-UnixTimeSeconds` on `Get-Date` to allow Unix time input ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Thanks @aetos382!)</span></span>

  <span data-ttu-id="5d156-160">Le paramètre `-FromUnixTime` a été ajouté pendant 7.1-preview.2.</span><span class="sxs-lookup"><span data-stu-id="5d156-160">The `-FromUnixTime` parameter was added during 7.1-preview.2.</span></span> <span data-ttu-id="5d156-161">Le paramètre a été renommé pour mieux correspondre au type de données.</span><span class="sxs-lookup"><span data-stu-id="5d156-161">The parameter was renamed to better match the data type.</span></span> <span data-ttu-id="5d156-162">Ce paramètre prend une valeur entière qui est représentée en secondes depuis le 1er janvier 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="5d156-162">This parameter takes an integer value that represents in seconds since January 1, 1970, 0:00:00.</span></span>

  <span data-ttu-id="5d156-163">Cet exemple convertit une heure UNIX (représentée par le nombre de secondes depuis le 01-01-1970 0:00:00) en DateHeure.</span><span class="sxs-lookup"><span data-stu-id="5d156-163">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- <span data-ttu-id="5d156-164">Autoriser le paramètre nommé explicitement spécifié à remplacer le même paramètre dans la projection de la table de hachage (#13162)</span><span class="sxs-lookup"><span data-stu-id="5d156-164">Allow explicitly specified named parameter to supersede the same one from hashtable splatting (#13162)</span></span>

  <span data-ttu-id="5d156-165">Avec ce changement, les paramètres nommés de la projection sont déplacés à la fin de la liste de paramètres afin qu’ils soient liés une fois que tous les paramètres nommés explicitement spécifiés sont liés.</span><span class="sxs-lookup"><span data-stu-id="5d156-165">With this change, the named parameters from splatting are moved to the end of the parameter list so that they are bound after all explicitly specified named parameters are bound.</span></span> <span data-ttu-id="5d156-166">La liaison de paramètre pour les fonctions simples ne génère pas d’erreur quand un paramètre nommé spécifié est introuvable.</span><span class="sxs-lookup"><span data-stu-id="5d156-166">Parameter binding for simple functions doesn't throw an error when a specified named parameter cannot be found.</span></span> <span data-ttu-id="5d156-167">Les paramètres nommés inconnus sont liés au paramètre `$args` de la fonction simple.</span><span class="sxs-lookup"><span data-stu-id="5d156-167">Unknown named parameters are bound to the `$args` parameter of the simple function.</span></span> <span data-ttu-id="5d156-168">Le déplacement de la projection à la fin de la liste d’arguments change l’ordre dans lequel les paramètres apparaissent dans `$args`.</span><span class="sxs-lookup"><span data-stu-id="5d156-168">Moving splatting to the end of the argument list changes the order the parameters appears in `$args`.</span></span>

  <span data-ttu-id="5d156-169">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5d156-169">For example:</span></span>

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  <span data-ttu-id="5d156-170">Dans le comportement précédent, **MyPath** n’est pas lié à `-Path` , car il s’agit du troisième argument dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5d156-170">In the previous behavior, **MyPath** is not bound to `-Path` because it's the third argument in the argument list.</span></span> <span data-ttu-id="5d156-171"># # Donc, il finit par être placé dans « $args » avec `Blah = "World"`</span><span class="sxs-lookup"><span data-stu-id="5d156-171">## So it ends up being stuffed into '$args' along with `Blah = "World"`</span></span>

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  <span data-ttu-id="5d156-172">Avec ce changement, les arguments de `@hash` sont déplacés à la fin de la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5d156-172">With this change, the arguments from `@hash` are moved to the end of the argument list.</span></span> <span data-ttu-id="5d156-173">**MyPath** devient le premier argument de la liste, donc il est lié à `-Path`.</span><span class="sxs-lookup"><span data-stu-id="5d156-173">**MyPath** becomes the first argument in the list, so it is bound to `-Path`.</span></span>

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- <span data-ttu-id="5d156-174">Rendre le paramètre de commutateur `-Qualifier` non positionnel pour `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Merci @yecril71pl !)</span><span class="sxs-lookup"><span data-stu-id="5d156-174">Make the switch parameter `-Qualifier` not positional for `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Thanks @yecril71pl!)</span></span>

- <span data-ttu-id="5d156-175">Correction du répertoire de travail comme chemin littéral pour `Start-Process` lorsqu’il n’est pas spécifié ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Merci @NoMoreFood !)</span><span class="sxs-lookup"><span data-stu-id="5d156-175">Resolve the working directory as literal path for `Start-Process` when it's not specified ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Thanks @NoMoreFood!)</span></span>

- <span data-ttu-id="5d156-176">Modification du paramètre `-OutFile` dans les applets de commande web pour qu’il fonctionne comme `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5d156-176">Make `-OutFile` parameter in web cmdlets to work like `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="5d156-177">Correction de la liaison de paramètre de chaîne pour les littéraux numériques `BigInteger` ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5d156-177">Fix string parameter binding for `BigInteger` numeric literals ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Thanks @vexx32!)</span></span>

- <span data-ttu-id="5d156-178">Sur Windows, `Start-Process` crée un environnement de processus avec toutes les variables d’environnement à partir de la session active, et `-UseNewEnvironment` crée un nouvel environnement de processus par défaut ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5d156-178">On Windows, `Start-Process` creates a process environment with all the environment variables from current session, using `-UseNewEnvironment` creates a new default process environment ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="5d156-179">Résultat non wrappé dans `PSObject` lors de la conversion de `ScriptBlock` en délégué ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span><span class="sxs-lookup"><span data-stu-id="5d156-179">Do not wrap return result in `PSObject` when converting a `ScriptBlock` to a delegate ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span></span>

  <span data-ttu-id="5d156-180">Quand un `ScriptBlock` est converti en type délégué à utiliser dans un contexte C#, le wrapping du résultat dans un `PSObject` pose des problèmes inutiles :</span><span class="sxs-lookup"><span data-stu-id="5d156-180">When a `ScriptBlock` is converted to a delegate type to be used in C# context, wrapping the result in a `PSObject` brings unneeded troubles:</span></span>

  - <span data-ttu-id="5d156-181">Lorsque la valeur est convertie en type de retour délégué, `PSObject` n’est pas wrappé par essence.</span><span class="sxs-lookup"><span data-stu-id="5d156-181">When the value is converted to the delegate return type, the `PSObject` essentially gets unwrapped.</span></span> <span data-ttu-id="5d156-182">Donc `PSObject` n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5d156-182">So the `PSObject` is unneeded.</span></span>
  - <span data-ttu-id="5d156-183">Lorsque le type de retour délégué est `object`, il est wrappé dans un `PSObject`, ce qui rend difficile son utilisation dans le code C#.</span><span class="sxs-lookup"><span data-stu-id="5d156-183">When the delegate return type is `object`, it gets wrapped in a `PSObject` making it hard to work with in C# code.</span></span>

  <span data-ttu-id="5d156-184">Après ce changement, l’objet retourné est l’objet sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="5d156-184">After this change, the returned object is the underlying object.</span></span>
