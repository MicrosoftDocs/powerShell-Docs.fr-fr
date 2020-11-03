---
description: Contient des questions et des réponses sur l’exécution des commandes distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: db3b7b554096c0cee6f13365dd8b2fbacb498282
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207734"
---
# <a name="about-remote-faq"></a>about_Remote

## <a name="short-description"></a>Description courte
Contient des questions et des réponses sur l’exécution des commandes distantes dans PowerShell.

## <a name="long-description"></a>Description longue

Lorsque vous travaillez à distance, vous tapez des commandes dans PowerShell sur un ordinateur (appelé « ordinateur local »), mais les commandes s’exécutent sur un autre ordinateur (appelé « ordinateur distant »). L’expérience de travail à distance doit être aussi proche que possible de travailler directement sur l’ordinateur distant.

Remarque : pour utiliser la communication à distance PowerShell, l’ordinateur distant doit être configuré pour la communication à distance. Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).

### <a name="must-both-computers-have-powershell-installed"></a>PowerShell doit-il être installé sur les deux ordinateurs ?

Oui. Pour travailler à distance, les ordinateurs locaux et distants doivent avoir PowerShell, l’infrastructure Microsoft .NET et le protocole WS-Management (Web Services for Management). Tous les fichiers et autres ressources nécessaires pour exécuter une commande particulière doivent se trouver sur l’ordinateur distant.

Les ordinateurs exécutant Windows PowerShell 3,0 et les ordinateurs exécutant Windows PowerShell 2,0 peuvent se connecter les uns aux autres à distance et exécuter des commandes distantes.
Toutefois, certaines fonctionnalités, telles que la possibilité de se déconnecter d’une session et de se reconnecter, fonctionnent uniquement lorsque les deux ordinateurs exécutent Windows PowerShell 3,0.

Vous devez être autorisé à vous connecter à l’ordinateur distant, à exécuter PowerShell et à accéder aux magasins de données (tels que des fichiers et des dossiers) et au registre de l’ordinateur distant.

Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).

### <a name="how-does-remoting-work"></a>Fonctionnement de la communication à distance

Lorsque vous envoyez une commande à distance, la commande est transmise via le réseau vers le moteur PowerShell sur l’ordinateur distant, et elle s’exécute dans le client PowerShell sur l’ordinateur distant. Les résultats de la commande sont renvoyés à l’ordinateur local et s’affichent dans la session PowerShell sur l’ordinateur local.

Pour transmettre les commandes et recevoir la sortie, PowerShell utilise le protocole WS-Management. Pour plus d’informations sur le protocole WS-Management, consultez [protocole WS-Management](/windows/win32/winrm/ws-management-protocol) dans la documentation de Windows.

À compter de Windows PowerShell 3,0, les sessions à distance sont stockées sur l’ordinateur distant. Cela vous permet de vous déconnecter de la session et de vous reconnecter à partir d’une autre session ou d’un autre ordinateur sans interrompre les commandes ou perdre l’État.

### <a name="is-powershell-remoting-secure"></a>La communication à distance PowerShell est-elle sécurisée ?

Lorsque vous vous connectez à un ordinateur distant, le système utilise les informations d’identification du nom d’utilisateur et du mot de passe sur l’ordinateur local ou les informations d’identification que vous fournissez dans la commande pour vous connecter à l’ordinateur distant. Les informations d’identification et le reste de la transmission sont chiffrés.

Pour ajouter une protection supplémentaire, vous pouvez configurer l’ordinateur distant pour qu’il utilise protocole SSL (SSL) au lieu de HTTP pour écouter les demandes Windows Remote Management (WinRM). Ensuite, les utilisateurs peuvent utiliser le paramètre **UseSSL** des `Invoke-Command` applets de commande, `New-PSSession` et lors de l' `Enter-PSSession` établissement d’une connexion. Cette option utilise le canal HTTPs plus sécurisé au lieu du protocole HTTP.

### <a name="do-all-remote-commands-require-powershell-remoting"></a>Toutes les commandes distantes requièrent-elle la communication à distance PowerShell ?

