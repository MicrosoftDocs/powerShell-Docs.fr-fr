---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3ef54618e065a5fca3d52415897b3042d6ba4c65
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603686"
---
# <span data-ttu-id="4f61e-102">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="4f61e-102">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="4f61e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4f61e-103">SYNOPSIS</span></span>
<span data-ttu-id="4f61e-104">Crée un fichier qui définit un ensemble de fonctionnalités à exposer par le biais d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-104">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="4f61e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4f61e-105">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="4f61e-106">Description</span><span class="sxs-lookup"><span data-stu-id="4f61e-106">DESCRIPTION</span></span>

<span data-ttu-id="4f61e-107">L' `New-PSRoleCapabilityFile` applet de commande crée un fichier qui définit un ensemble de fonctionnalités utilisateur qui peuvent être exposées par le biais de fichiers de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-107">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="4f61e-108">Cela comprend la détermination des applets de commande, des fonctions et des scripts disponibles pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4f61e-108">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="4f61e-109">Le fichier de capacité est un fichier texte lisible qui contient une table de hachage des propriétés et des valeurs de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-109">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="4f61e-110">Le fichier a une extension de nom de fichier. PSRC et peut être utilisé par plusieurs configurations de session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-110">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="4f61e-111">Tous les paramètres de `New-PSRoleCapabilityFile` sont facultatifs, à l’exception du paramètre **path** , qui spécifie le chemin d’accès au fichier pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="4f61e-111">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="4f61e-112">Si vous n’incluez pas de paramètre lorsque vous exécutez l’applet de commande, la clé correspondante dans le fichier de configuration de session est commentée, sauf indication contraire dans la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f61e-112">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="4f61e-113">Par exemple, si vous n’incluez pas le paramètre **AssembliesToLoad** , cette section du fichier de configuration de session est commentée.</span><span class="sxs-lookup"><span data-stu-id="4f61e-113">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="4f61e-114">Pour utiliser le fichier de capacité de rôle dans une configuration de session, placez d’abord le fichier dans un sous-dossier **RoleCapabilities** d’un dossier de module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="4f61e-114">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="4f61e-115">Ensuite, référencez le fichier par nom dans le champ **RoleDefinitions** dans un fichier de configuration de session PowerShell (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="4f61e-115">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="4f61e-116">Cette applet de commande a été introduite dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="4f61e-116">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="4f61e-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4f61e-117">EXAMPLES</span></span>

### <span data-ttu-id="4f61e-118">Exemple 1 : créer un fichier de capacité de rôle vide</span><span class="sxs-lookup"><span data-stu-id="4f61e-118">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="4f61e-119">Cet exemple crée un fichier de capacité de rôle qui utilise les valeurs par défaut (vides).</span><span class="sxs-lookup"><span data-stu-id="4f61e-119">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="4f61e-120">Le fichier peut ensuite être modifié dans un éditeur de texte pour modifier ces paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="4f61e-120">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="4f61e-121">Exemple 2 : créer un fichier de capacité de rôle permettant aux utilisateurs de redémarrer les services et tout ordinateur VDI</span><span class="sxs-lookup"><span data-stu-id="4f61e-121">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="4f61e-122">Cet exemple crée un exemple de fichier de capacité de rôle qui permet aux utilisateurs de redémarrer des services et des ordinateurs qui correspondent à un modèle de nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="4f61e-122">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="4f61e-123">Le filtrage de nom est défini en définissant le paramètre **ValidatePattern** sur l’expression régulière `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="4f61e-123">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## <span data-ttu-id="4f61e-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f61e-124">PARAMETERS</span></span>

### <span data-ttu-id="4f61e-125">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="4f61e-125">-AliasDefinitions</span></span>

