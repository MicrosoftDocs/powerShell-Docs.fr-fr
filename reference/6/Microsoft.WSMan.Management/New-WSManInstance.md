---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: cab18c513be5427f06165ae0558ad87653d23e35
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205574"
---
# New-WSManInstance

## SYNOPSIS
Crée une instance d'une ressource de gestion.

## SYNTAX

### ComputerName (par défaut)

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## Description

L' `New-WSManInstance` applet de commande crée une nouvelle instance d’une ressource de gestion. Elle utilise un URI de ressource et une valeur définie ou un fichier d'entrée pour créer l'instance de la ressource de gestion.

Cette applet de commande utilise la couche de connexion/transport WinRM pour créer l'instance de ressource de gestion.

## EXEMPLES

### Exemple 1 : créer un écouteur HTTPs

Cette commande crée une instance d'un écouteur HTTPS WS-Management sur toutes les adresses IP.

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## PARAMETERS

### -ApplicationName

Spécifie le nom d'application de la connexion. La valeur par défaut du paramètre **applicationName** est **WSMan** . L'identificateur complet du point de terminaison distant est au format suivant :

`<transport>://<server>:<port>/<ApplicationName>`

Par exemple :

`http://server01:8080/WSMAN`

Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée. Ce paramètre par défaut de **WSMan** est adapté à la plupart des utilisations. Ce paramètre est conçu pour être utilisé lorsque de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell. Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.

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

Spécifie le mécanisme d’authentification à utiliser au niveau du serveur. Les valeurs possibles sont les suivantes :

- De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.
- Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management. Il s’agit de la valeur par défaut.
- Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.
- Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide des certificats Kerberos.
- Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification. Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.
- CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification. Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.

> [!CAUTION]
> CredSSP délègue les informations d'identification de l'utilisateur d'un ordinateur local à un ordinateur distant. Cette pratique augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

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

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :.

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

Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion. La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP. Utilisez le nom de l’ordinateur local, utilisez localhost ou un point ( `.` ) pour spécifier l’ordinateur local. L'ordinateur local est la valeur par défaut. Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet. Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.

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

`<Transport>://<Server>:<Port>/<ApplicationName>`

La chaîne suivante est une valeur au format correct pour ce paramètre :

`http://Server01:8080/WSMAN`

L’URI doit être complet.

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel. Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou « User@Domain.com ». Ou entrez un objet PSCredential, tel que celui retourné par l’applet de commande `Get-Credential` . Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

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

### -FilePath

Spécifie le chemin d'accès d'un fichier qui est utilisé pour créer une ressource de gestion. Vous spécifiez la ressource de gestion à l’aide du paramètre **resourceuri** et du paramètre **SelectorSet** . Par exemple, la commande suivante utilise le paramètre **file** :

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

Cette commande appelle la méthode **StopService** sur le service Spooler en utilisant l’entrée d’un fichier. Le fichier, `Input.xml` , contient le contenu suivant :

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -A

Transmet un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande. Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service. N'importe quel nombre d'options peut être spécifié.

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

Spécifie le port à utiliser lorsque le client se connecte au service WinRM. Lorsque le transport est HTTP, le port par défaut est 80. Lorsque le transport est HTTPS, le port par défaut est 443.

Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre **ComputerName** doit correspondre au nom commun du certificat du serveur. Toutefois, si le paramètre **SkipCNCheck** est spécifié dans le cadre du paramètre **SessionOption** , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur. Le paramètre **SkipCNCheck** doit être utilisé uniquement pour les ordinateurs approuvés.

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

Contient l'URI de l'instance ou de la classe de ressource. L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource. Par exemple :

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

Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières. Le paramètre **SelectorSet** est utilisé lorsque plusieurs instances de la ressource existent. La valeur du paramètre **SelectorSet** doit être une table de hachage.

L'exemple suivant montre comment spécifier une valeur pour ce paramètre :

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -SessionOption

Définit un ensemble d'options étendues pour la session WS-Management. Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande `New-WSManSessionOption` . Pour plus d’informations sur les options disponibles, consultez `New-WSManSessionOption` .

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

Spécifie que le protocole SSL (Secure Sockets Layer) doit être utilisé pour établir une connexion à l'ordinateur distant. Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau. Le paramètre **UseSSL** vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http. Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ValueSet

Spécifie une table de hachage qui permet de modifier une ressource de gestion. Vous spécifiez la ressource de gestion à l’aide du paramètre **resourceuri** et du paramètre **SelectorSet** . La valeur du paramètre **ValueSet** doit être une table de hachage.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

L' `Set-WmiInstance` applet de commande, une applet de commande Windows Management Instrumentation (WMI), est similaire.
`Set-WmiInstance` utilise la couche de connexion/transport DCOM pour créer ou mettre à jour des instances WMI.

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
