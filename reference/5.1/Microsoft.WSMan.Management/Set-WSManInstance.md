---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: dcd6e50f7359aec379fdd8561804cd28b189ec32
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208662"
---
# Set-WSManInstance

## SYNOPSIS
Modifie les informations de gestion qui sont associées à une ressource.

## SYNTAX

### ComputerName (par défaut)

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## Description

L'applet de commande Set-WSManInstance modifie les informations de gestion qui sont associées à une ressource.

Cette applet de commande utilise la couche de connexion/transport WinRM pour modifier les informations.

## EXEMPLES

### Exemple 1 : désactiver un écouteur sur l’ordinateur local

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

Cette commande désactive l'écouteur https sur l'ordinateur local.

Important : le paramètre *ValueSet* respecte la casse lors de la correspondance avec les propriétés spécifiées.

Par exemple, dans cette commande,

Cette opération échoue : `-ValueSet @{enabled="False"}`

Cela s’effectue comme suit : `-ValueSet @{Enabled="False"}`

### Exemple 2 : définir la taille d’enveloppe maximale sur l’ordinateur local

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

Cette commande affecte à MaxEnvelopeSizekb la valeur 200 sur l'ordinateur local.

Important : le paramètre ValueSet respecte la casse lors de la correspondance avec les propriétés spécifiées.

Ainsi, voici ce qui se passe avec la commande ci-dessus.

Échec :-ValueSet @ {MaxEnvelopeSizeKB = "200"}

Cette opération a échoué :-ValueSet @ {MaxEnvelopeSizekb = "200"}

### Exemple 3 : désactiver un écouteur sur un ordinateur distant

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

Cette commande désactive l'écouteur https sur l'ordinateur distant SERVER02.

Important : le paramètre ValueSet respecte la casse lors de la correspondance avec les propriétés spécifiées.

Ainsi, voici ce qui se passe avec la commande ci-dessus.

Échec :-ValueSet @ {Enabled = "false"}

Cette opération a échoué :-ValueSet @ {Enabled = "false"}

## PARAMETERS

### -ApplicationName

Spécifie le nom d'application de la connexion.
La valeur par défaut du paramètre ApplicationName est « WSMAN ».
L'identificateur complet du point de terminaison distant est au format suivant :

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Par exemple :

`http://server01:8080/WSMAN`

Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.
La valeur par défaut « WSMAN » est appropriée pour la plupart des utilisations.
Ce paramètre est conçu pour être utilisé lorsque de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.
Dans ce cas, IIS héberge WS-Management (Web Services for Management) pour plus d'efficacité.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.
Les valeurs possibles sont les suivantes :

- De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.
- Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management. Il s’agit de la valeur par défaut.
- Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.
- Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide de certificats Kerberos.
- Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification. Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.
- CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification. Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.

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

Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion.
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
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

Spécifie le point de terminaison de connexion.
Le format de cette chaîne est :

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

La chaîne suivante est une valeur au format correct pour ce paramètre :

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
Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou « User@Domain.com ».
Vous pouvez également entrer un objet PSCredential, tel que celui généré par l'applet de commande Get-Credential.
Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

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

### -Dialecte

Spécifie le dialecte à utiliser dans le prédicat de filtre.
Ce peut être n'importe quel dialecte pris en charge par le service distant.
Les alias suivants peuvent être utilisés pour l'URI de dialecte :

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- Sélection `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie le chemin d'accès d'un fichier qui est utilisé pour mettre à jour une ressource de gestion.
Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.
Par exemple, la commande suivante utilise le paramètre de FilePath :

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

Cette commande appelle la méthode StopService sur le service Spouleur à l'aide des entrées fournies par un fichier.
Le contenu du fichier, Input.xml, est le suivant :

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

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

### -Fragment

Spécifie une section à l'intérieur de l'instance qui doit être mise à jour ou récupérée pour l'opération spécifiée.
Par exemple, pour obtenir l'état d'un service Spouleur, spécifiez « -Fragment Status ».

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

### -A

Transmet un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.
Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service.
N'importe quel nombre d'options peut être spécifié.

L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :

-OptionSet @{a=1;b=2;c=3}

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
Lorsque vous utilisez le protocole HTTPS, la valeur du paramètre ComputerName doit correspondre au nom commun du certificat du serveur.
Toutefois, si le paramètre SkipCNCheck est spécifié dans le cadre du paramètre SessionOption, le nom commun du certificat du serveur n'a pas à correspondre au nom d'hôte du serveur.
Le paramètre SkipCNCheck doit être utilisé uniquement pour les ordinateurs approuvés.

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

Contient l'URI de l'instance ou de la classe de ressource.
L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.
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
Le paramètre SelectorSet est utilisé lorsqu'il existe plusieurs instances de la ressource.
La valeur du paramètre SelectorSet doit être une table de hachage.
L'exemple suivant montre comment spécifier une valeur pour ce paramètre :

-SelectorSet @{Name="WinRM";ID="yyy"}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Définit un ensemble d'options étendues pour la session WS-Management.
Entrez un objet SessionOption que vous créez à l'aide de l'applet de commande New-WSManSessionOption.
Pour plus d'informations sur les options disponibles, consultez New-WSManSessionOption.

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

Spécifie que le protocole SSL (Secure Sockets Layer) doit être utilisé pour établir une connexion à l'ordinateur distant.
Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.
Le paramètre UseSSL vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de HTTP.
Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

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

### -ValueSet

Spécifie une table de hachage qui permet de modifier une ressource de gestion.
Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.
La valeur du paramètre ValueSet doit être une table de hachage.

```yaml
Type: System.Collections.Hashtable
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

### Aucun

Cette applet de commande ne génère aucune sortie.

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

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
