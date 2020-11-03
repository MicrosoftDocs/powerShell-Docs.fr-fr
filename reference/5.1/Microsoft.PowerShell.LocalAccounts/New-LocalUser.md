---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203622"
---
# <span data-ttu-id="2f686-103">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-103">New-LocalUser</span></span>

## <span data-ttu-id="2f686-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2f686-104">SYNOPSIS</span></span>

<span data-ttu-id="2f686-105">Crée un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="2f686-105">Creates a local user account.</span></span>

## <span data-ttu-id="2f686-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f686-106">SYNTAX</span></span>

### <span data-ttu-id="2f686-107">Mot de passe (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2f686-107">Password (Default)</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f686-108">Nopassword</span><span class="sxs-lookup"><span data-stu-id="2f686-108">NoPassword</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2f686-109">Description</span><span class="sxs-lookup"><span data-stu-id="2f686-109">DESCRIPTION</span></span>

<span data-ttu-id="2f686-110">L' `New-LocalUser` applet de commande crée un compte d’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="2f686-110">The `New-LocalUser` cmdlet creates a local user account.</span></span> <span data-ttu-id="2f686-111">Cette applet de commande crée un compte d’utilisateur local ou un compte d’utilisateur local qui est connecté à un compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2f686-111">This cmdlet creates a local user account or a local user account that is connected to a Microsoft account.</span></span>

> [!NOTE]
> <span data-ttu-id="2f686-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="2f686-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="2f686-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2f686-113">EXAMPLES</span></span>

### <span data-ttu-id="2f686-114">Exemple 1 : créer un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="2f686-114">Example 1: Create a user account</span></span>

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

<span data-ttu-id="2f686-115">Cette commande crée un compte d’utilisateur local et ne spécifie pas les paramètres de **AccountExpires dans** ou **de mot de passe** .</span><span class="sxs-lookup"><span data-stu-id="2f686-115">This command creates a local user account and does not specify the **AccountExpires** or **Password** parameters.</span></span> <span data-ttu-id="2f686-116">Par conséquent, le compte n’expire pas ou n’a pas de mot de passe par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f686-116">Therefore, the account doesn't expire or have a password by default.</span></span>

### <span data-ttu-id="2f686-117">Exemple 2 : créer un compte d’utilisateur avec un mot de passe</span><span class="sxs-lookup"><span data-stu-id="2f686-117">Example 2: Create a user account that has a password</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

