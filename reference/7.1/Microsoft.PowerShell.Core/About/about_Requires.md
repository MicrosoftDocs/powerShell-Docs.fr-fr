---
description: Empêche un script de s’exécuter sans les éléments requis.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: 5c4eb4e272f214ffe906fd1a3f1c127824183d4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208258"
---
# <a name="about-requires"></a><span data-ttu-id="5f8c5-104">À propos de requires</span><span class="sxs-lookup"><span data-stu-id="5f8c5-104">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="5f8c5-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="5f8c5-105">Short description</span></span>
<span data-ttu-id="5f8c5-106">Empêche un script de s’exécuter sans les éléments requis.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-106">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="5f8c5-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="5f8c5-107">Long description</span></span>

<span data-ttu-id="5f8c5-108">L' `#Requires` instruction empêche l’exécution d’un script, sauf si la version, les modules (et la version), les composants logiciels enfichables (et la version) et les composants logiciels enfichables de l’édition de PowerShell sont satisfaits.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-108">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="5f8c5-109">Si les conditions préalables ne sont pas remplies, PowerShell n’exécute pas le script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-109">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="5f8c5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f8c5-110">Syntax</span></span>

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="5f8c5-111">Pour plus d’informations sur la syntaxe, consultez [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span><span class="sxs-lookup"><span data-stu-id="5f8c5-111">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="5f8c5-112">Règles d’utilisation</span><span class="sxs-lookup"><span data-stu-id="5f8c5-112">Rules for use</span></span>

<span data-ttu-id="5f8c5-113">Un script peut inclure plusieurs `#Requires` instructions.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-113">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="5f8c5-114">Les `#Requires` instructions peuvent apparaître sur n’importe quelle ligne dans un script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-114">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="5f8c5-115">Le fait de placer une `#Requires` instruction à l’intérieur d’une fonction ne limite pas son étendue.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-115">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="5f8c5-116">Toutes les `#Requires` instructions sont toujours appliquées globalement et doivent être respectées avant que le script puisse s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-116">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="5f8c5-117">Bien qu’une `#Requires` instruction puisse apparaître sur n’importe quelle ligne d’un script, sa position dans un script n’affecte pas la séquence de son application.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-117">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="5f8c5-118">L’état global `#Requires` que l’instruction présente doit être respecté avant l’exécution du script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-118">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="5f8c5-119">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-119">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="5f8c5-120">Vous pouvez penser que le code ci-dessus ne doit pas s’exécuter parce que le module requis a été supprimé avant l' `#Requires` instruction.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-120">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="5f8c5-121">Toutefois, l' `#Requires` État devait être respecté pour que le script puisse même s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-121">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="5f8c5-122">La première ligne du script n’a pas validé l’État requis.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-122">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="5f8c5-123">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5f8c5-123">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="5f8c5-124">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="5f8c5-124">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

<span data-ttu-id="5f8c5-125">Spécifie le chemin d’accès au fichier DLL de l’assembly ou un nom d’assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-125">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="5f8c5-126">Le paramètre **assembly** a été introduit dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-126">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="5f8c5-127">Pour plus d’informations sur les assemblys .NET, consultez [noms d’assembly](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="5f8c5-127">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="5f8c5-128">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-128">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="5f8c5-129">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="5f8c5-129">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="5f8c5-130">Spécifie la version minimale de PowerShell requise par le script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-130">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="5f8c5-131">Entrez un numéro de version principale et un numéro de version mineure facultatif.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-131">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="5f8c5-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-132">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="5f8c5-133">-PSSnapin \<PSSnapin-Name\> [-version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="5f8c5-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="5f8c5-134">Spécifie un composant logiciel enfichable PowerShell requis par le script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-134">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="5f8c5-135">Entrez le nom du composant logiciel enfichable et un numéro de version facultatif.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-135">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="5f8c5-136">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-136">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="5f8c5-137">-Modules \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="5f8c5-137">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="5f8c5-138">Spécifie les modules PowerShell requis par le script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-138">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="5f8c5-139">Entrez le nom du module et un numéro de version facultatif.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-139">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="5f8c5-140">Si les modules requis ne se trouvent pas dans la session active, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-140">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="5f8c5-141">Si les modules ne peuvent pas être importés, PowerShell lève une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-141">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="5f8c5-142">Pour chaque module, tapez le nom du module ( \<String\> ) ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-142">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="5f8c5-143">La valeur peut être une combinaison de chaînes et de tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-143">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="5f8c5-144">La table de hachage a les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-144">The hash table has the following keys.</span></span>

- <span data-ttu-id="5f8c5-145">`ModuleName` - **Obligatoire** Spécifie le nom du module.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-145">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="5f8c5-146">`GUID` - **Facultatif** Spécifie le GUID du module.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-146">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="5f8c5-147">Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-147">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="5f8c5-148">Ces clés ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-148">These keys can't be used together.</span></span>
  - <span data-ttu-id="5f8c5-149">`ModuleVersion` -Spécifie une version minimale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-149">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="5f8c5-150">`RequiredVersion` -Spécifie une version exacte et obligatoire du module.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-150">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="5f8c5-151">`MaximumVersion` -Spécifie la version maximale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-151">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="5f8c5-152">`RequiredVersion` a été ajouté dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-152">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="5f8c5-153">`MaximumVersion` a été ajouté dans Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-153">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="5f8c5-154">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-154">For example:</span></span>

<span data-ttu-id="5f8c5-155">Exiger que `AzureRM.Netcore` (version `0.12.0` ou ultérieure) soit installé.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-155">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="5f8c5-156">Exiger que `AzureRM.Netcore` ( **seule** version `0.12.0` ) soit installé.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-156">Require that `AzureRM.Netcore` ( **only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="5f8c5-157">Requiert l' `AzureRM.Netcore` installation de (version `0.12.0` ou inférieure).</span><span class="sxs-lookup"><span data-stu-id="5f8c5-157">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="5f8c5-158">Exiger que toutes les versions de `AzureRM.Netcore` et de `PowerShellGet` soient installées.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-158">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="5f8c5-159">Lorsque vous utilisez la `RequiredVersion` clé, vérifiez que votre chaîne de version correspond exactement à la chaîne de version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-159">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="5f8c5-160">L’exemple suivant échoue car **0,12** ne correspond pas exactement à **0.12.0** .</span><span class="sxs-lookup"><span data-stu-id="5f8c5-160">The following example fails because **0.12** doesn't exactly match **0.12.0** .</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="5f8c5-161">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="5f8c5-161">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="5f8c5-162">Spécifie une édition PowerShell dont le script a besoin.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-162">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="5f8c5-163">Les valeurs valides sont **Core** pour PowerShell Core et **Desktop** pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-163">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="5f8c5-164">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-164">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="5f8c5-165">-ShellId</span><span class="sxs-lookup"><span data-stu-id="5f8c5-165">-ShellId</span></span>

<span data-ttu-id="5f8c5-166">Spécifie l’interpréteur de commandes requis par le script.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-166">Specifies the shell that the script requires.</span></span> <span data-ttu-id="5f8c5-167">Entrez l’ID de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-167">Enter the shell ID.</span></span> <span data-ttu-id="5f8c5-168">Si vous utilisez le paramètre **ShellId** , vous devez également inclure le paramètre **PSSnapin** .</span><span class="sxs-lookup"><span data-stu-id="5f8c5-168">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="5f8c5-169">Vous pouvez rechercher le **ShellId** en cours en interrogeant la `$ShellId` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-169">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="5f8c5-170">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-170">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="5f8c5-171">Ce paramètre est destiné à être utilisé dans les mini-shells, qui ont été dépréciés.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-171">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="5f8c5-172">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="5f8c5-172">-RunAsAdministrator</span></span>

<span data-ttu-id="5f8c5-173">Lorsque ce paramètre de commutateur est ajouté à votre `#Requires` instruction, il spécifie que la session PowerShell dans laquelle vous exécutez le script doit être démarrée avec des droits d’utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-173">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="5f8c5-174">Le paramètre **RunAsAdministrator** est ignoré sur un système d’exploitation autre que Windows.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-174">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="5f8c5-175">Le paramètre **RunAsAdministrator** a été introduit dans PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-175">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="5f8c5-176">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-176">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="5f8c5-177">Exemples</span><span class="sxs-lookup"><span data-stu-id="5f8c5-177">Examples</span></span>

<span data-ttu-id="5f8c5-178">Le script suivant comporte deux `#Requires` instructions.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-178">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="5f8c5-179">Si les exigences spécifiées dans les deux instructions ne sont pas satisfaites, le script ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="5f8c5-179">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="5f8c5-180">Chaque `#Requires` instruction doit être le premier élément d’une ligne :</span><span class="sxs-lookup"><span data-stu-id="5f8c5-180">Each `#Requires` statement must be the first item on a line:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5f8c5-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f8c5-181">See also</span></span>

[<span data-ttu-id="5f8c5-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="5f8c5-182">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="5f8c5-183">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="5f8c5-183">about_Language_Keywords</span></span>](about_Language_Keywords.md)

