---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 2ff87c8d4b714be3b5be3bfe8f384b4c89c25272
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208905"
---
# Get-Credential

## SYNOPSIS
Obtient un objet d'informations d'identification basé sur un nom d'utilisateur et un mot de passe.

## SYNTAX

### CredentialSet (par défaut)

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### MessageSet

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## Description

L' `Get-Credential` applet de commande crée un objet d’informations d’identification pour un nom d’utilisateur et un mot de passe spécifiés. Vous pouvez utiliser l'objet d'informations d'identification dans les opérations de sécurité.

L' `Get-Credential` applet de commande invite l’utilisateur à entrer un mot de passe ou un nom d’utilisateur et un mot de passe. Vous pouvez utiliser le paramètre **message** pour spécifier un message personnalisé dans l’invite de ligne de commande.

## EXEMPLES

### Exemple 1

```powershell
$c = Get-Credential
```

Cette commande obtient un objet d’informations d’identification et l’enregistre dans la `$c` variable.

Lorsque vous entrez la commande, vous êtes invité à entrer un nom d’utilisateur et un mot de passe. Lorsque vous entrez les informations demandées, l’applet de commande crée un objet **PSCredential** qui représente les informations d’identification de l’utilisateur et l’enregistre dans la `$c` variable.

Vous pouvez utiliser l'objet comme entrée dans les applets de commande qui impliquent une authentification utilisateur, telles que celles comportant un paramètre **Credential**. Toutefois, certains fournisseurs installés avec PowerShell ne prennent pas en charge le paramètre **Credential** .

### Exemple 2

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

Ces commandes utilisent un objet d’informations d’identification que l' `Get-Credential` applet de commande renvoie pour authentifier un utilisateur sur un ordinateur distant afin qu’il puisse utiliser Windows Management Instrumentation (WMI) pour gérer l’ordinateur.

La première commande obtient un objet d’informations d’identification et l’enregistre dans la `$c` variable. La deuxième commande utilise l’objet Credential dans une `Get-CimInstance` commande. Cette commande obtient des informations sur les lecteurs de disque sur l'ordinateur Server01.

### Exemple 3

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

Cette commande montre comment inclure une `Get-Credential` commande dans une  `Get-CimInstance` commande.

Cette commande utilise la `Get-CimInstance` cmdlet pour obtenir des informations sur le BIOS sur l’ordinateur SERVEUR01. Elle utilise le paramètre **Credential** pour authentifier l’utilisateur, Domaine01\Utilisateur01 et une `Get-Credential` commande en tant que valeur du paramètre **Credential** .

### Exemple 4

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

Cet exemple crée une information d'identification qui inclut un nom d'utilisateur sans nom de domaine.

La première commande obtient des informations d’identification avec le nom d’utilisateur User01 et les stocke dans la `$c` variable.
La deuxième commande affiche la valeur de la propriété **Username** de l'objet d'informations d'identification résultant.

### Exemple 5

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

Cette commande utilise la méthode **PromptForCredential** pour inviter l'utilisateur à indiquer ses nom d'utilisateur et mot de passe. La commande enregistre les informations d’identification résultantes dans la `$Credential` variable.

La méthode **PromptForCredential** est une alternative à l’utilisation de l’applet de commande `Get-Credential` . Lorsque vous utilisez **PromptForCredential** , vous pouvez spécifier la légende, les messages et le nom d’utilisateur qui s’affichent dans l’invite.

Pour plus d’informations, consultez la documentation [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) dans le kit de développement logiciel (SDK).

### Exemple 6

Cet exemple montre comment créer un objet d’informations d’identification identique à l’objet `Get-Credential` retourné sans inviter l’utilisateur. Cette méthode nécessite un mot de passe en texte brut, ce qui peut violer les normes de sécurité dans certaines entreprises.

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

La première commande enregistre le nom du compte d’utilisateur dans le `$User` paramètre. La valeur doit avoir le format « Domaine\Utilisateur » ou « Nom d'ordinateur\Utilisateur ».

La deuxième commande utilise l' `ConvertTo-SecureString` applet de commande pour créer une chaîne sécurisée à partir d’un mot de passe en texte brut. La commande utilise le paramètre **AsPlainText** pour indiquer que la chaîne est du texte brut, et le paramètre **Force** pour confirmer que vous comprenez les risques de l'utilisation de texte brut.

La troisième commande utilise l' `New-Object` applet de commande pour créer un objet **PSCredential** à partir des valeurs des `$User` `$PWord` variables et.

### Exemple 7

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

Cette commande utilise les paramètres **message** et **nom d’utilisateur** de l’applet de commande `Get-Credential` . Ce format de commande est conçu pour les fonctions et les scripts partagés. Dans ce cas, le message indique à l'utilisateur pourquoi les informations d'identification sont nécessaires tout en l'assurant implicitement que la demande est légitime.

### Exemple 8

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

Cette commande obtient des informations d'identification de l'ordinateur distant Server01. La commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Credential` commande sur l’ordinateur distant. La sortie affiche le message de sécurité distant qui `Get-Credential` comprend dans l’invite d’authentification.

## PARAMETERS

### -Credential

Spécifie un nom d’utilisateur pour les informations d’identification, tel que **User01** ou **Domaine01\Utilisateur01**. Le nom du paramètre, `-Credential` , est facultatif.

Lorsque vous envoyez la commande et spécifiez un nom d’utilisateur, vous êtes invité à entrer un mot de passe. Si vous omettez ce paramètre, vous êtes invité à entrer un nom d’utilisateur et un mot de passe.

À compter de PowerShell 3,0, si vous entrez un nom d’utilisateur sans domaine, `Get-Credential` n’insère plus de barre oblique inverse avant le nom.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -Message

Spécifie un message qui s'affiche dans l'invite d'authentification. Ce paramètre est conçu pour une utilisation dans une fonction ou un script. Vous pouvez utiliser le message pour expliquer à l'utilisateur pourquoi vous demandez des informations d'identification et comment elles seront utilisées.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### -Title

Définit le texte de la ligne de titre pour l’invite d’authentification dans la console.

Ce paramètre a été introduit dans PowerShell 6,0.

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

### -UserName

Spécifie un nom d'utilisateur. L'invite d'authentification demande un mot de passe pour le nom d'utilisateur. Par défaut, le nom d'utilisateur est vide et l'invite d'authentification demande un nom d'utilisateur et un mot de passe.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSCredential

`Get-Credential` retourne un objet d’informations d’identification.

## REMARQUES

Vous pouvez utiliser l’objet **PSCredential** qui est `Get-Credential` créé dans les applets de commande qui demandent l’authentification utilisateur, telles que celles avec un paramètre **Credential** .

Le paramètre **Credential** n’est pas pris en charge par tous les fournisseurs installés avec PowerShell.
À compter de PowerShell 3,0, il est pris en charge sur les applets de commande SELECT, telles que les `Get-Content` applets de commande et `New-PSDrive` .

## LIENS CONNEXES

[PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
