---
description: Décrit comment exécuter et écrire des scripts dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: c877627f8caeab8309326826caa4ec13d65d5d9d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206709"
---
# <a name="about-scripts"></a><span data-ttu-id="39a99-104">À propos des scripts</span><span class="sxs-lookup"><span data-stu-id="39a99-104">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="39a99-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="39a99-105">Short description</span></span>
<span data-ttu-id="39a99-106">Décrit comment exécuter et écrire des scripts dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39a99-106">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="39a99-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="39a99-107">Long description</span></span>

<span data-ttu-id="39a99-108">Un script est un fichier texte brut qui contient une ou plusieurs commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39a99-108">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="39a99-109">Les scripts PowerShell ont une `.ps1` extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="39a99-109">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="39a99-110">L’exécution d’un script ressemble beaucoup à l’exécution d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="39a99-110">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="39a99-111">Vous tapez le chemin d’accès et le nom de fichier du script et utilisez des paramètres pour envoyer des données et définir des options.</span><span class="sxs-lookup"><span data-stu-id="39a99-111">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="39a99-112">Vous pouvez exécuter des scripts sur votre ordinateur ou dans une session à distance sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="39a99-112">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="39a99-113">L’écriture d’un script enregistre une commande en vue d’une utilisation ultérieure et facilite le partage avec d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="39a99-113">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="39a99-114">Plus important encore, il vous permet d’exécuter les commandes simplement en tapant le chemin d’accès du script et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="39a99-114">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="39a99-115">Les scripts peuvent être aussi simples qu’une seule commande dans un fichier ou aussi étendu qu’un programme complexe.</span><span class="sxs-lookup"><span data-stu-id="39a99-115">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="39a99-116">Les scripts ont des fonctionnalités supplémentaires, telles que le `#Requires` commentaire spécial, l’utilisation de paramètres, la prise en charge des sections de données et la signature numérique pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="39a99-116">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="39a99-117">Vous pouvez également écrire des rubriques d’aide pour les scripts et pour toutes les fonctions du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-117">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="39a99-118">Comment exécuter un script</span><span class="sxs-lookup"><span data-stu-id="39a99-118">How to run a script</span></span>

<span data-ttu-id="39a99-119">Avant de pouvoir exécuter un script sur Windows, vous devez modifier la stratégie d’exécution PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="39a99-119">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="39a99-120">La stratégie d’exécution ne s’applique pas à PowerShell s’exécutant sur des plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="39a99-120">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="39a99-121">La stratégie d’exécution par défaut, `Restricted` , empêche l’exécution de tous les scripts, y compris les scripts que vous écrivez sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="39a99-121">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="39a99-122">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-122">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="39a99-123">La stratégie d’exécution étant enregistrée dans le registre, vous ne devez la modifier qu’une seule fois sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="39a99-123">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="39a99-124">Pour modifier la stratégie d’exécution, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="39a99-124">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="39a99-125">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="39a99-125">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="39a99-126">ou</span><span class="sxs-lookup"><span data-stu-id="39a99-126">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="39a99-127">La modification prend effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="39a99-127">The change is effective immediately.</span></span>

