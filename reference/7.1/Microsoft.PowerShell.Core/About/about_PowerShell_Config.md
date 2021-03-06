---
description: Fichiers de configuration pour PowerShell, remplaçant la configuration du Registre.
Locale: en-US
ms.date: 03/12/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: 80ff02200b066c6f4f5eb355d5ed08894235e986
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412883"
---
# <a name="about-powershell-config"></a>À propos de la configuration de PowerShell

## <a name="short-description"></a>DESCRIPTION COURTE
Fichiers de configuration pour PowerShell Core, remplaçant la configuration du Registre.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le `powershell.config.json` fichier contient des paramètres de configuration pour PowerShell Core. PowerShell charge cette configuration au démarrage. Les paramètres peuvent également être modifiés au moment de l’exécution. Auparavant, ces paramètres étaient stockés dans le Registre Windows pour PowerShell, mais ils sont maintenant contenus dans un fichier pour permettre la configuration sur macOS et Linux.

> [!WARNING]
> Les clés non reconnues ou les valeurs non valides dans le fichier de configuration sont ignorées en mode silencieux. Si le `powershell.config.json` fichier contient un JSON non valide, PowerShell ne peut pas démarrer une session interactive. Si cela se produit, vous devez corriger le fichier de configuration.

### <a name="allusers-shared-configuration"></a>Configuration de AllUsers (partagée)

Un `powershell.config.json` fichier du `$PSHOME` répertoire définit la configuration de toutes les sessions PowerShell Core en cours d’exécution à partir de cette installation de PowerShell Core.

> [!NOTE]
> L' `$PSHOME` emplacement est défini comme le même répertoire que l’assembly System.Management.Automation.dll en cours d’exécution. Cela s’applique également aux instances du kit de développement logiciel (SDK) PowerShell hébergé.

### <a name="currentuser-per-user-configurations"></a>Configuration CurrentUser (par utilisateur)

Vous pouvez également configurer PowerShell par utilisateur en plaçant le fichier dans le répertoire de configuration de l’étendue utilisateur. Le répertoire de configuration utilisateur peut être trouvé entre les plateformes à l’aide de la commande `Split-Path $PROFILE.CurrentUserCurrentHost` .

## <a name="general-configuration-settings"></a>Paramètres de configuration généraux

### <a name="executionpolicy"></a>ExecutionPolicy

> [!IMPORTANT]
> Cette configuration s’applique uniquement sur les plateformes Windows.

Configure la stratégie d’exécution pour les sessions PowerShell, en déterminant les scripts qui peuvent être exécutés. Par défaut, PowerShell utilise la stratégie d’exécution existante.

Pour les configurations de AllUsers, cela définit la stratégie d’exécution de **LocalMachine** .
Pour les configurations CurrentUser, définit la stratégie d’exécution **CurrentUser** .

> [!NOTE]
> L' [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) applet de commande modifie ce paramètre dans le fichier de configuration ALLUSERS quand il est appelé avec `-Scope LocalMachine` et modifie ce paramètre dans le fichier de configuration CurrentUser lorsqu’il est appelé avec `-Scope CurrentUser` .

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

Où :

- `<shell-id>` fait référence à l’ID de l’hôte PowerShell actuel. Pour PowerShell Core normal, il s’agit de `Microsoft.PowerShell` . Dans une session PowerShell, vous pouvez la découvrir avec `$ShellId` .
- `<execution-policy>` fait référence à un nom de stratégie d’exécution valide.

L’exemple suivant définit la stratégie d’exécution de PowerShell sur `RemoteSigned` .

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

Dans Windows, les clés de Registre équivalentes se trouvent dans `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` sous `HKEY_LOCAL_MACHINE` et `HKEY_CURRENT_USER` .

### <a name="psmodulepath"></a>PSModulePath

Remplace les `PSModulePath` paramètres de cette session PowerShell. Si la configuration est pour l’utilisateur actuel, définit le chemin d’accès du module **CurrentUser** . Si la configuration est pour tous les utilisateurs, définit le chemin d’accès du module **ALLUSERS** .

