---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: f43e84dfc5b3255d17df266bf04a05778362847b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203849"
---
# New-CimSessionOption

## SYNOPSIS
Spécifie les options avancées pour l’applet de commande New-CimSession.

## SYNTAX

### ProtocolTypeSet (par défaut)

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### WSManParameterSet

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### DcomParameterSet

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## Description

L' `New-CimSessionOption` applet de commande crée une instance d’un objet d’options de session CIM. Vous utilisez un objet d’options de session CIM comme entrée de l' `New-CimSession` applet de commande pour spécifier les options pour une session CIM.

Cette applet de commande a deux jeux de paramètres : un pour les options WsMan et un pour les options DCOM (Distributed Component Object Model). Selon les paramètres que vous utilisez, l’applet de commande retourne une instance d’options de session DCOM ou retourne des options de session WsMan.

## EXEMPLES

### Exemple 1 : créer un objet d’options de session CIM pour DCOM

Cet exemple crée un objet d’options de session CIM pour le protocole DCOM et le stocke dans une variable nommée `$so` . Le contenu de la variable est ensuite transmis à l' `New-CimSession` applet de commande.
`New-CimSession` crée ensuite une nouvelle session CIM avec le serveur distant nommé Serveur01, à l’aide des options définies dans la variable.

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### Exemple 2 : créer un objet d’options de session CIM pour WsMan

Cet exemple crée un objet d’options de session CIM pour le protocole WsMan. L’objet contient une configuration pour le mode d’authentification **Kerberos** spécifié par le paramètre **ProxyAuthentication** , les informations d’identification spécifiées par le paramètre **ProxyCredential** , et spécifie que la commande doit ignorer la vérification de l’autorité de certification, ignorer la vérification CN et utiliser SSL.

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### Exemple 3 : créer un objet d’options de session CIM avec la culture spécifiée

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

Cet exemple spécifie la culture utilisée pour la session CIM. Par défaut, la culture du client est utilisée lors de l’exécution d’opérations. Toutefois, la culture par défaut peut être substituée à l’aide du paramètre **culture** .

## PARAMETERS

### -Culture

Spécifie la culture de l’interface utilisateur à utiliser pour la session CIM. Spécifiez la valeur de ce paramètre à l’aide de l’un des formats suivants :

- Nom de culture dans un `<languagecode2>-<country/regioncode2>` format tel que « en-US ».
- Variable qui contient un objet **CultureInfo** .
- Une commande qui obtient un objet **CultureInfo** , tel que la [culture « obtenir-culture »](../Microsoft.PowerShell.Utility/Get-Culture.md) ;

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EncodePortInServicePrincipalName

Indique que la connexion Kerberos se connecte à un service dont le nom de principal du service (SPN) comprend le numéro de port du service. Ce type de connexion n’est pas courant.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Spécifie l’encodage utilisé pour le protocole WsMan. Les valeurs acceptables pour ce paramètre sont les suivantes : **default** , **UTF8** ou **Utf16** .

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -HttpPrefix

Spécifie la partie de l’URL HTTP Après le nom de l’ordinateur et le numéro de port. La modification de ce n’est pas courante. Par défaut, la valeur de ce paramètre est **/WSMan** .

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Emprunt d’identité

Crée une session DCOM pour Windows Management Instrumentation (WMI) à l’aide de l’emprunt d’identité.

Les valeurs valides pour ce paramètre sont les suivantes :

- Par défaut : DCOM peut choisir le niveau d’emprunt d’identité à l’aide de son algorithme de négociation de sécurité normal.
- None : le client est anonyme pour le serveur. Le processus serveur peut emprunter l’identité du client, mais le jeton d’emprunt d’identité ne contient aucune information et ne peut pas être utilisé.
- Identify : permet aux objets d’interroger les informations d’identification de l’appelant.
- Impersonate : permet aux objets d’utiliser les informations d’identification de l’appelant.
- Delegate : permet aux objets d’autoriser d’autres objets à utiliser les informations d’identification de l’appelant.

Si l' **emprunt d’identité** n’est pas spécifié, l' `New-CimSession` applet de commande utilise la valeur de **Impersonate** .

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxEnvelopeSizeKB

Spécifie la taille limite des messages XML WsMan pour l’une ou l’autre direction.

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoEncryption

Spécifie que le chiffrement des données est désactivé.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketIntegrity

Spécifie que la session DCOM créée à l’aide de WMI utilise la fonctionnalité _PACKETINTEGRITY_ com (Component Object Model). Par défaut, toutes les sessions CIM créées à l’aide de DCOM ont le paramètre **PacketIntegrity** défini sur **true** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketPrivacy

Crée une session DCOM vers WMI à l’aide de l' _PACKETPRIVACY_ com. Par défaut, toutes les sessions CIM créées à l’aide de DCOM ont le paramètre **PacketPrivacy** défini sur **true** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Spécifie le protocole à utiliser. Les valeurs acceptables pour ce paramètre sont les suivantes : **DCOM** , **default** ou **WSMan** .

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyAuthentication

Spécifie la méthode d’authentification à utiliser pour la résolution du proxy. Les valeurs acceptables pour ce paramètre sont les suivantes : **default** , **Digest** , **Negotiate** , **Basic** , **Kerberos** , **NtlmDomain** ou **CredSsp** .

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCertificateThumbprint

Spécifie le certificat de clé publique numérique (x. 509) d’un compte d’utilisateur pour l’authentification du proxy.
Entrez l’empreinte numérique du certificat. Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent uniquement être mappés à des comptes d’utilisateurs locaux et ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez les `Get-Item` `Get-ChildItem` applets de commande ou dans le lecteur de certificat PowerShell :.

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Spécifie les informations d'identification à utiliser pour l'authentification du proxy. Entrez l'une des informations suivantes :

- Variable qui contient un objet PSCredential.
- Commande qui obtient un objet PSCredential, tel que `Get-Credential`

Si cette option n’est pas définie, vous ne pouvez pas spécifier d’informations d’identification.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyType

Spécifie le mécanisme de résolution de nom d’hôte à utiliser. Les valeurs acceptables pour ce paramètre sont : **None** , **WinHTTP** , **auto** ou **InternetExplorer** .

La valeur par défaut de ce paramètre est **InternetExplorer** .

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCACheck

Indique que lors de la connexion via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.

Utilisez ce paramètre uniquement lorsque l’ordinateur distant est approuvé à l’aide d’un autre mécanisme, par exemple quand l’ordinateur distant fait partie d’un réseau qui est physiquement sécurisé et isolé, ou lorsque l’ordinateur distant est listé comme un hôte approuvé dans une configuration WinRM.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCNCheck

Indique que le nom commun du certificat du serveur n’a pas besoin de correspondre au nom d’hôte du serveur. Utilisez ce paramètre pour les opérations à distance uniquement avec les ordinateurs approuvés qui utilisent le protocole HTTPs.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipRevocationCheck

Indique que la vérification de la révocation des certificats de serveur est ignorée. Utilisez ce paramètre uniquement pour les ordinateurs approuvés.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UICulture

Spécifie la culture de l’interface utilisateur à utiliser pour la session CIM. Spécifiez la valeur de ce paramètre à l’aide de l’un des formats suivants :

- Nom de culture dans un `<languagecode2>-<country/regioncode2>` format tel que « en-US ».
- Variable qui contient un objet CultureInfo.
- Commande qui obtient un objet CultureInfo, tel que `Get-Culture` .

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

Indique que le protocole SSL doit être utilisé pour établir une connexion à l’ordinateur distant. Par défaut, SSL n'est pas utilisé. WsMan chiffre tout le contenu transmis sur le réseau, même en cas d’utilisation du protocole HTTP.

Ce paramètre vous permet de spécifier la protection supplémentaire du protocole HTTPs au lieu de HTTP. Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.

Il est recommandé d’utiliser ce paramètre uniquement lorsque le paramètre **PacketPrivacy** n’est pas spécifié.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucun objet d’entrée.

## SORTIES

### CIMSessionOption

Cette applet de commande retourne un objet qui contient des informations sur les options de session CIM.

## REMARQUES

## LIENS CONNEXES

[Get-ChildItem](../microsoft.powershell.management/get-childitem.md)

[Get-Credential](../microsoft.powershell.security/get-credential.md)

[Get-Culture](../microsoft.powershell.utility/get-culture.md)

[Get-Item](../microsoft.powershell.management/get-item.md)

[New-CimSession](New-CimSession.md)
