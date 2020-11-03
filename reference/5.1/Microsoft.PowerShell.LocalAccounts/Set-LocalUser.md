---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204094"
---
# <span data-ttu-id="38670-103">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-103">Set-LocalUser</span></span>

## <span data-ttu-id="38670-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="38670-104">SYNOPSIS</span></span>
<span data-ttu-id="38670-105">Modifie un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="38670-105">Modifies a local user account.</span></span>

## <span data-ttu-id="38670-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="38670-106">SYNTAX</span></span>

### <span data-ttu-id="38670-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="38670-107">Name (Default)</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="38670-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="38670-108">InputObject</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="38670-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="38670-109">SecurityIdentifier</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="38670-110">Description</span><span class="sxs-lookup"><span data-stu-id="38670-110">DESCRIPTION</span></span>
<span data-ttu-id="38670-111">L’applet de commande **Set-LocalUser** modifie un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="38670-111">The **Set-LocalUser** cmdlet modifies a local user account.</span></span>
<span data-ttu-id="38670-112">Cette applet de commande peut réinitialiser le mot de passe d’un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="38670-112">This cmdlet can reset the password of a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="38670-113">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="38670-113">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="38670-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="38670-114">EXAMPLES</span></span>

### <span data-ttu-id="38670-115">Exemple 1 : modifier la description d’un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="38670-115">Example 1: Change a description of a user account</span></span>

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

<span data-ttu-id="38670-116">Cette commande modifie la description d’un compte d’utilisateur nommé Admin07.</span><span class="sxs-lookup"><span data-stu-id="38670-116">This command changes the description of a user account named Admin07.</span></span>

### <span data-ttu-id="38670-117">Exemple 2 : modifier le mot de passe d’un compte</span><span class="sxs-lookup"><span data-stu-id="38670-117">Example 2: Change the password on an account</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

<span data-ttu-id="38670-118">La première commande vous invite à entrer un mot de passe à l’aide de l’applet de commande Read-Host.</span><span class="sxs-lookup"><span data-stu-id="38670-118">The first command prompts you for a password by using the Read-Host cmdlet.</span></span>
<span data-ttu-id="38670-119">La commande stocke le mot de passe sous la forme d’une chaîne sécurisée dans la variable $Password.</span><span class="sxs-lookup"><span data-stu-id="38670-119">The command stores the password as a secure string in the $Password variable.</span></span>

<span data-ttu-id="38670-120">La deuxième commande obtient un compte d’utilisateur nommé User02 à l’aide de l’option **obtenir-LocalUser** .</span><span class="sxs-lookup"><span data-stu-id="38670-120">The second command gets a user account named User02 by using **Get-LocalUser** .</span></span>
<span data-ttu-id="38670-121">La commande stocke le compte dans la variable $UserAccount.</span><span class="sxs-lookup"><span data-stu-id="38670-121">The command stores the account in the $UserAccount variable.</span></span>

<span data-ttu-id="38670-122">La troisième commande définit le nouveau mot de passe sur le compte d’utilisateur stocké dans $UserAccount.</span><span class="sxs-lookup"><span data-stu-id="38670-122">The third command sets the new password on the user account stored in $UserAccount.</span></span>

## <span data-ttu-id="38670-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38670-123">PARAMETERS</span></span>

### <span data-ttu-id="38670-124">-AccountExpires dans</span><span class="sxs-lookup"><span data-stu-id="38670-124">-AccountExpires</span></span>
<span data-ttu-id="38670-125">Spécifie à quel moment le compte d’utilisateur expire.</span><span class="sxs-lookup"><span data-stu-id="38670-125">Specifies when the user account expires.</span></span>
<span data-ttu-id="38670-126">Pour obtenir un objet **DateTime** , utilisez l’applet de commande Get-Date.</span><span class="sxs-lookup"><span data-stu-id="38670-126">To obtain a **DateTime** object, use the Get-Date cmdlet.</span></span>

<span data-ttu-id="38670-127">Si vous ne souhaitez pas que le compte expire, spécifiez le paramètre *AccountNeverExpires* .</span><span class="sxs-lookup"><span data-stu-id="38670-127">If you do not want the account to expire, specify the *AccountNeverExpires* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38670-128">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="38670-128">-AccountNeverExpires</span></span>
<span data-ttu-id="38670-129">Indique que le compte n’expire pas.</span><span class="sxs-lookup"><span data-stu-id="38670-129">Indicates that the account does not expire.</span></span>

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

### <span data-ttu-id="38670-130">Description</span><span class="sxs-lookup"><span data-stu-id="38670-130">-Description</span></span>
<span data-ttu-id="38670-131">Spécifie un commentaire pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38670-131">Specifies a comment for the user account.</span></span>
<span data-ttu-id="38670-132">La longueur maximale est de 48 caractères.</span><span class="sxs-lookup"><span data-stu-id="38670-132">The maximum length is 48 characters.</span></span>

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

