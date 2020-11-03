---
description: Décrit les composants logiciels enfichables Windows PowerShell et explique comment les utiliser et les gérer.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207618"
---
# <a name="about-pssnapins"></a><span data-ttu-id="d8577-104">À propos de PSSnapins</span><span class="sxs-lookup"><span data-stu-id="d8577-104">About PSSnapins</span></span>

## <a name="short-description"></a><span data-ttu-id="d8577-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="d8577-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d8577-106">Décrit les composants logiciels enfichables Windows PowerShell et explique comment les utiliser et les gérer.</span><span class="sxs-lookup"><span data-stu-id="d8577-106">Describes  Windows PowerShell snap-ins and shows how to use and manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="d8577-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="d8577-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d8577-108">Un composant logiciel enfichable Windows PowerShell est un assembly d’infrastructure Microsoft .NET qui contient des fournisseurs et des applets de commande Windows PowerShell \/ .</span><span class="sxs-lookup"><span data-stu-id="d8577-108">A Windows PowerShell snap-in is a Microsoft .NET Framework assembly that contains Windows PowerShell providers and\/or cmdlets.</span></span> <span data-ttu-id="d8577-109">Windows PowerShell comprend un ensemble de composants logiciels enfichables de base, mais vous pouvez étendre la puissance et la valeur de Windows PowerShell en ajoutant des composants logiciels enfichables qui contiennent des fournisseurs et des applets de commande que vous créez ou récupérez d’autres.</span><span class="sxs-lookup"><span data-stu-id="d8577-109">Windows PowerShell includes a set of basic snap-ins, but you can extend the power and value of Windows PowerShell by adding snap-ins that contain providers and cmdlets that you create or get from others.</span></span>

<span data-ttu-id="d8577-110">Lorsque vous ajoutez un composant logiciel enfichable, les applets de commande et les fournisseurs qu’il contient sont immédiatement disponibles pour une utilisation dans la session active, mais la modification affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="d8577-110">When you add a snap-in, the cmdlets and providers that it contains are immediately available for use in the current session, but the change affects only the current session.</span></span>

<span data-ttu-id="d8577-111">Pour ajouter le composant logiciel enfichable à toutes les sessions ultérieures, enregistrez-le dans votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-111">To add the snap-in to all future sessions, save it in your Windows PowerShell profile.</span></span> <span data-ttu-id="d8577-112">Vous pouvez également utiliser l’applet de commande Export-Console pour enregistrer les noms des composants logiciels enfichables dans un fichier de console, puis les utiliser dans les sessions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d8577-112">You can also use the Export-Console cmdlet to save the snap-in names to a console file and then use it in future sessions.</span></span> <span data-ttu-id="d8577-113">Vous pouvez même enregistrer plusieurs fichiers de console, chacun avec un ensemble différent de composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="d8577-113">You can even save multiple console files, each with a different set of snap-ins.</span></span>

