---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: a221c6126bbbf22dffb493828f759bcbd4cfe759
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205817"
---
# <span data-ttu-id="54ae7-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="54ae7-103">Start-Process</span></span>

## <span data-ttu-id="54ae7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="54ae7-104">SYNOPSIS</span></span>
<span data-ttu-id="54ae7-105">Démarre un ou plusieurs processus sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="54ae7-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="54ae7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="54ae7-106">SYNTAX</span></span>

### <span data-ttu-id="54ae7-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="54ae7-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="54ae7-108">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="54ae7-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="54ae7-109">Description</span><span class="sxs-lookup"><span data-stu-id="54ae7-109">DESCRIPTION</span></span>

<span data-ttu-id="54ae7-110">L' `Start-Process` applet de commande démarre un ou plusieurs processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="54ae7-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="54ae7-111">Par défaut, `Start-Process` crée un nouveau processus qui hérite de toutes les variables d’environnement définies dans le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="54ae7-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="54ae7-112">Pour spécifier le programme qui s'exécute dans le processus, entrez un fichier exécutable, un fichier de script ou un fichier qui peut s'ouvrir à l'aide d'un programme sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="54ae7-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="54ae7-113">Si vous spécifiez un fichier non exécutable, `Start-Process` démarre le programme associé au fichier, similaire à l’applet de commande `Invoke-Item` .</span><span class="sxs-lookup"><span data-stu-id="54ae7-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="54ae7-114">Vous pouvez utiliser les paramètres de `Start-Process` pour spécifier des options, telles que le chargement d’un profil utilisateur, le démarrage du processus dans une nouvelle fenêtre ou l’utilisation d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="54ae7-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="54ae7-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="54ae7-115">EXAMPLES</span></span>

### <span data-ttu-id="54ae7-116">Exemple 1 : démarrer un processus qui utilise des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="54ae7-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="54ae7-117">Cet exemple démarre un processus qui utilise le `Sort.exe` fichier dans le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="54ae7-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="54ae7-118">La commande utilise toutes les valeurs par défaut, y compris le style de fenêtre par défaut, le dossier de travail et les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="54ae7-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="54ae7-119">Exemple 2 : imprimer un fichier texte</span><span class="sxs-lookup"><span data-stu-id="54ae7-119">Example 2: Print a text file</span></span>

<span data-ttu-id="54ae7-120">Cet exemple démarre un processus qui imprime le `C:\PS-Test\MyFile.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="54ae7-121">Exemple 3 : démarrer un processus pour trier des éléments dans un nouveau fichier</span><span class="sxs-lookup"><span data-stu-id="54ae7-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="54ae7-122">Cet exemple démarre un processus qui trie des éléments dans le `Testsort.txt` fichier et retourne les éléments triés dans les `Sorted.txt` fichiers.</span><span class="sxs-lookup"><span data-stu-id="54ae7-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="54ae7-123">Toutes les erreurs sont écrites dans le `SortError.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="54ae7-124">Le paramètre **UseNewEnvironment** spécifie que le processus s’exécute avec ses propres variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="54ae7-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="54ae7-125">Exemple 4 : démarrer un processus dans une fenêtre agrandie</span><span class="sxs-lookup"><span data-stu-id="54ae7-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="54ae7-126">Cet exemple démarre le `Notepad.exe` processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="54ae7-127">Elle agrandit la fenêtre et la conserve tant que l'exécution du processus n'est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="54ae7-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="54ae7-128">Exemple 5 : Démarrer PowerShell en tant qu’administrateur</span><span class="sxs-lookup"><span data-stu-id="54ae7-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="54ae7-129">Cet exemple démarre PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="54ae7-130">Exemple 6 : utilisation de différents verbes pour démarrer un processus</span><span class="sxs-lookup"><span data-stu-id="54ae7-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="54ae7-131">Cet exemple montre comment trouver les verbes qui peuvent être utilisés lors du démarrage d’un processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="54ae7-132">Les verbes disponibles sont déterminés par l’extension de nom de fichier du fichier qui s’exécute dans le processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="54ae7-133">L’exemple utilise `New-Object` pour créer un objet **System. Diagnostics. ProcessStartInfo** pour **PowerShell.exe** , le fichier qui s’exécute dans le processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54ae7-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="54ae7-134">La propriété **Verbs** de l’objet **ProcessStartInfo** montre que vous pouvez utiliser les verbes **Open** et **runas** avec `PowerShell.exe` , ou avec n’importe quel processus qui exécute un `.exe` fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="54ae7-135">Exemple 7 : spécification d’arguments pour le processus</span><span class="sxs-lookup"><span data-stu-id="54ae7-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="54ae7-136">Les deux commandes démarrent l’interpréteur de commandes Windows, en émettant une `dir` commande sur le `Program Files` dossier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="54ae7-137">Étant donné que ce NomDossier contient un espace, la valeur doit être entourée de guillemets avec séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="54ae7-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="54ae7-138">Notez que la première commande spécifie une chaîne en tant que **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-138">Note that the first command specifies a string as **ArgumentList** .</span></span> <span data-ttu-id="54ae7-139">La deuxième commande est un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="54ae7-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## <span data-ttu-id="54ae7-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54ae7-140">PARAMETERS</span></span>

