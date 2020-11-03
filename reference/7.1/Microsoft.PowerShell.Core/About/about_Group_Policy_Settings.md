---
description: Décrit les paramètres de stratégie de groupe pour PowerShell
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: df2a3e9349dd3afbe621bd11b92ac5cdf552492a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206737"
---
# <a name="about-group-policy-settings"></a>À propos des paramètres de stratégie de groupe

## <a name="short-description"></a>Description courte
Décrit les paramètres de stratégie de groupe pour PowerShell

## <a name="long-description"></a>Description longue

PowerShell comprend des paramètres de stratégie de groupe pour vous aider à définir des valeurs de configuration cohérentes pour les ordinateurs Windows dans un environnement d’entreprise.

Les paramètres de stratégie de groupe PowerShell se trouvent dans les chemins d’accès de stratégie de groupe suivants :

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

Les paramètres de stratégie de groupe dans le chemin de configuration utilisateur ont priorité sur les paramètres de stratégie de groupe dans le chemin de configuration de l’ordinateur.

PowerShell 7 comprend des modèles de stratégie de groupe et un script d’installation dans `$PSHOME`.

Les outils de stratégie de groupe utilisent des fichiers de modèles d’administration (`.admx`, `.adml`) pour remplir les paramètres de stratégie dans l’interface utilisateur. Cela permet aux administrateurs de gérer les paramètres de stratégie basés sur le registre. Le `InstallPSCorePolicyDefinitions.ps1` script installe **PowerShell Core modèles d’administration** sur l’ordinateur local.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode       LastWriteTime         Length Name
----       -------------         ------ ----
-a---      2/27/2020 12:38 AM     15861 InstallPSCorePolicyDefinitions.ps1
-a---      2/27/2020 12:28 AM      9675 PowerShellCoreExecutionPolicy.adml
-a---      2/27/2020 12:28 AM      6201 PowerShellCoreExecutionPolicy.admx
```

Après avoir installé les modèles, vous pouvez modifier ces paramètres dans l’éditeur de stratégie de groupe ( `gpedit.msc` ).

Les stratégies sont les suivantes :

- Configuration de session de console : définit un point de terminaison de configuration dans lequel PowerShell est exécuté.
- Activer la journalisation des modules : définit la propriété **LogPipelineExecutionDetails** des modules.
- Activer la journalisation de blocs de scripts PowerShell : active la journalisation détaillée de tous les scripts PowerShell.
- Activer l’exécution des scripts : définit la stratégie d'exécution de PowerShell.
- Activer la transcription PowerShell : active la capture d’entrée et de sortie de commandes PowerShell dans des transcriptions textuelles.
- Définir le chemin source par défaut pour `Update-Help` : définit la source de l’aide actualisable dans un répertoire, et non sur Internet.

Chaque paramètre de stratégie de groupe PowerShell a une option (« utiliser le paramètre de stratégie Windows PowerShell ») pour utiliser la valeur d’un paramètre de stratégie de groupe Windows PowerShell similaire qui se trouve dans les chemins d’accès de stratégie de groupe suivants :

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

> [!NOTE]
> Ces **modèles d’administration PowerShell Core** n’incluent pas de paramètres pour Windows PowerShell. Pour plus d’informations sur l’acquisition d’autres modèles et la configuration de la stratégie de groupe, voir [How to Create and Manage the central Store for stratégie de groupe modèles d’administration dans Windows][gpstore].

## <a name="console-session-configuration"></a>Configuration de session de la console

Le paramètre de la stratégie de configuration de la session de la **console** spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté. Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.

## <a name="turn-on-module-logging"></a>Activer la journalisation des modules

Le paramètre de stratégie **activer la journalisation du module** active la journalisation pour les modules PowerShell sélectionnés. Le paramètre s’applique à toutes les sessions sur tous les ordinateurs concernés.

Si vous activez ce paramètre de stratégie et spécifiez un ou plusieurs modules, les événements d’exécution de pipeline pour les modules spécifiés sont enregistrés dans le journal Windows PowerShell dans observateur d’événements.

Si vous désactivez ce paramètre de stratégie, la journalisation des événements d’exécution est désactivée pour tous les modules PowerShell.

Si ce paramètre de stratégie n’est pas configuré, la propriété **LogPipelineExecutionDetails** de chaque module détermine si les événements d’exécution d’un module sont journalisés. Par défaut, la propriété **LogPipelineExecutionDetails** de tous les modules est définie sur false.

Pour activer la journalisation de module pour un module, utilisez le format de commande suivant. Le module doit être importé dans la session et le paramètre est effectif uniquement dans la session active.

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

Pour activer la journalisation des modules pour toutes les sessions sur un ordinateur particulier, ajoutez les commandes précédentes au profil PowerShell « tous les utilisateurs » ( `$Profile.AllUsersAllHosts` ).

Pour plus d’informations sur la journalisation des modules, consultez [about_Modules](about_Modules.md).

## <a name="turn-on-powershell-script-block-logging"></a>Activer la journalisation des blocs de script PowerShell

Le paramètre de stratégie activer la journalisation des **blocs de script PowerShell** active la journalisation de toutes les entrées de script PowerShell dans le journal des événements opérationnels de Microsoft-Windows-PowerShell/. Si vous activez ce paramètre de stratégie, PowerShell Core enregistre le traitement des commandes, des blocs de script, des fonctions et des scripts, qu’il soit appelé de manière interactive ou par le biais de l’automatisation.

Si vous désactivez ce paramètre de stratégie, la journalisation des entrées de script PowerShell est désactivée. Si vous activez la journalisation des appels de bloc de script, PowerShell journalise en plus les événements lors de l’appel d’une commande, un bloc de script, d’une fonction, ou quand un script démarre ou s’arrête. L’activation de la journalisation des appels génère un grand volume de journaux des événements.

## <a name="turn-on-script-execution"></a>Activer l’exécution du script

Le paramètre de stratégie **activer l’exécution du script** définit la stratégie d’exécution pour les ordinateurs et les utilisateurs, qui détermine quels scripts sont autorisés à s’exécuter.

Si vous activez le paramètre de stratégie, vous pouvez sélectionner parmi les paramètres de stratégie suivants.

- **Autoriser uniquement les scripts signés** permet aux scripts de s’exécuter uniquement s’ils sont signés par un éditeur approuvé. Ce paramètre de stratégie est équivalent à la stratégie d’exécution AllSigned.

- **Autoriser les scripts locaux et les scripts signés distants** autorise l’exécution de tous les scripts locaux. Les scripts provenant d’Internet doivent être signés par un éditeur approuvé. Ce paramètre de stratégie est équivalent à la stratégie d’exécution RemoteSigned.

- **Autoriser tous les scripts** autorise l’exécution de tous les scripts. Ce paramètre de stratégie équivaut à la stratégie d’exécution illimitée.

Si vous désactivez ce paramètre de stratégie, aucun script n’est autorisé à s’exécuter. Ce paramètre de stratégie est équivalent à la stratégie d’exécution restreinte.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, la stratégie d’exécution définie pour l’ordinateur ou l’utilisateur par l' `Set-ExecutionPolicy` applet de commande détermine si les scripts sont autorisés à s’exécuter. La valeur par défaut est Restricted.

Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).

## <a name="turn-on-powershell-transcription"></a>Activer la transcription PowerShell

Le paramètre de stratégie **activer la transcription PowerShell** vous permet de capturer l’entrée et la sortie des commandes PowerShell Core dans des transcriptions textuelles. Si vous activez ce paramètre de stratégie, PowerShell Core active la journalisation de la transcription pour PowerShell Core et toutes les autres applications qui exploitent le moteur PowerShell Core. Par défaut, PowerShell Core enregistre la sortie de transcription dans le répertoire Mes documents de chaque utilisateur, avec un nom de fichier qui comprend « PowerShell_transcript », ainsi que le nom de l’ordinateur et l’heure de début.
L’activation de cette stratégie revient à appeler l’applet de commande Start-Transcript sur chaque session PowerShell Core.

Si vous désactivez ce paramètre de stratégie, la journalisation transcription des applications basées sur PowerShell est désactivée par défaut, bien que la transcription puisse toujours être activée via l’applet de commande Start-Transcript.

Si vous utilisez le paramètre OutputDirectory pour activer la journalisation des transcriptions dans un emplacement partagé, veillez à limiter l’accès à ce répertoire pour empêcher les utilisateurs d’afficher les transcriptions d’autres utilisateurs ou ordinateurs.

## <a name="set-the-default-source-path-for-update-help"></a>Définir le chemin source par défaut de Update-Help

Le paramètre **définir le chemin d’accès source par défaut pour la stratégie Update-Help** définit une valeur par défaut pour le paramètre **SourcePath** de l’applet de commande `Update-Help` .
Ce paramètre empêche les utilisateurs d’utiliser l’applet de commande `Update-Help` pour télécharger les fichiers d’aide à partir d’Internet.

> [!NOTE]
> Ce paramètre stratégie de groupe s’affiche sous **Configuration ordinateur** et **Configuration utilisateur** . Toutefois, seul le paramètre stratégie de groupe sous **Configuration ordinateur** est effectif. Le paramètre stratégie de groupe sous **Configuration utilisateur** est ignoré.

L' `Update-Help` applet de commande télécharge et installe les fichiers d’aide les plus récents pour les modules PowerShell et les installe sur l’ordinateur. Par défaut, `Update-Help` télécharge les nouveaux fichiers d’aide à partir d’un emplacement Internet spécifié par le module.

Toutefois, vous pouvez utiliser l' `Save-Help` applet de commande pour télécharger les fichiers d’aide les plus récents vers un emplacement de système de fichiers, tel qu’un partage réseau, puis utiliser l' `Update-Help` applet de commande pour obtenir les fichiers d’aide à partir de l’emplacement du système de fichiers et les installer sur l’ordinateur. Le paramètre **SourcePath** de l' `Update-Help` applet de commande spécifie l’emplacement du système de fichiers.

En fournissant une valeur par défaut pour le paramètre **SourcePath** , ce stratégie de groupe paramètre ajoute implicitement le paramètre **SourcePath** à toutes les `Update-Help` commandes. Les utilisateurs peuvent remplacer l’emplacement spécifique du système de fichiers spécifié comme valeur par défaut en entrant un emplacement de système de fichiers différent.
Mais ils ne peuvent pas supprimer le paramètre **SourcePath** de la `Update-Help` commande.

Si vous activez ce paramètre de stratégie, vous pouvez spécifier une valeur par défaut pour le paramètre **SourcePath** . Entrez un emplacement de système de fichiers.

Si ce paramètre de stratégie est désactivé ou n’est pas configuré, il n’existe pas de valeur par défaut pour le paramètre **SourcePath** de l’applet de commande `Update-Help` . Les utilisateurs peuvent télécharger l’aide à partir d’Internet ou à partir de n’importe quel emplacement du système de fichiers.

Pour plus d’informations, voir [about_Updatable_Help](about_Updatable_Help.md).

## <a name="keywords"></a>Mots clés

about_Group_Policies about_GroupPolicy

## <a name="see-also"></a>Voir aussi

[RFC principale de la stratégie PowerShell](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Modules](about_Modules.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759

