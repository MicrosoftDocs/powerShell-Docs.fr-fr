---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 0a68c665e8a0b504cfef416134374c5598ba55a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596299"
---
# <span data-ttu-id="25925-102">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="25925-102">Send-MailMessage</span></span>

## <span data-ttu-id="25925-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="25925-103">SYNOPSIS</span></span>
<span data-ttu-id="25925-104">Envoie un e-mail.</span><span class="sxs-lookup"><span data-stu-id="25925-104">Sends an email message.</span></span>

## <span data-ttu-id="25925-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="25925-105">SYNTAX</span></span>

### <span data-ttu-id="25925-106">Tous</span><span class="sxs-lookup"><span data-stu-id="25925-106">All</span></span>

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="25925-107">Description</span><span class="sxs-lookup"><span data-stu-id="25925-107">DESCRIPTION</span></span>

<span data-ttu-id="25925-108">L' `Send-MailMessage` applet de commande envoie un message électronique à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25925-108">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="25925-109">Vous devez spécifier un serveur SMTP (Simple Mail Transfer Protocol) ou la `Send-MailMessage` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="25925-109">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="25925-110">Utilisez le paramètre **SmtpServer** ou définissez la `$PSEmailServer` variable sur un serveur SMTP valide.</span><span class="sxs-lookup"><span data-stu-id="25925-110">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="25925-111">La valeur assignée à `$PSEmailServer` est le paramètre SMTP par défaut pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25925-111">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="25925-112">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="25925-112">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="25925-113">L' `Send-MailMessage` applet de commande est obsolète.</span><span class="sxs-lookup"><span data-stu-id="25925-113">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="25925-114">Cette applet de commande ne garantit pas des connexions sécurisées aux serveurs SMTP.</span><span class="sxs-lookup"><span data-stu-id="25925-114">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="25925-115">Bien qu’aucun remplacement immédiat ne soit disponible dans PowerShell, nous vous recommandons de ne pas utiliser `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="25925-115">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="25925-116">Pour plus d’informations, consultez la remarque sur la compatibilité de la [plateforme](https://aka.ms/SendMailMessage).</span><span class="sxs-lookup"><span data-stu-id="25925-116">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="25925-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="25925-117">EXAMPLES</span></span>

### <span data-ttu-id="25925-118">Exemple 1 : envoyer un e-mail d’une personne à une autre personne</span><span class="sxs-lookup"><span data-stu-id="25925-118">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="25925-119">Cet exemple envoie un message électronique d’une personne à une autre personne.</span><span class="sxs-lookup"><span data-stu-id="25925-119">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="25925-120">Les paramètres **from**, **to** et **Subject** sont requis par `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="25925-120">The **From**, **To**, and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="25925-121">Cet exemple utilise la variable par défaut `$PSEmailServer` pour le serveur SMTP, le paramètre **SmtpServer** n’est donc pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="25925-121">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="25925-122">L' `Send-MailMessage` applet de commande utilise le paramètre **from** pour spécifier l’expéditeur du message.</span><span class="sxs-lookup"><span data-stu-id="25925-122">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="25925-123">Le paramètre **to** spécifie le destinataire du message.</span><span class="sxs-lookup"><span data-stu-id="25925-123">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="25925-124">Le paramètre **Subject** utilise la chaîne de texte **test mail** comme message, car le paramètre **Body** facultatif n’est pas inclus.</span><span class="sxs-lookup"><span data-stu-id="25925-124">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="25925-125">Exemple 2 : envoyer une pièce jointe</span><span class="sxs-lookup"><span data-stu-id="25925-125">Example 2: Send an attachment</span></span>

