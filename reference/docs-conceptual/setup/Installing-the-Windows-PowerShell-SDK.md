---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Installation du Kit de développement logiciel Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953563"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="3ef8a-103">Installation du Kit de développement logiciel Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ef8a-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="3ef8a-104">La rubrique suivante explique comment installer le SDK PowerShell sur différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="3ef8a-105">Installation du SDK Windows PowerShell 3.0 pour Windows 8 et Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3ef8a-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="3ef8a-106">Windows PowerShell 3.0 est automatiquement installé avec Windows 8 et Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="3ef8a-107">De plus, vous pouvez télécharger et installer les assemblys de référence pour Windows PowerShell 3.0 avec le SDK Windows 8.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="3ef8a-108">Ces assemblys permettent d’écrire des applets de commande, des fournisseurs et des programmes hôtes pour Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="3ef8a-109">Quand vous installez le SDK Windows pour Windows 8, les assemblys Windows PowerShell sont automatiquement installés dans le dossier d’assemblys de référence, dans \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="3ef8a-110">Pour plus d’informations, voir le [site de téléchargement du SDK Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="3ef8a-111">Des exemples de code Windows PowerShell sont aussi disponibles dans le Centre de développement.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="3ef8a-112">Pour plus d’informations, voir la page d’exemples de code Windows Desktop sur le [site du Centre de développement](http://code.msdn.microsoft.com/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="3ef8a-113">Par ailleurs, Windows PowerShell 3.0 est rétrocompatible avec le SDK Windows PowerShell 2.0 qui comprend un certain nombre d’exemples de code.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="3ef8a-114">Pour plus d’informations sur la façon de télécharger le SDK Windows PowerShell 2.0, voir ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="3ef8a-115">(Même si les exemples de code 2.0 sont compatibles avec Windows 8 et Windows PowerShell 3.0, notez que vous ne pouvez pas installer Windows PowerShell 2.0 sur une plateforme Windows 8.)</span><span class="sxs-lookup"><span data-stu-id="3ef8a-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="3ef8a-116">Installation du SDK Windows PowerShell 3.0 pour Windows 7 et Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3ef8a-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="3ef8a-117">PowerShell 2.0 est automatiquement installé sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="3ef8a-118">Par ailleurs, vous pouvez installer PowerShell 3.0 sur ces systèmes.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="3ef8a-119">(Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).)</span><span class="sxs-lookup"><span data-stu-id="3ef8a-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="3ef8a-120">Comme indiqué plus haut, vous pouvez aussi installer le SDK Windows 8 sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="3ef8a-121">Installation du SDK Windows PowerShell 2.0 pour Windows 7, Vista, XP, Server 2003 et Server 2008</span><span class="sxs-lookup"><span data-stu-id="3ef8a-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="3ef8a-122">Le SDK Windows PowerShell 2.0 fournit les assemblys de référence nécessaires à l’écriture d’applets de commande, de fournisseurs et d’applications d’hébergement. Il propose aussi un exemple de code C# qui peut vous servir de point de départ pour commencer à écrire du code.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="3ef8a-123">Pour installer ce SDK, voir le [SDK Windows PowerShell 2.0 ](http://go.microsoft.com/fwlink/?LinkId=184611).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="3ef8a-124">Assemblys de référence</span><span class="sxs-lookup"><span data-stu-id="3ef8a-124">Reference assemblies</span></span>

<span data-ttu-id="3ef8a-125">Les assemblys de référence sont installés dans l’emplacement par défaut suivant : `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="3ef8a-126">**Remarque** : Le code compilé sur les assemblys Windows PowerShell 2.0 ne peut pas être chargé dans les installations de Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="3ef8a-127">En revanche, le code compilé sur les assemblys Windows PowerShell 1.0 peut être chargé dans les installations de Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="3ef8a-128">exemples</span><span class="sxs-lookup"><span data-stu-id="3ef8a-128">Samples</span></span>

<span data-ttu-id="3ef8a-129">Les exemples de code sont installés dans l’emplacement par défaut suivant : `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="3ef8a-130">Les sections suivantes fournissent une brève description de la fonction de chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="3ef8a-131">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="3ef8a-131">Cmdlet samples</span></span>
<span data-ttu-id="3ef8a-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-132">**GetProcessSample01**</span></span>