### <span data-ttu-id="54ae7-141">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="54ae7-141">-ArgumentList</span></span>

<span data-ttu-id="54ae7-142">Spécifie des paramètres ou des valeurs de paramètre à utiliser lorsque cette applet de commande démarre le processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-142">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="54ae7-143">Les arguments peuvent être acceptés comme une chaîne unique avec les arguments séparés par des espaces, ou comme un tableau de chaînes séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="54ae7-143">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="54ae7-144">Si des paramètres ou des valeurs de paramètre contiennent un espace, ils doivent être placés entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="54ae7-144">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="54ae7-145">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="54ae7-145">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="54ae7-146">-Credential</span></span>

<span data-ttu-id="54ae7-147">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="54ae7-147">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="54ae7-148">Par défaut, l'applet de commande utilise les informations d'identification de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="54ae7-148">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="54ae7-149">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="54ae7-149">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="54ae7-150">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="54ae7-150">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="54ae7-151">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="54ae7-151">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="54ae7-152">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="54ae7-152">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-153">-FilePath</span><span class="sxs-lookup"><span data-stu-id="54ae7-153">-FilePath</span></span>

<span data-ttu-id="54ae7-154">Spécifie le chemin d’accès et le nom de fichier facultatifs du programme qui s’exécute dans le processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-154">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="54ae7-155">Entrez le nom d’un fichier exécutable ou d’un document, tel qu’un `.txt` fichier ou `.doc` , associé à un programme sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="54ae7-155">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="54ae7-156">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="54ae7-156">This parameter is required.</span></span>

<span data-ttu-id="54ae7-157">Si vous spécifiez uniquement un nom de fichier, utilisez le paramètre **WorkingDirectory** pour spécifier le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="54ae7-157">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-158">-LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="54ae7-158">-LoadUserProfile</span></span>

<span data-ttu-id="54ae7-159">Indique que cette applet de commande charge le profil utilisateur Windows stocké dans la `HKEY_USERS` clé de registre de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="54ae7-159">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="54ae7-160">Le paramètre ne s’applique pas aux systèmes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="54ae7-160">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="54ae7-161">Ce paramètre n’affecte pas les profils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54ae7-161">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="54ae7-162">Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="54ae7-162">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-163">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="54ae7-163">-NoNewWindow</span></span>

<span data-ttu-id="54ae7-164">Démarrez le nouveau processus dans la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="54ae7-164">Start the new process in the current console window.</span></span> <span data-ttu-id="54ae7-165">Par défaut sur Windows, PowerShell ouvre une nouvelle fenêtre.</span><span class="sxs-lookup"><span data-stu-id="54ae7-165">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="54ae7-166">Sur les systèmes non-Windows, vous n’accédez jamais à une nouvelle fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="54ae7-166">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="54ae7-167">Vous ne pouvez pas utiliser les paramètres **NoNewWindow** et **WindowStyle** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="54ae7-167">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="54ae7-168">Le paramètre ne s’applique pas aux systèmes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="54ae7-168">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-169">-PassThru</span><span class="sxs-lookup"><span data-stu-id="54ae7-169">-PassThru</span></span>

<span data-ttu-id="54ae7-170">Retourne un objet processus pour chaque processus démarré par l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="54ae7-170">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="54ae7-171">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="54ae7-171">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-172">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="54ae7-172">-RedirectStandardError</span></span>

<span data-ttu-id="54ae7-173">Spécifie un fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-173">Specifies a file.</span></span> <span data-ttu-id="54ae7-174">Cette applet de commande envoie toutes les erreurs générées par le processus à un fichier que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="54ae7-174">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="54ae7-175">Entrez le chemin d’accès et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-175">Enter the path and filename.</span></span> <span data-ttu-id="54ae7-176">Par défaut, les erreurs s'affichent dans la console.</span><span class="sxs-lookup"><span data-stu-id="54ae7-176">By default, the errors are displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-177">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="54ae7-177">-RedirectStandardInput</span></span>

<span data-ttu-id="54ae7-178">Spécifie un fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-178">Specifies a file.</span></span> <span data-ttu-id="54ae7-179">Cette applet de commande lit les entrées du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="54ae7-179">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="54ae7-180">Entrez le chemin d’accès et le nom du fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="54ae7-180">Enter the path and filename of the input file.</span></span> <span data-ttu-id="54ae7-181">Par défaut, le processus obtient son entrée à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-181">By default, the process gets its input from the keyboard.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-182">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="54ae7-182">-RedirectStandardOutput</span></span>

