---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Obtention d’informations sur les commandes
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808635"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="dd854-103">Obtention d’informations sur les commandes</span><span class="sxs-lookup"><span data-stu-id="dd854-103">Getting information about commands</span></span>

<span data-ttu-id="dd854-104">La cmdlet `Get-Command` de PowerShell affiche les commandes disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="dd854-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="dd854-105">Lorsque vous exécutez la cmdlet `Get-Command`, vous obtenez une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="dd854-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="dd854-106">Cette sortie ressemble beaucoup à la sortie Help de **cmd.exe**, à savoir un résumé des commandes internes sous forme de tableau.</span><span class="sxs-lookup"><span data-stu-id="dd854-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="dd854-107">Dans l’extrait de la sortie de la commande `Get-Command` ci-dessus, chaque commande est de type Cmdlet (« applet de commande »).</span><span class="sxs-lookup"><span data-stu-id="dd854-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="dd854-108">Une cmdlet est le type de commande intrinsèque de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd854-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="dd854-109">Ce type correspond à peu près à des commandes telles que `dir` et `cd` dans **cmd.exe** ou aux commandes intégrées des interpréteurs de commandes Unix tels que bash.</span><span class="sxs-lookup"><span data-stu-id="dd854-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="dd854-110">La cmdlet `Get-Command` dispose d’un paramètre **Syntax** qui retourne la syntaxe de chaque cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd854-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="dd854-111">L’exemple suivant montre comment obtenir la syntaxe de la cmdlet `Get-Help` :</span><span class="sxs-lookup"><span data-stu-id="dd854-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="dd854-112">Affichage des types de commandes disponibles</span><span class="sxs-lookup"><span data-stu-id="dd854-112">Displaying available command by type</span></span>

<span data-ttu-id="dd854-113">La commande `Get-Command` répertorie uniquement les cmdlets dans la session active.</span><span class="sxs-lookup"><span data-stu-id="dd854-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="dd854-114">PowerShell prend en charge plusieurs autres types de commandes :</span><span class="sxs-lookup"><span data-stu-id="dd854-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="dd854-115">Alias</span><span class="sxs-lookup"><span data-stu-id="dd854-115">Aliases</span></span>
- <span data-ttu-id="dd854-116">Fonctions</span><span class="sxs-lookup"><span data-stu-id="dd854-116">Functions</span></span>
- <span data-ttu-id="dd854-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="dd854-117">Scripts</span></span>

<span data-ttu-id="dd854-118">Les fichiers externes exécutables, ou les fichiers possédant un gestionnaire de type de fichier inscrit, sont également considérés comme des commandes.</span><span class="sxs-lookup"><span data-stu-id="dd854-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="dd854-119">Pour obtenir toutes les commandes dans la session, tapez :</span><span class="sxs-lookup"><span data-stu-id="dd854-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="dd854-120">Cette liste recense les commandes externes dans votre chemin de recherche, elle peut donc contenir des milliers d'éléments.</span><span class="sxs-lookup"><span data-stu-id="dd854-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="dd854-121">Il est plus judicieux d'examiner un ensemble réduit de commandes.</span><span class="sxs-lookup"><span data-stu-id="dd854-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="dd854-122">L’astérisque (\*) est utilisé comme caractère générique dans les arguments de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd854-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="dd854-123">Le symbole \* représente un ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="dd854-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="dd854-124">Vous pouvez taper `Get-Command a*` pour rechercher toutes les commandes dont le nom commence par la lettre « a ».</span><span class="sxs-lookup"><span data-stu-id="dd854-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="dd854-125">Contrairement aux caractères génériques dans **cmd.exe**, un caractère générique peut représenter un point dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd854-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="dd854-126">Pour obtenir les commandes natives d’autres types, utilisez le paramètre **CommandType** de la cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="dd854-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="dd854-127">applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dd854-127">cmdlet.</span></span>

<span data-ttu-id="dd854-128">Pour obtenir les alias des commandes, c'est-à-dire les surnoms affectés aux commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="dd854-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="dd854-129">Pour obtenir les fonctions dans la session active, tapez :</span><span class="sxs-lookup"><span data-stu-id="dd854-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="dd854-130">Pour afficher les scripts dans le chemin de recherche de PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="dd854-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