Non. Plusieurs applets de commande ont un paramètre **ComputerName** qui vous permet d’obtenir des objets de l’ordinateur distant.

Ces applets de commande n’utilisent pas la communication à distance PowerShell. Vous pouvez donc les utiliser sur n’importe quel ordinateur exécutant PowerShell, même si l’ordinateur n’est pas configuré pour la communication à distance PowerShell ou si l’ordinateur ne remplit pas les conditions requises pour la communication à distance PowerShell.

Ces applets de commande sont les suivantes :

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

Pour rechercher toutes les applets de commande avec un paramètre **ComputerName** , tapez :

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

Pour déterminer si le paramètre **ComputerName** d’une applet de commande particulière requiert la communication à distance PowerShell, consultez la description du paramètre. Pour afficher la description du paramètre, tapez :

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

Par exemple :

```powershell
Get-Help Get-Process -Parameter ComputerName
```

Pour toutes les autres commandes, utilisez l’applet de commande `Invoke-Command` .

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a>Comment faire exécuter une commande sur un ordinateur distant ?

Pour exécuter une commande sur un ordinateur distant, utilisez l' `Invoke-Command` applet de commande.

Placez votre commande entre accolades ( `{}` ) pour en faire un bloc de script. Utilisez le paramètre **scriptblock** de `Invoke-Command` pour spécifier la commande.

Vous pouvez utiliser le paramètre **ComputerName** de `Invoke-Command` pour spécifier un ordinateur distant. Ou bien, vous pouvez créer une connexion permanente à un ordinateur distant (une session), puis utiliser le paramètre de **session** de `Invoke-Command` pour exécuter la commande dans la session.

Par exemple, les commandes suivantes exécutent une `Get-Process` commande à distance.

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

Pour interrompre une commande distante, tapez <kbd>CTRL</kbd> + <kbd>C</kbd>. La demande d’interruption est transmise à l’ordinateur distant, où elle met fin à la commande à distance.

Pour plus d’informations sur les commandes distantes, consultez about_Remote et les rubriques d’aide pour les applets de commande qui prennent en charge la communication à distance.

### <a name="can-i-just-telnet-into-a-remote-computer"></a>Puis-je simplement faire appel à Telnet sur un ordinateur distant ?

Vous pouvez utiliser l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec un ordinateur distant.

À l’invite PowerShell, tapez :

```powershell
Enter-PSSession <ComputerName>
```

L’invite de commandes change pour indiquer que vous êtes connecté à l’ordinateur distant.

```
<ComputerName>\C:>
```

À présent, les commandes que vous tapez s’exécutent sur l’ordinateur distant comme si vous les tapiez directement sur l’ordinateur distant.

Pour terminer la session interactive, tapez :

```powershell
Exit-PSSession
```

Une session interactive est une session persistante qui utilise le protocole WS-Management. Elle n’est pas identique à l’utilisation de Telnet, mais elle offre une expérience similaire.

Pour plus d'informations, consultez `Enter-PSSession`.

### <a name="can-i-create-a-persistent-connection"></a>Puis-je créer une connexion permanente ?

Oui. Vous pouvez exécuter des commandes distantes en spécifiant le nom de l’ordinateur distant, son nom NetBIOS ou son adresse IP. Ou bien, vous pouvez exécuter des commandes distantes en spécifiant une session PowerShell (PSSession) qui est connectée à l’ordinateur distant.

Quand vous utilisez le paramètre **ComputerName** de `Invoke-Command` ou `Enter-PSSession` , PowerShell établit une connexion temporaire. PowerShell utilise la connexion pour exécuter uniquement la commande actuelle, puis ferme la connexion. Il s’agit d’une méthode très efficace pour exécuter une seule commande ou plusieurs commandes sans rapport, même sur de nombreux ordinateurs distants.

Lorsque vous utilisez l' `New-PSSession` applet de commande pour créer une session PSSession, PowerShell établit une connexion permanente pour la session PSSession. Ensuite, vous pouvez exécuter plusieurs commandes dans la session PSSession, y compris les commandes qui partagent des données.

