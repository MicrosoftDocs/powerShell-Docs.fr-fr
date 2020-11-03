---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 617deb71605462833c3ed816fb4391c88ccd2da8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204494"
---
# <span data-ttu-id="d5aee-103">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="d5aee-103">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="d5aee-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d5aee-104">SYNOPSIS</span></span>
<span data-ttu-id="d5aee-105">Crée un fichier qui définit un ensemble de fonctionnalités à exposer par le biais d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-105">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="d5aee-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5aee-106">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="d5aee-107">Description</span><span class="sxs-lookup"><span data-stu-id="d5aee-107">DESCRIPTION</span></span>

<span data-ttu-id="d5aee-108">L' `New-PSRoleCapabilityFile` applet de commande crée un fichier qui définit un ensemble de fonctionnalités utilisateur qui peuvent être exposées par le biais de fichiers de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-108">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="d5aee-109">Cela comprend la détermination des applets de commande, des fonctions et des scripts disponibles pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d5aee-109">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="d5aee-110">Le fichier de capacité est un fichier texte lisible qui contient une table de hachage des propriétés et des valeurs de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-110">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="d5aee-111">Le fichier a une extension de nom de fichier. PSRC et peut être utilisé par plusieurs configurations de session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-111">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="d5aee-112">Tous les paramètres de `New-PSRoleCapabilityFile` sont facultatifs, à l’exception du paramètre **path** , qui spécifie le chemin d’accès au fichier pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="d5aee-112">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="d5aee-113">Si vous n’incluez pas de paramètre lorsque vous exécutez l’applet de commande, la clé correspondante dans le fichier de configuration de session est commentée, sauf indication contraire dans la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="d5aee-113">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="d5aee-114">Par exemple, si vous n’incluez pas le paramètre **AssembliesToLoad** , cette section du fichier de configuration de session est commentée.</span><span class="sxs-lookup"><span data-stu-id="d5aee-114">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="d5aee-115">Pour utiliser le fichier de capacité de rôle dans une configuration de session, placez d’abord le fichier dans un sous-dossier **RoleCapabilities** d’un dossier de module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="d5aee-115">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="d5aee-116">Ensuite, référencez le fichier par nom dans le champ **RoleDefinitions** dans un fichier de configuration de session PowerShell (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="d5aee-116">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="d5aee-117">Cette applet de commande a été introduite dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="d5aee-117">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="d5aee-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d5aee-118">EXAMPLES</span></span>

### <span data-ttu-id="d5aee-119">Exemple 1 : créer un fichier de capacité de rôle vide</span><span class="sxs-lookup"><span data-stu-id="d5aee-119">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="d5aee-120">Cet exemple crée un fichier de capacité de rôle qui utilise les valeurs par défaut (vides).</span><span class="sxs-lookup"><span data-stu-id="d5aee-120">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="d5aee-121">Le fichier peut ensuite être modifié dans un éditeur de texte pour modifier ces paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="d5aee-121">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="d5aee-122">Exemple 2 : créer un fichier de capacité de rôle permettant aux utilisateurs de redémarrer les services et tout ordinateur VDI</span><span class="sxs-lookup"><span data-stu-id="d5aee-122">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="d5aee-123">Cet exemple crée un exemple de fichier de capacité de rôle qui permet aux utilisateurs de redémarrer des services et des ordinateurs qui correspondent à un modèle de nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="d5aee-123">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="d5aee-124">Le filtrage de nom est défini en définissant le paramètre **ValidatePattern** sur l’expression régulière `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="d5aee-124">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

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

## <span data-ttu-id="d5aee-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5aee-125">PARAMETERS</span></span>

### <span data-ttu-id="d5aee-126">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="d5aee-126">-AliasDefinitions</span></span>

