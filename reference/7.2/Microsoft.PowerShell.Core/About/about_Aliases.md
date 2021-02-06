---
description: Décrit comment utiliser des noms de remplacement pour les applets de commande et les commandes dans PowerShell.
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: e8b93e2b687e779048784c1eedb15fa53972b8b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596346"
---
# <a name="about-aliases"></a><span data-ttu-id="d12ea-103">À propos des alias</span><span class="sxs-lookup"><span data-stu-id="d12ea-103">About Aliases</span></span>

## <a name="short-description"></a><span data-ttu-id="d12ea-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="d12ea-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d12ea-105">Décrit comment utiliser des noms de remplacement pour les applets de commande et les commandes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d12ea-105">Describes how to use alternate names for cmdlets and commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d12ea-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="d12ea-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="d12ea-107">Un alias est un autre nom ou surnom pour une applet de commande ou un élément de commande, comme une fonction, un script, un fichier ou un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="d12ea-107">An alias is an alternate name or nickname for a cmdlet or for a command element, such as a function, script, file, or executable file.</span></span> <span data-ttu-id="d12ea-108">Vous pouvez utiliser l’alias à la place du nom de la commande dans toutes les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d12ea-108">You can use the alias instead of the command name in any PowerShell commands.</span></span>

<span data-ttu-id="d12ea-109">Pour créer un alias, utilisez l’applet de commande New-Alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-109">To create an alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="d12ea-110">Par exemple, la commande suivante crée l’alias « Gas » pour l' `Get-AuthenticodeSignature` applet de commande :</span><span class="sxs-lookup"><span data-stu-id="d12ea-110">For example, the following command creates the "gas" alias for the `Get-AuthenticodeSignature` cmdlet:</span></span>

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

<span data-ttu-id="d12ea-111">Après avoir créé l’alias pour le nom de l’applet de commande, vous pouvez utiliser l’alias à la place du nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d12ea-111">After you create the alias for the cmdlet name, you can use the alias instead of the cmdlet name.</span></span> <span data-ttu-id="d12ea-112">Par exemple, pour obtenir la signature Authenticode pour le fichier SqlScript.ps1, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-112">For example, to get the Authenticode signature for the SqlScript.ps1 file, type:</span></span>

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

<span data-ttu-id="d12ea-113">Ou tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-113">Or, type:</span></span>

```powershell
gas SqlScript.ps1
```

<span data-ttu-id="d12ea-114">Si vous créez « Word » comme alias pour Microsoft Office Word, vous pouvez taper « Word » à la place de ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d12ea-114">If you create "word" as the alias for Microsoft Office Word, you can type "word" instead of the following:</span></span>

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a><span data-ttu-id="d12ea-115">ALIAS INTÉGRÉS</span><span class="sxs-lookup"><span data-stu-id="d12ea-115">BUILT-IN ALIASES</span></span>

<span data-ttu-id="d12ea-116">PowerShell inclut un ensemble d’alias intégrés, y compris « CD » et « chdir » pour l’applet de commande Set-Location, et « LS » et « dir » pour l’applet de commande Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="d12ea-116">PowerShell includes a set of built-in aliases, including "cd" and "chdir" for the Set-Location cmdlet, and "ls" and "dir" for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="d12ea-117">Pour récupérer tous les alias sur l’ordinateur, y compris les alias intégrés, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-117">To get all the aliases on the computer, including the built-in aliases, type:</span></span>

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a><span data-ttu-id="d12ea-118">APPLETS DE COMMANDE D’ALIAS</span><span class="sxs-lookup"><span data-stu-id="d12ea-118">ALIAS CMDLETS</span></span>

<span data-ttu-id="d12ea-119">PowerShell comprend les applets de commande suivantes, qui sont conçues pour utiliser des alias :</span><span class="sxs-lookup"><span data-stu-id="d12ea-119">PowerShell includes the following cmdlets, which are designed for working with aliases:</span></span>

