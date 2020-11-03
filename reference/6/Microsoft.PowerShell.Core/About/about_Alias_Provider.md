---
description: Alias
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Alias
ms.openlocfilehash: e5251b6e36da5e5c32d9e7c826766aa3dc38a9e0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207205"
---
# <a name="alias-provider"></a><span data-ttu-id="d869d-104">Fournisseur alias</span><span class="sxs-lookup"><span data-stu-id="d869d-104">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="d869d-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="d869d-105">Provider name</span></span>
<span data-ttu-id="d869d-106">Alias</span><span class="sxs-lookup"><span data-stu-id="d869d-106">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="d869d-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="d869d-107">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="d869d-108">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d869d-108">Capabilities</span></span>

<span data-ttu-id="d869d-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="d869d-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="d869d-110">Description courte</span><span class="sxs-lookup"><span data-stu-id="d869d-110">Short description</span></span>

<span data-ttu-id="d869d-111">Fournit l’accès aux alias PowerShell et aux valeurs qu’ils représentent.</span><span class="sxs-lookup"><span data-stu-id="d869d-111">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="d869d-112">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="d869d-112">Detailed description</span></span>

<span data-ttu-id="d869d-113">Le fournisseur d' **alias** PowerShell vous permet d’accéder, d’ajouter, de modifier, d’effacer et de supprimer des alias dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d869d-113">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="d869d-114">Un alias est un autre nom pour une applet de commande, une fonction ou un fichier exécutable, y compris des scripts.</span><span class="sxs-lookup"><span data-stu-id="d869d-114">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="d869d-115">PowerShell comprend un ensemble d’alias intégrés.</span><span class="sxs-lookup"><span data-stu-id="d869d-115">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="d869d-116">Vous pouvez ajouter vos propres alias à la session active et à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d869d-116">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="d869d-117">Le lecteur d' **alias** est un espace de noms plat qui contient uniquement les objets d’alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-117">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="d869d-118">Les alias n'ont pas d'éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="d869d-118">The aliases have no child items.</span></span>

<span data-ttu-id="d869d-119">Le fournisseur **alias** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="d869d-119">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="d869d-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="d869d-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="d869d-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="d869d-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="d869d-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="d869d-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="d869d-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="d869d-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="d869d-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="d869d-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="d869d-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="d869d-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="d869d-126">PowerShell comprend un ensemble d’applets de commande conçues pour afficher et modifier des alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-126">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="d869d-127">Lorsque vous utilisez des applets de commande d' **alias** , vous n’avez pas besoin de spécifier le `Alias:` lecteur dans le nom.</span><span class="sxs-lookup"><span data-stu-id="d869d-127">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="d869d-128">Cet article ne traite pas de l’utilisation des applets de commande d' **alias** .</span><span class="sxs-lookup"><span data-stu-id="d869d-128">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="d869d-129">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="d869d-129">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="d869d-130">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="d869d-130">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="d869d-131">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="d869d-131">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="d869d-132">New-Alias</span><span class="sxs-lookup"><span data-stu-id="d869d-132">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="d869d-133">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="d869d-133">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="d869d-134">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="d869d-134">Types exposed by this provider</span></span>