### <span data-ttu-id="38670-133">-FullName</span><span class="sxs-lookup"><span data-stu-id="38670-133">-FullName</span></span>
<span data-ttu-id="38670-134">Spécifie le nom complet du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38670-134">Specifies the full name for the user account.</span></span>
<span data-ttu-id="38670-135">Le nom complet est différent du nom d’utilisateur du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38670-135">The full name differs from the user name of the user account.</span></span>

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

### <span data-ttu-id="38670-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="38670-136">-InputObject</span></span>
<span data-ttu-id="38670-137">Spécifie le compte d’utilisateur modifié par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38670-137">Specifies the user account that this cmdlet changes.</span></span>
<span data-ttu-id="38670-138">Pour obtenir un compte d’utilisateur, utilisez l’applet de commande Get-LocalUser.</span><span class="sxs-lookup"><span data-stu-id="38670-138">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38670-139">-Name</span><span class="sxs-lookup"><span data-stu-id="38670-139">-Name</span></span>
<span data-ttu-id="38670-140">Spécifie le nom du compte d’utilisateur modifié par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38670-140">Specifies the name of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38670-141">-Mot de passe</span><span class="sxs-lookup"><span data-stu-id="38670-141">-Password</span></span>
<span data-ttu-id="38670-142">Spécifie un mot de passe pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38670-142">Specifies a password for the user account.</span></span>
<span data-ttu-id="38670-143">Si le compte d’utilisateur est connecté à un compte Microsoft, ne définissez pas de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="38670-143">If the user account is connected to a Microsoft account, do not set a password.</span></span>

<span data-ttu-id="38670-144">Vous pouvez utiliser `Read-Host -GetCredential` , obtenir des informations d’identification ou ConvertTo-SecureString pour créer un objet **SecureString** pour le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="38670-144">You can use `Read-Host -GetCredential`, Get-Credential, or ConvertTo-SecureString to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="38670-145">Si vous omettez les paramètres *mot de passe* et *nopassword* , **Set-LocalUser** vous invite à entrer le mot de passe de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38670-145">If you omit the *Password* and *NoPassword* parameters, **Set-LocalUser** prompts you for the user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38670-146">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="38670-146">-PasswordNeverExpires</span></span>
<span data-ttu-id="38670-147">Indique si le mot de passe expire.</span><span class="sxs-lookup"><span data-stu-id="38670-147">Indicates whether the password expires.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38670-148">-SID</span><span class="sxs-lookup"><span data-stu-id="38670-148">-SID</span></span>
<span data-ttu-id="38670-149">Spécifie l’ID de sécurité (SID) du compte d’utilisateur modifié par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38670-149">Specifies the security ID (SID) of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38670-150">-UserMayChangePassword</span><span class="sxs-lookup"><span data-stu-id="38670-150">-UserMayChangePassword</span></span>
<span data-ttu-id="38670-151">Indique que l’utilisateur peut modifier le mot de passe du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38670-151">Indicates that the user can change the password on the user account.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38670-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="38670-152">-Confirm</span></span>
<span data-ttu-id="38670-153">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38670-153">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38670-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="38670-154">-WhatIf</span></span>
<span data-ttu-id="38670-155">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38670-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="38670-156">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="38670-156">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38670-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38670-157">CommonParameters</span></span>
<span data-ttu-id="38670-158">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38670-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38670-159">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="38670-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38670-160">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="38670-160">INPUTS</span></span>

### <span data-ttu-id="38670-161">System. Management. Automation. SecurityAccountsManager. LocalUser, System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="38670-161">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="38670-162">Vous pouvez diriger un utilisateur local, une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38670-162">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="38670-163">SORTIES</span><span class="sxs-lookup"><span data-stu-id="38670-163">OUTPUTS</span></span>

### <span data-ttu-id="38670-164">Aucun</span><span class="sxs-lookup"><span data-stu-id="38670-164">None</span></span>
<span data-ttu-id="38670-165">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="38670-165">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="38670-166">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="38670-166">NOTES</span></span>

* <span data-ttu-id="38670-167">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="38670-167">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="38670-168">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="38670-168">The possible sources are as follows:</span></span>

- <span data-ttu-id="38670-169">Local</span><span class="sxs-lookup"><span data-stu-id="38670-169">Local</span></span>
- <span data-ttu-id="38670-170">Active Directory</span><span class="sxs-lookup"><span data-stu-id="38670-170">Active Directory</span></span>
- <span data-ttu-id="38670-171">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="38670-171">Azure Active Directory group</span></span>
- <span data-ttu-id="38670-172">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="38670-172">Microsoft Account</span></span>

<span data-ttu-id="38670-173">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="38670-173">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="38670-174">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="38670-174">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="38670-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="38670-175">RELATED LINKS</span></span>

[<span data-ttu-id="38670-176">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-176">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="38670-177">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-177">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="38670-178">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-178">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="38670-179">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-179">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="38670-180">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-180">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="38670-181">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="38670-181">Rename-LocalUser</span></span>](Rename-LocalUser.md)
