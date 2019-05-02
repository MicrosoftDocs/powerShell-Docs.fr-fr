---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Tri d’objets
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086049"
---
# <a name="sorting-objects"></a>Tri d’objets

Vous pouvez organiser des données affichées pour faciliter leur analyse en utilisant l’applet de commande `Sort-Object`. L’applet de commande `Sort-Object` prend le nom d’une ou plusieurs propriétés pour trier et retourner les données triées sur les valeurs de ces propriétés.

## <a name="basic-sorting"></a>Tri de base

Prenez le problème d’affichage des sous-répertoires et fichiers du répertoire actif.
Si vous souhaitez trier sur l’état (**LastWriteTime**), puis sur le nom (**Name**), vous pouvez taper ce qui suit :

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

Vous pouvez également trier les objets dans l’ordre inverse en spécifiant le paramètre de commutateur **Descending**.

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

## <a name="using-hash-tables"></a>Utilisation des tables de hachage

Vous pouvez trier différentes propriétés selon divers ordres à l’aide de tables de hachage dans un tableau.
Chaque table de hachage utilise une clé **Expression** pour spécifier le nom de la propriété comme chaîne, ainsi qu’une clé **Ascending** ou **Descending** pour spécifier l’ordre de tri par `$true` ou `$false`.
La clé **Expression** est obligatoire.
La clé **Ascending** (Croissant) ou **Descending** (Décroissant) est facultative.

L’exemple suivant trie les objets par ordre décroissant **LastWriteTime** et par ordre croissant **Name**.

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

Vous pouvez également définir un bloc de script avec la clé **Expression**.
Lorsque vous exécutez l’applet de commande `Sort-Object`, le bloc de script est exécuté et le résultat sert pour le tri.

L’exemple suivant trie les objets par ordre décroissant en fonction de l’intervalle de temps entre **CreationTime** et **LastWriteTime**.

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

Vous pouvez omettre le nom du paramètre **Property** comme suit :

```powershell
Sort-Object LastWriteTime, Name
```

En outre, vous pouvez faire référence à `Sort-Object` en utilisant son alias intégré, `sort` :

```powershell
sort LastWriteTime, Name
```

Les clés de tri figurant dans les tables de hachage peuvent être abrégées comme suit :

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

Dans cet exemple, la lettre **e** signifie **Expression**, **d** signifie **Descending** (décroissant) et **a** signifie **Ascending** (croissant).

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