> [!WARNING]
> La configuration d’un chemin de module **ALLUSERS** ou **CurrentUser** ici ne change pas l’emplacement d’installation d’étendue pour les applets de commande PowerShellGet comme [install-module](/powershell/module/powershellget/install-module). Ces applets de commande utilisent toujours les chemins de module _par défaut_ .

Si aucune valeur n’est définie, PowerShell utilise la valeur par défaut pour le paramètre de chemin d’accès du module respectif. Pour plus d’informations sur ces valeurs par défaut, consultez [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath).

Ce paramètre permet d’utiliser les variables d’environnement en les incorporant entre des `%` caractères, comme `"%HOME%\Documents\PowerShell\Modules"` , de la même façon que cmd le permet. Cette syntaxe s’applique également à Linux et macOS. Consultez les exemples ci-dessous.

```Schema
"PSModulePath": "<ps-module-path>"
```

Où :

- `<ps-module-path>` est le chemin d’accès absolu d’un répertoire de module. Pour toutes les configurations utilisateur, il s’agit du répertoire du module partagé AllUsers. Pour les configurations utilisateur actuelles, il s’agit du répertoire du module CurrentUser.

Cet exemple illustre une `PSModulePath` configuration pour un environnement Windows :

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

Cet exemple illustre une `PSModulePath` configuration pour un environnement MacOS ou Linux :

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

Cet exemple illustre l’incorporation d’une variable d’environnement dans une `PSModulePath` Configuration. Notez que l’utilisation de la `HOME` variable d’environnement et du `/` séparateur de répertoires fonctionne sur Windows, MacOS et Linux.

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

