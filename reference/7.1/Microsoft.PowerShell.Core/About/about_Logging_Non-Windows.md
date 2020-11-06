---
description: PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: f70e2cb2c04287e36ecdf21a97dd099fcfd23d65
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355491"
---
# <a name="about-logging-non-windows"></a>À propos de la journalisation non-Windows

## <a name="short-description"></a>Description courte
PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.

## <a name="long-description"></a>Description longue

PowerShell journalise les détails des opérations PowerShell. Par exemple, PowerShell enregistre les opérations telles que le démarrage et l’arrêt du moteur, ainsi que le démarrage et l’arrêt des fournisseurs. Elle enregistre également des détails sur les commandes PowerShell.

L’emplacement des journaux PowerShell dépend de la plateforme cible. Sur **Linux** , les journaux PowerShell dans **syslog** et **rsyslog. conf** peuvent être utilisés. Pour plus d’informations, consultez les pages locales de l’ordinateur Linux `man` . Sur **MacOS** , le système de journalisation **os_log** est utilisé. Pour plus d’informations, consultez [os_log documentation pour développeurs](https://developer.apple.com/documentation/os/os_log).

## <a name="viewing-powershell-log-output-on-linux"></a>Affichage de la sortie de journal PowerShell sur Linux

Les journaux PowerShell dans **syslog** sur Linux et les outils couramment utilisés pour afficher le contenu **syslog** peuvent être utilisés.

Le format des entrées de journal utilise le modèle suivant :

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|Champ        |Description                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |Date/heure de génération de l’entrée de journal.            |
|`MACHINENAME`|Nom du système sur lequel le journal a été généré.      |
|`PID`        |ID de processus du processus qui a écrit l’entrée de journal. |
|`COMMITID`   |`git commit`ID ou balise utilisé pour générer la Build.   |
|`TID`        |ID de thread du thread qui a écrit l’entrée de journal.   |
|`CID`        |Identificateur de canal hexadécimal de l’entrée de journal.            |
|             |10 = opérationnel, 11 = analyse                         |
|`EVENTID`    |Identificateur d’événement de l’entrée de journal.                  |
|`TASK`       |Identificateur de tâche pour l’entrée d’événement.                 |
|`OPCODE`     |Opcode de l’entrée d’événement.                          |
|`LEVEL`      |Niveau de journalisation de l’entrée d’événement.                       |
|`MESSAGE`    |Message associé à l’entrée d’événement.             |

> [!NOTE]
> `EVENTID`, `TASK` , `OPCODE` et `LEVEL` sont les mêmes valeurs que celles utilisées lors de la journalisation dans le journal des événements Windows.

### <a name="filtering-powershell-log-entries-using-rsyslog"></a>Filtrage des entrées de journal PowerShell à l’aide de rsyslog

Normalement, les entrées de journal PowerShell sont écrites dans la valeur par défaut `location/file` pour **syslog**. Toutefois, il est possible de rediriger les entrées vers un fichier personnalisé.

1. Créez une configuration de journal conf pour PowerShell et fournissez un nombre inférieur à 50 (pour `50-default.conf` ), par exemple `40-powershell.conf` . Le fichier doit être placé sous `/etc/rsyslog.d` .

1. Ajoutez l’entrée suivante au fichier :

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. Assurez-vous que `/etc/rsyslog.conf` le nouveau fichier est inclus. Souvent, elle aura une instruction include générique qui ressemble à la configuration suivante :

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   Si ce n’est pas le cas, vous devez ajouter une instruction include manuellement.

1. Vérifiez que les attributs et les autorisations sont correctement définis.

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. Définissez la propriété sur **root**.

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. Définir les autorisations d’accès : la **racine** est en lecture/écriture, **les utilisateurs** ont accès en lecture.

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a>Affichage de la sortie du journal PowerShell sur macOS

La méthode la plus simple pour afficher la sortie de journal PowerShell sur macOS est l’utilisation de l’application **console** .

1. Recherchez l’application **console** et lancez-la.
1. Sélectionnez le nom de l’ordinateur sous **appareils**.
1. Dans le champ de **recherche** , entrez `pwsh` pour le binaire principal PowerShell.
1. Remplacez le filtre de recherche `Any` par `Process` .
1. Effectuez les opérations.
1. Si vous le souhaitez, enregistrez la recherche pour une utilisation ultérieure.

Pour filtrer sur une instance de processus spécifique de PowerShell dans la **console** , la variable `$pid` contient l’ID de processus.

1. Entrez le **PID** (ID de processus) dans le champ de **recherche** .
1. Modifiez le filtre de recherche en `PID` .
1. Effectuez les opérations.

### <a name="viewing-powershell-log-output-from-a-command-line"></a>Affichage de la sortie de journal PowerShell à partir d’une ligne de commande

La `log` commande peut être utilisée pour afficher les entrées de journal PowerShell à partir de la ligne de commande.

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a>Persistance de la sortie du journal PowerShell

Par défaut, PowerShell utilise la journalisation par défaut de la mémoire uniquement sur macOS. Ce comportement peut être modifié pour activer la persistance à l’aide de la `log config` commande.

Le script suivant active la journalisation et la persistance au niveau des informations :

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

La commande suivante rétablit l’État par défaut de la journalisation PowerShell :

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

Une fois la persistance activée, la `log show` commande peut être utilisée pour exporter des éléments de journal. La commande fournit des options pour exporter les N derniers éléments, les éléments depuis un moment donné, ou des éléments dans un intervalle de temps donné.

Par exemple, la commande suivante exporte des éléments depuis `9am on April 5 of 2018` :

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

Vous pouvez obtenir de l’aide pour `log` en exécutant `log show --help` pour plus d’informations.

> [!TIP]
> Quand vous exécutez l’une des commandes de journal à partir d’une invite ou d’un script PowerShell, utilisez des guillemets doubles autour de la chaîne de prédicat entière et des guillemets simples dans. Cela évite de devoir échapper les caractères de guillemet double dans la chaîne de prédicat.

Vous pouvez également envisager d’enregistrer les journaux des événements dans un emplacement plus sécurisé, tel qu’un collecteur de journaux des événements centraux ou un agrégateur [Siem][] . Vous pouvez configurer SIEM dans Azure. Pour plus d’informations, consultez [intégration Siem générique](/cloud-app-security/siem).

## <a name="configuring-logging-on-a-non-windows-system"></a>Configuration de la journalisation sur un système non-Windows

Sur Windows, la journalisation est configurée en créant des écouteurs de suivi ETW ou en utilisant le observateur d’événements pour activer la journalisation analytique. Sur Linux et macOS, la journalisation est configurée à l’aide du fichier `powershell.config.json` . Le reste de cette section traite de la configuration de la journalisation PowerShell sur un système non-Windows.

Par défaut, PowerShell active la journalisation d’informations sur le canal opérationnel. Cela signifie que toute sortie de journal produite par PowerShell marquée comme opérationnelle et dont le niveau de journalisation (suivi) est supérieur à information est consigné. Parfois, les diagnostics peuvent nécessiter une sortie de journal supplémentaire, par exemple une sortie de journal détaillée ou l’activation de la sortie de journal analytique.

Le fichier `powershell.config.json` est un fichier au format **JSON** résidant dans le `$PSHOME` répertoire PowerShell. Chaque installation de PowerShell utilise sa propre copie de ce fichier. Pour un fonctionnement normal, ce fichier reste inchangé. Bien qu’il puisse être utile, pour modifier certains paramètres dans le fichier, pour le diagnostic ou pour distinguer plusieurs versions de PowerShell sur le même système ou même plusieurs copies de la même version (voir `LogIdentity` dans le tableau ci-dessous).

Le code suivant est un exemple de configuration :

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

Les propriétés de configuration de la journalisation PowerShell sont répertoriées dans le tableau suivant. Les valeurs marquées d’un astérisque, telles que `Operational*` , indiquent la valeur par défaut quand aucune valeur n’est fournie dans le fichier.

|Propriété   |Valeurs        |Description                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|(nom de chaîne) |Nom à utiliser lors de la journalisation. Par défaut,  |
|           |PowerShell   |PowerShell est l’identité. Cette valeur peut être|
|           |              |permet d’indiquer la différence entre deux      |
|           |              |les instances d’une installation PowerShell, telles que |
|           |              |comme version bêta. Cette valeur est |
|           |              |également utilisé pour rediriger la sortie du journal vers un        |
|           |              |fichier distinct sur Linux. Consultez la discussion sur|
|           |              |**rsyslog** ci-dessus.                           |
|`LogChannels`|Quotidiennes  |Canaux à activer. Séparer les valeurs|
|           |Analytiques      |avec une virgule quand vous spécifiez plusieurs.  |
|`LogLevel`   |Always        |Spécifiez une valeur unique. La valeur active  |
|           |Critique      |elle-même et toutes les valeurs qui la précèdent dans le        |
|           |Erreur         |liste à gauche.                            |
|           |Avertissement       |                                             |
|           |D’information|                                             |
|           |Commentaires       |                                             |
|           |Débogage         |                                             |
|`LogKeywords`|Instance d'exécution      |Les mots clés permettent de limiter la journalisation|
|           |Pipeline      |à des composants spécifiques dans PowerShell. par |
|           |Protocole      |par défaut, tous les mots clés sont activés et modifiés |
|           |Transport     |Cette valeur est utile uniquement pour les           |
|           |Host          |résolution des problèmes spécialisés.                |
|           |Applets de commande       |                                             |
|           |serializer    |                                             |
|           |session       |                                             |
|           |ManagedPlugin |                                             |

## <a name="see-also"></a>Voir aussi

Pour les informations relatives à **syslog** et **rsyslog. conf** Linux, reportez-vous aux pages locales de l’ordinateur Linux `man` .

Pour plus d’informations sur le **Os_log** MacOS, consultez [os_log documentation du développeur](https://developer.apple.com/documentation/os/os_log).

[about_Logging_Windows](about_Logging_Windows.md)

[Intégration de SIEM générique](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
