---
ms.date: 08/21/2020
keywords: powershell,applet de commande
title: Exécution de commandes à distance
description: Explique les méthodes permettant d’exécuter des commandes sur des systèmes distants à l’aide de PowerShell.
ms.openlocfilehash: cff18a4f51c3ed8e3ed2c1f35862a88911e7ceb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391406"
---
# <a name="running-remote-commands"></a>Exécution de commandes à distance

Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande PowerShell. Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.

PowerShell Core prend en charge WMI, WS-Management et la communication à distance SSH. Dans PowerShell 6, RPC n’est plus pris en charge. Dans PowerShell 7 et versions ultérieures, RPC est pris en charge uniquement dans Windows.

Pour plus d’informations sur la communication à distance dans PowerShell Core, consultez les articles suivants :

- [Communication à distance SSH dans PowerShell Core][ssh-remoting]
- [Communication à distance WSMan dans PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Communication à distance Windows PowerShell sans configuration

De nombreuses applets de commande Windows PowerShell possèdent le paramètre ComputerName, qui vous permet de collecter des données et de modifier les paramètres sur un ou plusieurs ordinateurs distants. Ces cmdlets utilisent différents protocoles de communication et fonctionnent sur tous les systèmes d’exploitation Windows sans configuration spéciale.

Ces applets de commande sont les suivantes :

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

En général, les cmdlets qui prennent en charge la communication à distance sans configuration particulière possèdent le paramètre ComputerName. En revanche, elles ne possèdent pas le paramètre Session. Pour trouver ces applets de commande dans votre session, tapez :

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Communication à distance Windows PowerShell

La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, vous permet d'exécuter n'importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants. Vous pouvez établir des connexions persistantes, démarrer des sessions interactives et exécuter des scripts sur ordinateurs distants.

Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.
Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance.
Cet article en répertorie quelques-unes. Pour plus d’informations, consultez [À propos de la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Démarrer une session interactive

Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l'applet de commande [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession). Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :

```powershell
Enter-PSSession Server01
```

L'invite de commandes affiche alors le nom de l'ordinateur distant. Toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.

Pour terminer la session interactive, tapez :

```powershell
Exit-PSSession
```

Pour plus d’informations sur les cmdlets Enter-PSSession et Exit-PSSession, consultez :

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Exécuter une commande à distance

Pour exécuter une commande sur un ou plusieurs ordinateurs, utilisez la cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command). Par exemple, pour exécuter une commande [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) sur les ordinateurs distants Server01 et Server02, tapez :

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

La sortie est retournée à votre ordinateur.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Exécuter un script

Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de la cmdlet `Invoke-Command`. Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci. Les résultats sont retournés à votre ordinateur local.

Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Établir une connexion persistante

Utilisez la cmdlet `New-PSSession` pour créer une session persistante sur un ordinateur distant. L’exemple suivant crée des sessions distantes sur Server01 et Server02. Les objets de session sont stockés dans la variable `$s`.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci. Les sessions étant persistantes, vous pouvez collecter des données à partir d’une seule commande et les utiliser dans une autre commande.

Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h. La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Vous pouvez désormais utiliser les données dans la variable `$h` avec d’autres commandes dans la même session. Les résultats sont affichés sur l'ordinateur local. Exemple :

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Communication à distance avancée

Dans Windows PowerShell, la gestion à distance n'est qu'un début. Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.

Windows PowerShell inclut un fournisseur WSMan. Le fournisseur crée un lecteur `WSMAN:` qui vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants.

Pour plus d’informations sur le fournisseur WSMan, consultez [Fournisseur WSMan](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) et [À propos des cmdlets WS-Management](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets) ou tapez `Get-Help wsman` dans la console Windows PowerShell.

Pour plus d'informations, consultez les pages suivantes :

- [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

Pour obtenir de l'aide sur les erreurs de communication à distance, consultez [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).

## <a name="see-also"></a>Voir aussi

- [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [about_Remote_FAQ](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
- [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)
- [about_PSSessions](/powershell/module/microsoft.powershell.core/about/about_PSSessions)
- [about_WS-Management_Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [Fournisseur WSMan](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
