---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Résolutions de bogues dans WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809305"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="2e367-103">Résolutions de bogues dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2e367-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="2e367-104">Résolution des bogues</span><span class="sxs-lookup"><span data-stu-id="2e367-104">Bug fixes</span></span>

<span data-ttu-id="2e367-105">Les bogues importants suivants sont résolus dans WMF 5.1 :</span><span class="sxs-lookup"><span data-stu-id="2e367-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="2e367-106">La détection automatique de module respecte entièrement PSModulePath</span><span class="sxs-lookup"><span data-stu-id="2e367-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="2e367-107">La détection automatique de module (chargement automatique des modules sans Import-Module explicite lors de l’appel d’une commande) a été introduite dans WMF 3.</span><span class="sxs-lookup"><span data-stu-id="2e367-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="2e367-108">Lors de l’introduction, PowerShell vérifiait la présence des commandes dans `$PSHome\Modules` avant d’utiliser `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="2e367-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="2e367-109">WMF 5.1 modifie ce comportement pour honorer `$env:PSModulePath` complètement.</span><span class="sxs-lookup"><span data-stu-id="2e367-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="2e367-110">Ainsi, un module créé par l’utilisateur qui définit des commandes fournies par PowerShell (par exemple, `Get-ChildItem`) peut être chargé automatiquement et remplacer correctement la commande intégrée.</span><span class="sxs-lookup"><span data-stu-id="2e367-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="2e367-111">La redirection de fichiers ne code plus en dur -Encoding Unicode</span><span class="sxs-lookup"><span data-stu-id="2e367-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="2e367-112">Dans toutes les versions précédentes de PowerShell, il était impossible de contrôler l’encodage de fichier utilisé par l’opérateur de redirection de fichier.</span><span class="sxs-lookup"><span data-stu-id="2e367-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="2e367-113">À compter de WMF 5.1, vous pouvez modifier l’encodage de fichier de la redirection en définissant `$PSDefaultParameterValues` :</span><span class="sxs-lookup"><span data-stu-id="2e367-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="2e367-114">Correction d’une régression dans l’accès aux membres de System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="2e367-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="2e367-115">Une régression introduite dans WMF 5.0 interdisait l’accès aux membres de `System.Reflection.RuntimeType`, par exemple `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="2e367-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="2e367-116">Ce bogue a été résolu dans WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="2e367-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="2e367-117">Résolution de certains problèmes liés aux objets COM</span><span class="sxs-lookup"><span data-stu-id="2e367-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="2e367-118">WMF 5.0 a introduit un nouveau binder COM pour appeler des méthodes sur des objets COM et accéder aux propriétés des objets COM.</span><span class="sxs-lookup"><span data-stu-id="2e367-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="2e367-119">Ce nouveau binder a amélioré les performances de manière significative, mais il a également introduit des bogues qui ont été résolus dans WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="2e367-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="2e367-120">Les conversions d’arguments n’étaient pas toujours effectuées correctement</span><span class="sxs-lookup"><span data-stu-id="2e367-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="2e367-121">Dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e367-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="2e367-122">La méthode **SendKeys** attend une chaîne, mais PowerShell n’a pas converti le caractère en chaîne, ce qui diffère la conversion en **IDispatch::Invoke**, qui utilise **VariantChangeType**.</span><span class="sxs-lookup"><span data-stu-id="2e367-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="2e367-123">Dans cet exemple, les clés « 1 », « 7 » et « 3 » ont donc été envoyées au lieu de la clé **Volume.Mute** attendue.</span><span class="sxs-lookup"><span data-stu-id="2e367-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="2e367-124">Les objets COM énumérables ne sont pas toujours gérés correctement</span><span class="sxs-lookup"><span data-stu-id="2e367-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="2e367-125">PowerShell énumère normalement la plupart des objets énumérables, mais une régression introduite dans WMF 5.0 empêchait l’énumération des objets COM qui implémentent IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="2e367-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="2e367-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2e367-126">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="2e367-127">Dans l’exemple ci-dessus, WMF 5.0 écrivait le **Scripting.Dictionary** dans le pipeline au lieu d’énumérer les paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="2e367-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="2e367-128">[ordered] n’était pas autorisé à l’intérieur des classes</span><span class="sxs-lookup"><span data-stu-id="2e367-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="2e367-129">WMF 5.0 a introduit des classes avec la validation des littéraux de type utilisée dans les classes.</span><span class="sxs-lookup"><span data-stu-id="2e367-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="2e367-130">`[ordered]` ressemble à un littéral de type, mais n’est pas un vrai type .NET.</span><span class="sxs-lookup"><span data-stu-id="2e367-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="2e367-131">WMF 5.0 signalait de façon erronée une erreur sur `[ordered]` à l’intérieur d’une classe :</span><span class="sxs-lookup"><span data-stu-id="2e367-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="2e367-132">L’aide sur les rubriques de procédures avec plusieurs versions ne fonctionne pas</span><span class="sxs-lookup"><span data-stu-id="2e367-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="2e367-133">Avant WMF 5.1, si plusieurs versions d’un module étaient installées et que toutes partageaient une rubrique d’aide, par exemple about_PSReadline, `help about_PSReadline` retournait plusieurs rubriques sans aucun moyen évident d’afficher l’aide réelle.</span><span class="sxs-lookup"><span data-stu-id="2e367-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="2e367-134">WMF 5.1 résout ce problème en retournant l’aide de la version la plus récente de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="2e367-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="2e367-135">`Get-Help` n’offre aucun moyen de spécifier la version pour laquelle vous souhaitez obtenir de l’aide.</span><span class="sxs-lookup"><span data-stu-id="2e367-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="2e367-136">Pour contourner ce problème, accédez au répertoire de modules et affichez l’aide directement avec un outil tel que votre éditeur favori.</span><span class="sxs-lookup"><span data-stu-id="2e367-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="2e367-137">Impossible de lire powershell.exe à partir de STDIN</span><span class="sxs-lookup"><span data-stu-id="2e367-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="2e367-138">Les clients utilisent `powershell -command -` à partir d’applications natives pour passer des commandes PowerShell dans le script par le biais de STDIN. Malheureusement, d’autres modifications apportées à l’hôte de la console avaient cassé cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="2e367-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="2e367-139">Ce problème est résolu pour la version 5.1 dans la Mise à jour anniversaire Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2e367-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="2e367-140">powershell.exe crée un pic d’utilisation du processeur au démarrage</span><span class="sxs-lookup"><span data-stu-id="2e367-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="2e367-141">PowerShell utilise une requête WMI pour vérifier s’il a été démarré par le biais d’une stratégie de groupe afin de ne pas causer de retard au niveau de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2e367-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="2e367-142">La requête WMI finit par injecter tzres.mui.dll dans chaque processus du système, car la classe WMI **Win32_Process** tente de récupérer des informations sur le fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="2e367-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="2e367-143">Il en résulte un pic d’utilisation du processeur dans **wmiprvse** (hôte du fournisseur WMI).</span><span class="sxs-lookup"><span data-stu-id="2e367-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="2e367-144">Pour y remédier tout en obtenant les mêmes informations, utilisez des appels d’API Win32 à la place de WMI.</span><span class="sxs-lookup"><span data-stu-id="2e367-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
