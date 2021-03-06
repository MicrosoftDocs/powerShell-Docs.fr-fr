---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203146"
---
# Send-MailMessage

## SYNOPSIS
Envoie un e-mail.

## SYNTAX

### Tous

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## Description

L' `Send-MailMessage` applet de commande envoie un message électronique à partir de PowerShell.

Vous devez spécifier un serveur SMTP (Simple Mail Transfer Protocol) ou la `Send-MailMessage` commande échoue. Utilisez le paramètre **SmtpServer** ou définissez la `$PSEmailServer` variable sur un serveur SMTP valide.
La valeur assignée à `$PSEmailServer` est le paramètre SMTP par défaut pour PowerShell. Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

> [!WARNING]
> L' `Send-MailMessage` applet de commande est obsolète. Cette applet de commande ne garantit pas des connexions sécurisées aux serveurs SMTP. Bien qu’aucun remplacement immédiat ne soit disponible dans PowerShell, nous vous recommandons de ne pas utiliser `Send-MailMessage` . Pour plus d’informations, consultez la remarque sur la compatibilité de la [plateforme](https://aka.ms/SendMailMessage).

## EXEMPLES

### Exemple 1 : envoyer un e-mail d’une personne à une autre personne

Cet exemple envoie un message électronique d’une personne à une autre personne.

Les paramètres **from** , **to** et **Subject** sont requis par `Send-MailMessage` . Cet exemple utilise la variable par défaut `$PSEmailServer` pour le serveur SMTP, le paramètre **SmtpServer** n’est donc pas nécessaire.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

L' `Send-MailMessage` applet de commande utilise le paramètre **from** pour spécifier l’expéditeur du message. Le paramètre **to** spécifie le destinataire du message. Le paramètre **Subject** utilise la chaîne de texte **test mail** comme message, car le paramètre **Body** facultatif n’est pas inclus.

### Exemple 2 : envoyer une pièce jointe

Cet exemple envoie un message électronique avec une pièce jointe.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

L' `Send-MailMessage` applet de commande utilise le paramètre **from** pour spécifier l’expéditeur du message. Le paramètre **to** spécifie les destinataires du message. Le paramètre **Subject** décrit le contenu du message. Le paramètre **Body** est le contenu du message.

Le paramètre **Attachments** spécifie le fichier dans le répertoire actif qui est joint au message électronique. Le paramètre **Priority** définit le message sur **High** Priority. Le paramètre **-DeliveryNotificationOption** spécifie deux valeurs, **onSuccess** et **OnFailure** . L’expéditeur recevra des notifications par courrier électronique pour confirmer la réussite ou l’échec de la remise du message.
Le paramètre **SmtpServer** définit le serveur SMTP sur **SMTP.fabrikam.com** .

### Exemple 3 : envoyer un e-mail à une liste de diffusion

Cet exemple envoie un message électronique à une liste de diffusion.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

L' `Send-MailMessage` applet de commande utilise le paramètre **from** pour spécifier l’expéditeur du message. Le paramètre **to** spécifie les destinataires du message. Le paramètre **CC** envoie une copie du message au destinataire spécifié. Le paramètre **BCC** envoie une copie aveugle du message. Une copie aveugle est une adresse de messagerie qui est masquée par les autres destinataires. Le paramètre **Subject** est le message, car le paramètre **Body** facultatif n’est pas inclus.

Le paramètre **Credential** spécifie les informations d’identification d’un administrateur de domaine utilisées pour envoyer le message. Le paramètre **UseSsl** spécifie que le protocole SSL (Secure Socket Layer) crée une connexion sécurisée.

## PARAMETERS

### -Pièces jointes

Spécifie le chemin d’accès et les noms de fichiers à joindre au message électronique. Vous pouvez utiliser ce paramètre ou diriger les chemins d’accès et les noms de fichiers vers `Send-MailMessage` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CCI

Spécifie les adresses de messagerie qui reçoivent une copie du message, mais qui ne sont pas répertoriées en tant que destinataires du message. Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Corps

Spécifie le contenu du message électronique.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BodyAsHtml

Spécifie que la valeur du paramètre **Body** contient du code html.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CC

Spécifie les adresses de messagerie auxquelles une copie carbone (CC) du message électronique est envoyée. Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** . Ou entrez un objet **PSCredential** , tel que celui de l’applet de commande `Get-Credential` .

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DeliveryNotificationOption

Spécifie les options de notification de remise pour le message électronique. Vous pouvez spécifier plusieurs valeurs.
None est la valeur par défaut. L’alias de ce paramètre est **DNO** .

Les notifications de remise sont envoyées à l’adresse dans le paramètre **from** .

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `None`: Aucune notification.
- `OnSuccess`: Notifier si la remise a réussi.
- `OnFailure`: Avertit si la remise échoue.
- `Delay`: Notifier si la remise est retardée.
- `Never`: Ne jamais notifier.

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `Default`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ASCII` Utilise le jeu de caractères ASCII (7 bits).
- `BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).
- `OEM` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.
- `Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `UTF7` Utilise UTF-7.
- `UTF8` Utilise UTF-8.
- `UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -À partir de

Le paramètre **from** est obligatoire. Ce paramètre spécifie l’adresse e-mail de l’expéditeur. Entrez un nom (facultatif) et une adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Spécifie un autre port du serveur SMTP. La valeur par défaut est 25, qui est le port SMTP par défaut.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### -Priority

Spécifie la priorité du message électronique. Normal est la valeur par défaut. Les valeurs acceptables pour ce paramètre sont normal, High et Low.

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### -SmtpServer

Spécifie le nom du serveur SMTP qui envoie le message électronique.

La valeur par défaut est la valeur de la `$PSEmailServer` variable de préférence. Si la variable de préférence n’est pas définie et que ce paramètre n’est pas utilisé, la `Send-MailMessage` commande échoue.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Subject

Le paramètre **Subject** est obligatoire. Ce paramètre spécifie l’objet du message électronique.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

Le paramètre **to** est obligatoire. Ce paramètre spécifie l’adresse e-mail du destinataire. S’il y a plusieurs destinataires, séparez leurs adresses par une virgule ( `,` ). Entrez les noms (facultatif) et l’adresse de messagerie, par exemple `Name <someone@fabrikam.com>` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSsl

Le protocole protocole SSL (SSL) est utilisé pour établir une connexion sécurisée à l’ordinateur distant pour envoyer du courrier. Par défaut, SSL n'est pas utilisé.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger le chemin d’accès et les noms de fichiers des pièces jointes vers `Send-MailMessage` .

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)