<span data-ttu-id="d5aee-127">Ajoute les alias spécifiés aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-127">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="d5aee-128">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5aee-128">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="d5aee-129">Nom.</span><span class="sxs-lookup"><span data-stu-id="d5aee-129">Name.</span></span> <span data-ttu-id="d5aee-130">Nom de l'alias.</span><span class="sxs-lookup"><span data-stu-id="d5aee-130">Name of the alias.</span></span> <span data-ttu-id="d5aee-131">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-131">This key is required.</span></span>
- <span data-ttu-id="d5aee-132">Valeur.</span><span class="sxs-lookup"><span data-stu-id="d5aee-132">Value.</span></span> <span data-ttu-id="d5aee-133">Commande représentée par l'alias.</span><span class="sxs-lookup"><span data-stu-id="d5aee-133">The command that the alias represents.</span></span> <span data-ttu-id="d5aee-134">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-134">This key is required.</span></span>
- <span data-ttu-id="d5aee-135">Description.</span><span class="sxs-lookup"><span data-stu-id="d5aee-135">Description.</span></span> <span data-ttu-id="d5aee-136">Chaîne de texte qui décrit l'alias.</span><span class="sxs-lookup"><span data-stu-id="d5aee-136">A text string that describes the alias.</span></span> <span data-ttu-id="d5aee-137">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="d5aee-137">This key is optional.</span></span>
- <span data-ttu-id="d5aee-138">Options.</span><span class="sxs-lookup"><span data-stu-id="d5aee-138">Options.</span></span> <span data-ttu-id="d5aee-139">Options de l'alias.</span><span class="sxs-lookup"><span data-stu-id="d5aee-139">Alias options.</span></span> <span data-ttu-id="d5aee-140">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="d5aee-140">This key is optional.</span></span> <span data-ttu-id="d5aee-141">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="d5aee-141">The default value is None.</span></span> <span data-ttu-id="d5aee-142">Les valeurs acceptables pour ce paramètre sont : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="d5aee-142">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="d5aee-143">Par exemple : `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="d5aee-143">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

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

### <span data-ttu-id="d5aee-144">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="d5aee-144">-AssembliesToLoad</span></span>

<span data-ttu-id="d5aee-145">Spécifie les assemblys à charger dans les sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-145">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

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

### <span data-ttu-id="d5aee-146">-Auteur</span><span class="sxs-lookup"><span data-stu-id="d5aee-146">-Author</span></span>

<span data-ttu-id="d5aee-147">Spécifie l’utilisateur qui a créé le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-147">Specifies the user that created the role capability file.</span></span>

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

### <span data-ttu-id="d5aee-148">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="d5aee-148">-CompanyName</span></span>

<span data-ttu-id="d5aee-149">Identifie la société qui a créé le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-149">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="d5aee-150">La valeur par défaut est Unknown.</span><span class="sxs-lookup"><span data-stu-id="d5aee-150">The default value is Unknown.</span></span>

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

### <span data-ttu-id="d5aee-151">-Copyright</span><span class="sxs-lookup"><span data-stu-id="d5aee-151">-Copyright</span></span>

<span data-ttu-id="d5aee-152">Spécifie un copyright pour le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-152">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="d5aee-153">Si vous omettez ce paramètre, `New-PSRoleCapabilityFile` génère une déclaration de droits d’auteur à l’aide de la valeur du paramètre **auteur** .</span><span class="sxs-lookup"><span data-stu-id="d5aee-153">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="d5aee-154">Description</span><span class="sxs-lookup"><span data-stu-id="d5aee-154">-Description</span></span>

<span data-ttu-id="d5aee-155">Spécifie une description pour le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-155">Specifies a description for the role capability file.</span></span>

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

### <span data-ttu-id="d5aee-156">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="d5aee-156">-EnvironmentVariables</span></span>

<span data-ttu-id="d5aee-157">Spécifie les variables d’environnement pour les sessions qui exposent ce fichier de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-157">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="d5aee-158">Entrez une table de hachage dans laquelle les clés sont les noms des variables d'environnement, et les valeurs sont les valeurs des variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="d5aee-158">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="d5aee-159">Par exemple : `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="d5aee-159">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

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

