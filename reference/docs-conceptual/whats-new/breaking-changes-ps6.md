---
ms.date: 02/03/2020
keywords: powershell,core
title: Modifications avec rupture dans PowerShell 6.0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995464"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="6def5-103">Modifications avec rupture dans PowerShell 6.x</span><span class="sxs-lookup"><span data-stu-id="6def5-103">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="6def5-104">Fonctionnalités qui ne sont plus disponibles dans PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6def5-104">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="6def5-105">Modules non livrés pour PowerShell 6.x</span><span class="sxs-lookup"><span data-stu-id="6def5-105">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="6def5-106">Pour différentes raisons de compatibilité, les modules suivants ne sont pas inclus dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="6def5-106">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="6def5-107">ISE</span><span class="sxs-lookup"><span data-stu-id="6def5-107">ISE</span></span>
- <span data-ttu-id="6def5-108">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="6def5-108">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="6def5-109">Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="6def5-109">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="6def5-110">Microsoft.PowerShell.Operation.Validation</span><span class="sxs-lookup"><span data-stu-id="6def5-110">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="6def5-111">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6def5-111">PSScheduledJob</span></span>
- <span data-ttu-id="6def5-112">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="6def5-112">PSWorkflow</span></span>
- <span data-ttu-id="6def5-113">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="6def5-113">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="6def5-114">PowerShell Workflow</span><span class="sxs-lookup"><span data-stu-id="6def5-114">PowerShell Workflow</span></span>

<span data-ttu-id="6def5-115">[PowerShell Workflow][workflow] est une fonctionnalité de Windows PowerShell qui s’appuie sur [Windows Workflow Foundation (WF)][workflow-foundation] et permet de créer des runbooks robustes pour les tâches de longue durée ou parallélisées.</span><span class="sxs-lookup"><span data-stu-id="6def5-115">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="6def5-116">En raison du manque de support pour Windows Workflow Foundation dans .NET Core, nous ne prendrons plus en charge PowerShell Workflow dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="6def5-116">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="6def5-117">À l’avenir, nous aimerions activer le parallélisme/la concurrence natif(ve) dans le langage PowerShell sans utiliser PowerShell Workflow.</span><span class="sxs-lookup"><span data-stu-id="6def5-117">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="6def5-118">S’il est nécessaire d’utiliser des points de contrôle pour reprendre un script après le redémarrage du système d’exploitation, nous vous recommandons d’utiliser Planificateur de tâches pour exécuter un script au démarrage du système d’exploitation, mais le script doit conserver son propre état (par exemple, le rendre persistant dans un fichier).</span><span class="sxs-lookup"><span data-stu-id="6def5-118">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="6def5-119">Composants logiciels enfichables personnalisés</span><span class="sxs-lookup"><span data-stu-id="6def5-119">Custom snap-ins</span></span>

<span data-ttu-id="6def5-120">[Les composants logiciels enfichables PowerShell][snapin] sont les prédécesseurs des modules PowerShell qui ne bénéficient pas d’une adoption répandue dans la communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6def5-120">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="6def5-121">En raison de la complexité de la prise en charge des composants logiciels enfichables et leur sous-utilisation au sein de la communauté, nous ne prenons plus en charge les composants logiciels enfichables personnalisés dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="6def5-121">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="6def5-122">Aujourd’hui, cela arrête les modules `ActiveDirectory` et `DnsClient` dans Windows et Windows Server.</span><span class="sxs-lookup"><span data-stu-id="6def5-122">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="6def5-123">Cmdlets WMI v1</span><span class="sxs-lookup"><span data-stu-id="6def5-123">WMI v1 cmdlets</span></span>