<span data-ttu-id="4f61e-126">Ajoute les alias spécifiés aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-126">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="4f61e-127">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f61e-127">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="4f61e-128">Nom.</span><span class="sxs-lookup"><span data-stu-id="4f61e-128">Name.</span></span> <span data-ttu-id="4f61e-129">Nom de l'alias.</span><span class="sxs-lookup"><span data-stu-id="4f61e-129">Name of the alias.</span></span> <span data-ttu-id="4f61e-130">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-130">This key is required.</span></span>
- <span data-ttu-id="4f61e-131">Valeur.</span><span class="sxs-lookup"><span data-stu-id="4f61e-131">Value.</span></span> <span data-ttu-id="4f61e-132">Commande représentée par l'alias.</span><span class="sxs-lookup"><span data-stu-id="4f61e-132">The command that the alias represents.</span></span> <span data-ttu-id="4f61e-133">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-133">This key is required.</span></span>
- <span data-ttu-id="4f61e-134">Description.</span><span class="sxs-lookup"><span data-stu-id="4f61e-134">Description.</span></span> <span data-ttu-id="4f61e-135">Chaîne de texte qui décrit l'alias.</span><span class="sxs-lookup"><span data-stu-id="4f61e-135">A text string that describes the alias.</span></span> <span data-ttu-id="4f61e-136">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="4f61e-136">This key is optional.</span></span>
- <span data-ttu-id="4f61e-137">Options.</span><span class="sxs-lookup"><span data-stu-id="4f61e-137">Options.</span></span> <span data-ttu-id="4f61e-138">Options de l'alias.</span><span class="sxs-lookup"><span data-stu-id="4f61e-138">Alias options.</span></span> <span data-ttu-id="4f61e-139">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="4f61e-139">This key is optional.</span></span> <span data-ttu-id="4f61e-140">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="4f61e-140">The default value is None.</span></span> <span data-ttu-id="4f61e-141">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="4f61e-141">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="4f61e-142">Par exemple : `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="4f61e-142">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-143">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="4f61e-143">-AssembliesToLoad</span></span>

<span data-ttu-id="4f61e-144">Spécifie les assemblys à charger dans les sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-144">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-145">-Auteur</span><span class="sxs-lookup"><span data-stu-id="4f61e-145">-Author</span></span>

<span data-ttu-id="4f61e-146">Spécifie l’utilisateur qui a créé le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-146">Specifies the user that created the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-147">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="4f61e-147">-CompanyName</span></span>

<span data-ttu-id="4f61e-148">Identifie la société qui a créé le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-148">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="4f61e-149">La valeur par défaut est Unknown.</span><span class="sxs-lookup"><span data-stu-id="4f61e-149">The default value is Unknown.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-150">-Copyright</span><span class="sxs-lookup"><span data-stu-id="4f61e-150">-Copyright</span></span>

<span data-ttu-id="4f61e-151">Spécifie un copyright pour le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-151">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="4f61e-152">Si vous omettez ce paramètre, `New-PSRoleCapabilityFile` génère une déclaration de droits d’auteur à l’aide de la valeur du paramètre **auteur** .</span><span class="sxs-lookup"><span data-stu-id="4f61e-152">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-153">Description</span><span class="sxs-lookup"><span data-stu-id="4f61e-153">-Description</span></span>

<span data-ttu-id="4f61e-154">Spécifie une description pour le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-154">Specifies a description for the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-155">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="4f61e-155">-EnvironmentVariables</span></span>

<span data-ttu-id="4f61e-156">Spécifie les variables d’environnement pour les sessions qui exposent ce fichier de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-156">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="4f61e-157">Entrez une table de hachage dans laquelle les clés sont les noms des variables d'environnement, et les valeurs sont les valeurs des variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="4f61e-157">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="4f61e-158">Par exemple : `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="4f61e-158">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-159">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="4f61e-159">-FormatsToProcess</span></span>

<span data-ttu-id="4f61e-160">Spécifie les fichiers de mise en forme (. ps1xml) qui s’exécutent dans les sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-160">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="4f61e-161">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="4f61e-161">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-162">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="4f61e-162">-FunctionDefinitions</span></span>

<span data-ttu-id="4f61e-163">Ajoute les fonctions spécifiées aux sessions qui exposent la capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-163">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="4f61e-164">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f61e-164">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="4f61e-165">Nom.</span><span class="sxs-lookup"><span data-stu-id="4f61e-165">Name.</span></span> <span data-ttu-id="4f61e-166">Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="4f61e-166">Name of the function.</span></span> <span data-ttu-id="4f61e-167">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-167">This key is required.</span></span>
- <span data-ttu-id="4f61e-168">ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="4f61e-168">ScriptBlock.</span></span> <span data-ttu-id="4f61e-169">Corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="4f61e-169">Function body.</span></span> <span data-ttu-id="4f61e-170">Entrez un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="4f61e-170">Enter a script block.</span></span> <span data-ttu-id="4f61e-171">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-171">This key is required.</span></span>
- <span data-ttu-id="4f61e-172">Options.</span><span class="sxs-lookup"><span data-stu-id="4f61e-172">Options.</span></span> <span data-ttu-id="4f61e-173">Options de la fonction.</span><span class="sxs-lookup"><span data-stu-id="4f61e-173">Function options.</span></span> <span data-ttu-id="4f61e-174">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="4f61e-174">This key is optional.</span></span> <span data-ttu-id="4f61e-175">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="4f61e-175">The default value is None.</span></span> <span data-ttu-id="4f61e-176">Les valeurs acceptables pour ce paramètre sont les suivantes : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="4f61e-176">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="4f61e-177">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4f61e-177">For example:</span></span>

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-178">-Guid</span><span class="sxs-lookup"><span data-stu-id="4f61e-178">-Guid</span></span>