### <span data-ttu-id="d5aee-160">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="d5aee-160">-FormatsToProcess</span></span>

<span data-ttu-id="d5aee-161">Spécifie les fichiers de mise en forme (. ps1xml) qui s’exécutent dans les sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-161">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="d5aee-162">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d5aee-162">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="d5aee-163">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="d5aee-163">-FunctionDefinitions</span></span>

<span data-ttu-id="d5aee-164">Ajoute les fonctions spécifiées aux sessions qui exposent la capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-164">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="d5aee-165">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5aee-165">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="d5aee-166">Nom.</span><span class="sxs-lookup"><span data-stu-id="d5aee-166">Name.</span></span> <span data-ttu-id="d5aee-167">Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d5aee-167">Name of the function.</span></span> <span data-ttu-id="d5aee-168">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-168">This key is required.</span></span>
- <span data-ttu-id="d5aee-169">ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="d5aee-169">ScriptBlock.</span></span> <span data-ttu-id="d5aee-170">Corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d5aee-170">Function body.</span></span> <span data-ttu-id="d5aee-171">Entrez un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="d5aee-171">Enter a script block.</span></span> <span data-ttu-id="d5aee-172">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-172">This key is required.</span></span>
- <span data-ttu-id="d5aee-173">Options.</span><span class="sxs-lookup"><span data-stu-id="d5aee-173">Options.</span></span> <span data-ttu-id="d5aee-174">Options de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d5aee-174">Function options.</span></span> <span data-ttu-id="d5aee-175">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="d5aee-175">This key is optional.</span></span> <span data-ttu-id="d5aee-176">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="d5aee-176">The default value is None.</span></span> <span data-ttu-id="d5aee-177">Les valeurs acceptables pour ce paramètre sont les suivantes : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="d5aee-177">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="d5aee-178">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d5aee-178">For example:</span></span>

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

### <span data-ttu-id="d5aee-179">-Guid</span><span class="sxs-lookup"><span data-stu-id="d5aee-179">-Guid</span></span>

<span data-ttu-id="d5aee-180">Spécifie un identificateur unique pour le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-180">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="d5aee-181">Si vous omettez ce paramètre, `New-PSRoleCapabilityFile` génère un GUID pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="d5aee-181">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="d5aee-182">Pour créer un nouveau GUID dans PowerShell, tapez `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="d5aee-182">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="d5aee-183">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="d5aee-183">-ModulesToImport</span></span>

<span data-ttu-id="d5aee-184">Spécifie les modules qui sont importés automatiquement dans des sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-184">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="d5aee-185">Par défaut, toutes les commandes dans les modules répertoriés sont visibles.</span><span class="sxs-lookup"><span data-stu-id="d5aee-185">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="d5aee-186">En cas d’utilisation avec **VisibleCmdlets** ou **VisibleFunctions** , les commandes visibles à partir des modules spécifiés peuvent être restreintes.</span><span class="sxs-lookup"><span data-stu-id="d5aee-186">When used with **VisibleCmdlets** or **VisibleFunctions** , the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="d5aee-187">Chaque module utilisé dans la valeur de ce paramètre peut être représenté par une chaîne ou par une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="d5aee-187">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="d5aee-188">Une chaîne de module se compose uniquement du nom du module.</span><span class="sxs-lookup"><span data-stu-id="d5aee-188">A module string consists only of the name of the module.</span></span> <span data-ttu-id="d5aee-189">Une table de hachage de module peut inclure des clés **modulename** , **ModuleVersion** et **GUID** .</span><span class="sxs-lookup"><span data-stu-id="d5aee-189">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="d5aee-190">Seule la clé **ModuleName** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-190">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="d5aee-191">Par exemple, la valeur suivante se compose d'une chaîne et d'une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="d5aee-191">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="d5aee-192">Toutes les combinaisons de chaînes et de tables de hachage, dans n'importe quel ordre, sont valides.</span><span class="sxs-lookup"><span data-stu-id="d5aee-192">Any combination of strings and hash tables, in any order, is valid.</span></span>

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