- <span data-ttu-id="d12ea-120">`Get-Alias` -Obtient tous les alias dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d12ea-120">`Get-Alias` - Gets all the aliases in the current session.</span></span>
- <span data-ttu-id="d12ea-121">`New-Alias` -Crée un nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-121">`New-Alias` - Creates a new alias.</span></span>
- <span data-ttu-id="d12ea-122">`Set-Alias` -Crée ou modifie un alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-122">`Set-Alias` - Creates or changes an alias.</span></span>
- <span data-ttu-id="d12ea-123">`Export-Alias` -Exporte un ou plusieurs alias dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d12ea-123">`Export-Alias` - Exports one or more aliases to a file.</span></span>
- <span data-ttu-id="d12ea-124">`Import-Alias` -Importe un fichier d’alias dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d12ea-124">`Import-Alias` - Imports an alias file into PowerShell.</span></span>

<span data-ttu-id="d12ea-125">Pour plus d’informations sur les applets de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-125">For detailed information about the cmdlets, type:</span></span>

```powershell
Get-Help <cmdlet-Name> -Detailed
```

<span data-ttu-id="d12ea-126">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-126">For example, type:</span></span>

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a><span data-ttu-id="d12ea-127">CRÉATION D’UN ALIAS</span><span class="sxs-lookup"><span data-stu-id="d12ea-127">CREATING AN ALIAS</span></span>

<span data-ttu-id="d12ea-128">Pour créer un alias, utilisez l’applet de commande New-Alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-128">To create a new alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="d12ea-129">Par exemple, pour créer l’alias « GH » pour obtenir-Help, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-129">For example, to create the "gh" alias for Get-Help, type:</span></span>

```powershell
New-Alias -Name gh -Value Get-Help
```

<span data-ttu-id="d12ea-130">Vous pouvez utiliser l’alias dans les commandes, de la même façon que vous utilisez le nom complet de l’applet de commande, et vous pouvez utiliser l’alias avec des paramètres.</span><span class="sxs-lookup"><span data-stu-id="d12ea-130">You can use the alias in commands, just as you would use the full cmdlet name, and you can use the alias with parameters.</span></span>

<span data-ttu-id="d12ea-131">Par exemple, pour obtenir une aide détaillée sur l’applet de commande Get-WmiObject, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-131">For example, to get detailed Help for the Get-WmiObject cmdlet, type:</span></span>

```powershell
Get-Help Get-WmiObject -Detailed
```

<span data-ttu-id="d12ea-132">Ou tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-132">Or, type:</span></span>

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a><span data-ttu-id="d12ea-133">ENREGISTREMENT DES ALIAS</span><span class="sxs-lookup"><span data-stu-id="d12ea-133">SAVING ALIASES</span></span>

<span data-ttu-id="d12ea-134">Les alias que vous créez sont enregistrés uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d12ea-134">The aliases that you create are saved only in the current session.</span></span> <span data-ttu-id="d12ea-135">Pour utiliser les alias dans une autre session, ajoutez l’alias à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d12ea-135">To use the aliases in a different session, add the alias to your PowerShell profile.</span></span> <span data-ttu-id="d12ea-136">Vous pouvez utiliser l’applet de commande Export-Alias pour enregistrer les alias dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d12ea-136">Or, use the Export-Alias cmdlet to save the aliases to a file.</span></span>

<span data-ttu-id="d12ea-137">Pour plus d’informations, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d12ea-137">For more information, type:</span></span>

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a><span data-ttu-id="d12ea-138">OBTENTION D’ALIAS</span><span class="sxs-lookup"><span data-stu-id="d12ea-138">GETTING ALIASES</span></span>

<span data-ttu-id="d12ea-139">Pour obtenir tous les alias dans la session active, y compris les alias intégrés, les alias dans vos profils PowerShell et les alias que vous avez créés dans la session active, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-139">To get all the aliases in the current session, including the built-in aliases, the aliases in your PowerShell profiles, and the aliases that you have created in the current session, type:</span></span>

```powershell
Get-Alias
```

