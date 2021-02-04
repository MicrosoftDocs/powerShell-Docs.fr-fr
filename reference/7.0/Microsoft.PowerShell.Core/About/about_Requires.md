---
description: Empêche un script de s’exécuter sans les éléments requis.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: 73c225f493fb671b34925d0127cc0d5cff0ab33e
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490582"
---
# <a name="about-requires"></a><span data-ttu-id="c940f-103">À propos de requires</span><span class="sxs-lookup"><span data-stu-id="c940f-103">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="c940f-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="c940f-104">Short description</span></span>
<span data-ttu-id="c940f-105">Empêche un script de s’exécuter sans les éléments requis.</span><span class="sxs-lookup"><span data-stu-id="c940f-105">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="c940f-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="c940f-106">Long description</span></span>

<span data-ttu-id="c940f-107">L' `#Requires` instruction empêche l’exécution d’un script, sauf si la version, les modules (et la version), les composants logiciels enfichables (et la version) et les composants logiciels enfichables de l’édition de PowerShell sont satisfaits.</span><span class="sxs-lookup"><span data-stu-id="c940f-107">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="c940f-108">Si les conditions préalables ne sont pas remplies, PowerShell n’exécute pas le script.</span><span class="sxs-lookup"><span data-stu-id="c940f-108">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="c940f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c940f-109">Syntax</span></span>

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="c940f-110">Pour plus d’informations sur la syntaxe, consultez [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span><span class="sxs-lookup"><span data-stu-id="c940f-110">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="c940f-111">Règles d’utilisation</span><span class="sxs-lookup"><span data-stu-id="c940f-111">Rules for use</span></span>

<span data-ttu-id="c940f-112">Un script peut inclure plusieurs `#Requires` instructions.</span><span class="sxs-lookup"><span data-stu-id="c940f-112">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="c940f-113">Les `#Requires` instructions peuvent apparaître sur n’importe quelle ligne dans un script.</span><span class="sxs-lookup"><span data-stu-id="c940f-113">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="c940f-114">Le fait de placer une `#Requires` instruction à l’intérieur d’une fonction ne limite pas son étendue.</span><span class="sxs-lookup"><span data-stu-id="c940f-114">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="c940f-115">Toutes les `#Requires` instructions sont toujours appliquées globalement et doivent être respectées avant que le script puisse s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="c940f-115">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="c940f-116">Bien qu’une `#Requires` instruction puisse apparaître sur n’importe quelle ligne d’un script, sa position dans un script n’affecte pas la séquence de son application.</span><span class="sxs-lookup"><span data-stu-id="c940f-116">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="c940f-117">L’état global `#Requires` que l’instruction présente doit être respecté avant l’exécution du script.</span><span class="sxs-lookup"><span data-stu-id="c940f-117">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="c940f-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-118">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="c940f-119">Vous pouvez penser que le code ci-dessus ne doit pas s’exécuter parce que le module requis a été supprimé avant l' `#Requires` instruction.</span><span class="sxs-lookup"><span data-stu-id="c940f-119">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="c940f-120">Toutefois, l' `#Requires` État devait être respecté pour que le script puisse même s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="c940f-120">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="c940f-121">La première ligne du script n’a pas validé l’État requis.</span><span class="sxs-lookup"><span data-stu-id="c940f-121">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="c940f-122">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c940f-122">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="c940f-123">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="c940f-123">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

> [!IMPORTANT]
> <span data-ttu-id="c940f-124">La `-Assembly` syntaxe est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c940f-124">The `-Assembly` syntax is deprecated.</span></span> <span data-ttu-id="c940f-125">Elle n’a aucune fonction.</span><span class="sxs-lookup"><span data-stu-id="c940f-125">It serves no function.</span></span> <span data-ttu-id="c940f-126">La syntaxe a été ajoutée dans PowerShell 5,1, mais le code de prise en charge n’a jamais été implémenté.</span><span class="sxs-lookup"><span data-stu-id="c940f-126">The syntax was added in PowerShell 5.1 but the supporting code was never implemented.</span></span> <span data-ttu-id="c940f-127">La syntaxe est toujours acceptée pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="c940f-127">The syntax is still accepted for backward compatibility.</span></span>

<span data-ttu-id="c940f-128">Spécifie le chemin d’accès au fichier DLL de l’assembly ou un nom d’assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="c940f-128">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="c940f-129">Le paramètre **assembly** a été introduit dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="c940f-129">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="c940f-130">Pour plus d’informations sur les assemblys .NET, consultez [noms d’assembly](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="c940f-130">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="c940f-131">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-131">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="c940f-132">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="c940f-132">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="c940f-133">Spécifie la version minimale de PowerShell requise par le script.</span><span class="sxs-lookup"><span data-stu-id="c940f-133">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="c940f-134">Entrez un numéro de version principale et un numéro de version mineure facultatif.</span><span class="sxs-lookup"><span data-stu-id="c940f-134">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="c940f-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-135">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="c940f-136">-PSSnapin \<PSSnapin-Name\> [-version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="c940f-136">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="c940f-137">Spécifie un composant logiciel enfichable PowerShell requis par le script.</span><span class="sxs-lookup"><span data-stu-id="c940f-137">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="c940f-138">Entrez le nom du composant logiciel enfichable et un numéro de version facultatif.</span><span class="sxs-lookup"><span data-stu-id="c940f-138">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="c940f-139">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-139">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="c940f-140">-Modules \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="c940f-140">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="c940f-141">Spécifie les modules PowerShell requis par le script.</span><span class="sxs-lookup"><span data-stu-id="c940f-141">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="c940f-142">Entrez le nom du module et un numéro de version facultatif.</span><span class="sxs-lookup"><span data-stu-id="c940f-142">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="c940f-143">Si les modules requis ne se trouvent pas dans la session active, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="c940f-143">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="c940f-144">Si les modules ne peuvent pas être importés, PowerShell lève une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="c940f-144">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="c940f-145">Pour chaque module, tapez le nom du module ( \<String\> ) ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="c940f-145">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="c940f-146">La valeur peut être une combinaison de chaînes et de tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="c940f-146">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="c940f-147">La table de hachage a les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="c940f-147">The hash table has the following keys.</span></span>

- <span data-ttu-id="c940f-148">`ModuleName` - **Obligatoire** Spécifie le nom du module.</span><span class="sxs-lookup"><span data-stu-id="c940f-148">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="c940f-149">`GUID` - **Facultatif** Spécifie le GUID du module.</span><span class="sxs-lookup"><span data-stu-id="c940f-149">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="c940f-150">Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c940f-150">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="c940f-151">Ces clés ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="c940f-151">These keys can't be used together.</span></span>
  - <span data-ttu-id="c940f-152">`ModuleVersion` -Spécifie une version minimale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="c940f-152">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="c940f-153">`RequiredVersion` -Spécifie une version exacte et obligatoire du module.</span><span class="sxs-lookup"><span data-stu-id="c940f-153">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="c940f-154">`MaximumVersion` -Spécifie la version maximale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="c940f-154">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="c940f-155">`RequiredVersion` a été ajouté dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="c940f-155">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="c940f-156">`MaximumVersion` a été ajouté dans Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="c940f-156">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="c940f-157">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-157">For example:</span></span>

<span data-ttu-id="c940f-158">Exiger que `AzureRM.Netcore` (version `0.12.0` ou ultérieure) soit installé.</span><span class="sxs-lookup"><span data-stu-id="c940f-158">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="c940f-159">Exiger que `AzureRM.Netcore` (**seule** version `0.12.0` ) soit installé.</span><span class="sxs-lookup"><span data-stu-id="c940f-159">Require that `AzureRM.Netcore` (**only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="c940f-160">Requiert l' `AzureRM.Netcore` installation de (version `0.12.0` ou inférieure).</span><span class="sxs-lookup"><span data-stu-id="c940f-160">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="c940f-161">Exiger que toutes les versions de `AzureRM.Netcore` et de `PowerShellGet` soient installées.</span><span class="sxs-lookup"><span data-stu-id="c940f-161">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="c940f-162">Lorsque vous utilisez la `RequiredVersion` clé, vérifiez que votre chaîne de version correspond exactement à la chaîne de version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c940f-162">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="c940f-163">L’exemple suivant échoue car **0,12** ne correspond pas exactement à **0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="c940f-163">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="c940f-164">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="c940f-164">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="c940f-165">Spécifie une édition PowerShell dont le script a besoin.</span><span class="sxs-lookup"><span data-stu-id="c940f-165">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="c940f-166">Les valeurs valides sont **Core** pour PowerShell Core et **Desktop** pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c940f-166">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="c940f-167">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-167">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="c940f-168">-ShellId</span><span class="sxs-lookup"><span data-stu-id="c940f-168">-ShellId</span></span>

<span data-ttu-id="c940f-169">Spécifie l’interpréteur de commandes requis par le script.</span><span class="sxs-lookup"><span data-stu-id="c940f-169">Specifies the shell that the script requires.</span></span> <span data-ttu-id="c940f-170">Entrez l’ID de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="c940f-170">Enter the shell ID.</span></span> <span data-ttu-id="c940f-171">Si vous utilisez le paramètre **ShellId** , vous devez également inclure le paramètre **PSSnapin** .</span><span class="sxs-lookup"><span data-stu-id="c940f-171">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="c940f-172">Vous pouvez rechercher le **ShellId** en cours en interrogeant la `$ShellId` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="c940f-172">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="c940f-173">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-173">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="c940f-174">Ce paramètre est destiné à être utilisé dans les mini-shells, qui ont été dépréciés.</span><span class="sxs-lookup"><span data-stu-id="c940f-174">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="c940f-175">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="c940f-175">-RunAsAdministrator</span></span>

<span data-ttu-id="c940f-176">Lorsque ce paramètre de commutateur est ajouté à votre `#Requires` instruction, il spécifie que la session PowerShell dans laquelle vous exécutez le script doit être démarrée avec des droits d’utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="c940f-176">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="c940f-177">Le paramètre **RunAsAdministrator** est ignoré sur un système d’exploitation autre que Windows.</span><span class="sxs-lookup"><span data-stu-id="c940f-177">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="c940f-178">Le paramètre **RunAsAdministrator** a été introduit dans PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="c940f-178">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="c940f-179">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c940f-179">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="c940f-180">Exemples</span><span class="sxs-lookup"><span data-stu-id="c940f-180">Examples</span></span>

<span data-ttu-id="c940f-181">Le script suivant comporte deux `#Requires` instructions.</span><span class="sxs-lookup"><span data-stu-id="c940f-181">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="c940f-182">Si les exigences spécifiées dans les deux instructions ne sont pas satisfaites, le script ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="c940f-182">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="c940f-183">Chaque `#Requires` instruction doit être le premier élément d’une ligne :</span><span class="sxs-lookup"><span data-stu-id="c940f-183">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="c940f-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c940f-184">See also</span></span>

[<span data-ttu-id="c940f-185">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="c940f-185">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="c940f-186">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="c940f-186">about_Language_Keywords</span></span>](about_Language_Keywords.md)
