---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: d8f0a8a56792a39371a307166788f047fec99a9a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603476"
---
# Invoke-Command

## SYNOPSIS
Exécute des commandes sur des ordinateurs locaux et distants.

## SYNTAXE

### InProcess (par défaut)

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathRunspace

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Session

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### Uri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### FilePathUri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### VMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### VMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### FilePathVMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### FilePathVMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### SSHHost

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### ContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### FilePathContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### SSHHostHashParam

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### FilePathSSHHost

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathSSHHostHash

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## Description

L' `Invoke-Command` applet de commande exécute des commandes sur un ordinateur local ou distant et retourne toutes les sorties des commandes, y compris les erreurs. À l’aide d’une seule `Invoke-Command` commande, vous pouvez exécuter des commandes sur plusieurs ordinateurs.

Pour exécuter une seule commande sur un ordinateur distant, utilisez le paramètre **ComputerName**. Pour exécuter une série de commandes associées qui partagent des données, utilisez l' `New-PSSession` applet de commande pour créer une session **PSSession** (une connexion permanente) sur l’ordinateur distant, puis utilisez le paramètre **session** de `Invoke-Command` pour exécuter la commande dans la session **PSSession**. Pour exécuter une commande dans une session déconnectée, utilisez le paramètre **InDisconnectedSession**. Pour exécuter une commande dans une tâche en arrière-plan, utilisez le paramètre **AsJob**.

Vous pouvez également utiliser `Invoke-Command` sur un ordinateur local en tant que commande dans un bloc de script. PowerShell exécute immédiatement le bloc de script dans une étendue enfant de l’étendue actuelle.

Avant `Invoke-Command` d’utiliser pour exécuter des commandes sur un ordinateur distant, lisez [about_Remote](./About/about_Remote.md).

À compter de PowerShell 6,0, vous pouvez utiliser Secure Shell (SSH) pour établir une connexion à et appeler des commandes sur des ordinateurs distants. SSH doit être installé sur l’ordinateur local et l’ordinateur distant doit être configuré avec un point de terminaison SSH PowerShell. L’avantage d’une session à distance PowerShell basée sur SSH est qu’elle fonctionne sur plusieurs plateformes (Windows, Linux, macOS). Pour une session SSH, utilisez les paramètres **hostname** ou **SSHConnection** pour spécifier l’ordinateur distant et les informations de connexion appropriées. Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Certains exemples de code utilisent la projection pour réduire la longueur de la ligne. Pour plus d’informations, consultez [about_Splatting](./About/about_Splatting.md).

## EXEMPLES

### Exemple 1 : exécuter un script sur un serveur

Cet exemple exécute le `Test.ps1` script sur l’ordinateur SERVEUR01.

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

Le paramètre **filePath** spécifie un script qui se trouve sur l’ordinateur local. Le script s'exécute sur l'ordinateur distant et les résultats sont retournés à l'ordinateur local.

### Exemple 2 : exécuter une commande sur un serveur distant

Cet exemple exécute une `Get-Culture` commande sur l’ordinateur distant SERVEUR01.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

Le paramètre **ComputerName** spécifie le nom de l’ordinateur distant. Le paramètre **Credential** est utilisé pour exécuter la commande dans le contexte de sécurité de Domaine01\Utilisateur01, un utilisateur qui a l’autorisation d’exécuter des commandes. Le paramètre **scriptblock** spécifie la commande à exécuter sur l’ordinateur distant.

En réponse, PowerShell demande le mot de passe et une méthode d’authentification pour le compte User01.
Ensuite, il exécute la commande sur l'ordinateur Server01 et retourne le résultat.

### Exemple 3 : exécuter une commande dans une connexion permanente

Cet exemple exécute la même `Get-Culture` commande dans une session, à l’aide d’une connexion persistante, sur l’ordinateur distant nommé Server02.

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

L' `New-PSSession` applet de commande crée une session sur l’ordinateur distant SERVER02 et l’enregistre dans la `$s` variable. En règle générale, vous créez une session uniquement lorsque vous exécutez une série de commandes sur l’ordinateur distant.

L' `Invoke-Command` applet `Get-Culture` de commande exécute la commande sur Server02. Le paramètre **session** spécifie la session enregistrée dans la `$s` variable.

En réponse, PowerShell exécute la commande dans la session sur l’ordinateur Server02.

### Exemple 4 : utiliser une session pour exécuter une série de commandes qui partagent des données

Cet exemple compare les effets de l’utilisation de **ComputerName** et des paramètres de **session** de `Invoke-Command` . Il montre comment utiliser une session pour exécuter une série de commandes qui partagent les mêmes données.

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

