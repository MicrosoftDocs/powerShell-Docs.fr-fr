---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205414"
---
# Stop-Computer

## SYNOPSIS
Arrête les ordinateurs locaux et distants.

## SYNTAX

### Tous

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Stop-Computer` applet de commande arrête l’ordinateur local et les ordinateurs distants.

Vous pouvez utiliser les paramètres de `Stop-Computer` pour exécuter les opérations d’arrêt en tant que tâche en arrière-plan, spécifier les niveaux d’authentification et d’autres informations d’identification, pour limiter les connexions simultanées créées pour exécuter la commande et forcer l’arrêt immédiat.

Cette applet de commande ne requiert pas la communication à distance PowerShell, sauf si vous utilisez le paramètre **AsJob** .

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

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants. Le paramètre **AsJob** exécute la commande en tant que tâche en arrière-plan. Les objets de traitement sont stockés dans la `$j` variable.

Les objets de traitement dans la `$j` variable sont envoyés dans le pipeline à `Receive-Job` , qui obtient les résultats de la tâche. Les objets sont stockés dans la `$results` variable. La `$results` variable affiche les informations sur la tâche dans la console PowerShell.

Étant donné que **AsJob** crée la tâche sur l’ordinateur local et retourne automatiquement les résultats à l’ordinateur local, vous pouvez exécuter `Receive-Job` en tant que commande locale.

### Exemple 4 : arrêter un ordinateur distant

Cet exemple arrête un ordinateur distant à l’aide de l’authentification spécifiée.

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant. Le paramètre d' **emprunt d’identité** spécifie un emprunt d’identité personnalisé et le paramètre **DcomAuthentication** spécifie les paramètres au niveau de l’authentification.

### Exemple 5 : arrêter des ordinateurs dans un domaine

Dans cet exemple, les commandes forcent l’arrêt immédiat de tous les ordinateurs dans un domaine spécifié.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

`Get-Content` utilise le paramètre **path** pour obtenir un fichier dans le répertoire actif avec la liste des ordinateurs du domaine. Les objets sont stockés dans la `$s` variable.

`Get-Credential` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un administrateur de domaine. Les informations d’identification sont stockées dans la `$c` variable.

`Stop-Computer` arrête les ordinateurs spécifiés avec la liste des ordinateurs du paramètre **ComputerName** dans la `$s` variable. Le paramètre **force** force un arrêt immédiat. Le paramètre **ThrottleLimit** limite la commande à 10 connexions simultanées. Le paramètre **Credential** envoie les informations d’identification enregistrées dans la `$c` variable.

## PARAMETERS

### -AsJob

Indique que cette applet de commande s’exécute en tant que tâche en arrière-plan.

Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** . Pour plus d'informations, consultez [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).

Lorsque vous spécifiez le paramètre **AsJob** , la commande retourne immédiatement un objet qui représente la tâche en arrière-plan. Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche. La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local. Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.

Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) et [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).

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

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

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

### -DcomAuthentication

Spécifie le niveau d’authentification que cette applet de commande utilise avec WMI. `Stop-Computer` utilise WMI. La valeur par défaut est **Packet** .

Les valeurs valides pour ce paramètre sont :

- **Par défaut** : authentification Windows.
- **None** : aucune authentification com.
- **Connect** : authentification com au niveau de la connexion.
- **Appel** : authentification com au niveau de l’appel.
- **Paquet** : authentification com au niveau du paquet.
- **PacketIntegrity** : authentification com au niveau de l’intégrité du paquet.
- **PacketPrivacy** : authentification com au niveau de la confidentialité des paquets.
- Non **modifié** : identique à la commande précédente.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
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

### -Emprunt d’identité

Spécifie le niveau d’emprunt d’identité à utiliser lorsque cette applet de commande appelle WMI. La valeur par défaut est **Impersonate** .

`Stop-Computer` utilise WMI. Les valeurs valides pour ce paramètre sont :

- **Default** : emprunt d’identité par défaut.
- **Anonymous** : masque l’identité de l’appelant.
- **Identify** : permet aux objets d’interroger les informations d’identification de l’appelant.
- **Impersonate** : permet aux objets d’utiliser les informations d’identification de l’appelant.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Spécifie le protocole à utiliser pour redémarrer les ordinateurs. Les valeurs acceptables pour ce paramètre sont les suivantes : **WSMan** et **DCOM** . La valeur par défaut est **DCOM** .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

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

### -WsmanAuthentication

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan. La valeur par défaut est **Default** .

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

### Aucun

Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### None ou System. Management. Automation. RemotingJob

L’applet de commande retourne un objet **System. Management. Automation. RemotingJob** , si vous spécifiez le paramètre **AsJob** . Dans le cas contraire, elle ne génère aucune sortie.

## REMARQUES

Cette applet de commande utilise la méthode **Win32Shutdown** de la classe WMI **Win32_OperatingSystem** . Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.

## LIENS CONNEXES

[Add-Computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Test-Connection](Test-Connection.md)
