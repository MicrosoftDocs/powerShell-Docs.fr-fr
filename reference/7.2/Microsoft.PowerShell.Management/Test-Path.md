---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: a79f12739643a873703b39d9d07e8b7db01dfbb4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596122"
---
# <span data-ttu-id="2548d-102">Test-Path</span><span class="sxs-lookup"><span data-stu-id="2548d-102">Test-Path</span></span>

## <span data-ttu-id="2548d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2548d-103">SYNOPSIS</span></span>
<span data-ttu-id="2548d-104">Détermine si tous les éléments d'un chemin d'accès existent.</span><span class="sxs-lookup"><span data-stu-id="2548d-104">Determines whether all elements of a path exist.</span></span>

## <span data-ttu-id="2548d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2548d-105">SYNTAX</span></span>

### <span data-ttu-id="2548d-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2548d-106">Path (Default)</span></span>

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="2548d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2548d-107">LiteralPath</span></span>

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## <span data-ttu-id="2548d-108">Description</span><span class="sxs-lookup"><span data-stu-id="2548d-108">DESCRIPTION</span></span>

<span data-ttu-id="2548d-109">L' `Test-Path` applet de commande détermine si tous les éléments du chemin d’accès existent.</span><span class="sxs-lookup"><span data-stu-id="2548d-109">The `Test-Path` cmdlet determines whether all elements of the path exist.</span></span> <span data-ttu-id="2548d-110">Elle retourne `$True` si tous les éléments existent et `$False` si des éléments sont manquants.</span><span class="sxs-lookup"><span data-stu-id="2548d-110">It returns `$True` if all elements exist and `$False` if any are missing.</span></span> <span data-ttu-id="2548d-111">Il peut également indiquer si la syntaxe du chemin d’accès est valide et si le chemin d’accès est un conteneur ou un élément terminal ou feuille.</span><span class="sxs-lookup"><span data-stu-id="2548d-111">It can also tell whether the path syntax is valid and whether the path leads to a container or a terminal or leaf element.</span></span> <span data-ttu-id="2548d-112">Si le `Path` est un espace blanc d’une chaîne vide, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="2548d-112">If the `Path` is whitespace an empty string, then `$False` is returned.</span></span> <span data-ttu-id="2548d-113">Si `Path` est `$null` , tableau `$null` ou tableau vide, une erreur sans fin d’achèvement est retournée.</span><span class="sxs-lookup"><span data-stu-id="2548d-113">If the `Path` is `$null`, array of `$null` or empty array, a non-terminating error is returned.</span></span>

## <span data-ttu-id="2548d-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2548d-114">EXAMPLES</span></span>

### <span data-ttu-id="2548d-115">Exemple 1 : tester un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="2548d-115">Example 1: Test a path</span></span>

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

<span data-ttu-id="2548d-116">Cette commande vérifie si tous les éléments du chemin d’accès existent, autrement dit, le répertoire C :, le répertoire documents and Settings et le répertoire DavidC</span><span class="sxs-lookup"><span data-stu-id="2548d-116">This command checks whether all elements in the path exist, that is, the C: directory, the Documents and Settings directory, and the DavidC directory.</span></span> <span data-ttu-id="2548d-117">S’il en manque, l’applet de commande retourne `$False` .</span><span class="sxs-lookup"><span data-stu-id="2548d-117">If any are missing, the cmdlet returns `$False`.</span></span>
<span data-ttu-id="2548d-118">Sinon, `$True`est retourné.</span><span class="sxs-lookup"><span data-stu-id="2548d-118">Otherwise, it returns `$True`.</span></span>

### <span data-ttu-id="2548d-119">Exemple 2 : tester le chemin d’accès d’un profil</span><span class="sxs-lookup"><span data-stu-id="2548d-119">Example 2: Test the path of a profile</span></span>

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

<span data-ttu-id="2548d-120">Ces commandes testent le chemin d’accès du profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2548d-120">These commands test the path of the PowerShell profile.</span></span>