Les deux premières commandes utilisent le paramètre **ComputerName** de `Invoke-Command` pour exécuter des commandes sur l’ordinateur distant SERVER02. La première commande utilise l' `Get-Process` applet de commande pour récupérer le processus PowerShell sur l’ordinateur distant et l’enregistrer dans la `$p` variable. La deuxième commande obtient la valeur de la propriété **VirtualMemorySize** du processus PowerShell.

Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une nouvelle session pour exécuter la commande.
La session est fermée à la fin de l’exécution de la commande. La `$p` variable a été créée dans une connexion, mais elle n’existe pas dans la connexion créée pour la deuxième commande.

Le problème est résolu en créant une session persistante sur l’ordinateur distant, puis en exécutant les deux commandes de la même session.

L' `New-PSSession` applet de commande crée une session persistante sur l’ordinateur Server02 et enregistre la session dans la `$s` variable. Les `Invoke-Command` lignes qui suivent utilisent le paramètre **session** pour exécuter les deux commandes de la même session. Étant donné que les deux commandes s’exécutent dans la même session, la `$p` valeur reste active.

### Exemple 5 : entrer une commande stockée dans une variable locale

Cet exemple montre comment créer une commande stockée en tant que bloc de script dans une variable locale.
Lorsque le bloc de script est enregistré dans une variable locale, vous pouvez spécifier la variable comme valeur du paramètre **scriptblock** .

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

La `$command` variable stocke la `Get-WinEvent` commande mise en forme comme un bloc de script. Le `Invoke-Command` exécute la commande stockée dans `$command` sur les ordinateurs distants S1 et S2.

### Exemple 6 : exécuter une seule commande sur plusieurs ordinateurs

Cet exemple montre comment utiliser `Invoke-Command` pour exécuter une seule commande sur plusieurs ordinateurs.

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

Le paramètre **ComputerName** spécifie une liste de noms d’ordinateurs séparés par des virgules. La liste des ordinateurs comprend la valeur localhost, qui représente l’ordinateur local. Le paramètre **ConfigurationName** spécifie une autre configuration de session. Le paramètre **scriptblock** s’exécute `Get-WinEvent` pour récupérer les journaux des événements PowerShellCore/Operations de chaque ordinateur.

### Exemple 7 : récupération de la version du programme hôte sur plusieurs ordinateurs

Cet exemple obtient la version du programme hôte PowerShell en cours d’exécution sur les ordinateurs distants 200.

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

Comme une seule commande est exécutée, vous n’êtes pas obligé de créer des connexions persistantes à chacun des ordinateurs. À la place, la commande utilise le paramètre **ComputerName** pour indiquer les ordinateurs. Pour spécifier les ordinateurs, il utilise l' `Get-Content` applet de commande pour obtenir le contenu du fichier Machine.txt, un fichier de noms d’ordinateur.

L' `Invoke-Command` applet de commande exécute une `Get-Host` commande sur les ordinateurs distants. Elle utilise la notation par points pour récupérer la propriété de **version** de l’hôte PowerShell.

Ces commandes s’exécutent l’une après l’autre. Lorsque les commandes sont terminées, la sortie des commandes de tous les ordinateurs est enregistrée dans la `$version` variable. La sortie inclut le nom de l'ordinateur d'où proviennent les données.

### Exemple 8 : exécuter une tâche en arrière-plan sur plusieurs ordinateurs distants

Cet exemple exécute une commande sur deux ordinateurs distants. La `Invoke-Command` commande utilise le paramètre **AsJob** afin que la commande s’exécute en tant que tâche en arrière-plan. Les commandes s’exécutent sur les ordinateurs distants, mais la tâche existe sur l’ordinateur local. Les résultats sont transmis à l’ordinateur local.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

L' `New-PSSession` applet de commande crée des sessions sur les ordinateurs distants SERVEUR01 et Server02. L' `Invoke-Command` applet de commande exécute une tâche en arrière-plan dans chacune des sessions. La commande utilise le paramètre **AsJob** pour exécuter la commande en tant que tâche en arrière-plan. Cette commande retourne un objet de tâche qui contient deux objets de tâche enfants, un pour chacune des tâches exécutées sur les deux ordinateurs distants.

La `Get-Job` commande enregistre l’objet de traitement dans la `$j` variable. La `$j` variable est ensuite redirigée vers l' `Format-List` applet de commande pour afficher toutes les propriétés de l’objet de traitement dans une liste. La dernière commande obtient les résultats des tâches. Elle dirige l’objet de traitement dans `$j` vers l’applet de commande `Receive-Job` et stocke les résultats dans la `$results` variable.

### Exemple 9 : inclure des variables locales dans une commande exécutée sur un ordinateur distant

Cet exemple montre comment inclure les valeurs des variables locales dans une commande exécutée sur un ordinateur distant. La commande utilise le `Using` modificateur de portée pour identifier une variable locale dans une commande à distance. Par défaut, toutes les variables sont supposées être définies dans la session à distance. Le `Using` modificateur de portée a été introduit dans PowerShell 3,0. Pour plus d’informations sur le `Using` modificateur d’étendue, consultez [about_Remote_Variables](./About/about_Remote_Variables.md) et [about_Scopes](./about/about_scopes.md).

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

