---
description: Décrit comment accéder aux variables d’environnement Windows dans PowerShell.
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 66d2bcd76651a7231a670ee5b02b99d6edd63a72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597987"
---
# <a name="about-environment-variables"></a>À propos des variables d’environnement

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment accéder aux variables d’environnement Windows dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les variables d’environnement stockent des informations sur l’environnement du système d’exploitation. Ces informations incluent des détails tels que le chemin d’accès du système d’exploitation, le nombre de processeurs utilisés par le système d’exploitation et l’emplacement des dossiers temporaires.

Les variables d’environnement stockent les données utilisées par le système d’exploitation et d’autres programmes. Par exemple, la `WINDIR` variable d’environnement contient l’emplacement du répertoire d’installation de Windows. Les programmes peuvent interroger la valeur de cette variable pour déterminer où se trouvent les fichiers de système d’exploitation Windows.

PowerShell peut accéder aux variables d’environnement et les gérer dans toutes les plateformes de système d’exploitation prises en charge. Le fournisseur d’environnement PowerShell simplifie ce processus en facilitant l’affichage et la modification des variables d’environnement.

Contrairement aux autres types de variables dans PowerShell, les variables d’environnement sont héritées par les processus enfants, tels que les tâches en arrière-plan locales et les sessions dans lesquelles les membres du module s’exécutent. Ainsi, les variables d’environnement sont bien adaptées au stockage des valeurs nécessaires dans les processus parents et enfants.

## <a name="using-and-changing-environment-variables"></a>Utilisation et modification des variables d’environnement

Sur Windows, les variables d’environnement peuvent être définies dans trois étendues :

- Portée de l’ordinateur (ou système)
- Étendue d’utilisateur
- Portée du processus

La portée du _processus_ contient les variables d’environnement disponibles dans le processus en cours, ou la session PowerShell. Cette liste de variables est héritée du processus parent et est construite à partir des variables dans les étendues de l' _ordinateur_ et de l' _utilisateur_ . Les plateformes UNIX disposent uniquement de l’étendue du _processus_ .

Vous pouvez afficher et modifier les valeurs des variables d’environnement sans utiliser une applet de commande à l’aide d’une syntaxe de variable avec le fournisseur de l’environnement. Pour afficher la valeur d’une variable d’environnement, utilisez la syntaxe suivante :

```
$Env:<variable-name>
```

Par exemple, pour afficher la valeur de la `WINDIR` variable d’environnement, tapez la commande suivante à l’invite de commandes PowerShell :

```powershell
$Env:windir
```

Dans cette syntaxe, le signe dollar ( `$` ) indique une variable, et le nom du lecteur ( `Env:` ) indique une variable d’environnement suivie du nom de la variable ( `windir` ).

Lorsque vous modifiez des variables d’environnement dans PowerShell, la modification affecte uniquement la session active. Ce comportement ressemble au comportement de la `Set` commande dans l’interface de commande Windows et `Setenv` à la commande dans les environnements UNIX. Pour modifier des valeurs dans les portées de l’ordinateur ou de l’utilisateur, vous devez utiliser les méthodes de la classe **System. Environment** .

Pour apporter des modifications aux variables de l’étendue de l’ordinateur, doit également avoir l’autorisation. Si vous tentez de modifier une valeur sans autorisation suffisante, la commande échoue et PowerShell affiche une erreur.

Vous pouvez modifier les valeurs des variables sans utiliser une applet de commande à l’aide de la syntaxe suivante :

```powershell
$Env:<variable-name> = "<new-value>"
```

Par exemple, pour ajouter `;c:\temp` à la valeur de la `Path` variable d’environnement, utilisez la syntaxe suivante :

```powershell
$Env:Path += ";c:\temp"
```