<span data-ttu-id="2548d-121">La première commande détermine si tous les éléments du chemin d'accès existent.</span><span class="sxs-lookup"><span data-stu-id="2548d-121">The first command determines whether all elements in the path exist.</span></span> <span data-ttu-id="2548d-122">La deuxième commande détermine si la syntaxe du chemin d'accès est correcte.</span><span class="sxs-lookup"><span data-stu-id="2548d-122">The second command determines whether the syntax of the path is correct.</span></span> <span data-ttu-id="2548d-123">Dans ce cas, le chemin d’accès est `$False` , mais la syntaxe est correcte `$True` .</span><span class="sxs-lookup"><span data-stu-id="2548d-123">In this case, the path is `$False`, but the syntax is correct `$True`.</span></span> <span data-ttu-id="2548d-124">Ces commandes utilisent `$profile` , la variable automatique qui pointe vers l’emplacement du profil, même si le profil n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="2548d-124">These commands use `$profile`, the automatic variable that points to the location for the profile, even if the profile does not exist.</span></span>

<span data-ttu-id="2548d-125">Pour plus d'informations sur les variables automatiques, consultez about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="2548d-125">For more information about automatic variables, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="2548d-126">Exemple 3 : vérifier si des fichiers sont en dehors d’un type spécifié</span><span class="sxs-lookup"><span data-stu-id="2548d-126">Example 3: Check whether there are any files besides a specified type</span></span>

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

<span data-ttu-id="2548d-127">Cette commande vérifie si des fichiers se trouvent dans le répertoire des bâtiments commerciaux, à l’exception des fichiers. dwg.</span><span class="sxs-lookup"><span data-stu-id="2548d-127">This command checks whether there are any files in the Commercial Buildings directory other than .dwg files.</span></span>

<span data-ttu-id="2548d-128">La commande utilise le paramètre **path** pour spécifier le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2548d-128">The command uses the **Path** parameter to specify the path.</span></span> <span data-ttu-id="2548d-129">Étant donné que le chemin d’accès comprend un espace, le chemin d’accès est placé entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="2548d-129">Because the path includes a space, the path is enclosed in quotation marks.</span></span> <span data-ttu-id="2548d-130">L'astérisque situé à la fin du chemin d'accès indique le contenu du répertoire Commercial Building.</span><span class="sxs-lookup"><span data-stu-id="2548d-130">The asterisk at the end of the path indicates the contents of the Commercial Building directory.</span></span> <span data-ttu-id="2548d-131">Avec des chemins d’accès longs, tels que celui-ci, tapez les premières lettres du chemin d’accès, puis utilisez la touche TAB pour compléter le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2548d-131">With long paths, such as this one, type the first few letters of the path, and then use the TAB key to complete the path.</span></span>

<span data-ttu-id="2548d-132">La commande spécifie le paramètre **Exclude** pour spécifier les fichiers qui seront omis de l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="2548d-132">The command specifies the **Exclude** parameter to specify files that will be omitted from the evaluation.</span></span>

<span data-ttu-id="2548d-133">Dans ce cas, étant donné que le répertoire contient uniquement des fichiers. dwg, le résultat est `$False` .</span><span class="sxs-lookup"><span data-stu-id="2548d-133">In this case, because the directory contains only .dwg files, the result is `$False`.</span></span>

### <span data-ttu-id="2548d-134">Exemple 4 : Rechercher un fichier</span><span class="sxs-lookup"><span data-stu-id="2548d-134">Example 4: Check for a file</span></span>

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

<span data-ttu-id="2548d-135">Cette commande vérifie si le chemin d’accès stocké dans la `$profile` variable ouvre un fichier.</span><span class="sxs-lookup"><span data-stu-id="2548d-135">This command checks whether the path stored in the `$profile` variable leads to a file.</span></span> <span data-ttu-id="2548d-136">Dans ce cas, étant donné que le profil PowerShell est un `.ps1` fichier, l’applet de commande retourne `$True` .</span><span class="sxs-lookup"><span data-stu-id="2548d-136">In this case, because the PowerShell profile is a `.ps1` file, the cmdlet returns `$True`.</span></span>

### <span data-ttu-id="2548d-137">Exemple 5 : vérifier les chemins d’accès dans le registre</span><span class="sxs-lookup"><span data-stu-id="2548d-137">Example 5: Check paths in the Registry</span></span>

<span data-ttu-id="2548d-138">Ces commandes utilisent `Test-Path` avec le fournisseur de Registre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2548d-138">These commands use `Test-Path` with the PowerShell registry provider.</span></span>

