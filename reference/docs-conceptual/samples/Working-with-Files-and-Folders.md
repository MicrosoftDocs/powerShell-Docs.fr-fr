---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de fichiers et dossiers
ms.openlocfilehash: 0f7cb233918b59475417ec49b611ecc25a94ebe1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030691"
---
# <a name="working-with-files-and-folders"></a>Utilisation de fichiers et dossiers

La navigation dans des lecteurs Windows PowerShell et la manipulation des éléments qu’ils contiennent sont similaires à la manipulation de fichiers et dossiers sur des lecteurs de disques physiques Windows. Cette section explique comment effectuer certaines tâches de manipulation de fichiers et dossiers à l’aide de PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Affichage de la liste de tous les fichiers et dossiers figurant dans un dossier

Vous pouvez obtenir tous les éléments figurant directement dans un dossier à l’aide de l’applet de commande **Get-ChildItem**. Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force**. Par exemple, cette commande affiche le contenu direct du lecteur C de Windows PowerShell (qui est le même que le lecteur physique C de Windows) :

```powershell
Get-ChildItem -Path C:\ -Force
```

La commande répertorie uniquement les éléments contenus directement, de manière très similaire à la commande **DIR** de Cmd.exe ou à la commande **ls** dans un interpréteur de commande UNIX. Pour afficher les éléments contenus, vous devez également spécifier le paramètre **-Recurse**. (Cela peut prendre beaucoup de temps.) Pour répertorier tout ce qui figure sur le lecteur C :

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

L’applet de commande **Get-ChildItem** peut filtrer les éléments avec ses paramètres **Path**, **Filter**, **Include** et **Exclude**, mais ceux-ci sont généralement basés uniquement sur le nom. Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de l’applet de commande **Where-Object**.

La commande suivante recherche dans le dossier Program Files tous les exécutables modifiés après le 1er octobre 2005, dont la taille n’est pas inférieure à 1 Mo ou supérieure à 10 Mo :

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Copie de fichiers et dossiers

La copie s’effectue à l’aide de l’applet de commande **Copy-Item**. La commande suivante sauvegarde C:\\boot.ini dans C:\\boot.bak :

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Si le fichier de destination existe déjà, la tentative de copie échoue. Pour remplacer une destination existante, utilisez le paramètre **Force** :

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Cette commande fonctionne même lorsque la destination est en lecture seule.

La copie de dossier fonctionne de la même manière. Cette commande copie le dossier C:\\temp\\test1 vers le nouveau dossier C:\\temp\\DeleteMe de façon récursive :

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Vous pouvez également copier une sélection d’éléments. La commande suivante copie tous les fichiers .txt contenus n’importe où dans C:\\data vers C:\\temp\\text :

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Vous pouvez toujours utiliser d’autres outils pour effectuer des copies du système de fichiers. Les objets XCOPY, ROBOCOPY et COM, tels que **Scripting.FileSystemObject**, fonctionnent tous dans Windows PowerShell. Par exemple, vous pouvez utiliser la classe Windows Script Host **Scripting.FileSystem COM** pour sauvegarder C:\\boot.ini dans C:\\boot.bak :

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Création de fichiers et dossiers

La création de nouveaux éléments fonctionne de la même manière sur tous les fournisseurs Windows PowerShell. Si un fournisseur Windows PowerShell a plus d’un type d’élément (par exemple, le fournisseur FileSystem de Windows PowerShell fait la distinction entre les répertoires et les fichiers), vous devez spécifier le type d’élément.

Cette commande crée un dossier C:\\temp\\New Folder :

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Cette commande crée un fichier vide C:\\temp\\New Folder\\file.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Suppression de tous les fichiers et dossiers figurant dans un dossier

Vous pouvez supprimer des élément contenus à l’aide de l’applet de commande **Remove-Item**, mais vous devez confirmer la suppression si les éléments contiennent autre chose. Par exemple, si vous tentez de supprimer le dossier C:\\temp\\DeleteMe contenant d’autres éléments, Windows PowerShell vous invite à confirmer la suppression :

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Si vous ne souhaitez pas être invité à confirmer la suppression de chaque élément contenu, spécifiez le paramètre **Recurse**:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mappage d’un dossier local en tant que lecteur Windows accessible

Vous pouvez également mapper un dossier local à l’aide de la commande **subst**. La commande suivante crée un lecteur local P:, dans la racine du répertoire Program Files local :

```powershell
subst p: $env:programfiles
```

Comme les lecteurs réseau, les lecteurs mappés à l’intérieur de Windows PowerShell avec la commande **subst** sont immédiatement visibles pour l’interpréteur de commandes Windows PowerShell.

## <a name="reading-a-text-file-into-an-array"></a>Lecture d’un fichier texte dans un tableau

L’un des formats de stockage courants pour les données de texte est celui d’un fichier contenant des lignes séparées traitées en tant qu’éléments de données distincts. L’applet de commande **Get-Content** permet de lire un fichier entier en une seule étape, comme illustré ici :

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

L’applet de commande **Get-Content** traite déjà les données lues à partir du fichier en tant que tableau, avec un élément par ligne de contenu du fichier. Vous pouvez vous en assurer en vérifiant la longueur (**longueur**) du contenu retourné :

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Cette commande est particulièrement utile pour obtenir des listes d’informations directement dans Windows PowerShell. Par exemple, vous pouvez stocker une liste de noms d’ordinateur ou d’adresses IP dans un fichier C:\\temp\\domainMembers.txt, avec un nom sur chaque ligne du fichier. Vous pouvez utiliser l’applet de commande **Get-Content** pour récupérer le contenu du fichier et le placer dans la variable **$Computers** :

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

La variable **$Computers** est désormais un tableau contenant un nom d’ordinateur dans chaque élément.