<span data-ttu-id="54ae7-183">Spécifie un fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-183">Specifies a file.</span></span> <span data-ttu-id="54ae7-184">Cette applet de commande envoie la sortie générée par le processus à un fichier que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="54ae7-184">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="54ae7-185">Entrez le chemin d’accès et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-185">Enter the path and filename.</span></span> <span data-ttu-id="54ae7-186">Par défaut, la sortie s'affiche dans la console.</span><span class="sxs-lookup"><span data-stu-id="54ae7-186">By default, the output is displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-187">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="54ae7-187">-UseNewEnvironment</span></span>

<span data-ttu-id="54ae7-188">Indique que cette applet de commande utilise les nouvelles variables d’environnement spécifiées pour le processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-188">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="54ae7-189">Par défaut, le processus démarré s’exécute avec les variables d’environnement héritées du processus parent.</span><span class="sxs-lookup"><span data-stu-id="54ae7-189">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-190">-Verbe</span><span class="sxs-lookup"><span data-stu-id="54ae7-190">-Verb</span></span>

<span data-ttu-id="54ae7-191">Spécifie un verbe à utiliser lorsque cette applet de commande démarre le processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-191">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="54ae7-192">Les verbes disponibles sont déterminés par l’extension de nom de fichier du fichier qui s’exécute dans le processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-192">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="54ae7-193">Le tableau suivant répertorie les verbes pour quelques types de fichiers de processus courants.</span><span class="sxs-lookup"><span data-stu-id="54ae7-193">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="54ae7-194">Type de fichier</span><span class="sxs-lookup"><span data-stu-id="54ae7-194">File type</span></span> |                <span data-ttu-id="54ae7-195">Verbes et adverbes</span><span class="sxs-lookup"><span data-stu-id="54ae7-195">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="54ae7-196">.cmd</span><span class="sxs-lookup"><span data-stu-id="54ae7-196">.cmd</span></span>      | <span data-ttu-id="54ae7-197">Modifier, ouvrir, imprimer, RunAs, nom_d’emprunt</span><span class="sxs-lookup"><span data-stu-id="54ae7-197">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="54ae7-198">.exe</span><span class="sxs-lookup"><span data-stu-id="54ae7-198">.exe</span></span>      | <span data-ttu-id="54ae7-199">Open, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="54ae7-199">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="54ae7-200">.txt</span><span class="sxs-lookup"><span data-stu-id="54ae7-200">.txt</span></span>      | <span data-ttu-id="54ae7-201">Ouvrir, imprimer, PrintTo</span><span class="sxs-lookup"><span data-stu-id="54ae7-201">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="54ae7-202">.wav</span><span class="sxs-lookup"><span data-stu-id="54ae7-202">.wav</span></span>      | <span data-ttu-id="54ae7-203">Ouvrir, lire</span><span class="sxs-lookup"><span data-stu-id="54ae7-203">Open, Play</span></span>                          |

<span data-ttu-id="54ae7-204">Pour trouver les verbes qui peuvent être utilisés avec le fichier qui s’exécute dans un processus, utilisez l' `New-Object` applet de commande pour créer un objet **System. Diagnostics. ProcessStartInfo** pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="54ae7-204">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="54ae7-205">Les verbes disponibles se trouvent dans la propriété **Verbs** de l’objet **ProcessStartInfo** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-205">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="54ae7-206">Pour plus de détails, consultez les exemples.</span><span class="sxs-lookup"><span data-stu-id="54ae7-206">For details, see the examples.</span></span>

<span data-ttu-id="54ae7-207">Le paramètre ne s’applique pas aux systèmes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="54ae7-207">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-208">-Wait</span><span class="sxs-lookup"><span data-stu-id="54ae7-208">-Wait</span></span>

<span data-ttu-id="54ae7-209">Indique que cette applet de commande attend que le processus spécifié et ses descendants se terminent avant d’accepter une autre entrée.</span><span class="sxs-lookup"><span data-stu-id="54ae7-209">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="54ae7-210">Ce paramètre supprime l’invite de commandes ou conserve la fenêtre jusqu’à ce que les processus se terminent.</span><span class="sxs-lookup"><span data-stu-id="54ae7-210">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-211">-WindowStyle</span><span class="sxs-lookup"><span data-stu-id="54ae7-211">-WindowStyle</span></span>

<span data-ttu-id="54ae7-212">Spécifie l'état de la fenêtre utilisée pour le nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="54ae7-212">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="54ae7-213">Les valeurs acceptables pour ce paramètre sont les suivantes : **normal** , **masqué** , **réduit** et **agrandi** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-213">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized** .</span></span> <span data-ttu-id="54ae7-214">La valeur par défaut est **normal** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-214">The default value is **Normal** .</span></span>