<span data-ttu-id="6def5-124">En raison de la complexité de la prise en charge de deux ensembles de modules basés sur WMI, nous avons supprimé les cmdlets WMI v1 de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6def5-124">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="6def5-125">Au lieu de cela, nous vous recommandons d’utiliser les cmdlets CIM (également appelés WMI v2) qui offrent le même fonctionnement avec des fonctionnalités et une syntaxe nouvelles :</span><span class="sxs-lookup"><span data-stu-id="6def5-125">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="6def5-126">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="6def5-126">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="6def5-127">En raison de l’utilisation des API non prises en charge, `Microsoft.PowerShell.LocalAccounts` a été supprimé de PowerShell jusqu’à ce qu’une meilleure solution soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="6def5-127">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="6def5-128">Cmdlet `New-WebServiceProxy` supprimée</span><span class="sxs-lookup"><span data-stu-id="6def5-128">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="6def5-129">.NET Core ne prend pas en charge l’infrastructure de communication Windows, qui fournit des services pour l’utilisation du protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="6def5-129">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="6def5-130">Cette cmdlet a été supprimée, car elle nécessite SOAP.</span><span class="sxs-lookup"><span data-stu-id="6def5-130">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="6def5-131">Cmdlets `*-Transaction` supprimées</span><span class="sxs-lookup"><span data-stu-id="6def5-131">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="6def5-132">Ces cmdlets ont une utilisation très limitée.</span><span class="sxs-lookup"><span data-stu-id="6def5-132">These cmdlets had very limited usage.</span></span> <span data-ttu-id="6def5-133">Il a été décidé de ne plus les prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="6def5-133">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="6def5-134">Cmdlets de sécurité non disponibles sur les plateformes autres que Windows</span><span class="sxs-lookup"><span data-stu-id="6def5-134">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="6def5-135">`*-Computer` et autres cmdlets spécifiques à Windows</span><span class="sxs-lookup"><span data-stu-id="6def5-135">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="6def5-136">En raison de l’utilisation d’API non prises en charge, les applets de commande suivantes ont été supprimées de PowerShell Core jusqu’à ce qu’une meilleure solution soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="6def5-136">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a><span data-ttu-id="6def5-137">Cmdlets `*-Counter`</span><span class="sxs-lookup"><span data-stu-id="6def5-137">`*-Counter` cmdlets</span></span>

