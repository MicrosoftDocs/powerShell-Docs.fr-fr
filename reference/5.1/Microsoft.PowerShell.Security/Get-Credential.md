---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208889"
---
# <span data-ttu-id="6f20d-103">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="6f20d-103">Get-Credential</span></span>

## <span data-ttu-id="6f20d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6f20d-104">SYNOPSIS</span></span>
<span data-ttu-id="6f20d-105">Obtient un objet d'informations d'identification basé sur un nom d'utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-105">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="6f20d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6f20d-106">SYNTAX</span></span>

### <span data-ttu-id="6f20d-107">CredentialSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6f20d-107">CredentialSet (Default)</span></span>

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### <span data-ttu-id="6f20d-108">MessageSet</span><span class="sxs-lookup"><span data-stu-id="6f20d-108">MessageSet</span></span>

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="6f20d-109">Description</span><span class="sxs-lookup"><span data-stu-id="6f20d-109">DESCRIPTION</span></span>

<span data-ttu-id="6f20d-110">L' `Get-Credential` applet de commande crée un objet d’informations d’identification pour un nom d’utilisateur et un mot de passe spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6f20d-110">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="6f20d-111">Vous pouvez utiliser l'objet d'informations d'identification dans les opérations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6f20d-111">You can use the credential object in security operations.</span></span>

<span data-ttu-id="6f20d-112">À compter de PowerShell 3,0, vous pouvez utiliser le paramètre **message** pour spécifier un message personnalisé dans la boîte de dialogue qui invite l’utilisateur à entrer son nom et son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-112">Beginning in PowerShell 3.0, you can use the **Message** parameter to specify a customized message on the dialog box that prompts the user for their name and password.</span></span>

<span data-ttu-id="6f20d-113">L' `Get-Credential` applet de commande invite l’utilisateur à entrer un mot de passe ou un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-113">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="6f20d-114">Par défaut, une boîte de dialogue d'authentification s'affiche pour solliciter l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f20d-114">By default, an authentication dialog box appears to prompt the user.</span></span> <span data-ttu-id="6f20d-115">Toutefois, dans certains programmes hôtes, tels que la console PowerShell, vous pouvez inviter l’utilisateur sur la ligne de commande en modifiant une entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="6f20d-115">However, in some host programs, such as the PowerShell console, you can prompt the user at the command line by changing a registry entry.</span></span> <span data-ttu-id="6f20d-116">Pour plus d'informations sur cette entrée de Registre, consultez les remarques et les exemples.</span><span class="sxs-lookup"><span data-stu-id="6f20d-116">For more information about this registry entry, see the notes and examples.</span></span>

## <span data-ttu-id="6f20d-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6f20d-117">EXAMPLES</span></span>

