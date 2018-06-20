---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Démarrage de Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953121"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="4ba2e-103">Démarrage de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ba2e-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="4ba2e-104">PowerShell est une DLL de moteur de script qui est incorporée dans plusieurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="4ba2e-105">L’hôte le plus courant que vous démarrerez sont la ligne de commande interactive PowerShell.exe et l’environnement d’écriture de scripts interactif PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="4ba2e-106">Pour démarrer Windows PowerShell® sur Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 et Windows 8, voir [Tâches de gestion courantes et navigation](http://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="4ba2e-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="4ba2e-107">Comment démarrer Windows PowerShell sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="4ba2e-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="4ba2e-108">Cette section explique comment démarrer Windows PowerShell et l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell sur Windows® 7, Windows Server® 2008 R2 et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="4ba2e-109">Elle explique également comment activer la fonctionnalité facultative pour Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server® 2008 R2 et Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="4ba2e-110">Pour démarrer la version installée de Windows PowerShell 3.0 ou Windows PowerShell 4.0, le cas échéant, utilisez une des méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="4ba2e-111">À partir du menu Démarrer</span><span class="sxs-lookup"><span data-stu-id="4ba2e-111">From the Start Menu</span></span>

- <span data-ttu-id="4ba2e-112">Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="4ba2e-113">À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="4ba2e-114">À l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="4ba2e-114">At the Command Prompt</span></span>

<span data-ttu-id="4ba2e-115">Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="4ba2e-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="4ba2e-116">Vous pouvez également utiliser les paramètres du programme PowerShell.exe pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="4ba2e-117">Pour plus d’informations, voir [Aide sur la ligne de commande PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="4ba2e-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="4ba2e-118">Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="4ba2e-119">Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="4ba2e-120">Comment démarrer Windows PowerShell ISE sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="4ba2e-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="4ba2e-121">Utilisez une des méthodes suivantes pour démarrer Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="4ba2e-122">À partir du menu Démarrer</span><span class="sxs-lookup"><span data-stu-id="4ba2e-122">From the Start Menu</span></span>

- <span data-ttu-id="4ba2e-123">Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="4ba2e-124">À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="4ba2e-125">À l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="4ba2e-125">At the Command Prompt</span></span>

<span data-ttu-id="4ba2e-126">Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="4ba2e-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="4ba2e-127">ou</span><span class="sxs-lookup"><span data-stu-id="4ba2e-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="4ba2e-128">Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="4ba2e-129">Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="4ba2e-130">Comment activer Windows PowerShell ISE sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="4ba2e-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="4ba2e-131">Dans Windows PowerShell 4.0 et Windows PowerShell 3.0, Windows PowerShell ISE est activé par défaut sur toutes les versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="4ba2e-132">S’il n’est pas activé, Windows Management Framework 4.0 ou Windows Management Framework 3.0 l’active.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="4ba2e-133">Dans Windows PowerShell 2.0, Windows PowerShell ISE est activé par défaut sur Windows 7.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="4ba2e-134">Toutefois, sur Windows Server 2008 R2 et Windows Server 2008, c’est une fonctionnalité facultative.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="4ba2e-135">Pour activer Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server 2008 R2 ou Windows Server 2008, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="4ba2e-136">Pour activer Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="4ba2e-137">Démarrez le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-137">Start Server Manager.</span></span>
2. <span data-ttu-id="4ba2e-138">Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="4ba2e-139">Dans Sélectionner des fonctionnalités, cliquez sur Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="4ba2e-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="4ba2e-140">Démarrage de la Version 32 bits de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ba2e-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="4ba2e-141">Quand vous installez Windows PowerShell sur un ordinateur 64 bits, **Windows PowerShell (x86)**, version 32 bits de Windows PowerShell, est installé en plus de la version 64 bits.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="4ba2e-142">Quand vous exécutez Windows PowerShell, la version 64 bits s’exécute par défaut.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="4ba2e-143">Toutefois, il se peut que vous deviez occasionnellement exécuter **Windows PowerShell (x86)**, par exemple, lorsque vous utilisez un module nécessitant la version 32 bits ou lorsque vous vous connectez à distance à un ordinateur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="4ba2e-144">Pour démarrer une version 32 bits de Windows PowerShell, procédez de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="4ba2e-145">Dans Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4ba2e-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="4ba2e-146">Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="4ba2e-147">Cliquez sur la vignette **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="4ba2e-148">Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-149">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-150">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4ba2e-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="4ba2e-151">Dans Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="4ba2e-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="4ba2e-152">Dans l’écran **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-153">Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-154">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **recherche**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-155">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4ba2e-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="4ba2e-156">Dans Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="4ba2e-156">In Windows® 8.1</span></span>

- <span data-ttu-id="4ba2e-157">Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="4ba2e-158">Cliquez sur la vignette **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="4ba2e-159">Si vous exécutez les [Outils d’Administration de serveur distant](http://go.microsoft.com/fwlink/?LinkID=304145) pour Windows 8.1, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-159">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="4ba2e-160">Sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-161">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-162">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4ba2e-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="4ba2e-163">Dans Windows® 8</span><span class="sxs-lookup"><span data-stu-id="4ba2e-163">In Windows® 8</span></span>

- <span data-ttu-id="4ba2e-164">Dans l’écran **Démarrer**, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Paramètres**, **Vignettes**, puis positionnez le curseur **Afficher les outils d’administration** sur Oui.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="4ba2e-165">Ensuite, tapez **PowerShell** puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-166">Si vous exécutez les [Outils d’Administration de serveur distant](http://www.microsoft.com/download/details.aspx?id=28972) pour Windows 8, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-166">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="4ba2e-167">Sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-168">Dans l’écran **Démarrer** ou sur le Bureau, tapez **PowerShell (x86)**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="4ba2e-169">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4ba2e-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>