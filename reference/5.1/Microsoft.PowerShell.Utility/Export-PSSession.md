---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 67501a78ba577f63c97e595f4bacd28160fea416
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203302"
---
# <span data-ttu-id="e585b-103">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="e585b-103">Export-PSSession</span></span>

## <span data-ttu-id="e585b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e585b-104">SYNOPSIS</span></span>

<span data-ttu-id="e585b-105">Exporte les commandes d’une autre session et les enregistre dans un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-105">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="e585b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e585b-106">SYNTAX</span></span>

```
Export-PSSession [-Session] <PSSession> [-OutputModule] <string> [[-CommandName] <string[]>]
 [[-FormatTypeName] <string[]>] [-Force] [-Encoding <string>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <string[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-Certificate <X509Certificate2>]
 [<CommonParameters>]
```

## <span data-ttu-id="e585b-107">Description</span><span class="sxs-lookup"><span data-stu-id="e585b-107">DESCRIPTION</span></span>

<span data-ttu-id="e585b-108">L' `Export-PSSession` applet de commande obtient les applets de commande, les fonctions, les alias et d’autres types de commandes à partir d’une autre session PowerShell (PSSession) sur un ordinateur local ou distant et les enregistre dans un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-108">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="e585b-109">Pour ajouter les commandes du module à la session active, utilisez l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="e585b-109">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="e585b-110">Contrairement à `Import-PSSession` , qui importe les commandes d’une autre session PSSession dans la session active, `Export-PSSession` enregistre les commandes dans un module.</span><span class="sxs-lookup"><span data-stu-id="e585b-110">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="e585b-111">Les commandes ne sont pas importées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-111">The commands are not imported into the current session.</span></span>

<span data-ttu-id="e585b-112">Pour exporter des commandes, utilisez l' `New-PSSession` applet de commande pour créer une session PSSession qui contient les commandes que vous souhaitez exporter.</span><span class="sxs-lookup"><span data-stu-id="e585b-112">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="e585b-113">Utilisez ensuite l' `Export-PSSession` applet de commande pour exporter les commandes.</span><span class="sxs-lookup"><span data-stu-id="e585b-113">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="e585b-114">Pour éviter les conflits de noms de commande, la valeur par défaut de `Export-PSSession` est d’exporter toutes les commandes, à l’exception des commandes qui existent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-114">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="e585b-115">Vous pouvez utiliser le paramètre **CommandName** pour spécifier les commandes à exporter.</span><span class="sxs-lookup"><span data-stu-id="e585b-115">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="e585b-116">L' `Export-PSSession` applet de commande utilise la fonctionnalité de communication à distance implicite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-116">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="e585b-117">Lorsque vous importez des commandes dans la session active, elles s’exécutent implicitement dans la session d’origine ou dans une session similaire sur l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="e585b-117">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="e585b-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e585b-118">EXAMPLES</span></span>

