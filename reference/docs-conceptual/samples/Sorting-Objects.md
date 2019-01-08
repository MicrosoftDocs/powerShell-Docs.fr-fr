---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Tri d’objets
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401186"
---
# <a name="sorting-objects"></a>Tri d’objets

Vous pouvez organiser des données affichées pour faciliter leur analyse en utilisant le `Sort-Object` applet de commande. `Sort-Object` prend le nom d’une ou plusieurs propriétés à trier et retourner les données triées par les valeurs de ces propriétés.

## <a name="basic-sorting"></a>Tri de base

Prenez le problème de répertorier les sous-répertoires et fichiers dans le répertoire actif.
Si nous souhaitons trier par **LastWriteTime** puis par **nom**, nous pouvons le faire en tapant :

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

Vous pouvez également trier les objets dans l’ordre inverse en spécifiant le **décroissant** paramètre booléen.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>À l’aide de tables de hachage

Vous pouvez trier des propriétés différentes dans des ordres différents à l’aide de tables de hachage dans un tableau.
Chaque table de hachage utilise un **Expression** clé pour spécifier le nom de propriété en tant que chaîne et un **croissant** ou **décroissant** clé pour spécifier l’ordre de tri par `$true` ou `$false`.
Le **Expression** clé est obligatoire.
Le **croissant** ou **décroissant** clé est facultative.

L’exemple suivant trie les objets dans l’ordre décroissant **LastWriteTime** ordre et croissant **nom** ordre.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

Vous pouvez également définir un bloc de script la **Expression** clé.
Lorsque vous exécutez le `Sort-Object` applet de commande, le bloc de script est exécuté et le résultat est utilisé pour le tri.

L’exemple suivant trie les objets dans l’ordre décroissant à l’intervalle de temps entre **CreationTime** et **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Conseils

Vous pouvez omettre le **propriété** nom du paramètre comme suit :

```powershell
Sort-Object LastWriteTime, Name
```

En outre, vous pouvez faire référence à `Sort-Object` par son alias intégré, `sort`:

```powershell
sort LastWriteTime, Name
```

Les clés dans les tables de hachage pour le tri peuvent être abrégés comme suit :

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

Dans cet exemple, le **e** est l’acronyme **Expression**, le **d** est l’acronyme **décroissant**et le **un** l’acronyme **croissant**.

Pour améliorer la lisibilité, vous pouvez placer les tables de hachage dans une variable distincte :

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```