---
description: Explique comment installer, importer et utiliser des modules PowerShell.
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: ab4e9658ed4820c3ae84ac1cd9a55b59cc8017ab
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564477"
---
# <a name="about-modules"></a>À propos des modules

## <a name="short-description"></a>Description courte
Explique comment installer, importer et utiliser des modules PowerShell.

## <a name="long-description"></a>Description longue

Un module est un package qui contient des membres PowerShell, tels que des applets de commande, des fournisseurs, des fonctions, des workflows, des variables et des alias.

Les personnes qui écrivent des commandes peuvent utiliser des modules pour organiser leurs commandes et les partager avec d'autres utilisateurs. Les personnes qui reçoivent des modules peuvent ajouter les commandes dans les modules à leurs sessions PowerShell et les utiliser comme les commandes intégrées.

Cette rubrique explique comment utiliser les modules PowerShell. Pour plus d’informations sur l’écriture de modules PowerShell, consultez [écriture d’un module PowerShell](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

## <a name="what-is-a-module"></a>Qu’est-ce qu’un module ?

Un module est un package qui contient des membres PowerShell, tels que des applets de commande, des fournisseurs, des fonctions, des workflows, des variables et des alias. Les membres de ce package peuvent être implémentés dans un script PowerShell, une DLL compilée ou une combinaison des deux. Ces fichiers sont généralement regroupés dans un seul répertoire. Pour plus d’informations, consultez [comprendre un module Windows PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) dans la documentation du kit de développement logiciel (SDK).

## <a name="module-auto-loading"></a>Chargement automatique des modules

À compter de PowerShell 3,0, PowerShell importe automatiquement les modules la première fois que vous exécutez une commande dans un module installé. Vous pouvez désormais utiliser les commandes d'un module sans même le configurer ni définir de profil. Une fois vos modules installés sur votre ordinateur, vous n'avez pas à vous en occuper.

Vous pouvez aussi trouver plus facilement les commandes contenues dans un module. L' `Get-Command` applet de commande obtient désormais toutes les commandes de tous les modules installés, même si elles n’ont pas encore été dans la session. Vous pouvez rechercher une commande et l’utiliser sans importer en premier lieu.

Chacun des exemples suivants provoque l’importation du module CimCmdlets, qui contient `Get-CimInstance` , dans votre session.

- Exécutez la commande

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- Obtient la commande

  ```powershell
  Get-Command Get-CimInstance
  ```

- Obtenir de l’aide pour la commande

  ```powershell
  Get-Help Get-CimInstance
  ```

`Get-Command` les commandes qui incluent un caractère générique ( `*` ) sont considérées comme étant destinées à être découvertes, ne sont pas utilisées et n’importent pas de modules.

Seuls les modules stockés à l’emplacement spécifié par la variable d’environnement PSModulePath sont importés automatiquement. Les modules dans d’autres emplacements doivent être importés en exécutant l’applet de commande `Import-Module` .

En outre, les commandes qui utilisent des fournisseurs PowerShell n’importent pas automatiquement un module. Par exemple, si vous utilisez une commande qui requiert le lecteur WSMan :, tel que l' `Get-PSSessionConfiguration` applet de commande, vous devrez peut-être exécuter l' `Import-Module` applet de commande pour importer le module **Microsoft. WSMan. Management** qui comprend le `WSMan:` lecteur.

Vous pouvez toujours exécuter la `Import-Module` commande pour importer un module et utiliser la `$PSModuleAutoloadingPreference` variable pour activer, désactiver et configurer l’importation automatique de modules. Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md).

## <a name="how-to-use-a-module"></a>Comment utiliser un module

Pour utiliser un module, procédez comme suit :

1. Installez le module. (Bien souvent, cette tâche ne vous incombe pas.)
1. Recherchez les commandes ajoutées par le module.
1. Utilisez les commandes ajoutées par le module.

Cette rubrique explique comment effectuer ces tâches. Elle contient également d'autres informations utiles sur la gestion des modules.

## <a name="how-to-install-a-module"></a>Comment installer un module

Si vous recevez un module sous la forme d’un dossier contenant des fichiers, vous devez l’installer sur votre ordinateur avant de pouvoir l’utiliser dans PowerShell.