### <span data-ttu-id="e585b-119">Exemple 1 : exporter des commandes à partir d’une session PSSession</span><span class="sxs-lookup"><span data-stu-id="e585b-119">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="e585b-120">Cet exemple crée une session PSSession à partir de l’ordinateur local vers l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-120">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="e585b-121">Toutes les commandes, à l’exception de celles qui existent dans la session active, sont exportées vers le module nommé SERVEUR01 sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e585b-121">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="e585b-122">L’exportation comprend les données de mise en forme pour les commandes.</span><span class="sxs-lookup"><span data-stu-id="e585b-122">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="e585b-123">La `New-PSSession` commande crée une session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-123">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="e585b-124">La session PSSession est stockée dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="e585b-124">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="e585b-125">La `Export-PSSession` commande exporte les `$S` commandes et les données de mise en forme de la variable dans le module SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-125">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="e585b-126">Exemple 2 : exporter les commandes extraire et définir</span><span class="sxs-lookup"><span data-stu-id="e585b-126">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="e585b-127">Cet exemple exporte toutes les `Get` `Set` commandes et à partir d’un serveur.</span><span class="sxs-lookup"><span data-stu-id="e585b-127">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="e585b-128">Ces commandes exportent les `Get` `Set` commandes et à partir d’un composant logiciel enfichable Microsoft Exchange Server sur un ordinateur distant vers un module Exchange dans le `$PSHOME\Modules` Répertoire de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e585b-128">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="e585b-129">Le fait de placer le module dans le `$PSHOME\Modules` répertoire le rend accessible à tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e585b-129">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="e585b-130">Exemple 3 : exporter des commandes à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="e585b-130">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="e585b-131">Cet exemple exporte des applets de commande à partir d’une session PSSession sur un ordinateur distant et les enregistre dans un module sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e585b-131">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="e585b-132">Les applets de commande du module sont ajoutées à la session active afin qu’elles puissent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="e585b-132">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="e585b-133">La `New-PSSession` commande crée une session PSSession sur l’ordinateur SERVEUR01 et l’enregistre dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="e585b-133">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="e585b-134">La `Export-PSSession` commande exporte les applets de commande dont les noms commencent par test à partir de la session PSSession dans `$S` le module TestCmdlets sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e585b-134">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="e585b-135">L' `Remove-PSSession` applet de commande supprime la session PSSession dans `$S` de la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-135">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="e585b-136">Cette commande montre que la session PSSession n’a pas besoin d’être active pour utiliser les commandes qui ont été importées à partir de la session.</span><span class="sxs-lookup"><span data-stu-id="e585b-136">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="e585b-137">L' `Import-Module` applet de commande ajoute les applets de commande du module TestCmdlets à la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-137">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="e585b-138">La commande peut être exécutée dans n’importe quelle session à tout moment.</span><span class="sxs-lookup"><span data-stu-id="e585b-138">The command can be run in any session at any time.</span></span>

<span data-ttu-id="e585b-139">L' `Get-Help` applet de commande obtient de l’aide pour les applets de commande dont les noms commencent par test.</span><span class="sxs-lookup"><span data-stu-id="e585b-139">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="e585b-140">Une fois que les commandes d’un module sont ajoutées à la session active, vous pouvez utiliser les `Get-Help` applets de commande et `Get-Command` pour en savoir plus sur les commandes importées.</span><span class="sxs-lookup"><span data-stu-id="e585b-140">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="e585b-141">L' `Test-Files` applet de commande a été exportée à partir de l’ordinateur SERVEUR01 et ajoutée à la session.</span><span class="sxs-lookup"><span data-stu-id="e585b-141">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="e585b-142">L' `Test-Files` applet de commande s’exécute dans une session à distance sur l’ordinateur à partir duquel la commande a été importée.</span><span class="sxs-lookup"><span data-stu-id="e585b-142">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="e585b-143">PowerShell crée une session à partir des informations stockées dans le module TestCmdlets.</span><span class="sxs-lookup"><span data-stu-id="e585b-143">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="e585b-144">Exemple 4 : commandes Export et écrasé dans la session active</span><span class="sxs-lookup"><span data-stu-id="e585b-144">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="e585b-145">Cet exemple exporte les commandes qui sont stockées dans une variable dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-145">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="e585b-146">Cette `Export-PSSession` commande exporte toutes les commandes et toutes les données de mise en forme de la session PSSession dans la `$S` variable vers la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-146">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="e585b-147">Le paramètre **AllowClobber** comprend des commandes portant le même nom que les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-147">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="e585b-148">Exemple 5 : exporter des commandes à partir d’une session PSSession fermée</span><span class="sxs-lookup"><span data-stu-id="e585b-148">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="e585b-149">Cet exemple montre comment exécuter les commandes exportées avec des options spéciales lorsque la session PSSession qui a créé les commandes exportées est fermée.</span><span class="sxs-lookup"><span data-stu-id="e585b-149">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="e585b-150">Si la session à distance d’origine est fermée lors de l’importation d’un module, le module utilisera toute session à distance ouverte qui se connecte à l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="e585b-150">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="e585b-151">S’il n’existe aucune session active sur l’ordinateur d’origine, le module rétablit une session.</span><span class="sxs-lookup"><span data-stu-id="e585b-151">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="e585b-152">Pour exécuter les commandes exportées avec des options spéciales dans une session à distance, vous devez créer une session à distance avec ces options avant d’importer le module.</span><span class="sxs-lookup"><span data-stu-id="e585b-152">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="e585b-153">Utiliser l' `New-PSSession` applet de commande avec le paramètre **SessionOption**</span><span class="sxs-lookup"><span data-stu-id="e585b-153">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="e585b-154">L' `New-PSSessionOption` applet de commande crée un objet **PSSessionOption** et enregistre l’objet dans la `$Options` variable.</span><span class="sxs-lookup"><span data-stu-id="e585b-154">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="e585b-155">La `New-PSSession` commande crée une session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-155">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="e585b-156">Le paramètre **SessionOption** utilise l’objet stocké dans `$Options` .</span><span class="sxs-lookup"><span data-stu-id="e585b-156">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="e585b-157">La session est stockée dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="e585b-157">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="e585b-158">L' `Export-PSSession` applet de commande exporte les commandes de la session PSSession dans `$S` vers le module SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-158">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="e585b-159">L' `Remove-PSSession` applet de commande supprime la session PSSession dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="e585b-159">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="e585b-160">L' `New-PSSession` applet de commande crée une session PSSession qui se connecte à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-160">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="e585b-161">Le paramètre **SessionOption** utilise l’objet stocké dans `$Options` .</span><span class="sxs-lookup"><span data-stu-id="e585b-161">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="e585b-162">L' `Import-Module` applet de commande importe les commandes à partir du module SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-162">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="e585b-163">Les commandes du module sont exécutées dans la session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e585b-163">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="e585b-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e585b-164">PARAMETERS</span></span>