En général, vous créez une session PSSession pour exécuter une série de commandes associées qui partagent des données. Dans le cas contraire, la connexion temporaire créée par le paramètre **ComputerName** est suffisante pour la plupart des commandes.

Pour plus d’informations sur les sessions, consultez about_PSSessions.

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a>Puis-je exécuter des commandes sur plusieurs ordinateurs à la fois ?

Oui. Le paramètre **ComputerName** de l' `Invoke-Command` applet de commande accepte plusieurs noms d’ordinateur, et le paramètre de **session** accepte plusieurs sessions PSSession.

Quand vous exécutez une `Invoke-Command` commande, PowerShell exécute les commandes sur tous les ordinateurs spécifiés ou dans tous les sessions PSSession spécifiés.

PowerShell peut gérer des centaines de connexions à distance simultanées. Toutefois, le nombre de commandes distantes que vous pouvez envoyer peut être limité par les ressources de votre ordinateur et sa capacité à établir et à gérer plusieurs connexions réseau.

Pour plus d’informations, consultez l’exemple de la `Invoke-Command` rubrique d’aide.

### <a name="where-are-my-profiles"></a>Où sont mes profils ?

Les profils PowerShell ne sont pas exécutés automatiquement dans les sessions à distance. par conséquent, les commandes ajoutées par le profil ne sont pas présentes dans la session. En outre, la `$profile` variable automatique n’est pas remplie dans les sessions à distance.

Pour exécuter un profil dans une session, utilisez l' `Invoke-Command` applet de commande.

Par exemple, la commande suivante exécute le profil CurrentUserCurrentHost à partir de l’ordinateur local dans la session dans `$s` .

```
Invoke-Command -Session $s -FilePath $profile
```

La commande suivante exécute le profil CurrentUserCurrentHost à partir de l’ordinateur distant dans la session dans `$s` . Étant donné que la `$profile` variable n’est pas remplie, la commande utilise le chemin d’accès explicite au profil.

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

Après l’exécution de cette commande, les commandes ajoutées par le profil à la session sont disponibles dans `$s` .

Vous pouvez également utiliser un script de démarrage dans une configuration de session pour exécuter un profil dans chaque session à distance qui utilise la configuration de session.

Pour plus d’informations sur les profils PowerShell, voir about_Profiles.
Pour plus d’informations sur les configurations de session, consultez `Register-PSSessionConfiguration` .

### <a name="how-does-throttling-work-on-remote-commands"></a>Comment la limitation fonctionne-t-elle sur les commandes distantes ?

Pour vous aider à gérer les ressources sur votre ordinateur local, PowerShell intègre une fonctionnalité de limitation par commande qui vous permet de limiter le nombre de connexions à distance simultanées établies pour chaque commande.

La valeur par défaut est 32 connexions simultanées, mais vous pouvez utiliser le paramètre **ThrottleLimit** des applets de commande pour définir une limite de limitation personnalisée pour des commandes particulières.

Lorsque vous utilisez la fonctionnalité de limitation, n’oubliez pas qu’elle est appliquée à chaque commande, et non à l’ensemble de la session ou à l’ordinateur. Si vous exécutez des commandes simultanément dans plusieurs sessions ou sessions PSSession, le nombre de connexions simultanées est la somme des connexions simultanées dans toutes les sessions.

Pour rechercher des applets de commande avec un paramètre **ThrottleLimit** , tapez :

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a>La sortie des commandes à distance est-elle différente de la sortie locale ?

Lorsque vous utilisez PowerShell localement, vous envoyez et recevez des objets « Live » .NET Framework. les objets « actifs » sont des objets qui sont associés à des programmes ou des composants système réels. Lorsque vous appelez les méthodes ou modifiez les propriétés d’objets actifs, les modifications affectent le programme ou le composant réel. Et, lorsque les propriétés d’un programme ou d’un composant changent, les propriétés de l’objet qui les représentent sont également modifiées.