<span data-ttu-id="3ef8a-133">Montre comment écrire une applet de commande simple qui obtient tous les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="3ef8a-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-134">**GetProcessSample02**</span></span>

<span data-ttu-id="3ef8a-135">Montre comment ajouter des paramètres à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="3ef8a-136">L’applet de commande prend un ou plusieurs noms de processus et retourne les processus correspondants.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="3ef8a-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-137">**GetProcessSample03**</span></span>

<span data-ttu-id="3ef8a-138">Montre comment ajouter des paramètres qui acceptent une entrée provenant du pipeline.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="3ef8a-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-139">**GetProcessSample04**</span></span>

<span data-ttu-id="3ef8a-140">Montre comment gérer les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="3ef8a-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-141">**GetProcessSample05**</span></span>

<span data-ttu-id="3ef8a-142">Montre comment afficher une liste de processus spécifiés.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="3ef8a-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-143">**SelectObject**</span></span>

<span data-ttu-id="3ef8a-144">Montre comment écrire un filtre pour sélectionner uniquement certains objets.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="3ef8a-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-145">**SelectString**</span></span>

<span data-ttu-id="3ef8a-146">Montre comment rechercher des modèles spécifiés dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="3ef8a-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-147">**StopProcessSample01**</span></span>

<span data-ttu-id="3ef8a-148">Montre comment implémenter un paramètre *PassThru* et comment demander des commentaires utilisateur en appelant les méthodes [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) et [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="3ef8a-149">Les utilisateurs spécifient le paramètre *PassThru* quand ils veulent forcer l’applet de commande à retourner un objet.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="3ef8a-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-150">**StopProcessSample02**</span></span>

<span data-ttu-id="3ef8a-151">Montre comment arrêter un processus spécifique.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="3ef8a-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-152">**StopProcessSample03**</span></span>

<span data-ttu-id="3ef8a-153">Montre comment déclarer des alias de paramètres et comment prendre en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="3ef8a-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-154">**StopProcessSample04**</span></span>

<span data-ttu-id="3ef8a-155">Montre comment déclarer des jeux de paramètres, l’objet que prend l’applet de commande comme entrée et comment spécifier le jeu de paramètres à utiliser par défaut.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="3ef8a-156">Exemples de communication à distance</span><span class="sxs-lookup"><span data-stu-id="3ef8a-156">Remoting samples</span></span>

<span data-ttu-id="3ef8a-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="3ef8a-158">Montre comment créer une instance d’exécution à distance servant à établir une connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="3ef8a-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="3ef8a-160">Montre comment construire un pool d’instances d’exécution à distance et comment exécuter plusieurs commandes simultanément en utilisant ce pool.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="3ef8a-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-161">**Serialization01**</span></span>

<span data-ttu-id="3ef8a-162">Montre comment examiner une classe .NET existante et vérifier que les informations provenant des propriétés publiques sélectionnées de cette classe sont conservées à l’issue de la sérialisation/désérialisation.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="3ef8a-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-163">**Serialization02**</span></span>

<span data-ttu-id="3ef8a-164">Montre comment examiner une classe .NET existante et vérifier que les informations provenant de l’instance de cette classe sont conservées à l’issue de la sérialisation/désérialisation quand les informations ne sont pas disponibles dans les propriétés publiques de la classe.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="3ef8a-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-165">**Serialization03**</span></span>

<span data-ttu-id="3ef8a-166">Montre comment examiner une classe .NET existante et vérifier que les instances de cette classe et des classes dérivées sont désérialisées (réactivées) en objets .NET dynamiques.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="3ef8a-167">Exemples d’événements</span><span class="sxs-lookup"><span data-stu-id="3ef8a-167">Event samples</span></span>

<span data-ttu-id="3ef8a-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-168">**Event01**</span></span>

<span data-ttu-id="3ef8a-169">Montre comment créer une applet de commande pour l’inscription d’événements en la dérivant de la classe ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="3ef8a-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-170">**Event02**</span></span>

<span data-ttu-id="3ef8a-171">Montre comment recevoir des notifications d’événements Windows PowerShell générés sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="3ef8a-172">Il utilise l’événement PSEventReceived exposé via la classe [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="3ef8a-173">Exemples d’applications d’hébergement</span><span class="sxs-lookup"><span data-stu-id="3ef8a-173">Hosting application samples</span></span>

<span data-ttu-id="3ef8a-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-174">**Runspace01**</span></span>

<span data-ttu-id="3ef8a-175">Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter l’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="3ef8a-176">L’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retourne des objets [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) pour chaque processus s’exécutant sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="3ef8a-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-177">**Runspace02**</span></span>

<span data-ttu-id="3ef8a-178">Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter les applets de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) et [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="3ef8a-179">L’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retourne des objets [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) pour chaque processus s’exécutant sur l’ordinateur local, tandis que Sort-Object trie les objets en fonction de leur propriété [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="3ef8a-180">Le résultat de ces commandes s’affiche au moyen d’un contrôle [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="3ef8a-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-181">**Runspace03**</span></span>

<span data-ttu-id="3ef8a-182">Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="3ef8a-183">Le script reçoit une liste de noms de processus et récupère ensuite ces processus.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="3ef8a-184">Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="3ef8a-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-185">**Runspace04**</span></span>

<span data-ttu-id="3ef8a-186">Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter des commandes et comment intercepter les erreurs avec fin d’exécution qui sont levées pendant l’exécution des commandes.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="3ef8a-187">Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="3ef8a-188">Par conséquent, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="3ef8a-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-189">**Runspace05**</span></span>

<span data-ttu-id="3ef8a-190">Montre comment ajouter un composant logiciel enfichable à un objet [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) de telle sorte que l’applet de commande du composant logiciel enfichable soit disponible quand l’instance d’exécution est ouverte.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="3ef8a-191">Le composant logiciel enfichable fournit une applet de commande Get-Process (définie par [l’exemple GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) qui est exécutée de façon synchrone à l’aide d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="3ef8a-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-192">**Runspace06**</span></span>

<span data-ttu-id="3ef8a-193">Montre comment ajouter un module à un objet [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) de telle sorte que le module soit chargé quand l’instance d’exécution est ouverte.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="3ef8a-194">Le module fournit une applet de commande Get-Process (définie par [l’exemple GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) qui est exécutée de façon synchrone à l’aide d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="3ef8a-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-195">**Runspace07**</span></span>

<span data-ttu-id="3ef8a-196">Montre comment créer une instance d’exécution, puis s’en servir pour exécuter deux applets de commande de façon synchrone en utilisant un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="3ef8a-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-197">**Runspace08**</span></span>

<span data-ttu-id="3ef8a-198">Montre comment ajouter des commandes et des arguments au pipeline d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) et comment exécuter les commandes de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="3ef8a-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-199">**Runspace09**</span></span>

<span data-ttu-id="3ef8a-200">Montre comment ajouter un script au pipeline d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) et comment exécuter le script de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="3ef8a-201">Des événements sont utilisés pour gérer la sortie du script.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="3ef8a-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-202">**Runspace10**</span></span>

<span data-ttu-id="3ef8a-203">Montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande en utilisant un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="3ef8a-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-204">**Runspace11**</span></span>

<span data-ttu-id="3ef8a-205">Montre comment utiliser la classe [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) pour créer une commande proxy qui appelle une applet de commande existante, mais qui limite le jeu de paramètres disponibles.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="3ef8a-206">La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="3ef8a-207">Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="3ef8a-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-208">**PowerShell01**</span></span>

<span data-ttu-id="3ef8a-209">Montre comment créer une instance d’exécution contrainte en utilisant un objet [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="3ef8a-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-210">**PowerShell02**</span></span>

<span data-ttu-id="3ef8a-211">Montre comment utiliser un pool d’instances d’exécution pour exécuter plusieurs commandes simultanément.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="3ef8a-212">Exemples d’hôtes</span><span class="sxs-lookup"><span data-stu-id="3ef8a-212">Host samples</span></span>

<span data-ttu-id="3ef8a-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-213">**Host01**</span></span>

<span data-ttu-id="3ef8a-214">Montre comment implémenter une application hôte qui utilise un hôte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="3ef8a-215">Dans cet exemple, l’instance d’exécution qui est créée utilise l’hôte personnalisé, puis l’API [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) est utilisée pour exécuter un script qui appelle « exit ».</span><span class="sxs-lookup"><span data-stu-id="3ef8a-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="3ef8a-216">L’application hôte analyse ensuite la sortie du script et imprime les résultats.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="3ef8a-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-217">**Host02**</span></span>

<span data-ttu-id="3ef8a-218">Montre comment écrire une application hôte qui utilise le runtime Windows PowerShell avec une implémentation d’hôte personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="3ef8a-219">L’application hôte définit la culture de l’hôte sur l’allemand, exécute l’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) et affiche les résultats comme vous les verriez avec pwrsh.exe pour ensuite imprimer la date et l’heure actuelles en allemand.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="3ef8a-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-220">**Host03**</span></span>

<span data-ttu-id="3ef8a-221">Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="3ef8a-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-222">**Host04**</span></span>

<span data-ttu-id="3ef8a-223">Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="3ef8a-224">Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="3ef8a-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-225">**Host05**</span></span>

<span data-ttu-id="3ef8a-226">Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="3ef8a-227">Cette application hôte prend aussi en charge les appels à des ordinateurs distants à l’aide des applets de commande [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) et [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="3ef8a-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-228">**Host06**</span></span>

<span data-ttu-id="3ef8a-229">Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="3ef8a-230">Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="3ef8a-231">Exemples de fournisseurs</span><span class="sxs-lookup"><span data-stu-id="3ef8a-231">Provider samples</span></span>

<span data-ttu-id="3ef8a-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="3ef8a-233">Montre comment déclarer une classe de fournisseur qui dérive directement de la classe [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="3ef8a-234">Il est indiqué ici uniquement par souci de citer tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-234">It is included here only for completeness.</span></span>

<span data-ttu-id="3ef8a-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="3ef8a-236">Montre comment remplacer les méthodes [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) et [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) pour prendre en charge les appels aux applets de commande New-PSDrive et Remove-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="3ef8a-237">La classe de fournisseur de cet exemple dérive de la classe [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="3ef8a-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="3ef8a-239">Montre comment remplacer les méthodes [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) et [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) pour prendre en charge les appels aux applets de commande Get-Item et Set-Item.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="3ef8a-240">La classe de fournisseur de cet exemple dérive de la classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="3ef8a-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="3ef8a-242">Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande Copy-Item, Get-ChildItem, New-Item et Remove-Item.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="3ef8a-243">Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="3ef8a-244">Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="3ef8a-245">La classe de fournisseur de cet exemple dérive de la classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="3ef8a-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="3ef8a-247">Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande Move-Item et Join-Path.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="3ef8a-248">Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="3ef8a-249">La classe de fournisseur de cet exemple dérive de la classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="3ef8a-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="3ef8a-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="3ef8a-251">Montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux applets de commande Clear-Content, Get-Content et Set-Content.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="3ef8a-252">Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="3ef8a-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="3ef8a-253">La classe de fournisseur de cet exemple dérive de la classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) et implémente l’interface [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="3ef8a-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>