<span data-ttu-id="39a99-128">Pour exécuter un script, tapez le nom complet et le chemin d’accès complet au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="39a99-128">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="39a99-129">Par exemple, pour exécuter le script Get-ServiceLog.ps1 dans le répertoire C:\Scripts, tapez :</span><span class="sxs-lookup"><span data-stu-id="39a99-129">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="39a99-130">Pour exécuter un script dans le répertoire actif, tapez le chemin d’accès au répertoire actif ou utilisez un point pour représenter le répertoire actif, suivi d’une barre oblique inverse ( `.\` ).</span><span class="sxs-lookup"><span data-stu-id="39a99-130">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="39a99-131">Par exemple, pour exécuter le script ServicesLog.ps1 dans le répertoire local, tapez :</span><span class="sxs-lookup"><span data-stu-id="39a99-131">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="39a99-132">Si le script contient des paramètres, tapez les paramètres et les valeurs de paramètre après le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-132">If the script has parameters, type the parameters and parameter values after the script filename.</span></span>

<span data-ttu-id="39a99-133">Par exemple, la commande suivante utilise le paramètre ServiceName du script Get-ServiceLog pour demander un journal de l’activité du service WinRM.</span><span class="sxs-lookup"><span data-stu-id="39a99-133">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="39a99-134">En tant que fonctionnalité de sécurité, PowerShell n’exécute pas de scripts lorsque vous double-cliquez sur l’icône de script dans l’Explorateur de fichiers ou lorsque vous tapez le nom du script sans chemin d’accès complet, même si le script se trouve dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="39a99-134">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="39a99-135">Pour plus d’informations sur l’exécution de commandes et de scripts dans PowerShell, consultez [about_Command_Precedence](about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-135">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="39a99-136">Exécuter avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="39a99-136">Run with PowerShell</span></span>

<span data-ttu-id="39a99-137">À compter de PowerShell 3,0, vous pouvez exécuter des scripts à partir de l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="39a99-137">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="39a99-138">Pour utiliser la fonctionnalité « exécuter avec PowerShell » :</span><span class="sxs-lookup"><span data-stu-id="39a99-138">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="39a99-139">Exécutez l’Explorateur de fichiers, cliquez avec le bouton droit sur le nom de fichier du script, puis sélectionnez exécuter avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39a99-139">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="39a99-140">La fonctionnalité « exécuter avec PowerShell » est conçue pour exécuter des scripts qui n’ont pas de paramètres requis et ne renvoient pas de sortie à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="39a99-140">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="39a99-141">Pour plus d'informations, consultez [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-141">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="39a99-142">Exécution de scripts sur d’autres ordinateurs</span><span class="sxs-lookup"><span data-stu-id="39a99-142">Running scripts on other computers</span></span>

<span data-ttu-id="39a99-143">Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre **filePath** de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="39a99-143">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="39a99-144">Entrez le chemin d’accès et le nom de fichier du script en tant que valeur du paramètre **filePath** .</span><span class="sxs-lookup"><span data-stu-id="39a99-144">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="39a99-145">Le script doit résider sur l'ordinateur local ou dans un répertoire auquel celui-ci peut accéder.</span><span class="sxs-lookup"><span data-stu-id="39a99-145">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="39a99-146">La commande suivante exécute le `Get-ServiceLog.ps1` script sur les ordinateurs distants nommés SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="39a99-146">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="39a99-147">Obtenir de l’aide pour les scripts</span><span class="sxs-lookup"><span data-stu-id="39a99-147">Get help for scripts</span></span>

<span data-ttu-id="39a99-148">L’applet de commande Get-Help obtient les rubriques d’aide pour les scripts, ainsi que pour les applets de commande et autres types de commandes.</span><span class="sxs-lookup"><span data-stu-id="39a99-148">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="39a99-149">Pour obtenir la rubrique d’aide d’un script, tapez `Get-Help` suivi du chemin d’accès et du nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-149">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="39a99-150">Si le chemin d’accès du script se trouve dans votre `Path` variable d’environnement, vous pouvez omettre le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="39a99-150">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="39a99-151">Par exemple, pour obtenir de l’aide pour le script ServicesLog.ps1, tapez :</span><span class="sxs-lookup"><span data-stu-id="39a99-151">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="39a99-152">Comment écrire un script</span><span class="sxs-lookup"><span data-stu-id="39a99-152">How to write a script</span></span>

<span data-ttu-id="39a99-153">Un script peut contenir toutes les commandes PowerShell valides, y compris les commandes uniques, les commandes qui utilisent le pipeline, les fonctions et les structures de contrôle telles que les instructions If et les boucles for.</span><span class="sxs-lookup"><span data-stu-id="39a99-153">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="39a99-154">Pour écrire un script, ouvrez un nouveau fichier dans un éditeur de texte, tapez les commandes et enregistrez-les dans un fichier avec un nom de fichier valide avec l' `.ps1` extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="39a99-154">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="39a99-155">L’exemple suivant est un script simple qui obtient les services qui s’exécutent sur le système actuel et les enregistre dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="39a99-155">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="39a99-156">Le nom du fichier journal est créé à partir de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="39a99-156">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="39a99-157">Pour créer ce script, ouvrez un éditeur de texte ou un éditeur de script, tapez ces commandes, puis enregistrez-les dans un fichier nommé `ServiceLog.ps1` .</span><span class="sxs-lookup"><span data-stu-id="39a99-157">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="39a99-158">Paramètres dans les scripts</span><span class="sxs-lookup"><span data-stu-id="39a99-158">Parameters in scripts</span></span>

<span data-ttu-id="39a99-159">Pour définir des paramètres dans un script, utilisez une instruction param.</span><span class="sxs-lookup"><span data-stu-id="39a99-159">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="39a99-160">L' `Param` instruction doit être la première instruction d’un script, à l’exception des commentaires et des `#Require` instructions.</span><span class="sxs-lookup"><span data-stu-id="39a99-160">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="39a99-161">Les paramètres de script fonctionnent comme les paramètres de fonction.</span><span class="sxs-lookup"><span data-stu-id="39a99-161">Script parameters work like function parameters.</span></span> <span data-ttu-id="39a99-162">Les valeurs des paramètres sont disponibles pour toutes les commandes dans le script.</span><span class="sxs-lookup"><span data-stu-id="39a99-162">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="39a99-163">Toutes les fonctionnalités des paramètres de fonction, y compris l’attribut de paramètre et ses arguments nommés, sont également valides dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="39a99-163">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="39a99-164">Lors de l’exécution du script, les utilisateurs de script tapent les paramètres après le nom du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-164">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="39a99-165">L’exemple suivant montre un `Test-Remote.ps1` script qui a un paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="39a99-165">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="39a99-166">Les deux fonctions de script peuvent accéder à la valeur du paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="39a99-166">Both of the script functions can access the **ComputerName** parameter value.</span></span>

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

<span data-ttu-id="39a99-167">Pour exécuter ce script, tapez le nom du paramètre après le nom du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-167">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="39a99-168">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="39a99-168">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="39a99-169">Pour plus d’informations sur l’instruction param et les paramètres de fonction, consultez [about_Functions](about_Functions.md) et [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-169">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="39a99-170">Écriture de l’aide pour les scripts</span><span class="sxs-lookup"><span data-stu-id="39a99-170">Writing help for scripts</span></span>

<span data-ttu-id="39a99-171">Vous pouvez écrire une rubrique d’aide pour un script à l’aide de l’une des deux méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="39a99-171">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="39a99-172">Aide Comment-Based pour les scripts</span><span class="sxs-lookup"><span data-stu-id="39a99-172">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="39a99-173">Créez une rubrique d’aide en utilisant des mots clés spéciaux dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="39a99-173">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="39a99-174">Pour créer une aide basée sur des commentaires pour un script, les commentaires doivent être placés au début ou à la fin du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="39a99-174">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="39a99-175">Pour plus d’informations sur l’aide basée sur les commentaires, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-175">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="39a99-176">Aide XML-Based pour les scripts</span><span class="sxs-lookup"><span data-stu-id="39a99-176">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="39a99-177">Créez une rubrique d’aide XML, telle que le type qui est généralement créé pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="39a99-177">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="39a99-178">L’aide XML est requise si vous traduisez des rubriques d’aide en plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="39a99-178">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="39a99-179">Pour associer le script à la rubrique d’aide basée sur XML, utilisez le. Mot clé d’aide commentaire ExternalHelp.</span><span class="sxs-lookup"><span data-stu-id="39a99-179">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="39a99-180">Pour plus d’informations sur le mot clé commentaire ExternalHelp, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-180">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="39a99-181">Pour plus d’informations sur l’aide XML, consultez [Comment écrire l’aide sur les applets de](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)commande.</span><span class="sxs-lookup"><span data-stu-id="39a99-181">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="39a99-182">Retour d’une valeur de sortie</span><span class="sxs-lookup"><span data-stu-id="39a99-182">Returning an exit value</span></span>

<span data-ttu-id="39a99-183">Par défaut, les scripts ne retournent pas d’état de sortie lorsque le script se termine.</span><span class="sxs-lookup"><span data-stu-id="39a99-183">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="39a99-184">Vous devez utiliser l' `exit` instruction pour retourner un code de sortie à partir d’un script.</span><span class="sxs-lookup"><span data-stu-id="39a99-184">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="39a99-185">Par défaut, l' `exit` instruction retourne `0` .</span><span class="sxs-lookup"><span data-stu-id="39a99-185">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="39a99-186">Vous pouvez fournir une valeur numérique pour retourner un état de sortie différent.</span><span class="sxs-lookup"><span data-stu-id="39a99-186">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="39a99-187">Un code de sortie différent de zéro signale généralement un échec.</span><span class="sxs-lookup"><span data-stu-id="39a99-187">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="39a99-188">Sur Windows, toute valeur comprise entre `[int]::MinValue` et `[int]::MaxValue` est autorisée.</span><span class="sxs-lookup"><span data-stu-id="39a99-188">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>

<span data-ttu-id="39a99-189">Sur UNIX, seuls les nombres positifs compris entre `[byte]::MinValue` (0) et `[byte]::MaxValue` (255) sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="39a99-189">On Unix, only positive numbers between `[byte]::MinValue` (0) and `[byte]::MaxValue` (255) are allowed.</span></span> <span data-ttu-id="39a99-190">Un nombre négatif dans la plage de `-1` par `-255` est automatiquement converti en nombre positif en ajoutant</span><span class="sxs-lookup"><span data-stu-id="39a99-190">A negative number in the range of `-1` through `-255` is automatically translated into a positive number by adding</span></span>
256. <span data-ttu-id="39a99-191">Par exemple, `-2` est transformé en `254` .</span><span class="sxs-lookup"><span data-stu-id="39a99-191">For example, `-2` is transformed to `254`.</span></span>

<span data-ttu-id="39a99-192">Dans PowerShell, l' `exit` instruction définit la valeur de la `$LASTEXITCODE` variable.</span><span class="sxs-lookup"><span data-stu-id="39a99-192">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="39a99-193">Dans l’interface de commande Windows (cmd.exe), l’instruction Exit définit la valeur de la `%ERRORLEVEL%` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="39a99-193">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="39a99-194">Tout argument qui n’est pas numérique ou qui se trouve en dehors de la plage spécifique à la plateforme est traduit en valeur de `0` .</span><span class="sxs-lookup"><span data-stu-id="39a99-194">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="39a99-195">Étendue de script et source de points</span><span class="sxs-lookup"><span data-stu-id="39a99-195">Script scope and dot sourcing</span></span>

<span data-ttu-id="39a99-196">Chaque script s’exécute dans sa propre étendue.</span><span class="sxs-lookup"><span data-stu-id="39a99-196">Each script runs in its own scope.</span></span> <span data-ttu-id="39a99-197">Les fonctions, les variables, les alias et les lecteurs créés dans le script existent uniquement dans l’étendue du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-197">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="39a99-198">Vous ne pouvez pas accéder à ces éléments ou à leurs valeurs dans l’étendue dans laquelle le script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="39a99-198">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="39a99-199">Pour exécuter un script dans une autre étendue, vous pouvez spécifier une étendue, telle que global ou local, ou vous pouvez pointer le script à la source.</span><span class="sxs-lookup"><span data-stu-id="39a99-199">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="39a99-200">La fonctionnalité de source de points vous permet d’exécuter un script dans l’étendue actuelle plutôt que dans la portée du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-200">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="39a99-201">Quand vous exécutez un script qui a la forme d’un point, les commandes du script s’exécutent comme si vous les aviez tapées à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="39a99-201">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="39a99-202">Les fonctions, les variables, les alias et les lecteurs créés par le script sont créés dans l’étendue dans laquelle vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="39a99-202">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="39a99-203">Une fois le script exécuté, vous pouvez utiliser les éléments créés et accéder à leurs valeurs dans votre session.</span><span class="sxs-lookup"><span data-stu-id="39a99-203">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="39a99-204">Pour un script de source de point, tapez un point (.) et un espace avant le chemin du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-204">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="39a99-205">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="39a99-205">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="39a99-206">or</span><span class="sxs-lookup"><span data-stu-id="39a99-206">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="39a99-207">Une fois le `UtilityFunctions.ps1` script exécuté, les fonctions et les variables créées par le script sont ajoutées à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="39a99-207">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="39a99-208">Par exemple, le `UtilityFunctions.ps1` script crée la `New-Profile` fonction et la `$ProfileName` variable.</span><span class="sxs-lookup"><span data-stu-id="39a99-208">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

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

<span data-ttu-id="39a99-209">Si vous exécutez le `UtilityFunctions.ps1` script dans sa propre étendue de script, la `New-Profile` fonction et la `$ProfileName` variable existent uniquement lorsque le script est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="39a99-209">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="39a99-210">Lorsque le script se termine, la fonction et la variable sont supprimées, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="39a99-210">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

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

<span data-ttu-id="39a99-211">Lorsque vous pointez le script source et que vous l’exécutez, le script crée la `New-Profile` fonction et la `$ProfileName` variable de votre session dans votre portée.</span><span class="sxs-lookup"><span data-stu-id="39a99-211">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="39a99-212">Une fois le script exécuté, vous pouvez utiliser la `New-Profile` fonction dans votre session, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="39a99-212">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

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

<span data-ttu-id="39a99-213">Pour plus d’informations sur l’étendue, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="39a99-213">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="39a99-214">Scripts dans les modules</span><span class="sxs-lookup"><span data-stu-id="39a99-214">Scripts in modules</span></span>

<span data-ttu-id="39a99-215">Un module est un ensemble de ressources PowerShell associées qui peuvent être distribuées en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="39a99-215">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="39a99-216">Vous pouvez utiliser des modules pour organiser vos scripts, fonctions et autres ressources.</span><span class="sxs-lookup"><span data-stu-id="39a99-216">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="39a99-217">Vous pouvez également utiliser des modules pour distribuer votre code à d’autres utilisateurs et pour récupérer du code à partir de sources approuvées.</span><span class="sxs-lookup"><span data-stu-id="39a99-217">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="39a99-218">Vous pouvez inclure des scripts dans vos modules, ou vous pouvez créer un module de script, qui est un module qui se compose entièrement ou principalement d’un script et de ressources de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="39a99-218">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="39a99-219">Un module de script est simplement un script avec une extension de fichier. psm1.</span><span class="sxs-lookup"><span data-stu-id="39a99-219">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="39a99-220">Pour plus d’informations sur les modules, consultez [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-220">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="39a99-221">Autres fonctionnalités de script</span><span class="sxs-lookup"><span data-stu-id="39a99-221">Other script features</span></span>

<span data-ttu-id="39a99-222">PowerShell offre de nombreuses fonctionnalités utiles que vous pouvez utiliser dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="39a99-222">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="39a99-223">`#Requires` -Vous pouvez utiliser une `#Requires` instruction pour empêcher l’exécution d’un script sans modules ou composants logiciels enfichables spécifiés et une version spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39a99-223">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="39a99-224">Pour plus d’informations, consultez about_Requires.</span><span class="sxs-lookup"><span data-stu-id="39a99-224">For more information, see about_Requires.</span></span>

- <span data-ttu-id="39a99-225">`$PSCommandPath` -Contient le chemin d’accès complet et le nom du script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="39a99-225">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="39a99-226">Ce paramètre est valide dans tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="39a99-226">This parameter is valid in all scripts.</span></span> <span data-ttu-id="39a99-227">Cette variable automatique est introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="39a99-227">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="39a99-228">`$PSScriptRoot` -Contient le répertoire à partir duquel un script est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="39a99-228">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="39a99-229">Dans PowerShell 2,0, cette variable est valide uniquement dans les modules de script ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="39a99-229">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="39a99-230">À compter de PowerShell 3,0, il est valide dans tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="39a99-230">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="39a99-231">`$MyInvocation` -La `$MyInvocation` variable automatique contient des informations sur le script en cours, y compris des informations sur la façon dont il a été démarré ou « appelé ».</span><span class="sxs-lookup"><span data-stu-id="39a99-231">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="39a99-232">Vous pouvez utiliser cette variable et ses propriétés pour obtenir des informations sur le script pendant son exécution.</span><span class="sxs-lookup"><span data-stu-id="39a99-232">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="39a99-233">Par exemple, `$MyInvocation` . La variable MyCommand. Path contient le chemin d’accès et le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="39a99-233">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="39a99-234">`$MyInvocation`. La ligne contient la commande qui a démarré le script, y compris tous les paramètres et les valeurs.</span><span class="sxs-lookup"><span data-stu-id="39a99-234">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="39a99-235">À compter de PowerShell 3,0, `$MyInvocation` possède deux nouvelles propriétés qui fournissent des informations sur le script qui a appelé ou appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="39a99-235">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="39a99-236">Les valeurs de ces propriétés sont remplies uniquement lorsque le demandeur ou l’appelant est un script.</span><span class="sxs-lookup"><span data-stu-id="39a99-236">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="39a99-237">**PSCommandPath** contient le chemin d’accès complet et le nom du script qui a appelé ou appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="39a99-237">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="39a99-238">**PSScriptRoot** contient le répertoire du script qui a appelé ou appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="39a99-238">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="39a99-239">Contrairement aux `$PSCommandPath` `$PSScriptRoot` variables automatiques et, qui contiennent des informations sur le script en cours, les propriétés **PSCommandPath** et **PSScriptRoot** de la `$MyInvocation` variable contiennent des informations sur le script qui a appelé le script actuel.</span><span class="sxs-lookup"><span data-stu-id="39a99-239">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="39a99-240">Sections de données : vous pouvez utiliser le `Data` mot clé pour séparer les données de la logique dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="39a99-240">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="39a99-241">Les sections de données peuvent également faciliter la localisation.</span><span class="sxs-lookup"><span data-stu-id="39a99-241">Data sections can also make localization easier.</span></span> <span data-ttu-id="39a99-242">Pour plus d’informations, consultez [about_Data_Sections](about_Data_Sections.md) et [about_Script_Internationalization](about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-242">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="39a99-243">Signature de script : vous pouvez ajouter une signature numérique à un script.</span><span class="sxs-lookup"><span data-stu-id="39a99-243">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="39a99-244">Selon la stratégie d’exécution, vous pouvez utiliser des signatures numériques pour limiter l’exécution de scripts pouvant inclure des commandes non sécurisées.</span><span class="sxs-lookup"><span data-stu-id="39a99-244">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="39a99-245">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md) et [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="39a99-245">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39a99-246">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39a99-246">See also</span></span>

[<span data-ttu-id="39a99-247">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="39a99-247">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="39a99-248">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="39a99-248">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="39a99-249">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="39a99-249">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="39a99-250">about_Functions</span><span class="sxs-lookup"><span data-stu-id="39a99-250">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="39a99-251">about_Modules</span><span class="sxs-lookup"><span data-stu-id="39a99-251">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="39a99-252">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="39a99-252">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="39a99-253">about_Requires</span><span class="sxs-lookup"><span data-stu-id="39a99-253">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="39a99-254">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="39a99-254">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="39a99-255">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="39a99-255">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="39a99-256">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="39a99-256">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="39a99-257">about_Signing</span><span class="sxs-lookup"><span data-stu-id="39a99-257">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="39a99-258">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="39a99-258">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
