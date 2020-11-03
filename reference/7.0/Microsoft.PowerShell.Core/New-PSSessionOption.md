---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: 3a9336fedece67c2c84532f226cec01de14cbb2a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201622"
---
# New-PSSessionOption

## SYNOPSIS
Crée un objet qui contient des options avancées pour une session PSSession.

## SYNTAX

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## Description

L' `New-PSSessionOption` applet de commande crée un objet qui contient des options avancées pour une session gérée par l’utilisateur ( **PSSession** ). Vous pouvez utiliser l’objet comme valeur du paramètre **SessionOption** des applets de commande qui créent une **session PSSession** , comme `New-PSSession` , `Enter-PSSession` et `Invoke-Command` .

Sans paramètres, `New-PSSessionOption` génère un objet qui contient les valeurs par défaut pour toutes les options. Comme toutes les propriétés peuvent être modifiées, vous pouvez utiliser l'objet résultant comme modèle et créer des objets d'option standard pour votre entreprise.

Vous pouvez également enregistrer un objet d’option de session dans la `$PSSessionOption` variable de préférence. Les valeurs de cette variable établissent de nouvelles valeurs par défaut pour les options de session. Elles sont effectives quand aucune option de session n'est définie pour la session, et elles sont prioritaires sur les options définies dans la configuration de session. Vous pouvez cependant les remplacer en spécifiant des options de session ou un objet d'option de session dans une applet de commande qui crée une session. Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

Quand vous utilisez un objet d'option de session dans une applet de commande qui crée une session, les valeurs d'option de session sont prioritaires sur les valeurs par défaut pour l'ensemble des sessions dans la variable de préférence $PSSessionOption et dans la configuration de la session. Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session. Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

## EXEMPLES

### Exemple 1 : créer une option de session par défaut

Cette commande crée un objet d’option de session avec toutes les valeurs par défaut.

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### Exemple 2 : configurer une session à l’aide d’un objet d’option de session

Cet exemple montre comment utiliser un objet d'option de session pour configurer une session.

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

La première commande crée un objet d’option de session et l’enregistre dans la valeur de la `$pso` variable. La deuxième commande utilise l' `New-PSSession` applet de commande pour créer une session sur l’ordinateur distant SERVEUR01. La commande utilise l’objet d’option de session dans la valeur de la `$pso` variable comme valeur du paramètre **SessionOption** de la commande.

### Exemple 3 : démarrer une session interactive

Cette commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec l’ordinateur SERVEUR01.

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

La valeur du paramètre **SessionOption** est une `New-PSSessionOption` commande qui a les paramètres **nocryption** et **NoCompression** .

La `New-PSSessionOption` commande est placée entre parenthèses pour vérifier qu’elle s’exécute avant la `Enter-PSSession` commande.

### Exemple 4 : modifier un objet d’option de session

Cet exemple montre que vous pouvez modifier l’objet d’option de session. Toutes les propriétés ont des valeurs en lecture/écriture.

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

Utilisez cette méthode pour créer un objet de session standard pour votre entreprise, puis créez-en des versions personnalisées pour des utilisations particulières.

### Exemple 5 : créer une variable de préférence

Cette commande crée une `$PSSessionOption` variable de préférence.

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

Lorsque la `$PSSessionOption` variable de préférence se produit dans la session, elle établit des valeurs par défaut pour les options dans les sessions créées à l’aide des `New-PSSession` applets de commande, `Enter-PSSession` et `Invoke-Command` .

Pour rendre la `$PSSessionOption` variable disponible dans toutes les sessions, ajoutez-la à votre session PowerShell et à votre profil PowerShell.

Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).
Pour plus d'informations sur les profils, consultez [about_Profiles](About/about_Profiles.md).

### Exemple 6 : répondre aux exigences d’une configuration de session à distance

Cet exemple montre comment utiliser un objet **SessionOption** pour satisfaire aux spécifications requises pour la configuration d'une session à distance.

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

La première commande utilise l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session qui a la propriété **SkipCNCheck** . La commande enregistre l’objet de session résultant dans la `$skipCN` variable.