Sur Linux ou MacOS, le signe deux-points ( `:` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.

```powershell
$Env:PATH += ":/usr/local/temp"
```

Vous pouvez également utiliser les applets de commande Item, telles que `Set-Item` , `Remove-Item` et `Copy-Item` pour modifier les valeurs des variables d’environnement. Par exemple, pour utiliser l' `Set-Item` applet de commande pour ajouter `;c:\temp` à la valeur de la `Path` variable d’environnement, utilisez la syntaxe suivante :

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

Dans cette commande, la valeur est placée entre parenthèses afin qu’elle soit interprétée comme une unité.

## <a name="environment-variables-that-store-preferences"></a>Variables d’environnement qui stockent des préférences

Les fonctionnalités PowerShell peuvent utiliser des variables d’environnement pour stocker les préférences de l’utilisateur.
Ces variables fonctionnent comme des variables de préférence, mais elles sont héritées par les sessions enfants des sessions dans lesquelles elles sont créées. Pour plus d’informations sur les variables de préférence, consultez [about_Preference_Variables](about_Preference_Variables.md).

Les variables d’environnement qui stockent les préférences sont les suivantes :

- PSExecutionPolicyPreference

  Stocke la stratégie d’exécution définie pour la session active. Cette variable d’environnement existe uniquement lorsque vous définissez une stratégie d’exécution pour une seule session.
  Vous pouvez le faire de deux manières différentes.

  - Démarrez une session à partir de la ligne de commande à l’aide du paramètre **ExecutionPolicy** pour définir la stratégie d’exécution de la session.

  - Utilisez l'applet de commande `Set-ExecutionPolicy`. Utilisez le paramètre scope avec la valeur « Process ».

    Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).

- PSModuleAnalysisCachePath

  PowerShell vous permet de contrôler le fichier utilisé pour mettre en cache les données relatives aux modules et à leurs applets de commande. Le cache est lu au démarrage lors de la recherche d’une commande et est écrit sur un thread d’arrière-plan quelque temps après l’importation d’un module.

  L’emplacement par défaut du cache est le suivant :

  - Windows PowerShell 5.1 : `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`
  - PowerShell 6,0 et versions ultérieures : `$env:LOCALAPPDATA\Microsoft\PowerShell`
  - Valeur non-Windows par défaut : `~/.cache/powershell`

  Le nom de fichier par défaut du cache est `ModuleAnalysisCache` . Lorsque plusieurs instances de PowerShell sont installées, le nom de fichier inclut un suffixe hexadécimal afin qu’il existe un nom de fichier unique par installation.

  > [!NOTE]
  > Si la découverte de commande ne fonctionne pas correctement, par exemple IntelliSense affiche des commandes qui n’existent pas, vous pouvez supprimer le fichier cache. Le cache est recréé la prochaine fois que vous démarrez PowerShell.

  Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement avant de Démarrer PowerShell. Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants. La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.

  Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  Cela définit le chemin d’accès à l’appareil **nul** . PowerShell ne peut pas écrire dans le chemin d’accès, mais aucune erreur n’est retournée. Vous pouvez voir les erreurs signalées à l’aide d’un suivi :

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- PSDisableModuleAnalysisCacheCleanup

  Lors de l’écriture du cache d’analyse de module, PowerShell recherche les modules qui n’existent plus afin d’éviter un cache trop volumineux. Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant cette valeur de variable d’environnement sur `1` .

  La définition de cette variable d’environnement prend effet immédiatement dans le processus actuel.