### <span data-ttu-id="6f20d-118">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="6f20d-118">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="6f20d-119">Cette commande obtient un objet d’informations d’identification et l’enregistre dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="6f20d-119">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="6f20d-120">Quand vous entrez la commande, une boîte de dialogue s'affiche demandant un nom d'utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-120">When you enter the command, a dialog box appears requesting a user name and password.</span></span> <span data-ttu-id="6f20d-121">Lorsque vous entrez les informations demandées, l’applet de commande crée un objet **PSCredential** qui représente les informations d’identification de l’utilisateur et l’enregistre dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="6f20d-121">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="6f20d-122">Vous pouvez utiliser l'objet comme entrée dans les applets de commande qui impliquent une authentification utilisateur, telles que celles comportant un paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="6f20d-122">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="6f20d-123">Toutefois, certains fournisseurs installés avec PowerShell ne prennent pas en charge le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="6f20d-123">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="6f20d-124">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="6f20d-124">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="6f20d-125">Ces commandes utilisent un objet d’informations d’identification que l' `Get-Credential` applet de commande renvoie pour authentifier un utilisateur sur un ordinateur distant afin qu’il puisse utiliser Windows Management Instrumentation (WMI) pour gérer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6f20d-125">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="6f20d-126">La première commande obtient un objet d’informations d’identification et l’enregistre dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="6f20d-126">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="6f20d-127">La deuxième commande utilise l’objet Credential dans une `Get-CimInstance` commande.</span><span class="sxs-lookup"><span data-stu-id="6f20d-127">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="6f20d-128">Cette commande obtient des informations sur les lecteurs de disque sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="6f20d-128">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="6f20d-129">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="6f20d-129">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="6f20d-130">Cette commande montre comment inclure une `Get-Credential` commande dans une  `Get-CimInstance` commande.</span><span class="sxs-lookup"><span data-stu-id="6f20d-130">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="6f20d-131">Cette commande utilise la `Get-CimInstance` cmdlet pour obtenir des informations sur le BIOS sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="6f20d-131">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="6f20d-132">Elle utilise le paramètre **Credential** pour authentifier l’utilisateur, Domaine01\Utilisateur01 et une `Get-Credential` commande en tant que valeur du paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="6f20d-132">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="6f20d-133">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="6f20d-133">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="6f20d-134">Cet exemple crée une information d'identification qui inclut un nom d'utilisateur sans nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="6f20d-134">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="6f20d-135">La première commande obtient des informations d’identification avec le nom d’utilisateur User01 et les stocke dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="6f20d-135">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="6f20d-136">La deuxième commande affiche la valeur de la propriété **Username** de l'objet d'informations d'identification résultant.</span><span class="sxs-lookup"><span data-stu-id="6f20d-136">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="6f20d-137">Exemple 5</span><span class="sxs-lookup"><span data-stu-id="6f20d-137">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="6f20d-138">Cette commande utilise la méthode **PromptForCredential** pour inviter l'utilisateur à indiquer ses nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-138">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="6f20d-139">La commande enregistre les informations d’identification résultantes dans la `$Credential` variable.</span><span class="sxs-lookup"><span data-stu-id="6f20d-139">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="6f20d-140">La méthode **PromptForCredential** est une alternative à l’utilisation de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="6f20d-140">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6f20d-141">Quand vous utilisez **PromptForCredential** , vous pouvez spécifier la légende, les messages et le nom d'utilisateur qui s'affichent dans la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="6f20d-141">When you use **PromptForCredential** , you can specify the caption, messages, and user name that appear in the message box.</span></span>