<span data-ttu-id="25925-126">Cet exemple envoie un message électronique avec une pièce jointe.</span><span class="sxs-lookup"><span data-stu-id="25925-126">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="25925-127">L' `Send-MailMessage` applet de commande utilise le paramètre **from** pour spécifier l’expéditeur du message.</span><span class="sxs-lookup"><span data-stu-id="25925-127">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="25925-128">Le paramètre **to** spécifie les destinataires du message.</span><span class="sxs-lookup"><span data-stu-id="25925-128">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="25925-129">Le paramètre **Subject** décrit le contenu du message.</span><span class="sxs-lookup"><span data-stu-id="25925-129">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="25925-130">Le paramètre **Body** est le contenu du message.</span><span class="sxs-lookup"><span data-stu-id="25925-130">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="25925-131">Le paramètre **Attachments** spécifie le fichier dans le répertoire actif qui est joint au message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-131">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="25925-132">Le paramètre **Priority** définit le message sur **High** Priority.</span><span class="sxs-lookup"><span data-stu-id="25925-132">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="25925-133">Le paramètre **-DeliveryNotificationOption** spécifie deux valeurs, **onSuccess** et **OnFailure**.</span><span class="sxs-lookup"><span data-stu-id="25925-133">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="25925-134">L’expéditeur recevra des notifications par courrier électronique pour confirmer la réussite ou l’échec de la remise du message.</span><span class="sxs-lookup"><span data-stu-id="25925-134">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="25925-135">Le paramètre **SmtpServer** définit le serveur SMTP sur **SMTP.fabrikam.com**.</span><span class="sxs-lookup"><span data-stu-id="25925-135">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="25925-136">Exemple 3 : envoyer un e-mail à une liste de diffusion</span><span class="sxs-lookup"><span data-stu-id="25925-136">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="25925-137">Cet exemple envoie un message électronique à une liste de diffusion.</span><span class="sxs-lookup"><span data-stu-id="25925-137">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="25925-138">L' `Send-MailMessage` applet de commande utilise le paramètre **from** pour spécifier l’expéditeur du message.</span><span class="sxs-lookup"><span data-stu-id="25925-138">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="25925-139">Le paramètre **to** spécifie les destinataires du message.</span><span class="sxs-lookup"><span data-stu-id="25925-139">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="25925-140">Le paramètre **CC** envoie une copie du message au destinataire spécifié.</span><span class="sxs-lookup"><span data-stu-id="25925-140">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="25925-141">Le paramètre **BCC** envoie une copie aveugle du message.</span><span class="sxs-lookup"><span data-stu-id="25925-141">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="25925-142">Une copie aveugle est une adresse de messagerie qui est masquée par les autres destinataires.</span><span class="sxs-lookup"><span data-stu-id="25925-142">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="25925-143">Le paramètre **Subject** est le message, car le paramètre **Body** facultatif n’est pas inclus.</span><span class="sxs-lookup"><span data-stu-id="25925-143">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="25925-144">Le paramètre **Credential** spécifie les informations d’identification d’un administrateur de domaine utilisées pour envoyer le message.</span><span class="sxs-lookup"><span data-stu-id="25925-144">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="25925-145">Le paramètre **UseSsl** spécifie que le protocole SSL (Secure Socket Layer) crée une connexion sécurisée.</span><span class="sxs-lookup"><span data-stu-id="25925-145">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="25925-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="25925-146">PARAMETERS</span></span>

### <span data-ttu-id="25925-147">-Pièces jointes</span><span class="sxs-lookup"><span data-stu-id="25925-147">-Attachments</span></span>

<span data-ttu-id="25925-148">Spécifie le chemin d’accès et les noms de fichiers à joindre au message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-148">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="25925-149">Vous pouvez utiliser ce paramètre ou diriger les chemins d’accès et les noms de fichiers vers `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="25925-149">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-150">-CCI</span><span class="sxs-lookup"><span data-stu-id="25925-150">-Bcc</span></span>

<span data-ttu-id="25925-151">Spécifie les adresses de messagerie qui reçoivent une copie du message, mais qui ne sont pas répertoriées en tant que destinataires du message.</span><span class="sxs-lookup"><span data-stu-id="25925-151">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="25925-152">Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="25925-152">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-153">-Corps</span><span class="sxs-lookup"><span data-stu-id="25925-153">-Body</span></span>

