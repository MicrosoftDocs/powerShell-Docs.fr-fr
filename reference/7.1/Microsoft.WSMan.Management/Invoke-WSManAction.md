---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 112b4a1e0a790c32b6a3ea2011fbc72ec86a0324
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205645"
---
# Invoke-WSManAction

## SYNOPSIS
Appelle une action sur l'objet qui est spécifié par l'URI de ressource et par les sélecteurs.

## SYNTAX

### URI (par défaut)

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## Description
**Invoke-wsmanaction** exécute une action sur l’objet spécifié par RESOURCE_URI, où les paramètres sont spécifiés par les paires clé/valeur.

Cette applet de commande utilise la couche de connexion/transport WSMan pour exécuter l'action.

## EXEMPLES

### Exemple 1 : appeler une méthode

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

Cette commande appelle la méthode **StartService** de l’instance de classe WMI Win32_Service qui correspond au service du spouleur.

La valeur de retour indique si l'action a réussi.
Si c'est le cas, la valeur de retour est 0.
Une valeur de retour de 5 indique que le service est déjà démarré.

### Exemple 2 : appeler une méthode

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

Cette commande appelle la méthode **StopService** sur le service Spooler en utilisant l’entrée d’un fichier.
Le contenu du fichier, Input.xml, est le suivant :

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### Exemple 3 : appeler une méthode avec des valeurs de paramètre spécifiées

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

Cette commande appelle la méthode **Create** de la classe Win32_Process.
Il passe à la méthode deux valeurs de paramètre, Notepad.exe et C:\.
Par conséquent, un nouveau processus est créé pour exécuter le bloc-notes et le répertoire actif du nouveau processus est défini sur C:\.

### Exemple 4 : appeler une méthode sur un ordinateur distant

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

Cette commande appelle la méthode **StartService** de l’instance de classe WMI Win32_Service qui correspond au service du spouleur.
Étant donné que le paramètre *ComputerName* est spécifié, la commande s’exécute sur l’ordinateur SERVEUR01 distant.

## PARAMETERS

### -Action
Spécifie la méthode à exécuter sur l’objet de gestion spécifié par l’ResourceURI et les sélecteurs.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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
Aliases: CURI, CU

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

### -FilePath
Spécifie le chemin d'accès d'un fichier qui est utilisé pour mettre à jour une ressource de gestion.
Vous spécifiez la ressource de gestion à l’aide du paramètre *resourceuri* et du paramètre *SelectorSet* .
Par exemple, la commande suivante utilise le paramètre *filePath* :

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

Cette commande appelle la méthode **StopService** sur le service **Spooler** en utilisant l’entrée d’un fichier.
Le contenu du fichier, Input.xml, est le suivant :

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
Accept pipeline input: True (ByPropertyName, ByValue)
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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SelectorSet
Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.
*SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.
La valeur de *SelectorSet* doit être une table de hachage.

L'exemple suivant montre comment spécifier une valeur pour ce paramètre :

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
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

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.
Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.
Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

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
Spécifie une table de hachage qui permet de modifier une ressource de gestion.
Vous spécifiez la ressource de gestion à l’aide de *resourceuri* et *SelectorSet* .
La valeur du paramètre *ValueSet* doit être une table de hachage.

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
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