- PSModulePath

  La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources.

  Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :

  - Emplacements à l’ensemble du système : ces dossiers contiennent des modules fournis avec PowerShell. Les modules sont stockés à l' `$PSHOME\Modules` emplacement. Il s’agit également de l’emplacement où sont installés les modules de gestion Windows.

  - Modules installés par l’utilisateur : il s’agit de modules installés par l’utilisateur.
    `Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs. Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).

    - Sur Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME\Documents\PowerShell\Modules` dossier. L’emplacement de l’étendue **ALLUSERS** est `$env:ProgramFiles\PowerShell\Modules` .
    - Sur les systèmes non-Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME/.local/share/powershell/Modules` dossier. L’emplacement de l’étendue **ALLUSERS** est `/usr/local/share/powershell/Modules` .

  En outre, les programmes d’installation qui installent des modules dans d’autres répertoires, tels que le répertoire Program Files, peuvent ajouter leurs emplacements à la valeur de `$env:PSModulePath` .

  Pour plus d’informations, consultez [about_PSModulePath](about_PSModulePath.md).

## <a name="managing-environment-variables"></a>Gestion des variables d’environnement

PowerShell offre plusieurs méthodes différentes pour la gestion des variables d’environnement.

- Lecteur du fournisseur de l’environnement
- Applets de commande Item
- Classe .NET **System. Environment**
- Sur Windows, le panneau de configuration système

### <a name="using-the-environment-provider"></a>Utilisation du fournisseur d’environnement

Chaque variable d’environnement est représentée par une instance de la classe **System. Collections. DictionaryEntry** . Dans chaque objet **DictionaryEntry** , le nom de la variable d’environnement est la clé du dictionnaire. La valeur de la variable est la valeur du dictionnaire.

Pour afficher les propriétés et les méthodes de l’objet qui représente une variable d’environnement dans PowerShell, utilisez l’applet de commande `Get-Member` . Par exemple, pour afficher les méthodes et les propriétés de tous les objets du `Env:` lecteur, tapez :

```powershell
Get-Item -Path Env:* | Get-Member
```

Le fournisseur d’environnement PowerShell vous permet d’accéder aux variables d’environnement dans un lecteur PowerShell (le `Env:` lecteur). Ce lecteur ressemble plus à un lecteur du système de fichiers. Pour accéder au `Env:` lecteur, tapez :

```powershell
Set-Location Env:
```

Utilisez les applets de commande content pour récupérer ou définir les valeurs d’une variable d’environnement.

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

Vous pouvez afficher les variables d’environnement dans le `Env:` lecteur à partir de n’importe quel autre lecteur PowerShell, et vous pouvez accéder au `Env:` lecteur pour afficher et modifier les variables d’environnement.

### <a name="using-item-cmdlets"></a>Utilisation des applets de commande Item

Lorsque vous faites référence à une variable d’environnement, tapez le `Env:` nom du lecteur, suivi du nom de la variable. Par exemple, pour afficher la valeur de la `COMPUTERNAME` variable d’environnement, tapez :

```powershell
Get-ChildItem Env:Computername
```

Pour afficher les valeurs de toutes les variables d’environnement, tapez :

```powershell
Get-ChildItem Env:
```

Étant donné que les variables d’environnement n’ont pas d’éléments enfants, la sortie de `Get-Item` et `Get-ChildItem` est la même.

Par défaut, PowerShell affiche les variables d’environnement dans l’ordre dans lequel elles les récupère. Pour trier la liste des variables d’environnement par nom de variable, dirigez la sortie d’une `Get-ChildItem` commande vers l’applet de commande `Sort-Object` . Par exemple, à partir de n’importe quel lecteur PowerShell, tapez :

```powershell
Get-ChildItem Env: | Sort Name
```

Vous pouvez également accéder au lecteur à l' `Env:` aide de l’applet de commande `Set-Location` :

```powershell
Set-Location Env:
```

Lorsque vous êtes dans le `Env:` lecteur, vous pouvez omettre le `Env:` nom du lecteur dans le chemin d’accès. Par exemple, pour afficher toutes les variables d’environnement, tapez :

```powershell
PS Env:\> Get-ChildItem
```

Pour afficher la valeur de la `COMPUTERNAME` variable à partir du `Env:` lecteur, tapez :

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a>Enregistrement des modifications apportées aux variables d’environnement

Pour apporter une modification permanente à une variable d’environnement sur Windows, utilisez le panneau de configuration système. Sélectionnez **paramètres système avancés**. Sous l’onglet **avancé** , cliquez sur **variable d’environnement...**. Vous pouvez ajouter ou modifier des variables d’environnement existantes dans les étendues **utilisateur** et **système** (ordinateur). Windows écrit ces valeurs dans le registre afin qu’elles soient conservées entre les sessions et les redémarrages du système.

Vous pouvez également ajouter ou modifier des variables d’environnement dans votre profil PowerShell. Cette méthode fonctionne pour n’importe quelle version de PowerShell sur n’importe quelle plateforme prise en charge.

### <a name="using-systemenvironment-methods"></a>Utilisation des méthodes System. Environment

La classe **System. Environment** fournit des méthodes **GetEnvironmentVariable** et **SetEnvironmentVariable ne contient** qui vous permettent de spécifier la portée de la variable.

L’exemple suivant utilise la méthode **GetEnvironmentVariable** pour récupérer le paramètre de l’ordinateur de `PSModulePath` et la méthode **SetEnvironmentVariable ne contient** pour ajouter le `C:\Program Files\Fabrikam\Modules` chemin d’accès à la valeur.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

Pour plus d’informations sur les méthodes de la classe **System. Environment** , consultez [méthodes d’environnement](/dotnet/api/system.environment).

## <a name="see-also"></a>VOIR AUSSI

- [Environnement (fournisseur)](../About/about_Environment_Provider.md)
- [about_Modules](about_Modules.md)