<span data-ttu-id="4f61e-179">Spécifie un identificateur unique pour le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-179">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="4f61e-180">Si vous omettez ce paramètre, `New-PSRoleCapabilityFile` génère un GUID pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="4f61e-180">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="4f61e-181">Pour créer un nouveau GUID dans PowerShell, tapez `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="4f61e-181">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-182">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="4f61e-182">-ModulesToImport</span></span>

<span data-ttu-id="4f61e-183">Spécifie les modules qui sont importés automatiquement dans des sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-183">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="4f61e-184">Par défaut, toutes les commandes dans les modules répertoriés sont visibles.</span><span class="sxs-lookup"><span data-stu-id="4f61e-184">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="4f61e-185">En cas d’utilisation avec **VisibleCmdlets** ou **VisibleFunctions**, les commandes visibles à partir des modules spécifiés peuvent être restreintes.</span><span class="sxs-lookup"><span data-stu-id="4f61e-185">When used with **VisibleCmdlets** or **VisibleFunctions**, the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="4f61e-186">Chaque module utilisé dans la valeur de ce paramètre peut être représenté par une chaîne ou par une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4f61e-186">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="4f61e-187">Une chaîne de module se compose uniquement du nom du module.</span><span class="sxs-lookup"><span data-stu-id="4f61e-187">A module string consists only of the name of the module.</span></span> <span data-ttu-id="4f61e-188">Une table de hachage de module peut inclure des clés **modulename**, **ModuleVersion** et **GUID** .</span><span class="sxs-lookup"><span data-stu-id="4f61e-188">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="4f61e-189">Seule la clé **ModuleName** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-189">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="4f61e-190">Par exemple, la valeur suivante se compose d'une chaîne et d'une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4f61e-190">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="4f61e-191">Toutes les combinaisons de chaînes et de tables de hachage, dans n'importe quel ordre, sont valides.</span><span class="sxs-lookup"><span data-stu-id="4f61e-191">Any combination of strings and hash tables, in any order, is valid.</span></span>

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-192">-Path</span><span class="sxs-lookup"><span data-stu-id="4f61e-192">-Path</span></span>

<span data-ttu-id="4f61e-193">Spécifie le chemin d’accès et le nom du fichier de capacité du rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-193">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="4f61e-194">Le fichier doit avoir une `.psrc` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="4f61e-194">The file must have a `.psrc` filename extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-195">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="4f61e-195">-ScriptsToProcess</span></span>

<span data-ttu-id="4f61e-196">Spécifie les scripts à ajouter aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-196">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="4f61e-197">Entrez le chemin d'accès et les noms de fichiers des scripts.</span><span class="sxs-lookup"><span data-stu-id="4f61e-197">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="4f61e-198">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="4f61e-198">The value of this parameter must be a full or absolute path of the script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-199">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="4f61e-199">-TypesToProcess</span></span>

<span data-ttu-id="4f61e-200">Spécifie les fichiers de type (. ps1xml) à ajouter aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-200">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="4f61e-201">Entrez les noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="4f61e-201">Enter the type filenames.</span></span> <span data-ttu-id="4f61e-202">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="4f61e-202">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-203">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="4f61e-203">-VariableDefinitions</span></span>

