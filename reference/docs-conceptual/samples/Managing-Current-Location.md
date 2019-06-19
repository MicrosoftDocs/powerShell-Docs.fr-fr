---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion de l'emplacement actuel
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030203"
---
# <a name="managing-current-location"></a>Gestion de l'emplacement actuel

Quand vous parcourez des systèmes de dossiers dans l'Explorateur de fichiers, vous disposez généralement d'un emplacement de travail spécifique, à savoir le dossier actuellement ouvert. Pour manipuler les éléments contenus dans le dossier actif, il vous suffit de cliquer dessus. Dans les interfaces de ligne de commande telles que Cmd.exe, quand vous vous trouvez dans le même dossier qu'un fichier particulier, vous pouvez accéder à ce fichier en spécifiant un nom relativement court, ce qui vous évite de préciser le chemin d'accès complet au fichier. Le répertoire actif est désigné sous le nom de « répertoire de travail ».

Windows PowerShell utilise le substantif **Location** pour faire référence au répertoire de travail, et implémente une famille d’applets de commande pour vous permettre d’examiner et de manipuler votre emplacement.

## <a name="getting-your-current-location-get-location"></a>Obtention de votre emplacement actuel (Get-Location)

Pour déterminer le chemin d’accès à l’emplacement de votre répertoire actif, entrez la commande **Get-Location** :

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> L’applet de commande Get-Location est similaire à la commande **pwd** dans l’interpréteur de commandes BASH. L’applet de commande Set-Location est similaire à la commande **cd** dans Cmd.exe.

## <a name="setting-your-current-location-set-location"></a>Définition de votre emplacement actuel (Set-Location)

La commande **Get-Location** s’utilise avec la commande **Set-Location**. La commande **Set-Location** permet de spécifier l’emplacement de votre répertoire actif.

```powershell
Set-Location -Path C:\Windows
```

Une fois la commande entrée, notez qu'aucun commentaire concernant l'impact de la commande n'est affiché. La plupart des commandes Windows PowerShell qui exécutent une action ne génèrent que peu de commentaires, voire aucun, car la sortie n'est pas toujours utile. Pour vérifier qu’un changement de répertoire a bien eu lieu après l’exécution de la commande **Set-Location**, incluez le paramètre **-PassThru** dans la commande **Set-Location** :

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Vous pouvez utiliser le paramètre **-PassThru** avec de nombreuses commandes Set dans Windows PowerShell pour retourner des informations sur le résultat quand aucune sortie n’est générée par défaut.

Pour spécifier des chemins d'accès par rapport à votre emplacement actuel, procédez de la même façon que dans la plupart des interpréteurs de commandes UNIX et Windows. Dans la notation standard des chemins d’accès relatifs, un point ( **.** ) représente votre dossier actif, tandis qu’un point double ( **..** ) représente le répertoire parent de votre emplacement actuel.

Par exemple, si vous vous trouvez dans le dossier **C:\\Windows**, un point ( **.** ) représente **C:\\Windows** et un point double ( **..** ) représente **C:** . Pour passer de votre emplacement actuel à la racine du lecteur C:, tapez :

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Vous pouvez employer la même technique sur les lecteurs Windows PowerShell qui ne sont pas des lecteurs du système de fichiers, comme **HKLM:** . Pour sélectionner l’emplacement de la clé HKLM\\Software dans le Registre, tapez ce qui suit :

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Vous pouvez ensuite passer au répertoire parent, c'est-à-dire à la racine du lecteur Windows PowerShell HKLM:, à l'aide d'un chemin d'accès relatif :

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Vous pouvez taper Set-Location ou utiliser l'un des alias Windows PowerShell intégrés pour Set-Location (cd, chdir, sl). Par exemple :

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Enregistrement et rappel des emplacements récents (Push-Location et Pop-Location)

Quand vous passez d'un emplacement à un autre, il est utile de faire le suivi des emplacements visités et d'être en mesure de retourner à l'emplacement précédent. L’applet de commande **Push-Location** dans Windows PowerShell crée un historique chronologique (ou « pile ») des chemins d’accès aux répertoires visités. Pour revenir en arrière dans l’historique des chemins d’accès aux répertoires, utilisez l’applet de commande complémentaire, **Pop-Location**.

Par exemple, Windows PowerShell démarre généralement dans le répertoire de base de l'utilisateur.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Le terme de pile (*stack*) a une signification particulière dans de nombreux environnements de programmation, y compris dans .NET Framework. Comme dans une pile d'objets, le dernier objet que vous placez en haut de la pile est le premier que vous pouvez ôter de la pile. Quand vous ajoutez un élément à une pile, vous le « poussez » sur la pile (« push » en anglais). Quand vous ôtez un élément de la pile, celui-ci est « extrait » de la pile (« pop » en anglais).

Pour ajouter l'emplacement actuel à la pile, puis passer au dossier Local Settings, tapez :

```powershell
Push-Location -Path "Local Settings"
```

Ensuite, pour ajouter l'emplacement Local Settings à la pile et passer au dossier Temp, tapez :

```powershell
Push-Location -Path Temp
```

Pour vérifier que le changement de répertoire a bien eu lieu, entrez la commande **Get-Location** :

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Pour revenir au dernier répertoire visité, entrez la commande **Pop-Location**. Ensuite, pour vérifier que le changement a bien eu lieu, entrez la commande **Get-Location** :

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Comme avec l’applet de commande **Set-Location**, lorsque vous entrez l’applet de commande **Pop-Location**, vous pouvez inclure le paramètre **-PassThru** pour afficher le répertoire entré :

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Vous pouvez également utiliser les applets de commande Location avec des chemins d'accès réseau. Si vous disposez d'un serveur nommé FS01 avec un partage nommé Public, vous pouvez changer votre emplacement en tapant

```powershell
Set-Location \\FS01\Public
```

ou

```powershell
Push-Location \\FS01\Public
```

Vous pouvez utiliser les commandes **Push-Location** et **Set-Location** pour modifier l’emplacement en le définissant sur tout lecteur disponible. Par exemple, si vous possédez un lecteur de CD-ROM local associé à la lettre de lecteur D qui contient un CD de données, vous pouvez passer à l’emplacement du lecteur de CD en entrant la commande **Set-Location D:** .

Si le lecteur est vide, le message d'erreur suivant s'affiche :

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Quand vous utilisez une interface de ligne de commande, il n'est pas pratique de recourir à l'Explorateur de fichiers pour examiner les lecteurs physiques disponibles. En outre, l'Explorateur de fichiers n'affiche pas tous les lecteurs Windows PowerShell. Windows PowerShell fournit un ensemble de commandes permettant de manipuler les lecteurs Windows PowerShell. Celles-ci seront traitées dans une autre section.