<span data-ttu-id="25925-154">Spécifie le contenu du message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-154">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-155">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="25925-155">-BodyAsHtml</span></span>

<span data-ttu-id="25925-156">Spécifie que la valeur du paramètre **Body** contient du code html.</span><span class="sxs-lookup"><span data-stu-id="25925-156">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-157">-CC</span><span class="sxs-lookup"><span data-stu-id="25925-157">-Cc</span></span>

<span data-ttu-id="25925-158">Spécifie les adresses de messagerie auxquelles une copie carbone (CC) du message électronique est envoyée.</span><span class="sxs-lookup"><span data-stu-id="25925-158">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="25925-159">Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="25925-159">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="25925-160">-Credential</span></span>

<span data-ttu-id="25925-161">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="25925-161">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="25925-162">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="25925-162">The default is the current user.</span></span>

<span data-ttu-id="25925-163">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**.</span><span class="sxs-lookup"><span data-stu-id="25925-163">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="25925-164">Ou entrez un objet **PSCredential** , tel que celui de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="25925-164">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="25925-165">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="25925-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="25925-166">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="25925-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-167">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="25925-167">-DeliveryNotificationOption</span></span>

<span data-ttu-id="25925-168">Spécifie les options de notification de remise pour le message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-168">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="25925-169">Vous pouvez spécifier plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="25925-169">You can specify multiple values.</span></span>
<span data-ttu-id="25925-170">None est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="25925-170">None is the default value.</span></span> <span data-ttu-id="25925-171">L’alias de ce paramètre est **DNO**.</span><span class="sxs-lookup"><span data-stu-id="25925-171">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="25925-172">Les notifications de remise sont envoyées à l’adresse dans le paramètre **from** .</span><span class="sxs-lookup"><span data-stu-id="25925-172">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="25925-173">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="25925-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="25925-174">`None`: Aucune notification.</span><span class="sxs-lookup"><span data-stu-id="25925-174">`None`: No notification.</span></span>
- <span data-ttu-id="25925-175">`OnSuccess`: Notifier si la remise a réussi.</span><span class="sxs-lookup"><span data-stu-id="25925-175">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="25925-176">`OnFailure`: Avertit si la remise échoue.</span><span class="sxs-lookup"><span data-stu-id="25925-176">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="25925-177">`Delay`: Notifier si la remise est retardée.</span><span class="sxs-lookup"><span data-stu-id="25925-177">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="25925-178">`Never`: Ne jamais notifier.</span><span class="sxs-lookup"><span data-stu-id="25925-178">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-179">-Encoding</span><span class="sxs-lookup"><span data-stu-id="25925-179">-Encoding</span></span>

<span data-ttu-id="25925-180">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="25925-180">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="25925-181">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="25925-181">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="25925-182">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="25925-182">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="25925-183">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="25925-183">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="25925-184">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="25925-184">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="25925-185">`bigendianutf32`: Encode au format UTF-32 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="25925-185">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="25925-186">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="25925-186">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="25925-187">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="25925-187">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="25925-188">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="25925-188">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="25925-189">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="25925-189">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="25925-190">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="25925-190">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="25925-191">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="25925-191">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="25925-192">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="25925-192">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="25925-193">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="25925-193">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="25925-194">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="25925-194">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-195">-À partir de</span><span class="sxs-lookup"><span data-stu-id="25925-195">-From</span></span>

<span data-ttu-id="25925-196">Le paramètre **from** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="25925-196">The **From** parameter is required.</span></span> <span data-ttu-id="25925-197">Ce paramètre spécifie l’adresse e-mail de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="25925-197">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="25925-198">Entrez un nom (facultatif) et une adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="25925-198">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-199">-Port</span><span class="sxs-lookup"><span data-stu-id="25925-199">-Port</span></span>

<span data-ttu-id="25925-200">Spécifie un autre port du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="25925-200">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="25925-201">La valeur par défaut est 25, qui est le port SMTP par défaut.</span><span class="sxs-lookup"><span data-stu-id="25925-201">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-202">-Priority</span><span class="sxs-lookup"><span data-stu-id="25925-202">-Priority</span></span>

