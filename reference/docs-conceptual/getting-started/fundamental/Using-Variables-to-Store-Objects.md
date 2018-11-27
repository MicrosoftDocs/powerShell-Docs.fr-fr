---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Utilisation de variables pour stocker des objets
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320956"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="ad058-103">Utilisation de variables pour stocker des objets</span><span class="sxs-lookup"><span data-stu-id="ad058-103">Using variables to store objects</span></span>

<span data-ttu-id="ad058-104">PowerShell fonctionne avec des objets.</span><span class="sxs-lookup"><span data-stu-id="ad058-104">PowerShell works with objects.</span></span> <span data-ttu-id="ad058-105">PowerShell vous permet de créer des objets nommés reconnus comme des variables.</span><span class="sxs-lookup"><span data-stu-id="ad058-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="ad058-106">Les noms de variables peuvent inclure le caractère de soulignement et des caractères alphanumériques.</span><span class="sxs-lookup"><span data-stu-id="ad058-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="ad058-107">Lorsqu’elle est utilisée dans PowerShell, une variable est toujours spécifiée à l’aide du caractère \$ suivi par le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="ad058-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="ad058-108">Création d’une variable</span><span class="sxs-lookup"><span data-stu-id="ad058-108">Creating a variable</span></span>

<span data-ttu-id="ad058-109">Vous pouvez créer une variable en tapant un nom de variable valide :</span><span class="sxs-lookup"><span data-stu-id="ad058-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="ad058-110">Cet exemple ne retourne aucun résultat, car `$loc` n’a pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="ad058-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="ad058-111">Vous pouvez créer une variable et lui attribuer une valeur au cours de la même étape.</span><span class="sxs-lookup"><span data-stu-id="ad058-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="ad058-112">PowerShell ne crée la variable que si elle n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="ad058-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="ad058-113">Sinon, il attribue la valeur spécifiée à la variable existante.</span><span class="sxs-lookup"><span data-stu-id="ad058-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="ad058-114">L’exemple suivant stocke l’emplacement actuel dans la variable `$loc` :</span><span class="sxs-lookup"><span data-stu-id="ad058-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="ad058-115">PowerShell n’affiche aucune sortie lorsque vous tapez cette commande.</span><span class="sxs-lookup"><span data-stu-id="ad058-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="ad058-116">PowerShell envoie la sortie de « Get-Location » à `$loc`.</span><span class="sxs-lookup"><span data-stu-id="ad058-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="ad058-117">Dans PowerShell, les données qui ne sont pas attribuées ou redirigées sont envoyées à l’écran.</span><span class="sxs-lookup"><span data-stu-id="ad058-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="ad058-118">Tapez `$loc` pour afficher votre emplacement actuel :</span><span class="sxs-lookup"><span data-stu-id="ad058-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="ad058-119">Vous pouvez utiliser `Get-Member` pour afficher des informations sur le contenu de variables.</span><span class="sxs-lookup"><span data-stu-id="ad058-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="ad058-120">`Get-Member` indique que `$loc` est un objet **PathInfo**, tout comme la sortie de `Get-Location` :</span><span class="sxs-lookup"><span data-stu-id="ad058-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="ad058-121">Manipulation de variables</span><span class="sxs-lookup"><span data-stu-id="ad058-121">Manipulating variables</span></span>

<span data-ttu-id="ad058-122">PowerShell fournit plusieurs commandes pour manipuler des variables.</span><span class="sxs-lookup"><span data-stu-id="ad058-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="ad058-123">Vous pouvez afficher leur liste complète sous forme lisible en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ad058-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="ad058-124">PowerShell crée également plusieurs variables définies par le système.</span><span class="sxs-lookup"><span data-stu-id="ad058-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="ad058-125">Vous pouvez utiliser la cmdlet `Remove-Variable` pour effacer toutes les variables non contrôlées par PowerShell de la session actuelle.</span><span class="sxs-lookup"><span data-stu-id="ad058-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="ad058-126">Pour effacer toutes les variables, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ad058-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="ad058-127">Après avoir exécuté la commande précédente, la cmdlet `Get-Variable` affiche les variables système PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad058-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="ad058-128">PowerShell crée également un lecteur de variable.</span><span class="sxs-lookup"><span data-stu-id="ad058-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="ad058-129">Pour afficher toutes les variables PowerShell à l’aide du lecteur de variable, utilisez l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ad058-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="ad058-130">Utilisation de variables cmd.exe</span><span class="sxs-lookup"><span data-stu-id="ad058-130">Using cmd.exe variables</span></span>

<span data-ttu-id="ad058-131">PowerShell peut utiliser les mêmes variables d’environnement que celles disponibles pour n’importe quel processus Windows, notamment **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="ad058-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="ad058-132">Ces variables sont exposées via un lecteur nommé `env:`.</span><span class="sxs-lookup"><span data-stu-id="ad058-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="ad058-133">Vous pouvez consulter ces variables en tapant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ad058-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="ad058-134">Les cmdlets `*-Variable` standard ne sont pas conçues pour fonctionner avec les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="ad058-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="ad058-135">Les variables d’environnement sont accessibles à l’aide du préfixe du lecteur `env:`.</span><span class="sxs-lookup"><span data-stu-id="ad058-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="ad058-136">Par exemple, la variable **%SystemRoot%** dans **cmd.exe** contient le nom du répertoire racine du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ad058-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="ad058-137">Dans PowerShell, vous utilisez `$env:SystemRoot` pour accéder à la même valeur.</span><span class="sxs-lookup"><span data-stu-id="ad058-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="ad058-138">Vous pouvez également créer et modifier des variables d’environnement à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad058-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="ad058-139">Les variables d’environnement dans PowerShell suivent les mêmes règles que les variables d’environnement utilisées ailleurs dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ad058-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="ad058-140">L’exemple suivant crée une variable d’environnement :</span><span class="sxs-lookup"><span data-stu-id="ad058-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="ad058-141">Bien que cela ne soit pas obligatoire, il est courant que les noms des variables d’environnement utilisent uniquement des lettres majuscules.</span><span class="sxs-lookup"><span data-stu-id="ad058-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>
