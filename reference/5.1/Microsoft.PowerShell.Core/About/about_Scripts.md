---
description: Décrit comment exécuter et écrire des scripts dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: f91319db98ac3108f3a780814a0e80bdf5bc6f4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207917"
---
# <a name="about-scripts"></a><span data-ttu-id="adb02-104">À propos des scripts</span><span class="sxs-lookup"><span data-stu-id="adb02-104">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="adb02-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="adb02-105">Short description</span></span>
<span data-ttu-id="adb02-106">Décrit comment exécuter et écrire des scripts dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adb02-106">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="adb02-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="adb02-107">Long description</span></span>

<span data-ttu-id="adb02-108">Un script est un fichier texte brut qui contient une ou plusieurs commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adb02-108">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="adb02-109">Les scripts PowerShell ont une `.ps1` extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="adb02-109">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="adb02-110">L’exécution d’un script ressemble beaucoup à l’exécution d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="adb02-110">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="adb02-111">Vous tapez le chemin d’accès et le nom de fichier du script et utilisez des paramètres pour envoyer des données et définir des options.</span><span class="sxs-lookup"><span data-stu-id="adb02-111">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="adb02-112">Vous pouvez exécuter des scripts sur votre ordinateur ou dans une session à distance sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="adb02-112">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="adb02-113">L’écriture d’un script enregistre une commande en vue d’une utilisation ultérieure et facilite le partage avec d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="adb02-113">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="adb02-114">Plus important encore, il vous permet d’exécuter les commandes simplement en tapant le chemin d’accès du script et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="adb02-114">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="adb02-115">Les scripts peuvent être aussi simples qu’une seule commande dans un fichier ou aussi étendu qu’un programme complexe.</span><span class="sxs-lookup"><span data-stu-id="adb02-115">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="adb02-116">Les scripts ont des fonctionnalités supplémentaires, telles que le `#Requires` commentaire spécial, l’utilisation de paramètres, la prise en charge des sections de données et la signature numérique pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="adb02-116">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="adb02-117">Vous pouvez également écrire des rubriques d’aide pour les scripts et pour toutes les fonctions du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-117">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="adb02-118">Comment exécuter un script</span><span class="sxs-lookup"><span data-stu-id="adb02-118">How to run a script</span></span>

<span data-ttu-id="adb02-119">Avant de pouvoir exécuter un script sur Windows, vous devez modifier la stratégie d’exécution PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="adb02-119">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="adb02-120">La stratégie d’exécution ne s’applique pas à PowerShell s’exécutant sur des plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="adb02-120">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="adb02-121">La stratégie d’exécution par défaut, `Restricted` , empêche l’exécution de tous les scripts, y compris les scripts que vous écrivez sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="adb02-121">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="adb02-122">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-122">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="adb02-123">La stratégie d’exécution étant enregistrée dans le registre, vous ne devez la modifier qu’une seule fois sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="adb02-123">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="adb02-124">Pour modifier la stratégie d’exécution, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="adb02-124">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="adb02-125">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="adb02-125">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="adb02-126">ou</span><span class="sxs-lookup"><span data-stu-id="adb02-126">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="adb02-127">La modification prend effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="adb02-127">The change is effective immediately.</span></span>