<span data-ttu-id="25925-203">Spécifie la priorité du message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-203">Specifies the priority of the email message.</span></span> <span data-ttu-id="25925-204">Normal est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="25925-204">Normal is the default.</span></span> <span data-ttu-id="25925-205">Les valeurs acceptables pour ce paramètre sont normal, High et Low.</span><span class="sxs-lookup"><span data-stu-id="25925-205">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-206">-ReplyTo</span><span class="sxs-lookup"><span data-stu-id="25925-206">-ReplyTo</span></span>

<span data-ttu-id="25925-207">Spécifie des adresses de messagerie supplémentaires (autres que l’adresse de provenance) à utiliser pour répondre à ce message.</span><span class="sxs-lookup"><span data-stu-id="25925-207">Specifies additional email addresses (other than the From address) to use to reply to this message.</span></span>
<span data-ttu-id="25925-208">Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="25925-208">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

<span data-ttu-id="25925-209">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="25925-209">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-210">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="25925-210">-SmtpServer</span></span>

<span data-ttu-id="25925-211">Spécifie le nom du serveur SMTP qui envoie le message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-211">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="25925-212">La valeur par défaut est la valeur de la `$PSEmailServer` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="25925-212">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="25925-213">Si la variable de préférence n’est pas définie et que ce paramètre n’est pas utilisé, la `Send-MailMessage` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="25925-213">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-214">-Subject</span><span class="sxs-lookup"><span data-stu-id="25925-214">-Subject</span></span>

<span data-ttu-id="25925-215">Le paramètre **Subject** n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="25925-215">The **Subject** parameter isn't required.</span></span> <span data-ttu-id="25925-216">Ce paramètre spécifie l’objet du message électronique.</span><span class="sxs-lookup"><span data-stu-id="25925-216">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-217">-To</span><span class="sxs-lookup"><span data-stu-id="25925-217">-To</span></span>

<span data-ttu-id="25925-218">Le paramètre **to** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="25925-218">The **To** parameter is required.</span></span> <span data-ttu-id="25925-219">Ce paramètre spécifie l’adresse e-mail du destinataire.</span><span class="sxs-lookup"><span data-stu-id="25925-219">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="25925-220">S’il y a plusieurs destinataires, séparez leurs adresses par une virgule ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="25925-220">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="25925-221">Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="25925-221">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25925-222">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="25925-222">-UseSsl</span></span>

<span data-ttu-id="25925-223">Le protocole SSL (Secure Sockets Layer) (SSL) est utilisé pour établir une connexion sécurisée à l’ordinateur distant pour envoyer du courrier.</span><span class="sxs-lookup"><span data-stu-id="25925-223">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="25925-224">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="25925-224">By default, SSL is not used.</span></span>

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

### <span data-ttu-id="25925-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25925-225">CommonParameters</span></span>

<span data-ttu-id="25925-226">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="25925-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25925-227">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="25925-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25925-228">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="25925-228">INPUTS</span></span>

### <span data-ttu-id="25925-229">System.String</span><span class="sxs-lookup"><span data-stu-id="25925-229">System.String</span></span>

<span data-ttu-id="25925-230">Vous pouvez diriger le chemin d’accès et les noms de fichiers des pièces jointes vers `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="25925-230">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="25925-231">SORTIES</span><span class="sxs-lookup"><span data-stu-id="25925-231">OUTPUTS</span></span>

### <span data-ttu-id="25925-232">None</span><span class="sxs-lookup"><span data-stu-id="25925-232">None</span></span>

<span data-ttu-id="25925-233">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="25925-233">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="25925-234">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="25925-234">NOTES</span></span>

## <span data-ttu-id="25925-235">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="25925-235">RELATED LINKS</span></span>

[<span data-ttu-id="25925-236">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="25925-236">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="25925-237">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="25925-237">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