<span data-ttu-id="d869d-135">Chaque alias est une instance de la classe [System. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .</span><span class="sxs-lookup"><span data-stu-id="d869d-135">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="d869d-136">Navigation dans le lecteur d’alias</span><span class="sxs-lookup"><span data-stu-id="d869d-136">Navigating the Alias drive</span></span>

<span data-ttu-id="d869d-137">Le fournisseur **alias** expose son magasin de données dans le `Alias:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="d869d-137">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="d869d-138">Pour utiliser des alias, vous pouvez modifier votre emplacement sur le lecteur à l' `Alias:` aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d869d-138">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="d869d-139">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="d869d-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="d869d-140">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="d869d-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="d869d-141">Vous pouvez également utiliser le fournisseur alias à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d869d-141">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="d869d-142">Pour référencer un alias à partir d’un autre emplacement, utilisez le `Alias:` nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d869d-142">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="d869d-143">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="d869d-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="d869d-144">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="d869d-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="d869d-145">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="d869d-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="d869d-146">Affichage du contenu du lecteur Alias :</span><span class="sxs-lookup"><span data-stu-id="d869d-146">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="d869d-147">Cette commande obtient la liste de tous les alias lorsque l’emplacement actuel est le `Alias:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="d869d-147">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="d869d-148">Elle utilise un caractère générique `*` pour indiquer tout le contenu de l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="d869d-148">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="d869d-149">Dans le `Alias:` lecteur, un point `.` , qui représente l’emplacement actuel, et un caractère générique `*` , qui représente tous les éléments de l’emplacement actuel, ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="d869d-149">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="d869d-150">Par exemple, `Get-Item -Path .` ou `Get-Item \*` produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="d869d-150">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="d869d-151">Le fournisseur alias n’a pas de conteneurs, donc la commande ci-dessus a le même effet lorsqu’elle est utilisée avec `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="d869d-151">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="d869d-152">Obtenir un alias sélectionné</span><span class="sxs-lookup"><span data-stu-id="d869d-152">Get a selected alias</span></span>

<span data-ttu-id="d869d-153">Cette commande obtient l' `ls` alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-153">This command gets the `ls` alias.</span></span>
<span data-ttu-id="d869d-154">Étant donné qu’il comprend le chemin d’accès, vous pouvez l’utiliser dans n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d869d-154">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="d869d-155">Si vous êtes dans le `Alias:` lecteur, vous pouvez omettre le nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d869d-155">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="d869d-156">Vous pouvez également récupérer la définition d’un alias en préfixant le chemin d’accès du fournisseur avec le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="d869d-156">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="d869d-157">Obtenir tous les alias pour une applet de commande spécifique</span><span class="sxs-lookup"><span data-stu-id="d869d-157">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="d869d-158">Cette commande obtient une liste des alias associés à l’applet de commande `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="d869d-158">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="d869d-159">Elle utilise la propriété de **définition** , qui stocke le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d869d-159">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="d869d-160">Création d’alias</span><span class="sxs-lookup"><span data-stu-id="d869d-160">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="d869d-161">Créer un alias à partir du lecteur Alias :</span><span class="sxs-lookup"><span data-stu-id="d869d-161">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="d869d-162">Cette commande crée l' `serv` alias pour l' `Get-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d869d-162">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="d869d-163">Étant donné que l’emplacement actuel se trouve dans le `Alias:` lecteur, le `-Path` paramètre n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d869d-163">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="d869d-164">Cette commande utilise également le `-Options` paramètre Dynamic pour définir l’option **options AllScope** sur l’alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-164">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="d869d-165">Le `-Options` paramètre est disponible dans l' `New-Item` applet de commande uniquement lorsque vous êtes dans le `Alias:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="d869d-165">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="d869d-166">Le point ( `.` ) indique le répertoire actif, qui est le lecteur d’alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-166">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="d869d-167">Créer un alias avec un chemin d’accès absolu</span><span class="sxs-lookup"><span data-stu-id="d869d-167">Create an alias with an absolute path</span></span>

<span data-ttu-id="d869d-168">Vous pouvez créer un alias pour tout élément qui appelle une commande.</span><span class="sxs-lookup"><span data-stu-id="d869d-168">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="d869d-169">Cette commande crée l' `np` alias pour `Notepad.exe` .</span><span class="sxs-lookup"><span data-stu-id="d869d-169">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="d869d-170">Créer un alias pour une nouvelle fonction</span><span class="sxs-lookup"><span data-stu-id="d869d-170">Create an alias to a new function</span></span>

<span data-ttu-id="d869d-171">Vous pouvez créer un alias pour n'importe quelle fonction.</span><span class="sxs-lookup"><span data-stu-id="d869d-171">You can create an alias for any function.</span></span> <span data-ttu-id="d869d-172">Vous pouvez utiliser cette fonctionnalité pour créer un alias qui inclut à la fois une applet de commande et ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="d869d-172">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="d869d-173">La première commande crée la `CD32` fonction, qui remplace le répertoire actif par le `System32` répertoire.</span><span class="sxs-lookup"><span data-stu-id="d869d-173">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="d869d-174">La deuxième commande crée l' `go` alias pour la `CD32` fonction.</span><span class="sxs-lookup"><span data-stu-id="d869d-174">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="d869d-175">Une fois la commande terminée, vous pouvez utiliser `CD32` ou `go` pour appeler la fonction.</span><span class="sxs-lookup"><span data-stu-id="d869d-175">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="d869d-176">Modification des alias</span><span class="sxs-lookup"><span data-stu-id="d869d-176">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="d869d-177">Modifier les options d’un alias</span><span class="sxs-lookup"><span data-stu-id="d869d-177">Change the options of an alias</span></span>

<span data-ttu-id="d869d-178">Vous pouvez utiliser l' `Set-Item` applet de commande avec le `-Options` paramètre Dynamic pour modifier la valeur de la `-Options` propriété d’un alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-178">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="d869d-179">Cette commande définit les options **options AllScope** et **ReadOnly** pour l' `dir` alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-179">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="d869d-180">La commande utilise le `-Options` paramètre dynamique de l' `Set-Item` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d869d-180">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="d869d-181">Le `-Options` paramètre est disponible dans `Set-Item` lorsque vous l’utilisez avec l' **alias** ou le fournisseur de **fonctions** .</span><span class="sxs-lookup"><span data-stu-id="d869d-181">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="d869d-182">Modifier une commande référencée d’alias</span><span class="sxs-lookup"><span data-stu-id="d869d-182">Change an aliases referenced command</span></span>

<span data-ttu-id="d869d-183">Cette commande utilise la `Set-Item` cmdlet pour modifier l' `gp` alias afin qu’il représente l' `Get-Process` applet de commande au lieu de l’applet de commande `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="d869d-183">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="d869d-184">Le `-Force` paramètre est obligatoire, car la valeur de la propriété **options** de l' `gp` alias est définie sur `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="d869d-184">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="d869d-185">Étant donné que la commande est envoyée à partir du `Alias:` lecteur, le lecteur n’est pas spécifié dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d869d-185">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="d869d-186">La modification affecte les quatre propriétés qui définissent l'association entre l'alias et la commande.</span><span class="sxs-lookup"><span data-stu-id="d869d-186">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="d869d-187">Pour afficher l’effet de la modification, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d869d-187">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="d869d-188">Renommer un alias</span><span class="sxs-lookup"><span data-stu-id="d869d-188">Rename an alias</span></span>

<span data-ttu-id="d869d-189">Cette commande utilise l' `Rename-Item` applet de commande pour remplacer l' `popd` alias par `pop` .</span><span class="sxs-lookup"><span data-stu-id="d869d-189">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="d869d-190">Copie d’un alias</span><span class="sxs-lookup"><span data-stu-id="d869d-190">Copying an alias</span></span>

<span data-ttu-id="d869d-191">Cette commande copie l' `pushd` alias afin qu’un nouvel `push` alias soit créé pour l' `Push-Location` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d869d-191">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="d869d-192">Lorsque le nouvel alias est créé, sa propriété **Description** a une valeur null.</span><span class="sxs-lookup"><span data-stu-id="d869d-192">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="d869d-193">Et, sa propriété **option** a la valeur `None` .</span><span class="sxs-lookup"><span data-stu-id="d869d-193">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="d869d-194">Si la commande est émise à partir du `Alias:` lecteur, vous pouvez omettre le nom du lecteur de la valeur du `-Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d869d-194">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="d869d-195">Suppression d’un alias</span><span class="sxs-lookup"><span data-stu-id="d869d-195">Deleting an alias</span></span>

<span data-ttu-id="d869d-196">Cette commande supprime l' `serv` alias de la session active.</span><span class="sxs-lookup"><span data-stu-id="d869d-196">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="d869d-197">Vous pouvez utiliser cette commande dans n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d869d-197">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="d869d-198">Cette commande supprime les alias qui commencent par « s ».</span><span class="sxs-lookup"><span data-stu-id="d869d-198">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="d869d-199">Elle ne supprime pas les alias en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d869d-199">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="d869d-200">Supprimer les alias en lecture seule</span><span class="sxs-lookup"><span data-stu-id="d869d-200">Delete read-only aliases</span></span>

<span data-ttu-id="d869d-201">Cette commande supprime tous les alias de la session active, à l’exception de ceux dont la `Constant` propriété **options** a la valeur.</span><span class="sxs-lookup"><span data-stu-id="d869d-201">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="d869d-202">Le `-Force` paramètre permet à la commande de supprimer des alias dont la propriété **options** a la valeur `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="d869d-202">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="d869d-203">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="d869d-203">Dynamic parameters</span></span>

<span data-ttu-id="d869d-204">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d869d-204">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="d869d-205">Options [System. Management. Automation. ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="d869d-205">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="d869d-206">Détermine la valeur de la propriété **options** d’un alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-206">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="d869d-207">**None** : aucune option.</span><span class="sxs-lookup"><span data-stu-id="d869d-207">**None** : No options.</span></span> <span data-ttu-id="d869d-208">Cette valeur est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d869d-208">This value is the default.</span></span>
- <span data-ttu-id="d869d-209">**Constante** : l’alias ne peut pas être supprimé et ses propriétés ne peuvent pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="d869d-209">**Constant** :The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="d869d-210">La **constante** n’est disponible que lorsque vous créez un alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-210">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="d869d-211">Vous ne pouvez pas modifier l’option d’un alias existant en **constant** .</span><span class="sxs-lookup"><span data-stu-id="d869d-211">You cannot change the option of an existing alias to **Constant** .</span></span>
- <span data-ttu-id="d869d-212">**Privé** : l’alias est visible uniquement dans l’étendue actuelle, et non dans les étendues enfants.</span><span class="sxs-lookup"><span data-stu-id="d869d-212">**Private** :The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="d869d-213">**ReadOnly** : les propriétés de l’alias ne peuvent pas être modifiées, sauf en utilisant le `-Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d869d-213">**ReadOnly** :The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="d869d-214">Vous pouvez utiliser `Remove-Item` pour supprimer l’alias.</span><span class="sxs-lookup"><span data-stu-id="d869d-214">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="d869d-215">**Options AllScope** : l’alias est copié vers toutes les nouvelles étendues créées.</span><span class="sxs-lookup"><span data-stu-id="d869d-215">**AllScope** :The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="d869d-216">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="d869d-216">Cmdlets supported</span></span>

- [<span data-ttu-id="d869d-217">New-Item</span><span class="sxs-lookup"><span data-stu-id="d869d-217">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="d869d-218">Set-Item</span><span class="sxs-lookup"><span data-stu-id="d869d-218">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="d869d-219">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="d869d-219">Using the pipeline</span></span>

<span data-ttu-id="d869d-220">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="d869d-220">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="d869d-221">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d869d-221">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="d869d-222">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="d869d-222">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="d869d-223">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="d869d-223">Getting help</span></span>

<span data-ttu-id="d869d-224">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d869d-224">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="d869d-225">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d869d-225">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="d869d-226">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d869d-226">See also</span></span>

[<span data-ttu-id="d869d-227">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="d869d-227">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="d869d-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d869d-228">about_Providers</span></span>](../About/about_Providers.md)