<span data-ttu-id="d12ea-140">Pour accéder à des alias particuliers, utilisez le paramètre Name de l’applet de commande Get-Alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-140">To get particular aliases, use the Name parameter of the Get-Alias cmdlet.</span></span> <span data-ttu-id="d12ea-141">Par exemple, pour obtenir des alias qui commencent par « p », tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-141">For example, to get aliases that begin with "p", type:</span></span>

```powershell
Get-Alias -Name p*
```

<span data-ttu-id="d12ea-142">Pour obtenir les alias pour un élément particulier, utilisez le paramètre de définition.</span><span class="sxs-lookup"><span data-stu-id="d12ea-142">To get the aliases for a particular item, use the Definition parameter.</span></span> <span data-ttu-id="d12ea-143">Par exemple, pour obtenir les alias pour le type d’applet de commande Get-ChildItem :</span><span class="sxs-lookup"><span data-stu-id="d12ea-143">For example, to get the aliases for the Get-ChildItem cmdlet type:</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a><span data-ttu-id="d12ea-144">RÉSULTAT DE LA RÉCUPÉRATION DE L’ALIAS</span><span class="sxs-lookup"><span data-stu-id="d12ea-144">GET-ALIAS OUTPUT</span></span>

<span data-ttu-id="d12ea-145">Get-Alias retourne un seul type d’objet, un objet AliasInfo (System. Management. Automation. AliasInfo).</span><span class="sxs-lookup"><span data-stu-id="d12ea-145">Get-Alias returns only one type of object, an AliasInfo object (System.Management.Automation.AliasInfo).</span></span> <span data-ttu-id="d12ea-146">Le nom des alias qui n’incluent pas de trait d’Union, tel que « CD », est affiché au format suivant :</span><span class="sxs-lookup"><span data-stu-id="d12ea-146">The name of aliases that don't include a hyphen, such as "cd" are displayed in the following format:</span></span>

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

<span data-ttu-id="d12ea-147">Il est ainsi très rapide et facile d’accéder aux informations dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="d12ea-147">This makes it very quick and easy to get the information that you need.</span></span>

<span data-ttu-id="d12ea-148">Le format de nom d'alias basé sur les flèches n'est pas utilisé pour les alias qui comportent un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="d12ea-148">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="d12ea-149">Il s’agit probablement de noms de substitution préférés pour les applets de commande et les fonctions, plutôt que par des abréviations ou des surnoms typiques, et l’auteur peut ne pas souhaiter qu’ils soient aussi évidents.</span><span class="sxs-lookup"><span data-stu-id="d12ea-149">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames, and the author might not want them to be as evident.</span></span>

## <a name="alternate-names-for-commands-with-parameters"></a><span data-ttu-id="d12ea-150">AUTRES NOMS POUR LES COMMANDES AVEC DES PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="d12ea-150">ALTERNATE NAMES FOR COMMANDS WITH PARAMETERS</span></span>

<span data-ttu-id="d12ea-151">Vous pouvez assigner un alias à une applet de commande, un script, une fonction ou un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="d12ea-151">You can assign an alias to a cmdlet, script, function, or executable file.</span></span> <span data-ttu-id="d12ea-152">Vous ne pouvez pas assigner un alias à une commande et à ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="d12ea-152">You cannot assign an alias to a command and its parameters.</span></span> <span data-ttu-id="d12ea-153">Par exemple, vous pouvez assigner un alias à l' `Get-Eventlog` applet de commande, mais vous ne pouvez pas assigner un alias à la `Get-Eventlog -LogName System` commande.</span><span class="sxs-lookup"><span data-stu-id="d12ea-153">For example, you can assign an alias to the `Get-Eventlog` cmdlet, but you cannot assign an alias to the `Get-Eventlog -LogName System` command.</span></span>

