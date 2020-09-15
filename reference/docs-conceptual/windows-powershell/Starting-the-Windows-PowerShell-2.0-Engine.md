---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation du moteur Windows PowerShell 2.0
ms.openlocfilehash: c5ac92159d63e5669643908016186ed32dfb46db
ms.sourcegitcommit: 3e343f005fe76960c998ef1869a1a093d37ef349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216020"
---
# <a name="using-the-windows-powershell-20-engine"></a><span data-ttu-id="2fde6-103">Utilisation du moteur Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="2fde6-103">Using the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="2fde6-104">Windows PowerShell est conçu pour offrir une compatibilité descendante avec des versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="2fde6-104">Windows PowerShell is designed to be backward compatible with previous versions.</span></span> <span data-ttu-id="2fde6-105">Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour Windows PowerShell 2.0 s’exécutent sans modification dans les versions plus récentes de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fde6-105">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in newer versions Windows PowerShell.</span></span> <span data-ttu-id="2fde6-106">Toutefois, Microsoft .NET Framework 4 a changé la stratégie d’activation du runtime.</span><span class="sxs-lookup"><span data-stu-id="2fde6-106">However, Microsoft .NET Framework 4 changed the runtime activation policy.</span></span>
<span data-ttu-id="2fde6-107">Les programmes hôtes de Windows PowerShell écrits pour Windows PowerShell 2.0 et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans les nouvelles versions de Windows PowerShell qui sont compilées avec CLR 4.0 (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="2fde6-107">Windows PowerShell host programs written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in new versions Windows PowerShell that are compiled with CLR 4.0 (or higher).</span></span>

<span data-ttu-id="2fde6-108">Le moteur Windows PowerShell 2.0 est destiné à être utilisé uniquement quand un script ou un programme hôte existant ne peut pas s’exécuter car il n’est pas compatible avec Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="2fde6-108">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 5.1.</span></span> <span data-ttu-id="2fde6-109">Il peut s’agir, par exemple, de versions antérieures de modules Exchange ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2fde6-109">Examples of this include older versions of Exchange or SQL Server modules.</span></span> <span data-ttu-id="2fde6-110">Ces cas sont supposé être rares.</span><span class="sxs-lookup"><span data-stu-id="2fde6-110">Such cases are expected to be rare.</span></span>

<span data-ttu-id="2fde6-111">De nombreux programmes qui nécessitent le moteur Windows PowerShell 2.0 le démarrent automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2fde6-111">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="2fde6-112">Ces instructions sont fournies pour les rares cas où vous devez démarrer le moteur manuellement.</span><span class="sxs-lookup"><span data-stu-id="2fde6-112">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="deprecation-and-security-concerns"></a><span data-ttu-id="2fde6-113">Dépréciation et problèmes de sécurité</span><span class="sxs-lookup"><span data-stu-id="2fde6-113">Deprecation and security concerns</span></span>

<span data-ttu-id="2fde6-114">Windows PowerShell 2.0 a été déprécié en août 2017.</span><span class="sxs-lookup"><span data-stu-id="2fde6-114">Windows PowerShell 2.0 was deprecated in August, 2017.</span></span> <span data-ttu-id="2fde6-115">Pour plus d’informations, consultez l’[annonce][] sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fde6-115">For more information, see the [announcement][] on the PowerShell blog.</span></span>

<span data-ttu-id="2fde6-116">Windows PowerShell 2.0 ne dispose pas d’une quantité importante de fonctionnalités de sécurisation de renforcement et de sécurité qui ont été ajoutées dans les versions 3, 4 et 5.</span><span class="sxs-lookup"><span data-stu-id="2fde6-116">Windows PowerShell 2.0 is missing a significant amount of the hardening and security features added in versions 3, 4, and 5.</span></span> <span data-ttu-id="2fde6-117">Nous recommandons vivement aux utilisateurs de ne pas l’utiliser, s’ils peuvent l’éviter.</span><span class="sxs-lookup"><span data-stu-id="2fde6-117">We highly, highly recommend that users not use it if they can help it.</span></span> <span data-ttu-id="2fde6-118">Pour plus d’informations, consultez [Comparaison de l’interpréteur de commandes et de la sécurité du langage de script][] et [PowerShell ♥ the Blue Team][blueteam].</span><span class="sxs-lookup"><span data-stu-id="2fde6-118">For more information, see [A Comparison of Shell and Scripting Language Security][] and [PowerShell ♥ the Blue Team][blueteam].</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="2fde6-119">Installation et activation des programmes requis</span><span class="sxs-lookup"><span data-stu-id="2fde6-119">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="2fde6-120">Avant de démarrer le moteur Windows PowerShell 2.0, activez le moteur Windows PowerShell 2.0 et Microsoft .NET Framework 3.5 avec Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="2fde6-120">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="2fde6-121">Pour obtenir des instructions, voir [Installation de Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="2fde6-121">For instructions, see [Installing Windows PowerShell][].</span></span>

<span data-ttu-id="2fde6-122">Les systèmes sur lesquels Windows Management Framework 3.0 ou les versions ultérieures sont installés disposent de tous les composants nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2fde6-122">Systems on which Windows Management Framework 3.0 or higher is installed have all of the required components.</span></span> <span data-ttu-id="2fde6-123">Aucune autre configuration n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2fde6-123">No further configuration is necessary.</span></span> <span data-ttu-id="2fde6-124">Pour plus d’informations sur l’installation de Windows Management Framework, consultez [Installer et configurer WMF][].</span><span class="sxs-lookup"><span data-stu-id="2fde6-124">For information about installing Windows Management Framework, see [Install and configure WMF][].</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="2fde6-125">Comment démarrer le moteur Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="2fde6-125">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="2fde6-126">Quand vous démarrez Windows PowerShell, la version la plus récente démarre par défaut.</span><span class="sxs-lookup"><span data-stu-id="2fde6-126">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="2fde6-127">Pour démarrer Windows PowerShell avec le moteur Windows PowerShell 2.0, utilisez le paramètre Version de `PowerShell.exe`.</span><span class="sxs-lookup"><span data-stu-id="2fde6-127">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of `PowerShell.exe`.</span></span> <span data-ttu-id="2fde6-128">Vous pouvez exécuter la commande à tout invite de commandes, y compris de Windows PowerShell et de Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="2fde6-128">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="2fde6-129">Comment démarrer une session à distance avec le moteur Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="2fde6-129">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="2fde6-130">Pour exécuter le moteur Windows PowerShell 2.0 dans une session à distance, créez une configuration de session (également appelée _point de terminaison_) sur l’ordinateur distant qui charge le moteur Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2fde6-130">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an _endpoint_) on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="2fde6-131">La configuration de session est enregistrée sur l’ordinateur distant et peut être utilisée par toute personne autorisée à créer des sessions faisant appel au moteur Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2fde6-131">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="2fde6-132">Il s’agit d’une tâche avancée généralement effectuée par un administrateur système.</span><span class="sxs-lookup"><span data-stu-id="2fde6-132">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="2fde6-133">La procédure suivante utilise le paramètre **PSVersion** de l’applet de commande [Register-PSSessionConfiguration][] pour créer une configuration de session qui utilise le moteur Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2fde6-133">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration][] cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="2fde6-134">Vous pouvez également utiliser le paramètre **PowerShellVersion** de l’applet de comment [New-PSSessionConfigurationFile][] pour créer un fichier de configuration de session pour une session qui charge le moteur Windows PowerShell 2.0, et pouvez utiliser le paramètre **PSVersion** de l’applet de commande [Set-PSSessionConfiguration][] pour modifier une configuration de session afin d’utiliser le moteur Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2fde6-134">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile][] cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration][] parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="2fde6-135">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files][].</span><span class="sxs-lookup"><span data-stu-id="2fde6-135">For more information about session configuration files, see [about_Session_Configuration_Files][].</span></span>
<span data-ttu-id="2fde6-136">Pour obtenir des informations sur les configurations de session, notamment l’installation et la sécurité, consultez [about_Session_Configurations][].</span><span class="sxs-lookup"><span data-stu-id="2fde6-136">For information about session configurations, including setup and security, see [about_Session_Configurations][].</span></span>

### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="2fde6-137">Pour démarrer une session Windows PowerShell 2.0 à distance</span><span class="sxs-lookup"><span data-stu-id="2fde6-137">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="2fde6-138">Pour créer une configuration de session qui nécessite le moteur Windows PowerShell 2.0, utilisez le paramètre **PSVersion** de l’applet de commande `Register-PSSessionConfiguration` avec la valeur `2.0`.</span><span class="sxs-lookup"><span data-stu-id="2fde6-138">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet with a value of `2.0`.</span></span>
   <span data-ttu-id="2fde6-139">Exécutez cette commande sur l’ordinateur « côté serveur » ou en fin de réception de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2fde6-139">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="2fde6-140">L’exemple de commande suivant crée la configuration de session PS2 sur l’ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="2fde6-140">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="2fde6-141">Pour exécuter cette commande, démarrez Windows PowerShell avec l’option **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="2fde6-141">To run this command, start Windows PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. <span data-ttu-id="2fde6-142">Pour créer une session sur l’ordinateur Server01 qui utilise la configuration de session PS2, utilisez le paramètre **ConfigurationName** d’applets de commande qui créent une session à distance, comme l’applet de commande « New-PSSession ».</span><span class="sxs-lookup"><span data-stu-id="2fde6-142">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the \`New-PSSession cmdlet.</span></span>

   <span data-ttu-id="2fde6-143">Quand une session utilisant la configuration de session démarre, le moteur Windows PowerShell 2.0 est automatiquement chargé dans la session.</span><span class="sxs-lookup"><span data-stu-id="2fde6-143">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="2fde6-144">La commande suivante démarre une session sur l’ordinateur Server01 qui utilise la configuration de session PS2.</span><span class="sxs-lookup"><span data-stu-id="2fde6-144">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="2fde6-145">La commande enregistre la session dans la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="2fde6-145">The command saves the session in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="2fde6-146">Comment démarrer un travail en arrière-plan avec le moteur Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="2fde6-146">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="2fde6-147">Pour démarrer un travail en arrière-plan avec le moteur Windows PowerShell 2.0, utilisez le paramètre **PSVersion** de l’applet de commande [Start-Job][].</span><span class="sxs-lookup"><span data-stu-id="2fde6-147">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job][] cmdlet.</span></span>

<span data-ttu-id="2fde6-148">La commande suivante démarre un travail en arrière-plan avec le moteur Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="2fde6-148">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="2fde6-149">Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs][].</span><span class="sxs-lookup"><span data-stu-id="2fde6-149">For more information about background jobs, see [about_Jobs][].</span></span>

<!-- link references -->
[Annonce]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Comparaison de l’interpréteur de commandes et de la sécurité du langage de script]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[A Comparison of Shell and Scripting Language Security]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Installation de Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installing Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installer et configurer WMF]: wmf/setup/install-configure.md
[Install and configure WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
