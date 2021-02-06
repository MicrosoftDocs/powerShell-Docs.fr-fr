---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 5630c4d09a2806eb117d005466d4925c1740d3a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596109"
---
# <span data-ttu-id="af4d2-102">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="af4d2-102">Get-Credential</span></span>

## <span data-ttu-id="af4d2-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="af4d2-103">SYNOPSIS</span></span>
<span data-ttu-id="af4d2-104">Obtient un objet d'informations d'identification basé sur un nom d'utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-104">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="af4d2-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="af4d2-105">SYNTAX</span></span>

### <span data-ttu-id="af4d2-106">CredentialSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="af4d2-106">CredentialSet (Default)</span></span>

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="af4d2-107">MessageSet</span><span class="sxs-lookup"><span data-stu-id="af4d2-107">MessageSet</span></span>

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## <span data-ttu-id="af4d2-108">Description</span><span class="sxs-lookup"><span data-stu-id="af4d2-108">DESCRIPTION</span></span>

<span data-ttu-id="af4d2-109">L' `Get-Credential` applet de commande crée un objet d’informations d’identification pour un nom d’utilisateur et un mot de passe spécifiés.</span><span class="sxs-lookup"><span data-stu-id="af4d2-109">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="af4d2-110">Vous pouvez utiliser l'objet d'informations d'identification dans les opérations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="af4d2-110">You can use the credential object in security operations.</span></span>

<span data-ttu-id="af4d2-111">L' `Get-Credential` applet de commande invite l’utilisateur à entrer un mot de passe ou un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-111">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="af4d2-112">Vous pouvez utiliser le paramètre **message** pour spécifier un message personnalisé dans l’invite de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="af4d2-112">You can use the **Message** parameter to specify a customized message in the command line prompt.</span></span>

## <span data-ttu-id="af4d2-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="af4d2-113">EXAMPLES</span></span>

### <span data-ttu-id="af4d2-114">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="af4d2-114">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="af4d2-115">Cette commande obtient un objet d’informations d’identification et l’enregistre dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="af4d2-115">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="af4d2-116">Lorsque vous entrez la commande, vous êtes invité à entrer un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-116">When you enter the command, you are prompted for a user name and password.</span></span> <span data-ttu-id="af4d2-117">Lorsque vous entrez les informations demandées, l’applet de commande crée un objet **PSCredential** qui représente les informations d’identification de l’utilisateur et l’enregistre dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="af4d2-117">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="af4d2-118">Vous pouvez utiliser l'objet comme entrée dans les applets de commande qui impliquent une authentification utilisateur, telles que celles comportant un paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="af4d2-118">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="af4d2-119">Toutefois, certains fournisseurs installés avec PowerShell ne prennent pas en charge le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="af4d2-119">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="af4d2-120">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="af4d2-120">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="af4d2-121">Ces commandes utilisent un objet d’informations d’identification que l' `Get-Credential` applet de commande renvoie pour authentifier un utilisateur sur un ordinateur distant afin qu’il puisse utiliser Windows Management Instrumentation (WMI) pour gérer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="af4d2-121">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="af4d2-122">La première commande obtient un objet d’informations d’identification et l’enregistre dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="af4d2-122">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="af4d2-123">La deuxième commande utilise l’objet Credential dans une `Get-CimInstance` commande.</span><span class="sxs-lookup"><span data-stu-id="af4d2-123">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="af4d2-124">Cette commande obtient des informations sur les lecteurs de disque sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="af4d2-124">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="af4d2-125">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="af4d2-125">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="af4d2-126">Cette commande montre comment inclure une `Get-Credential` commande dans une  `Get-CimInstance` commande.</span><span class="sxs-lookup"><span data-stu-id="af4d2-126">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="af4d2-127">Cette commande utilise la `Get-CimInstance` cmdlet pour obtenir des informations sur le BIOS sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="af4d2-127">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="af4d2-128">Elle utilise le paramètre **Credential** pour authentifier l’utilisateur, Domaine01\Utilisateur01 et une `Get-Credential` commande en tant que valeur du paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="af4d2-128">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="af4d2-129">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="af4d2-129">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="af4d2-130">Cet exemple crée une information d'identification qui inclut un nom d'utilisateur sans nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="af4d2-130">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="af4d2-131">La première commande obtient des informations d’identification avec le nom d’utilisateur User01 et les stocke dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="af4d2-131">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="af4d2-132">La deuxième commande affiche la valeur de la propriété **Username** de l'objet d'informations d'identification résultant.</span><span class="sxs-lookup"><span data-stu-id="af4d2-132">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="af4d2-133">Exemple 5</span><span class="sxs-lookup"><span data-stu-id="af4d2-133">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="af4d2-134">Cette commande utilise la méthode **PromptForCredential** pour inviter l'utilisateur à indiquer ses nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-134">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="af4d2-135">La commande enregistre les informations d’identification résultantes dans la `$Credential` variable.</span><span class="sxs-lookup"><span data-stu-id="af4d2-135">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="af4d2-136">La méthode **PromptForCredential** est une alternative à l’utilisation de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="af4d2-136">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="af4d2-137">Lorsque vous utilisez **PromptForCredential**, vous pouvez spécifier la légende, les messages et le nom d’utilisateur qui s’affichent dans l’invite.</span><span class="sxs-lookup"><span data-stu-id="af4d2-137">When you use **PromptForCredential**, you can specify the caption, messages, and user name that appear in the prompt.</span></span>