<span data-ttu-id="adb02-128">Pour exécuter un script, tapez le nom complet et le chemin d’accès complet au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="adb02-128">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="adb02-129">Par exemple, pour exécuter le script Get-ServiceLog.ps1 dans le répertoire C:\Scripts, tapez :</span><span class="sxs-lookup"><span data-stu-id="adb02-129">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="adb02-130">Pour exécuter un script dans le répertoire actif, tapez le chemin d’accès au répertoire actif ou utilisez un point pour représenter le répertoire actif, suivi d’une barre oblique inverse ( `.\` ).</span><span class="sxs-lookup"><span data-stu-id="adb02-130">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="adb02-131">Par exemple, pour exécuter le script ServicesLog.ps1 dans le répertoire local, tapez :</span><span class="sxs-lookup"><span data-stu-id="adb02-131">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="adb02-132">Si le script contient des paramètres, tapez les paramètres et les valeurs de paramètre après le nom du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="adb02-132">If the script has parameters, type the parameters and parameter values after the script file name.</span></span>

<span data-ttu-id="adb02-133">Par exemple, la commande suivante utilise le paramètre ServiceName du script Get-ServiceLog pour demander un journal de l’activité du service WinRM.</span><span class="sxs-lookup"><span data-stu-id="adb02-133">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="adb02-134">En tant que fonctionnalité de sécurité, PowerShell n’exécute pas de scripts lorsque vous double-cliquez sur l’icône de script dans l’Explorateur de fichiers ou lorsque vous tapez le nom du script sans chemin d’accès complet, même si le script se trouve dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="adb02-134">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="adb02-135">Pour plus d’informations sur l’exécution de commandes et de scripts dans PowerShell, consultez [about_Command_Precedence](about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-135">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="adb02-136">Exécuter avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="adb02-136">Run with PowerShell</span></span>

<span data-ttu-id="adb02-137">À compter de PowerShell 3,0, vous pouvez exécuter des scripts à partir de l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="adb02-137">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="adb02-138">Pour utiliser la fonctionnalité « exécuter avec PowerShell » :</span><span class="sxs-lookup"><span data-stu-id="adb02-138">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="adb02-139">Exécutez l’Explorateur de fichiers, cliquez avec le bouton droit sur le nom de fichier du script, puis sélectionnez exécuter avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adb02-139">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="adb02-140">La fonctionnalité « exécuter avec PowerShell » est conçue pour exécuter des scripts qui n’ont pas de paramètres requis et ne renvoient pas de sortie à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="adb02-140">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="adb02-141">Pour plus d'informations, consultez [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-141">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="adb02-142">Exécution de scripts sur d’autres ordinateurs</span><span class="sxs-lookup"><span data-stu-id="adb02-142">Running scripts on other computers</span></span>

<span data-ttu-id="adb02-143">Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre **filePath** de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="adb02-143">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="adb02-144">Entrez le chemin d’accès et le nom de fichier du script en tant que valeur du paramètre **filePath** .</span><span class="sxs-lookup"><span data-stu-id="adb02-144">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="adb02-145">Le script doit résider sur l'ordinateur local ou dans un répertoire auquel celui-ci peut accéder.</span><span class="sxs-lookup"><span data-stu-id="adb02-145">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="adb02-146">La commande suivante exécute le `Get-ServiceLog.ps1` script sur les ordinateurs distants nommés SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="adb02-146">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="adb02-147">Obtenir de l’aide pour les scripts</span><span class="sxs-lookup"><span data-stu-id="adb02-147">Get help for scripts</span></span>

<span data-ttu-id="adb02-148">L’applet de commande Get-Help obtient les rubriques d’aide pour les scripts, ainsi que pour les applets de commande et autres types de commandes.</span><span class="sxs-lookup"><span data-stu-id="adb02-148">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="adb02-149">Pour obtenir la rubrique d’aide d’un script, tapez `Get-Help` suivi du chemin d’accès et du nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-149">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="adb02-150">Si le chemin d’accès du script se trouve dans votre `Path` variable d’environnement, vous pouvez omettre le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="adb02-150">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="adb02-151">Par exemple, pour obtenir de l’aide pour le script ServicesLog.ps1, tapez :</span><span class="sxs-lookup"><span data-stu-id="adb02-151">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="adb02-152">Comment écrire un script</span><span class="sxs-lookup"><span data-stu-id="adb02-152">How to write a script</span></span>

<span data-ttu-id="adb02-153">Un script peut contenir toutes les commandes PowerShell valides, y compris les commandes uniques, les commandes qui utilisent le pipeline, les fonctions et les structures de contrôle telles que les instructions If et les boucles for.</span><span class="sxs-lookup"><span data-stu-id="adb02-153">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="adb02-154">Pour écrire un script, ouvrez un nouveau fichier dans un éditeur de texte, tapez les commandes et enregistrez-les dans un fichier avec un nom de fichier valide avec l' `.ps1` extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="adb02-154">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="adb02-155">L’exemple suivant est un script simple qui obtient les services qui s’exécutent sur le système actuel et les enregistre dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="adb02-155">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="adb02-156">Le nom du fichier journal est créé à partir de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="adb02-156">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="adb02-157">Pour créer ce script, ouvrez un éditeur de texte ou un éditeur de script, tapez ces commandes, puis enregistrez-les dans un fichier nommé `ServiceLog.ps1` .</span><span class="sxs-lookup"><span data-stu-id="adb02-157">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="adb02-158">Paramètres dans les scripts</span><span class="sxs-lookup"><span data-stu-id="adb02-158">Parameters in scripts</span></span>

<span data-ttu-id="adb02-159">Pour définir des paramètres dans un script, utilisez une instruction param.</span><span class="sxs-lookup"><span data-stu-id="adb02-159">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="adb02-160">L' `Param` instruction doit être la première instruction d’un script, à l’exception des commentaires et des `#Require` instructions.</span><span class="sxs-lookup"><span data-stu-id="adb02-160">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="adb02-161">Les paramètres de script fonctionnent comme les paramètres de fonction.</span><span class="sxs-lookup"><span data-stu-id="adb02-161">Script parameters work like function parameters.</span></span> <span data-ttu-id="adb02-162">Les valeurs des paramètres sont disponibles pour toutes les commandes dans le script.</span><span class="sxs-lookup"><span data-stu-id="adb02-162">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="adb02-163">Toutes les fonctionnalités des paramètres de fonction, y compris l’attribut de paramètre et ses arguments nommés, sont également valides dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="adb02-163">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="adb02-164">Lors de l’exécution du script, les utilisateurs de script tapent les paramètres après le nom du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-164">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="adb02-165">L’exemple suivant montre un `Test-Remote.ps1` script qui a un paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="adb02-165">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="adb02-166">Les deux fonctions de script peuvent accéder à la valeur du paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="adb02-166">Both of the script functions can access the **ComputerName** parameter value.</span></span>

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

<span data-ttu-id="adb02-167">Pour exécuter ce script, tapez le nom du paramètre après le nom du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-167">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="adb02-168">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="adb02-168">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="adb02-169">Pour plus d’informations sur l’instruction param et les paramètres de fonction, consultez [about_Functions](about_Functions.md) et [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-169">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="adb02-170">Écriture de l’aide pour les scripts</span><span class="sxs-lookup"><span data-stu-id="adb02-170">Writing help for scripts</span></span>

<span data-ttu-id="adb02-171">Vous pouvez écrire une rubrique d’aide pour un script à l’aide de l’une des deux méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="adb02-171">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="adb02-172">Aide Comment-Based pour les scripts</span><span class="sxs-lookup"><span data-stu-id="adb02-172">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="adb02-173">Créez une rubrique d’aide en utilisant des mots clés spéciaux dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="adb02-173">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="adb02-174">Pour créer une aide basée sur des commentaires pour un script, les commentaires doivent être placés au début ou à la fin du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="adb02-174">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="adb02-175">Pour plus d’informations sur l’aide basée sur les commentaires, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-175">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="adb02-176">Aide XML-Based pour les scripts</span><span class="sxs-lookup"><span data-stu-id="adb02-176">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="adb02-177">Créez une rubrique d’aide XML, telle que le type qui est généralement créé pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="adb02-177">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="adb02-178">L’aide XML est requise si vous traduisez des rubriques d’aide en plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="adb02-178">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="adb02-179">Pour associer le script à la rubrique d’aide basée sur XML, utilisez le. Mot clé d’aide commentaire ExternalHelp.</span><span class="sxs-lookup"><span data-stu-id="adb02-179">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="adb02-180">Pour plus d’informations sur le mot clé commentaire ExternalHelp, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-180">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="adb02-181">Pour plus d’informations sur l’aide XML, consultez [Comment écrire l’aide sur les applets de](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)commande.</span><span class="sxs-lookup"><span data-stu-id="adb02-181">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="adb02-182">Retour d’une valeur de sortie</span><span class="sxs-lookup"><span data-stu-id="adb02-182">Returning an exit value</span></span>

<span data-ttu-id="adb02-183">Par défaut, les scripts ne retournent pas d’état de sortie lorsque le script se termine.</span><span class="sxs-lookup"><span data-stu-id="adb02-183">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="adb02-184">Vous devez utiliser l' `exit` instruction pour retourner un code de sortie à partir d’un script.</span><span class="sxs-lookup"><span data-stu-id="adb02-184">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="adb02-185">Par défaut, l' `exit` instruction retourne `0` .</span><span class="sxs-lookup"><span data-stu-id="adb02-185">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="adb02-186">Vous pouvez fournir une valeur numérique pour retourner un état de sortie différent.</span><span class="sxs-lookup"><span data-stu-id="adb02-186">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="adb02-187">Un code de sortie différent de zéro signale généralement un échec.</span><span class="sxs-lookup"><span data-stu-id="adb02-187">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="adb02-188">Sur Windows, toute valeur comprise entre `[int]::MinValue` et `[int]::MaxValue` est autorisée.</span><span class="sxs-lookup"><span data-stu-id="adb02-188">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>


<span data-ttu-id="adb02-189">Dans PowerShell, l' `exit` instruction définit la valeur de la `$LASTEXITCODE` variable.</span><span class="sxs-lookup"><span data-stu-id="adb02-189">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="adb02-190">Dans l’interface de commande Windows (cmd.exe), l’instruction Exit définit la valeur de la `%ERRORLEVEL%` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="adb02-190">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="adb02-191">Tout argument qui n’est pas numérique ou qui se trouve en dehors de la plage spécifique à la plateforme est traduit en valeur de `0` .</span><span class="sxs-lookup"><span data-stu-id="adb02-191">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="adb02-192">Étendue de script et source de points</span><span class="sxs-lookup"><span data-stu-id="adb02-192">Script scope and dot sourcing</span></span>

<span data-ttu-id="adb02-193">Chaque script s’exécute dans sa propre étendue.</span><span class="sxs-lookup"><span data-stu-id="adb02-193">Each script runs in its own scope.</span></span> <span data-ttu-id="adb02-194">Les fonctions, les variables, les alias et les lecteurs créés dans le script existent uniquement dans l’étendue du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-194">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="adb02-195">Vous ne pouvez pas accéder à ces éléments ou à leurs valeurs dans l’étendue dans laquelle le script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="adb02-195">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="adb02-196">Pour exécuter un script dans une autre étendue, vous pouvez spécifier une étendue, telle que global ou local, ou vous pouvez pointer le script à la source.</span><span class="sxs-lookup"><span data-stu-id="adb02-196">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="adb02-197">La fonctionnalité de source de points vous permet d’exécuter un script dans l’étendue actuelle plutôt que dans la portée du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-197">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="adb02-198">Quand vous exécutez un script qui a la forme d’un point, les commandes du script s’exécutent comme si vous les aviez tapées à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="adb02-198">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="adb02-199">Les fonctions, les variables, les alias et les lecteurs créés par le script sont créés dans l’étendue dans laquelle vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="adb02-199">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="adb02-200">Une fois le script exécuté, vous pouvez utiliser les éléments créés et accéder à leurs valeurs dans votre session.</span><span class="sxs-lookup"><span data-stu-id="adb02-200">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="adb02-201">Pour un script de source de point, tapez un point (.) et un espace avant le chemin du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-201">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="adb02-202">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="adb02-202">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="adb02-203">or</span><span class="sxs-lookup"><span data-stu-id="adb02-203">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="adb02-204">Une fois le `UtilityFunctions.ps1` script exécuté, les fonctions et les variables créées par le script sont ajoutées à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="adb02-204">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="adb02-205">Par exemple, le `UtilityFunctions.ps1` script crée la `New-Profile` fonction et la `$ProfileName` variable.</span><span class="sxs-lookup"><span data-stu-id="adb02-205">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

<span data-ttu-id="adb02-206">Si vous exécutez le `UtilityFunctions.ps1` script dans sa propre étendue de script, la `New-Profile` fonction et la `$ProfileName` variable existent uniquement lorsque le script est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="adb02-206">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="adb02-207">Lorsque le script se termine, la fonction et la variable sont supprimées, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="adb02-207">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

<span data-ttu-id="adb02-208">Lorsque vous pointez le script source et que vous l’exécutez, le script crée la `New-Profile` fonction et la `$ProfileName` variable de votre session dans votre portée.</span><span class="sxs-lookup"><span data-stu-id="adb02-208">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="adb02-209">Une fois le script exécuté, vous pouvez utiliser la `New-Profile` fonction dans votre session, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="adb02-209">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

<span data-ttu-id="adb02-210">Pour plus d’informations sur l’étendue, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="adb02-210">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="adb02-211">Scripts dans les modules</span><span class="sxs-lookup"><span data-stu-id="adb02-211">Scripts in modules</span></span>

<span data-ttu-id="adb02-212">Un module est un ensemble de ressources PowerShell associées qui peuvent être distribuées en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="adb02-212">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="adb02-213">Vous pouvez utiliser des modules pour organiser vos scripts, fonctions et autres ressources.</span><span class="sxs-lookup"><span data-stu-id="adb02-213">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="adb02-214">Vous pouvez également utiliser des modules pour distribuer votre code à d’autres utilisateurs et pour récupérer du code à partir de sources approuvées.</span><span class="sxs-lookup"><span data-stu-id="adb02-214">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="adb02-215">Vous pouvez inclure des scripts dans vos modules, ou vous pouvez créer un module de script, qui est un module qui se compose entièrement ou principalement d’un script et de ressources de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="adb02-215">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="adb02-216">Un module de script est simplement un script avec une extension de fichier. psm1.</span><span class="sxs-lookup"><span data-stu-id="adb02-216">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="adb02-217">Pour plus d’informations sur les modules, consultez [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-217">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="adb02-218">Autres fonctionnalités de script</span><span class="sxs-lookup"><span data-stu-id="adb02-218">Other script features</span></span>

<span data-ttu-id="adb02-219">PowerShell offre de nombreuses fonctionnalités utiles que vous pouvez utiliser dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="adb02-219">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="adb02-220">`#Requires` -Vous pouvez utiliser une `#Requires` instruction pour empêcher l’exécution d’un script sans modules ou composants logiciels enfichables spécifiés et une version spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adb02-220">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="adb02-221">Pour plus d’informations, consultez about_Requires.</span><span class="sxs-lookup"><span data-stu-id="adb02-221">For more information, see about_Requires.</span></span>

- <span data-ttu-id="adb02-222">`$PSCommandPath` -Contient le chemin d’accès complet et le nom du script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="adb02-222">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="adb02-223">Ce paramètre est valide dans tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="adb02-223">This parameter is valid in all scripts.</span></span> <span data-ttu-id="adb02-224">Cette variable automatique est introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="adb02-224">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="adb02-225">`$PSScriptRoot` -Contient le répertoire à partir duquel un script est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="adb02-225">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="adb02-226">Dans PowerShell 2,0, cette variable est valide uniquement dans les modules de script ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="adb02-226">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="adb02-227">À compter de PowerShell 3,0, il est valide dans tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="adb02-227">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="adb02-228">`$MyInvocation` -La `$MyInvocation` variable automatique contient des informations sur le script en cours, y compris des informations sur la façon dont il a été démarré ou « appelé ».</span><span class="sxs-lookup"><span data-stu-id="adb02-228">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="adb02-229">Vous pouvez utiliser cette variable et ses propriétés pour obtenir des informations sur le script pendant son exécution.</span><span class="sxs-lookup"><span data-stu-id="adb02-229">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="adb02-230">Par exemple, `$MyInvocation` . La variable MyCommand. Path contient le chemin d’accès et le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="adb02-230">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="adb02-231">`$MyInvocation`. La ligne contient la commande qui a démarré le script, y compris tous les paramètres et les valeurs.</span><span class="sxs-lookup"><span data-stu-id="adb02-231">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="adb02-232">À compter de PowerShell 3,0, `$MyInvocation` possède deux nouvelles propriétés qui fournissent des informations sur le script qui a appelé ou appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="adb02-232">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="adb02-233">Les valeurs de ces propriétés sont remplies uniquement lorsque le demandeur ou l’appelant est un script.</span><span class="sxs-lookup"><span data-stu-id="adb02-233">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="adb02-234">**PSCommandPath** contient le chemin d’accès complet et le nom du script qui a appelé ou appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="adb02-234">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="adb02-235">**PSScriptRoot** contient le répertoire du script qui a appelé ou appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="adb02-235">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="adb02-236">Contrairement aux `$PSCommandPath` `$PSScriptRoot` variables automatiques et, qui contiennent des informations sur le script en cours, les propriétés **PSCommandPath** et **PSScriptRoot** de la `$MyInvocation` variable contiennent des informations sur le script qui a appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="adb02-236">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="adb02-237">Sections de données : vous pouvez utiliser le `Data` mot clé pour séparer les données de la logique dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="adb02-237">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="adb02-238">Les sections de données peuvent également faciliter la localisation.</span><span class="sxs-lookup"><span data-stu-id="adb02-238">Data sections can also make localization easier.</span></span> <span data-ttu-id="adb02-239">Pour plus d’informations, consultez [about_Data_Sections](about_Data_Sections.md) et [about_Script_Internationalization](about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-239">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="adb02-240">Signature de script : vous pouvez ajouter une signature numérique à un script.</span><span class="sxs-lookup"><span data-stu-id="adb02-240">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="adb02-241">Selon la stratégie d’exécution, vous pouvez utiliser des signatures numériques pour limiter l’exécution de scripts pouvant inclure des commandes non sécurisées.</span><span class="sxs-lookup"><span data-stu-id="adb02-241">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="adb02-242">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md) et [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="adb02-242">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="adb02-243">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adb02-243">See also</span></span>

[<span data-ttu-id="adb02-244">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="adb02-244">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="adb02-245">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="adb02-245">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="adb02-246">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="adb02-246">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="adb02-247">about_Functions</span><span class="sxs-lookup"><span data-stu-id="adb02-247">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="adb02-248">about_Modules</span><span class="sxs-lookup"><span data-stu-id="adb02-248">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="adb02-249">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="adb02-249">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="adb02-250">about_Requires</span><span class="sxs-lookup"><span data-stu-id="adb02-250">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="adb02-251">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="adb02-251">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="adb02-252">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="adb02-252">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="adb02-253">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="adb02-253">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="adb02-254">about_Signing</span><span class="sxs-lookup"><span data-stu-id="adb02-254">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="adb02-255">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="adb02-255">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
