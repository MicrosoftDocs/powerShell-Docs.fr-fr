---
description: Explique les modes de langue et leur effet sur les sessions PowerShell.
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 9e4b1ec2dd16d3442c553460ff217e7e0223f41f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596303"
---
# <a name="about-language-modes"></a><span data-ttu-id="b13d4-103">À propos des modes de langage</span><span class="sxs-lookup"><span data-stu-id="b13d4-103">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="b13d4-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="b13d4-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b13d4-105">Explique les modes de langue et leur effet sur les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b13d4-105">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="b13d4-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="b13d4-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b13d4-107">Le mode de langage d’une session PowerShell détermine, en partie, les éléments du langage PowerShell qui peuvent être utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-107">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="b13d4-108">PowerShell prend en charge les modes de langue suivants :</span><span class="sxs-lookup"><span data-stu-id="b13d4-108">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="b13d4-109">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="b13d4-109">FullLanguage</span></span>
- <span data-ttu-id="b13d4-110">ConstrainedLanguage (introduit dans PowerShell 3,0)</span><span class="sxs-lookup"><span data-stu-id="b13d4-110">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="b13d4-111">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="b13d4-111">RestrictedLanguage</span></span>
- <span data-ttu-id="b13d4-112">NoLanguage</span><span class="sxs-lookup"><span data-stu-id="b13d4-112">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="b13d4-113">QU’EST-CE QU’UN MODE DE LANGAGE ?</span><span class="sxs-lookup"><span data-stu-id="b13d4-113">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="b13d4-114">Le mode de langage détermine les éléments de langage qui sont autorisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-114">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="b13d4-115">Le mode de langage est en fait une propriété de la configuration de session (ou « point de terminaison ») qui est utilisée pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-115">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="b13d4-116">Toutes les sessions qui utilisent une configuration de session particulière ont le mode de langue de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-116">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="b13d4-117">Toutes les sessions PowerShell ont un mode de langage, y compris les sessions PSSession que vous créez à l’aide de l’applet de commande `New-PSSession` , des sessions temporaires qui utilisent le paramètre ComputerName et des sessions par défaut qui s’affichent lorsque vous démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b13d4-117">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="b13d4-118">Les sessions à distance sont créées à l’aide des configurations de session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b13d4-118">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="b13d4-119">Le mode de langage défini dans la configuration de session détermine le mode de langue de la session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-119">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="b13d4-120">Pour spécifier la configuration de session d’une session PSSession, utilisez le paramètre ConfigurationName des applets de commande qui créent une session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-120">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="b13d4-121">MODES DE LANGUE</span><span class="sxs-lookup"><span data-stu-id="b13d4-121">LANGUAGE MODES</span></span>