La `$Log` variable stocke le nom du journal des événements, PowerShellCore/Operational. L' `Invoke-Command` applet de commande s’exécute `Get-WinEvent` sur SERVEUR01 pour recevoir les dix événements les plus récents du journal des événements. La valeur du paramètre **logname** est la `$Log` variable qui est préfixée par le `Using` modificateur de portée pour indiquer qu’elle a été créée dans la session locale, et non dans la session à distance.

### Exemple 10 : masquer le nom de l’ordinateur

Cet exemple montre l’effet de l’utilisation du paramètre **HideComputerName** de `Invoke-Command` .
**HideComputerName** ne modifie pas l’objet retourné par cette applet de commande. Il modifie uniquement l’affichage. Vous pouvez toujours utiliser les applets de commande **format** pour afficher la propriété **PSComputerName** de l’un des objets affectés.

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

Les deux premières commandes utilisent `Invoke-Command` pour exécuter une `Get-Process` commande pour le processus PowerShell. La sortie de la première commande inclut la propriété **PsComputerName**, qui contient le nom de l'ordinateur sur lequel la commande a été exécutée. La sortie de la deuxième commande, qui utilise **HideComputerName**, n’inclut pas la colonne **PSComputerName** .

### Exemple 11 : utiliser le mot clé param dans un bloc de script

Le `Param` mot clé et le paramètre **argumentlist** sont utilisés pour passer des valeurs de variable à des paramètres nommés dans un bloc de script. Cet exemple affiche les noms de fichiers qui commencent par la lettre `a` et ont l' `.pdf` extension.