La plupart des modules sont installés pour vous. PowerShell est fourni avec plusieurs modules préinstallés, parfois appelés modules _principaux_ . Sur les ordinateurs Windows, si des fonctionnalités incluses avec le système d’exploitation possèdent des applets de commande pour les gérer, ces modules sont préinstallés. Quand vous installez une fonctionnalité Windows, en utilisant, par exemple, l’Assistant Ajout de rôles et de fonctionnalités dans Gestionnaire de serveur, ou la boîte de dialogue Activer ou désactiver des fonctionnalités Windows dans le panneau de configuration, tous les modules PowerShell qui font partie de la fonctionnalité sont installés. D'autres modules sont fournis avec un programme d'installation.

Utilisez la commande suivante pour créer un répertoire **modules** pour l’utilisateur actuel :

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

Copiez le dossier du module en totalité dans le répertoire Modules. Vous pouvez utiliser n’importe quelle méthode pour copier le dossier, y compris l’Explorateur Windows et Cmd.exe, ainsi que PowerShell. Dans PowerShell, utilisez l’applet de commande `Copy-Item` . Par exemple, pour copier le dossier MyModule de dans `C:\ps-test\MyModule` le répertoire Modules, tapez :

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

Vous pouvez installer vos modules n'importe où, mais nous vous recommandons de les installer dans un emplacement de module par défaut pour faciliter leur gestion. Pour plus d’informations sur les emplacements par défaut des modules, consultez les sections [module et emplacements des ressources DSC et PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) .

## <a name="how-to-find-installed-modules"></a>Comment rechercher des modules installés

Pour trouver les modules qui sont installés dans un emplacement par défaut, mais qui ne sont pas encore dans votre session, tapez :

```powershell
Get-Module -ListAvailable
```

Pour rechercher les modules qui ont déjà été importés dans votre session, à l’invite de PowerShell, tapez :

```powershell
Get-Module
```

Pour plus d’informations sur l’applet de commande `Get-Module` , consultez la rubrique [obtenir-module](xref:Microsoft.PowerShell.Core.Get-Module).

## <a name="how-to-find-the-commands-in-a-module"></a>Comment rechercher les commandes dans un module

Utilisez l' `Get-Command` applet de commande pour rechercher toutes les commandes disponibles. Vous pouvez utiliser les paramètres de l' `Get-Command` applet de commande pour filtrer les commandes, par exemple par module, nom et substantif.

Pour trouver toutes les commandes dans un module, tapez :

```powershell
Get-Command -Module <module-name>
```

Par exemple, pour rechercher les commandes dans le module BitsTransfer, tapez :

```powershell
Get-Command -Module BitsTransfer
```

Pour plus d’informations sur l' `Get-Command` applet de commande, consultez la rubrique [obtenir-Command](xref:Microsoft.PowerShell.Core.Get-Command).

## <a name="how-to-get-help-for-the-commands-in-a-module"></a>Comment obtenir de l’aide pour les commandes d’un module

Si le module contient des fichiers d’aide pour les commandes qu’il exporte, l’applet de commande `Get-Help` affiche les rubriques d’aide. Utilisez le même `Get-Help` format de commande que celui que vous utiliseriez pour obtenir de l’aide pour n’importe quelle commande dans PowerShell.

À compter de PowerShell 3,0, vous pouvez télécharger les fichiers d’aide d’un module et télécharger les mises à jour des fichiers d’aide afin qu’elles ne soient jamais obsolètes.

Pour obtenir de l'aide sur une commande d'un module, tapez :

```powershell
Get-Help <command-name>
```

Pour obtenir de l’aide en ligne pour la commande dans un module, tapez :

```powershell
Get-Help <command-name> -Online
```

Pour télécharger et installer les fichiers d’aide pour les commandes d’un module, tapez :

```powershell
Update-Help -Module <module-name>
```

Pour plus d’informations, consultez la rubrique [obtenir-aide](xref:Microsoft.PowerShell.Core.Get-Help) et [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).

## <a name="how-to-import-a-module"></a>Comment importer un module