<span data-ttu-id="d8577-114">Remarque : les composants logiciels enfichables Windows PowerShell (PSSnapins) peuvent être utilisés dans Windows PowerShell 3,0 et Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8577-114">NOTE: Windows PowerShell snap-ins (PSSnapins) are available for use in Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="d8577-115">Ils peuvent être modifiés ou non disponibles dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d8577-115">They might be altered or unavailable in subsequent versions.</span></span> <span data-ttu-id="d8577-116">Pour empaqueter les fournisseurs et applets de commande de Windows PowerShell, utilisez des modules.</span><span class="sxs-lookup"><span data-stu-id="d8577-116">To package Windows PowerShell cmdlets and providers, use modules.</span></span> <span data-ttu-id="d8577-117">Pour plus d’informations sur la création de modules et la conversion de composants logiciels enfichables en modules, consultez [écriture d’un module Windows PowerShell](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="d8577-117">For information about creating modules and converting snap-ins to modules, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

### <a name="finding-snap-ins"></a><span data-ttu-id="d8577-118">RECHERCHE DE COMPOSANTS LOGICIELS ENFICHABLES</span><span class="sxs-lookup"><span data-stu-id="d8577-118">FINDING SNAP-INS</span></span>

<span data-ttu-id="d8577-119">Pour obtenir la liste des composants logiciels enfichables Windows PowerShell sur votre ordinateur, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-119">To get a list of the  Windows PowerShell snap-ins on your computer, type:</span></span>

```powershell
Get-PSSnapin
```

<span data-ttu-id="d8577-120">Pour obtenir le composant logiciel enfichable pour chaque fournisseur Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-120">To get the snap-in for each  Windows PowerShell provider, type:</span></span>

```powershell
Get-PSProvider | Format-List name, pssnapin
```

<span data-ttu-id="d8577-121">Pour obtenir la liste des applets de commande dans un composant logiciel enfichable Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-121">To get a list of the cmdlets in a  Windows PowerShell snap-in, type:</span></span>

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a><span data-ttu-id="d8577-122">INSTALLATION D’UN COMPOSANT LOGICIEL ENFICHABLE</span><span class="sxs-lookup"><span data-stu-id="d8577-122">INSTALLING A SNAP-IN</span></span>

<span data-ttu-id="d8577-123">Les composants logiciels enfichables intégrés sont enregistrés dans le système et ajoutés à la session par défaut lorsque vous démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-123">The built-in snap-ins are registered in the system and added to the default session when you start Windows PowerShell.</span></span> <span data-ttu-id="d8577-124">Toutefois, vous devez inscrire les composants logiciels enfichables que vous créez ou obtenez à partir d’autres, puis ajouter les composants logiciels enfichables à votre session.</span><span class="sxs-lookup"><span data-stu-id="d8577-124">However, you have to register snap-ins that you create or obtain from others and then add the snap-ins to your session.</span></span>

### <a name="registering-a-snap-in"></a><span data-ttu-id="d8577-125">INSCRIPTION D’UN COMPOSANT LOGICIEL ENFICHABLE</span><span class="sxs-lookup"><span data-stu-id="d8577-125">REGISTERING A SNAP-IN</span></span>

<span data-ttu-id="d8577-126">Un composant logiciel enfichable Windows PowerShell est un programme écrit dans un langage de .NET Framework qui est compilé dans un fichier. dll.</span><span class="sxs-lookup"><span data-stu-id="d8577-126">A Windows PowerShell snap-in is a program written in a .NET Framework language that is compiled into a .dll file.</span></span> <span data-ttu-id="d8577-127">Pour utiliser les fournisseurs et les applets de commande dans un composant logiciel enfichable, vous devez d’abord inscrire le composant logiciel enfichable (l’ajouter au registre).</span><span class="sxs-lookup"><span data-stu-id="d8577-127">To use the providers and cmdlets in a snap-in, you must first register the snap-in (add it to the registry).</span></span>

<span data-ttu-id="d8577-128">La plupart des composants logiciels enfichables incluent un programme d’installation (un fichier. exe ou. msi) qui enregistre le fichier. dll pour vous.</span><span class="sxs-lookup"><span data-stu-id="d8577-128">Most snap-ins include an installation program (an .exe or .msi file) that registers the .dll file for you.</span></span> <span data-ttu-id="d8577-129">Toutefois, si vous recevez un composant logiciel enfichable sous la forme d’un fichier. dll, vous pouvez l’inscrire sur votre système.</span><span class="sxs-lookup"><span data-stu-id="d8577-129">However, if you receive a snap-in as a .dll file, you can register it on your system.</span></span> <span data-ttu-id="d8577-130">Pour plus d’informations, voir [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://go.microsoft.com/fwlink/?LinkID=143619) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="d8577-130">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://go.microsoft.com/fwlink/?LinkID=143619) in the MSDN library.</span></span>

<span data-ttu-id="d8577-131">Pour obtenir tous les composants logiciels enfichables inscrits sur votre système ou pour vérifier qu’un composant logiciel enfichable est inscrit, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-131">To get all the registered snap-ins on your system or to verify that a snap-in is registered, type:</span></span>

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a><span data-ttu-id="d8577-132">AJOUT DU COMPOSANT LOGICIEL ENFICHABLE À LA SESSION ACTIVE</span><span class="sxs-lookup"><span data-stu-id="d8577-132">ADDING THE SNAP-IN TO THE CURRENT SESSION</span></span>

<span data-ttu-id="d8577-133">Pour ajouter un composant logiciel enfichable inscrit à la session active, utilisez l’applet de commande Add-PsSnapin.</span><span class="sxs-lookup"><span data-stu-id="d8577-133">To add a registered snap-in to the current session, use the Add-PsSnapin cmdlet.</span></span> <span data-ttu-id="d8577-134">Par exemple, pour ajouter le composant logiciel enfichable Microsoft SQL Server à la session, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-134">For example, to add the Microsoft SQL Server snap-in to the session, type:</span></span>

```powershell
Add-PSSnapin sql
```

<span data-ttu-id="d8577-135">Une fois la commande terminée, les fournisseurs et les applets de commande du composant logiciel enfichable sont disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="d8577-135">After the command is completed, the providers and cmdlets in the snap-in are available in the session.</span></span> <span data-ttu-id="d8577-136">Toutefois, elles ne sont disponibles que dans la session active, sauf si vous les enregistrez.</span><span class="sxs-lookup"><span data-stu-id="d8577-136">However, they are available only in the current session unless you save them.</span></span>

### <a name="saving-the-snap-ins"></a><span data-ttu-id="d8577-137">ENREGISTREMENT DES COMPOSANTS LOGICIELS ENFICHABLES</span><span class="sxs-lookup"><span data-stu-id="d8577-137">SAVING THE SNAP-INS</span></span>

<span data-ttu-id="d8577-138">Pour utiliser un composant logiciel enfichable dans de futures sessions Windows PowerShell, ajoutez la commande Add-PsSnapin à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-138">To use a snap-in in future Windows PowerShell sessions, add the Add-PsSnapin command to your Windows PowerShell profile.</span></span> <span data-ttu-id="d8577-139">Ou, exportez les noms des composants logiciels enfichables dans un fichier de console.</span><span class="sxs-lookup"><span data-stu-id="d8577-139">Or, export the snap-in names to a console file.</span></span>

<span data-ttu-id="d8577-140">Si vous ajoutez la commande Add-PSSnapin à votre profil, elle est disponible dans toutes les futures sessions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-140">If you add the Add-PSSnapin command to your profile, it is available in all future Windows PowerShell sessions.</span></span> <span data-ttu-id="d8577-141">Si vous exportez les noms des composants logiciels enfichables dans votre session, vous pouvez utiliser le fichier d’exportation uniquement lorsque vous avez besoin des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="d8577-141">If you export the names of the snap-ins in your session, you can use the export file only when you need the snap-ins.</span></span>

<span data-ttu-id="d8577-142">Pour ajouter la commande Add-PsSnapin à votre profil Windows PowerShell, ouvrez votre profil, collez ou tapez la commande, puis enregistrez le profil.</span><span class="sxs-lookup"><span data-stu-id="d8577-142">To add the Add-PsSnapin command to your Windows PowerShell profile, open your profile, paste or type the command, and then save the profile.</span></span> <span data-ttu-id="d8577-143">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="d8577-143">For more information, see about_Profiles.</span></span>

<span data-ttu-id="d8577-144">Pour enregistrer les composants logiciels enfichables à partir d’une session dans le fichier de console (. psc1), utilisez l’applet de commande Export-Console.</span><span class="sxs-lookup"><span data-stu-id="d8577-144">To save the snap-ins from a session in console file (.psc1), use the Export-Console cmdlet.</span></span> <span data-ttu-id="d8577-145">Par exemple, pour enregistrer les composants logiciels enfichables dans la configuration de session active dans le fichier NewConsole. psc1 dans le répertoire actif, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-145">For example, to save the snap-ins in the current session configuration to the NewConsole.psc1 file in the current directory, type:</span></span>

```powershell
Export-Console NewConsole
```

<span data-ttu-id="d8577-146">Pour plus d’informations, consultez Export-Console.</span><span class="sxs-lookup"><span data-stu-id="d8577-146">For more information, see Export-Console.</span></span>

### <a name="opening-windows-powershell-with-a-console-file"></a><span data-ttu-id="d8577-147">OUVERTURE DE WINDOWS POWERSHELL AVEC UN FICHIER DE CONSOLE</span><span class="sxs-lookup"><span data-stu-id="d8577-147">OPENING WINDOWS POWERSHELL WITH A CONSOLE FILE</span></span>

<span data-ttu-id="d8577-148">Pour utiliser un fichier de console qui comprend le composant logiciel enfichable, démarrez Windows PowerShell (PowerShell.exe) à partir de l’invite de commandes dans Cmd.exe ou dans une autre session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-148">To use a console file that includes the snap-in, start Windows PowerShell (PowerShell.exe) from the command prompt in Cmd.exe or in another Windows PowerShell session.</span></span> <span data-ttu-id="d8577-149">Utilisez le paramètre PsConsoleFile pour spécifier le fichier de console qui contient le composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="d8577-149">Use the PsConsoleFile parameter to specify the console file that includes the snap-in.</span></span> <span data-ttu-id="d8577-150">Par exemple, la commande suivante démarre Windows PowerShell avec le fichier de console NewConsole. psc1 :</span><span class="sxs-lookup"><span data-stu-id="d8577-150">For example, the following command starts Windows PowerShell with the NewConsole.psc1 console file:</span></span>

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

<span data-ttu-id="d8577-151">Les fournisseurs et les applets de commande du composant logiciel enfichable peuvent désormais être utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="d8577-151">The providers and cmdlets in the snapin are now available for use in the session.</span></span>

### <a name="removing-a-snap-in"></a><span data-ttu-id="d8577-152">SUPPRESSION D’UN COMPOSANT LOGICIEL ENFICHABLE</span><span class="sxs-lookup"><span data-stu-id="d8577-152">REMOVING A SNAP-IN</span></span>

<span data-ttu-id="d8577-153">Pour supprimer un composant logiciel enfichable Windows PowerShell de la session active, utilisez l’applet de commande Remove-PsSnapin.</span><span class="sxs-lookup"><span data-stu-id="d8577-153">To remove a Windows PowerShell snap-in from the current session, use the Remove-PsSnapin cmdlet.</span></span> <span data-ttu-id="d8577-154">Par exemple, pour supprimer le composant logiciel enfichable SQL Server de la session active, tapez :</span><span class="sxs-lookup"><span data-stu-id="d8577-154">For example, to remove the SQL Server snap-in from the current session, type:</span></span>

```powershell
Remove-PSSnapin sql
```

<span data-ttu-id="d8577-155">Cette applet de commande supprime le composant logiciel enfichable de la session.</span><span class="sxs-lookup"><span data-stu-id="d8577-155">This cmdlet removes the snap-in from the session.</span></span> <span data-ttu-id="d8577-156">Le composant logiciel enfichable est toujours chargé, mais les fournisseurs et les applets de commande qu’il prend en charge ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="d8577-156">The snap-in is still loaded, but the providers and cmdlets that it supports are no longer available.</span></span>

### <a name="built-in-commands"></a><span data-ttu-id="d8577-157">COMMANDES INTÉGRÉES</span><span class="sxs-lookup"><span data-stu-id="d8577-157">BUILT-IN COMMANDS</span></span>

<span data-ttu-id="d8577-158">Dans Windows PowerShell 2,0 et dans les anciens programmes hôtes de Windows PowerShell 3,0 et versions ultérieures, les commandes intégrées qui sont installées avec Windows PowerShell sont empaquetées dans des composants logiciels enfichables qui sont ajoutés automatiquement à chaque session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-158">In Windows PowerShell 2.0 and in older-style host programs in Windows PowerShell 3.0 and later, the built-in commands that are installed with Windows PowerShell are packaged in snap-ins that are added automatically to every Windows PowerShell session.</span></span>

<span data-ttu-id="d8577-159">À compter de Windows PowerShell 3,0, dans les programmes hôtes de style plus récents, ceux qui démarrent des sessions à l’aide de la méthode InitialSessionState. CreateDefault2, les commandes intégrées sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="d8577-159">Beginning in Windows PowerShell 3.0, in newer-style host programs -- those that start sessions by using the InitialSessionState.CreateDefault2 method -- the built-in commands are packaged in modules.</span></span> <span data-ttu-id="d8577-160">L’exception est Microsoft. PowerShell. Core, qui apparaît toujours comme un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="d8577-160">The exception is Microsoft.PowerShell.Core, which always appears as a snap-in.</span></span> <span data-ttu-id="d8577-161">Le composant logiciel enfichable principal est inclus dans chaque session par défaut.</span><span class="sxs-lookup"><span data-stu-id="d8577-161">The Core snap-in is included in every session by default.</span></span> <span data-ttu-id="d8577-162">Les modules intégrés sont chargés automatiquement lors de la première utilisation.</span><span class="sxs-lookup"><span data-stu-id="d8577-162">The built-in modules are loaded automatically on first-use.</span></span>

<span data-ttu-id="d8577-163">Remarque : les sessions à distance, y compris les sessions qui sont démarrées à l’aide de l’applet de commande New-PSSession, sont des sessions de style plus anciennes dans lesquelles les commandes intégrées sont empaquetées dans des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="d8577-163">NOTE: Remote sessions, including sessions that are started by using the New-PSSession cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="d8577-164">Les composants logiciels enfichables (ou modules) suivants sont installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-164">The following snap-ins (or modules) are installed with Windows PowerShell.</span></span>

- <span data-ttu-id="d8577-165">Microsoft. PowerShell. Core : contient les fournisseurs et les applets de commande utilisés pour gérer les fonctionnalités de base de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8577-165">Microsoft.PowerShell.Core - Contains providers and cmdlets used to manage the basic features of Windows PowerShell.</span></span> <span data-ttu-id="d8577-166">Il comprend le système de fichiers, le registre, les alias, l’environnement, la fonction et les fournisseurs de variables, ainsi que les applets de commande de base, telles que obtenir-aide, obtenir-commande et obtenir l’historique.</span><span class="sxs-lookup"><span data-stu-id="d8577-166">It includes the FileSystem, Registry, Alias, Environment, Function, and Variable providers and basic cmdlets like Get-Help, Get-Command, and Get-History.</span></span>

- <span data-ttu-id="d8577-167">Microsoft. PowerShell. Host-contient des applets de commande utilisées par l’hôte Windows PowerShell, telles que Start-Transcript et Stop-Transcript.</span><span class="sxs-lookup"><span data-stu-id="d8577-167">Microsoft.PowerShell.Host - Contains cmdlets used by the Windows PowerShell host, such as Start-Transcript and Stop-Transcript.</span></span>

- <span data-ttu-id="d8577-168">Microsoft. PowerShell. Management : contient des applets de commande, telles que Get-Service et Get-ChildItem, qui sont utilisées pour gérer les fonctionnalités Windows.</span><span class="sxs-lookup"><span data-stu-id="d8577-168">Microsoft.PowerShell.Management - Contains cmdlets such as Get-Service and Get-ChildItem that are used to manage Windows-based features.</span></span>

- <span data-ttu-id="d8577-169">Microsoft. PowerShell. Security : contient le fournisseur de certificats et les applets de commande utilisés pour gérer la sécurité Windows PowerShell, tels que l’applet de commande, l’applet de commande, l’applet de commande, l’applet de commande et le contrôle ConvertTo-SecureString.</span><span class="sxs-lookup"><span data-stu-id="d8577-169">Microsoft.PowerShell.Security - Contains the Certificate provider and cmdlets used to manage Windows PowerShell security, such as Get-Acl, Get-AuthenticodeSignature, and ConvertTo-SecureString.</span></span>

- <span data-ttu-id="d8577-170">Microsoft. PowerShell. Utility-contient des applets de commande qui permettent de manipuler des objets et des données, tels que l’applet de commande, l’accès en écriture et la liste de formats.</span><span class="sxs-lookup"><span data-stu-id="d8577-170">Microsoft.PowerShell.Utility - Contains cmdlets used to manipulate objects and data, such as Get-Member, Write-Host, and Format-List.</span></span>

- <span data-ttu-id="d8577-171">Microsoft. WSMan. Management : contient le fournisseur WSMan et les applets de commande qui gèrent le service Windows Remote Management, comme Connect-WSMan et Enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="d8577-171">Microsoft.WSMan.Management - Contains the WSMan provider and cmdlets that manage the Windows Remote Management service, such as Connect-WSMan and Enable-WSManCredSSP.</span></span>

## <a name="logging-snap-in-events"></a><span data-ttu-id="d8577-172">ÉVÉNEMENTS DU COMPOSANT LOGICIEL ENFICHABLE JOURNALISATION</span><span class="sxs-lookup"><span data-stu-id="d8577-172">LOGGING SNAP-IN EVENTS</span></span>

<span data-ttu-id="d8577-173">À compter de Windows PowerShell 3,0, vous pouvez enregistrer les événements d’exécution des applets de commande dans les modules et les composants logiciels enfichables Windows PowerShell en affectant la valeur TRUE à la propriété LogPipelineExecutionDetails des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="d8577-173">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="d8577-174">Pour plus d’informations, consultez [about_EventLogs](about_EventLogs.md).</span><span class="sxs-lookup"><span data-stu-id="d8577-174">For more information, see [about_EventLogs](about_EventLogs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8577-175">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="d8577-175">SEE ALSO</span></span>

[<span data-ttu-id="d8577-176">Add-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="d8577-176">Add-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[<span data-ttu-id="d8577-177">Obtient-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="d8577-177">Get-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[<span data-ttu-id="d8577-178">Remove-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="d8577-178">Remove-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[<span data-ttu-id="d8577-179">Export-Console</span><span class="sxs-lookup"><span data-stu-id="d8577-179">Export-Console</span></span>](xref:Microsoft.PowerShell.Core.Export-Console)

[<span data-ttu-id="d8577-180">Get-Command</span><span class="sxs-lookup"><span data-stu-id="d8577-180">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="d8577-181">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="d8577-181">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="d8577-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="d8577-182">about_Modules</span></span>](about_Modules.md)

## <a name="keywords"></a><span data-ttu-id="d8577-183">MOT</span><span class="sxs-lookup"><span data-stu-id="d8577-183">KEYWORDS</span></span>

<span data-ttu-id="d8577-184">about_Snapins, about_Snap_ins, about_Snap-ins</span><span class="sxs-lookup"><span data-stu-id="d8577-184">about_Snapins, about_Snap_ins, about_Snap-ins</span></span>
