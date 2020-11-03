---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 0b4ec4902df2b2e93def549586e3f6cde70fadee
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205478"
---
# Enable-WSManCredSSP

## SYNOPSIS
Active l’authentification CredSSP (Credential Security Support Provider) sur un ordinateur.

## SYNTAX

### Tous

```
Enable-WSManCredSSP [-Role] <String> [[-DelegateComputer] <String[]>] [-Force] [<CommonParameters>]
```

## Description

L' `Enable-WSManCredSSP` applet de commande active l’authentification CredSSP sur un client ou sur un ordinateur serveur.
Lorsque l’authentification CredSSP est utilisée, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées. Ce type d’authentification est conçu pour les commandes qui créent une session à distance à partir d’une autre session à distance. Par exemple, si vous souhaitez exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez ce type d’authentification.

`Enable-WSManCredSSP` peut activer CredSSP sur un **client** ou un **serveur** . Pour activer CredSSP sur un client, spécifiez **client** dans le paramètre **role** . Les clients délèguent des informations d’identification explicites à un serveur lorsque l’authentification du serveur est effectuée. Pour activer CredSSP sur un serveur, spécifiez **Server** dans le paramètre **role** . Un serveur agit comme un délégué pour les clients. Pour plus d’informations, consultez **role** dans la section Parameters.

> [!CAUTION]
> L’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant. Cette pratique augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

## EXEMPLES

### Exemple 1 : déléguer les informations d’identification du client

Cet exemple permet de déléguer les informations d’identification du client à un ordinateur à l’aide du nom de domaine complet.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### Exemple 2 : déléguer les informations d’identification du client à tous les ordinateurs d’un domaine

Cet exemple permet de déléguer les informations d’identification du client à tous les ordinateurs du domaine **fabrikam.com** . Le `*` caractère générique astérisque () spécifie tous les ordinateurs.

> [!NOTE]
> L’utilisation de caractères génériques avec le paramètre **delegatecomputer** peut activer CredSSP sur plus d’ordinateurs que nécessaire.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### Exemple 3 : déléguer les informations d’identification du client à plusieurs ordinateurs

Cet exemple permet de déléguer les informations d’identification du client à plusieurs ordinateurs.

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

La `$servers` variable contient une liste de noms de serveurs. `Enable-WSManCredSSP` utilise le paramètre **role** pour spécifier le rôle **client** . **Delegatecomputer** obtient les noms d’ordinateur à partir de la `$servers` variable.

### Exemple 4 : autoriser un ordinateur à agir en tant que délégué

Cet exemple permet à un ordinateur d’agir en tant que délégué pour un autre. L' `Enable-WSManCredSSP` applet de commande, illustrée dans les exemples précédents, active uniquement l’authentification CredSSP sur le client et spécifie les ordinateurs distants qui peuvent agir en son nom. Pour que l’ordinateur distant agisse en tant que délégué pour le client, l’élément CredSSP dans le nœud **service** de wsman doit avoir la valeur true. Cet exemple affecte la valeur true à l’élément CredSSP dans le nœud **service** de wsman.

```powershell
Enable-WSManCredSSP -Role "Server"
```

### Exemple 5 : autoriser un ordinateur à agir en tant que délégué à l’aide d' Set-Item

Cet exemple permet à un ordinateur d’agir en tant que délégué pour un autre ordinateur. Les `Enable-WSManCredSSP` commandes, présentées dans les exemples précédents, activent l’authentification CredSSP uniquement sur l’ordinateur client et spécifient les ordinateurs distants qui peuvent agir au nom de l’ordinateur client. Pour que l'ordinateur distant agisse en tant que délégué pour l'ordinateur client, l'élément CredSSP dans le répertoire Service du fournisseur WSMan doit avoir la valeur true.

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

`Connect-WSMan` crée une connexion à l’ordinateur distant, Server02. `Set-Item` utilise le paramètre **path** pour spécifier l’emplacement du fournisseur **WSMan** . Le paramètre **value** définit le paramètre de **service** sur true.

## PARAMETERS

### -DelegateComputer

Spécifie les serveurs auxquels les informations d’identification du client sont déléguées. La meilleure pratique consiste à utiliser des noms de domaine complets.

Les caractères génériques sont acceptés, mais peuvent activer CredSSP sur plus d’ordinateurs que nécessaire.

Si le paramètre **role** est **client** , vous devez spécifier ce paramètre. Si le **rôle** est **serveur** , ne spécifiez pas ce paramètre.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Rôle

Spécifie s’il faut activer CredSSP en tant que client ou serveur. Les valeurs acceptables pour ce paramètre sont : **client** et **serveur** .

Si vous spécifiez **client** , les actions suivantes sont effectuées. Ces paramètres permettent au client de déléguer les informations d'identification explicites à un serveur quand l'authentification du serveur est effectuée.

- Active CredSSP sur le client.
- Affecte la valeur true au paramètre WS-Management `\<localhost|computername\>\Client\Auth\CredSSP` .
- Définit la stratégie Windows CredSSP **AllowFreshCredentials** sur **WSMan/Delegate** sur le client.

Si vous spécifiez **Server** , les actions suivantes sont effectuées. Ce paramètre de stratégie permet au serveur d'agir en tant que délégué pour les clients.

- Active CredSSP sur le serveur.
- Affecte la valeur true au paramètre WS-Management `\<localhost|computername\>\Service\Auth\CredSSP` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
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

### Élément System.Xml.Xml

Si l’authentification CredSSP est correctement activée, cette applet de commande génère un objet **XmlElement** .

## REMARQUES

Pour désactiver l’authentification CredSSP, utilisez l’applet de commande `Disable-WSManCredSSP` .

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