<span data-ttu-id="af4d2-138">Pour plus d’informations, consultez la documentation [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="af4d2-138">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="af4d2-139">Exemple 6</span><span class="sxs-lookup"><span data-stu-id="af4d2-139">Example 6</span></span>

<span data-ttu-id="af4d2-140">Cet exemple montre comment créer un objet d’informations d’identification identique à l’objet `Get-Credential` retourné sans inviter l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af4d2-140">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="af4d2-141">Cette méthode nécessite un mot de passe en texte brut, ce qui peut violer les normes de sécurité dans certaines entreprises.</span><span class="sxs-lookup"><span data-stu-id="af4d2-141">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="af4d2-142">La première commande enregistre le nom du compte d’utilisateur dans le `$User` paramètre.</span><span class="sxs-lookup"><span data-stu-id="af4d2-142">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="af4d2-143">La valeur doit avoir le format « Domaine\Utilisateur » ou « Nom d'ordinateur\Utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="af4d2-143">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="af4d2-144">La deuxième commande utilise l' `ConvertTo-SecureString` applet de commande pour créer une chaîne sécurisée à partir d’un mot de passe en texte brut.</span><span class="sxs-lookup"><span data-stu-id="af4d2-144">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="af4d2-145">La commande utilise le paramètre **AsPlainText** pour indiquer que la chaîne est du texte brut, et le paramètre **Force** pour confirmer que vous comprenez les risques de l'utilisation de texte brut.</span><span class="sxs-lookup"><span data-stu-id="af4d2-145">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="af4d2-146">La troisième commande utilise l' `New-Object` applet de commande pour créer un objet **PSCredential** à partir des valeurs des `$User` `$PWord` variables et.</span><span class="sxs-lookup"><span data-stu-id="af4d2-146">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="af4d2-147">Exemple 7</span><span class="sxs-lookup"><span data-stu-id="af4d2-147">Example 7</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="af4d2-148">Cette commande utilise les paramètres **message** et **nom d’utilisateur** de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="af4d2-148">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="af4d2-149">Ce format de commande est conçu pour les fonctions et les scripts partagés.</span><span class="sxs-lookup"><span data-stu-id="af4d2-149">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="af4d2-150">Dans ce cas, le message indique à l'utilisateur pourquoi les informations d'identification sont nécessaires tout en l'assurant implicitement que la demande est légitime.</span><span class="sxs-lookup"><span data-stu-id="af4d2-150">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="af4d2-151">Exemple 8</span><span class="sxs-lookup"><span data-stu-id="af4d2-151">Example 8</span></span>

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

<span data-ttu-id="af4d2-152">Cette commande obtient des informations d'identification de l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="af4d2-152">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="af4d2-153">La commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Credential` commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="af4d2-153">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="af4d2-154">La sortie affiche le message de sécurité distant qui `Get-Credential` comprend dans l’invite d’authentification.</span><span class="sxs-lookup"><span data-stu-id="af4d2-154">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="af4d2-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="af4d2-155">PARAMETERS</span></span>

### <span data-ttu-id="af4d2-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="af4d2-156">-Credential</span></span>

<span data-ttu-id="af4d2-157">Spécifie un nom d’utilisateur pour les informations d’identification, tel que **User01** ou **Domaine01\Utilisateur01**.</span><span class="sxs-lookup"><span data-stu-id="af4d2-157">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="af4d2-158">Le nom du paramètre, `-Credential` , est facultatif.</span><span class="sxs-lookup"><span data-stu-id="af4d2-158">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="af4d2-159">Lorsque vous envoyez la commande et spécifiez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-159">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="af4d2-160">Si vous omettez ce paramètre, vous êtes invité à entrer un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-160">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="af4d2-161">À compter de PowerShell 3,0, si vous entrez un nom d’utilisateur sans domaine, `Get-Credential` n’insère plus de barre oblique inverse avant le nom.</span><span class="sxs-lookup"><span data-stu-id="af4d2-161">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="af4d2-162">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="af4d2-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="af4d2-163">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="af4d2-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af4d2-164">-Message</span><span class="sxs-lookup"><span data-stu-id="af4d2-164">-Message</span></span>

<span data-ttu-id="af4d2-165">Spécifie un message qui s'affiche dans l'invite d'authentification.</span><span class="sxs-lookup"><span data-stu-id="af4d2-165">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="af4d2-166">Ce paramètre est conçu pour une utilisation dans une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="af4d2-166">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="af4d2-167">Vous pouvez utiliser le message pour expliquer à l'utilisateur pourquoi vous demandez des informations d'identification et comment elles seront utilisées.</span><span class="sxs-lookup"><span data-stu-id="af4d2-167">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="af4d2-168">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="af4d2-168">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af4d2-169">-Title</span><span class="sxs-lookup"><span data-stu-id="af4d2-169">-Title</span></span>

<span data-ttu-id="af4d2-170">Définit le texte de la ligne de titre pour l’invite d’authentification dans la console.</span><span class="sxs-lookup"><span data-stu-id="af4d2-170">Sets the text of the title line for the authentication prompt in the console.</span></span>

<span data-ttu-id="af4d2-171">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="af4d2-171">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af4d2-172">-UserName</span><span class="sxs-lookup"><span data-stu-id="af4d2-172">-UserName</span></span>

<span data-ttu-id="af4d2-173">Spécifie un nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af4d2-173">Specifies a user name.</span></span> <span data-ttu-id="af4d2-174">L'invite d'authentification demande un mot de passe pour le nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af4d2-174">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="af4d2-175">Par défaut, le nom d'utilisateur est vide et l'invite d'authentification demande un nom d'utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af4d2-175">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="af4d2-176">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="af4d2-176">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="af4d2-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af4d2-177">CommonParameters</span></span>

<span data-ttu-id="af4d2-178">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="af4d2-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af4d2-179">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="af4d2-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af4d2-180">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="af4d2-180">INPUTS</span></span>

### <span data-ttu-id="af4d2-181">None</span><span class="sxs-lookup"><span data-stu-id="af4d2-181">None</span></span>

<span data-ttu-id="af4d2-182">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="af4d2-182">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="af4d2-183">SORTIES</span><span class="sxs-lookup"><span data-stu-id="af4d2-183">OUTPUTS</span></span>

### <span data-ttu-id="af4d2-184">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="af4d2-184">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="af4d2-185">`Get-Credential` retourne un objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="af4d2-185">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="af4d2-186">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="af4d2-186">NOTES</span></span>

<span data-ttu-id="af4d2-187">Vous pouvez utiliser l’objet **PSCredential** qui est `Get-Credential` créé dans les applets de commande qui demandent l’authentification utilisateur, telles que celles avec un paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="af4d2-187">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="af4d2-188">Le paramètre **Credential** n’est pas pris en charge par tous les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af4d2-188">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="af4d2-189">À compter de PowerShell 3,0, il est pris en charge sur les applets de commande SELECT, telles que les `Get-Content` applets de commande et `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="af4d2-189">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="af4d2-190">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="af4d2-190">RELATED LINKS</span></span>

[<span data-ttu-id="af4d2-191">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="af4d2-191">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