### <span data-ttu-id="e585b-165">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="e585b-165">-AllowClobber</span></span>

<span data-ttu-id="e585b-166">Exporte les commandes spécifiées, même si elles ont les mêmes noms que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-166">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="e585b-167">Si vous exportez une commande portant le même nom qu’une commande dans la session active, la commande exportée masque ou remplace les commandes d’origine.</span><span class="sxs-lookup"><span data-stu-id="e585b-167">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="e585b-168">Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="e585b-168">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="e585b-169">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="e585b-169">-ArgumentList</span></span>

<span data-ttu-id="e585b-170">Exporte la variante de la commande obtenue suite à l'utilisation des arguments spécifiés (valeurs de paramètre).</span><span class="sxs-lookup"><span data-stu-id="e585b-170">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="e585b-171">Par exemple, pour exporter la variante de la `Get-Item` commande dans le certificat (CERT :) dans la session PSSession dans `$S` , tapez `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="e585b-171">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-172">-Certificat</span><span class="sxs-lookup"><span data-stu-id="e585b-172">-Certificate</span></span>

<span data-ttu-id="e585b-173">Spécifie le certificat client utilisé pour signer les fichiers de format (\* .Format.ps1XML) ou les fichiers de module de script (. psm1) dans le module `Export-PSSession` créé par.</span><span class="sxs-lookup"><span data-stu-id="e585b-173">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="e585b-174">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="e585b-174">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="e585b-175">Pour rechercher un certificat, utilisez l' `Get-PfxCertificate` applet de commande ou utilisez l' `Get-ChildItem` applet de commande dans le certificat (CERT :) unités.</span><span class="sxs-lookup"><span data-stu-id="e585b-175">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="e585b-176">Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="e585b-176">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-177">-CommandName</span><span class="sxs-lookup"><span data-stu-id="e585b-177">-CommandName</span></span>