Pour plus d’informations sur le `Param` mot clé, consultez [about_Language_Keywords](./about/about_language_keywords.md#param).

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

`Invoke-Command` utilise le paramètre **scriptblock** qui définit deux variables, `$param1` et `$param2` . `Get-ChildItem` utilise les paramètres nommés, **Name** et **include** avec les noms de variables. Le **argumentlist** transmet les valeurs aux variables.

### Exemple 12 : utiliser la variable automatique $args dans un bloc de script

La `$args` variable automatique et le paramètre **argumentlist** sont utilisés pour passer des valeurs de tableau aux positions de paramètre dans un bloc de script. Cet exemple affiche le contenu du répertoire d’un serveur de `.txt` fichiers. Le `Get-ChildItem` paramètre **path** a la position 0 et le paramètre **Filter** est position
1.

Pour plus d’informations sur la `$args` variable, consultez [about_Automatic_Variables](./about/about_automatic_variables.md#args)

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

`Invoke-Command` utilise un paramètre **scriptblock** et `Get-ChildItem` spécifie `$args[0]` les `$args[1]` valeurs de tableau et. Le **argumentlist** passe les `$args` valeurs de tableau aux `Get-ChildItem` positions de paramètre pour le **chemin d’accès** et le **filtre**.

### Exemple 13 : exécuter un script sur tous les ordinateurs listés dans un fichier texte

Cet exemple utilise l' `Invoke-Command` applet de commande pour exécuter le `Sample.ps1` script sur tous les ordinateurs figurant dans le `Servers.txt` fichier. La commande utilise le paramètre **FilePath** pour spécifier le fichier de script. Cette commande vous permet d’exécuter le script sur les ordinateurs distants, même si le fichier de script n’est pas accessible aux ordinateurs distants.

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

Lorsque vous envoyez la commande, le contenu du `Sample.ps1` fichier est copié dans un bloc de script et le bloc de script est exécuté sur chacun des ordinateurs distants. Cette procédure est équivalente à l'utilisation du paramètre **ScriptBlock** pour envoyer le contenu du script.

### Exemple 14 : exécuter une commande sur un ordinateur distant à l’aide d’un URI

Cet exemple montre comment exécuter une commande sur un ordinateur distant identifié par un Uniform Resource Identifier (URI). Cet exemple particulier exécute une `Set-Mailbox` commande sur un serveur Exchange distant.

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

La première ligne utilise l' `Get-Credential` applet de commande pour stocker les informations d’identification Windows Live ID dans la `$LiveCred` variable. PowerShell invite l’utilisateur à entrer des informations d’identification Windows Live ID.

La `$parameters` variable est une table de hachage contenant les paramètres à passer à l' `Invoke-Command` applet de commande. L' `Invoke-Command` applet de commande exécute une `Set-Mailbox` commande à l’aide de la configuration de session **Microsoft. Exchange** . Le paramètre **ConnectionURI** spécifie l'URL du point de terminaison de serveur Exchange. Le paramètre **Credential** spécifie les informations d’identification stockées dans la `$LiveCred` variable. Le paramètre **AuthenticationMechanism** spécifie l'utilisation de l'authentification de base. Le paramètre **ScriptBlock** spécifie un bloc de script qui contient la commande.

### Exemple 15 : utiliser une option de session

Cet exemple montre comment créer et utiliser un paramètre **SessionOption** .

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

L' `New-PSSessionOption` applet de commande crée un objet d’option de session qui oblige l’extrémité distante à ne pas vérifier l’autorité de certification, le nom canonique et les listes de révocation lors de l’évaluation de la connexion HTTPS entrante. L’objet **SessionOption** est enregistré dans la `$so` variable.

> [!NOTE]
> La désactivation de ces contrôles est pratique pour la résolution des problèmes, mais évidemment non sécurisée.

L' `Invoke-Command` applet de commande exécute une `Get-HotFix` commande à distance. La variable est attribuée au paramètre **SessionOption** `$so` .

### Exemple 16 : gérer la redirection d’URI dans une commande distante

Cet exemple montre comment utiliser les paramètres **AllowRedirection** et **SessionOption** pour gérer la redirection d’URI dans une commande distante.

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

L' `New-PSSessionOption` applet de commande crée un objet **PSSessionOption** qui est enregistré dans la `$max` variable. La commande utilise le paramètre **MaximumRedirection** pour définir la propriété **MaximumConnectionRedirectionCount** de l'objet **PSSessionOption** sur 1.

L' `Invoke-Command` applet de commande exécute une `Get-Mailbox` commande sur un serveur Microsoft Exchange distant. Le paramètre **AllowRedirection** fournit une autorisation explicite pour rediriger la connexion vers un autre point de terminaison. Le paramètre **SessionOption** utilise l’objet de session stocké dans la `$max` variable.

Par conséquent, si l’ordinateur distant spécifié par **ConnectionUri** retourne un message de redirection, PowerShell redirige la connexion, mais si la nouvelle destination retourne un autre message de redirection, la valeur du nombre de redirections de 1 est dépassée et `Invoke-Command` retourne une erreur sans fin d’achèvement.

### Exemple 17 : accéder à un partage réseau dans une session à distance

Cet exemple montre comment accéder à un partage réseau à partir d’une session à distance. Trois ordinateurs sont utilisés pour illustrer l’exemple. SERVEUR01 est l’ordinateur local, Server02 est l’ordinateur distant et Net03 contient le partage réseau. SERVEUR01 se connecte à Server02, puis Server02 effectue un deuxième tronçon vers Net03 pour accéder au partage réseau. Pour plus d’informations sur la façon dont la communication à distance PowerShell prend en charge les tronçons entre ordinateurs, consultez [création du deuxième tronçon dans la communication à distance PowerShell](/powershell/scripting/learn/remoting/ps-remoting-second-hop).

La délégation CredSSP (Credential Security Support Provider) requise est activée dans les paramètres du client sur l’ordinateur local et dans les paramètres de service sur l’ordinateur distant. Pour exécuter les commandes dans cet exemple, vous devez être membre du groupe **administrateurs** sur l’ordinateur local et l’ordinateur distant.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

L' `Enable-WSManCredSSP` applet de commande active la délégation CredSSP à partir de l’ordinateur local SERVEUR01 sur l’ordinateur distant SERVER02. Le paramètre **role** spécifie au **client** de configurer le paramètre client CredSSP sur l’ordinateur local.

`New-PSSession` crée un objet **PSSession** pour Server02 et stocke l’objet dans la `$s` variable.

L' `Invoke-Command` applet `$s` de commande utilise la variable pour se connecter à l’ordinateur distant, Server02. Le paramètre **scriptblock** s’exécute `Enable-WSManCredSSP` sur l’ordinateur distant. Le paramètre **role** spécifie le **serveur** pour configurer le paramètre de serveur CredSSP sur l’ordinateur distant.

La `$parameters` variable contient les valeurs des paramètres pour se connecter au partage réseau. L' `Invoke-Command` applet de commande exécute une `Get-Item` commande dans la session dans `$s` . Cette commande obtient un script à partir du `\\Net03\Scripts` partage réseau. La commande utilise le paramètre **Authentication** avec la valeur **CredSSP** et le paramètre **Credential** avec la valeur **domain01\admin01**.

### Exemple 18 : démarrer des scripts sur de nombreux ordinateurs distants

Cet exemple exécute un script sur plus de cent ordinateurs. Pour réduire au minimum l'impact sur l'ordinateur local, elle se connecte à chaque ordinateur, lance le script, puis se déconnecte de chaque ordinateur.
Le script continue de s'exécuter dans les sessions déconnectées.

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

La commande utilise `Invoke-Command` pour exécuter le script. La valeur du paramètre **ComputerName** est une `Get-Content` commande qui obtient les noms des ordinateurs distants à partir d’un fichier texte. Le paramètre **InDisconnectedSession** déconnecte les sessions dès qu'il démarre la commande. La valeur du paramètre **filePath** est le script qui `Invoke-Command` s’exécute sur chaque ordinateur.

La valeur de **SessionOption** est une table de hachage. La valeur **OutputBufferingMode** est définie sur **Drop** et la valeur **IdleTimeout** est définie sur **43,2 millions** millisecondes (12 heures).

Pour obtenir les résultats des commandes et des scripts qui s’exécutent dans les sessions déconnectées, utilisez l’applet de commande `Receive-PSSession` .

### Exemple 19 : exécuter une commande sur un ordinateur distant à l’aide de SSH

Cet exemple montre comment exécuter une commande sur un ordinateur distant à l’aide d’Secure Shell (SSH). Si SSH est configuré sur l’ordinateur distant pour demander des mots de passe, vous obtenez une invite de mot de passe.
Dans le cas contraire, vous devrez utiliser l’authentification utilisateur basée sur les clés SSH.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### Exemple 20 : exécuter une commande sur un ordinateur distant à l’aide de SSH et spécifier une clé d’authentification utilisateur

Cet exemple montre comment exécuter une commande sur un ordinateur distant à l’aide de SSH et spécifier un fichier de clé pour l’authentification de l’utilisateur. Vous ne serez pas invité à entrer un mot de passe, sauf si l’authentification par clé échoue et que l’ordinateur distant est configuré pour autoriser l’authentification de mot de passe de base.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### Exemple 21 : exécuter un fichier de script sur plusieurs ordinateurs distants à l’aide de SSH en tant que tâche

Cet exemple montre comment exécuter un fichier de script sur plusieurs ordinateurs distants à l’aide de SSH et du jeu de paramètres **SSHConnection** . Le paramètre **SSHConnection** prend un tableau de tables de hachage qui contiennent des informations de connexion pour chaque ordinateur. Cet exemple exige que le protocole SSH soit configuré sur les ordinateurs distants cibles pour prendre en charge l’authentification des utilisateurs basée sur les clés.

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## PARAMETERS

### -AllowRedirection

Autorise la redirection de cette connexion vers un autre URI (Uniform Resource Identifier).

Quand vous utilisez le paramètre **ConnectionURI**, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.

Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**. Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence. La valeur par défaut est 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Spécifie le segment de nom d'application de l'URI de connexion. Utilisez ce paramètre pour spécifier le nom de l’application lorsque vous n’utilisez pas le paramètre **ConnectionUri** dans la commande.

La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local. Si cette variable de préférence n’est pas définie, la valeur par défaut est WSMAN. Cette valeur convient pour la plupart des utilisations. Pour plus d’informations, consultez [about_Preference_Variables](./About/about_Preference_Variables.md).

Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.
La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

Fournit les valeurs des variables locales dans la commande. Les variables dans la commande sont remplacées par ces valeurs avant l'exécution de la commande sur l'ordinateur distant. Entrez les valeurs dans une liste séparée par des virgules. Les valeurs sont associées à des variables dans l’ordre dans lequel elles sont répertoriées. L’alias pour **argumentlist** est args.

Les valeurs du paramètre **argumentlist** peuvent être des valeurs réelles, telles que 1024, ou elles peuvent être des références à des variables locales, telles que `$max` .

Pour utiliser des variables locales dans une commande, utilisez le format de commande suivant :

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` ou `<local-variable>`

Le mot clé **param** répertorie les variables locales utilisées dans la commande. **Argumentlist** fournit les valeurs des variables, dans l’ordre dans lequel elles sont listées. Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan sur un ordinateur distant. Utilisez ce paramètre pour exécuter des commandes qui prennent beaucoup de temps pour se terminer.

Quand vous utilisez le paramètre **AsJob** , la commande retourne un objet qui représente le travail, puis affiche l’invite de commandes. Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche. Pour gérer le travail, utilisez les `*-Job` applets de commande. Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.

Le paramètre **AsJob** ressemble à l’utilisation de l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` applet de commande à distance. Toutefois, avec **AsJob**, la tâche est créée sur l’ordinateur local, même si le travail s’exécute sur un ordinateur distant. Les résultats de la tâche à distance sont automatiquement retournés à l’ordinateur local.

Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](About/about_Jobs.md) et [about_Remote_Jobs](About/about_Remote_Jobs.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur. L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- Default
- Basic
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau. Pour plus d’informations, consultez [informations d’identification Support Provider](/windows/win32/secauthn/credential-security-support-provider).

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux et ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez une `Get-Item` `Get-ChildItem` commande ou dans le lecteur de certificat PowerShell :.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie les ordinateurs sur lesquels la commande s'exécute. La valeur par défaut est l'ordinateur local.

Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une connexion temporaire qui est utilisée uniquement pour exécuter la commande spécifiée, puis elle est fermée. Si vous avez besoin d’une connexion permanente, utilisez le paramètre **session** .

Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point ( `.` ).

Pour utiliser une adresse IP dans la valeur **ComputerName**, la commande doit inclure le paramètre **Credential** . L’ordinateur doit être configuré pour le transport HTTPs ou l’adresse IP de l’ordinateur distant doit être incluse dans la liste **TrustedHosts** de l’ordinateur local. Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste **TrustedHosts** , consultez [comment ajouter un ordinateur à la liste des hôtes approuvés](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).

Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, pour inclure l’ordinateur local dans la valeur **ComputerName**, vous devez exécuter PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

Spécifie la configuration de session utilisée pour la nouvelle session **PSSession**.

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session. Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/PowerShell` .

Lorsqu’il est utilisé avec SSH, ce paramètre spécifie le sous-système à utiliser sur la cible, comme défini dans `sshd_config` . La valeur par défaut pour SSH est le `powershell` sous-système.

La configuration d'une session se trouve sur l'ordinateur distant. Si la configuration de session spécifiée n’existe pas sur l’ordinateur distant, la commande échoue.

La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local. Si cette variable de préférence n’est pas définie, la valeur par défaut est **Microsoft. PowerShell**. Pour plus d’informations, consultez [about_Preference_Variables](about/about_Preference_Variables.md).

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Spécifie un URI (Uniform Resource Identifier) qui définit le point de terminaison de connexion de la session.
L’URI doit être complet.

Le format de cette chaîne est le suivant :

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

La valeur par défaut est la suivante :

`http://localhost:5985/WSMAN`

Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres **UseSSL** et **port** pour spécifier les valeurs d’URI de connexion.

Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContainerId

Spécifie un tableau d’ID de conteneur.

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage. Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs. Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.

Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur. Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou affectez-lui la valeur dot ( `.` ), localhost ou le nom de l’ordinateur local.

Par défaut, les sessions de bouclage sont créées à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.

Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage. Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.

Vous pouvez autoriser l’accès à distance dans une session de bouclage à l’aide de la valeur **CredSSP** du paramètre **Authentication** , qui délègue les informations d’identification de session à d’autres ordinateurs.

Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, qui sont créés à l’aide de **EnableNetworkAccess**, peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée. Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs. Pour plus d’informations, consultez `Disconnect-PSSession`.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un script local que cette applet de commande exécute sur un ou plusieurs ordinateurs distants. Entrez le chemin d’accès et le nom de fichier du script, ou dirigez un chemin d’accès de script vers `Invoke-Command` . Le script doit exister sur l’ordinateur local ou dans un répertoire auquel l’ordinateur local peut accéder. Utilisez **argumentlist** pour spécifier les valeurs des paramètres dans le script.

Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script, transmet le bloc de script à l’ordinateur distant et l’exécute sur l’ordinateur distant.

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideComputerName

Indique que cette applet de commande omet le nom d’ordinateur de chaque objet dans l’affichage de sortie. Par défaut, le nom de l'ordinateur qui a généré l'objet apparaît dans l'affichage.

Ce paramètre affecte uniquement l'affichage de la sortie. Elle ne modifie pas l’objet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Spécifie un tableau de noms d’ordinateurs pour une connexion Secure Shell (SSH). Cela est similaire au paramètre **ComputerName** , à ceci près que la connexion à l’ordinateur distant s’effectue à l’aide de SSH plutôt que de Windows WinRM.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InDisconnectedSession

Indique que cette applet de commande exécute une commande ou un script dans une session déconnectée.

Quand vous utilisez le paramètre **InDisconnectedSession** , `Invoke-Command` crée une session persistante sur chaque ordinateur distant, démarre la commande spécifiée par le paramètre **scriptblock** ou **filePath** , puis se déconnecte de la session. Les commandes continuent à s’exécuter dans les sessions déconnectées. **InDisconnectedSession** vous permet d’exécuter des commandes sans maintenir une connexion aux sessions à distance. Et, étant donné que la session est déconnectée avant le renvoi des résultats, **InDisconnectedSession** garantit que tous les résultats de la commande sont retournés à la session reconnectée, au lieu d’être fractionnés entre les sessions.

Vous ne pouvez pas utiliser **InDisconnectedSession** avec le paramètre de **session** ou le paramètre **AsJob** .

Les commandes qui utilisent **InDisconnectedSession** retournent un objet **PSSession** qui représente la session déconnectée. Ils ne retournent pas la sortie de commande. Pour vous connecter à la session déconnectée, utilisez les `Connect-PSSession` applets de commande ou `Receive-PSSession` . Pour obtenir les résultats des commandes exécutées dans la session, utilisez l' `Receive-PSSession` applet de commande. Pour exécuter des commandes qui génèrent une sortie dans une session déconnectée, définissez la valeur de l’option de session **OutputBufferingMode** sur **Drop**. Si vous envisagez de vous connecter à la session déconnectée, définissez le délai d’inactivité dans la session afin qu’elle fournisse suffisamment de temps pour vous connecter avant de supprimer la session.

Vous pouvez définir le mode de mise en mémoire tampon de sortie et le délai d’inactivité dans le paramètre **SessionOption** ou dans la `$PSSessionOption` variable de préférence. Pour plus d’informations sur les options de session, consultez `New-PSSessionOption` et [about_Preference_Variables](./about/about_preference_variables.md).

Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l'entrée de la commande. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.

Quand vous utilisez le paramètre **InputObject** , utilisez la `$Input` variable Automatic dans la valeur du paramètre **scriptblock** pour représenter les objets d’entrée.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JobName

Spécifie un nom convivial pour la tâche en arrière-plan. Par défaut, les tâches sont nommées `Job<n>` , où `<n>` est un nombre ordinal.

Si vous utilisez le paramètre **JobName** dans une commande, la commande est exécutée en tant que tâche et `Invoke-Command` retourne un objet de traitement, même si vous n’incluez pas **AsJob** dans la commande.

Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](./About/about_Jobs.md).

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### -KeyFilePath

Spécifie un chemin de fichier de clé utilisé par Secure Shell (SSH) pour authentifier un utilisateur sur un ordinateur distant.

SSH permet d’effectuer l’authentification des utilisateurs via des clés privées et publiques comme alternative à l’authentification de base par mot de passe. Si l’ordinateur distant est configuré pour l’authentification de clé, ce paramètre peut être utilisé pour fournir la clé qui identifie l’utilisateur.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewScope

Indique que cette applet de commande exécute la commande spécifiée dans l’étendue actuelle. Par défaut, `Invoke-Command` exécute des commandes dans leur propre étendue.

Ce paramètre est valide uniquement dans les commandes qui sont exécutées dans la session active, autrement dit, dans les commandes qui omettent les deux paramètres **ComputerName** et **Session**.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau sur l’ordinateur distant utilisé pour cette commande. Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPs).