<span data-ttu-id="d12ea-154">Vous pouvez créer une fonction qui comprend la commande.</span><span class="sxs-lookup"><span data-stu-id="d12ea-154">You can create a function that includes the command.</span></span> <span data-ttu-id="d12ea-155">Pour créer une fonction, tapez le mot « function » suivi d’un nom pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="d12ea-155">To create a function, type the word "function" followed by a name for the function.</span></span> <span data-ttu-id="d12ea-156">Tapez la commande et mettez-la entre accolades ( {} ).</span><span class="sxs-lookup"><span data-stu-id="d12ea-156">Type the command, and enclose it in braces ({}).</span></span>

<span data-ttu-id="d12ea-157">Par exemple, la commande suivante crée la fonction syslog.</span><span class="sxs-lookup"><span data-stu-id="d12ea-157">For example, the following command creates the syslog function.</span></span> <span data-ttu-id="d12ea-158">Cette fonction représente la `Get-Eventlog -LogName System` commande :</span><span class="sxs-lookup"><span data-stu-id="d12ea-158">This function represents the `Get-Eventlog -LogName System` command:</span></span>

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

<span data-ttu-id="d12ea-159">Vous pouvez maintenant taper « syslog » à la place de la commande.</span><span class="sxs-lookup"><span data-stu-id="d12ea-159">You can now type "syslog" instead of the command.</span></span> <span data-ttu-id="d12ea-160">Vous pouvez créer des alias pour la nouvelle fonction.</span><span class="sxs-lookup"><span data-stu-id="d12ea-160">And, you can create aliases for the new function.</span></span>

<span data-ttu-id="d12ea-161">Pour plus d’informations sur les fonctions, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-161">For more information about functions, type:</span></span>

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a><span data-ttu-id="d12ea-162">OBJETS ALIAS</span><span class="sxs-lookup"><span data-stu-id="d12ea-162">ALIAS OBJECTS</span></span>

<span data-ttu-id="d12ea-163">Les alias PowerShell sont représentés par des objets qui sont des instances de la classe System. Management. Automation. AliasInfo.</span><span class="sxs-lookup"><span data-stu-id="d12ea-163">PowerShell aliases are represented by objects that are instances of the System.Management.Automation.AliasInfo class.</span></span> <span data-ttu-id="d12ea-164">Pour plus d’informations sur ce type d’objet, consultez [AliasInfo, classe][aliasinfo] dans le kit de développement logiciel (SDK) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d12ea-164">For more information about this type of object, see [AliasInfo Class][aliasinfo] in the PowerShell SDK.</span></span>

<span data-ttu-id="d12ea-165">Pour afficher les propriétés et les méthodes des objets alias, récupérez les alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-165">To view the properties and methods of the alias objects, get the aliases.</span></span>
<span data-ttu-id="d12ea-166">Ensuite, dirigez-les vers l’applet de commande Get-Member.</span><span class="sxs-lookup"><span data-stu-id="d12ea-166">Then, pipe them to the Get-Member cmdlet.</span></span> <span data-ttu-id="d12ea-167">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d12ea-167">For example:</span></span>

```powershell
Get-Alias | Get-Member
```

<span data-ttu-id="d12ea-168">Pour afficher les valeurs des propriétés d’un alias spécifique, telles que l' `dir` alias, récupérez l’alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-168">To view the values of the properties of a specific alias, such as the `dir` alias, get the alias.</span></span> <span data-ttu-id="d12ea-169">Ensuite, dirigez-le vers l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="d12ea-169">Then, pipe it to the Format-List cmdlet.</span></span> <span data-ttu-id="d12ea-170">Par exemple, la commande suivante obtient l’alias « dir ».</span><span class="sxs-lookup"><span data-stu-id="d12ea-170">For example, the following command gets the "dir" alias.</span></span> <span data-ttu-id="d12ea-171">Ensuite, la commande dirige l’alias vers l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="d12ea-171">Next, the command pipes the alias to the Format-List cmdlet.</span></span> <span data-ttu-id="d12ea-172">Ensuite, la commande utilise le paramètre Property de Format-List avec un caractère générique ( \* ) pour afficher toutes les propriétés de l' `dir` alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-172">Then, the command uses the Property parameter of Format-List with a wildcard character (\*) to display all the properties of the `dir` alias.</span></span> <span data-ttu-id="d12ea-173">La commande suivante effectue ces tâches :</span><span class="sxs-lookup"><span data-stu-id="d12ea-173">The following command performs these tasks:</span></span>

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a><span data-ttu-id="d12ea-174">FOURNISSEUR d’ALIAS PowerShell</span><span class="sxs-lookup"><span data-stu-id="d12ea-174">PowerShell ALIAS PROVIDER</span></span>