<span data-ttu-id="2f686-118">La première commande vous invite à entrer un mot de passe à l’aide de l’applet de commande `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="2f686-118">The first command prompts you for a password by using the `Read-Host` cmdlet.</span></span> <span data-ttu-id="2f686-119">La commande stocke le mot de passe en tant que chaîne sécurisée dans la `$Password` variable.</span><span class="sxs-lookup"><span data-stu-id="2f686-119">The command stores the password as a secure string in the `$Password` variable.</span></span>

<span data-ttu-id="2f686-120">La deuxième commande crée un compte d’utilisateur local à l’aide du mot de passe stocké dans `$Password` .</span><span class="sxs-lookup"><span data-stu-id="2f686-120">The second command creates a local user account by using the password stored in `$Password`.</span></span> <span data-ttu-id="2f686-121">La commande spécifie un nom d’utilisateur, un nom complet et une description pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-121">The command specifies a user name, full name, and description for the user account.</span></span>

## <span data-ttu-id="2f686-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f686-122">PARAMETERS</span></span>

### <span data-ttu-id="2f686-123">-AccountExpires dans</span><span class="sxs-lookup"><span data-stu-id="2f686-123">-AccountExpires</span></span>

<span data-ttu-id="2f686-124">Spécifie à quel moment le compte d’utilisateur expire.</span><span class="sxs-lookup"><span data-stu-id="2f686-124">Specifies when the user account expires.</span></span> <span data-ttu-id="2f686-125">Pour obtenir un objet **DateTime** , utilisez l' `Get-Date` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f686-125">To obtain a **DateTime** object, use the `Get-Date` cmdlet.</span></span>
<span data-ttu-id="2f686-126">Si vous ne spécifiez pas ce paramètre, le compte n’expire pas.</span><span class="sxs-lookup"><span data-stu-id="2f686-126">If you do not specify this parameter, the account does not expire.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-127">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="2f686-127">-AccountNeverExpires</span></span>

<span data-ttu-id="2f686-128">Indique que le compte n’expire pas.</span><span class="sxs-lookup"><span data-stu-id="2f686-128">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-129">Description</span><span class="sxs-lookup"><span data-stu-id="2f686-129">-Description</span></span>

<span data-ttu-id="2f686-130">Spécifie un commentaire pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-130">Specifies a comment for the user account.</span></span>
<span data-ttu-id="2f686-131">La longueur maximale est de 48 caractères.</span><span class="sxs-lookup"><span data-stu-id="2f686-131">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-132">-Désactivé</span><span class="sxs-lookup"><span data-stu-id="2f686-132">-Disabled</span></span>

<span data-ttu-id="2f686-133">Indique que cette applet de commande crée le compte d’utilisateur comme étant désactivé.</span><span class="sxs-lookup"><span data-stu-id="2f686-133">Indicates that this cmdlet creates the user account as disabled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-134">-FullName</span><span class="sxs-lookup"><span data-stu-id="2f686-134">-FullName</span></span>

<span data-ttu-id="2f686-135">Spécifie le nom complet du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-135">Specifies the full name for the user account.</span></span> <span data-ttu-id="2f686-136">Le nom complet est différent du nom d’utilisateur du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-136">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-137">-Name</span><span class="sxs-lookup"><span data-stu-id="2f686-137">-Name</span></span>

<span data-ttu-id="2f686-138">Spécifie le nom d’utilisateur du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-138">Specifies the user name for the user account.</span></span>

<span data-ttu-id="2f686-139">Si vous créez un compte d’utilisateur local pour le système local, le nom d’utilisateur peut contenir jusqu’à 20 caractères majuscules ou minuscules.</span><span class="sxs-lookup"><span data-stu-id="2f686-139">If you create a local user account for the local system, the user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="2f686-140">Un nom d’utilisateur ne peut pas contenir les caractères suivants :</span><span class="sxs-lookup"><span data-stu-id="2f686-140">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="2f686-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="2f686-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

<span data-ttu-id="2f686-142">Un nom d’utilisateur ne peut pas être composé uniquement de points `.` ou d’espaces.</span><span class="sxs-lookup"><span data-stu-id="2f686-142">A user name cannot consist only of periods `.` or spaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-143">-Nopassword</span><span class="sxs-lookup"><span data-stu-id="2f686-143">-NoPassword</span></span>

<span data-ttu-id="2f686-144">Indique que le compte d’utilisateur n’a pas de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2f686-144">Indicates that the user account does not have a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-145">-Mot de passe</span><span class="sxs-lookup"><span data-stu-id="2f686-145">-Password</span></span>

<span data-ttu-id="2f686-146">Spécifie un mot de passe pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-146">Specifies a password for the user account.</span></span> <span data-ttu-id="2f686-147">Vous pouvez utiliser `Read-Host -GetCredential` , `Get-Credential` ou `ConvertTo-SecureString` pour créer un objet **SecureString** pour le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2f686-147">You can use `Read-Host -GetCredential`, `Get-Credential`, or `ConvertTo-SecureString` to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="2f686-148">Si vous omettez les paramètres **mot de passe** et **nopassword** , vous `New-LocalUser` invite à entrer le mot de passe du nouvel utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-148">If you omit the **Password** and **NoPassword** parameters, `New-LocalUser` prompts you for the new user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-149">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="2f686-149">-PasswordNeverExpires</span></span>

<span data-ttu-id="2f686-150">Indique si le mot de passe expire.</span><span class="sxs-lookup"><span data-stu-id="2f686-150">Indicates whether the password expires.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-151">-UserMayNotChangePassword</span><span class="sxs-lookup"><span data-stu-id="2f686-151">-UserMayNotChangePassword</span></span>

<span data-ttu-id="2f686-152">Indique que l’utilisateur ne peut pas modifier le mot de passe du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-152">Indicates that the user cannot change the password on the user account.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f686-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f686-153">-Confirm</span></span>

<span data-ttu-id="2f686-154">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f686-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2f686-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f686-155">-WhatIf</span></span>

<span data-ttu-id="2f686-156">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f686-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2f686-157">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2f686-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2f686-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f686-158">CommonParameters</span></span>

<span data-ttu-id="2f686-159">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2f686-159">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2f686-160">Pour plus d’informations, consultez [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2f686-160">For more information, see [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2f686-161">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2f686-161">INPUTS</span></span>

### <span data-ttu-id="2f686-162">System. String, System. DateTime, System. Boolean, System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="2f686-162">System.String, System.DateTime, System.Boolean, System.Security.SecureString</span></span>

<span data-ttu-id="2f686-163">Vous pouvez diriger une chaîne, un objet **DateTime** , une valeur booléenne ou une chaîne sécurisée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2f686-163">You can pipe a string, a **DateTime** object, a boolean value, or a secure string to this cmdlet.</span></span>

## <span data-ttu-id="2f686-164">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2f686-164">OUTPUTS</span></span>

### <span data-ttu-id="2f686-165">System. Management. Automation. SecurityAccountsManager. LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-165">System.Management.Automation.SecurityAccountsManager.LocalUser</span></span>

<span data-ttu-id="2f686-166">Cette applet de commande retourne un objet **LocalUser** .</span><span class="sxs-lookup"><span data-stu-id="2f686-166">This cmdlet returns a **LocalUser** object.</span></span>
<span data-ttu-id="2f686-167">Cet objet fournit des informations sur le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-167">This object provides information about the user account.</span></span>

## <span data-ttu-id="2f686-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2f686-168">NOTES</span></span>

- <span data-ttu-id="2f686-169">Un nom d’utilisateur ne peut pas être identique à un autre nom d’utilisateur ou de groupe sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f686-169">A user name cannot be identical to any other user name or group name on the computer.</span></span> <span data-ttu-id="2f686-170">Un nom d’utilisateur ne peut pas être composé uniquement de points `.` ou d’espaces.</span><span class="sxs-lookup"><span data-stu-id="2f686-170">A user name cannot consist only of periods `.` or spaces.</span></span> <span data-ttu-id="2f686-171">Un nom d’utilisateur peut contenir jusqu’à 20 caractères majuscules ou minuscules.</span><span class="sxs-lookup"><span data-stu-id="2f686-171">A user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="2f686-172">Un nom d’utilisateur ne peut pas contenir les caractères suivants :</span><span class="sxs-lookup"><span data-stu-id="2f686-172">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="2f686-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="2f686-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

- <span data-ttu-id="2f686-174">Un mot de passe peut contenir jusqu’à 127 caractères.</span><span class="sxs-lookup"><span data-stu-id="2f686-174">A password can contain up to 127 characters.</span></span>
- <span data-ttu-id="2f686-175">La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f686-175">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="2f686-176">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f686-176">The possible sources are as follows:</span></span>

  - <span data-ttu-id="2f686-177">Local</span><span class="sxs-lookup"><span data-stu-id="2f686-177">Local</span></span>
  - <span data-ttu-id="2f686-178">Active Directory</span><span class="sxs-lookup"><span data-stu-id="2f686-178">Active Directory</span></span>
  - <span data-ttu-id="2f686-179">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2f686-179">Azure Active Directory group</span></span>
  - <span data-ttu-id="2f686-180">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="2f686-180">Microsoft Account</span></span>

> [!NOTE]
> <span data-ttu-id="2f686-181">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="2f686-181">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="2f686-182">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="2f686-182">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="2f686-183">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2f686-183">RELATED LINKS</span></span>

[<span data-ttu-id="2f686-184">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-184">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="2f686-185">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-185">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="2f686-186">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-186">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="2f686-187">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-187">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="2f686-188">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-188">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="2f686-189">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2f686-189">Set-LocalUser</span></span>](Set-LocalUser.md)