Cet exemple illustre l’incorporation d’une variable d’environnement dans une `PSModulePath` configuration qui fonctionne uniquement sur MacOS et Linux :

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> Les variables PowerShell ne peuvent pas être incorporées dans des `PSModulePath` configurations.
> `PSModulePath` les configurations sur Linux et macOS respectent la casse. Une `PSModulePath` configuration doit utiliser des séparateurs de répertoire valides pour la plateforme. Sur macOS et Linux, cela signifie `/` . Sur Windows, `/` et `\` fonctionnent.

### <a name="experimentalfeatures"></a>ExperimentalFeatures

Noms des fonctionnalités expérimentales à activer dans PowerShell. Par défaut, aucune fonctionnalité expérimentale n’est activée. La valeur par défaut est un tableau vide.

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

Où :

- `<experimental-feature-name>` nom d’une fonctionnalité expérimentale à activer.

L’exemple suivant active les fonctionnalités expérimentales **PSImplicitRemoting** et **PSUseAbbreviationExpansion** lors du démarrage de PowerShell.

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

Pour plus d’informations sur les fonctionnalités expérimentales, consultez [utilisation des fonctionnalités expérimentales](/powershell/scripting/learn/experimental-features).

## <a name="non-windows-logging-configuration"></a>Configuration de la journalisation non-Windows

> [!IMPORTANT]
> Les options de configuration de cette section s’appliquent uniquement à macOS et Linux.
> La journalisation pour Windows est gérée par le observateur d’événements Windows.

La journalisation de PowerShell sur macOS et Linux peut être configurée dans le fichier de configuration PowerShell. Pour obtenir une description complète de la journalisation PowerShell pour les systèmes non-Windows, consultez [à propos de la journalisation](./about_Logging_Non-Windows.md).

### <a name="logidentity"></a>LogIdentity

> [!IMPORTANT]
> Ce paramètre peut uniquement être utilisé dans macOS et Linux.

Définit le nom d’identité utilisé pour écrire dans le journal système. La valeur par défaut est « PowerShell ».

```Schema
"LogIdentity": "<log-identity>"
```

Où :

- `<log-identity>` identité de la chaîne que PowerShell doit utiliser pour écrire dans syslog.

> [!NOTE]
> Vous souhaiterez peut-être avoir différentes valeurs **LogIdentity** pour chaque instance différente de PowerShell que vous avez installée.

Dans cet exemple, nous configurons **LogIdentity** pour une version préliminaire de PowerShell.

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a>LogLevel

> [!IMPORTANT]
> Ce paramètre peut uniquement être utilisé dans macOS et Linux.

Spécifie le niveau de gravité minimal auquel PowerShell doit se connecter.

```Schema
"LogLevel": "<log-level>|default"
```

Où :

- `<log-level>` a l’une des valeurs suivantes :
  - Toujours
  - Critique
  - Error
  - Avertissement
  - Informationnel
  - Commentaires
  - Débogage

> [!NOTE]
> La définition d’un niveau de journalisation active tous les niveaux de journal au-dessus de celui-ci.

L’affectation de la valeur **par défaut** à ce paramètre est interprétée comme la valeur par défaut.
La valeur par défaut est **informatif**.

L’exemple suivant définit la valeur sur **Verbose**.

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a>LogChannels

> [!IMPORTANT]
> Ce paramètre peut uniquement être utilisé dans macOS et Linux.

Détermine les canaux de journalisation qui sont activés.

```Schema
"LogChannels": "<log-channel>,..."
```

Où :

- `<log-channel>` a l’une des valeurs suivantes :
  - Operational : journalise des informations de base sur les activités PowerShell
  - Analyse-journalise des informations de diagnostic plus détaillées

La valeur par défaut est **Operational**. Pour activer les deux canaux, incluez les deux valeurs sous la forme d’une seule chaîne séparée par des virgules. Par exemple :

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a>LogKeywords

> [!IMPORTANT]
> Ce paramètre peut uniquement être utilisé dans macOS et Linux.

Détermine les parties de PowerShell qui sont journalisées. Par défaut, tous les mots clés de journal sont activés. Pour activer plusieurs mots clés, répertoriez les valeurs dans une seule chaîne séparée par des virgules.

```Schema
"LogKeywords": "<log-keyword>,..."
```

Où :

- `<log-keyword>` a l’une des valeurs suivantes :
  - Runspace-gestion de l’instance d’exécution
  - Pipeline-opérations de pipeline
  - Gestion du protocole de communication par protocole, par exemple PSRP
  - Transport-prise en charge de la couche transport, telle que SSH
  - Fonctionnalités hôtes PowerShell hôtes, par exemple l’interaction de la console
  - Applets de commande-applets de commande builtin PowerShell
  - Sérialiseur-logique de sérialisation
  - Session-État de session PowerShell
  - ManagedPlugin-plug-in WSMan

> [!NOTE]
> Il est généralement recommandé de conserver cette valeur non définie, sauf si vous essayez de diagnostiquer un comportement spécifique dans une partie connue de PowerShell. La modification de cette valeur réduit uniquement la quantité d’informations journalisées.

Cet exemple limite la journalisation aux opérations d’instance d’exécution, à la logique de pipeline et à l’utilisation des applets de commande. Tous les autres enregistrements sont omis.

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a>Autres exemples de configurations

### <a name="example-windows-configuration"></a>Exemple de configuration de Windows

Cette configuration a davantage de paramètres définis explicitement :

- La stratégie d’exécution pour cette installation de PowerShell est `AllSigned`
- Le chemin d’accès du module CurrentUser est défini sur un répertoire de module sur un lecteur partagé
- La `PSImplicitRemotingBatching` fonctionnalité expérimentale est activée

> [!NOTE]
> Les `ExecutionPolicy` paramètres et ne `PSModulePath` fonctionnent que sur une plate-forme Windows, car le chemin d’accès du module utilise `\` des `;` caractères de séparation et et la stratégie d’exécution n’est pas `Unrestricted` (la seule stratégie autorisée sur les plateformes de type UNIX).

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a>Exemple de configuration non-Windows

Cette configuration définit un certain nombre d’options qui fonctionnent uniquement dans macOS ou Linux :

- Le chemin d’accès du module CurrentUser est défini sur un répertoire de module personnalisé dans `$HOME`
- La fonctionnalité expérimental **PSImplicitRemotingBatching** est activée
- Le niveau de journalisation PowerShell est défini sur **Verbose**, pour plus d’informations sur la journalisation
- Cette installation de PowerShell écrit dans les journaux à l’aide de l’identité **PowerShell d’hébergement** .

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a>Voir aussi

[À propos des stratégies d’exécution](./about_Execution_Policies.md)

[À propos des variables automatiques](./about_Automatic_Variables.md)