### <span data-ttu-id="d5aee-193">-Path</span><span class="sxs-lookup"><span data-stu-id="d5aee-193">-Path</span></span>

<span data-ttu-id="d5aee-194">Spécifie le chemin d’accès et le nom du fichier de capacité du rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-194">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="d5aee-195">Le fichier doit avoir une `.psrc` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="d5aee-195">The file must have a `.psrc` filename extension.</span></span>

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

### <span data-ttu-id="d5aee-196">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="d5aee-196">-ScriptsToProcess</span></span>

<span data-ttu-id="d5aee-197">Spécifie les scripts à ajouter aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-197">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="d5aee-198">Entrez le chemin d'accès et les noms de fichiers des scripts.</span><span class="sxs-lookup"><span data-stu-id="d5aee-198">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="d5aee-199">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="d5aee-199">The value of this parameter must be a full or absolute path of the script file names.</span></span>

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

### <span data-ttu-id="d5aee-200">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="d5aee-200">-TypesToProcess</span></span>

<span data-ttu-id="d5aee-201">Spécifie les fichiers de type (. ps1xml) à ajouter aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-201">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="d5aee-202">Entrez les noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="d5aee-202">Enter the type filenames.</span></span> <span data-ttu-id="d5aee-203">La valeur de ce paramètre doit être un chemin d’accès complet ou absolu des noms de fichiers de type.</span><span class="sxs-lookup"><span data-stu-id="d5aee-203">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

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

### <span data-ttu-id="d5aee-204">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="d5aee-204">-VariableDefinitions</span></span>

<span data-ttu-id="d5aee-205">Spécifie des variables à ajouter aux sessions qui utilisent le fichier de capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d5aee-205">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="d5aee-206">Entrez une table de hachage avec les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5aee-206">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="d5aee-207">Nom.</span><span class="sxs-lookup"><span data-stu-id="d5aee-207">Name.</span></span> <span data-ttu-id="d5aee-208">Nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="d5aee-208">Name of the variable.</span></span> <span data-ttu-id="d5aee-209">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-209">This key is required.</span></span>
- <span data-ttu-id="d5aee-210">Valeur.</span><span class="sxs-lookup"><span data-stu-id="d5aee-210">Value.</span></span> <span data-ttu-id="d5aee-211">Valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="d5aee-211">Variable value.</span></span> <span data-ttu-id="d5aee-212">Cette clé est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d5aee-212">This key is required.</span></span>
- <span data-ttu-id="d5aee-213">Options.</span><span class="sxs-lookup"><span data-stu-id="d5aee-213">Options.</span></span> <span data-ttu-id="d5aee-214">Options de la variable.</span><span class="sxs-lookup"><span data-stu-id="d5aee-214">Variable options.</span></span> <span data-ttu-id="d5aee-215">Cette clé est facultative.</span><span class="sxs-lookup"><span data-stu-id="d5aee-215">This key is optional.</span></span> <span data-ttu-id="d5aee-216">La valeur par défaut est Aucun.</span><span class="sxs-lookup"><span data-stu-id="d5aee-216">The default value is None.</span></span> <span data-ttu-id="d5aee-217">Les valeurs acceptables pour ce paramètre sont les suivantes : None, ReadOnly, constant, Private ou options AllScope.</span><span class="sxs-lookup"><span data-stu-id="d5aee-217">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="d5aee-218">Par exemple : `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="d5aee-218">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

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

### <span data-ttu-id="d5aee-219">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="d5aee-219">-VisibleAliases</span></span>

<span data-ttu-id="d5aee-220">Limite les alias de la session à ceux spécifiés dans la valeur de ce paramètre, ainsi qu’à tous les alias que vous définissez dans le paramètre **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="d5aee-220">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="d5aee-221">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d5aee-221">Wildcard characters are supported.</span></span>
<span data-ttu-id="d5aee-222">Par défaut, tous les alias définis par le moteur PowerShell et tous les alias que les modules exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-222">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="d5aee-223">Par exemple, pour limiter les alias disponibles à GM et GCM, utilisez la syntaxe suivante : `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="d5aee-223">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="d5aee-224">Lorsqu’un paramètre **visible** est inclus dans le fichier de capacité de rôle, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-224">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="d5aee-225">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="d5aee-225">-VisibleCmdlets</span></span>

