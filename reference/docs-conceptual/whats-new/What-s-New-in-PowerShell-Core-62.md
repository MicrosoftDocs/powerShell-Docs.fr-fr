---
title: Nouveautés de PowerShell Core 6.2
description: Nouvelles fonctionnalités et modifications de PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "76995476"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="decc1-103">Nouveautés de PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="decc1-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="decc1-104">La version PowerShell Core 6.2 offre de meilleures performances, des correctifs de bogues, des applets de commande plus compactes et un meilleur langage, garantissant plus de qualité.</span><span class="sxs-lookup"><span data-stu-id="decc1-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="decc1-105">Pour voir une liste complète des améliorations, consultez nos [journaux de modifications](https://github.com/PowerShell/PowerShell/releases) détaillés sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="decc1-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="decc1-106">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="decc1-106">Experimental Features</span></span>

<span data-ttu-id="decc1-107">Les [fonctionnalités expérimentales][] étaient auparavant prises en charge.</span><span class="sxs-lookup"><span data-stu-id="decc1-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="decc1-108">La version 6.2 propose quatre fonctionnalités expérimentales à tester. Veuillez nous faire part de vos commentaires pour nous permettre apporter des améliorations et décider si la fonctionnalité mérite d’être implémentée.</span><span class="sxs-lookup"><span data-stu-id="decc1-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="decc1-109">Utilisez `Get-ExperimentalFeature` pour obtenir la liste des fonctionnalités expérimentales disponibles.</span><span class="sxs-lookup"><span data-stu-id="decc1-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="decc1-110">Vous pouvez activer ou désactiver ces fonctionnalités avec `Enable-ExperimentalFeature` et `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="decc1-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="decc1-111">Suggestions en cas de commande introuvable</span><span class="sxs-lookup"><span data-stu-id="decc1-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="decc1-112">Cette fonctionnalité utilise la correspondance approximative afin de rechercher des suggestions pour les commandes ou applets de commande que vous avez peut-être mal saisies.</span><span class="sxs-lookup"><span data-stu-id="decc1-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="decc1-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="decc1-113">Example</span></span>

<span data-ttu-id="decc1-114">Dans cet exemple, le nom de l’applet de commande mal orthographié est mis en correspondance avec plusieurs suggestions, par ordre de probabilité.</span><span class="sxs-lookup"><span data-stu-id="decc1-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a><span data-ttu-id="decc1-115">Traitement par lot de la communication à distance implicite</span><span class="sxs-lookup"><span data-stu-id="decc1-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="decc1-116">Lorsque vous utilisez la [communication à distance implicite](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) dans un pipeline, PowerShell traite chaque commande du pipeline de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="decc1-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="decc1-117">Les objets sont sérialisés et `de-serialized` à plusieurs reprises entre le client et le système distant lors de l’exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="decc1-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="decc1-118">Avec cette fonctionnalité, PowerShell analyse le pipeline afin de déterminer si la commande peut s’exécuter sans risque et existe sur le système cible.</span><span class="sxs-lookup"><span data-stu-id="decc1-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="decc1-119">Si la valeur est true, PowerShell exécute à distance l’ensemble du pipeline, puis sérialise et `de-serializes` les résultats retournés au client.</span><span class="sxs-lookup"><span data-stu-id="decc1-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="decc1-120">Un test de `Get-Process | Sort-Object` en conditions réelles via localhost réduit le délai de 10-15 secondes à 20-30 **millisecondes**.</span><span class="sxs-lookup"><span data-stu-id="decc1-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="decc1-121">La fonctionnalité doit uniquement être activée sur le client.</span><span class="sxs-lookup"><span data-stu-id="decc1-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="decc1-122">Aucune modification n’est nécessaire sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="decc1-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="decc1-123">Lecteur temporaire</span><span class="sxs-lookup"><span data-stu-id="decc1-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="decc1-124">Si vous utilisez PowerShell Core sur différents systèmes d’exploitation, vous découvrirez que la variable d’environnement pour rechercher le répertoire temporaire est différente sur Windows, macOS et Linux !</span><span class="sxs-lookup"><span data-stu-id="decc1-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="decc1-125">Avec cette fonctionnalité, vous obtenez un [PSDrive][] appelé `Temp:` et automatiquement mappé au dossier temporaire du système d’exploitation que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="decc1-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="decc1-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="decc1-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="decc1-127">N’oubliez pas que les commandes de fichier natives (telles que `ls` sur Linux) ne reconnaissent pas les PSDrives et n’affichent pas le lecteur `Temp:`.</span><span class="sxs-lookup"><span data-stu-id="decc1-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="decc1-128">Expansion des abréviations</span><span class="sxs-lookup"><span data-stu-id="decc1-128">Abbreviation Expansion</span></span>

<span data-ttu-id="decc1-129">Les applets de commande PowerShell sont supposées afficher des noms descriptifs.</span><span class="sxs-lookup"><span data-stu-id="decc1-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="decc1-130">Cela entraîne des noms longs plus difficiles à saisir.</span><span class="sxs-lookup"><span data-stu-id="decc1-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="decc1-131">Cette fonctionnalité vous permet de saisir simplement les caractères majuscules de l’applet de commande et d’utiliser la saisie semi-automatique via la touche Tab pour rechercher une correspondance.</span><span class="sxs-lookup"><span data-stu-id="decc1-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="decc1-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="decc1-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="decc1-133">Si vous appuyez sur la touche Tab et que le module Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) est installé, la saisie semi-automatique sera appliquée à :</span><span class="sxs-lookup"><span data-stu-id="decc1-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="decc1-134">Cette fonctionnalité est destinée à être utilisée de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="decc1-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="decc1-135">Les formes abrégées des applets de commande ne peuvent pas être exécutées.</span><span class="sxs-lookup"><span data-stu-id="decc1-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="decc1-136">Cette fonctionnalité ne remplace pas les alias.</span><span class="sxs-lookup"><span data-stu-id="decc1-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="decc1-137">Dernières modifications</span><span class="sxs-lookup"><span data-stu-id="decc1-137">Breaking Changes</span></span>

- <span data-ttu-id="decc1-138">Correction du comportement de `-NoEnumerate` dans `Write-Output` pour le rendre cohérent avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="decc1-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="decc1-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="decc1-139">(#9069)</span></span>
- <span data-ttu-id="decc1-140">Modification du résultat `Join-String -InputObject 1,2,3` pour le rendre égal à `1,2,3 | Join-String` (#8611) (merci @sethvs !)</span><span class="sxs-lookup"><span data-stu-id="decc1-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="decc1-141">Ajout de `-Stable` à `Sort-Object` et aux tests associés (#7862) (merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="decc1-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="decc1-142">Amélioration de l’applet de commande `Start-Sleep` pour accepter les fractions de seconde (#8537) (merci @Prototyyppi !)</span><span class="sxs-lookup"><span data-stu-id="decc1-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="decc1-143">Modification de la table de hachage pour rendre OrdinalIgnoreCase `case-insensitive` dans toutes les cultures (#8566)</span><span class="sxs-lookup"><span data-stu-id="decc1-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="decc1-144">Correction de **LiteralPath** dans `Import-Csv` pour la liaison au résultat `Get-ChildItem` (#8277) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-145">N’ignore plus une colonne sans nom si le délimiteur de guillemet double est utilisé dans `Import-Csv` (#7899) (merci @Topping !)</span><span class="sxs-lookup"><span data-stu-id="decc1-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="decc1-146">`Get-ExperimentalFeature` ne comporte plus de commutateur `-ListAvailable` (#8318)</span><span class="sxs-lookup"><span data-stu-id="decc1-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="decc1-147">Le paramètre de débogage définit maintenant `$DebugPreference` sur **Continue** au lieu de **Inquire** (#8195) (merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="decc1-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="decc1-148">Honorer `-OutputFormat` si spécifié dans une commande non interactive, redirigée, encodée utilisée avec pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="decc1-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="decc1-149">Chargement de l’assembly à partir du chemin de base du module avant d’essayer de le charger à partir du GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="decc1-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="decc1-150">Suppression du tilde des packages en version préliminaire Linux (#8244)</span><span class="sxs-lookup"><span data-stu-id="decc1-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="decc1-151">Déplacement du traitement de `-WorkingDirectory` avant le traitement des profils (#8079)</span><span class="sxs-lookup"><span data-stu-id="decc1-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="decc1-152">Pas d’ajout de la variable d’environnement `PATHEXT` sur Unix (#7697) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="decc1-153">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="decc1-153">Known Issues</span></span>

- <span data-ttu-id="decc1-154">La communication à distance sur les plateformes Windows IOT ARM entraîne un problème de chargement des modules.</span><span class="sxs-lookup"><span data-stu-id="decc1-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="decc1-155">Voir (#8053)</span><span class="sxs-lookup"><span data-stu-id="decc1-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="decc1-156">Mises à jour et correctifs généraux</span><span class="sxs-lookup"><span data-stu-id="decc1-156">General Updates and Fixes</span></span>

- <span data-ttu-id="decc1-157">Activation de la saisie semi-automatique via la touche Tab pour les fichiers et dossiers sur le système de fichiers respectant la casse (#8128)</span><span class="sxs-lookup"><span data-stu-id="decc1-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="decc1-158">Publication de PSVersionInfo.PSVersion et PSVersionInfo.PSEdition (#8054) (merci @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="decc1-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="decc1-159">Ajout de l’inférence de type `$_` / `$PSItem` dans les blocs `catch{ }` (#8020) (merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="decc1-160">Correction de l’inférence de type d’appel à la méthode statique (#8018) (merci @SeeminglyScience !)</span><span class="sxs-lookup"><span data-stu-id="decc1-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="decc1-161">Création des types déduits pour `Select-Object`, `Group-Object`, **PSObject** et **Hashtable** (#7231) (merci @powercode !)</span><span class="sxs-lookup"><span data-stu-id="decc1-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="decc1-162">Prise en charge de la méthode d’appel avec les paramètres de type `ByRef-like` (#7721)</span><span class="sxs-lookup"><span data-stu-id="decc1-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="decc1-163">Gestion du cas où le chemin d’accès du module Windows PowerShell est déjà dans l’élément PSModulePath de l’environnement (#7727)</span><span class="sxs-lookup"><span data-stu-id="decc1-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="decc1-164">Activation des applets de commande `SecureString` pour Non-Windows en stockant le texte brut (#9199)</span><span class="sxs-lookup"><span data-stu-id="decc1-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="decc1-165">Amélioration du message d’erreur sur les systèmes non Windows lors de l’importation de clixml avec securestring (#7997)</span><span class="sxs-lookup"><span data-stu-id="decc1-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="decc1-166">Ajout du paramètre ReplyTo à `Send-MailMessage` (#8727) (merci @replicaJunction !)</span><span class="sxs-lookup"><span data-stu-id="decc1-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="decc1-167">Ajout d’un message obsolète à `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="decc1-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="decc1-168">Correctif `Restart-Computer` pour travailler sur `localhost` en l’absence de WinRM (#9160)</span><span class="sxs-lookup"><span data-stu-id="decc1-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="decc1-169">Amener `Start-Job` à générer une erreur de fin d’exécution lorsque PowerShell est hébergé (#9128)</span><span class="sxs-lookup"><span data-stu-id="decc1-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="decc1-170">Ajout d’accélérateurs de type de style C# et de suffixes pour ushort, uint, ulong et les littéraux courts (#7813) (merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="decc1-171">Ajout de nouveaux suffixes pour les littéraux numériques - [about_Numeric_Literals][] (#7901) (merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="decc1-172">Création d’un rapport correct sur le niveau d’impact lorsque SupportsShouldProcess n’est pas défini sur « true » (#8209) (merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="decc1-173">Correction des problèmes de jeu de caractères dans les applets de commande Web (#8742) (merci @markekraus !)</span><span class="sxs-lookup"><span data-stu-id="decc1-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="decc1-174">Correction du problème attendu `100-continue` avec les applets de commande Web (#8679) (merci @markekraus !)</span><span class="sxs-lookup"><span data-stu-id="decc1-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="decc1-175">Correction du problème de blocage de fichier avec les applets de commande Web (#7676) (merci @Claustn !)</span><span class="sxs-lookup"><span data-stu-id="decc1-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="decc1-176">Correction du problème d’analyse de la page de codes dans `Invoke-RestMethod` (#8694) (merci @markekraus !)</span><span class="sxs-lookup"><span data-stu-id="decc1-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="decc1-177">Refactorisation de `ConvertTo-Json` pour exposer JsonObject.ConvertToJson comme une API publique (#8682)</span><span class="sxs-lookup"><span data-stu-id="decc1-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="decc1-178">Ajout d’une profondeur maximale configurable dans `ConvertFrom-Json` avec -Depth (#8199) (merci @louistio !)</span><span class="sxs-lookup"><span data-stu-id="decc1-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="decc1-179">Ajout d’un paramètre EscapeHandling dans l’applet de commande `ConvertTo-Json` (#7775) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-180">Ajout de `-CustomPipeName` à pwsh et `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="decc1-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="decc1-181">Activation de la création de liens symboliques relatifs sur Windows avec `New-Item` (8783 #)</span><span class="sxs-lookup"><span data-stu-id="decc1-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="decc1-182">Autoriser les utilisateurs Windows en mode développeur à créer des liens symboliques sans élévation (#8534)</span><span class="sxs-lookup"><span data-stu-id="decc1-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="decc1-183">Activation de `Write-Information` pour accepter `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="decc1-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="decc1-184">Correctif `Get-Help` pour les fonctions avancées avec contenu d’aide MAML (8353 #)</span><span class="sxs-lookup"><span data-stu-id="decc1-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="decc1-185">Correction du problème `Get-Help` PSTypeName avec -Parameter lorsque qu’un seul paramètre est déclaré (#8754) (merci @pougetat !)</span><span class="sxs-lookup"><span data-stu-id="decc1-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="decc1-186">Correction du calcul du jeton pour `Get-Help` exécuté sur ScriptBlock pour l’aide sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="decc1-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="decc1-187">(#8238) (merci @hubuk !)</span><span class="sxs-lookup"><span data-stu-id="decc1-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="decc1-188">Modification du paramètre -Parameter pour l’applet de commande `Get-Help` afin d’accepter des tableaux de chaînes (#8454) (merci @sethvs !)</span><span class="sxs-lookup"><span data-stu-id="decc1-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="decc1-189">Résolution de PAGER si son chemin d’accès contient des espaces (#8571) (merci @pougetat !)</span><span class="sxs-lookup"><span data-stu-id="decc1-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="decc1-190">Ajout d’une invite pour utiliser `less` dans la fonction 'help' afin d’indiquer à utilisateur comment quitter (#7998)</span><span class="sxs-lookup"><span data-stu-id="decc1-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="decc1-191">Ajout de la prise en charge des types enum et char dans l’applet de commande `Format-Hex` (#8191) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-192">Suppression de ShouldProcess de `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="decc1-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="decc1-193">Ajout des nouveaux paramètres Offset et Count pour `Format-Hex` et refactorisation de l’applet de commande (#7877) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-194">Autoriser 'name' comme clé d’alias pour 'label' dans `ConvertTo-Html`, autoriser l’entrée 'width' à être un entier (#8426) (merci @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="decc1-195">Rendre les propriétés calculées basées sur Scriptblock réutilisables `ConvertTo-Html` (#8427) (merci @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="decc1-196">Ajout de l’applet de commande `Join-String` pour la création de texte à partir de l’entrée du pipeline (#7660) (merci @powercode !)</span><span class="sxs-lookup"><span data-stu-id="decc1-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="decc1-197">Correctif `Join-String` pour la logique du paramètre FormatString de l’applet de commande (#8449) (merci @sethvs !)</span><span class="sxs-lookup"><span data-stu-id="decc1-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="decc1-198">Retour de `Clear-Host` à `$RAWUI` et autorisation d’utiliser la communication à distance (#8609)</span><span class="sxs-lookup"><span data-stu-id="decc1-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="decc1-199">Modification de `Clear-Host` en `[console]::clear` et suppression des alias clairs d’Unix (#8603)</span><span class="sxs-lookup"><span data-stu-id="decc1-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="decc1-200">Correction de LiteralPath dans `Import-Csv` pour la liaison au résultat `Get-ChildItem` (#8277) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-201">la fonction help ne devrait pas utiliser la radiomessagerie pour AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="decc1-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="decc1-202">Ajout de `-UseMinimalHeader` à `Start-Transcript` pour réduire l’en-tête de transcription (#8402) (merci @lukexjeremy !)</span><span class="sxs-lookup"><span data-stu-id="decc1-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="decc1-203">Ajouter les applets de commande `Enable-ExperimentalFeature` et `Disable-ExperimentalFeature` (#8318)</span><span class="sxs-lookup"><span data-stu-id="decc1-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="decc1-204">Exposition de toutes les applets de commande depuis **PSDiagnostics** si logman.exe est disponible (#8366)</span><span class="sxs-lookup"><span data-stu-id="decc1-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="decc1-205">Suppression du paramètre **Persist** de `New-PSDrive` sur la plateforme `non-Windows` (#8291) (merci @lukexjeremy !)</span><span class="sxs-lookup"><span data-stu-id="decc1-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="decc1-206">Ajout de la prise en charge de `cd +` (#7206) (merci @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="decc1-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="decc1-207">Autoriser `Set-Location -LiteralPath` à utiliser des dossiers nommés - et + (#8089)</span><span class="sxs-lookup"><span data-stu-id="decc1-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="decc1-208">`Test-Path` renvoie `$false` avec une valeur de chemin d’accès vide ou `$null` (#8080) (merci @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="decc1-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="decc1-209">Autoriser le renvoi d’un paramètre dynamique même si le chemin d’accès ne correspond à aucun fournisseur (#7957)</span><span class="sxs-lookup"><span data-stu-id="decc1-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="decc1-210">Prise en charge de `Get-PSHostProcessInfo` et `Enter-PSHostProcess` sur les plateformes Unix (#8232)</span><span class="sxs-lookup"><span data-stu-id="decc1-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="decc1-211">Réduction des allocations dans l’applet de commande `Get-Content` (#8103) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-212">Autoriser `Add-Content` à partager l’accès en lecture avec d’autres outils pendant l’écriture de contenu (#8091)</span><span class="sxs-lookup"><span data-stu-id="decc1-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="decc1-213">`Get/Add-Content` génère une erreur améliorée lors du ciblage d’un conteneur (#7823) (merci @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="decc1-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="decc1-214">Ajout des paramètres `-Name`, `-NoUserOverrides` et `-ListAvailable` à l’applet de commande `Get-Culture` (#7702) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-215">Ajout d’un attribut unifié pour finaliser le paramètre **Encoding**.</span><span class="sxs-lookup"><span data-stu-id="decc1-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="decc1-216">(#7732) (merci @ThreeFive-O !)</span><span class="sxs-lookup"><span data-stu-id="decc1-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="decc1-217">Autoriser des ID numériques et un nom de pages de codes enregistrées dans les paramètres **Encoding** (#7636) (merci @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="decc1-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="decc1-218">Correctif `Rename-Item -Path` avec caractère générique char (#7398) (merci @kwkam !)</span><span class="sxs-lookup"><span data-stu-id="decc1-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="decc1-219">Si vous utilisez `Start-Transcript` et que le fichier existe, utiliser un fichier vide plutôt que de le supprimer (#8131) (merci @paalbra !)</span><span class="sxs-lookup"><span data-stu-id="decc1-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="decc1-220">Créer des fichiers open source `Add-Type` avec **FileAccess.Read** et **FileShare.Read** explicitement (#7915) (merci @IISResetMe !)</span><span class="sxs-lookup"><span data-stu-id="decc1-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="decc1-221">Correctif `Enter-PSSession -ContainerId` pour la dernière version Windows (#7883)</span><span class="sxs-lookup"><span data-stu-id="decc1-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="decc1-222">Vérification que la propriété **NestedModules** est remplie par `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="decc1-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="decc1-223">Ajout d’un cas `%F` à `Get-Date` - UFormat (#7630) (merci @britishben !)</span><span class="sxs-lookup"><span data-stu-id="decc1-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="decc1-224">Correctif `Set-Service -Status Stopped` pour arrêter les services avec des dépendances (#5525) (merci @zhenggu !)</span><span class="sxs-lookup"><span data-stu-id="decc1-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Fonctionnalités expérimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
