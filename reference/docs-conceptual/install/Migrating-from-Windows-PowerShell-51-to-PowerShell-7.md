---
title: Migration de Windows PowerShell 5.1 vers PowerShell 7
description: Mise à jour de PowerShell 5.1 vers PowerShell 7 pour vos plateformes Windows.
ms.date: 03/25/2020
ms.openlocfilehash: cb14a4f159b6dc33f31386da4264c0ebb640aef8
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "83809205"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>Migration de Windows PowerShell 5.1 vers PowerShell 7

Conçu pour les environnements cloud, locaux et hybrides, PowerShell 7 intègre de nombreuses améliorations et [nouvelles fonctionnalités](../whats-new/What-s-New-in-PowerShell-70.md).

- S’installe et s’exécute côte à côte avec Windows PowerShell
- Meilleure compatibilité avec les modules Windows PowerShell existants
- Nouvelles fonctionnalités de langage, notamment les opérateurs ternaires et `ForEach-Object -Parallel`
- performances améliorées
- Communication à distance basée sur SSH
- Interopérabilité multiplateforme
- Prise en charge des conteneurs Docker

PowerShell 7 fonctionne côte à côte avec Windows PowerShell, ce qui vous permet de tester et de comparer facilement différentes versions avant le déploiement. La migration est simple, rapide et sécurisée.

PowerShell 7 est pris en charge sur les systèmes d'exploitation Windows suivants :

- Windows 8.1 et 10
- Windows Server 2012, 2012 R2, 2016 et 2019

PowerShell 7 s’exécute également sur macOS et plusieurs distributions Linux. Pour obtenir une liste des systèmes d’exploitation pris en charge et des informations sur le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle).

## <a name="installing-powershell-7"></a>Installation de PowerShell 7

Pour offrir plus de flexibilité et répondre aux besoins du service informatique, des ingénieurs DevOps et des développeurs, plusieurs options d’installation de PowerShell 7 sont disponibles. Dans la plupart des cas, les options d’installation peuvent se limiter aux méthodes suivantes :

- Déployer PowerShell à l’aide du [package MSI](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)
- Déployer PowerShell à l’aide du [package ZIP](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)

> [!NOTE]
> Le package MSI peut être déployé et mis à jour avec des produits de gestion, notamment [System Center Configuration Manager (SCCM)](/configmgr/apps/). Téléchargez les packages à partir de la [page de mise en production GitHub](https://github.com/PowerShell/PowerShell/releases).

Le déploiement du package MSI nécessite une autorisation d’administrateur. Le package ZIP peut être déployé par n’importe quel utilisateur. Le package ZIP constitue le moyen le plus simple d’installer PowerShell 7 à des fins de test, avant de procéder à une installation complète.

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>Utilisation de PowerShell 7 côte à côte avec Windows PowerShell 5.1

PowerShell 7 est conçu pour coexister avec Windows PowerShell 5.1. Les fonctionnalités suivantes protègent votre investissement dans PowerShell et simplifient la migration vers PowerShell 7.

- Chemins d’installation et noms d’exécutables distincts
- PSModulePath distinct
- Profils distincts pour chaque version
- Compatibilité améliorée des modules
- Nouveaux points de terminaison de communication à distance
- Prise en charge de la stratégie de groupe
- Journaux d’événements distincts

### <a name="separate-installation-path-and-executable-name"></a>Chemins d’installation et noms d’exécutables distincts

PowerShell 7 s’installe dans un nouveau répertoire, permettant une exécution côte à côte avec Windows PowerShell 5.1.

Emplacements d’installation par version :

- Windows PowerShell 5.1 : `$env:WINDIR\System32\WindowsPowerShell\v1.0`
- PowerShell Core 6.x : `$env:ProgramFiles\PowerShell\6`
- PowerShell 7 : `$env:ProgramFiles\PowerShell\7`

Le nouvel emplacement est ajouté à votre chemin d’accès, ce qui vous permet d’exécuter à la fois Windows PowerShell 5.1 et PowerShell 7. Si vous effectuez une migration de PowerShell Core 6.x vers PowerShell 7, PowerShell 6 est supprimé et le chemin d’accès remplacé.

Dans Windows PowerShell, l’exécutable PowerShell est nommé `powershell.exe`. Dans la version 6 et versions ultérieures, l’exécutable est nommé `pwsh.exe`. Le nouveau nom facilite la prise en charge de l’exécution côte à côte des deux versions.

### <a name="separate-psmodulepath"></a>PSModulePath distinct

Par défaut, Windows PowerShell et PowerShell 7 stockent les modules à différents emplacements. PowerShell 7 combine ces emplacements dans la variable d’environnement `$Env:PSModulePath`. Lors de l’importation d’un module par nom, PowerShell vérifie l’emplacement spécifié par `$Env:PSModulePath`. Cela permet à PowerShell 7 de charger à la fois les modules de base et de bureau.

|            Étendue Install            |                Windows PowerShell 5.1                 |             PowerShell 7.0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| Modules PowerShell                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| Installé par l’utilisateur<br>Étendue AllUsers    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| Installé par l’utilisateur<br>Étendue CurrentUser | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

Les exemples suivants montrent les valeurs par défaut de `$Env:PSModulePath` pour chaque version.

- Pour Windows PowerShell 5.1 :

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- Pour PowerShell 7 :

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

Notez que PowerShell 7 inclut les chemins d’accès Windows PowerShell et les chemins d’accès PowerShell 7 pour garantir le chargement automatique des modules.

> [!NOTE]
> Des chemins d’accès supplémentaires peuvent exister si vous avez modifié la variable d’environnement PSModulePath ou si vous avez installé des modules ou des applications personnalisés.

Pour plus d’informations, consultez `PSModulePath` dans [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).

Pour plus d'informations sur les modules, consultez [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).

### <a name="separate-profiles"></a>Profils distincts

Un profil PowerShell est un script qui s’exécute au démarrage de PowerShell. Ce script personnalise votre environnement en ajoutant des commandes, des alias, des fonctions, des variables, des modules et des lecteurs PowerShell. Le script de profil rend ces personnalisations disponibles dans chaque session, sans avoir à les recréer manuellement.

Le chemin d’accès vers l’emplacement du profil a changé dans PowerShell 7.

- Dans Windows PowerShell 5,1, l’emplacement du profil est `$HOME\Documents\WindowsPowerShell`.
- Dans PowerShell 7, l’emplacement du profil est `$HOME\Documents\PowerShell`.

Les noms des fichiers de profil ont également changé :

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

Pour plus d'informations, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>Compatibilité de PowerShell 7 avec les modules Windows PowerShell 5.1

La plupart des modules que vous utilisez dans Windows PowerShell 5.1 fonctionnent déjà avec PowerShell 7, y compris Azure PowerShell et Active Directory. Nous continuons à collaborer avec d’autres équipes afin d’ajouter une prise en charge native de PowerShell 7 pour d’autres modules, notamment Microsoft Graph, Office 365, entre autres. Pour obtenir la liste actuelle des modules pris en charge, consultez [Compatibilité des modules PowerShell 7](/powershell/scripting/whats-new/module-compatibility).

> [!NOTE]
> Sur Windows, nous avons également ajouté un commutateur **UseWindowsPowerShell** vers `Import-Module` afin de faciliter la transition vers PowerShell 7 pour ceux qui utilisent des modules incompatibles. Pour plus d’informations sur cette fonctionnalité, consultez [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).

### <a name="powershell-remoting"></a>Communication à distance PowerShell

La communication à distance PowerShell, vous permet d'exécuter n'importe quelle commande PowerShell sur un ou plusieurs ordinateurs distants. Vous pouvez établir des connexions persistantes, démarrer des sessions interactives et exécuter des scripts sur ordinateurs distants.

#### <a name="ws-management-remoting"></a>Communication à distance WS-Management

Windows PowerShell 5.1 et les versions antérieures utilisent le protocole WS-Management (WSMAN) pour la négociation de connexion et le transport de données. Windows Remote Management (WinRM) utilise le protocole WSMAN. Si WinRM a été activé, PowerShell 7 utilise le point de terminaison Windows PowerShell 5.1 existant, nommé `Microsoft.PowerShell`, pour les connexions de communication à distance. Pour mettre à jour PowerShell 7 afin d’inclure son propre point de terminaison, exécutez l’applet de commande `Enable-PSRemoting`. Pour plus d’informations sur la connexion à des points de terminaison spécifiques, consultez [Communication à distance WS-Management dans PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)

Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.
Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Pour plus d'informations sur l’utilisation de la communication à distance, consultez [À propos de la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote)

#### <a name="ssh-based-remoting"></a>Communication à distance basée sur SSH

La communication à distance basée sur SSH a été ajoutée dans PowerShell Core 6.x pour prendre en charge d’autres systèmes d’exploitation qui ne peuvent pas utiliser des composants natifs Windows comme **WinRM**. La communication à distance SSH crée un processus hôte PowerShell sur l’ordinateur cible en tant que sous-système SSH. Pour obtenir des informations et des exemples sur la configuration de la communication à distance basée sur SSH sur Windows ou Linux, consultez : [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> PowerShell Gallery (PSGallery) contient un module et une applet de commande qui configure automatiquement la communication à distance basée sur SSH. Installez le module `Microsoft.PowerShell.RemotingTools` à partir de [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0), puis exécutez l’applet de commande `Enable-SSH`.

Les applets de commande `New-PSSession`, `Enter-PSSession` et `Invoke-Command` intègrent de nouveaux jeux de paramètres pour prendre en charge les connexions SSH.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Pour créer une session distante, spécifiez l’ordinateur cible avec le paramètre **HostName** et indiquez le nom d’utilisateur avec **UserName**. Lors de l’exécution des cmdlets de manière interactive, vous êtes invité à entrer un mot de passe.

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

Si vous utilisez le paramètre **HostName**, vous pouvez également fournir les informations de nom d’utilisateur en y ajoutant le signe arobase (`@`) et le nom de l’ordinateur.

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

Vous pouvez configurer l’authentification par clé SSH à l’aide d’un fichier de clé privée avec le paramètre **KeyFilePath**.
Pour plus d’informations, consultez [Gestion des clés OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).

### <a name="group-policy-supported"></a>Stratégie de groupe prise en charge

PowerShell inclut des paramètres de stratégie de groupe qui vous aident à définir des valeurs d’option cohérentes pour les serveurs d’un environnement d’entreprise. Ces paramètres comprennent ce qui suit :

- Configuration de session de console : définit un point de terminaison de configuration dans lequel PowerShell est exécuté.
- Activer la journalisation des modules : définit la propriété LogPipelineExecutionDetails des modules.
- Activer la journalisation de blocs de scripts PowerShell : active la journalisation détaillée de tous les scripts PowerShell.
- Activer l’exécution des scripts : définit la stratégie d'exécution de PowerShell.
- Activer la transcription PowerShell : active la capture d’entrée et de sortie de commandes PowerShell dans des transcriptions textuelles.
- Définir le chemin source par défaut pour Update-Help : définit la source de l’aide actualisable sur un répertoire, et non sur Internet.

Pour plus d’informations, consultez [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).

PowerShell 7 comprend des modèles de stratégie de groupe et un script d’installation dans `$PSHOME`.

Les outils de stratégie de groupe utilisent des fichiers de modèles d’administration (`.admx`, `.adml`) pour remplir les paramètres de stratégie dans l’interface utilisateur. Cela permet aux administrateurs de gérer les paramètres de stratégie basés sur le registre. Le script `InstallPSCorePolicyDefinitions.ps1` installe les modèles d’administration PowerShell Core sur l’ordinateur local.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>Journaux d’événements distincts

Windows PowerShell et PowerShell 7 journalisent les événements dans des journaux d’événements distincts. Utilisez la commande suivante pour obtenir la liste des journaux PowerShell.

```powershell
Get-WinEvent -ListLog *PowerShell*
```

Pour plus d’informations, consultez [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).

## <a name="improved-editing-experience-with-visual-studio-code"></a>Amélioration de l’expérience de modification avec Visual Studio Code

[Visual Studio Code (VSCode)](https://code.visualstudio.com/) avec l’extension [PowerShell](https://code.visualstudio.com/docs/languages/powershell) est l’environnement de script pris en charge pour PowerShell 7. Windows PowerShell Integrated Scripting Environment (ISE) prend uniquement en charge Windows PowerShell.

L’extension PowerShell mise à jour comprend les éléments suivants :

- Nouveau mode de compatibilité ISE
- PSReadLine dans la console intégrée, notamment la mise en surbrillance de la syntaxe, la modification sur plusieurs lignes et la recherche en arrière
- Améliorations en matière de stabilité et de performances
- Nouvelle intégration CodeLens
- Amélioration de la saisie semi-automatique du chemin

Pour faciliter la transition vers Visual Studio Code, utilisez la fonction **Activer le mode ISE**, disponible dans la **palette de commandes**. Cette fonction bascule VSCode dans une disposition de style ISE. La disposition de style ISE vous offre toutes les nouvelles fonctionnalités et capacités de PowerShell dans une expérience utilisateur familière.

Pour basculer vers la nouvelle disposition ISE, appuyez sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> pour ouvrir la **de la palette de commandes**, tapez `PowerShell` et sélectionnez **PowerShell : Activez le mode ISE**.

Pour revenir à la disposition d’origine, ouvrez la **palette de commandes**, puis sélectionnez **PowerShell : Désactiver le mode ISE (restaurer les valeurs par défaut)**.

Pour plus d’informations sur la personnalisation de la disposition VSCode pour ISE, consultez [Guide pratique de réplication de l’expérience ISE dans Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)

> [!NOTE]
> Aucune mise à jour de l’environnement ISE avec de nouvelles fonctionnalités n’est prévue. L’environnement ISE est désormais une fonctionnalité qui n’est pas installée par l’utilisateur dans les dernières versions de Windows 10 et Windows Server. Il n’est pas prévu de supprimer définitivement l’environnement ISE. L’équipe PowerShell et ses partenaires se concentrent actuellement sur l’amélioration de l’expérience de script dans l’extension PowerShell pour Visual Studio Code.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous possédez les connaissances requises pour réussir votre migration, [installez PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) !