<span data-ttu-id="54ae7-215">Vous ne pouvez pas utiliser les paramètres **WindowStyle** et **NoNewWindow** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="54ae7-215">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="54ae7-216">Le paramètre ne s’applique pas aux systèmes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="54ae7-216">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-217">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="54ae7-217">-WorkingDirectory</span></span>

<span data-ttu-id="54ae7-218">Spécifie l’emplacement dans lequel le nouveau processus doit commencer.</span><span class="sxs-lookup"><span data-stu-id="54ae7-218">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="54ae7-219">La valeur par défaut est l’emplacement du fichier exécutable ou du document en cours de démarrage.</span><span class="sxs-lookup"><span data-stu-id="54ae7-219">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="54ae7-220">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="54ae7-220">Wildcards are not supported.</span></span> <span data-ttu-id="54ae7-221">Le nom du chemin d’accès ne doit pas contenir de caractères qui seraient interprétés comme des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="54ae7-221">The path name must not contain characters that would be interpreted as wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-222">-Confirm</span><span class="sxs-lookup"><span data-stu-id="54ae7-222">-Confirm</span></span>

<span data-ttu-id="54ae7-223">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="54ae7-223">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-224">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="54ae7-224">-WhatIf</span></span>

<span data-ttu-id="54ae7-225">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="54ae7-225">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="54ae7-226">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="54ae7-226">The cmdlet is not run.</span></span>

<span data-ttu-id="54ae7-227">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="54ae7-227">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54ae7-228">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54ae7-228">CommonParameters</span></span>

<span data-ttu-id="54ae7-229">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54ae7-229">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54ae7-230">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="54ae7-230">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="54ae7-231">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="54ae7-231">INPUTS</span></span>

### <span data-ttu-id="54ae7-232">Aucun</span><span class="sxs-lookup"><span data-stu-id="54ae7-232">None</span></span>

<span data-ttu-id="54ae7-233">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="54ae7-233">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="54ae7-234">SORTIES</span><span class="sxs-lookup"><span data-stu-id="54ae7-234">OUTPUTS</span></span>

### <span data-ttu-id="54ae7-235">Aucun, System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="54ae7-235">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="54ae7-236">Cette applet de commande génère un objet **System. Diagnostics. Process** , si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-236">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="54ae7-237">Sinon, cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="54ae7-237">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="54ae7-238">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="54ae7-238">NOTES</span></span>

- <span data-ttu-id="54ae7-239">Cette applet de commande est implémentée à l’aide de la méthode **Start** de la classe **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-239">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="54ae7-240">Pour plus d’informations sur cette méthode, consultez [méthode Process. Start](/dotnet/api/system.diagnostics.process.start#overloads).</span><span class="sxs-lookup"><span data-stu-id="54ae7-240">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="54ae7-241">Sur Windows, quand vous utilisez **UseNewEnvironment** , le nouveau processus démarre uniquement les variables d’environnement par défaut définies pour la portée de l' **ordinateur** .</span><span class="sxs-lookup"><span data-stu-id="54ae7-241">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="54ae7-242">Cela a pour effet d’affecter la `$env:USERNAME` valeur **système** à.</span><span class="sxs-lookup"><span data-stu-id="54ae7-242">This has the side affect that the `$env:USERNAME` is set to **SYSTEM** .</span></span> <span data-ttu-id="54ae7-243">Aucune des variables de l’étendue de l' **utilisateur** n’est incluse.</span><span class="sxs-lookup"><span data-stu-id="54ae7-243">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="54ae7-244">Sur Windows, le cas d’utilisation le plus courant de `Start-Process` est d’utiliser le paramètre **Wait** pour bloquer la progression jusqu’à ce que le nouveau processus se termine.</span><span class="sxs-lookup"><span data-stu-id="54ae7-244">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="54ae7-245">Sur un système non-Windows, cela est rarement nécessaire, car le comportement par défaut pour les applications en ligne de commande est équivalent à `Start-Process -Wait` .</span><span class="sxs-lookup"><span data-stu-id="54ae7-245">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="54ae7-246">Si `Start-Process` vous utilisez sur des systèmes autres que Windows, vous n’avez jamais une nouvelle fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="54ae7-246">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="54ae7-247">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="54ae7-247">RELATED LINKS</span></span>

[<span data-ttu-id="54ae7-248">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="54ae7-248">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="54ae7-249">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="54ae7-249">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="54ae7-250">Get-Process</span><span class="sxs-lookup"><span data-stu-id="54ae7-250">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="54ae7-251">Start-Service</span><span class="sxs-lookup"><span data-stu-id="54ae7-251">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="54ae7-252">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="54ae7-252">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="54ae7-253">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="54ae7-253">Wait-Process</span></span>](Wait-Process.md)
