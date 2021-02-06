---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598146"
---
# Stop-Computer

## SYNOPSIS
Arrête les ordinateurs locaux et distants.

## SYNTAXE

### Tous

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Stop-Computer` applet de commande arrête l’ordinateur local et les ordinateurs distants.

Vous pouvez utiliser les paramètres de `Stop-Computer` pour spécifier les niveaux d’authentification et d’autres informations d’identification, et pour forcer l’arrêt immédiat.

Dans PowerShell 7,1, `Stop-Computer` a été ajouté pour Linux et MacOS. Les paramètres n’ont aucun effet sur ces plateformes. L’applet de commande appelle simplement la commande native `/sbin/shutdown` .

## EXEMPLES

### Exemple 1 : arrêter l’ordinateur local

Cet exemple arrête l’ordinateur local.

```powershell
Stop-Computer -ComputerName localhost
```

### Exemple 2 : arrêter deux ordinateurs distants et l’ordinateur local

Cet exemple arrête deux ordinateurs distants et l’ordinateur local.

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants et l’ordinateur local. Chaque ordinateur est arrêté.

### Exemple 3 : arrêter des ordinateurs distants en tant que tâche en arrière-plan

Dans cet exemple, `Stop-Computer` s’exécute en tant que tâche en arrière-plan sur deux ordinateurs distants.

L’opérateur d’arrière-plan `&` exécute la `Stop-Computer` commande en tant que tâche en arrière-plan. Pour plus d’informations, consultez [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants. L' `&` opérateur d’arrière-plan exécute la commande en tant que tâche en arrière-plan. Les objets de traitement sont stockés dans la `$j` variable.

Les objets de traitement dans la `$j` variable sont envoyés dans le pipeline à `Receive-Job` , qui obtient les résultats de la tâche. Les objets sont stockés dans la `$results` variable. La `$results` variable affiche les informations sur la tâche dans la console PowerShell.

### Exemple 4 : arrêter un ordinateur distant

Cet exemple arrête un ordinateur distant à l’aide de l’authentification spécifiée.

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant. Le paramètre **WsmanAuthentication** spécifie d’utiliser Kerberos pour établir une connexion à distance.

### Exemple 5 : arrêter des ordinateurs dans un domaine

Dans cet exemple, les commandes forcent l’arrêt immédiat de tous les ordinateurs dans un domaine spécifié.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

`Get-Content` utilise le paramètre **path** pour obtenir un fichier dans le répertoire actif avec la liste des ordinateurs du domaine. Les objets sont stockés dans la `$s` variable.

`Get-Credential` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un administrateur de domaine. Les informations d’identification sont stockées dans la `$c` variable.

`Stop-Computer` arrête les ordinateurs spécifiés avec la liste des ordinateurs du paramètre **ComputerName** dans la `$s` variable. Le paramètre **force** force un arrêt immédiat. Le paramètre **Credential** envoie les informations d’identification enregistrées dans la `$c` variable.

## PARAMETERS

### -ComputerName

Spécifie les ordinateurs à arrêter. La valeur par défaut est l'ordinateur local.

Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur ou localhost.

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’arrêt immédiat de l’ordinateur.

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

### -WsmanAuthentication

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan. La valeur par défaut est **Default**.

Les valeurs valides pour ce paramètre sont :

- Basic
- CredSSP
- Default
- Digest
- Kerberos
- Negotiate.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### None

Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### None

## REMARQUES

Cette applet de commande utilise la méthode **Win32Shutdown** de la classe WMI **Win32_OperatingSystem** . Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.

Dans PowerShell 7,1, `Stop-Computer` a été ajouté pour Linux et MacOS. Pour ces plateformes, l’applet de commande appelle la commande native `/sbin/shutdown` .

## LIENS CONNEXES

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Test-Connection](Test-Connection.md)