Toutefois, étant donné que la plupart des objets en ligne ne peuvent pas être transmis sur le réseau, PowerShell « sérialise » la plupart des objets envoyés dans les commandes distantes, autrement dit, il convertit chaque objet en une série de éléments de données XML (contrainte Language dans XML [CLiXML]) pour la transmission.

Lorsque PowerShell reçoit un objet sérialisé, il convertit le XML en un type d’objet désérialisé. L’objet désérialisé est un enregistrement précis des propriétés du programme ou du composant à un moment précédent, mais il n’est plus « en temps réel », c’est-à-dire qu’il n’est plus directement associé au composant. Et, les méthodes sont supprimées, car elles ne sont plus efficaces.

En règle générale, vous pouvez utiliser des objets désérialisés de la même façon que vous utilisez des objets actifs, mais vous devez être conscient de leurs limitations. En outre, les objets retournés par l' `Invoke-Command` applet de commande ont des propriétés supplémentaires qui vous aident à déterminer l’origine de la commande.

Certains types d’objets, tels que les objets DirectoryInfo et les GUID, sont reconvertis en objets dynamiques lorsqu’ils sont reçus. Ces objets n’ont pas besoin d’une gestion ou d’une mise en forme spéciale.

Pour plus d’informations sur l’interprétation et la mise en forme de la sortie à distance, consultez [about_Remote_Output](about_Remote_Output.md).

### <a name="can-i-run-background-jobs-remotely"></a>Puis-je exécuter des tâches en arrière-plan à distance ?

Oui. Une tâche en arrière-plan PowerShell est une commande PowerShell qui s’exécute de façon asynchrone sans interagir avec la session. Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, et vous pouvez continuer à travailler dans la session pendant l’exécution de la tâche, même si elle s’exécute pendant une période prolongée.

Vous pouvez démarrer un travail en arrière-plan même si d’autres commandes sont en cours d’exécution, car les travaux en arrière-plan s’exécutent toujours de façon asynchrone dans une session temporaire.

Vous pouvez exécuter des tâches en arrière-plan sur un ordinateur local ou distant. Par défaut, une tâche en arrière-plan s’exécute sur l’ordinateur local. Toutefois, vous pouvez utiliser le paramètre **AsJob** de l' `Invoke-Command` applet de commande pour exécuter une commande à distance en tant que tâche en arrière-plan. Et, vous pouvez utiliser `Invoke-Command` pour exécuter une `Start-Job` commande à distance.

Pour plus d’informations sur les tâches en arrière-plan dans PowerShell, consultez [about_Jobs (about_Jobs. MD)] et [about_Remote_Jobs (about_Remote_Jobs. MD)].

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a>Puis-je exécuter des programmes Windows sur un ordinateur distant ?

Vous pouvez utiliser les commandes à distance PowerShell pour exécuter des programmes Windows sur des ordinateurs distants. Par exemple, vous pouvez exécuter `Shutdown.exe` ou `Ipconfig.exe` sur un ordinateur distant.

Toutefois, vous ne pouvez pas utiliser de commandes PowerShell pour ouvrir l’interface utilisateur d’un programme sur un ordinateur distant.

Lorsque vous démarrez un programme Windows sur un ordinateur distant, la commande n’est pas terminée et l’invite de commandes PowerShell ne retourne pas, jusqu’à ce que le programme soit terminé ou que vous appuyiez sur <kbd>CTRL</kbd> + <kbd>C</kbd> pour interrompre la commande. Par exemple, si vous exécutez le `Ipconfig.exe` programme sur un ordinateur distant, l’invite de commandes n’est pas renvoyée tant que `Ipconfig.exe` n’est pas terminé.

Si vous utilisez des commandes à distance pour démarrer un programme avec une interface utilisateur, le processus de programme démarre, mais l’interface utilisateur n’apparaît pas. La commande PowerShell n’est pas terminée, et l’invite de commandes ne retourne pas tant que vous n’arrêtez pas le processus du programme ou que vous n’appuyez pas sur <kbd>CTRL</kbd> + <kbd>C</kbd>, ce qui interrompt la commande et arrête le processus.