<span data-ttu-id="e585b-178">Exporte uniquement les commandes avec les noms ou les modèles de noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e585b-178">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="e585b-179">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e585b-179">Wildcards are permitted.</span></span> <span data-ttu-id="e585b-180">Utilisez **CommandName** ou son alias, **Name** .</span><span class="sxs-lookup"><span data-stu-id="e585b-180">Use **CommandName** or its alias, **Name** .</span></span>

<span data-ttu-id="e585b-181">Par défaut, `Export-PSSession` exporte toutes les commandes de la session PSSession, à l’exception des commandes qui ont les mêmes noms que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-181">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="e585b-182">Cela empêche les commandes d’être masquées ou remplacées par les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-182">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="e585b-183">Pour exporter toutes les commandes, y compris celles qui masquent ou remplacent d’autres commandes, utilisez le paramètre **AllowClobber** .</span><span class="sxs-lookup"><span data-stu-id="e585b-183">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="e585b-184">Si vous utilisez le paramètre **CommandName** , les fichiers de mise en forme des commandes ne sont pas exportés, sauf si vous utilisez le paramètre **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="e585b-184">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="e585b-185">De même, si vous utilisez le paramètre **FormatTypeName** , aucune commande n’est exportée, sauf si vous utilisez le paramètre **CommandName** .</span><span class="sxs-lookup"><span data-stu-id="e585b-185">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e585b-186">-CommandType</span><span class="sxs-lookup"><span data-stu-id="e585b-186">-CommandType</span></span>

<span data-ttu-id="e585b-187">Exporte uniquement les types spécifiés d'objets de commande.</span><span class="sxs-lookup"><span data-stu-id="e585b-187">Exports only the specified types of command objects.</span></span> <span data-ttu-id="e585b-188">Utilisez **CommandType** ou son alias, **Type** .</span><span class="sxs-lookup"><span data-stu-id="e585b-188">Use **CommandType** or its alias, **Type** .</span></span>

<span data-ttu-id="e585b-189">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e585b-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e585b-190">Affecté.</span><span class="sxs-lookup"><span data-stu-id="e585b-190">Alias.</span></span> <span data-ttu-id="e585b-191">Tous les alias PowerShell dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-191">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="e585b-192">Tout le monde.</span><span class="sxs-lookup"><span data-stu-id="e585b-192">All.</span></span> <span data-ttu-id="e585b-193">tous les types de commandes.</span><span class="sxs-lookup"><span data-stu-id="e585b-193">All command types.</span></span> <span data-ttu-id="e585b-194">C’est l’équivalent de `Get-Command -Name *` .</span><span class="sxs-lookup"><span data-stu-id="e585b-194">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="e585b-195">console.</span><span class="sxs-lookup"><span data-stu-id="e585b-195">Application.</span></span> <span data-ttu-id="e585b-196">Tous les fichiers autres que les fichiers PowerShell dans les chemins d’accès figurant dans la variable d’environnement PATH ( `$env:path` ), y compris les fichiers. txt,. exe et. dll.</span><span class="sxs-lookup"><span data-stu-id="e585b-196">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="e585b-197">PolicySchedule.</span><span class="sxs-lookup"><span data-stu-id="e585b-197">Cmdlet.</span></span> <span data-ttu-id="e585b-198">applets de commande dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-198">The cmdlets in the current session.</span></span> <span data-ttu-id="e585b-199">Est l’applet de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="e585b-199">Cmdlet is the default.</span></span>
- <span data-ttu-id="e585b-200">Configuration.</span><span class="sxs-lookup"><span data-stu-id="e585b-200">Configuration.</span></span> <span data-ttu-id="e585b-201">Une configuration PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-201">A PowerShell configuration.</span></span> <span data-ttu-id="e585b-202">Pour plus d’informations, consultez [about_session_configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e585b-202">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="e585b-203">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="e585b-203">ExternalScript.</span></span> <span data-ttu-id="e585b-204">Tous les fichiers. ps1 dans les chemins d’accès figurant dans la variable d’environnement PATH ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="e585b-204">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="e585b-205">Filtre et fonction.</span><span class="sxs-lookup"><span data-stu-id="e585b-205">Filter and Function.</span></span> <span data-ttu-id="e585b-206">Toutes les fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-206">All PowerShell functions.</span></span>
- <span data-ttu-id="e585b-207">Script.</span><span class="sxs-lookup"><span data-stu-id="e585b-207">Script.</span></span> <span data-ttu-id="e585b-208">blocs de script dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e585b-208">Script blocks in the current session.</span></span>
- <span data-ttu-id="e585b-209">Flux.</span><span class="sxs-lookup"><span data-stu-id="e585b-209">Workflow.</span></span> <span data-ttu-id="e585b-210">Un flux de travail PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-210">A PowerShell workflow.</span></span> <span data-ttu-id="e585b-211">Pour plus d’informations, consultez [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span><span class="sxs-lookup"><span data-stu-id="e585b-211">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-212">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e585b-212">-Encoding</span></span>