La deuxième commande utilise l' `New-PSSession` applet de commande pour créer une nouvelle session sur un ordinateur distant. La `$skipCN` variable check est utilisée dans la valeur du paramètre **SessionOption** .

Étant donné que l’ordinateur est identifié par son adresse IP, la valeur du paramètre **ComputerName** ne correspond à aucun des noms communs du certificat utilisé pour protocole SSL (SSL). Par conséquent, l'option **SkipCNCheck** est requise.

### Exemple 7 : rendre les arguments disponibles pour une session à distance

Cet exemple montre comment utiliser le paramètre **ApplicationArguments** de l' `New-PSSessionOption` applet de commande pour rendre des données supplémentaires disponibles pour la session à distance.

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

La première commande crée une table de hachage avec deux clés, **Team** et **use** . La commande enregistre la table de hachage dans la `$team` variable. Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](about/about_Hash_Tables.md).

Ensuite, l' `New-PSSessionOption` applet de commande, à l’aide du paramètre **ApplicationArguments** , crée un objet d’option de session enregistré dans la `$team` variable. Lorsque `New-PSSessionOption` crée l’objet d’option de session, il convertit automatiquement la table de hachage dans la valeur du paramètre **ApplicationArguments** en un dictionnaire primitif afin que les données puissent être transmises de manière fiable à la session à distance.

L' `New-PSSession` applet de commande démarre une session sur l’ordinateur SERVEUR01. Elle utilise le paramètre **SessionOption** pour inclure les options dans la `$teamOption` variable.

L' `Invoke-Command` applet de commande montre que les données de la `$team` variable sont disponibles pour les commandes dans la session à distance. Les données s’affichent dans la propriété **ApplicationArguments** de la `$PSSenderInfo` variable automatique.

Le dernier `Invoke-Command` montre comment les données peuvent être utilisées.

## PARAMETERS

### -ApplicationArguments

Spécifie un dictionnaire primitif qui est envoyé à la session à distance. Les commandes et les scripts dans la session à distance, y compris les scripts de démarrage dans la configuration de session, peuvent trouver ce dictionnaire dans la propriété **ApplicationArguments** de la `$PSSenderInfo` variable automatique. Vous pouvez utiliser ce paramètre pour envoyer des données à la session à distance.

Pour plus d’informations, consultez [about_Hash_Tables](about/about_Hash_Tables.md), [about_session_configurations](About/about_Session_Configurations.md)et [about_Automatic_Variables](about/about_Automatic_Variables.md).

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CancelTimeout

Détermine la durée pendant laquelle PowerShell attend qu’une opération d’annulation (CTRL + C) se termine avant de se terminer.
Entrez une valeur en millisecondes.

La valeur par défaut est 60000 (une minute). Une valeur 0 (zéro) signifie qu'il n'y a pas de délai d'attente et que la commande continue indéfiniment.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

Spécifie la culture à utiliser pour la session. Entrez un nom de culture au `<languagecode2>-<country/regioncode2>` format (comme `ja-JP` ), une variable qui contient un objet **CultureInfo** ou une commande qui obtient un objet **CultureInfo** .

La valeur par défaut est `$Null` , et la culture définie dans le système d’exploitation est utilisée dans la session.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout

Détermine la durée pendant laquelle la session reste ouverte si l’ordinateur distant ne reçoit pas de communication de l’ordinateur local. Cela comprend le signal de pulsation. Quand le délai expire, la session se ferme.

La valeur du délai d’inactivité est importante si vous envisagez de vous déconnecter et de vous reconnecter à une session. Vous pouvez vous reconnecter seulement si la session n'est pas expirée.

Entrez une valeur en millisecondes. La valeur minimale est 60000 (1 minute). La valeur maximale est la valeur de la propriété **MaxIdleTimeoutms** de la configuration de session. La valeur par défaut,-1, ne définit pas un délai d’inactivité.

La session utilise le délai d’inactivité défini dans les options de session, le cas échéant. Si aucune valeur n’est définie (-1), la session utilise la valeur de la propriété **IdleTimeoutMs** de la configuration de session ou la valeur du délai d’attente de l’interpréteur de commandes WSMan ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), selon la valeur la plus petite.