Par exemple, si vous utilisez une commande PowerShell pour l’exécuter `Notepad` sur un ordinateur distant, le processus du bloc-notes démarre sur l’ordinateur distant, mais l’interface utilisateur du bloc-notes n’apparaît pas. Pour interrompre la commande et restaurer l’invite de commandes, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a>Puis-je limiter les commandes que les utilisateurs peuvent exécuter à distance sur mon ordinateur ?

Oui. Chaque session à distance doit utiliser l’une des configurations de session sur l’ordinateur distant. Vous pouvez gérer les configurations de session sur votre ordinateur (et les autorisations sur ces configurations de session) pour déterminer qui peut exécuter des commandes à distance sur votre ordinateur et les commandes qu’ils peuvent exécuter.

Une configuration de session configure l’environnement pour la session. Vous pouvez définir la configuration à l’aide d’un assembly qui implémente une nouvelle classe de configuration ou à l’aide d’un script qui s’exécute dans la session. La configuration peut déterminer les commandes qui sont disponibles dans la session.
De plus, la configuration peut inclure des paramètres qui protègent l’ordinateur, tels que des paramètres qui limitent la quantité de données que la session peut recevoir à distance dans un objet ou une commande unique. Vous pouvez également spécifier un descripteur de sécurité qui détermine les autorisations requises pour utiliser la configuration.

L' `Enable-PSRemoting` applet de commande crée les configurations de session par défaut sur votre ordinateur : Microsoft. PowerShell, Microsoft. PowerShell. Workflow et Microsoft. powershell32 (systèmes d’exploitation 64 bits uniquement). `Enable-PSRemoting` définit le descripteur de sécurité pour la configuration afin d’autoriser uniquement les membres du groupe Administrateurs sur votre ordinateur à les utiliser.

Vous pouvez utiliser les applets de commande de configuration de session pour modifier les configurations de session par défaut, pour créer de nouvelles configurations de session et pour modifier les descripteurs de sécurité de toutes les configurations de session.

À compter de Windows PowerShell 3,0, l’applet de commande `New-PSSessionConfigurationFile` vous permet de créer des configurations de session personnalisées à l’aide d’un fichier texte. Le fichier comprend des options permettant de définir le mode de langage et de spécifier les applets de commande et les modules disponibles dans les sessions qui utilisent la configuration de session.

Quand les utilisateurs utilisent `Invoke-Command` les `New-PSSession` applets de commande, ou, `Enter-PSSession` ils peuvent utiliser le paramètre **ConfigurationName** pour indiquer la configuration de session utilisée pour la session. Ils peuvent modifier la configuration par défaut utilisée par leurs sessions en modifiant la valeur de la `$PSSessionConfigurationName` variable de préférence dans la session.

Pour plus d’informations sur les configurations de session, consultez l’aide sur les applets de commande de configuration de session. Pour rechercher les applets de commande de configuration de session, tapez :

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a>Que sont les configurations de ventilateur et de ventilateur ?

Le scénario de communication à distance PowerShell le plus courant impliquant plusieurs ordinateurs est la configuration un-à-plusieurs, dans laquelle un ordinateur local (l’ordinateur de l’administrateur) exécute des commandes PowerShell sur de nombreux ordinateurs distants. C’est ce que l’on appelle le scénario de « Fanout ».

Toutefois, dans certaines entreprises, la configuration est de type plusieurs-à-un, où de nombreux ordinateurs clients se connectent à un ordinateur distant unique exécutant PowerShell, tel qu’un serveur de fichiers ou une borne. C’est ce que l’on appelle la configuration « fan-in ».

La communication à distance PowerShell prend en charge les configurations de ventilateur et de ventilateur.

Pour la configuration de Fanout, PowerShell utilise le protocole WS-Management (Web Services for Management) et le service WinRM qui prend en charge l’implémentation Microsoft de WS-Management. Lorsqu’un ordinateur local se connecte à un ordinateur distant, WS-Management établit une connexion et utilise un plug-in pour PowerShell pour démarrer le processus hôte PowerShell (Wsmprovhost.exe) sur l’ordinateur distant. L’utilisateur peut spécifier un autre port, une autre configuration de session et d’autres fonctionnalités pour personnaliser la connexion à distance.

