---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Capacités de rôle JEA
ms.openlocfilehash: 528b41c0e2ffdcfed3251fb0f714c649e7290761
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229555"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="1f983-103">Capacités de rôle JEA</span><span class="sxs-lookup"><span data-stu-id="1f983-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="1f983-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1f983-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1f983-105">Lorsque vous créez un point de terminaison JEA, vous devez définir une ou plusieurs « capacités de rôle », qui décrivent *ce que* quelqu’un peut faire dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="1f983-106">Une capacité de rôle est un fichier de données PowerShell avec l’extension .psrc qui liste toutes les applets de commande, toutes les fonctions, tous les fournisseurs et tous les programmes externes devant être accessibles aux utilisateurs qui se connectent.</span><span class="sxs-lookup"><span data-stu-id="1f983-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="1f983-107">Cette rubrique décrit comment créer un fichier de capacités de rôle PowerShell pour vos utilisateurs JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="1f983-108">Déterminer les commandes à autoriser</span><span class="sxs-lookup"><span data-stu-id="1f983-108">Determine which commands to allow</span></span>

<span data-ttu-id="1f983-109">La première étape de la création d’un fichier de capacités de rôle consiste à prendre en considération ce à quoi les utilisateurs de ce rôle auront besoin d’accéder.</span><span class="sxs-lookup"><span data-stu-id="1f983-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="1f983-110">Ce processus de collecte des exigences peut prendre un certain temps, mais il est très important.</span><span class="sxs-lookup"><span data-stu-id="1f983-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="1f983-111">En donnant accès aux utilisateurs à trop peu de fonctions et d’applets de commande, vous les empêchez de faire leur travail.</span><span class="sxs-lookup"><span data-stu-id="1f983-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="1f983-112">Si vous autorisez l’accès à un trop grand nombre d’applets de commande et de fonctions, les utilisateurs pourront faire plus que prévu avec leurs privilèges Administrateur implicites, ce qui affaiblira votre position en matière de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1f983-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="1f983-113">Vos choix vis-à-vis de ce processus dépendent de votre organisation et de vos objectifs, mais les conseils suivants peuvent vous aider à vérifier que vous êtes sur la bonne voie.</span><span class="sxs-lookup"><span data-stu-id="1f983-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="1f983-114">**Identifiez** les commandes que les utilisateurs emploient pour effectuer leur travail.</span><span class="sxs-lookup"><span data-stu-id="1f983-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="1f983-115">Cela peut impliquer d’observer le personnel informatique, de consulter les scripts d’automatisation et d’analyser les journaux ou les transcriptions de sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f983-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="1f983-116">**Transposez** l’utilisation des outils de ligne de commande à leurs équivalents PowerShell, si possible, pour assurer la meilleure expérience d’audit et de personnalisation JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="1f983-117">Les programmes externes ne peuvent pas avoir de contraintes aussi granulaires que les fonctions et applets de commande PowerShell natives de JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="1f983-118">**Restreignez** si nécessaire la portée des applets de commande pour n’autoriser que des paramètres ou des valeurs de paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1f983-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="1f983-119">C’est particulièrement important si les utilisateurs ne doivent pouvoir gérer qu’une partie d’un système.</span><span class="sxs-lookup"><span data-stu-id="1f983-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="1f983-120">**Créez** des fonctions personnalisées pour remplacer des commandes complexes ou difficiles à contraindre dans JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="1f983-121">Une fonction simple qui inclut une commande complexe dans un wrapper ou applique une logique de validation supplémentaire peut offrir des contrôles supplémentaires aux administrateurs et plus de simplicité aux utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="1f983-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="1f983-122">**Testez** la liste étendue des commandes admissibles avec vos utilisateurs et/ou services d’automatisation et effectuez les ajustements nécessaires.</span><span class="sxs-lookup"><span data-stu-id="1f983-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="1f983-123">N’oubliez pas que les commandes d’une session JEA sont souvent exécutées avec des privilèges Administrateur (ou avec élévation de privilèges autre).</span><span class="sxs-lookup"><span data-stu-id="1f983-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="1f983-124">Une sélection rigoureuse des commandes disponibles est essentielle pour que le point de terminaison JEA n’autorise pas l’utilisateur connecté à élever ses autorisations.</span><span class="sxs-lookup"><span data-stu-id="1f983-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="1f983-125">Voici quelques exemples de commandes qui peuvent être utilisées à des fins malveillantes si elles sont autorisées sans contraintes.</span><span class="sxs-lookup"><span data-stu-id="1f983-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="1f983-126">Notez que cette liste n’est pas exhaustive et ne doit être utilisée que comme point de départ pour prendre les précautions qui s’imposent.</span><span class="sxs-lookup"><span data-stu-id="1f983-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="1f983-127">Exemples de commandes potentiellement dangereuses</span><span class="sxs-lookup"><span data-stu-id="1f983-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="1f983-128">Risque</span><span class="sxs-lookup"><span data-stu-id="1f983-128">Risk</span></span> | <span data-ttu-id="1f983-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f983-129">Example</span></span> | <span data-ttu-id="1f983-130">Commandes associées</span><span class="sxs-lookup"><span data-stu-id="1f983-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="1f983-131">Accorder des privilèges Administrateur à l’utilisateur connecté pour contourner JEA</span><span class="sxs-lookup"><span data-stu-id="1f983-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="1f983-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="1f983-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="1f983-133">Exécuter du code arbitraire, notamment des logiciels malveillants, du code malveillant exploitant une faille de sécurité ou des scripts personnalisés afin de contourner les protections</span><span class="sxs-lookup"><span data-stu-id="1f983-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="1f983-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="1f983-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="1f983-135">Créer un fichier de capacités de rôle</span><span class="sxs-lookup"><span data-stu-id="1f983-135">Create a role capability file</span></span>