Avant d'utiliser un autre port, configurez l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port. Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

N’utilisez pas le paramètre **port** , sauf si vous devez le faire. Le port défini dans la commande s'applique à tous les ordinateurs ou toutes les sessions sur lesquelles la commande s'exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteDebug

Utilisé pour exécuter la commande appelée en mode débogage dans la session PowerShell distante.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Indique que cette applet de commande appelle une commande en tant qu’administrateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

Spécifie les commandes à exécuter. Placez les commandes entre accolades `{ }` pour créer un bloc de script.
Ce paramètre est obligatoire.

Par défaut, les variables de la commande sont évaluées sur l'ordinateur distant. Pour inclure des variables locales dans la commande, utilisez **argumentlist**.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

Spécifie un tableau de sessions dans lequel cette applet de commande exécute la commande. Entrez une variable qui contient des objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu' `New-PSSession` une `Get-PSSession` commande ou.

Lorsque vous créez une **session PSSession**, PowerShell établit une connexion permanente à l’ordinateur distant. Utilisez une **session PSSession** pour exécuter une série de commandes associées qui partagent des données. Pour exécuter une seule commande ou une série de commandes sans rapport, utilisez le paramètre **ComputerName** . Pour plus d’informations, consultez [about_PSSessions](./About/about_PSSessions.md).

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nom_session