Si le délai d'inactivité défini dans les options de session dépasse la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session, la commande de création d'une session échoue.

La valeur **IdleTimeoutMs** de la configuration de session **Microsoft. PowerShell** par défaut est de 7,2 millions millisecondes (2 heures). Sa valeur de **MaxIdleTimeoutMs** est de 2147483647 millisecondes ( \> 24 jours). La valeur par défaut du délai d’inactivité de l’interpréteur de commandes WSMan ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) est de 7,2 millions millisecondes (2 heures).

La valeur du délai d’inactivité d’une session peut également être modifiée lors de la déconnexion d’une session ou de la reconnexion à une session. Pour plus d’informations, consultez `Disconnect-PSSession` et `Connect-PSSession`.

Dans Windows PowerShell 2.0, la valeur par défaut du paramètre **IdleTimeout** est 240000 (4 minutes).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludePortInSPN

Comprend le numéro de port dans le nom de principal du service (SPN) utilisé pour l’authentification Kerberos, par exemple, `HTTP://<ComputerName>:5985` . Cette option permet à un client qui utilise un nom de principal du service qui n'est pas le nom par défaut de s'authentifier auprès d'un ordinateur distant qui utilise l'authentification Kerberos.

L'option est conçue pour les entreprises où plusieurs services prenant en charge l'authentification Kerberos s'exécutent sous différents comptes d'utilisateurs. Par exemple, une application IIS qui autorise l’authentification Kerberos peut exiger que le nom principal de service par défaut soit inscrit auprès d’un compte d’utilisateur différent du compte d’ordinateur. Dans ce cas, la communication à distance PowerShell ne peut pas utiliser Kerberos pour s’authentifier, car elle requiert un nom de principal du service inscrit auprès du compte d’ordinateur. Pour résoudre ce problème, les administrateurs peuvent créer des noms de principal du service différents, par exemple à l’aide de **Setspn.exe** , qui sont inscrits auprès de différents comptes d’utilisateur et peuvent les distinguer en incluant le numéro de port dans le nom de principal du service.

Pour plus d’informations, consultez [vue d’ensemble de setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -MaxConnectionRetryCount

Spécifie le nombre de tentatives de connexion de PowerShell à un ordinateur cible en cas d’échec de la tentative en cours en raison de problèmes réseau. La valeur par défaut est 5.

Ce paramètre a été ajouté pour PowerShell version 5,0.

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

### -MaximumReceivedDataSizePerCommand

Spécifie le nombre maximal d'octets que l'ordinateur local peut recevoir de l'ordinateur distant dans une même commande. Entrez une valeur en octets. Par défaut, il n'existe pas de limite de taille des données.

Cette option est conçue pour protéger les ressources sur l'ordinateur client.

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

### -MaximumReceivedObjectSize

Spécifie la taille maximale d'un objet que l'ordinateur local peut recevoir de l'ordinateur distant. Cette option est conçue pour protéger les ressources sur l'ordinateur client. Entrez une valeur en octets.

Dans Windows PowerShell 2.0, si vous omettez ce paramètre, la taille des objets n'est pas limitée. À compter de Windows PowerShell 3.0, si vous omettez ce paramètre, la valeur par défaut est 200 Mo.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

Détermine le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue. La valeur par défaut est 5. La valeur 0 (zéro) empêche toute redirection.

Cette option est utilisée dans la session uniquement lorsque le paramètre **AllowRedirection** est utilisé dans la commande qui crée la session.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCompression

Désactive la compression de paquets dans la session. La compression utilise davantage de cycles processeur, mais rend la transmission plus rapide.

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

### -NoEncryption

Désactive le chiffrement des données.

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

### -NoMachineProfile

Empêche le chargement du profil d'utilisateur Windows de l'utilisateur. Par conséquent, la session peut-être être créée plus rapidement, mais les paramètres de Registre spécifiques à l'utilisateur, les éléments comme des variables d'environnement et les certificats ne sont pas disponibles dans la session.

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

### -OpenTimeout

Détermine le temps pendant lequel l'ordinateur client attend que la connexion de la session soit établie. Quand le délai expire, la commande d'établissement de la connexion échoue. Entrez une valeur en millisecondes.

La valeur par défaut est 180000 (3 minutes). Une valeur 0 (zéro) signifie qu'il n'y a pas de délai d'attente et que la commande continue indéfiniment.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout

Détermine la durée maximale pendant laquelle une opération de la session peut s'exécuter. Quand le délai expire, l'opération échoue. Entrez une valeur en millisecondes.

La valeur par défaut est 180000 (3 minutes). Une valeur 0 (zéro) signifie qu'il n'y a pas de délai d'attente et que l'opération continue indéfiniment.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

Détermine comment la sortie de la commande est gérée dans des sessions déconnectées quand la mémoire tampon de sortie est pleine.

Si le mode de mise en mémoire tampon de sortie n'est pas défini dans la session ni dans la configuration de session, la valeur par défaut est **Block** . Les utilisateurs peuvent également changer le mode de mise en mémoire tampon de sortie lors de la déconnexion de la session.

Si vous omettez ce paramètre, la valeur de **OutputBufferingMode** de l’objet d’option de session est None. La valeur **Block** ou **Drop** remplace l'option de transport du mode de mise en mémoire tampon de sortie définie dans la configuration de session. Les valeurs valides pour ce paramètre sont :

- Bloquer. Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée.
- Drop. Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit. Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.
- Aucun. Aucun mode de mise en mémoire tampon de sortie n'est spécifié.

Pour plus d’informations sur l’option de transport mode de mise en mémoire tampon de sortie, consultez `New-PSTransportOption` .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType

Détermine quel mécanisme est utilisé pour résoudre le nom d'hôte. Les valeurs valides pour ce paramètre sont :

- IEConfig
- WinHttpConfig
- Détection automatique
- NoProxyServer
- Aucun

La valeur par défaut est Aucun.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération ProxyAccessType](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0).

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication

Spécifie la méthode d'authentification qui est utilisée pour la résolution du proxy. Les valeurs acceptables pour ce paramètre sont les suivantes : **Basic** , **Digest** et **Negotiate** . La valeur par défaut est **Negotiate** .

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0).

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Spécifie les informations d'identification à utiliser pour l'authentification du proxy. Entrez une variable qui contient un objet **PSCredential** ou une commande qui obtient un objet **PSCredential** , tel qu’une `Get-Credential` commande. Si cette option n'est pas définie, aucune information d'identification n'est spécifiée.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck

Spécifie que lorsqu’il se connecte via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.

Utilisez cette option seulement quand l'ordinateur distant est approuvé via un autre mécanisme, par exemple quand l'ordinateur distant fait partie d'un réseau qui est physiquement sécurisé et isolé, ou bien quand l'ordinateur distant est répertorié comme hôte approuvé dans une configuration WinRM.

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

### -SkipCNCheck

Spécifie que le nom commun de certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur. Cette option est utilisée seulement dans les opérations à distance utilisant le protocole HTTPS.

Utilisez cette option seulement pour des ordinateurs approuvés.

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

### -SkipRevocationCheck

Ne vérifie pas l'état de révocation du certificat serveur.

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

### -UICulture

Spécifie la culture de l'interface utilisateur à utiliser pour la session.

Les valeurs valides sont les suivantes :

- Nom de culture au `<languagecode2>-<country/regioncode2>` format, tel que `ja-JP`
- Une variable qui contient un objet **CultureInfo**
- Commande qui obtient un objet **CultureInfo** , tel que `Get-Culture`

La valeur par défaut est `$null` , et la culture d’interface utilisateur définie dans le système d’exploitation lors de la création de la session est utilisée dans la session.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16

Indique que cette applet de commande encode la demande au format UTF16 au lieu du format UTF8.

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

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. Remoting. PSSessionOption

## REMARQUES

Si le paramètre **SessionOption** n’est pas utilisé dans une commande pour créer une session **PSSession** , les options de session sont déterminées par les valeurs de propriété de la `$PSSessionOption` variable de préférence, si elle est définie. Pour plus d’informations sur la `$PSSessionOption` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options. En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.

## LIENS CONNEXES

[Enter-PSSession](Enter-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)