<span data-ttu-id="e585b-213">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="e585b-213">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="e585b-214">La valeur par défaut est `UTF8`.</span><span class="sxs-lookup"><span data-stu-id="e585b-214">The default value is `UTF8`.</span></span>

<span data-ttu-id="e585b-215">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e585b-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e585b-216">`ASCII` Utilise le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="e585b-216">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e585b-217">`BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="e585b-217">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="e585b-218">`Default` Utilise l’encodage qui correspond à la page de codes active du système.</span><span class="sxs-lookup"><span data-stu-id="e585b-218">`Default` Uses the encoding that corresponds to the system's active code page.</span></span>
- <span data-ttu-id="e585b-219">`OEM` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="e585b-219">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="e585b-220">`Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="e585b-220">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="e585b-221">`UTF7` Utilise UTF-7.</span><span class="sxs-lookup"><span data-stu-id="e585b-221">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="e585b-222">`UTF8` Utilise UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e585b-222">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="e585b-223">`UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="e585b-223">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: UTF8
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-224">-Force</span><span class="sxs-lookup"><span data-stu-id="e585b-224">-Force</span></span>

<span data-ttu-id="e585b-225">Remplace un ou plusieurs fichiers de sortie existants, même si le fichier possède l'attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="e585b-225">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="e585b-226">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="e585b-226">-FormatTypeName</span></span>

<span data-ttu-id="e585b-227">Exportations les instructions de mise en forme uniquement pour les types Microsoft .NET Framework spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e585b-227">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="e585b-228">Entrez les noms des types.</span><span class="sxs-lookup"><span data-stu-id="e585b-228">Enter the type names.</span></span> <span data-ttu-id="e585b-229">Par défaut, `Export-PSSession` exporte des instructions de mise en forme pour tous les types de .NET Framework qui ne sont pas dans l’espace de noms **System. Management. Automation** .</span><span class="sxs-lookup"><span data-stu-id="e585b-229">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="e585b-230">La valeur de ce paramètre doit être le nom d’un type retourné par une `Get-FormatData` commande dans la session à partir de laquelle les commandes sont importées.</span><span class="sxs-lookup"><span data-stu-id="e585b-230">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="e585b-231">Pour récupérer toutes les données de mise en forme dans la session à distance, tapez `*` .</span><span class="sxs-lookup"><span data-stu-id="e585b-231">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="e585b-232">Si vous utilisez le paramètre **FormatTypeName** , aucune commande n’est exportée, sauf si vous utilisez le paramètre **CommandName** .</span><span class="sxs-lookup"><span data-stu-id="e585b-232">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="e585b-233">Si vous utilisez le paramètre **CommandName** , les fichiers de mise en forme des commandes ne sont pas exportés, sauf si vous utilisez le paramètre **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="e585b-233">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-234">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="e585b-234">-FullyQualifiedModule</span></span>