<span data-ttu-id="6f20d-142">Pour plus d’informations, consultez la documentation [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="6f20d-142">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="6f20d-143">Exemple 6</span><span class="sxs-lookup"><span data-stu-id="6f20d-143">Example 6</span></span>

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

<span data-ttu-id="6f20d-144">Cet exemple montre comment modifier le Registre pour que l'utilisateur soit sollicité depuis la ligne de commande, et non à l'aide d'une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f20d-144">This example shows how to modify the registry so that the user is prompted at the command line, instead of by using a dialog box.</span></span>

<span data-ttu-id="6f20d-145">La commande crée l'entrée de Registre **ConsolePrompting** et lui affecte la valeur True.</span><span class="sxs-lookup"><span data-stu-id="6f20d-145">The command creates the **ConsolePrompting** registry entry and sets its value to True.</span></span> <span data-ttu-id="6f20d-146">Pour exécuter cette commande, démarrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="6f20d-146">To run this command, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="6f20d-147">Pour utiliser une boîte de dialogue de confirmation, définissez la valeur de ConsolePrompting sur false ($false) ou utilisez l' `Remove-ItemProperty` applet de commande pour la supprimer.</span><span class="sxs-lookup"><span data-stu-id="6f20d-147">To use a dialog box for prompting, set the value of the ConsolePrompting to false ($false) or use the `Remove-ItemProperty` cmdlet to delete it.</span></span>

<span data-ttu-id="6f20d-148">L’entrée de Registre ConsolePrompting fonctionne dans certains programmes hôtes, tels que la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f20d-148">The ConsolePrompting registry entry works in some host programs, such as the PowerShell console.</span></span> <span data-ttu-id="6f20d-149">Elle peut ne pas fonctionner dans tous les programmes hôtes.</span><span class="sxs-lookup"><span data-stu-id="6f20d-149">It might not work in all host programs.</span></span>

### <span data-ttu-id="6f20d-150">Exemple 7</span><span class="sxs-lookup"><span data-stu-id="6f20d-150">Example 7</span></span>

<span data-ttu-id="6f20d-151">Cet exemple montre comment créer un objet d’informations d’identification identique à l’objet `Get-Credential` retourné sans inviter l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f20d-151">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="6f20d-152">Cette méthode nécessite un mot de passe en texte brut, ce qui peut violer les normes de sécurité dans certaines entreprises.</span><span class="sxs-lookup"><span data-stu-id="6f20d-152">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="6f20d-153">La première commande enregistre le nom du compte d’utilisateur dans le `$User` paramètre.</span><span class="sxs-lookup"><span data-stu-id="6f20d-153">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="6f20d-154">La valeur doit avoir le format « Domaine\Utilisateur » ou « Nom d'ordinateur\Utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="6f20d-154">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="6f20d-155">La deuxième commande utilise l' `ConvertTo-SecureString` applet de commande pour créer une chaîne sécurisée à partir d’un mot de passe en texte brut.</span><span class="sxs-lookup"><span data-stu-id="6f20d-155">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="6f20d-156">La commande utilise le paramètre **AsPlainText** pour indiquer que la chaîne est du texte brut, et le paramètre **Force** pour confirmer que vous comprenez les risques de l'utilisation de texte brut.</span><span class="sxs-lookup"><span data-stu-id="6f20d-156">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="6f20d-157">La troisième commande utilise l' `New-Object` applet de commande pour créer un objet **PSCredential** à partir des valeurs des `$User` `$PWord` variables et.</span><span class="sxs-lookup"><span data-stu-id="6f20d-157">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="6f20d-158">Exemple 8</span><span class="sxs-lookup"><span data-stu-id="6f20d-158">Example 8</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="6f20d-159">Cette commande utilise les paramètres **message** et **nom d’utilisateur** de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="6f20d-159">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6f20d-160">Ce format de commande est conçu pour les fonctions et les scripts partagés.</span><span class="sxs-lookup"><span data-stu-id="6f20d-160">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="6f20d-161">Dans ce cas, le message indique à l'utilisateur pourquoi les informations d'identification sont nécessaires tout en l'assurant implicitement que la demande est légitime.</span><span class="sxs-lookup"><span data-stu-id="6f20d-161">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="6f20d-162">Exemple 9</span><span class="sxs-lookup"><span data-stu-id="6f20d-162">Example 9</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

<span data-ttu-id="6f20d-163">Cette commande obtient des informations d'identification de l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="6f20d-163">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="6f20d-164">La commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Credential` commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="6f20d-164">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="6f20d-165">La sortie affiche le message de sécurité distant qui `Get-Credential` comprend dans l’invite d’authentification.</span><span class="sxs-lookup"><span data-stu-id="6f20d-165">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="6f20d-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6f20d-166">PARAMETERS</span></span>

### <span data-ttu-id="6f20d-167">-Credential</span><span class="sxs-lookup"><span data-stu-id="6f20d-167">-Credential</span></span>

<span data-ttu-id="6f20d-168">Spécifie un nom d’utilisateur pour les informations d’identification, tel que **User01** ou **Domaine01\Utilisateur01**.</span><span class="sxs-lookup"><span data-stu-id="6f20d-168">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="6f20d-169">Le nom du paramètre, `-Credential` , est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6f20d-169">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="6f20d-170">Lorsque vous envoyez la commande et spécifiez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-170">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="6f20d-171">Si vous omettez ce paramètre, vous êtes invité à entrer un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-171">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="6f20d-172">À compter de PowerShell 3,0, si vous entrez un nom d’utilisateur sans domaine, `Get-Credential` n’insère plus de barre oblique inverse avant le nom.</span><span class="sxs-lookup"><span data-stu-id="6f20d-172">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="6f20d-173">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="6f20d-173">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6f20d-174">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="6f20d-174">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6f20d-175">-Message</span><span class="sxs-lookup"><span data-stu-id="6f20d-175">-Message</span></span>

<span data-ttu-id="6f20d-176">Spécifie un message qui s'affiche dans l'invite d'authentification.</span><span class="sxs-lookup"><span data-stu-id="6f20d-176">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="6f20d-177">Ce paramètre est conçu pour une utilisation dans une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="6f20d-177">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="6f20d-178">Vous pouvez utiliser le message pour expliquer à l'utilisateur pourquoi vous demandez des informations d'identification et comment elles seront utilisées.</span><span class="sxs-lookup"><span data-stu-id="6f20d-178">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="6f20d-179">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6f20d-179">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6f20d-180">-UserName</span><span class="sxs-lookup"><span data-stu-id="6f20d-180">-UserName</span></span>

<span data-ttu-id="6f20d-181">Spécifie un nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f20d-181">Specifies a user name.</span></span> <span data-ttu-id="6f20d-182">L'invite d'authentification demande un mot de passe pour le nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f20d-182">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="6f20d-183">Par défaut, le nom d'utilisateur est vide et l'invite d'authentification demande un nom d'utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f20d-183">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="6f20d-184">Quand l'invite d'authentification s'affiche dans une boîte de dialogue, l'utilisateur peut modifier le nom d'utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f20d-184">When the authentication prompt appears in a dialog box, the user can edit the specified user name.</span></span>
<span data-ttu-id="6f20d-185">Toutefois, l'utilisateur ne peut pas modifier le nom d'utilisateur quand l'invite apparaît sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="6f20d-185">However, the user cannot change the user name when the prompt appears at the command line.</span></span> <span data-ttu-id="6f20d-186">Quand vous utilisez ce paramètre dans une fonction partagée ou un script, envisagez toutes les présentations possibles.</span><span class="sxs-lookup"><span data-stu-id="6f20d-186">When using this parameter in a shared function or script, consider all possible presentations.</span></span>

<span data-ttu-id="6f20d-187">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6f20d-187">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6f20d-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6f20d-188">CommonParameters</span></span>

<span data-ttu-id="6f20d-189">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6f20d-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6f20d-190">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6f20d-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6f20d-191">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6f20d-191">INPUTS</span></span>

### <span data-ttu-id="6f20d-192">Aucun</span><span class="sxs-lookup"><span data-stu-id="6f20d-192">None</span></span>

<span data-ttu-id="6f20d-193">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6f20d-193">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6f20d-194">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6f20d-194">OUTPUTS</span></span>

### <span data-ttu-id="6f20d-195">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="6f20d-195">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="6f20d-196">`Get-Credential` retourne un objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="6f20d-196">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="6f20d-197">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6f20d-197">NOTES</span></span>

<span data-ttu-id="6f20d-198">Vous pouvez utiliser l’objet **PSCredential** qui est `Get-Credential` créé dans les applets de commande qui demandent l’authentification utilisateur, telles que celles avec un paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="6f20d-198">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="6f20d-199">Par défaut, l'invite d'authentification s'affiche dans une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f20d-199">By default, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="6f20d-200">Pour afficher l’invite d’authentification sur la ligne de commande, ajoutez l’entrée de Registre **ConsolePrompting** ( `HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting` ) et définissez sa valeur sur **true**.</span><span class="sxs-lookup"><span data-stu-id="6f20d-200">To display the authentication prompt at the command line, add the **ConsolePrompting** registry entry (`HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting`) and set its value to **True**.</span></span>
<span data-ttu-id="6f20d-201">Si l'entrée de Registre **ConsolePrompting** n'existe pas ou si sa valeur est False, l'invite d'authentification s'affiche dans une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f20d-201">If the **ConsolePrompting** registry entry does not exist or if its value is False, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="6f20d-202">Pour obtenir des instructions, consultez les exemples.</span><span class="sxs-lookup"><span data-stu-id="6f20d-202">For instructions, see the examples.</span></span>

<span data-ttu-id="6f20d-203">L’entrée de Registre **ConsolePrompting** fonctionne dans la console PowerShell, mais elle ne fonctionne pas dans tous les programmes hôtes.</span><span class="sxs-lookup"><span data-stu-id="6f20d-203">The **ConsolePrompting** registry entry works in the PowerShell console, but it does not work in all host programs.</span></span>

<span data-ttu-id="6f20d-204">Par exemple, il n’a aucun effet dans l’environnement d’écriture de scripts intégré de PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="6f20d-204">For example, it has no effect in the PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="6f20d-205">Pour plus d'informations sur l'effet de l'entrée de Registre **ConsolePrompting** , consultez les rubriques d'aide sur le programme hôte.</span><span class="sxs-lookup"><span data-stu-id="6f20d-205">For information about the effect of the **ConsolePrompting** registry entry, see the help topics for the host program.</span></span>

<span data-ttu-id="6f20d-206">Le paramètre **Credential** n’est pas pris en charge par tous les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f20d-206">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="6f20d-207">À compter de PowerShell 3,0, il est pris en charge sur les applets de commande SELECT, telles que les `Get-Content` applets de commande et `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="6f20d-207">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="6f20d-208">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6f20d-208">RELATED LINKS</span></span>

[<span data-ttu-id="6f20d-209">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="6f20d-209">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
