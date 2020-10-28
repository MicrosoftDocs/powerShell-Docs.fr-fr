---
ms.date: 07/28/2020
keywords: powershell,applet de commande
title: Utilisation des fichiers, dossiers et clés de Registre
description: Cet article explique comment gérer les tâches de manipulation des clés de Registre à l’aide de PowerShell.
ms.openlocfilehash: 6f653c1fb409a238aa05658e89261a12e96f6fe1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499975"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Utilisation des fichiers, dossiers et clés de Registre

Windows PowerShell utilise le substantif **Item** pour faire référence aux éléments figurant sur un lecteur Windows PowerShell.
En relation avec le fournisseur FileSystem de Windows PowerShell, le terme **Item** peut désigner un fichier, un dossier ou le lecteur Windows PowerShell. Nous allons examiner en détail comment répertorier et utiliser ces éléments, ces tâches étant essentielles dans la plupart des environnements d'administration.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Énumération des fichiers, des dossiers et des clés de Registre (Get-ChildItem)

L’obtention d’une collection d’éléments à partir d’un emplacement particulier étant une tâche très courante, l’applet de commande `Get-ChildItem` est conçue pour retourner tous les éléments figurant dans un conteneur tel qu’un dossier.

Pour retourner tous les fichiers et dossiers contenus directement dans le dossier C:\\Windows, tapez ce qui suit :

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

La liste ressemble à celle qui s’affiche quand vous entrez la commande `dir` dans **Cmd.exe** , ou la commande `ls` dans un interpréteur de commandes UNIX.

Vous pouvez effectuer des recherches très complexes à l’aide des paramètres de l’applet de commande `Get-ChildItem`. Nous examinerons quelques scénarios dans les sections suivantes. Pour voir la syntaxe de l’applet de commande `Get-ChildItem`, tapez ce qui suit :

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Vous pouvez combiner ces paramètres pour personnaliser davantage les sorties.

### <a name="listing-all-contained-items--recurse"></a>Affichage de la liste de tous les éléments contenus (-Recurse)

Pour voir à la fois les éléments d’un dossier Windows et ceux contenus dans ses sous-dossiers, utilisez le paramètre **Recurse** de l’applet de commande `Get-ChildItem`. La liste affiche tous les éléments contenus dans le dossier Windows et ses sous-dossiers. Par exemple :

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Filtrage des éléments par nom (-Name)

Pour voir uniquement les noms des éléments, utilisez le paramètre **Name** de l’applet de commande `Get-Childitem` :

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Affichage forcé de la liste des éléments cachés (-Force)

Les éléments normalement invisibles dans l’Explorateur de fichiers ou dans Cmd.exe ne figurent pas dans la sortie d’une commande `Get-ChildItem`. Pour voir les éléments masqués, utilisez le paramètre **Force** de `Get-ChildItem`.
Par exemple :

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Ce paramètre est nommé Force, car il permet de remplacer de force le comportement habituel de la commande `Get-ChildItem`. Force est un paramètre couramment employé qui force une action dont l'exécution n'est généralement pas assurée par une applet de commande. Notez toutefois qu'il n'exécute aucune action susceptible de compromettre la sécurité du système.

### <a name="matching-item-names-with-wildcards"></a>Recherche de noms d'éléments avec des caractères génériques

La commande `Get-ChildItem` accepte les caractères génériques dans le chemin des éléments à lister.

La mise en correspondance des caractères génériques étant gérée par le moteur Windows PowerShell, toutes les applets de commande qui acceptent des caractères génériques utilisent la même notation et suivent le même comportement de mise en correspondance. Parmi les caractères génériques disponibles dans la notation Windows PowerShell, citons les suivants :

- L’astérisque (`*`) correspond à zéro ou plusieurs occurrences d’un caractère quelconque.

- Le point d’interrogation (`?`) correspond à exactement un caractère.

- Le crochet gauche (`[`) et le crochet droit (`]`) entourent un ensemble de caractères à mettre en correspondance.

Voici quelques exemples qui illustrent l'utilisation des caractères génériques.

Pour trouver tous les fichiers contenus dans le répertoire Windows avec le suffixe `.log` et exactement cinq caractères dans le nom de base, entrez la commande suivante :

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Pour rechercher tous les fichiers qui commencent par la lettre `x` dans le répertoire Windows, tapez ce qui suit :

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Pour rechercher tous les fichiers dont le nom commence par x ou z, tapez ce qui suit :

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

Pour plus d’informations sur les caractères génériques, consultez [À propos des caractères génériques](/powershell/module/microsoft.powershell.core/about/about_wildcards).

### <a name="excluding-items--exclude"></a>Exclusion d'éléments (-Exclude)

Vous pouvez exclure des éléments spécifiques à l’aide du paramètre **Exclude** de l’applet de commande `Get-ChildItem`. Vous pouvez ainsi effectuer des opérations de filtrage complexes à l'aide d'une seule instruction.

Par exemple, supposons que vous essayiez de trouver la DLL Windows Time Service dans le dossier **System32** . Tout ce dont vous vous souvenez, c’est que le nom de la DLL commence par la lettre « W » et qu’il contient le nombre « 32 ».

Une expression comme `w*32*.dll` recherchera toutes les DLL qui répondent aux critères. Toutefois, vous pouvez affiner le filtrage des fichiers pour omettre les fichiers Win32. Vous pouvez omettre ces fichiers à l’aide du paramètre **Exclude** en suivant le modèle `win*` :

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude win*

    Directory: C:\WINDOWS\System32

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           3/18/2019  9:43 PM         495616 w32time.dll
-a---           3/18/2019  9:44 PM          35328 w32topl.dll
-a---           1/24/2020  5:44 PM         401920 Wldap32.dll
-a---          10/10/2019  5:40 PM         442704 ws2_32.dll
-a---           3/18/2019  9:44 PM          66048 wsnmp32.dll
-a---           3/18/2019  9:44 PM          18944 wsock32.dll
-a---           3/18/2019  9:44 PM          64792 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Combinaison de paramètres Get-ChildItem

Vous pouvez utiliser plusieurs paramètres de l’applet de commande `Get-ChildItem` dans la même commande. Avant de combiner des paramètres, assurez-vous de bien comprendre à quoi correspondent les caractères génériques. Par exemple, la commande suivante ne retourne aucun résultat :

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Aucun résultat n'est disponible, même s'il existe deux DLL qui commencent par la lettre « z » dans le dossier Windows.

Aucun résultat n'est retourné, car nous avons spécifié le caractère générique comme faisant partie du chemin d'accès. Même si la commande est récursive, l’applet de commande `Get-ChildItem` limite les résultats aux éléments qui se trouvent dans le dossier Windows et dont le nom se termine par `.dll`.

Pour spécifier une recherche récursive des fichiers dont le nom correspond à un modèle particulier, utilisez le paramètre **Include** .

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
