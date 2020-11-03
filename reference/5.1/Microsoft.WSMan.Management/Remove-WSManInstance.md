---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 22f74418cb8c404f7ca8d388f2a30d7db045cce2
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208665"
---
# Remove-WSManInstance

## SYNOPSIS
Supprime une instance de ressource de gestion.

## SYNTAX

### ComputerName (par défaut)

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## Description
L’applet de commande **Remove-WSManInstance** supprime une instance d’une ressource de gestion qui est spécifiée dans les paramètres *resourceuri* et *SelectorSet* .

Cette applet de commande utilise la couche de connexion/transport WinRM pour supprimer l'instance de ressource de gestion.

## EXEMPLES

### Exemple 1 : supprimer un écouteur

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

Cette commande supprime l’écouteur HTTP WS-Management sur un ordinateur.

## PARAMETERS

### -ApplicationName
Spécifie le nom d'application de la connexion.
La valeur par défaut du paramètre *applicationName* est WSMan.
L'identificateur complet du point de terminaison distant est au format suivant :

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Par exemple : `http://server01:8080/WSMAN`

Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.
Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.
Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.
Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.

```yaml
Type: System.String
Parameter Sets: ComputerName
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

Pour obtenir une empreinte numérique du certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur de certificats de Windows PowerShell.

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
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI
Spécifie le point de terminaison de connexion.
Le format de cette chaîne est le suivant :

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :

`http://Server01:8080/WSMAN`

L’URI doit être complet.

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -A
Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.
Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.
N'importe quel nombre d'options peut être spécifié.

L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port
Spécifie le port à utiliser lorsque le client se connecte au service WinRM.
Lorsque le transport est HTTP, le port par défaut est 80.
Lorsque le transport est HTTPS, le port par défaut est 443.

Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.
Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.
Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceURI
Spécifie l’URI de la classe ou de l’instance de ressource.
L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d’un préfixe et d’un chemin d’accès à une ressource.
Par exemple :

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SelectorSet
Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.
Le paramètre *SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.
La valeur de *SelectorSet* doit être une table de hachage.

L'exemple suivant montre comment spécifier une valeur pour ce paramètre :

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption
Spécifie les options étendues pour la session WS-Management.
Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.
Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL
Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.
Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.
Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.
Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

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
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* L'applet de commande Remove-WmiObject, une applet de commande WMI (Windows Management Instrumentation), est similaire. **Remove-WmiObject** utilise la couche de connexion/transport DCOM pour créer ou mettre à jour des instances WMI.

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

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