<span data-ttu-id="4f61e-204">Spécifie des variables à ajouter aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="4f61e-204">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="4f61e-205">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f61e-205">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="4f61e-206">Nom.</span><span class="sxs-lookup"><span data-stu-id="4f61e-206">Name.</span></span> <span data-ttu-id="4f61e-207">Nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="4f61e-207">Name of the variable.</span></span> <span data-ttu-id="4f61e-208">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-208">This key is required.</span></span>
- <span data-ttu-id="4f61e-209">Valeur.</span><span class="sxs-lookup"><span data-stu-id="4f61e-209">Value.</span></span> <span data-ttu-id="4f61e-210">Valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="4f61e-210">Variable value.</span></span> <span data-ttu-id="4f61e-211">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f61e-211">This key is required.</span></span>
- <span data-ttu-id="4f61e-212">Options.</span><span class="sxs-lookup"><span data-stu-id="4f61e-212">Options.</span></span> <span data-ttu-id="4f61e-213">Options de la variable.</span><span class="sxs-lookup"><span data-stu-id="4f61e-213">Variable options.</span></span> <span data-ttu-id="4f61e-214">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="4f61e-214">This key is optional.</span></span> <span data-ttu-id="4f61e-215">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="4f61e-215">The default value is None.</span></span> <span data-ttu-id="4f61e-216">Les valeurs acceptables pour ce paramètre sont les suivantes : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="4f61e-216">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="4f61e-217">Par exemple : `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="4f61e-217">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-218">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="4f61e-218">-VisibleAliases</span></span>

<span data-ttu-id="4f61e-219">Limite les alias de la session à ceux spécifiés dans la valeur de ce paramètre, ainsi qu’à tous les alias que vous définissez dans le paramètre **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="4f61e-219">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="4f61e-220">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4f61e-220">Wildcard characters are supported.</span></span>
<span data-ttu-id="4f61e-221">Par défaut, tous les alias définis par le moteur PowerShell et tous les alias que les modules exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-221">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="4f61e-222">Par exemple, pour limiter les alias disponibles à GM et GCM, utilisez la syntaxe suivante : `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="4f61e-222">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="4f61e-223">Lorsqu’un paramètre **visible** est inclus dans le fichier de capacité de rôle, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-223">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="4f61e-224">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="4f61e-224">-VisibleCmdlets</span></span>

<span data-ttu-id="4f61e-225">Limite les applets de commande de la session à celles spécifiées dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f61e-225">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="4f61e-226">Les caractères génériques et les noms de module qualifiés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4f61e-226">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="4f61e-227">Par défaut, toutes les applets de commande que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-227">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="4f61e-228">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-228">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="4f61e-229">Si aucun module dans **ModulesToImport** n’expose l’applet de commande, `New-PSRoleCapabilityFile` tente de charger le module approprié.</span><span class="sxs-lookup"><span data-stu-id="4f61e-229">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="4f61e-230">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-230">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4f61e-231">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="4f61e-231">-VisibleExternalCommands</span></span>

<span data-ttu-id="4f61e-232">Limite les fichiers binaires externes, les scripts et les commandes qui peuvent être exécutés dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f61e-232">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="4f61e-233">Par défaut, aucune commande externe n’est visible dans cette session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-233">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="4f61e-234">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-234">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f61e-235">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="4f61e-235">-VisibleFunctions</span></span>

<span data-ttu-id="4f61e-236">Limite les fonctions de la session à celles spécifiées dans la valeur de ce paramètre, ainsi qu’à toutes les fonctions que vous définissez dans le paramètre **FunctionDefinitions** .</span><span class="sxs-lookup"><span data-stu-id="4f61e-236">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="4f61e-237">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4f61e-237">Wildcard characters are supported.</span></span>

<span data-ttu-id="4f61e-238">Par défaut, toutes les fonctions exportées par les modules de la session sont visibles dans cette session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-238">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="4f61e-239">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-239">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="4f61e-240">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-240">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4f61e-241">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="4f61e-241">-VisibleProviders</span></span>

<span data-ttu-id="4f61e-242">Limite les fournisseurs PowerShell dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f61e-242">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="4f61e-243">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4f61e-243">Wildcard characters are supported.</span></span>

<span data-ttu-id="4f61e-244">Par défaut, tous les fournisseurs exportés par un module dans la session sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-244">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="4f61e-245">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-245">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="4f61e-246">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="4f61e-246">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="4f61e-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f61e-247">CommonParameters</span></span>

<span data-ttu-id="4f61e-248">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f61e-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f61e-249">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f61e-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f61e-250">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4f61e-250">INPUTS</span></span>

## <span data-ttu-id="4f61e-251">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4f61e-251">OUTPUTS</span></span>

## <span data-ttu-id="4f61e-252">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4f61e-252">NOTES</span></span>

## <span data-ttu-id="4f61e-253">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4f61e-253">RELATED LINKS</span></span>

[<span data-ttu-id="4f61e-254">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="4f61e-254">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="4f61e-255">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="4f61e-255">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)