<span data-ttu-id="b13d4-122">Cette section décrit les modes de langue dans les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b13d4-122">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="b13d4-123">FULL LANGUAGE (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="b13d4-123">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="b13d4-124">Le mode FullLanguage autorise tous les éléments de langage de la session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-124">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="b13d4-125">FullLanguage est le mode de langue par défaut pour les sessions par défaut sur toutes les versions de Windows, à l’exception de Windows RT.</span><span class="sxs-lookup"><span data-stu-id="b13d4-125">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="b13d4-126">LANGUE RESTREINTe (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="b13d4-126">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="b13d4-127">En mode RestrictedLanguage, les utilisateurs peuvent exécuter des commandes (applets de commande, fonctions, commandes CIM et flux de travail), mais ils ne sont pas autorisés à utiliser des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="b13d4-127">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="b13d4-128">Par défaut, seules les variables suivantes sont autorisées en mode RestrictedLanguage :</span><span class="sxs-lookup"><span data-stu-id="b13d4-128">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="b13d4-129">Les manifestes de module, qui utilisent le mode RestrictedLanguage, autorisent également les variables supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="b13d4-129">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="b13d4-130">`$PSEdition` (dans PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="b13d4-130">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="b13d4-131">`$EnabledExperimentalFeatures` (dans PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="b13d4-131">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="b13d4-132">Seuls les opérateurs de comparaison suivants sont autorisés :</span><span class="sxs-lookup"><span data-stu-id="b13d4-132">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="b13d4-133">`-eq` valeur</span><span class="sxs-lookup"><span data-stu-id="b13d4-133">`-eq` (equal)</span></span>
- <span data-ttu-id="b13d4-134">`-gt` (supérieur à)</span><span class="sxs-lookup"><span data-stu-id="b13d4-134">`-gt` (greater-than)</span></span>
- <span data-ttu-id="b13d4-135">`-lt` (inférieur à)</span><span class="sxs-lookup"><span data-stu-id="b13d4-135">`-lt` (less-than)</span></span>

<span data-ttu-id="b13d4-136">Les instructions d'assignation, les références de propriété et les appels de méthode ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b13d4-136">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="b13d4-137">AUCUNE langue (nolanguage)</span><span class="sxs-lookup"><span data-stu-id="b13d4-137">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="b13d4-138">Le mode nolanguage ne peut être utilisé que par le biais de l’API.</span><span class="sxs-lookup"><span data-stu-id="b13d4-138">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="b13d4-139">Le mode nolanguage signifie qu’aucun texte de script n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="b13d4-139">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="b13d4-140">Cela exclut l’utilisation de la méthode **AddScript ()** qui envoie des fragments de script PowerShell à analyser et à exécuter.</span><span class="sxs-lookup"><span data-stu-id="b13d4-140">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="b13d4-141">Vous ne pouvez utiliser que **AddCommand ()** et **AddParameter ()** qui ne passent pas par l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="b13d4-141">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="b13d4-142">LANGUE restreinte (langage restreint)</span><span class="sxs-lookup"><span data-stu-id="b13d4-142">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="b13d4-143">Le mode ConstrainedLanguage autorise toutes les applets de commande et tous les éléments de langage PowerShell, mais il limite les types autorisés.</span><span class="sxs-lookup"><span data-stu-id="b13d4-143">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="b13d4-144">Le mode ConstrainedLanguage est conçu pour prendre en charge l’intégrité du code en mode utilisateur (UMCI) sur Windows RT.</span><span class="sxs-lookup"><span data-stu-id="b13d4-144">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="b13d4-145">Il s’agit du seul mode de langage pris en charge sur Windows RT, mais il est disponible sur tous les systèmes pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b13d4-145">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="b13d4-146">UMCI protège les appareils ARM en autorisant uniquement l’installation d’applications signées par Microsoft et certifiées par Microsoft sur des appareils basés sur Windows RT.</span><span class="sxs-lookup"><span data-stu-id="b13d4-146">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="b13d4-147">Le mode ConstrainedLanguage empêche les utilisateurs d’utiliser PowerShell pour contourner ou enfreindre UMCI.</span><span class="sxs-lookup"><span data-stu-id="b13d4-147">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="b13d4-148">Les fonctionnalités du mode ConstrainedLanguage sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b13d4-148">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="b13d4-149">Toutes les applets de commande dans les modules Windows et les autres applets de commande approuvées par UMCI sont entièrement opérationnelles et disposent d’un accès complet aux ressources système, sauf indication contraire.</span><span class="sxs-lookup"><span data-stu-id="b13d4-149">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="b13d4-150">Tous les éléments du langage de script PowerShell sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b13d4-150">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="b13d4-151">Tous les modules inclus dans Windows peuvent être importés et toutes les commandes que les modules exportent s’exécutent dans la session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-151">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="b13d4-152">Dans PowerShell workflow, vous pouvez écrire et exécuter des workflows de script (workflows écrits dans le langage PowerShell).</span><span class="sxs-lookup"><span data-stu-id="b13d4-152">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="b13d4-153">Les workflows XAML ne sont pas pris en charge et vous ne pouvez pas exécuter XAML dans un flux de travail de script, par exemple à l’aide de `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="b13d4-153">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="b13d4-154">En outre, les flux de travail ne peuvent pas appeler d’autres workflows, bien que les workflows imbriqués soient autorisés.</span><span class="sxs-lookup"><span data-stu-id="b13d4-154">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="b13d4-155">L' `Add-Type` applet de commande peut charger des assemblys signés, mais elle ne peut pas charger du code C# arbitraire ou des API Win32.</span><span class="sxs-lookup"><span data-stu-id="b13d4-155">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="b13d4-156">L' `New-Object` applet de commande peut être utilisée uniquement sur les types autorisés (listés ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="b13d4-156">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="b13d4-157">Seuls les types autorisés (listés ci-dessous) peuvent être utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b13d4-157">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="b13d4-158">Les autres types ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b13d4-158">Other types are not permitted.</span></span>

- <span data-ttu-id="b13d4-159">La conversion de type est autorisée, mais uniquement lorsque le résultat est un type autorisé.</span><span class="sxs-lookup"><span data-stu-id="b13d4-159">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="b13d4-160">Les paramètres d’applet de commande qui convertissent une entrée de chaîne en types fonctionnent uniquement lorsque le type résultant est un type autorisé.</span><span class="sxs-lookup"><span data-stu-id="b13d4-160">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="b13d4-161">La méthode **ToString ()** et les méthodes .net des types autorisés (listés ci-dessous) peuvent être appelées.</span><span class="sxs-lookup"><span data-stu-id="b13d4-161">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="b13d4-162">D’autres méthodes ne peuvent pas être appelées.</span><span class="sxs-lookup"><span data-stu-id="b13d4-162">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="b13d4-163">Les utilisateurs peuvent accéder à toutes les propriétés des types autorisés.</span><span class="sxs-lookup"><span data-stu-id="b13d4-163">Users can get all properties of allowed types.</span></span> <span data-ttu-id="b13d4-164">Les utilisateurs peuvent définir les valeurs des propriétés uniquement sur les types de base.</span><span class="sxs-lookup"><span data-stu-id="b13d4-164">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="b13d4-165">Seuls les objets COM suivants sont autorisés :</span><span class="sxs-lookup"><span data-stu-id="b13d4-165">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="b13d4-166">**Script. dictionary**</span><span class="sxs-lookup"><span data-stu-id="b13d4-166">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="b13d4-167">**Scripting.FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="b13d4-167">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="b13d4-168">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="b13d4-168">**VBScript.RegExp**</span></span>

<span data-ttu-id="b13d4-169">Les types suivants sont autorisés en mode ConstrainedLanguage.</span><span class="sxs-lookup"><span data-stu-id="b13d4-169">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="b13d4-170">Les utilisateurs peuvent accéder aux propriétés, appeler des méthodes et convertir des objets en ces types.</span><span class="sxs-lookup"><span data-stu-id="b13d4-170">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="b13d4-171">Types autorisés :</span><span class="sxs-lookup"><span data-stu-id="b13d4-171">Allowed Types:</span></span>

- <span data-ttu-id="b13d4-172">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-172">AliasAttribute</span></span>
- <span data-ttu-id="b13d4-173">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-173">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="b13d4-174">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-174">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="b13d4-175">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-175">AllowNullAttribute</span></span>
- <span data-ttu-id="b13d4-176">Array</span><span class="sxs-lookup"><span data-stu-id="b13d4-176">Array</span></span>
- <span data-ttu-id="b13d4-177">Bool</span><span class="sxs-lookup"><span data-stu-id="b13d4-177">Bool</span></span>
- <span data-ttu-id="b13d4-178">byte</span><span class="sxs-lookup"><span data-stu-id="b13d4-178">byte</span></span>
- <span data-ttu-id="b13d4-179">char</span><span class="sxs-lookup"><span data-stu-id="b13d4-179">char</span></span>
- <span data-ttu-id="b13d4-180">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-180">CmdletBindingAttribute</span></span>
- <span data-ttu-id="b13d4-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="b13d4-181">DateTime</span></span>
- <span data-ttu-id="b13d4-182">Décimal</span><span class="sxs-lookup"><span data-stu-id="b13d4-182">decimal</span></span>
- <span data-ttu-id="b13d4-183">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="b13d4-183">DirectoryEntry</span></span>
- <span data-ttu-id="b13d4-184">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="b13d4-184">DirectorySearcher</span></span>
- <span data-ttu-id="b13d4-185">double</span><span class="sxs-lookup"><span data-stu-id="b13d4-185">double</span></span>
- <span data-ttu-id="b13d4-186">float</span><span class="sxs-lookup"><span data-stu-id="b13d4-186">float</span></span>
- <span data-ttu-id="b13d4-187">Guid</span><span class="sxs-lookup"><span data-stu-id="b13d4-187">Guid</span></span>
- <span data-ttu-id="b13d4-188">Hashtable</span><span class="sxs-lookup"><span data-stu-id="b13d4-188">Hashtable</span></span>
- <span data-ttu-id="b13d4-189">int</span><span class="sxs-lookup"><span data-stu-id="b13d4-189">int</span></span>
- <span data-ttu-id="b13d4-190">Int16</span><span class="sxs-lookup"><span data-stu-id="b13d4-190">Int16</span></span>
- <span data-ttu-id="b13d4-191">long</span><span class="sxs-lookup"><span data-stu-id="b13d4-191">long</span></span>
- <span data-ttu-id="b13d4-192">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="b13d4-192">ManagementClass</span></span>
- <span data-ttu-id="b13d4-193">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="b13d4-193">ManagementObject</span></span>
- <span data-ttu-id="b13d4-194">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="b13d4-194">ManagementObjectSearcher</span></span>
- <span data-ttu-id="b13d4-195">NullString</span><span class="sxs-lookup"><span data-stu-id="b13d4-195">NullString</span></span>
- <span data-ttu-id="b13d4-196">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-196">OutputTypeAttribute</span></span>
- <span data-ttu-id="b13d4-197">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-197">ParameterAttribute</span></span>
- <span data-ttu-id="b13d4-198">PSCredential</span><span class="sxs-lookup"><span data-stu-id="b13d4-198">PSCredential</span></span>
- <span data-ttu-id="b13d4-199">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-199">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="b13d4-200">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="b13d4-200">PSListModifier</span></span>
- <span data-ttu-id="b13d4-201">PSObject</span><span class="sxs-lookup"><span data-stu-id="b13d4-201">PSObject</span></span>
- <span data-ttu-id="b13d4-202">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="b13d4-202">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="b13d4-203">PSReference</span><span class="sxs-lookup"><span data-stu-id="b13d4-203">PSReference</span></span>
- <span data-ttu-id="b13d4-204">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-204">PSTypeNameAttribute</span></span>
- <span data-ttu-id="b13d4-205">Expression régulière</span><span class="sxs-lookup"><span data-stu-id="b13d4-205">Regex</span></span>
- <span data-ttu-id="b13d4-206">SByte</span><span class="sxs-lookup"><span data-stu-id="b13d4-206">SByte</span></span>
- <span data-ttu-id="b13d4-207">chaîne</span><span class="sxs-lookup"><span data-stu-id="b13d4-207">string</span></span>
- <span data-ttu-id="b13d4-208">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="b13d4-208">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="b13d4-209">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b13d4-209">SwitchParameter</span></span>
- <span data-ttu-id="b13d4-210">System. Globalization. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="b13d4-210">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="b13d4-211">System .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="b13d4-211">System.Net.IPAddress</span></span>
- <span data-ttu-id="b13d4-212">System .net. mail. MailAddress</span><span class="sxs-lookup"><span data-stu-id="b13d4-212">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="b13d4-213">System. Numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="b13d4-213">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="b13d4-214">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="b13d4-214">System.Security.SecureString</span></span>
- <span data-ttu-id="b13d4-215">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b13d4-215">TimeSpan</span></span>
- <span data-ttu-id="b13d4-216">UInt16</span><span class="sxs-lookup"><span data-stu-id="b13d4-216">UInt16</span></span>
- <span data-ttu-id="b13d4-217">UInt32</span><span class="sxs-lookup"><span data-stu-id="b13d4-217">UInt32</span></span>
- <span data-ttu-id="b13d4-218">UInt64</span><span class="sxs-lookup"><span data-stu-id="b13d4-218">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="b13d4-219">RECHERCHE DU MODE DE LANGUE D’UNE CONFIGURATION DE SESSION</span><span class="sxs-lookup"><span data-stu-id="b13d4-219">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="b13d4-220">Quand une configuration de session est créée à l’aide d’un fichier de configuration de session, la configuration de session a une propriété LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="b13d4-220">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="b13d4-221">Vous pouvez trouver le mode de langage en obtenant la valeur de la propriété LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="b13d4-221">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="b13d4-222">Sur d’autres configurations de session, vous pouvez trouver le mode de langage indirectement en recherchant le mode de langue d’une session créée à l’aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-222">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="b13d4-223">RECHERCHE DU MODE DE LANGUE D’UNE SESSION</span><span class="sxs-lookup"><span data-stu-id="b13d4-223">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="b13d4-224">Vous pouvez trouver le mode de langage d’une session FullLanguage ou ConstrainedLanguage en obtenant la valeur de la propriété LanguageMode de l’état de session.</span><span class="sxs-lookup"><span data-stu-id="b13d4-224">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="b13d4-225">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b13d4-225">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="b13d4-226">Toutefois, dans les sessions avec des modes RestrictedLanguage et nolanguage, vous ne pouvez pas utiliser la méthode dot pour récupérer des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="b13d4-226">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="b13d4-227">Au lieu de cela, le message d’erreur révèle le mode de langage.</span><span class="sxs-lookup"><span data-stu-id="b13d4-227">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="b13d4-228">Quand vous exécutez la `$ExecutionContext.SessionState.LanguageMode` commande dans une session RestrictedLanguage, PowerShell retourne les messages d’erreur PropertyReferenceNotSupportedInDataSection et VariableReferenceNotSupportedInDataSection.</span><span class="sxs-lookup"><span data-stu-id="b13d4-228">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="b13d4-229">PropertyReferenceNotSupportedInDataSection : les références de propriété ne sont pas autorisées en mode de langage restreint ou dans une section de données.</span><span class="sxs-lookup"><span data-stu-id="b13d4-229">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="b13d4-230">VariableReferenceNotSupportedInDataSection : une variable qui ne peut pas être référencée en mode de langage restreint ou une section de données est référencée.</span><span class="sxs-lookup"><span data-stu-id="b13d4-230">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="b13d4-231">Quand vous exécutez la `$ExecutionContext.SessionState.LanguageMode` commande dans une session nolanguage, PowerShell retourne le message d’erreur ScriptsNotAllowed.</span><span class="sxs-lookup"><span data-stu-id="b13d4-231">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="b13d4-232">ScriptsNotAllowed : la syntaxe n’est pas prise en charge par cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b13d4-232">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="b13d4-233">Cela peut être dû au fait qu’il n’est pas en mode sans langage.</span><span class="sxs-lookup"><span data-stu-id="b13d4-233">This might be because it is in no-language mode.</span></span>

## <a name="see-also"></a><span data-ttu-id="b13d4-234">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="b13d4-234">SEE ALSO</span></span>

- [<span data-ttu-id="b13d4-235">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="b13d4-235">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="b13d4-236">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="b13d4-236">about_Session_Configurations</span></span>](about_Session_Configurations.md)
