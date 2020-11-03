---
description: Explique les modes de langue et leur effet sur les sessions PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 8254760e49d5d9b2d1b035038b14414b0074435c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207050"
---
# <a name="about-language-modes"></a><span data-ttu-id="c6feb-104">À propos des modes de langage</span><span class="sxs-lookup"><span data-stu-id="c6feb-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="c6feb-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="c6feb-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c6feb-106">Explique les modes de langue et leur effet sur les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6feb-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="c6feb-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="c6feb-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c6feb-108">Le mode de langage d’une session PowerShell détermine, en partie, les éléments du langage PowerShell qui peuvent être utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="c6feb-109">PowerShell prend en charge les modes de langue suivants :</span><span class="sxs-lookup"><span data-stu-id="c6feb-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="c6feb-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-110">FullLanguage</span></span>
- <span data-ttu-id="c6feb-111">ConstrainedLanguage (introduit dans PowerShell 3,0)</span><span class="sxs-lookup"><span data-stu-id="c6feb-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="c6feb-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-112">RestrictedLanguage</span></span>
- <span data-ttu-id="c6feb-113">NoLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="c6feb-114">QU’EST-CE QU’UN MODE DE LANGAGE ?</span><span class="sxs-lookup"><span data-stu-id="c6feb-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="c6feb-115">Le mode de langage détermine les éléments de langage qui sont autorisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="c6feb-116">Le mode de langage est en fait une propriété de la configuration de session (ou « point de terminaison ») qui est utilisée pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="c6feb-117">Toutes les sessions qui utilisent une configuration de session particulière ont le mode de langue de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="c6feb-118">Toutes les sessions PowerShell ont un mode de langage, y compris les sessions PSSession que vous créez à l’aide de l’applet de commande `New-PSSession` , des sessions temporaires qui utilisent le paramètre ComputerName et des sessions par défaut qui s’affichent lorsque vous démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6feb-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="c6feb-119">Les sessions à distance sont créées à l’aide des configurations de session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="c6feb-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="c6feb-120">Le mode de langage défini dans la configuration de session détermine le mode de langue de la session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="c6feb-121">Pour spécifier la configuration de session d’une session PSSession, utilisez le paramètre ConfigurationName des applets de commande qui créent une session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="c6feb-122">MODES DE LANGUE</span><span class="sxs-lookup"><span data-stu-id="c6feb-122">LANGUAGE MODES</span></span>

