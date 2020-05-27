---
ms.date: 12/05/2019
keywords: powershell,applet de commande
title: Démarrage de Windows PowerShell
ms.openlocfilehash: 32ed85510899ea239c9dc332a023554ce9b53e47
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809015"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="369db-103">Démarrage de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="369db-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="369db-104">Windows PowerShell est une entité `.DLL` de moteur de script qui est incorporée dans plusieurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="369db-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="369db-105">Les hôtes les plus courants que vous démarrerez sont l’outil interactif **powershell.exe** de ligne de commande et l’environnement d’écriture de scripts interactif **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="369db-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="369db-106">Pour démarrer Windows PowerShell® sur Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 et Windows 8, consultez [Tâches de gestion courantes et navigation dans Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="369db-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="369db-107">PowerShell Core a un fichier binaire renommé</span><span class="sxs-lookup"><span data-stu-id="369db-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="369db-108">PowerShell Core (version 6 ou ultérieure), connu en tant que PowerShell, est open source et utilise .NET Core.</span><span class="sxs-lookup"><span data-stu-id="369db-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="369db-109">Les versions prises en charge sont disponibles sur Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="369db-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="369db-110">Depuis PowerShell 6, le fichier binaire PowerShell a été renommé **pwsh.exe** pour Windows et **pwsh** pour macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="369db-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="369db-111">Vous pouvez démarrer les préversions de PowerShell à l’aide de **pwsh-preview**.</span><span class="sxs-lookup"><span data-stu-id="369db-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="369db-112">Pour plus d’informations, consultez [Nouveautés de PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) et [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="369db-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="369db-113">Pour trouver la référence des applets de commande et la documentation d’installation de PowerShell 7, utilisez les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="369db-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="369db-114">Document</span><span class="sxs-lookup"><span data-stu-id="369db-114">Document</span></span> | <span data-ttu-id="369db-115">Lien</span><span class="sxs-lookup"><span data-stu-id="369db-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="369db-116">Référence des applets de commande</span><span class="sxs-lookup"><span data-stu-id="369db-116">Cmdlet reference</span></span> | [<span data-ttu-id="369db-117">Navigateur du module PowerShell</span><span class="sxs-lookup"><span data-stu-id="369db-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="369db-118">Installation sur Windows</span><span class="sxs-lookup"><span data-stu-id="369db-118">Windows installation</span></span> | [<span data-ttu-id="369db-119">Installation de PowerShell Core sur Windows</span><span class="sxs-lookup"><span data-stu-id="369db-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="369db-120">Installation sur macOS</span><span class="sxs-lookup"><span data-stu-id="369db-120">macOS installation</span></span> | [<span data-ttu-id="369db-121">Installation de PowerShell Core sur macOS</span><span class="sxs-lookup"><span data-stu-id="369db-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="369db-122">Installation sur Linux</span><span class="sxs-lookup"><span data-stu-id="369db-122">Linux installation</span></span> | [<span data-ttu-id="369db-123">Installation de PowerShell Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="369db-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="369db-124">Pour afficher du contenu pour d’autres versions de PowerShell, consultez [Guide pratique pour utiliser la documentation PowerShell](../how-to-use-docs.md).</span><span class="sxs-lookup"><span data-stu-id="369db-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="369db-125">Comment démarrer Windows PowerShell sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="369db-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="369db-126">Cette section explique comment démarrer Windows PowerShell et l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell sur Windows® 7, Windows Server® 2008 R2 et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="369db-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="369db-127">Elle explique également comment activer la fonctionnalité facultative pour Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server® 2008 R2 et Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="369db-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="369db-128">Pour démarrer la version installée de Windows PowerShell 3.0 ou Windows PowerShell 4.0, le cas échéant, utilisez une des méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="369db-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="369db-129">À partir du menu Démarrer</span><span class="sxs-lookup"><span data-stu-id="369db-129">From the Start Menu</span></span>

- <span data-ttu-id="369db-130">Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="369db-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="369db-131">À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="369db-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="369db-132">À l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="369db-132">At the Command Prompt</span></span>

<span data-ttu-id="369db-133">Dans **cmd.exe**, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="369db-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="369db-134">Vous pouvez également utiliser les paramètres du programme **powershell.exe** pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="369db-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="369db-135">Pour plus d’informations, voir [Aide sur la ligne de commande PowerShell.exe](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span><span class="sxs-lookup"><span data-stu-id="369db-135">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="369db-136">Avec des privilèges d’administration (Exécuter en tant qu’administrateur)</span><span class="sxs-lookup"><span data-stu-id="369db-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="369db-137">Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="369db-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="369db-138">Comment démarrer Windows PowerShell ISE sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="369db-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="369db-139">Utilisez une des méthodes suivantes pour démarrer Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="369db-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="369db-140">À partir du menu Démarrer</span><span class="sxs-lookup"><span data-stu-id="369db-140">From the Start Menu</span></span>

- <span data-ttu-id="369db-141">Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="369db-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="369db-142">À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="369db-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="369db-143">À l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="369db-143">At the Command Prompt</span></span>

<span data-ttu-id="369db-144">Dans **cmd.exe**, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="369db-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="369db-145">or</span><span class="sxs-lookup"><span data-stu-id="369db-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="369db-146">Avec des privilèges d’administration (Exécuter en tant qu’administrateur)</span><span class="sxs-lookup"><span data-stu-id="369db-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="369db-147">Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="369db-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="369db-148">Comment activer Windows PowerShell ISE sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="369db-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="369db-149">Dans Windows PowerShell 4.0 et Windows PowerShell 3.0, Windows PowerShell ISE est activé par défaut sur toutes les versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="369db-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="369db-150">S’il n’est pas déjà activé, Windows Management Framework 4.0 ou Windows Management Framework 3.0 l’active.</span><span class="sxs-lookup"><span data-stu-id="369db-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="369db-151">Dans Windows PowerShell 2.0, Windows PowerShell ISE est activé par défaut sur Windows 7.</span><span class="sxs-lookup"><span data-stu-id="369db-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="369db-152">Toutefois, sur Windows Server 2008 R2 et Windows Server 2008, il s’agit d’une fonctionnalité facultative.</span><span class="sxs-lookup"><span data-stu-id="369db-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="369db-153">Pour activer Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server 2008 R2 ou Windows Server 2008, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="369db-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="369db-154">Pour activer Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="369db-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="369db-155">Démarrez le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="369db-155">Start Server Manager.</span></span>
2. <span data-ttu-id="369db-156">Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="369db-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="369db-157">Dans Sélectionner des fonctionnalités, cliquez sur Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="369db-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="369db-158">Démarrage de la Version 32 bits de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="369db-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="369db-159">Quand vous installez Windows PowerShell sur un ordinateur 64 bits, **Windows PowerShell (x86)** , version 32 bits de Windows PowerShell, est installé en plus de la version 64 bits.</span><span class="sxs-lookup"><span data-stu-id="369db-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="369db-160">Quand vous exécutez Windows PowerShell, la version 64 bits s’exécute par défaut.</span><span class="sxs-lookup"><span data-stu-id="369db-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="369db-161">Toutefois, il se peut que vous deviez occasionnellement exécuter **Windows PowerShell (x86)** , par exemple, lorsque vous utilisez un module nécessitant la version 32 bits ou lorsque vous vous connectez à distance à un ordinateur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="369db-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="369db-162">Pour démarrer une version 32 bits de Windows PowerShell, procédez de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="369db-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="369db-163">Dans Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="369db-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="369db-164">Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="369db-165">Cliquez sur la vignette **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="369db-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="369db-166">Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-167">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-168">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369db-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="369db-169">Dans Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="369db-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="369db-170">Dans l’écran **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-171">Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-172">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **recherche**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-173">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369db-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="369db-174">Dans Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="369db-174">In Windows® 8.1</span></span>

- <span data-ttu-id="369db-175">Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="369db-176">Cliquez sur la vignette **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="369db-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="369db-177">Si vous exécutez les [Outils d’administration de serveur distant](https://go.microsoft.com/fwlink/?LinkID=304145) pour Windows 8.1, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="369db-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="369db-178">Sélectionnez **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-179">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-180">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369db-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="369db-181">Dans Windows® 8</span><span class="sxs-lookup"><span data-stu-id="369db-181">In Windows® 8</span></span>

- <span data-ttu-id="369db-182">Dans l’écran **Démarrer**, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Paramètres**, **Vignettes**, puis positionnez le curseur **Afficher les outils d’administration** sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="369db-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="369db-183">Ensuite, tapez **PowerShell** puis cliquez sur **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-184">Si vous exécutez les [Outils d’administration de serveur distant](https://www.microsoft.com/download/details.aspx?id=28972) pour Windows 8, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="369db-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="369db-185">Sélectionnez **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-186">Dans l’écran **Démarrer** ou sur le Bureau, tapez **PowerShell (x86)** , puis cliquez sur **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369db-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369db-187">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369db-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