<span data-ttu-id="6def5-138">En raison de l’utilisation des API non prises en charge, `*-Counter` a été supprimé de PowerShell jusqu’à ce qu’une meilleure solution soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="6def5-138">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="6def5-139">Cmdlets `*-EventLog`</span><span class="sxs-lookup"><span data-stu-id="6def5-139">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="6def5-140">En raison de l’utilisation des API non prises en charge, `*-EventLog` a été supprimé de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6def5-140">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="6def5-141">jusqu’à ce qu’une meilleure solution soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="6def5-141">until a better solution is found.</span></span> <span data-ttu-id="6def5-142">`Get-WinEvent` et `Create-WinEvent` sont disponibles pour obtenir et créer des événements sur Windows.</span><span class="sxs-lookup"><span data-stu-id="6def5-142">`Get-WinEvent` and `Create-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="6def5-143">Les cmdlets qui utilisent WPF ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="6def5-143">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="6def5-144">WPF n’est pas pris en charge sur CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6def5-144">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="6def5-145">Les cmdlets suivantes sont affectées :</span><span class="sxs-lookup"><span data-stu-id="6def5-145">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="6def5-146">Le paramètre **showwindow** de `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="6def5-146">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="6def5-147">Certaines cmdlets DSC supprimées</span><span class="sxs-lookup"><span data-stu-id="6def5-147">Some DSC cmdlets removed</span></span>

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a><span data-ttu-id="6def5-148">Modifications apportées au moteur/langage</span><span class="sxs-lookup"><span data-stu-id="6def5-148">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a><span data-ttu-id="6def5-149">Renommer `powershell.exe` pour `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="6def5-149">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="6def5-150">Afin d’offrir aux utilisateurs une solution déterministe pour appeler PowerShell Core sur Windows (par opposition à Windows PowerShell), le fichier binaire PowerShell Core a été remplacé par `pwsh.exe` sur Windows et `pwsh` sur les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="6def5-150">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="6def5-151">Le nom abrégé est également cohérent avec la désignation des shells sur les plateformes non Windows.</span><span class="sxs-lookup"><span data-stu-id="6def5-151">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a><span data-ttu-id="6def5-152">Ne pas insérer de sauts de ligne en sortie (sauf pour les tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="6def5-152">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="6def5-153">Auparavant, la sortie était alignée sur la largeur de la console et des sauts de ligne étaient ajoutés à la largeur de fin de la console, ce qui signifie que la sortie n’était pas reformatée comme prévu si le terminal était redimensionné.</span><span class="sxs-lookup"><span data-stu-id="6def5-153">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="6def5-154">Cette modification n’a pas été appliquée aux tables, car les sauts de ligne sont nécessaires pour garantir l’alignement des colonnes.</span><span class="sxs-lookup"><span data-stu-id="6def5-154">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a><span data-ttu-id="6def5-155">Ignorer la vérification de l’élément null pour les collections avec un élément de type valeur [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="6def5-155">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="6def5-156">Pour le paramètre `Mandatory` et les attributs `ValidateNotNull` et `ValidateNotNullOrEmpty`, ignorer la vérification de l’élément null si le type d’élément de la collection est de type valeur.</span><span class="sxs-lookup"><span data-stu-id="6def5-156">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a><span data-ttu-id="6def5-157">Modifier `$OutputEncoding` pour utiliser l’encodage `UTF-8 NoBOM` plutôt qu’ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="6def5-157">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="6def5-158">L’encodage précédent, ASCII (7 bits) causait une modification incorrecte de la sortie dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="6def5-158">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="6def5-159">Cette modification vise à faire de `UTF-8 NoBOM` la valeur par défaut, qui conserve la sortie Unicode avec un encodage pris en charge par la plupart des outils et systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6def5-159">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a><span data-ttu-id="6def5-160">Supprimer `AllScope` de la plupart des alias par défaut [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="6def5-160">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="6def5-161">Pour accélérer la création d’étendue, `AllScope` a été supprimé de la plupart des alias par défaut.</span><span class="sxs-lookup"><span data-stu-id="6def5-161">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="6def5-162">`AllScope` a été conservé pour quelques alias fréquemment utilisés, où la recherche était plus rapide.</span><span class="sxs-lookup"><span data-stu-id="6def5-162">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a><span data-ttu-id="6def5-163">`-Verbose` et `-Debug` ne remplacent plus `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="6def5-163">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="6def5-164">Auparavant, si `-Verbose` ou `-Debug` était spécifié, il remplaçait le comportement de `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="6def5-164">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="6def5-165">Avec cette modification, `-Verbose` et `-Debug` n’affectent plus le comportement de `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="6def5-165">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="6def5-166">Modifications apportées aux cmdlets</span><span class="sxs-lookup"><span data-stu-id="6def5-166">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a><span data-ttu-id="6def5-167">Invoke-RestMethod ne retourne pas d’informations utiles quand aucune donnée n’est retournée.</span><span class="sxs-lookup"><span data-stu-id="6def5-167">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="6def5-168">#5320</span><span class="sxs-lookup"><span data-stu-id="6def5-168">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="6def5-169">Lorsqu’une API retourne simplement `null`, Invoke-RestMethod sérialisait cet élément comme la chaîne `"null"` au lieu de `$null`.</span><span class="sxs-lookup"><span data-stu-id="6def5-169">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="6def5-170">Cette modification résout la logique dans `Invoke-RestMethod` pour sérialiser correctement une seule valeur JSON valide `null` de manière littérale en tant que `$null`.</span><span class="sxs-lookup"><span data-stu-id="6def5-170">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a><span data-ttu-id="6def5-171">Supprimer `-Protocol` des cmdlets `*-Computer`[#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="6def5-171">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="6def5-172">En raison de problèmes avec l’accès à distance RPC dans CoreFX (en particulier sur les plateformes non Windows) et en vue de garantir une expérience cohérente de la communication à distance dans PowerShell, le paramètre `-Protocol` a été supprimé des cmdlets `\*-Computer`.</span><span class="sxs-lookup"><span data-stu-id="6def5-172">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="6def5-173">DCOM n’est plus pris en charge pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="6def5-173">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="6def5-174">Les applets de commande suivantes prennent en charge seulement la communication à distance WSMAN :</span><span class="sxs-lookup"><span data-stu-id="6def5-174">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="6def5-175">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="6def5-175">Rename-Computer</span></span>
- <span data-ttu-id="6def5-176">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="6def5-176">Restart-Computer</span></span>
- <span data-ttu-id="6def5-177">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="6def5-177">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a><span data-ttu-id="6def5-178">Supprimer `-ComputerName` des cmdlets `*-Service`[#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="6def5-178">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="6def5-179">Pour favoriser l’utilisation cohérente de PSRP, le paramètre `-ComputerName` a été supprimé des cmdlets `*-Service`.</span><span class="sxs-lookup"><span data-stu-id="6def5-179">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a><span data-ttu-id="6def5-180">Corriger `Get-Item -LiteralPath a*b` si `a*b` n’existe pas réellement pour retourner l’erreur [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="6def5-180">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="6def5-181">Auparavant, `-LiteralPath` avec un caractère générique le traitait de la même façon que `-Path` et si le caractère générique ne trouvait aucun fichier, il s’arrêtait en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="6def5-181">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="6def5-182">Le comportement correct doit être que `-LiteralPath` est littéral, donc si le fichier n’existe pas, il doit afficher une erreur.</span><span class="sxs-lookup"><span data-stu-id="6def5-182">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="6def5-183">La modification consiste à traiter les caractères génériques utilisés avec `-Literal` en tant qu’éléments littéraux.</span><span class="sxs-lookup"><span data-stu-id="6def5-183">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a><span data-ttu-id="6def5-184">`Import-Csv` doit appliquer `PSTypeNames` lors de l’importation lorsque les informations de type sont présentes dans le CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="6def5-184">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="6def5-185">Auparavant, les objets exportés utilisant `Export-CSV` avec `TypeInformation` importé avec `ConvertFrom-Csv` ne conservaient pas les informations de type.</span><span class="sxs-lookup"><span data-stu-id="6def5-185">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="6def5-186">Cette modification ajoute des informations de type au membre `PSTypeNames` s’il est disponible dans le fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="6def5-186">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a><span data-ttu-id="6def5-187">`-NoTypeInformation` doit prendre la valeur par défaut `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="6def5-187">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="6def5-188">Cette modification a été apportée suite à des commentaires client sur le comportement par défaut de `Export-CSV` pour inclure les informations de type.</span><span class="sxs-lookup"><span data-stu-id="6def5-188">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="6def5-189">Auparavant, la cmdlet affichait un commentaire en tant que première ligne contenant le nom du type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6def5-189">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="6def5-190">La modification consiste à supprimer cela par défaut, car cette opération n’est pas comprise par la plupart des outils.</span><span class="sxs-lookup"><span data-stu-id="6def5-190">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="6def5-191">Utilisez `-IncludeTypeInformation` pour conserver le comportement précédent.</span><span class="sxs-lookup"><span data-stu-id="6def5-191">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a><span data-ttu-id="6def5-192">Les cmdlets web doivent signaler lorsque `-Credential` est envoyé via des connexions non chiffrées [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="6def5-192">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="6def5-193">Lorsque vous utilisez HTTP, le contenu, notamment les mots de passe, est envoyé en texte clair.</span><span class="sxs-lookup"><span data-stu-id="6def5-193">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="6def5-194">Cette modification consiste à ne pas autoriser ce comportement par défaut et à retourner une erreur si les informations d’identification sont transmises de façon non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="6def5-194">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="6def5-195">Les utilisateurs peuvent contourner cela à l’aide du commutateur `-AllowUnencryptedAuthentication`.</span><span class="sxs-lookup"><span data-stu-id="6def5-195">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="6def5-196">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="6def5-196">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a><span data-ttu-id="6def5-197">Classe `AddTypeCommandBase` supprimée [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="6def5-197">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="6def5-198">La classe `AddTypeCommandBase` a été supprimée de `Add-Type` pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="6def5-198">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="6def5-199">Cette classe est utilisée uniquement par la cmdlet Add-Type et ne devrait pas affecter les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6def5-199">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a><span data-ttu-id="6def5-200">Unifier les cmdlets avec le paramètre `-Encoding` de type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="6def5-200">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="6def5-201">`-Encoding` avec la valeur `Byte` a été supprimé des cmdlets du fournisseur de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="6def5-201">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="6def5-202">Un nouveau paramètre, `-AsByteStream`, est désormais utilisé pour spécifier qu’un flux d’octets est requis en tant qu’entrée ou que la sortie est un flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="6def5-202">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a><span data-ttu-id="6def5-203">Ajouter un meilleur message d’erreur si le paramètre `-UFormat` est vide ou null [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="6def5-203">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="6def5-204">Auparavant, lors de l’envoi d’une chaîne de format vide à `-UFormat`, un message d’erreur inutile s’affichait.</span><span class="sxs-lookup"><span data-stu-id="6def5-204">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="6def5-205">Une erreur plus descriptive a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="6def5-205">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a><span data-ttu-id="6def5-206">Nettoyer le code de la console [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="6def5-206">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="6def5-207">Les fonctionnalités suivantes ont été supprimées car elles ne sont pas prises en charge dans PowerShell Core, et il n’est pas prévu d’ajouter leur prise en charge, car elles existent pour des raisons d’héritage pour Windows PowerShell : commutateur et code `-psconsolefile`, commutateur et code `-importsystemmodules`, et code de modification de police.</span><span class="sxs-lookup"><span data-stu-id="6def5-207">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a><span data-ttu-id="6def5-208">Prise en charge de `RunspaceConfiguration` supprimée [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span><span class="sxs-lookup"><span data-stu-id="6def5-208">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="6def5-209">Auparavant, lors de la création d’une instance d’exécution PowerShell par programmation à l’aide de l’API, vous pouviez utiliser [`RunspaceConfiguration`][runspaceconfig] hérité ou [`InitialSessionState`][iss] plus récent.</span><span class="sxs-lookup"><span data-stu-id="6def5-209">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="6def5-210">Cette modification supprime la prise en charge de `RunspaceConfiguration` et prend uniquement en charge `InitialSessionState`.</span><span class="sxs-lookup"><span data-stu-id="6def5-210">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a><span data-ttu-id="6def5-211">`CommandInvocationIntrinsics.InvokeScript` lie les arguments à `$input` au lieu de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="6def5-211">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="6def5-212">En raison d’une position incorrecte d’un paramètre, les arguments étaient passés en tant qu’entrée au lieu d’arguments.</span><span class="sxs-lookup"><span data-stu-id="6def5-212">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a><span data-ttu-id="6def5-213">Supprimer le commutateur `-showwindow` non pris en charge de `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="6def5-213">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="6def5-214">`-showwindow` s’appuie sur WPF, qui n’est pas pris en charge dans CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6def5-214">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a><span data-ttu-id="6def5-215">Autoriser l’utilisation de \* dans le chemin du registre pour `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="6def5-215">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="6def5-216">Auparavant, `-LiteralPath` avec un caractère générique le traitait de la même façon que `-Path` et si le caractère générique ne trouvait aucun fichier, il s’arrêtait en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="6def5-216">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="6def5-217">Le comportement correct doit être que `-LiteralPath` est littéral, donc si le fichier n’existe pas, il doit afficher une erreur.</span><span class="sxs-lookup"><span data-stu-id="6def5-217">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="6def5-218">La modification consiste à traiter les caractères génériques utilisés avec `-Literal` en tant qu’éléments littéraux.</span><span class="sxs-lookup"><span data-stu-id="6def5-218">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a><span data-ttu-id="6def5-219">Corriger l’échec au test de `Set-Service`[#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="6def5-219">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="6def5-220">Auparavant, si `New-Service -StartupType foo` était utilisé, `foo` était ignoré et le service était créé avec un certain type de démarrage par défaut.</span><span class="sxs-lookup"><span data-stu-id="6def5-220">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="6def5-221">Cette modification vise à lever explicitement une erreur pour un type de démarrage non valide.</span><span class="sxs-lookup"><span data-stu-id="6def5-221">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a><span data-ttu-id="6def5-222">Renommer `$IsOSX` par `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="6def5-222">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="6def5-223">L’affectation de noms dans PowerShell doit être cohérente avec notre affectation de noms et conforme à l’utilisation d’Apple de macOS au lieu de OSX.</span><span class="sxs-lookup"><span data-stu-id="6def5-223">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="6def5-224">Toutefois, pour une lisibilité et une cohérence optimales, nous conservons la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="6def5-224">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a><span data-ttu-id="6def5-225">Uniformiser le message d’erreur lorsqu’un script non valide est transmis à -File, erreur optimisée lors de l’envoi d’un argument ambigu [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="6def5-225">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="6def5-226">Modifier les codes de sortie de `pwsh.exe` pour se conformer aux conventions Unix</span><span class="sxs-lookup"><span data-stu-id="6def5-226">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a><span data-ttu-id="6def5-227">Suppression de `LocalAccount` et des cmdlets des modules `Diagnostics`.</span><span class="sxs-lookup"><span data-stu-id="6def5-227">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="6def5-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="6def5-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="6def5-229">En raison d’API non prises en charge, le module `LocalAccounts` et les cmdlets `Counter` dans le module `Diagnostics` ont été supprimés jusqu’à ce qu’une meilleure solution soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="6def5-229">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a><span data-ttu-id="6def5-230">L’exécution du script PowerShell avec un paramètre bool ne fonctionne pas [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="6def5-230">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="6def5-231">Auparavant, l’utilisation de **powershell.exe** (désormais **pwsh.exe**) pour exécuter un script PowerShell à l’aide de `-File` ne fournissait aucun moyen de transmettre `$true`/`$false` comme valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6def5-231">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="6def5-232">La prise en charge de `$true`/`$false` comme valeurs analysées des paramètres a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="6def5-232">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="6def5-233">Les valeurs de commutateur sont également prises en charge, car la syntaxe actuellement documentée ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="6def5-233">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a><span data-ttu-id="6def5-234">Supprimer la propriété `ClrVersion` de `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="6def5-234">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="6def5-235">La propriété `ClrVersion` de `$PSVersionTable` n’est pas utile avec CoreCLR, les utilisateurs finaux ne doivent pas utiliser cette valeur pour déterminer la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="6def5-235">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a><span data-ttu-id="6def5-236">Modifier le paramètre positionnel pour `powershell.exe` de `-Command` par `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="6def5-236">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="6def5-237">Autoriser shebang à utiliser PowerShell sur les plateformes non Windows.</span><span class="sxs-lookup"><span data-stu-id="6def5-237">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="6def5-238">Cela signifie que sur les systèmes Unix, vous pouvez rendre un script exécutable qui appelle PowerShell automatiquement au lieu d’appeler explicitement `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="6def5-238">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="6def5-239">Cela signifie également que vous pouvez faire des choses comme `powershell foo.ps1` ou `powershell fooScript` sans spécifier `-File`.</span><span class="sxs-lookup"><span data-stu-id="6def5-239">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="6def5-240">Toutefois, cette modification nécessite désormais que vous indiquiez explicitement `-c` ou `-Command` quand vous essayez de faire des choses comme `powershell.exe Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="6def5-240">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a><span data-ttu-id="6def5-241">Implémenter l’analyse d’échappement Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="6def5-241">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="6def5-242">`` `u####`` ou `` `u{####}`` est converti en caractère Unicode correspondant.</span><span class="sxs-lookup"><span data-stu-id="6def5-242">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="6def5-243">Pour générer un `` `u`` littéral, appliquer l’échappement au guillemet inversé : ``` ``u```.</span><span class="sxs-lookup"><span data-stu-id="6def5-243">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a><span data-ttu-id="6def5-244">Modifier l’encodage `New-ModuleManifest` sur `UTF8NoBOM` pour les plateformes non Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="6def5-244">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="6def5-245">Auparavant, `New-ModuleManifest` créait les manifestes psd1 en UTF-16 avec BOM, causant un problème pour les outils Linux.</span><span class="sxs-lookup"><span data-stu-id="6def5-245">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="6def5-246">Cette modification avec rupture modifie l’encodage de `New-ModuleManifest` sur UTF (sans BOM) pour les plateformes non Windows.</span><span class="sxs-lookup"><span data-stu-id="6def5-246">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a><span data-ttu-id="6def5-247">Empêcher la récurrence de `Get-ChildItem` dans des liens symboliques (#1875).</span><span class="sxs-lookup"><span data-stu-id="6def5-247">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="6def5-248">#3780</span><span class="sxs-lookup"><span data-stu-id="6def5-248">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="6def5-249">Cette modification aligne `Get-ChildItem` avec `ls -r` Unix et les commandes natives `dir /s` Windows.</span><span class="sxs-lookup"><span data-stu-id="6def5-249">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="6def5-250">Comme les commandes mentionnées, la cmdlet affiche des liens symboliques vers les répertoires trouvés lors de la récursivité, mais elle n’est pas récursive dans ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="6def5-250">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a><span data-ttu-id="6def5-251">Corriger `Get-Content -Delimiter` pour ne pas inclure le délimiteur dans les lignes retournées [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="6def5-251">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="6def5-252">Auparavant, la sortie lors de l’utilisation de `Get-Content -Delimiter` était incohérente et peu pratique, car elle nécessitait un traitement supplémentaire des données pour supprimer le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="6def5-252">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="6def5-253">Cette modification supprime le délimiteur dans les lignes retournées.</span><span class="sxs-lookup"><span data-stu-id="6def5-253">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a><span data-ttu-id="6def5-254">Implémenter Format-Hex dans C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="6def5-254">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="6def5-255">Le paramètre `-Raw` est désormais un « no-op » (c’est-à-dire, qu’il ne fait rien).</span><span class="sxs-lookup"><span data-stu-id="6def5-255">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="6def5-256">À l’avenir, l’ensemble de la sortie sera affiché avec une représentation réelle des nombres incluant tous les octets pour son type (ce que le paramètre `-Raw` faisait formellement avant cette modification).</span><span class="sxs-lookup"><span data-stu-id="6def5-256">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a><span data-ttu-id="6def5-257">PowerShell en tant que shell par défaut ne fonctionne pas avec la commande de script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="6def5-257">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="6def5-258">Sous Unix, une convention stipule que les shells doivent accepter `-i` pour un shell interactif et de nombreux outils attendent ce comportement (`script` par exemple, et lorsque PowerShell est défini en tant que shell par défaut), et appelle le shell avec le commutateur `-i`.</span><span class="sxs-lookup"><span data-stu-id="6def5-258">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="6def5-259">Il s’agit d’une modification avec rupture, car `-i` pouvait auparavant être utilisé en tant que paramètre abrégé pour correspondre à `-inputformat`, qui doit maintenant être `-in`.</span><span class="sxs-lookup"><span data-stu-id="6def5-259">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a><span data-ttu-id="6def5-260">Correction typographique dans le nom de la propriété Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="6def5-260">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="6def5-261">`BiosSerialNumber` était mal orthographié en tant que `BiosSeralNumber` et a été remplacé par l’orthographe correcte.</span><span class="sxs-lookup"><span data-stu-id="6def5-261">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a><span data-ttu-id="6def5-262">Ajouter les cmdlets `Get-StringHash` et `Get-FileHash`[#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="6def5-262">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="6def5-263">Cette modification indique que certains algorithmes de hachage ne sont pas pris en charge par CoreFX, donc ils ne sont plus disponibles :</span><span class="sxs-lookup"><span data-stu-id="6def5-263">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a><span data-ttu-id="6def5-264">Ajouter la validation sur les cmdlets `Get-*` où la transmission de $null retourne tous les objets au lieu de l’erreur [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="6def5-264">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="6def5-265">La transmission de `$null` à l’un des éléments ci-dessous génère maintenant une erreur :</span><span class="sxs-lookup"><span data-stu-id="6def5-265">Passing `$null` to any of the following now throws an error:</span></span>

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a><span data-ttu-id="6def5-266">Ajouter le support Format de fichier journal étendu W3C dans `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="6def5-266">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="6def5-267">Auparavant, la cmdlet `Import-Csv` ne pouvait pas être utilisée pour importer directement les fichiers journaux au format de journal étendu W3C et une action supplémentaire était nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6def5-267">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="6def5-268">Avec cette modification, le format de journal étendu W3C est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6def5-268">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a><span data-ttu-id="6def5-269">Problème de liaison de paramètre avec `ValueFromRemainingArguments` dans les fonctions PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="6def5-269">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="6def5-270">`ValueFromRemainingArguments` retourne désormais les valeurs sous forme de tableau au lieu d’une seule valeur qui est elle-même un tableau.</span><span class="sxs-lookup"><span data-stu-id="6def5-270">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a><span data-ttu-id="6def5-271">`BuildVersion` est supprimé de `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="6def5-271">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="6def5-272">Suppression de la propriété `BuildVersion` de `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="6def5-272">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="6def5-273">Cette propriété était liée à la version de build Windows.</span><span class="sxs-lookup"><span data-stu-id="6def5-273">This property was tied to the Windows build version.</span></span> <span data-ttu-id="6def5-274">Au lieu de cela, nous vous recommandons d’utiliser `GitCommitId` pour récupérer la version de build exacte de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="6def5-274">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="6def5-275">Modifications apportées aux cmdlets web</span><span class="sxs-lookup"><span data-stu-id="6def5-275">Changes to Web Cmdlets</span></span>

<span data-ttu-id="6def5-276">L’API .NET sous-jacente des cmdlets web a été remplacée par `System.Net.Http.HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="6def5-276">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="6def5-277">Cette modification offre de nombreux avantages.</span><span class="sxs-lookup"><span data-stu-id="6def5-277">This change provides many benefits.</span></span> <span data-ttu-id="6def5-278">Toutefois, cette modification, ainsi qu’un manque d’interopérabilité avec Internet Explorer, ont causé plusieurs modifications avec rupture dans `Invoke-WebRequest` et `Invoke-RestMethod`.</span><span class="sxs-lookup"><span data-stu-id="6def5-278">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="6def5-279">`Invoke-WebRequest` prend désormais en charge l’analyse HTML de base uniquement.</span><span class="sxs-lookup"><span data-stu-id="6def5-279">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="6def5-280">`Invoke-WebRequest` retourne toujours un objet `BasicHtmlWebResponseObject`.</span><span class="sxs-lookup"><span data-stu-id="6def5-280">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="6def5-281">Les propriétés `ParsedHtml` et `Forms` ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="6def5-281">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="6def5-282">Les valeurs `BasicHtmlWebResponseObject.Headers` sont maintenant `String[]` au lieu de `String`.</span><span class="sxs-lookup"><span data-stu-id="6def5-282">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="6def5-283">`BasicHtmlWebResponseObject.BaseResponse` est désormais un objet `System.Net.Http.HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="6def5-283">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="6def5-284">La propriété `Response` sur les exceptions de cmdlet web est désormais un objet `System.Net.Http.HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="6def5-284">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="6def5-285">L’analyse d’en-tête RFC stricte est désormais la valeur par défaut pour les paramètres `-Headers` et `-UserAgent`.</span><span class="sxs-lookup"><span data-stu-id="6def5-285">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="6def5-286">Vous pouvez contourner ceci avec `-SkipHeaderValidation`.</span><span class="sxs-lookup"><span data-stu-id="6def5-286">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="6def5-287">Les schémas d’URI `file://` et `ftp://` ne sont plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6def5-287">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="6def5-288">Les paramètres `System.Net.ServicePointManager` ne sont plus respectés.</span><span class="sxs-lookup"><span data-stu-id="6def5-288">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="6def5-289">Aucune authentification par certificat n’est actuellement disponible sur macOS.</span><span class="sxs-lookup"><span data-stu-id="6def5-289">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="6def5-290">L’utilisation de `-Credential` sur un URI `http://` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="6def5-290">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="6def5-291">Utilisez un URI `https://` ou fournissez le paramètre `-AllowUnencryptedAuthentication` pour supprimer l’erreur.</span><span class="sxs-lookup"><span data-stu-id="6def5-291">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="6def5-292">`-MaximumRedirection` génère désormais une erreur avec fin d’exécution quand les tentatives de redirection dépassent la limite fournie au lieu de retourner les résultats de la dernière redirection.</span><span class="sxs-lookup"><span data-stu-id="6def5-292">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="6def5-293">Dans PowerShell 6.2, une modification a été apportée pour sélectionner par défaut à le codage UTF-8 pour les réponses JSON.</span><span class="sxs-lookup"><span data-stu-id="6def5-293">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="6def5-294">Lorsqu’un jeu de caractères n’est pas fourni pour une réponse JSON, le codage par défaut doit être UTF-8 par RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="6def5-294">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