<span data-ttu-id="1f983-136">Vous pouvez créer un fichier de capacités de rôle PowerShell avec l’applet de commande [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).</span><span class="sxs-lookup"><span data-stu-id="1f983-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="1f983-137">Le fichier de capacités de rôle résultant peut être ouvert dans un éditeur de texte et modifié pour autoriser les commandes souhaitées pour le rôle.</span><span class="sxs-lookup"><span data-stu-id="1f983-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="1f983-138">La documentation d’aide PowerShell contient plusieurs exemples de configuration du fichier.</span><span class="sxs-lookup"><span data-stu-id="1f983-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="1f983-139">Autoriser les fonctions et les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f983-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="1f983-140">Pour autoriser les utilisateurs à exécuter des fonctions ou des applets de commande PowerShell, ajoutez le nom de l’applet de commande ou de la fonction au champ VisibleFunctions ou VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="1f983-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="1f983-141">Si vous ne savez pas si une commande est une applet de commande ou une fonction, vous pouvez exécuter `Get-Command <name>` et vérifier la propriété « CommandType » dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="1f983-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="1f983-142">La portée d’une applet de commande ou d’une fonction donnée est parfois trop vaste pour les besoins de vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1f983-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="1f983-143">Un administrateur DNS, par exemple, n’a probablement besoin que de l’accès nécessaire pour redémarrer le service DNS.</span><span class="sxs-lookup"><span data-stu-id="1f983-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="1f983-144">Dans un environnement mutualisé où les locataires ont accès à des outils de gestion en libre-service, ils doivent être limités à la gestion de leurs propres ressources.</span><span class="sxs-lookup"><span data-stu-id="1f983-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="1f983-145">Dans ce cas, vous pouvez restreindre les paramètres exposés à partir de l’applet de commande ou de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1f983-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="1f983-146">Dans des scénarios plus avancés, vous devrez peut-être également restreindre les valeurs que les utilisateurs peuvent fournir à ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f983-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="1f983-147">Les capacités de rôle vous permettent de définir un ensemble de valeurs autorisées ou un modèle d’expression régulière évalué pour déterminer si une entrée donnée est autorisée.</span><span class="sxs-lookup"><span data-stu-id="1f983-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="1f983-148">Les [paramètres PowerShell communs](https://technet.microsoft.com/library/hh847884.aspx) sont toujours autorisés, même si vous limitez les paramètres disponibles.</span><span class="sxs-lookup"><span data-stu-id="1f983-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="1f983-149">Vous ne devez pas les lister explicitement dans le champ Paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f983-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="1f983-150">Le tableau ci-dessous décrit les différentes façons de personnaliser une fonction ou une applet de commande visible.</span><span class="sxs-lookup"><span data-stu-id="1f983-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="1f983-151">Vous pouvez associer les méthodes suivantes comme vous le souhaitez dans le champ VisibleCmdlets.</span><span class="sxs-lookup"><span data-stu-id="1f983-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="1f983-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f983-152">Example</span></span>                                                                                      | <span data-ttu-id="1f983-153">Cas d’usage</span><span class="sxs-lookup"><span data-stu-id="1f983-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="1f983-154">`'My-Func'` ou `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="1f983-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="1f983-155">Permet à l’utilisateur d’exécuter `My-Func` sans aucune restriction sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f983-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="1f983-156">Permet à l’utilisateur d’exécuter `My-Func` à partir du module `MyModule` sans aucune restriction sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f983-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="1f983-157">Permet à l’utilisateur d’exécuter toutes les applets de commande ou fonctions avec le verbe `My`.</span><span class="sxs-lookup"><span data-stu-id="1f983-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="1f983-158">Permet à l’utilisateur d’exécuter toutes les applets de commande ou fonctions avec le nom `Func`.</span><span class="sxs-lookup"><span data-stu-id="1f983-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="1f983-159">Permet à l’utilisateur d’exécuter `My-Func` avec les paramètres `Param1` et/ou `Param2`.</span><span class="sxs-lookup"><span data-stu-id="1f983-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="1f983-160">Toutes les valeurs peuvent être transmises aux paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f983-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="1f983-161">Permet à l’utilisateur d’exécuter `My-Func` avec le paramètre `Param1`.</span><span class="sxs-lookup"><span data-stu-id="1f983-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="1f983-162">Seules les valeurs « Value1 » et « Value2 » peuvent être transmises au paramètre.</span><span class="sxs-lookup"><span data-stu-id="1f983-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="1f983-163">Permet à l’utilisateur d’exécuter `My-Func` avec le paramètre `Param1`.</span><span class="sxs-lookup"><span data-stu-id="1f983-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="1f983-164">Toutes les valeurs commençant par « contoso » peuvent être transmises au paramètre.</span><span class="sxs-lookup"><span data-stu-id="1f983-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="1f983-165">Les meilleures pratiques de sécurité déconseillent d’utiliser des caractères génériques pour définir des fonctions ou des applets de commande visibles.</span><span class="sxs-lookup"><span data-stu-id="1f983-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="1f983-166">Au contraire, listez explicitement chaque commande approuvée de façon qu’aucune autre commande partageant le même schéma d’affectation de noms ne soit autorisée par inadvertance.</span><span class="sxs-lookup"><span data-stu-id="1f983-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="1f983-167">Vous ne pouvez pas appliquer à la fois un ValidatePattern et un ValidateSet à la même applet de commande ou fonction.</span><span class="sxs-lookup"><span data-stu-id="1f983-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="1f983-168">Si vous le faites, le ValidatePattern remplacera le ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="1f983-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="1f983-169">Pour plus d’informations sur ValidatePattern, consultez [cet article *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) et le contenu de référence [Expressions régulières PowerShell](https://technet.microsoft.com/library/hh847880.aspx).</span><span class="sxs-lookup"><span data-stu-id="1f983-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="1f983-170">Autoriser des commandes externes et des scripts PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f983-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="1f983-171">Pour permettre aux utilisateurs de lancer des exécutables et des scripts PowerShell (.ps1) dans une session JEA, vous devez ajouter le chemin d’accès complet de chaque programme dans le champ VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="1f983-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="1f983-172">Il est recommandé, si possible, d’utiliser des applets de commande/fonctions PowerShell équivalentes de tous les exécutables externes que vous autorisez, car vous contrôlez les paramètres autorisés avec les applets de commande/fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f983-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="1f983-173">De nombreux exécutables permettent de lire l’état actuel puis de le modifier en fournissant simplement d’autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f983-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="1f983-174">Par exemple, prenons le rôle d’un administrateur de serveurs de fichiers qui souhaite connaître les partages réseau hébergés par l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1f983-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="1f983-175">Il est possible pour cela d’utiliser `net share`.</span><span class="sxs-lookup"><span data-stu-id="1f983-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="1f983-176">Toutefois, autoriser net.exe est très dangereux, car l’administrateur pourrait tout aussi facilement utiliser la commande pour obtenir des privilèges Administrateur avec `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="1f983-176">However, allowing net.exe is very dangerous because the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="1f983-177">Il est préférable d’autoriser [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx), qui donne le même résultat mais a une portée bien plus limitée.</span><span class="sxs-lookup"><span data-stu-id="1f983-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="1f983-178">Quand vous mettez des commandes externes à la disposition des utilisateurs dans une session JEA, spécifiez toujours le chemin complet de l’exécutable pour éviter qu’un programme portant le même nom (et potentiellement malveillant), placé ailleurs sur le système, ne soit exécuté à la place.</span><span class="sxs-lookup"><span data-stu-id="1f983-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicious) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="1f983-179">Autoriser l’accès aux fournisseurs PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f983-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="1f983-180">Par défaut, les fournisseurs PowerShell sont disponibles dans les sessions JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="1f983-181">Il s’agit principalement de réduire le risque de divulgation d’informations sensibles et de paramètres de configuration à l’utilisateur qui établit la connexion.</span><span class="sxs-lookup"><span data-stu-id="1f983-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="1f983-182">Si nécessaire, vous pouvez autoriser l’accès aux fournisseurs de PowerShell à l’aide de la commande `VisibleProviders`.</span><span class="sxs-lookup"><span data-stu-id="1f983-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="1f983-183">Pour obtenir la liste complète des fournisseurs, exécutez `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="1f983-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="1f983-184">Pour des tâches simples qui requièrent l’accès au système de fichiers, au registre, au magasin de certificats ou à d’autres fournisseurs sensibles, vous pouvez également envisager d’écrire une fonction personnalisée qui fonctionne avec le fournisseur au nom de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1f983-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="1f983-185">Les fonctions, applets de commande et programmes externes disponibles dans une session JEA ne sont pas soumis aux mêmes contraintes que JEA : ils peuvent accéder à tous les fournisseurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="1f983-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="1f983-186">Envisagez également d’utiliser le [lecteur utilisateur](session-configurations.md#user-drive) lorsqu’il est nécessaire de copier des fichiers vers/à partir d’un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="1f983-187">Créer des fonctions personnalisées</span><span class="sxs-lookup"><span data-stu-id="1f983-187">Creating custom functions</span></span>

<span data-ttu-id="1f983-188">Vous pouvez créer des fonctions personnalisées dans un fichier de capacités de rôle pour simplifier les tâches complexes de vos utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="1f983-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="1f983-189">Les fonctions personnalisées sont également utiles lorsque vous avez besoin d’une logique de validation avancée pour les valeurs de paramètres des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="1f983-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="1f983-190">Vous pouvez écrire des fonctions simples dans le champ **FunctionDefinitions** :</span><span class="sxs-lookup"><span data-stu-id="1f983-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="1f983-191">N’oubliez pas d’ajouter le nom de vos fonctions personnalisées au champ **VisibleFunctions** pour qu’elles puissent être exécutées par les utilisateurs JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="1f983-192">Le corps (bloc de script) des fonctions personnalisées s’exécute dans le mode de langage par défaut du système et n’est pas soumis aux contraintes de langage de JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="1f983-193">Cela signifie que les fonctions peuvent accéder au système de fichiers et au registre, puis exécuter des commandes qui n’étaient pas visibles dans le fichier de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1f983-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="1f983-194">Prenez soin d’éviter d’autoriser l’exécution de code arbitraire lorsque vous utilisez les paramètres et d’éviter d’injecter directement l’entrée utilisateur dans des applets de commande comme `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="1f983-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="1f983-195">Dans l’exemple ci-dessus, vous remarquerez que le nom du module complet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` a été utilisé à la place du nom raccourci `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="1f983-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="1f983-196">Les fonctions définies dans les fichiers de capacités de rôle sont toujours soumises à la portée des sessions JEA, qui comprend les fonctions de proxy créées par JEA pour contraindre les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="1f983-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="1f983-197">Select-Object est une applet de commande contrainte par défaut dans toutes les sessions JEA qui ne vous permet pas de sélectionner des propriétés arbitraires sur les objets.</span><span class="sxs-lookup"><span data-stu-id="1f983-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="1f983-198">Pour utiliser Select-Object sans contraintes dans les fonctions, vous devez demander explicitement l’implémentation complète en spécifiant le FQMN.</span><span class="sxs-lookup"><span data-stu-id="1f983-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="1f983-199">Une applet de commande contrainte dans une session JEA présente le même comportement lorsqu’elle est appelée à partir d’une fonction, conformément à la [précédence des commandes](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f983-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="1f983-200">Si vous écrivez de nombreuses fonctions personnalisées, il peut être plus facile de les placer dans un [Module de script PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1f983-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="1f983-201">Vous pouvez ensuite rendre ces fonctions visibles dans la session JEA à l’aide du champ VisibleFunctions, comme avec des modules intégrés et tiers.</span><span class="sxs-lookup"><span data-stu-id="1f983-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

<span data-ttu-id="1f983-202">Pour que la complétion avec la touche TAB fonctionne correctement dans les sessions JEA, vous devez inclure la fonction intégrée `tabexpansion2` dans la liste **VisibleFunctions**.</span><span class="sxs-lookup"><span data-stu-id="1f983-202">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="1f983-203">Placer les capacités de rôle dans un module</span><span class="sxs-lookup"><span data-stu-id="1f983-203">Place role capabilities in a module</span></span>

<span data-ttu-id="1f983-204">Pour que PowerShell trouve un fichier de capacités de rôle, celui-ci doit être stocké dans le dossier « RoleCapabilities » d’un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f983-204">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="1f983-205">Le module peut être stocké dans un dossier inclus dans la variable d’environnement `$env:PSModulePath`, cependant vous ne devez pas le placer dans System32 (réservé aux modules intégrés) ou dans un dossier où des utilisateurs non fiables qui établissent la connexion pourraient modifier les fichiers.</span><span class="sxs-lookup"><span data-stu-id="1f983-205">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="1f983-206">Voici un exemple de création d’un module de script PowerShell de base, appelé *ContosoJEA* dans le chemin d’accès « Program Files ».</span><span class="sxs-lookup"><span data-stu-id="1f983-206">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="1f983-207">Consultez la page [Comprendre un module PowerShell](https://msdn.microsoft.com/library/dd878324.aspx) pour plus d’informations sur les modules PowerShell, les manifestes de modules et la variable d’environnement PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="1f983-207">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="1f983-208">Mettre à jour les capacités de rôle</span><span class="sxs-lookup"><span data-stu-id="1f983-208">Updating role capabilities</span></span>

<span data-ttu-id="1f983-209">Vous pouvez mettre à jour un fichier de capacités de rôle à tout moment en enregistrant simplement les modifications dans le fichier de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1f983-209">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="1f983-210">Les nouvelles sessions JEA lancées après la mise à jour de la capacité du rôle reflèteront les fonctionnalités modifiées.</span><span class="sxs-lookup"><span data-stu-id="1f983-210">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="1f983-211">C’est pourquoi il est très important de contrôler l’accès au dossier de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1f983-211">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="1f983-212">Seuls les administrateurs de confiance doivent pouvoir modifier les fichiers de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1f983-212">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="1f983-213">Si un utilisateur non fiable peut modifier les fichiers de capacités de rôle, il peut facilement s’accorder l’accès aux applets de commande qui lui permettront d’élever ses privilèges.</span><span class="sxs-lookup"><span data-stu-id="1f983-213">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>

<span data-ttu-id="1f983-214">Les administrateurs qui souhaitent verrouiller l’accès aux capacités de rôle doivent vérifier que le système local a un accès en lecture aux fichiers de capacités de rôle et aux modules qui les contiennent.</span><span class="sxs-lookup"><span data-stu-id="1f983-214">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="1f983-215">Fusionner les capacités de rôle</span><span class="sxs-lookup"><span data-stu-id="1f983-215">How role capabilities are merged</span></span>

<span data-ttu-id="1f983-216">Les utilisateurs peuvent accéder à plusieurs capacités de rôle lorsqu’ils intègrent une session JEA en fonction du mappage des rôles dans le [fichier de configuration de session](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="1f983-216">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="1f983-217">Dans ce cas, JEA tente de donner à l’utilisateur l’ensemble de commandes *le plus permissif* autorisé par les rôles.</span><span class="sxs-lookup"><span data-stu-id="1f983-217">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="1f983-218">**VisibleCmdlets et VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="1f983-218">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="1f983-219">La logique de fusion la plus complexe affecte les applets de commande et les fonctions, dont les paramètres et les valeurs de paramètres peuvent être limités dans JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-219">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="1f983-220">Les règles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f983-220">The rules are as follows:</span></span>

1. <span data-ttu-id="1f983-221">Si une applet de commande n’est visible que dans un rôle, elle sera visible par l’utilisateur avec n’importe quelles contraintes de paramètres applicables.</span><span class="sxs-lookup"><span data-stu-id="1f983-221">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="1f983-222">Si une applet de commande est visible dans plusieurs rôles, et que chaque rôle a les mêmes contraintes sur l’applet de commande, l’applet de commande sera visible par l’utilisateur avec ces contraintes.</span><span class="sxs-lookup"><span data-stu-id="1f983-222">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="1f983-223">Si une applet de commande est visible dans plusieurs rôles, et que les rôles autorisent différents ensembles de paramètres, l’applet de commande et tous les paramètres définis sur tous les rôles seront visibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1f983-223">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="1f983-224">Si un rôle n’a pas de contraintes sur les paramètres, tous les paramètres seront autorisées.</span><span class="sxs-lookup"><span data-stu-id="1f983-224">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="1f983-225">Si un rôle définit un ensemble ou un modèle de validation d’un paramètre d’applet de commande, et que l’autre rôle autorise le paramètre mais ne contraint pas les valeurs du paramètre, l’ensemble ou le modèle de validation sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="1f983-225">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="1f983-226">Si un ensemble de validation est défini pour le même paramètre d’applet de commande dans plusieurs rôles, toutes les valeurs de tous les ensembles de validation seront autorisées.</span><span class="sxs-lookup"><span data-stu-id="1f983-226">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="1f983-227">Si un modèle de validation est défini pour le même paramètre d’applet de commande dans plusieurs rôles, toutes les valeurs qui correspondent aux modèles seront autorisées.</span><span class="sxs-lookup"><span data-stu-id="1f983-227">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="1f983-228">Si un ensemble de validation est défini dans un ou plusieurs rôles, et qu’un modèle de validation est défini dans un autre rôle pour le même paramètre d’applet de commande, l’ensemble de validation est ignoré et la règle (6) s’applique aux modèles de validation restants.</span><span class="sxs-lookup"><span data-stu-id="1f983-228">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="1f983-229">Vous trouverez ci-dessous un exemple de la façon dont les rôles sont fusionnés en fonction de ces règles :</span><span class="sxs-lookup"><span data-stu-id="1f983-229">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

<span data-ttu-id="1f983-230">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="1f983-230">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="1f983-231">Tous les autres champs du fichier de capacités de rôle sont simplement ajoutés à un ensemble cumulatif de commandes externes admissibles, d’alias, de fournisseurs et de scripts de démarrage.</span><span class="sxs-lookup"><span data-stu-id="1f983-231">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="1f983-232">Les commandes, alias, fournisseurs ou scripts disponibles dans une capacité de rôle seront accessibles à l’utilisateur JEA.</span><span class="sxs-lookup"><span data-stu-id="1f983-232">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="1f983-233">Veillez à ce que l’ensemble combiné de fournisseurs d’une capacité de rôle et les applets de commande/fonctions/commandes d’une autre n’autorisent pas les utilisateurs connectés à accéder involontairement aux ressources système.</span><span class="sxs-lookup"><span data-stu-id="1f983-233">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="1f983-234">Par exemple, si un rôle autorise l’applet de commande `Remove-Item` et un autre le fournisseur `FileSystem`, il existe un risque qu’un utilisateur JEA supprime des fichiers arbitraires sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1f983-234">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="1f983-235">Vous trouverez des informations supplémentaires sur l’identification des autorisations effectives des utilisateurs dans la [rubrique Audit de JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="1f983-235">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f983-236">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f983-236">Next steps</span></span>

- [<span data-ttu-id="1f983-237">Créer un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="1f983-237">Create a session configuration file</span></span>](session-configurations.md)
