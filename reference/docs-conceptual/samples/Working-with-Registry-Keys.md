---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Utilisation de clés de Registre
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736843"
---
# <a name="working-with-registry-keys"></a>Utilisation de clés de Registre

Étant donné que les clés de registre sont des éléments sur des lecteurs PowerShell, leur utilisation est très similaire à l’utilisation de fichiers et dossiers. Une différence importante est que chaque élément sur un lecteur PowerShell basé sur un registre est un conteneur, tout comme un dossier sur un lecteur du système de fichiers. En revanche, les entrées de Registre et les valeurs qui leur sont associées sont des propriétés des éléments, pas des éléments distincts.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Affichage de la liste de toutes les sous-clés d’une clé de Registre

Vous pouvez afficher tous les éléments figurant directement à l’intérieur d’une clé de registre à l’aide de `Get-ChildItem`. Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force**. Par exemple, cette commande affiche les éléments figurant directement dans le lecteur PowerShell `HKCU:`, qui correspond au hive du registre `HKEY_CURRENT_USER` :

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

Il s’agit des clés de niveau supérieur visibles sous `HKEY_CURRENT_USER` dans l’Éditeur du registre (Regedit.exe).

Vous pouvez également définir ce chemin du registre en spécifiant le nom du fournisseur de registre, suivi de `::`. Le nom complet du fournisseur de registre est `Microsoft.PowerShell.Core\Registry`, mais il peut être abrégé en `Registry` uniquement. Toutes les commandes suivantes répertorient le contenu directement sous `HKCU:`.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Ces commandes répertorient uniquement les éléments contenus directement, de manière très similaire à l’utilisation de `DIR` dans **cmd.exe** ou `ls` dans un interpréteur de commandes UNIX. Pour afficher les éléments contenus, vous devez spécifier le paramètre **Recurse**. Pour répertorier toutes les clés de registre dans `HKCU:`, utilisez la commande suivante.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem` peut exécuter des fonctionnalités de filtrage complexes via ses paramètres **Chemin d'accès**, **Filtre**, **Inclure** et **Exclure**, mais ces paramètres sont généralement basés uniquement sur le nom. Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de la cmdlet `Where-Object`. La commande suivante recherche dans `HKCU:\Software` toutes les clés qui n’ont pas plus d’une sous-clé et ont aussi exactement quatre valeurs :

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Copie de clés

La copie s’effectue avec `Copy-Item`. L’exemple suivant copie la sous-clé `CurrentVersion` de `HKLM:\SOFTWARE\Microsoft\Windows\` et toutes ses propriétés dans `HKCU:\`.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

Si vous examinez cette nouvelle clé dans l’Éditeur du registre ou en utilisant `Get-ChildItem`, vous remarquerez que vous n’avez pas de copies des sous-clés contenues dans le nouvel emplacement. Pour copier tout le contenu d’un conteneur, vous devez spécifier le paramètre **Recurse**. Pour rendre la commande de copie précédente récursive, vous devez utiliser la commande suivante :

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

Vous pouvez toujours utiliser d’autres outils déjà disponibles pour effectuer des copies du système de fichiers. Les outils d’édition du registre (dont **reg.exe**, **regini.exe** et **regedit.exe**) et les objets COM qui prennent en charge l’édition du registre (par exemple, **WScript.Shell** et la classe **StdRegProv** de WM) peuvent être utilisés à partir de Windows PowerShell.

## <a name="creating-keys"></a>Création de clés

Créer des clés dans le Registre est plus simple que créer un élément dans un système de fichiers. Étant donné que toutes les clés de Registre sont des conteneurs, il est inutile spécifier le type d’élément. Vous devez simplement fournir un chemin d’accès explicite, par exemple :

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

Pour spécifier une clé, vous pouvez également utiliser un chemin d’accès basé sur un fournisseur :

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>Suppression de clés

La suppression d’éléments est essentiellement identique pour tous les fournisseurs. Les commandes suivantes suppriment des éléments en mode silencieux :

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Suppression de toutes les clés sous une clé spécifique

Vous pouvez supprimer des éléments contenus à l’aide de `Remove-Item`, mais vous devez confirmer la suppression si les éléments contiennent autre chose. Par exemple, si nous tentons de supprimer la sous-clé `HKCU:\CurrentVersion` que nous avons créée, nous voyons ceci :

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Pour supprimer des éléments contenus sans invite de confirmation, spécifiez le paramètre **Recurse** :

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Si vous vouliez supprimer tous les éléments dans `HKCU:\CurrentVersion` mais pas `HKCU:\CurrentVersion` lui-même, vous devrez plutôt utiliser :

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