<span data-ttu-id="2548d-139">La première commande teste si le chemin d’accès du registre de la clé de Registre **Microsoft. PowerShell** est correct sur le système.</span><span class="sxs-lookup"><span data-stu-id="2548d-139">The first command tests whether the registry path of the **Microsoft.PowerShell** registry key is correct on the system.</span></span> <span data-ttu-id="2548d-140">Si PowerShell est installé correctement, l’applet de commande retourne `$True` .</span><span class="sxs-lookup"><span data-stu-id="2548d-140">If PowerShell is installed correctly, the cmdlet returns `$True`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2548d-141">`Test-Path` ne fonctionne pas correctement avec tous les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2548d-141">`Test-Path` does not work correctly with all PowerShell providers.</span></span> <span data-ttu-id="2548d-142">Par exemple, vous pouvez utiliser `Test-Path` pour tester le chemin d’accès à une clé de Registre, mais si vous l’utilisez pour tester le chemin d’accès d’une entrée de Registre, elle retourne toujours `$False` , même si l’entrée de Registre est présente.</span><span class="sxs-lookup"><span data-stu-id="2548d-142">For example, you can use `Test-Path` to test the path of a registry key, but if you use it to test the path of a registry entry, it always returns `$False`, even if the registry entry is present.</span></span>

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### <span data-ttu-id="2548d-143">Exemple 6 : tester si un fichier est plus récent qu’une date spécifiée</span><span class="sxs-lookup"><span data-stu-id="2548d-143">Example 6: Test if a file is newer than a specified date</span></span>

<span data-ttu-id="2548d-144">Cette commande utilise le paramètre dynamique **NewerThan** pour déterminer si le fichier « PowerShell.exe » sur l’ordinateur est plus récent que « le 13 juillet 2009 ».</span><span class="sxs-lookup"><span data-stu-id="2548d-144">This command uses the **NewerThan** dynamic parameter to determine whether the "PowerShell.exe" file on the computer is newer than "July 13, 2009".</span></span>

<span data-ttu-id="2548d-145">Le paramètre NewerThan fonctionne uniquement dans les lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="2548d-145">The NewerThan parameter works only in file system drives.</span></span>

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### <span data-ttu-id="2548d-146">Exemple 7 : tester un chemin d’accès avec NULL comme valeur</span><span class="sxs-lookup"><span data-stu-id="2548d-146">Example 7: Test a path with null as the value</span></span>

