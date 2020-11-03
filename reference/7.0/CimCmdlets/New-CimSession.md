---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 85b7f62686ed5f4aef267041ef624e3d7e388038
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "93206090"
---
# New-CimSession

## SYNOPSIS

Crée une session CIM.

## SYNTAX

### CredentialParameterSet (par défaut)

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### CertificateParameterSet

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## Description

L' `New-CimSession` applet de commande crée une session CIM. Une session CIM est un objet côté client qui représente une connexion à un ordinateur local ou à un ordinateur distant. La session CIM contient des informations sur la connexion, telles que **ComputerName** , le protocole utilisé ou divers identificateurs.

Cette applet de commande retourne un objet de session CIM qui peut être utilisé par toutes les autres applets de commande CIM.

## EXEMPLES

### Exemple 1 : créer une session CIM avec les options par défaut

Cet exemple crée une session CIM locale avec les options par défaut. Si **ComputerName** n’est pas spécifié, `New-CimSession` crée une session DCOM sur l’ordinateur local.

```powershell
New-CimSession
```

### Exemple 2 : créer une session CIM sur un ordinateur spécifique

Cet exemple crée une session CIM sur l’ordinateur spécifié par **ComputerName** .
Par défaut, `New-CimSession` crée une session WSMan lorsque **ComputerName** est spécifié.

```powershell
New-CimSession -ComputerName Server01
```

### Exemple 3 : créer une session CIM sur plusieurs ordinateurs

Cet exemple crée une session CIM sur chacun des ordinateurs spécifiés par **ComputerName** , dans la liste séparée par des virgules.

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### Exemple 4 : créer une session CIM avec un nom convivial

Cet exemple crée une session CIM distante sur chacun des ordinateurs spécifiés par **ComputerName** , dans la liste séparée par des virgules, et affecte un nom convivial aux nouvelles sessions, en spécifiant **Name** .

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

Vous pouvez utiliser le nom convivial d’une session CIM pour faire référence à la session dans d’autres applets de commande CIM, par exemple, [CimSession](Get-CimSession.md).

### Exemple 5 : créer une session CIM sur un ordinateur à l’aide d’un objet PSCredential

Cet exemple crée une session CIM sur l’ordinateur spécifié par **ComputerName** , à l’aide de l’objet **PSCredential** spécifié par **Credential** et du type d’authentification spécifié par **l’authentification** .

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

Vous pouvez créer un objet **PSCredential** à l’aide de l’applet de commande [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) .

### Exemple 6 : créer une session CIM sur un ordinateur à l’aide d’un port spécifique

Cet exemple crée une session CIM sur l’ordinateur spécifié par **ComputerName** à l’aide du port TCP spécifié par **port** .

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### Exemple 7 : créer une session CIM à l’aide de DCOM

Cet exemple crée une session CIM à l’aide du protocole DCOM (Distributed COM) au lieu de WSMan.

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## PARAMETERS

### -Authentification

Spécifie le type d’authentification utilisé pour les informations d’identification de l’utilisateur. Les valeurs valides pour ce paramètre sont :

- Default
- Digest
- Negotiate
- Basic
- Kerberos
- NtlmDomain
- CredSsp

Vous ne pouvez pas utiliser le type d’authentification **NtlmDomain** pour la connexion à l’ordinateur local. L’authentification **CredSSP** est disponible uniquement dans Windows Vista, windows Server 2008 et les versions ultérieures de Windows.

> [!CAUTION]
> L’authentification CredSSP (Credential Security Service Provider) est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X. 509) d’un compte d’utilisateur qui a l’autorisation d’effectuer cette action. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez les [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) applets de commande ou dans le fournisseur de certificats PowerShell.

Pour plus d’informations, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).

```yaml
Type: System.String
Parameter Sets: CertificateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel créer la session CIM. Spécifiez un nom d’ordinateur unique ou plusieurs noms d’ordinateurs séparés par une virgule.

Si **ComputerName** n’est pas spécifié, une session CIM sur l’ordinateur local est créée. Vous pouvez spécifier la valeur du nom de l’ordinateur dans l’un des formats suivants :

- Un ou plusieurs noms NetBIOS
- Une ou plusieurs adresses IP
- Un ou plusieurs noms de domaines complets.

Si l’ordinateur se trouve dans un domaine différent de celui de l’utilisateur, vous devez spécifier le nom de domaine complet.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. Si **Credential** n’est pas spécifié, le compte d’utilisateur actuel est utilisé.

Spécifiez la valeur des **informations d’identification** à l’aide de l’un des formats suivants :

- Nom d’utilisateur : « User01 »
- Un nom de domaine et un nom d’utilisateur : « Domaine01\utilisateur01 »
- Un nom d’utilisateur principal : « User@Domain.com »
- Objet PSCredential, tel que celui retourné par l’applet de commande [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) .

Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un nom convivial pour la session CIM.

Vous pouvez utiliser le nom pour faire référence à la session CIM lors de l’utilisation d’autres applets de commande, telles que l’applet de commande [CimSession](Get-CimSession.md) .
Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.

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

### -OperationTimeoutSec

Durée pendant laquelle l’applet de commande attend une réponse du serveur.

Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.

Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion. Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPS).

Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port. Utilisez les commandes suivantes pour configurer l'écouteur :

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé. Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SessionOption

Définit des options avancées pour la nouvelle session CIM. Entrez le nom d’un objet **CimSessionOption** créé à l’aide de l’applet de commande [`New-CimSessionOption`](New-CimSessionOption.md) .

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipTestConnection

Par défaut, l' `New-CimSession` applet de commande établit une connexion avec un point de terminaison de WS-Management distant pour deux raisons : pour vérifier que le serveur distant écoute sur le numéro de port spécifié à l’aide du paramètre de **port** et pour vérifier les informations d’identification de compte spécifiées. La vérification s’effectue à l’aide d’une opération de WS-Identity standard. Vous pouvez ajouter le paramètre de commutateur **SkipTestConnection** si le point de terminaison de WS-Management distant ne peut pas utiliser WS-identify ou pour réduire le temps de transmission de données.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucune entrée.

## SORTIES

### Microsoft.Management.Infrastructure.CimSession

## REMARQUES

## LIENS CONNEXES

[Get-ChildItem](../Microsoft.Powershell.Management/Get-ChildItem.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-Item](../Microsoft.Powershell.Management/Get-Item.md)

[Get-CimSession](Get-CimSession.md)

[Remove-CimSession](Remove-CimSession.md)

[New-CimSessionOption](New-CimSessionOption.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