<span data-ttu-id="d12ea-175">PowerShell comprend le fournisseur d’alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-175">PowerShell includes the Alias provider.</span></span> <span data-ttu-id="d12ea-176">Le fournisseur alias vous permet d’afficher les alias dans PowerShell comme s’ils étaient sur un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d12ea-176">The Alias provider lets you view the aliases in PowerShell as though they were on a file system drive.</span></span>

<span data-ttu-id="d12ea-177">Le fournisseur alias expose le lecteur Alias :.</span><span class="sxs-lookup"><span data-stu-id="d12ea-177">The Alias provider exposes the Alias: drive.</span></span> <span data-ttu-id="d12ea-178">Pour accéder au lecteur Alias :, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-178">To go into the Alias: drive, type:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="d12ea-179">Pour afficher le contenu du lecteur, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-179">To view the contents of the drive, type:</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="d12ea-180">Pour afficher le contenu du lecteur à partir d’un autre lecteur PowerShell, commencez le chemin d’accès par le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="d12ea-180">To view the contents of the drive from another PowerShell drive, begin the path with the drive name.</span></span> <span data-ttu-id="d12ea-181">Incluez le signe deux-points ( :).</span><span class="sxs-lookup"><span data-stu-id="d12ea-181">Include the colon (:).</span></span> <span data-ttu-id="d12ea-182">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d12ea-182">For example:</span></span>

```powershell
Get-ChildItem -Path Alias:
```

<span data-ttu-id="d12ea-183">Pour obtenir des informations sur un alias particulier, tapez le nom du lecteur et le nom de l’alias.</span><span class="sxs-lookup"><span data-stu-id="d12ea-183">To get information about a particular alias, type the drive name and the alias name.</span></span> <span data-ttu-id="d12ea-184">Ou tapez un modèle de nom.</span><span class="sxs-lookup"><span data-stu-id="d12ea-184">Or, type a name pattern.</span></span> <span data-ttu-id="d12ea-185">Par exemple, pour obtenir tous les alias qui commencent par « p », tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-185">For example, to get all the aliases that begin with "p", type:</span></span>

```powershell
Get-ChildItem -Path Alias:p*
```

<span data-ttu-id="d12ea-186">Pour plus d’informations sur le fournisseur d’alias PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="d12ea-186">For more information about the PowerShell Alias provider, type:</span></span>

```powershell
Get-Help Alias
```

## <a name="see-also"></a><span data-ttu-id="d12ea-187">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="d12ea-187">SEE ALSO</span></span>

- [<span data-ttu-id="d12ea-188">New-Alias</span><span class="sxs-lookup"><span data-stu-id="d12ea-188">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="d12ea-189">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="d12ea-189">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="d12ea-190">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="d12ea-190">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [<span data-ttu-id="d12ea-191">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="d12ea-191">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="d12ea-192">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="d12ea-192">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="d12ea-193">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d12ea-193">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [<span data-ttu-id="d12ea-194">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="d12ea-194">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="d12ea-195">about_functions</span><span class="sxs-lookup"><span data-stu-id="d12ea-195">about_functions</span></span>](about_functions.md)
- [<span data-ttu-id="d12ea-196">about_profiles</span><span class="sxs-lookup"><span data-stu-id="d12ea-196">about_profiles</span></span>](about_profiles.md)
- [<span data-ttu-id="d12ea-197">about_providers</span><span class="sxs-lookup"><span data-stu-id="d12ea-197">about_providers</span></span>](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo