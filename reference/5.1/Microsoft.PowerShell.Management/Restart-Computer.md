---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205418"
---
# Restart-Computer

## SYNOPSIS
Redémarre le système d’exploitation sur les ordinateurs locaux et distants.

## SYNTAX

### DefaultSet (par défaut)

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AsJobSet

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Restart-Computer` applet de commande redémarre le système d’exploitation sur les ordinateurs locaux et distants.

Vous pouvez utiliser les paramètres de `Restart-Computer` pour exécuter les opérations de redémarrage en tant que tâche en arrière-plan, spécifier les niveaux d’authentification et d’autres informations d’identification, pour limiter les opérations qui s’exécutent en même temps et pour forcer un redémarrage immédiat.

À partir de Windows PowerShell 3,0, vous pouvez attendre la fin du redémarrage avant d’exécuter la commande suivante. Spécifiez un délai d’attente et un intervalle de requête, puis attendez que certains services soient disponibles sur l’ordinateur redémarré. Cette fonctionnalité facilite `Restart-Computer` l’utilisation de dans les scripts et les fonctions.

Vous pouvez utiliser le protocole WS-Management (WSMan) pour redémarrer l’ordinateur, dans le cas où les appels DCOM (Distributed Component Object Model) sont bloqués, par exemple par un pare-feu d’entreprise. Pour plus d’informations, consultez [protocole WS-Management](/windows/desktop/WinRM/ws-management-protocol).

Cette applet de commande requiert uniquement la communication à distance Windows PowerShell lorsque vous utilisez le paramètre **AsJob** dans une commande.

## EXEMPLES

### Exemple 1 : redémarrer l’ordinateur local

`Restart-Computer` redémarre l’ordinateur local.

```powershell
Restart-Computer
```

### Exemple 2 : redémarrer plusieurs ordinateurs

`Restart-Computer` peut redémarrer les ordinateurs locaux et distants. Le paramètre **ComputerName** accepte un tableau de noms d’ordinateurs.

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### Exemple 3 : redémarrer les ordinateurs en tant que tâche en arrière-plan

Ces commandes exécutent une `Restart-Computer` commande en tant que tâche en arrière-plan sur deux ordinateurs distants, puis obtiennent les résultats.

Étant donné que **AsJob** crée la tâche sur l’ordinateur local et retourne automatiquement les résultats à l’ordinateur local, vous pouvez exécuter `Receive-Job` en tant que commande locale.

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** et **Server02** . Le paramètre **AsJob** exécute la commande en tant que tâche en arrière-plan. L’objet de traitement est stocké dans la `$Job` variable. `$Job` est envoyé par le pipeline à l’applet de commande `Receive-Job` qui obtient les résultats.

### Exemple 4 : redémarrer un ordinateur distant

`Restart-Computer` redémarre un ordinateur distant avec des paramètres d’authentification et d’emprunt d’identité personnalisés.

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** . Le paramètre d' **emprunt d’identité** spécifie anonyme pour masquer l’identité du demandeur. Le paramètre **DcomAuthentication** spécifie PacketIntegrity comme niveau d’authentification de la connexion.

### Exemple 5 : forcer le redémarrage des ordinateurs listés dans un fichier texte

Cet exemple force un redémarrage immédiat des ordinateurs listés dans le `Domain01.txt` fichier. Les noms d’ordinateurs du fichier texte sont stockés dans une variable. Le paramètre **force** force un redémarrage immédiat et le paramètre **ThrottleLimit** limite le nombre de connexions simultanées.

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

`Get-Content` utilise le paramètre **path** pour obtenir une liste de noms d’ordinateurs à partir d’un fichier texte, **Domain01.txt** . Les noms des ordinateurs sont stockés dans la variable `$Names` . `Get-Credential` vous invite à entrer un nom d’utilisateur et un mot de passe, et stocke les valeurs dans la variable `$Creds` . `Restart-Computer` utilise les paramètres **ComputerName** et **Credential** avec leurs variables. Le paramètre **force** provoque un redémarrage immédiat de chaque ordinateur. Le paramètre **ThrottleLimit** limite la commande à 10 connexions simultanées.

### Exemple 6 : redémarrer un ordinateur distant et attendre PowerShell

`Restart-Computer` redémarre l’ordinateur distant, puis attend jusqu’à 5 minutes (300 secondes) que PowerShell soit disponible sur l’ordinateur redémarré avant de continuer.

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** . Le paramètre **Wait** attend la fin du redémarrage. **Pour** spécifie que PowerShell peut exécuter des commandes sur l’ordinateur distant. Le paramètre **timeout** spécifie une attente de cinq minutes. Le paramètre **delay** interroge l’ordinateur distant toutes les deux secondes pour déterminer s’il est redémarré.

### Exemple 7 : redémarrer un ordinateur à l’aide du protocole WSMan

`Restart-Computer` redémarre l’ordinateur distant à l’aide du protocole WSMan au lieu du protocole par défaut DCOM. L’authentification Kerberos détermine si l’utilisateur actuel est autorisé à redémarrer l’ordinateur distant.

Ces paramètres sont conçus pour les entreprises dans lesquelles les redémarrages basés sur DCOM échouent, car DCOM est bloqué. Par exemple, par un pare-feu.

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant **SERVEUR01** .
Le paramètre **Protocol** spécifie d’utiliser le protocole WSMan. Le paramètre **WsmanAuthentication** spécifie la méthode d’authentification comme **Kerberos** .

## PARAMETERS

### -AsJob

Indique que `Restart-Computer` s’exécute en tant que tâche en arrière-plan.

Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance. Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** . Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

Lorsque vous spécifiez le paramètre **AsJob** , la commande retourne immédiatement un objet qui représente la tâche en arrière-plan. Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche. La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local. Pour gérer le travail, utilisez les applets de commande **Job** . Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.

Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie un nom d’ordinateur ou un tableau de noms d’ordinateurs séparés par des virgules. `Restart-Computer` accepte les objets **ComputerName** du ou des variables.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point `.` ou localhost.

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

Si le paramètre **ComputerName** n’est pas spécifié, `Restart-Computer` redémarre l’ordinateur local.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

Spécifie le niveau d’authentification utilisé pour la connexion WMI. `Restart-Computer` utilise WMI.

Les valeurs autorisées sont :

- **Appel** : authentification com au niveau de l’appel
- **Connect** : authentification com au niveau de la connexion
- **Par défaut** : authentification Windows
- **None** : aucune authentification com
- **Paquet** : authentification com au niveau du paquet.
- **PacketIntegrity** : authentification com au niveau de l’intégrité du paquet
- **PacketPrivacy** : authentification com au niveau de la confidentialité des paquets.
- **Inchangé** : le niveau d’authentification est le même que la commande précédente.

Pour plus d’informations, consultez [énumération AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Délai

Spécifie la fréquence des requêtes, en secondes. PowerShell interroge le service spécifié par le paramètre **for** pour déterminer si le service est disponible après le redémarrage de l’ordinateur.

Ce paramètre est valide uniquement avec les paramètres **Wait** et **for** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

Si le paramètre **delay** n’est pas spécifié, `Restart-Computer` utilise un délai de cinq secondes.

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Pour

Spécifie le comportement de PowerShell, car il attend que le service ou la fonctionnalité spécifié soit disponible après le redémarrage de l’ordinateur. Ce paramètre est valide uniquement avec le paramètre **Wait** .

Les valeurs valides pour ce paramètre sont :

- **Default** : attend le redémarrage de PowerShell.
- **PowerShell** : peut exécuter des commandes dans une session à distance PowerShell sur l’ordinateur.
- **WMI** : reçoit une réponse à une requête de Win32_ComputerSystem pour l’ordinateur.
- **WinRM** : peut établir une session à distance sur l’ordinateur à l’aide de WS-Management.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force un redémarrage immédiat de l’ordinateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Emprunt d’identité

Spécifie le niveau d’emprunt d’identité utilisé par cette applet de commande pour appeler WMI. `Restart-Computer` utilise WMI.
Les valeurs valides pour ce paramètre sont :

- **Default** : emprunt d’identité par défaut. En dépit du nom, il ne s’agit pas de la valeur par défaut.
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Spécifie le protocole à utiliser pour redémarrer les ordinateurs. Les valeurs valides sont **WSMan** et **DCOM** .

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

Si le paramètre **ThrottleLimit** n’est pas spécifié ou si la valeur 0 est utilisée, `Restart-Computer` utilise un maximum de 32 connexions simultanées.

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout

Spécifie la durée de l'attente, en secondes. Lorsque le délai d’attente est écoulé, `Restart-Computer` retourne à l’invite de commandes, même si les ordinateurs ne sont pas redémarrés.

Le paramètre **timeout** est valide uniquement avec le paramètre **Wait** . Le **délai d'** attente remplace la période d’attente indéfinie du paramètre **Wait** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

`Restart-Computer` supprime l’invite PowerShell et bloque le pipeline jusqu’à ce que les ordinateurs aient redémarré. Vous pouvez utiliser ce paramètre dans un script pour redémarrer les ordinateurs, puis continuer le traitement une fois le redémarrage terminé.

Le paramètre **Wait** attend indéfiniment que les ordinateurs redémarrent. Vous pouvez utiliser le **délai d’expiration** pour ajuster le minutage et les paramètres **de** **délai** et pour attendre que des services particuliers soient disponibles sur les ordinateurs redémarrés.

Le paramètre **Wait** n’est pas valide lorsque vous redémarrez l’ordinateur local. Si la valeur du paramètre **ComputerName** contient les noms des ordinateurs distants et de l’ordinateur local, `Restart-Computer` génère une erreur sans fin d' **attente** sur l’ordinateur local, mais attend que les ordinateurs distants redémarrent.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur. Ce paramètre a été introduit dans Windows PowerShell 3.0.

Les valeurs acceptables pour ce paramètre sont les suivantes : de **base** , **CredSSP** , **par défaut** , **Digest** , **Kerberos** et **Negotiate** .

Pour plus d’informations, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!WARNING]
> L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer l’exécution `Restart-Computer` .

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

### -WhatIf

Montre ce qui se passerait si le `Restart-Computer` s’exécute. L' `Restart-Computer` applet de commande n’est pas exécutée.

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

### System.String

`Restart-Computer` accepte les noms d’ordinateur à partir du ou des variables.

Dans Windows PowerShell 2.0, le paramètre **ComputerName** accepte l'entrée provenant du pipeline uniquement par nom de propriété. Dans Windows PowerShell 3,0 et versions ultérieures, le paramètre **ComputerName** prend en entrée le pipeline par valeur.

## SORTIES

### Aucun, System. Management. Automation. RemotingJob

Si vous spécifiez le paramètre **AsJob** , `Restart-Computer` retourne un objet de traitement. Sinon, aucune sortie n’est générée.

## REMARQUES

- `Restart-Computer` fonctionne uniquement sur les ordinateurs exécutant Windows et requiert WinRM et WMI pour arrêter un système, y compris le système local.
- `Restart-Computer` utilise la [méthode Win32Shutdown](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) de la classe [WIN32_OPERATINGSYSTEM](/windows/desktop/CIMWin32Prov/win32-operatingsystem) Windows Management Instrumentation (WMI).  Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.

Dans Windows PowerShell 2,0, le paramètre **AsJob** ne fonctionne pas de façon fiable lorsque vous redémarrez ou arrêtez des ordinateurs distants. Dans Windows PowerShell 3.0, l'implémentation est modifiée pour résoudre ce problème.

## LIENS CONNEXES

[À propos de Windows Remote Management](/windows/desktop/WinRM/about-windows-remote-management)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Protocole Gestion des services web](/windows/desktop/WinRM/ws-management-protocol)
