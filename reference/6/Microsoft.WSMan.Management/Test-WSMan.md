---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 0cf40af09354314a28af216642d09a5c1fa7479d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202546"
---
# Test-WSMan

## SYNOPSIS
Teste si le service WinRM est en cours d'exécution sur un ordinateur local ou distant.

## SYNTAX

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## Description

L’applet de commande **Test-WSMan** soumet une demande d’identification qui détermine si le service WinRM est en cours d’exécution sur un ordinateur local ou distant.
Si l'ordinateur testé exécute le service, l'applet de commande affiche le schéma d'identité WS-Management, la version du protocole, le fournisseur du produit et la version du produit du service testé.

## EXEMPLES

### Exemple 1 : déterminer l’état du service WinRM

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

Cette commande détermine si le service WinRM est en cours d'exécution sur l'ordinateur local ou sur un ordinateur distant.

### Exemple 2 : déterminer l’état du service WinRM sur un ordinateur distant

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

Cette commande détermine si le service WinRM est en cours d’exécution sur l’ordinateur SERVEUR01.

### Exemple 3 : déterminer l’état du service WinRM et la version du système d’exploitation

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

Cette commande vérifie si le service WS-Management (WinRM) est en cours d’exécution sur l’ordinateur local à l’aide du paramètre d’authentification.

L’utilisation du paramètre d’authentification permet à **Test-WSMan** de retourner la version du système d’exploitation.

### Exemple 4 : déterminer l’état du service WinRM et la version du système d’exploitation sur un ordinateur distant

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

Cette commande vérifie si le service WS-Management (WinRM) est en cours d’exécution sur l’ordinateur nommé SERVEUR01 à l’aide du paramètre d’authentification.

L’utilisation du paramètre d’authentification permet à **Test-WSMan** de retourner la version du système d’exploitation.

## PARAMETERS

### -ApplicationName

Spécifie le nom d'application de la connexion.
La valeur par défaut du paramètre *applicationName* est WSMan.
L'identificateur complet du point de terminaison distant est au format suivant :

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Par exemple : `http://server01:8080/WSMAN`

Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.
Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.
Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.
Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.

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

### -Authentification

Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.
Les valeurs valides pour ce paramètre sont :

- De base.
L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.
- Par défaut.
Utilisez la méthode d'authentification implémentée par le protocole WS-Management.
Il s’agit de la valeur par défaut.
- Digest.
Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.
- Kerberos.
L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.
- Negotiate.
L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.
Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.
- CredSSP.
Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.
Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.

ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.
Cette pratique augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

Important : Si vous ne spécifiez pas le paramètre *d’authentification* ,, la demande **Test-WSMan** est envoyée de manière anonyme à l’ordinateur distant, sans utiliser l’authentification.
Si la demande est rendue anonyme, elle ne retourne aucune information spécifique à la version du système d’exploitation.
Au lieu de cela, cette applet de commande affiche des valeurs NULL pour la version du système d’exploitation et le niveau de Service Pack (système d’exploitation : 0.0.0 SP : 0,0).

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.
Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client.
Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.

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

### -ComputerName

Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.
La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.
Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.
L'ordinateur local est la valeur par défaut.
Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.
Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.
Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .
Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.
Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Spécifie le port à utiliser lorsque le client se connecte au service WinRM.
Lorsque le transport est HTTP, le port par défaut est 80.
Lorsque le transport est HTTPS, le port par défaut est 443.

Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.

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

### -UseSSL

Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.
Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.
Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.
Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

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

### Aucun

Cette applet de commande n’accepte aucune entrée.

## SORTIES

### Aucun

Cette applet de commande ne génère aucun objet de sortie.

## REMARQUES

* Par défaut, l’applet de commande **Test-WSMan** interroge le service WinRM sans utiliser l’authentification, et ne retourne aucune information spécifique à la version du système d’exploitation. Au lieu de cela, elle affiche des valeurs NULL pour la version du système d’exploitation et le niveau de Service Pack (système d’exploitation : 0.0.0 SP : 0,0).

*

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)