<span data-ttu-id="d5aee-226">Limite les applets de commande de la session à celles spécifiées dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d5aee-226">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="d5aee-227">Les caractères génériques et les noms de module qualifiés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d5aee-227">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="d5aee-228">Par défaut, toutes les applets de commande que les modules de la session exportent sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-228">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="d5aee-229">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer quels modules et composants logiciels enfichables sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-229">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="d5aee-230">Si aucun module dans **ModulesToImport** n’expose l’applet de commande, `New-PSRoleCapabilityFile` tente de charger le module approprié.</span><span class="sxs-lookup"><span data-stu-id="d5aee-230">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="d5aee-231">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-231">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="d5aee-232">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="d5aee-232">-VisibleExternalCommands</span></span>

<span data-ttu-id="d5aee-233">Limite les fichiers binaires externes, les scripts et les commandes qui peuvent être exécutés dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d5aee-233">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="d5aee-234">Par défaut, aucune commande externe n’est visible dans cette session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-234">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="d5aee-235">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-235">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="d5aee-236">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="d5aee-236">-VisibleFunctions</span></span>

<span data-ttu-id="d5aee-237">Limite les fonctions de la session à celles spécifiées dans la valeur de ce paramètre, ainsi qu’à toutes les fonctions que vous définissez dans le paramètre **FunctionDefinitions** .</span><span class="sxs-lookup"><span data-stu-id="d5aee-237">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="d5aee-238">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d5aee-238">Wildcard characters are supported.</span></span>

<span data-ttu-id="d5aee-239">Par défaut, toutes les fonctions exportées par les modules de la session sont visibles dans cette session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-239">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="d5aee-240">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-240">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="d5aee-241">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-241">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="d5aee-242">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="d5aee-242">-VisibleProviders</span></span>

<span data-ttu-id="d5aee-243">Limite les fournisseurs PowerShell dans la session à ceux spécifiés dans la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d5aee-243">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="d5aee-244">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d5aee-244">Wildcard characters are supported.</span></span>

<span data-ttu-id="d5aee-245">Par défaut, tous les fournisseurs exportés par un module dans la session sont visibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-245">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="d5aee-246">Utilisez les paramètres **SessionType** et **ModulesToImport** pour déterminer les modules qui sont importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-246">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="d5aee-247">Quand un paramètre **visible** est inclus dans le fichier de configuration de session, PowerShell supprime l' `Import-Module` applet de commande et son `ipmo` alias de la session.</span><span class="sxs-lookup"><span data-stu-id="d5aee-247">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="d5aee-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5aee-248">CommonParameters</span></span>

<span data-ttu-id="d5aee-249">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d5aee-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5aee-250">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d5aee-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5aee-251">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d5aee-251">INPUTS</span></span>

## <span data-ttu-id="d5aee-252">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d5aee-252">OUTPUTS</span></span>

## <span data-ttu-id="d5aee-253">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d5aee-253">NOTES</span></span>

## <span data-ttu-id="d5aee-254">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d5aee-254">RELATED LINKS</span></span>

[<span data-ttu-id="d5aee-255">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="d5aee-255">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="d5aee-256">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="d5aee-256">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)