Vous pouvez être amené à importer un module ou un fichier de module. L’importation est requise lorsqu’un module n’est pas installé dans les emplacements spécifiés par la variable d’environnement **PSModulePath** , `$env:PSModulePath` ou le module se compose d’un fichier, tel qu’un fichier. dll ou. psm1, au lieu d’un module standard fourni sous forme de dossier.

Vous pouvez également choisir d’importer un module pour pouvoir utiliser les paramètres de la `Import-Module` commande, tels que le paramètre prefix, qui ajoute un préfixe unique aux noms de toutes les commandes importées, ou le paramètre **NoClobber** , qui empêche le module d’ajouter des commandes qui masquent ou remplacent des commandes existantes dans la session.

Pour importer des modules, utilisez l’applet de commande `Import-Module` .

Pour importer des modules dans un emplacement PSModulePath de la session active, utilisez le format de commande suivant.

```powershell
Import-Module <module-name>
```

Par exemple, la commande suivante importe le module BitsTransfer dans la session active.

```powershell
Import-Module BitsTransfer
```

Pour importer un module qui ne figure pas dans un emplacement de module par défaut, utilisez le chemin d'accès complet au dossier du module dans la commande.

Par exemple, pour ajouter le module TestCmdlets dans le `C:\ps-test` répertoire à votre session, tapez :

```powershell
Import-Module C:\ps-test\TestCmdlets
```

Pour importer un fichier de module qui ne figure pas dans un dossier de module, utilisez le chemin d'accès complet au fichier du module dans la commande.

Par exemple, pour ajouter le module TestCmdlets.dll dans le `C:\ps-test` répertoire à votre session, tapez :

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

Pour plus d’informations sur l’ajout de modules à votre session, consultez [import-module](xref:Microsoft.PowerShell.Core.Import-Module).

## <a name="how-to-import-a-module-into-every-session"></a>Comment importer un module dans chaque session

La `Import-Module` commande importe les modules dans votre session PowerShell actuelle. Pour importer un module dans chaque session PowerShell que vous démarrez, ajoutez la `Import-Module` commande à votre profil PowerShell.

Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).

## <a name="how-to-remove-a-module"></a>Comment supprimer un module

Quand vous supprimez un module, les commandes ajoutées par le module sont supprimées de la session.

Pour supprimer un module de votre session, utilisez le format de commande suivant.

```powershell
Remove-Module <module-name>
```

Par exemple, la commande suivante supprime le module BitsTransfer de la session active.

```powershell
Remove-Module BitsTransfer
```