<span data-ttu-id="e585b-235">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** .</span><span class="sxs-lookup"><span data-stu-id="e585b-235">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="e585b-236">Consultez la section Notes du [constructeur ModuleSpecification (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span><span class="sxs-lookup"><span data-stu-id="e585b-236">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span>

<span data-ttu-id="e585b-237">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="e585b-237">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="e585b-238">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e585b-238">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="e585b-239">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** ; les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="e585b-239">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter; the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-240">-Module</span><span class="sxs-lookup"><span data-stu-id="e585b-240">-Module</span></span>

<span data-ttu-id="e585b-241">Exporte uniquement les commandes dans les modules et les composants logiciels enfichables PowerShell spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e585b-241">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="e585b-242">Entrez les noms de composant logiciel enfichable et de module.</span><span class="sxs-lookup"><span data-stu-id="e585b-242">Enter the snap-in and module names.</span></span> <span data-ttu-id="e585b-243">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="e585b-243">Wildcards are not permitted.</span></span>

<span data-ttu-id="e585b-244">Pour plus d’informations, consultez `Import-Module` et [about_Pssnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).</span><span class="sxs-lookup"><span data-stu-id="e585b-244">For more information, see `Import-Module` and [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-245">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="e585b-245">-OutputModule</span></span>

<span data-ttu-id="e585b-246">Spécifie un chemin d’accès et un nom facultatifs pour le module créé par `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e585b-246">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="e585b-247">Le chemin d’accès par défaut est : `$home\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="e585b-247">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="e585b-248">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e585b-248">This parameter is required.</span></span>

<span data-ttu-id="e585b-249">Si le sous-répertoire du module ou l’un des fichiers `Export-PSSession` créés par est déjà présent, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="e585b-249">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="e585b-250">Pour remplacer les fichiers existants, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="e585b-250">To overwrite existing files, use the **Force** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-251">-Session</span><span class="sxs-lookup"><span data-stu-id="e585b-251">-Session</span></span>

<span data-ttu-id="e585b-252">Spécifie la session PSSession à partir de laquelle les commandes sont exportées.</span><span class="sxs-lookup"><span data-stu-id="e585b-252">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="e585b-253">Entrez une variable qui contient un objet de session ou une commande qui obtient un objet de session, tel qu’une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="e585b-253">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="e585b-254">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e585b-254">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e585b-255">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e585b-255">CommonParameters</span></span>

<span data-ttu-id="e585b-256">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e585b-256">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e585b-257">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e585b-257">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e585b-258">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e585b-258">INPUTS</span></span>

### <span data-ttu-id="e585b-259">Aucun</span><span class="sxs-lookup"><span data-stu-id="e585b-259">None</span></span>

<span data-ttu-id="e585b-260">Vous ne pouvez pas diriger d’objets vers `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e585b-260">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="e585b-261">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e585b-261">OUTPUTS</span></span>

### <span data-ttu-id="e585b-262">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="e585b-262">System.IO.FileInfo</span></span>

<span data-ttu-id="e585b-263">`Export-PSSession` retourne une liste des fichiers qui composent le module qu’il a créé.</span><span class="sxs-lookup"><span data-stu-id="e585b-263">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="e585b-264">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e585b-264">NOTES</span></span>

<span data-ttu-id="e585b-265">`Export-PSSession` s’appuie sur l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-265">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="e585b-266">Pour utiliser cette applet de commande, l'ordinateur doit être configuré pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="e585b-266">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="e585b-267">Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e585b-267">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="e585b-268">Vous ne pouvez pas utiliser `Export-PSSession` pour exporter un fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-268">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="e585b-269">Les commandes exportées s'exécutent implicitement dans la session PSSession à partir de laquelle elles ont été exportées.</span><span class="sxs-lookup"><span data-stu-id="e585b-269">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="e585b-270">Les détails de l’exécution des commandes à distance sont gérées entièrement par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e585b-270">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="e585b-271">Vous pouvez exécuter les commandes exportées tout comme vous exécuteriez des commandes locales.</span><span class="sxs-lookup"><span data-stu-id="e585b-271">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="e585b-272">`Export-ModuleMember` capture et enregistre des informations sur la session PSSession dans le module qu’elle exporte.</span><span class="sxs-lookup"><span data-stu-id="e585b-272">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="e585b-273">Si la session PSSession à partir de laquelle les commandes ont été exportées est fermée lorsque vous importez le module, et qu’il n’y a aucun sessions PSSession actif sur le même ordinateur, les commandes du module essaient de recréer la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="e585b-273">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="e585b-274">Si les tentatives de recréation de la session PSSession échouent, les commandes exportées ne sont pas exécutées.</span><span class="sxs-lookup"><span data-stu-id="e585b-274">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="e585b-275">Les informations de session `Export-ModuleMember` capturées et enregistrées dans le module n’incluent pas les options de session, telles que celles que vous spécifiez dans la `$PSSessionOption` variable de préférence ou à l’aide du paramètre **SessionOption** des `New-PSSession` applets de commande, `Enter-PSSession` ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e585b-275">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="e585b-276">Si la session PSSession d'origine est fermée quand vous importez le module, ce dernier utilisera une autre session PSSession sur le même ordinateur, si celle-ci est disponible.</span><span class="sxs-lookup"><span data-stu-id="e585b-276">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="e585b-277">Pour permettre aux commandes importées de s'exécuter dans une session correctement configurée, créez une session PSSession avec les options que vous souhaitez avant d'importer le module.</span><span class="sxs-lookup"><span data-stu-id="e585b-277">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="e585b-278">Pour rechercher les commandes à exporter, `Export-PSSession` utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Command` commande dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="e585b-278">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="e585b-279">Pour obtenir et enregistrer des données de mise en forme pour les commandes, elle utilise les `Get-FormatData` applets de commande et `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="e585b-279">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="e585b-280">Vous pouvez voir des messages d’erreur de `Invoke-Command` ,, `Get-Command` `Get-FormatData` et `Export-FormatData` lorsque vous exécutez une `Export-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="e585b-280">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="e585b-281">En outre, `Export-PSSession` ne peut pas exporter des commandes à partir d’une session qui n’inclut pas les `Get-Command` applets de commande,, `Get-FormatData` `Select-Object` et `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="e585b-281">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="e585b-282">`Export-PSSession` utilise l' `Write-Progress` applet de commande pour afficher la progression de la commande.</span><span class="sxs-lookup"><span data-stu-id="e585b-282">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="e585b-283">Vous pouvez voir la barre de progression pendant l'exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e585b-283">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="e585b-284">Les commandes exportées présentent les mêmes restrictions que les autres commandes à distance, notamment l'impossibilité de démarrer un programme avec une interface utilisateur, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="e585b-284">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="e585b-285">Étant donné que les profils PowerShell ne sont pas exécutés dans sessions PSSession, les commandes qu’un profil ajoute à une session ne sont pas disponibles pour `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e585b-285">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="e585b-286">Pour exporter des commandes à partir d’un profil, utilisez une `Invoke-Command` commande pour exécuter le profil dans la session PSSession manuellement avant d’exporter les commandes.</span><span class="sxs-lookup"><span data-stu-id="e585b-286">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="e585b-287">Le module que `Export-PSSession` crée peut inclure un fichier de mise en forme, même si la commande n’importe pas de données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e585b-287">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="e585b-288">Si la commande n'importe pas de données de mise en forme, les fichiers de mise en forme éventuellement créés ne contiennent pas de données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e585b-288">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="e585b-289">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e585b-289">RELATED LINKS</span></span>

[<span data-ttu-id="e585b-290">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="e585b-290">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="e585b-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e585b-291">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="e585b-292">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="e585b-292">about_PSSnapins</span></span>](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)

[<span data-ttu-id="e585b-293">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="e585b-293">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="e585b-294">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="e585b-294">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="e585b-295">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e585b-295">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="e585b-296">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e585b-296">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="e585b-297">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e585b-297">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="e585b-298">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="e585b-298">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="e585b-299">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e585b-299">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)
