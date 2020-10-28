---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Manipulation d'éléments de manière directe
description: PowerShell fournit plusieurs applets de commande qui permettent de gérer des éléments sur des ordinateurs locaux et distants. Les éléments sont des objets exposés par les fournisseurs PowerShell tels que le système de fichiers, le registre, les certificats, etc.
ms.openlocfilehash: 20132b63a8ff4ef24b1d8346066315dbb053e59c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500315"
---
# <a name="manipulating-items-directly"></a>Manipulation d'éléments de manière directe

Dans Windows PowerShell, le terme *élément* est utilisé pour désigner ce que vous voyez dans les lecteurs Windows PowerShell, comme les fichiers et les dossiers dans les lecteurs du système de fichiers ainsi que les clés de Registre dans les lecteurs de Registre Windows PowerShell. Les applets de commande associées à ces éléments comportent le nom **Item** dans leur intitulé.

La sortie de la commande **Get-Command -Noun Item** montre qu'il existe neuf applets de commande Windows PowerShell relatives aux éléments.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a>Création d'éléments (New-Item)

Pour créer un élément dans le système de fichiers, utilisez l'applet de commande **New-Item** . Indiquez le chemin d'accès à l'élément dans le paramètre **Path** , et la valeur « File » ou « Directory » dans le paramètre **ItemType** .

Par exemple, pour créer un répertoire nommé « New.Directory » dans le répertoire C:\\Temp, tapez :

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Pour créer un fichier, affectez au paramètre **ItemType** la valeur « File ». Par exemple, pour créer un fichier nommé « file1.txt » dans le répertoire New.Directory, tapez :

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Vous pouvez utiliser la même technique pour créer une clé de Registre. En fait, une clé de Registre est plus facile à créer, car le seul type d'élément dans le Registre Windows est une clé. (Les entrées de Registre sont des *propriétés* d’élément.) Par exemple, pour créer une clé nommée « _Test » dans la sous-clé CurrentVersion, tapez :

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Quand vous tapez un chemin d'accès au Registre, veillez à inclure le signe deux-points ( **:** ) dans les noms de lecteur Windows PowerShell (HKLM: et HKCU:). Sans les deux-points, Windows PowerShell ne reconnaît pas le nom du lecteur dans le chemin d'accès.

## <a name="why-registry-values-are-not-items"></a>Pourquoi les valeurs de Registre ne sont pas des éléments

Quand vous utilisez l'applet de commande **Get-ChildItem** pour rechercher les éléments dans une clé de Registre, ni les entrées de Registre ni leurs valeurs n'apparaissent.

Par exemple, la clé de Registre **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** contient généralement plusieurs entrées de Registre qui représentent des applications qui s’exécutent au démarrage du système.

Toutefois, quand vous utilisez **Get-ChildItem** pour rechercher les éléments enfants dans la clé, la sous-clé **OptionalComponents** de la clé est la seule chose qui s'affiche :

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Bien qu'il serait pratique de traiter les entrées de Registre en tant qu'éléments, vous ne pouvez pas spécifier un chemin d'accès à une entrée de Registre d'une façon qui garantit son unicité. La notation de chemin d’accès ne fait pas la distinction entre la sous-clé de Registre nommée **Run** et l’entrée de Registre **(Default)** dans la sous-clé **Run** . Par ailleurs, si les entrées de Registre étaient des éléments, du fait que les noms des entrées de Registre peuvent contenir une barre oblique inverse ( **\\** ), vous ne pourriez pas faire la distinction entre une entrée de Registre nommée **Windows\\CurrentVersion\\Run** et la sous-clé située dans ce chemin d’accès.

## <a name="renaming-existing-items-rename-item"></a>Affectation d'un nouveau nom à des éléments existants (Rename-Item)

Pour modifier le nom d'un fichier ou d'un dossier, utilisez l'applet de commande **Rename-Item** . La commande suivante remplace le nom du fichier **file1.txt** par **fileOne.txt** .

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

L'applet de commande **Rename-Item** peut modifier le nom d'un fichier ou d'un dossier, mais elle ne peut pas déplacer un élément. La commande suivante échoue, car elle tente de déplacer le fichier du répertoire New.Directory vers le répertoire Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Déplacement d'éléments (Move-Item)

Pour déplacer un fichier ou un dossier, utilisez l'applet de commande **Move-Item** .

Par exemple, la commande suivante déplace le répertoire New.Directory du répertoire C:\\temp vers la racine du lecteur C:. Pour vérifier que l'élément a bien été déplacé, incluez le paramètre **PassThru** de l'applet de commande **Move-Item** . Sans le paramètre **Passthru** , l'applet de commande **Move-Item** n'affiche aucun résultat.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Copie d'éléments (Copy-Item)

Si vous avez déjà effectué des opérations de copie dans d'autres interpréteurs de commandes, le comportement de l'applet de commande **Copy-Item** dans Windows PowerShell peut vous sembler inhabituel. Quand vous copiez un élément d'un emplacement vers un autre, Copy-Item ne copie pas par défaut son contenu.

Par exemple, si vous copiez le répertoire **New.Directory** du lecteur C: vers le répertoire C:\\temp, la commande aboutit, mais les fichiers du répertoire New.Directory ne sont pas copiés.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Si vous affichez le contenu du dossier **C:\\temp\\New.Directory** , vous pouvez constater qu’il ne comprend aucun fichier :

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Pourquoi l'applet de commande **Copy-Item** ne copie-t-elle pas le contenu vers le nouvel emplacement ?

L'applet de commande **Copy-Item** a été conçue de manière générique, c'est-à-dire qu'elle ne sert pas simplement à copier des fichiers et des dossiers. En outre, même si vous copiez des fichiers et des dossiers, vous pouvez être amené à copier uniquement le conteneur et non les éléments qu'il contient.

Pour copier tout le contenu d'un dossier, incluez le paramètre **Recurse** de l'applet de commande **Copy-Item** dans la commande. Si vous avez déjà copié le répertoire sans son contenu, ajoutez le paramètre **Force** pour remplacer le dossier vide.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a>Suppression d'éléments (Remove-Item)

Pour supprimer des fichiers et des dossiers, utilisez l'applet de commande **Remove-Item** . À l'instar de **Remove-Item** , les applets de commande Windows PowerShell qui effectuent des modifications importantes et irréversibles affichent souvent une invite de confirmation quand vous entrez les commandes. Par exemple, si vous essayez de supprimer le dossier **New.Directory** qui contient des fichiers, vous serez invité à confirmer la commande :

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

**Yes** étant la réponse par défaut, appuyez sur la touche **Entrée** pour supprimer le dossier et ses fichiers. Pour supprimer le dossier sans confirmation, utilisez le paramètre **-Recurse** .

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Exécution d'éléments (Invoke-Item)

Windows PowerShell utilise l'applet de commande **Invoke-Item** pour effectuer une action par défaut pour un fichier ou un dossier. Cette action par défaut est déterminée par le gestionnaire d'application par défaut dans le Registre. Vous obtenez le même résultat qu'en double-cliquant sur l'élément dans l'Explorateur de fichiers.

Par exemple, imaginez que vous exécutiez la commande suivante :

```powershell
Invoke-Item C:\WINDOWS
```

Une fenêtre d’explorateur située dans C:\\Windows s’affiche comme si vous aviez double-cliqué sur le dossier C:\\Windows.

Si vous appelez le fichier **Boot.ini** sur un système antérieur à Windows Vista :

```powershell
Invoke-Item C:\boot.ini
```

Si le type de fichier .ini est associé au Bloc-notes, le fichier boot.ini s'ouvre dans le Bloc-notes.