<span data-ttu-id="c6feb-123">Cette section décrit les modes de langue dans les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6feb-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="c6feb-124">FULL LANGUAGE (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="c6feb-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="c6feb-125">Le mode FullLanguage autorise tous les éléments de langage de la session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="c6feb-126">FullLanguage est le mode de langue par défaut pour les sessions par défaut sur toutes les versions de Windows, à l’exception de Windows RT.</span><span class="sxs-lookup"><span data-stu-id="c6feb-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="c6feb-127">LANGUE RESTREINTe (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="c6feb-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="c6feb-128">En mode RestrictedLanguage, les utilisateurs peuvent exécuter des commandes (applets de commande, fonctions, commandes CIM et flux de travail), mais ils ne sont pas autorisés à utiliser des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="c6feb-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="c6feb-129">Par défaut, seules les variables suivantes sont autorisées en mode RestrictedLanguage :</span><span class="sxs-lookup"><span data-stu-id="c6feb-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="c6feb-130">Les manifestes de module, qui utilisent le mode RestrictedLanguage, autorisent également les variables supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6feb-130">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="c6feb-131">`$PSEdition` (dans PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="c6feb-131">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="c6feb-132">`$EnabledExperimentalFeatures` (dans PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="c6feb-132">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="c6feb-133">Seuls les opérateurs de comparaison suivants sont autorisés :</span><span class="sxs-lookup"><span data-stu-id="c6feb-133">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="c6feb-134">`-eq` valeur</span><span class="sxs-lookup"><span data-stu-id="c6feb-134">`-eq` (equal)</span></span>
- <span data-ttu-id="c6feb-135">`-gt` (supérieur à)</span><span class="sxs-lookup"><span data-stu-id="c6feb-135">`-gt` (greater-than)</span></span>
- <span data-ttu-id="c6feb-136">`-lt` (inférieur à)</span><span class="sxs-lookup"><span data-stu-id="c6feb-136">`-lt` (less-than)</span></span>

<span data-ttu-id="c6feb-137">Les instructions d'assignation, les références de propriété et les appels de méthode ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="c6feb-137">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="c6feb-138">AUCUNE langue (nolanguage)</span><span class="sxs-lookup"><span data-stu-id="c6feb-138">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="c6feb-139">Le mode nolanguage ne peut être utilisé que par le biais de l’API.</span><span class="sxs-lookup"><span data-stu-id="c6feb-139">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="c6feb-140">Le mode nolanguage signifie qu’aucun texte de script n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="c6feb-140">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="c6feb-141">Cela exclut l’utilisation de la méthode **AddScript ()** qui envoie des fragments de script PowerShell à analyser et à exécuter.</span><span class="sxs-lookup"><span data-stu-id="c6feb-141">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="c6feb-142">Vous ne pouvez utiliser que **AddCommand ()** et **AddParameter ()** qui ne passent pas par l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="c6feb-142">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="c6feb-143">LANGUE restreinte (langage restreint)</span><span class="sxs-lookup"><span data-stu-id="c6feb-143">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="c6feb-144">Le mode ConstrainedLanguage autorise toutes les applets de commande et tous les éléments de langage PowerShell, mais il limite les types autorisés.</span><span class="sxs-lookup"><span data-stu-id="c6feb-144">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="c6feb-145">Le mode ConstrainedLanguage est conçu pour prendre en charge l’intégrité du code en mode utilisateur (UMCI) sur Windows RT.</span><span class="sxs-lookup"><span data-stu-id="c6feb-145">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="c6feb-146">Il s’agit du seul mode de langage pris en charge sur Windows RT, mais il est disponible sur tous les systèmes pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c6feb-146">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="c6feb-147">UMCI protège les appareils ARM en autorisant uniquement l’installation d’applications signées par Microsoft et certifiées par Microsoft sur des appareils basés sur Windows RT.</span><span class="sxs-lookup"><span data-stu-id="c6feb-147">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="c6feb-148">Le mode ConstrainedLanguage empêche les utilisateurs d’utiliser PowerShell pour contourner ou enfreindre UMCI.</span><span class="sxs-lookup"><span data-stu-id="c6feb-148">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="c6feb-149">Les fonctionnalités du mode ConstrainedLanguage sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6feb-149">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="c6feb-150">Toutes les applets de commande dans les modules Windows et les autres applets de commande approuvées par UMCI sont entièrement opérationnelles et disposent d’un accès complet aux ressources système, sauf indication contraire.</span><span class="sxs-lookup"><span data-stu-id="c6feb-150">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="c6feb-151">Tous les éléments du langage de script PowerShell sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c6feb-151">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="c6feb-152">Tous les modules inclus dans Windows peuvent être importés et toutes les commandes que les modules exportent s’exécutent dans la session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-152">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="c6feb-153">Dans PowerShell workflow, vous pouvez écrire et exécuter des workflows de script (workflows écrits dans le langage PowerShell).</span><span class="sxs-lookup"><span data-stu-id="c6feb-153">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="c6feb-154">Les workflows XAML ne sont pas pris en charge et vous ne pouvez pas exécuter XAML dans un flux de travail de script, par exemple à l’aide de `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="c6feb-154">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="c6feb-155">En outre, les flux de travail ne peuvent pas appeler d’autres workflows, bien que les workflows imbriqués soient autorisés.</span><span class="sxs-lookup"><span data-stu-id="c6feb-155">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="c6feb-156">L' `Add-Type` applet de commande peut charger des assemblys signés, mais elle ne peut pas charger du code C# arbitraire ou des API Win32.</span><span class="sxs-lookup"><span data-stu-id="c6feb-156">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="c6feb-157">L' `New-Object` applet de commande peut être utilisée uniquement sur les types autorisés (listés ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="c6feb-157">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="c6feb-158">Seuls les types autorisés (listés ci-dessous) peuvent être utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6feb-158">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="c6feb-159">Les autres types ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="c6feb-159">Other types are not permitted.</span></span>

- <span data-ttu-id="c6feb-160">La conversion de type est autorisée, mais uniquement lorsque le résultat est un type autorisé.</span><span class="sxs-lookup"><span data-stu-id="c6feb-160">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="c6feb-161">Les paramètres d’applet de commande qui convertissent une entrée de chaîne en types fonctionnent uniquement lorsque le type résultant est un type autorisé.</span><span class="sxs-lookup"><span data-stu-id="c6feb-161">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="c6feb-162">La méthode **ToString ()** et les méthodes .net des types autorisés (listés ci-dessous) peuvent être appelées.</span><span class="sxs-lookup"><span data-stu-id="c6feb-162">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="c6feb-163">D’autres méthodes ne peuvent pas être appelées.</span><span class="sxs-lookup"><span data-stu-id="c6feb-163">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="c6feb-164">Les utilisateurs peuvent accéder à toutes les propriétés des types autorisés.</span><span class="sxs-lookup"><span data-stu-id="c6feb-164">Users can get all properties of allowed types.</span></span> <span data-ttu-id="c6feb-165">Les utilisateurs peuvent définir les valeurs des propriétés uniquement sur les types de base.</span><span class="sxs-lookup"><span data-stu-id="c6feb-165">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="c6feb-166">Seuls les objets COM suivants sont autorisés :</span><span class="sxs-lookup"><span data-stu-id="c6feb-166">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="c6feb-167">**Script. dictionary**</span><span class="sxs-lookup"><span data-stu-id="c6feb-167">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="c6feb-168">**Scripting.FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="c6feb-168">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="c6feb-169">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="c6feb-169">**VBScript.RegExp**</span></span>

<span data-ttu-id="c6feb-170">Les types suivants sont autorisés en mode ConstrainedLanguage.</span><span class="sxs-lookup"><span data-stu-id="c6feb-170">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="c6feb-171">Les utilisateurs peuvent accéder aux propriétés, appeler des méthodes et convertir des objets en ces types.</span><span class="sxs-lookup"><span data-stu-id="c6feb-171">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="c6feb-172">Types autorisés :</span><span class="sxs-lookup"><span data-stu-id="c6feb-172">Allowed Types:</span></span>

- <span data-ttu-id="c6feb-173">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-173">AliasAttribute</span></span>
- <span data-ttu-id="c6feb-174">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-174">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="c6feb-175">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-175">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="c6feb-176">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-176">AllowNullAttribute</span></span>
- <span data-ttu-id="c6feb-177">Array</span><span class="sxs-lookup"><span data-stu-id="c6feb-177">Array</span></span>
- <span data-ttu-id="c6feb-178">Bool</span><span class="sxs-lookup"><span data-stu-id="c6feb-178">Bool</span></span>
- <span data-ttu-id="c6feb-179">byte</span><span class="sxs-lookup"><span data-stu-id="c6feb-179">byte</span></span>
- <span data-ttu-id="c6feb-180">char</span><span class="sxs-lookup"><span data-stu-id="c6feb-180">char</span></span>
- <span data-ttu-id="c6feb-181">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-181">CmdletBindingAttribute</span></span>
- <span data-ttu-id="c6feb-182">DateTime</span><span class="sxs-lookup"><span data-stu-id="c6feb-182">DateTime</span></span>
- <span data-ttu-id="c6feb-183">Décimal</span><span class="sxs-lookup"><span data-stu-id="c6feb-183">decimal</span></span>
- <span data-ttu-id="c6feb-184">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="c6feb-184">DirectoryEntry</span></span>
- <span data-ttu-id="c6feb-185">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="c6feb-185">DirectorySearcher</span></span>
- <span data-ttu-id="c6feb-186">double</span><span class="sxs-lookup"><span data-stu-id="c6feb-186">double</span></span>
- <span data-ttu-id="c6feb-187">float</span><span class="sxs-lookup"><span data-stu-id="c6feb-187">float</span></span>
- <span data-ttu-id="c6feb-188">Guid</span><span class="sxs-lookup"><span data-stu-id="c6feb-188">Guid</span></span>
- <span data-ttu-id="c6feb-189">Hashtable</span><span class="sxs-lookup"><span data-stu-id="c6feb-189">Hashtable</span></span>
- <span data-ttu-id="c6feb-190">int</span><span class="sxs-lookup"><span data-stu-id="c6feb-190">int</span></span>
- <span data-ttu-id="c6feb-191">Int16</span><span class="sxs-lookup"><span data-stu-id="c6feb-191">Int16</span></span>
- <span data-ttu-id="c6feb-192">long</span><span class="sxs-lookup"><span data-stu-id="c6feb-192">long</span></span>
- <span data-ttu-id="c6feb-193">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="c6feb-193">ManagementClass</span></span>
- <span data-ttu-id="c6feb-194">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="c6feb-194">ManagementObject</span></span>
- <span data-ttu-id="c6feb-195">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="c6feb-195">ManagementObjectSearcher</span></span>
- <span data-ttu-id="c6feb-196">NullString</span><span class="sxs-lookup"><span data-stu-id="c6feb-196">NullString</span></span>
- <span data-ttu-id="c6feb-197">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-197">OutputTypeAttribute</span></span>
- <span data-ttu-id="c6feb-198">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-198">ParameterAttribute</span></span>
- <span data-ttu-id="c6feb-199">PSCredential</span><span class="sxs-lookup"><span data-stu-id="c6feb-199">PSCredential</span></span>
- <span data-ttu-id="c6feb-200">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-200">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="c6feb-201">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="c6feb-201">PSListModifier</span></span>
- <span data-ttu-id="c6feb-202">PSObject</span><span class="sxs-lookup"><span data-stu-id="c6feb-202">PSObject</span></span>
- <span data-ttu-id="c6feb-203">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="c6feb-203">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="c6feb-204">PSReference</span><span class="sxs-lookup"><span data-stu-id="c6feb-204">PSReference</span></span>
- <span data-ttu-id="c6feb-205">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-205">PSTypeNameAttribute</span></span>
- <span data-ttu-id="c6feb-206">Expression régulière</span><span class="sxs-lookup"><span data-stu-id="c6feb-206">Regex</span></span>
- <span data-ttu-id="c6feb-207">SByte</span><span class="sxs-lookup"><span data-stu-id="c6feb-207">SByte</span></span>
- <span data-ttu-id="c6feb-208">string</span><span class="sxs-lookup"><span data-stu-id="c6feb-208">string</span></span>
- <span data-ttu-id="c6feb-209">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="c6feb-209">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="c6feb-210">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="c6feb-210">SwitchParameter</span></span>
- <span data-ttu-id="c6feb-211">System. Globalization. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="c6feb-211">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="c6feb-212">System .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="c6feb-212">System.Net.IPAddress</span></span>
- <span data-ttu-id="c6feb-213">System .net. mail. MailAddress</span><span class="sxs-lookup"><span data-stu-id="c6feb-213">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="c6feb-214">System. Numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="c6feb-214">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="c6feb-215">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="c6feb-215">System.Security.SecureString</span></span>
- <span data-ttu-id="c6feb-216">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c6feb-216">TimeSpan</span></span>
- <span data-ttu-id="c6feb-217">UInt16</span><span class="sxs-lookup"><span data-stu-id="c6feb-217">UInt16</span></span>
- <span data-ttu-id="c6feb-218">UInt32</span><span class="sxs-lookup"><span data-stu-id="c6feb-218">UInt32</span></span>
- <span data-ttu-id="c6feb-219">UInt64</span><span class="sxs-lookup"><span data-stu-id="c6feb-219">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="c6feb-220">RECHERCHE DU MODE DE LANGUE D’UNE CONFIGURATION DE SESSION</span><span class="sxs-lookup"><span data-stu-id="c6feb-220">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="c6feb-221">Quand une configuration de session est créée à l’aide d’un fichier de configuration de session, la configuration de session a une propriété LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="c6feb-221">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="c6feb-222">Vous pouvez trouver le mode de langage en obtenant la valeur de la propriété LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="c6feb-222">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="c6feb-223">Sur d’autres configurations de session, vous pouvez trouver le mode de langage indirectement en recherchant le mode de langue d’une session créée à l’aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-223">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="c6feb-224">RECHERCHE DU MODE DE LANGUE D’UNE SESSION</span><span class="sxs-lookup"><span data-stu-id="c6feb-224">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="c6feb-225">Vous pouvez trouver le mode de langage d’une session FullLanguage ou ConstrainedLanguage en obtenant la valeur de la propriété LanguageMode de l’état de session.</span><span class="sxs-lookup"><span data-stu-id="c6feb-225">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="c6feb-226">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6feb-226">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="c6feb-227">Toutefois, dans les sessions avec des modes RestrictedLanguage et nolanguage, vous ne pouvez pas utiliser la méthode dot pour récupérer des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="c6feb-227">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="c6feb-228">Au lieu de cela, le message d’erreur révèle le mode de langage.</span><span class="sxs-lookup"><span data-stu-id="c6feb-228">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="c6feb-229">Quand vous exécutez la `$ExecutionContext.SessionState.LanguageMode` commande dans une session RestrictedLanguage, PowerShell retourne les messages d’erreur PropertyReferenceNotSupportedInDataSection et VariableReferenceNotSupportedInDataSection.</span><span class="sxs-lookup"><span data-stu-id="c6feb-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="c6feb-230">PropertyReferenceNotSupportedInDataSection : les références de propriété ne sont pas autorisées en mode de langage restreint ou dans une section de données.</span><span class="sxs-lookup"><span data-stu-id="c6feb-230">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="c6feb-231">VariableReferenceNotSupportedInDataSection : une variable qui ne peut pas être référencée en mode de langage restreint ou une section de données est référencée.</span><span class="sxs-lookup"><span data-stu-id="c6feb-231">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="c6feb-232">Quand vous exécutez la `$ExecutionContext.SessionState.LanguageMode` commande dans une session nolanguage, PowerShell retourne le message d’erreur ScriptsNotAllowed.</span><span class="sxs-lookup"><span data-stu-id="c6feb-232">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="c6feb-233">ScriptsNotAllowed : la syntaxe n’est pas prise en charge par cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c6feb-233">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="c6feb-234">Cela peut être dû au fait qu’il n’est pas en mode sans langage.</span><span class="sxs-lookup"><span data-stu-id="c6feb-234">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="c6feb-235">MOT</span><span class="sxs-lookup"><span data-stu-id="c6feb-235">KEYWORDS</span></span>

- <span data-ttu-id="c6feb-236">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-236">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="c6feb-237">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-237">about_FullLanguage</span></span>
- <span data-ttu-id="c6feb-238">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-238">about_NoLanguage</span></span>
- <span data-ttu-id="c6feb-239">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="c6feb-239">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="c6feb-240">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="c6feb-240">SEE ALSO</span></span>

- [<span data-ttu-id="c6feb-241">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="c6feb-241">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="c6feb-242">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="c6feb-242">about_Session_Configurations</span></span>](about_Session_Configurations.md)