Pour prendre en charge la configuration « fan-in », PowerShell utilise Internet Information Services (IIS) pour héberger WS-Management, charger le plug-in PowerShell et Démarrer PowerShell. Dans ce scénario, au lieu de démarrer chaque session PowerShell dans un processus distinct, toutes les sessions PowerShell s’exécutent dans le même processus hôte.

L’hébergement IIS et la gestion à distance du fan-in ne sont pas pris en charge dans Windows XP ou Windows Server 2003.

Dans une configuration de fan-in, l’utilisateur peut spécifier un URI de connexion et un point de terminaison HTTP, y compris le transport, le nom de l’ordinateur, le port et le nom de l’application.
IIS transfère toutes les demandes avec un nom d’application spécifié à l’application. La valeur par défaut est WS-Management, qui peut héberger PowerShell.

Vous pouvez également spécifier un mécanisme d’authentification et interdire ou autoriser la redirection à partir de points de terminaison HTTP et HTTPs.

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a>Puis-je tester la communication à distance sur un seul ordinateur qui n’est pas dans un domaine ?

Oui. La communication à distance PowerShell est disponible même lorsque l’ordinateur local n’est pas dans un domaine. Vous pouvez utiliser les fonctionnalités de communication à distance pour vous connecter à des sessions et créer des sessions sur le même ordinateur. Les fonctionnalités fonctionnent de la même façon que lorsque vous vous connectez à un ordinateur distant.

Pour exécuter des commandes à distance sur un ordinateur dans un groupe de travail, modifiez les paramètres Windows suivants sur l’ordinateur.

ATTENTION : ces paramètres affectent tous les utilisateurs du système et peuvent rendre le système plus vulnérable à une attaque malveillante. Soyez prudent lorsque vous apportez ces modifications.

- Windows Vista, Windows 7, Windows 8 :

  Créez l’entrée de Registre suivante, puis définissez sa valeur sur 1 : LocalAccountTokenFilterPolicy dans ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

  Vous pouvez utiliser la commande PowerShell suivante pour ajouter cette entrée :

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2 :

  Aucune modification n’est nécessaire, car le paramètre par défaut de la stratégie « accès réseau : modèle de partage et de sécurité pour les comptes locaux » est « classique ». Vérifiez le paramètre en cas de modification de celui-ci.

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a>Puis-je exécuter des commandes à distance sur un ordinateur dans un autre domaine ?

Oui. En règle générale, les commandes s’exécutent sans erreur, même si vous devrez peut-être utiliser le paramètre **Credential** des `Invoke-Command` applets de commande, `New-PSSession` ou `Enter-PSSession` pour fournir les informations d’identification d’un membre du groupe Administrateurs sur l’ordinateur distant. Cela est parfois nécessaire même lorsque l’utilisateur actuel est membre du groupe Administrateurs sur les ordinateurs locaux et distants.

Toutefois, si l’ordinateur distant n’est pas dans un domaine approuvé par l’ordinateur local, l’ordinateur distant peut ne pas être en mesure d’authentifier les informations d’identification de l’utilisateur.

Pour activer l’authentification, utilisez la commande suivante pour ajouter l’ordinateur distant à la liste des hôtes approuvés pour l’ordinateur local dans WinRM. Tapez la commande à l’invite PowerShell.

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

Par exemple, pour ajouter l’ordinateur SERVEUR01 à la liste des hôtes approuvés sur l’ordinateur local, tapez la commande suivante à l’invite de commandes PowerShell :

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a>PowerShell prend-il en charge la communication à distance via SSH ?

Oui. Pour plus d’informations, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="see-also"></a>Voir aussi

[about_Remote](about_Remote.md)

[about_Profiles](about_Profiles.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote_Jobs](about_Remote_Jobs.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
