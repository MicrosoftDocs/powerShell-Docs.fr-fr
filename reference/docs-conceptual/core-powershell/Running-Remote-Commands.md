---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Exécution de commandes à distance
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482877"
---
# <a name="running-remote-commands"></a>Exécution de commandes à distance

Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande Windows PowerShell. Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.

## <a name="remoting-in-powershell-core"></a>Accès distant dans PowerShell Core

PowerShell Core, l’édition la plus récente de PowerShell sur Windows, macOS et Linux, prend en charge WMI, WS-Management et l’accès distant SSH.
(RPC n’est plus pris en charge.)

Pour plus d’informations sur la configuration de ceci, consultez :

* [Communication à distance SSH dans PowerShell Core][ssh-remoting]
* [Communication à distance WSMan dans PowerShell Core][wsman-remoting]

## <a name="remoting-without-configuration"></a>Communication à distance sans configuration

De nombreuses applets de commande Windows PowerShell possèdent le paramètre ComputerName, qui vous permet de collecter des données et de modifier les paramètres sur un ou plusieurs ordinateurs distants. Elles utilisent diverses technologies de communication et bon nombre d'entre elles fonctionnent sur tous les systèmes d'exploitation Windows pris en charge par Windows PowerShell, et ce sans configuration particulière.

Ces applets de commande sont les suivantes :

* [Restart-Computer](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Test-Connection](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Clear-EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-EventLog](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Set-Service](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

En général, les applets de commande qui prennent en charge la communication à distance sans configuration particulière possèdent le paramètre ComputerName. En revanche, elles ne possèdent pas le paramètre Session. Pour trouver ces applets de commande dans votre session, tapez :

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Communication à distance Windows PowerShell

La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, vous permet d'exécuter n'importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants. Vous pouvez ainsi établir des connexions persistantes, démarrer des sessions interactives 1:1 et exécuter des scripts sur plusieurs ordinateurs.

Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance. Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx).

Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance. Le reste de ce document répertorie quelques-unes d'entre elles. Pour plus d’informations, voir [À propos de la connexion à distance](https://technet.microsoft.com/library/dd347744.aspx) et [FAQ de la connexion à distance](https://technet.microsoft.com/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Démarrer une session interactive

Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l’applet de commande [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).
Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :

```powershell
Enter-PSSession Server01
```

L'invite de commandes affiche alors le nom de l'ordinateur auquel vous êtes connecté. À partir de là, toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.

Pour terminer la session interactive, tapez :

```powershell
Exit-PSSession
```

Pour plus d’informations sur les applets de commande Enter-PSSession et Exit-PSSession, voir [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) et [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Exécuter une commande à distance

Pour exécuter une commande sur un ou plusieurs ordinateurs distants, utilisez l’applet de commande [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).
Par exemple, pour exécuter une commande [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) sur les ordinateurs distants Serveur01 et Serveur02, tapez :

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

Pour plus d’informations sur l’applet de commande Invoke-Command, voir [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Exécuter un script

Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de l'applet de commande Invoke-Command. Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci. Les résultats sont retournés à votre ordinateur local.

Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Pour plus d’informations sur l’applet de commande Invoke-Command, voir [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Établir une connexion persistante

Pour exécuter une série de commandes associées qui partagent des données, créez une session sur l'ordinateur distant, puis utilisez l'applet de commande Invoke-Command pour exécuter des commandes dans la session créée. Pour créer une session à distance, utilisez l'applet de commande New-PSSession.

Par exemple, la commande suivante crée une session à distance sur l'ordinateur Server01 et une autre session à distance sur l'ordinateur Server02. Elle enregistre les objets de session dans la variable $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci. Les sessions étant persistantes, vous pouvez collecter des données en une seule commande et les utiliser dans une commande ultérieure.

Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h. La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Vous pouvez désormais utiliser les données dans la variable $h dans des commandes ultérieures, comme celle qui suit. Les résultats sont affichés sur l'ordinateur local.

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Communication à distance avancée

Dans Windows PowerShell, la gestion à distance n'est qu'un début. Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.

Pour faciliter la configuration à distance, Windows PowerShell comprend un fournisseur WSMan. Le lecteur WSMAN: créé par le fournisseur vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants.
Pour plus d’informations sur le fournisseur WSMan, voir [Fournisseur WSMan](https://technet.microsoft.com/library/dd819476.aspx) et [À propos des applets de commande WSMan](https://technet.microsoft.com/library/dd819481.aspx) ou tapez « Get-Help wsman » dans la console Windows PowerShell.

Pour plus d’informations, voir :

- [About_Remote_FAQ](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Pour obtenir de l’aide sur les erreurs de communication à distance, voir [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Voir aussi

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Fournisseur WSMan](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md