Spécifie un nom convivial pour une session déconnectée. Vous pouvez utiliser le nom pour faire référence à la session dans les commandes suivantes, par exemple une `Get-PSSession` commande. Ce paramètre est valide uniquement avec le paramètre **InDisconnectedSession**.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Spécifie les options avancées pour la session. Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.

Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session. Toutefois, elles ne sont pas prioritaires sur les valeurs maximales, les quotas ou les limites définies dans la configuration de session.

Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` . Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).
Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

Ce paramètre prend un tableau de tables de hachage dans lequel chaque table de hachage contient un ou plusieurs paramètres de connexion nécessaires pour établir une connexion Secure Shell (SSH). Le paramètre **SSHConnection** est utile pour créer plusieurs sessions où chaque session requiert des informations de connexion différentes.

La Hashtable contient les membres suivants :

- **ComputerName** (ou **hostname**)
- **Port**
- **UserName**
- **KeyFilePath** (ou **IdentityFilePath**)

**ComputerName** (ou **hostname**) est la seule paire clé-valeur requise.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

Indique que la connexion à distance est établie à l’aide d’Secure Shell (SSH).

Par défaut, PowerShell utilise Windows WinRM pour se connecter à un ordinateur distant. Ce commutateur force PowerShell à utiliser le paramètre **hostname** pour établir une connexion à distance basée sur SSH.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

Spécifie le nom d’utilisateur du compte utilisé pour exécuter une commande sur l’ordinateur distant. La méthode d’authentification de l’utilisateur dépend de la configuration de Secure Shell (SSH) sur l’ordinateur distant.

Si SSH est configuré pour l’authentification de mot de passe de base, vous êtes invité à entrer le mot de passe de l’utilisateur.

Si SSH est configuré pour l’authentification utilisateur basée sur les clés, un chemin d’accès de fichier de clé peut être fourni via le paramètre **keyFilePath** et aucune invite de mot de passe n’est générée. Si le fichier de clé de l’utilisateur client se trouve dans un emplacement connu SSH, le paramètre **keyFilePath** n’est pas nécessaire pour l’authentification basée sur les clés et l’authentification de l’utilisateur se produit automatiquement en fonction du nom d’utilisateur. Pour plus d’informations, consultez la documentation SSH de votre plateforme relative à l’authentification des utilisateurs basée sur les clés.

Ce paramètre n’est pas obligatoire. Si le paramètre **username** n’est pas spécifié, le nom d’utilisateur actuellement connecté est utilisé pour la connexion.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Indique que cette applet de commande utilise le protocole SSL (Secure Sockets Layer) (SSL) pour établir une connexion à l’ordinateur distant. Par défaut, SSL n’est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau. Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via HTTPS au lieu de http.

Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Spécifie un tableau d’ID de machines virtuelles.

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Spécifie un tableau de noms d'ordinateurs virtuels.

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Sous-système

Spécifie le sous-système SSH utilisé pour la nouvelle **session PSSession**.

Cela spécifie le sous-système à utiliser sur la cible, tel que défini dans sshd_config.
Le sous-système démarre une version spécifique de PowerShell avec des paramètres prédéfinis.
Si le sous-système spécifié n’existe pas sur l’ordinateur distant, la commande échoue.

Si ce paramètre n’est pas utilisé, la valeur par défaut est le sous-système « PowerShell ».

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. ScriptBlock

Vous pouvez diriger une commande dans un bloc de script vers `Invoke-Command` . Utilisez la `$Input` variable Automatic pour représenter les objets d’entrée de la commande.

## SORTIES

### System. Management. Automation. PSRemotingJob, System. Management. Automation. instances d’exécution. PSSession ou la sortie de la commande appelée

Cette applet de commande retourne un objet de traitement, si vous utilisez le paramètre **AsJob** . Si vous spécifiez le paramètre **InDisconnectedSession** , `Invoke-Command` retourne un objet **PSSession** . Dans le cas contraire, elle retourne la sortie de la commande appelée, qui est la valeur du paramètre **scriptblock** .

## REMARQUES

Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, pour utiliser le paramètre **ComputerName** de `Invoke-Command` pour exécuter une commande sur l’ordinateur local, vous devez exécuter PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

Lorsque vous exécutez des commandes sur plusieurs ordinateurs, PowerShell se connecte aux ordinateurs dans l’ordre dans lequel ils apparaissent dans la liste. Toutefois, la sortie de la commande s’affiche dans l’ordre dans lequel elle est reçue des ordinateurs distants, ce qui peut être différent.

Les erreurs qui résultent de la commande qui `Invoke-Command` s’exécute sont incluses dans les résultats de la commande.
Les erreurs qui seraient des erreurs avec fin d'exécution dans une commande locale sont traitées comme des erreurs sans fin d'exécution dans une commande à distance. Cette stratégie permet de s’assurer que les erreurs d’arrêt sur un ordinateur ne ferment pas la commande sur tous les ordinateurs sur lesquels elle est exécutée. Cette pratique est utilisée même quand une commande à distance est exécutée sur un seul ordinateur.

Si l’ordinateur distant n’est pas dans un domaine approuvé par l’ordinateur local, il se peut que l’ordinateur ne soit pas en mesure d’authentifier les informations d’identification de l’utilisateur. Pour ajouter l’ordinateur distant à la liste des hôtes approuvés dans WS-Management, utilisez la commande suivante dans le `WSMAN` fournisseur, où `<Remote-Computer-Name>` est le nom de l’ordinateur distant :

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

Lorsque vous déconnectez une session **PSSession** à l’aide du paramètre **InDisconnectedSession** , l’état de session est **Disconnected** et la disponibilité est **None**. La valeur de la propriété **State** dépend de la session active. La valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active. Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions. Elle peut être connectée à une autre session. Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.

Une propriété **Availability** avec la valeur **None** signifie que vous pouvez vous connecter à la session. La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session. Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate). Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

Les paramètres **hostname** et **SSHConnection** ont été inclus à partir de PowerShell 6,0. Elles ont été ajoutées pour fournir une communication à distance PowerShell basée sur Secure Shell (SSH). PowerShell et SSH sont pris en charge sur plusieurs plateformes (Windows, Linux, macOS) et la communication à distance PowerShell fonctionne sur ces plateformes où PowerShell et SSH sont installés et configurés. Cela est différent de la version précédente de Windows uniquement qui est basée sur WinRM et la plupart des fonctionnalités et limitations spécifiques à WinRM ne s’appliquent pas. Par exemple, les quotas basés sur WinRM, les options de session, la configuration de point de terminaison personnalisée et les fonctionnalités de déconnexion/reconnexion ne sont actuellement pas pris en charge. Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## LIENS CONNEXES

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Item](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