<span data-ttu-id="2548d-147">L’erreur retournée pour `null` , tableau de `null` ou tableau vide est une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="2548d-147">The error returned for `null`, array of `null` or empty array is a non-terminating error.</span></span> <span data-ttu-id="2548d-148">Il peut être supprimé à l’aide de `-ErrorAction SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="2548d-148">It can be suppress by using `-ErrorAction SilentlyContinue`.</span></span> <span data-ttu-id="2548d-149">L’exemple suivant montre tous les cas qui retournent l' `NullPathNotPermitted` erreur.</span><span class="sxs-lookup"><span data-stu-id="2548d-149">The following example shows all cases which return the `NullPathNotPermitted` error.</span></span>

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### <span data-ttu-id="2548d-150">Exemple 8 : test d’un chemin d’accès avec un espace blanc en tant que valeur</span><span class="sxs-lookup"><span data-stu-id="2548d-150">Example 8: Test a path with whitespace as the value</span></span>

<span data-ttu-id="2548d-151">Lorsqu’un espace blanc ou une chaîne vide est fourni pour le `-Path` paramètre, la **valeur false** est retournée.</span><span class="sxs-lookup"><span data-stu-id="2548d-151">When a whitespace or empty string is provided for the the `-Path` parameter, it returns **False**.</span></span>
<span data-ttu-id="2548d-152">L’exemple suivant montre un espace blanc et une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="2548d-152">The following example show whitespace and empty string.</span></span>

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## <span data-ttu-id="2548d-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2548d-153">PARAMETERS</span></span>

### <span data-ttu-id="2548d-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="2548d-154">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2548d-155">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2548d-155">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="2548d-156">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="2548d-156">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2548d-157">-Exclude</span><span class="sxs-lookup"><span data-stu-id="2548d-157">-Exclude</span></span>

<span data-ttu-id="2548d-158">Spécifie les éléments que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="2548d-158">Specifies items that this cmdlet omits.</span></span> <span data-ttu-id="2548d-159">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="2548d-159">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2548d-160">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="2548d-160">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="2548d-161">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2548d-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2548d-162">-Filter</span><span class="sxs-lookup"><span data-stu-id="2548d-162">-Filter</span></span>

<span data-ttu-id="2548d-163">Spécifie un filtre dans le format ou la langue du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2548d-163">Specifies a filter in the format or language of the provider.</span></span> <span data-ttu-id="2548d-164">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="2548d-164">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2548d-165">La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2548d-165">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="2548d-166">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsqu’il récupère les objets au lieu d’avoir le filtre PowerShell pour les objets après leur récupération.</span><span class="sxs-lookup"><span data-stu-id="2548d-166">Filters are more efficient than other parameters, because the provider applies them when it retrieves the objects instead of having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2548d-167">-Include</span><span class="sxs-lookup"><span data-stu-id="2548d-167">-Include</span></span>

<span data-ttu-id="2548d-168">Spécifie les chemins que cette applet de commande teste.</span><span class="sxs-lookup"><span data-stu-id="2548d-168">Specifies paths that this cmdlet tests.</span></span> <span data-ttu-id="2548d-169">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="2548d-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2548d-170">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="2548d-170">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="2548d-171">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2548d-171">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2548d-172">-IsValid</span><span class="sxs-lookup"><span data-stu-id="2548d-172">-IsValid</span></span>

<span data-ttu-id="2548d-173">Indique que cette applet de commande teste la syntaxe du chemin d’accès, que les éléments du chemin d’accès existent ou non.</span><span class="sxs-lookup"><span data-stu-id="2548d-173">Indicates that this cmdlet tests the syntax of the path, regardless of whether the elements of the path exist.</span></span> <span data-ttu-id="2548d-174">Cette applet de commande retourne `$True` si la syntaxe du chemin d’accès est valide et si ce n' `$False` est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="2548d-174">This cmdlet returns `$True` if the path syntax is valid and `$False` if it is not.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2548d-175">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2548d-175">-LiteralPath</span></span>

<span data-ttu-id="2548d-176">Spécifie un chemin d’accès à vérifier.</span><span class="sxs-lookup"><span data-stu-id="2548d-176">Specifies a path to be tested.</span></span> <span data-ttu-id="2548d-177">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="2548d-177">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="2548d-178">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="2548d-178">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="2548d-179">Si le chemin d’accès comprend des caractères qui peuvent être interprétés par PowerShell comme des séquences d’échappement, vous devez placer le chemin d’accès entre guillemets simples afin qu’ils ne soient pas interprétés.</span><span class="sxs-lookup"><span data-stu-id="2548d-179">If the path includes characters that could be interpreted by PowerShell as escape sequences, you must enclose the path in single quote so that they won't be interpreted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2548d-180">-NewerThan</span><span class="sxs-lookup"><span data-stu-id="2548d-180">-NewerThan</span></span>

<span data-ttu-id="2548d-181">Spécifiez une heure sous la forme d’un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="2548d-181">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2548d-182">-OlderThan </span><span class="sxs-lookup"><span data-stu-id="2548d-182">-OlderThan</span></span>

<span data-ttu-id="2548d-183">Spécifiez une heure sous la forme d’un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="2548d-183">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2548d-184">-Path</span><span class="sxs-lookup"><span data-stu-id="2548d-184">-Path</span></span>

<span data-ttu-id="2548d-185">Spécifie un chemin d’accès à vérifier.</span><span class="sxs-lookup"><span data-stu-id="2548d-185">Specifies a path to be tested.</span></span> <span data-ttu-id="2548d-186">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2548d-186">Wildcard characters are permitted.</span></span> <span data-ttu-id="2548d-187">Si le chemin d’accès inclut des espaces, mettez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="2548d-187">If the path includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2548d-188">-PathType</span><span class="sxs-lookup"><span data-stu-id="2548d-188">-PathType</span></span>

<span data-ttu-id="2548d-189">Spécifie le type de l’élément final dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2548d-189">Specifies the type of the final element in the path.</span></span> <span data-ttu-id="2548d-190">Cette applet de commande retourne `$True` si l’élément est du type spécifié et `$False` si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="2548d-190">This cmdlet returns `$True` if the element is of the specified type and `$False` if it is not.</span></span> <span data-ttu-id="2548d-191">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="2548d-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2548d-192">Conteneur.</span><span class="sxs-lookup"><span data-stu-id="2548d-192">Container.</span></span>
  <span data-ttu-id="2548d-193">élément qui contient d'autres éléments (répertoire ou clé de Registre, par exemple).</span><span class="sxs-lookup"><span data-stu-id="2548d-193">An element that contains other elements, such as a directory or registry key.</span></span>
- <span data-ttu-id="2548d-194">Inférieurs.</span><span class="sxs-lookup"><span data-stu-id="2548d-194">Leaf.</span></span>
  <span data-ttu-id="2548d-195">élément qui ne contient pas d'autres éléments (fichier, par exemple).</span><span class="sxs-lookup"><span data-stu-id="2548d-195">An element that does not contain other elements, such as a file.</span></span>
- <span data-ttu-id="2548d-196">Aux.</span><span class="sxs-lookup"><span data-stu-id="2548d-196">Any.</span></span>
  <span data-ttu-id="2548d-197">conteneur ou nœud terminal.</span><span class="sxs-lookup"><span data-stu-id="2548d-197">Either a container or a leaf.</span></span>

<span data-ttu-id="2548d-198">Indique si le dernier élément figurant dans le chemin d’accès est d’un type particulier.</span><span class="sxs-lookup"><span data-stu-id="2548d-198">Tells whether the final element in the path is of a particular type.</span></span>

> [!CAUTION]
>
> <span data-ttu-id="2548d-199">Jusqu’à PowerShell version 6.1.2, lorsque les commutateurs **IsValid** et **PathType** sont spécifiés ensemble, l’applet de commande `Test-Path` ignore le commutateur **PathType** et valide uniquement le chemin syntaxique sans valider le type de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="2548d-199">Up to PowerShell version 6.1.2, when the **IsValid** and **PathType** switches are specified together, the `Test-Path` cmdlet ignores the **PathType** switch and only validates the syntactic path without validating the path type.</span></span>
>
> <span data-ttu-id="2548d-200">En fonction du [problème #8607](https://github.com/PowerShell/PowerShell/issues/8607), la résolution de ce problème peut être une modification avec rupture dans une future version, où les commutateurs **IsValid** et **PathType** appartiennent à des jeux de paramètres distincts et, par conséquent, ne peuvent pas être utilisés ensemble pour éviter cette confusion.</span><span class="sxs-lookup"><span data-stu-id="2548d-200">According to [issue #8607](https://github.com/PowerShell/PowerShell/issues/8607), fixing this behavior may be a breaking change in a future version, where the **IsValid** and **PathType** switches belong to separate parameter sets, and thus, cannot be used together avoiding this confusion.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2548d-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2548d-201">CommonParameters</span></span>

<span data-ttu-id="2548d-202">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2548d-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2548d-203">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2548d-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2548d-204">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2548d-204">INPUTS</span></span>

### <span data-ttu-id="2548d-205">System.String</span><span class="sxs-lookup"><span data-stu-id="2548d-205">System.String</span></span>

<span data-ttu-id="2548d-206">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2548d-206">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="2548d-207">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2548d-207">OUTPUTS</span></span>

### <span data-ttu-id="2548d-208">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="2548d-208">System.Boolean</span></span>

<span data-ttu-id="2548d-209">L’applet de commande retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="2548d-209">The cmdlet returns a **Boolean** value.</span></span>

## <span data-ttu-id="2548d-210">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2548d-210">NOTES</span></span>

<span data-ttu-id="2548d-211">Les applets de commande qui contiennent le nom de **chemin** d’accès (les applets de commande **path** ) fonctionnent avec des noms de chemins d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="2548d-211">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="2548d-212">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="2548d-212">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="2548d-213">Utilisez-les comme vous le feriez avec **dirname**, **Normpath**, **realpath**, **join** ou d’autres manipulateurs de chemin.</span><span class="sxs-lookup"><span data-stu-id="2548d-213">Use them as you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

<span data-ttu-id="2548d-214">Le `Test-Path` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2548d-214">The `Test-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2548d-215">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="2548d-215">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="2548d-216">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2548d-216">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2548d-217">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2548d-217">RELATED LINKS</span></span>

[<span data-ttu-id="2548d-218">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="2548d-218">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="2548d-219">Join-Path</span><span class="sxs-lookup"><span data-stu-id="2548d-219">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="2548d-220">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="2548d-220">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="2548d-221">Split-Path</span><span class="sxs-lookup"><span data-stu-id="2548d-221">Split-Path</span></span>](Split-Path.md)