Le fait de supprimer un module annule l'opération d'importation d'un module. Toutefois, le module supprimé n'est pas désinstallé. Pour plus d’informations, consultez [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a>Emplacements des ressources de module et DSC, et PSModulePath

La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources.

Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :

- Emplacements à l’ensemble du système : `$PSHOME\Modules`

  Ces dossiers contiennent des modules fournis avec Windows et PowerShell.

  Les ressources DSC incluses avec PowerShell sont stockées dans le `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` dossier.

- Modules spécifiques à l’utilisateur : il s’agit de modules installés par l’utilisateur dans l’étendue de l’utilisateur. `Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs. Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).

  L’emplacement **CurrentUser** spécifique à l’utilisateur sur Windows est le `PowerShell\Modules` dossier situé à l’emplacement **documents** dans votre profil utilisateur. Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non. Microsoft OneDrive peut également modifier l’emplacement de votre dossier **documents** .

  Par défaut, sur Windows 10, cet emplacement est `$HOME\Documents\PowerShell\Modules` . Sur Linux ou Mac, l’emplacement **CurrentUser** est `$HOME/.local/share/powershell/Modules` .

  > [!NOTE]
  > Vous pouvez vérifier l’emplacement de votre dossier **documents** à l’aide de la commande suivante : `[Environment]::GetFolderPath('MyDocuments')` .

- L’emplacement de **ALLUSERS** est `$env:PROGRAMFILES\PowerShell\Modules` sur Windows. Sur Linux ou Mac, les modules sont stockés à l’adresse `/usr/local/share/powershell/Modules` .

> [!NOTE]
> Pour ajouter ou modifier des fichiers dans le `$env:Windir\System32` répertoire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

Vous pouvez modifier les emplacements par défaut des modules sur votre système en modifiant la valeur de la variable d’environnement **PSModulePath** , `$Env:PSModulePath` . La variable d’environnement **PSModulePath** est modélisée sur la variable d’environnement PATH et a le même format.

Pour afficher les emplacements par défaut des modules, tapez :

```powershell
$Env:PSModulePath
```

Pour ajouter un emplacement de module par défaut, utilisez le format de commande suivant.

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

Le point-virgule ( `;` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.

Par exemple, pour ajouter le `C:\ps-test\Modules` répertoire, tapez :

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

Pour ajouter un emplacement de module par défaut sur Linux ou MacOS, utilisez le format de commande suivant :

```powershell
$Env:PSModulePath += ":<path>"
```

Par exemple, pour ajouter le `/usr/local/Fabrikam/Modules` répertoire à la valeur de la variable d’environnement **PSModulePath** , tapez :

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

Sur Linux ou MacOS, le signe deux-points ( `:` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.

Lorsque vous ajoutez un chemin d’accès à **PSModulePath**, `Get-Module` les `Import-Module` commandes incluent des modules dans ce chemin d’accès.

La valeur que vous définissez affecte uniquement la session active. Pour rendre le changement persistant, ajoutez la commande à votre profil PowerShell ou utilisez l’option système du panneau de configuration pour modifier la valeur de la variable d’environnement **PSModulePath** dans le registre.

En outre, pour rendre le changement persistant, vous pouvez également utiliser la méthode **SetEnvironmentVariable ne contient** de la classe **System. Environment** pour ajouter un chemin d’accès à la variable d’environnement **PSModulePath** .

Pour plus d’informations sur la variable **PSModulePath** , consultez [about_Environment_Variables](about_Environment_Variables.md).

## <a name="modules-and-name-conflicts"></a>Modules et conflits de noms

Des conflits de noms se produisent quand plusieurs commandes portent le même nom dans la session. Quand vous importez un module, un conflit survient si les noms des commandes de ce module sont identiques à ceux de commandes ou d'éléments présents dans la session.

Les conflits de noms peuvent entraîner le masquage ou le remplacement de commandes.

### <a name="hidden"></a>Hidden

Une commande est masquée si elle ne s'exécute pas quand vous tapez son nom. Vous pouvez toutefois l'exécuter en utilisant une autre méthode, par exemple en qualifiant le nom de la commande avec le nom du module ou du composant logiciel enfichable d'où elle provient.

### <a name="replaced"></a>Remplacé

Une commande est remplacée quand vous ne pouvez pas l'exécuter parce qu'elle a été remplacée par une commande du même nom. Même quand vous supprimez le module à l'origine du conflit, vous ne pouvez pas exécuter une commande remplacée, à moins de redémarrer la session.

`Import-Module` peut ajouter des commandes qui masquent et remplacent des commandes dans la session active. Par ailleurs, les commandes dans votre session peuvent masquer les commandes ajoutées par le module.

Pour détecter les conflits de noms, utilisez le paramètre **All** de l’applet de commande `Get-Command` . À compter de PowerShell 3,0, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande. Le paramètre **All** obtient toutes les commandes portant le nom spécifique dans la session.

Pour éviter les conflits de noms, utilisez les paramètres **NoClobber** ou **prefix** de l’applet de commande `Import-Module` . Le paramètre **prefix** ajoute un préfixe aux noms des commandes importées afin qu’elles soient uniques dans la session. Le paramètre **NoClobber** n’importe aucune commande susceptible de masquer ou de remplacer des commandes existantes dans la session.

Vous pouvez également utiliser les paramètres **alias**, **cmdlet**, **Function** et **variable** de `Import-Module` pour sélectionner uniquement les commandes que vous souhaitez importer, et vous pouvez exclure les commandes qui provoquent des conflits de noms dans votre session.

Les auteurs de modules peuvent éviter les conflits de noms à l’aide de la propriété **DefaultCommandPrefix** du manifeste de module pour ajouter un préfixe par défaut à tous les noms de commandes.
La valeur du paramètre **prefix** est prioritaire sur la valeur de **DefaultCommandPrefix**.

Même si une commande est masquée, vous pouvez l'exécuter en qualifiant le nom de la commande avec le nom du module ou du composant logiciel enfichable d'où elle provient.

Les règles de priorité des commandes PowerShell déterminent la commande qui est exécutée lorsque la session comprend des commandes portant le même nom.

Par exemple, lorsqu’une session comprend une fonction et une applet de commande portant le même nom, PowerShell exécute la fonction par défaut. Quand la session inclut des commandes du même type avec le même nom, par exemple deux applets de commande avec le même nom, la commande la plus récemment ajoutée est exécutée par défaut.

Pour plus d’informations, y compris une explication des règles de précédence et des instructions pour l’exécution de commandes masquées, consultez [about_Command_Precedence](about_Command_Precedence.md).

## <a name="modules-and-snap-ins"></a>Modules et composants logiciels enfichables

Vous pouvez ajouter des commandes à votre session à partir de modules et de composants logiciels enfichables. Les modules peuvent ajouter tous les types de commandes, y compris les applets de commande, les fournisseurs, les fonctions et les éléments, tels que les variables, les alias et les lecteurs PowerShell. Les composants logiciels enfichables peuvent uniquement ajouter des applets de commande et des fournisseurs.

Avant de supprimer un module ou un composant logiciel enfichable de votre session, utilisez les commandes suivantes pour déterminer les commandes qui seront supprimées.

Pour rechercher la source d’une applet de commande dans votre session, utilisez le format de commande suivant :

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

Par exemple, pour trouver la source de l' `Get-Date` applet de commande, tapez :

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a>Avertissements et erreurs liés au module

Les commandes exportées par un module doivent respecter les règles d’affectation des noms de commande PowerShell. Si le module que vous importez exporte des applets de commande ou des fonctions dont les noms comportent des verbes non approuvés, l' `Import-Module` applet de commande affiche le message d’avertissement suivant.

> AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables. Utilisez le paramètre Verbose pour obtenir plus d'informations ou tapez Get-Verb pour afficher la liste des verbes approuvés.

Ce message n'est qu'un avertissement. Le module entier est toujours importé, y compris les commandes non conformes. Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.

Pour supprimer le message d’avertissement, utilisez le paramètre **DisableNameChecking** de l’applet de commande `Import-Module` .

## <a name="built-in-modules-and-snap-ins"></a>Modules intégrés et composants logiciels enfichables

Dans PowerShell 2,0 et dans les anciens programmes hôtes de PowerShell 3,0 et versions ultérieures, les commandes de base qui sont installées avec PowerShell sont empaquetées dans des composants logiciels enfichables qui sont ajoutés automatiquement à chaque session PowerShell.

À compter de PowerShell 3,0, pour les programmes hôtes qui implémentent l' `InitialSessionState.CreateDefault2` API d’état de session initiale, le composant logiciel enfichable Microsoft. PowerShell. Core est ajouté à chaque session par défaut. Les modules sont chargés automatiquement lors de la première utilisation.

> [!NOTE]
> Les sessions à distance, y compris les sessions démarrées à l’aide de l' `New-PSSession` applet de commande, sont des sessions de style plus ancienne dans lesquelles les commandes intégrées sont empaquetées dans des composants logiciels enfichables.

Les modules (ou composants logiciels enfichables) suivants sont installés avec PowerShell.

- CimCmdlets
- Microsoft.PowerShell.Archive
- Microsoft.PowerShell.Core
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management
- PackageManagement
- PowerShellGet
- PSDesiredStateConfiguration
- PSDiagnostics
- PSReadline

## <a name="logging-module-events"></a>Journalisation des événements du module

À compter de PowerShell 3,0, vous pouvez enregistrer les événements d’exécution des applets de commande et des fonctions dans les modules et les composants logiciels enfichables PowerShell en affectant à la propriété **LogPipelineExecutionDetails** des modules et des composants logiciels enfichables `$True` .
Vous pouvez également utiliser un paramètre stratégie de groupe, activer la journalisation des modules, pour activer la journalisation des modules dans toutes les sessions PowerShell. Pour plus d’informations, consultez les articles sur la journalisation et la stratégie de groupe.

## <a name="see-also"></a>Voir aussi

[about_Logging_Windows](about_Logging_Windows.md)

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Command_Precedence](about_Command_Precedence.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Module d’importation](xref:Microsoft.PowerShell.Core.Import-Module)

[Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module)
