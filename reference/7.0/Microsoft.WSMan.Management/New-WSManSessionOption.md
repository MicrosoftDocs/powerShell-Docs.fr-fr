---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: 2fa100a0388b91a060e1778d703f73e2c85957a8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201554"
---
# New-WSManSessionOption

## SYNOPSIS
Crée une table de hachage des options de session à utiliser comme paramètres d’entrée pour les applets de commande WS-Management.

## SYNTAX

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## Description
L’applet **de commande New-WSManSessionOption** crée une table de hachage de l’option de session WSMan qui peut être passée aux applets de commande WSMan :

- Get-WSManInstance
- Set-WSManInstance
- Invoke-WSManAction
- Connect-WSMan

## EXEMPLES

### Exemple 1 : créer une connexion qui utilise des options de connexion

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

Cet exemple crée une connexion à l’ordinateur SERVEUR01 distant à l’aide des options de connexion définies par **New-WSManSessionOption** .

La première commande utilise **New-WSManSessionOption** pour stocker un ensemble d’options de paramètres de connexion dans la variable $a.
Dans cet exemple, les options de session définissent un délai de connexion de 30 secondes (30 000 millisecondes).

La deuxième commande utilise le paramètre *SessionOption* pour transmettre les informations d’identification stockées dans la variable $A à **connect-wsman** .
Ensuite, **connect-wsman** se connecte à l’ordinateur SERVEUR01 distant à l’aide des options de session spécifiées.

**Connect-wsman** est généralement utilisé dans le contexte du fournisseur WSMan pour se connecter à un ordinateur distant, dans le cas présent l’ordinateur SERVEUR01.
Toutefois, vous pouvez utiliser l'applet de commande pour établir des connexions aux ordinateurs distants avant de choisir le fournisseur WSMan.
Ces connexions s’affichent dans la liste **ComputerName** .

## PARAMETERS

### -NoEncryption
Indique que la connexion n’utilise pas le chiffrement pour les opérations distantes sur HTTP.

Par défaut, le trafic non chiffré n’est pas activé.
Elle doit être activée dans la configuration locale.

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

### -OperationTimeout
Spécifie le délai d’attente, en millisecondes, pour l’opération de WS-Management.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType
Spécifie le mécanisme par lequel le serveur proxy est trouvé.
Les valeurs valides pour ce paramètre sont :

- ProxyIEConfig.
Utilisez la configuration du proxy Internet Explorer pour l’utilisateur actuel.
- ProxyWinHttpConfig.
Le client WSMan utilise les paramètres de proxy configurés pour WinHTTP, à l’aide de l’utilitaire ProxyCfg.exe.
- ProxyAutoDetect.
Force la détection automatique d’un serveur proxy.
- ProxyNoProxyServer.
N’utilisez pas de serveur proxy.
Résolvez tous les noms d’hôte localement.

La valeur par défaut est ProxyIEConfig.

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication
Spécifie la méthode d'authentification à utiliser au niveau du proxy.
Les valeurs valides pour ce paramètre sont :

- De base.
L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.
- Digest.
Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.
- Negotiate.
L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.
Le protocole Kerberos et NTLM en sont des exemples.

La valeur par défaut est Negotiate.

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential
Spécifie un compte d’utilisateur qui a l’autorisation d’accéder via un proxy Web intermédiaire.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck
Spécifie que, lorsqu’il se connecte via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.
Utilisez cette option uniquement lorsque l’ordinateur distant est approuvé par une autre méthode, par exemple, si l’ordinateur distant fait partie d’un réseau qui est physiquement sécurisé et isolé ou que l’ordinateur distant est listé comme un hôte approuvé dans la configuration de WS-Management.

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

### -SkipCNCheck
Spécifie que le nom commun de certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.
Ce paramètre est utilisé uniquement dans les opérations à distance avec HTTPS.
Cette option ne doit être utilisée que pour les ordinateurs approuvés.

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

### -SkipRevocationCheck
Indique que la connexion ne valide pas l’état de révocation sur le certificat de serveur.

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

### -SPNPort
Spécifie un numéro de port à ajouter au nom de principal du service (SPN) de connexion du serveur distant.
Un nom SPN est utilisé quand le mécanisme d'authentification est Kerberos ou par négociation.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16
Indique que la connexion encode la demande au format UTF16 au lieu du format UTF8.
La valeur par défaut est l'encodage UTF8.

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

## SORTIES

### SessionOption

## REMARQUES

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
