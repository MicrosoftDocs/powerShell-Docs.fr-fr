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
# <a name="sorting-objects"></a><span data-ttu-id="2de6c-103">Tri d’objets</span><span class="sxs-lookup"><span data-stu-id="2de6c-103">Sorting Objects</span></span>

<span data-ttu-id="2de6c-104">Vous pouvez organiser des données affichées pour faciliter leur analyse en utilisant le `Sort-Object` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2de6c-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2de6c-105">`Sort-Object` prend le nom d’une ou plusieurs propriétés à trier et retourner les données triées par les valeurs de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="2de6c-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="2de6c-106">Tri de base</span><span class="sxs-lookup"><span data-stu-id="2de6c-106">Basic sorting</span></span>

<span data-ttu-id="2de6c-107">Prenez le problème de répertorier les sous-répertoires et fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="2de6c-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="2de6c-108">Si nous souhaitons trier par **LastWriteTime** puis par **nom**, nous pouvons le faire en tapant :</span><span class="sxs-lookup"><span data-stu-id="2de6c-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="2de6c-109">Vous pouvez également trier les objets dans l’ordre inverse en spécifiant le **décroissant** paramètre booléen.</span><span class="sxs-lookup"><span data-stu-id="2de6c-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="2de6c-110">À l’aide de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="2de6c-110">Using hash tables</span></span>

<span data-ttu-id="2de6c-111">Vous pouvez trier des propriétés différentes dans des ordres différents à l’aide de tables de hachage dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="2de6c-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="2de6c-112">Chaque table de hachage utilise un **Expression** clé pour spécifier le nom de propriété en tant que chaîne et un **croissant** ou **décroissant** clé pour spécifier l’ordre de tri par `$true` ou `$false`.</span><span class="sxs-lookup"><span data-stu-id="2de6c-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="2de6c-113">Le **Expression** clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2de6c-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="2de6c-114">Le **croissant** ou **décroissant** clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="2de6c-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="2de6c-115">L’exemple suivant trie les objets dans l’ordre décroissant **LastWriteTime** ordre et croissant **nom** ordre.</span><span class="sxs-lookup"><span data-stu-id="2de6c-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="2de6c-116">Vous pouvez également définir un bloc de script la **Expression** clé.</span><span class="sxs-lookup"><span data-stu-id="2de6c-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="2de6c-117">Lorsque vous exécutez le `Sort-Object` applet de commande, le bloc de script est exécuté et le résultat est utilisé pour le tri.</span><span class="sxs-lookup"><span data-stu-id="2de6c-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="2de6c-118">L’exemple suivant trie les objets dans l’ordre décroissant à l’intervalle de temps entre **CreationTime** et **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="2de6c-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="2de6c-119">Conseils</span><span class="sxs-lookup"><span data-stu-id="2de6c-119">Tips</span></span>

<span data-ttu-id="2de6c-120">Vous pouvez omettre le **propriété** nom du paramètre comme suit :</span><span class="sxs-lookup"><span data-stu-id="2de6c-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="2de6c-121">En outre, vous pouvez faire référence à `Sort-Object` par son alias intégré, `sort`:</span><span class="sxs-lookup"><span data-stu-id="2de6c-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="2de6c-122">Les clés dans les tables de hachage pour le tri peuvent être abrégés comme suit :</span><span class="sxs-lookup"><span data-stu-id="2de6c-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="2de6c-123">Dans cet exemple, le **e** est l’acronyme **Expression**, le **d** est l’acronyme **décroissant**et le **un** l’acronyme **croissant**.</span><span class="sxs-lookup"><span data-stu-id="2de6c-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="2de6c-124">Pour améliorer la lisibilité, vous pouvez placer les tables de hachage dans une variable distincte :</span><span class="sxs-lookup"><span data-stu-id="2de6c-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```