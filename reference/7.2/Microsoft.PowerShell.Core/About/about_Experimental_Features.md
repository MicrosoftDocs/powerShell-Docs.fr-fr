---
description: La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des fonctionnalités expérimentales
ms.openlocfilehash: 82f5ef9838fcbb98e71e362ad00b1ec68f9a9f67
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597563"
---
# <a name="experimental-features"></a><span data-ttu-id="a5ad2-103">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="a5ad2-103">Experimental Features</span></span>

<span data-ttu-id="a5ad2-104">La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="a5ad2-105">Une fonctionnalité expérimentale est une fonctionnalité dans laquelle la conception n’est pas finalisée.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="a5ad2-106">Les utilisateurs peuvent tester la fonctionnalité et fournir des commentaires.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="a5ad2-107">Lorsqu’une fonctionnalité expérimentale est finalisée, les modifications apportées à la conception deviennent des changements cassants.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="a5ad2-108">Les fonctionnalités expérimentales ne sont pas destinées à être utilisées en production, car les changements peuvent être cassants.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="a5ad2-109">Les fonctionnalités expérimentales sont désactivées par défaut et doivent être activées explicitement par l’utilisateur ou l’administrateur du système.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-109">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="a5ad2-110">Les fonctionnalités expérimentales activées sont répertoriées dans le `powershell.config.json` fichier de `$PSHOME` pour tous les utilisateurs ou dans le fichier de configuration spécifique à l’utilisateur pour un utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-110">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="a5ad2-111">Les fonctionnalités expérimentales activées dans le fichier de configuration utilisateur sont prioritaires sur les fonctionnalités expérimentales figurant dans le fichier de configuration système.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-111">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="a5ad2-112">Attribut expérimental</span><span class="sxs-lookup"><span data-stu-id="a5ad2-112">The Experimental Attribute</span></span>

<span data-ttu-id="a5ad2-113">Utilisez l' `Experimental` attribut pour déclarer du code comme expérimental.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-113">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="a5ad2-114">Utilisez la syntaxe suivante pour déclarer l' `Experimental` attribut qui fournit le nom de la fonctionnalité expérimentale et l’action à exécuter si la fonctionnalité expérimentale est activée :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-114">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="a5ad2-115">Pour les modules, `NameOfExperimentalFeature` doit respecter la forme `<modulename>.<experimentname>` .</span><span class="sxs-lookup"><span data-stu-id="a5ad2-115">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="a5ad2-116">Le `ExperimentAction` paramètre doit être spécifié et les seules valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-116">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="a5ad2-117">`Show` signifie que cette fonctionnalité expérimentale est affichée si la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-117">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="a5ad2-118">`Hide` signifie masquer cette fonctionnalité expérimentale si la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-118">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="a5ad2-119">Déclaration de fonctionnalités expérimentales dans les modules écrits en C\#</span><span class="sxs-lookup"><span data-stu-id="a5ad2-119">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="a5ad2-120">Les auteurs de modules qui veulent utiliser les indicateurs de fonctionnalité expérimentale peuvent déclarer une applet de commande comme expérimentale à l’aide de l' `Experimental` attribut.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-120">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="a5ad2-121">Déclaration de fonctionnalités expérimentales dans les modules écrits dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5ad2-121">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="a5ad2-122">Le module écrit dans PowerShell peut également utiliser l' `Experimental` attribut pour déclarer des applets de commande expérimentales :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-122">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="a5ad2-123">Fonctionnalités expérimentales mutuellement exclusives</span><span class="sxs-lookup"><span data-stu-id="a5ad2-123">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="a5ad2-124">Dans certains cas, une fonctionnalité expérimentale ne peut pas coexister côte à côte avec une fonctionnalité existante ou une autre fonctionnalité expérimentale.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-124">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="a5ad2-125">Par exemple, vous pouvez avoir une applet de commande expérimentale qui remplace une applet de commande existante.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-125">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="a5ad2-126">Les deux versions ne peuvent pas coexister côte à côte.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-126">The two versions can't coexist side by side.</span></span> <span data-ttu-id="a5ad2-127">Le `ExperimentAction.Hide` paramètre autorise l’activation d’une seule des deux applets de commande à la fois.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-127">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="a5ad2-128">Dans cet exemple, nous créons une applet de commande expérimentale `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="a5ad2-128">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="a5ad2-129">`InvokeWebRequestCommand` contient l’implémentation non expérimentale.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-129">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="a5ad2-130">`InvokeWebRequestCommandV2` contient la version expérimentale de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-130">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="a5ad2-131">L’utilisation de permet l' `ExperimentAction.Hide` activation d’une seule des deux fonctionnalités à la fois :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-131">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="a5ad2-132">Lorsque la `MyWebCmdlets.PSWebCmdletV2` fonctionnalité expérimentale est activée, l' `InvokeWebRequestCommand` implémentation existante est masquée et le `InvokeWebRequestCommandV2` fournit l’implémentation de `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="a5ad2-132">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="a5ad2-133">Cela permet aux utilisateurs d’essayer la nouvelle cmdlet et de fournir des commentaires, puis de revenir à la version non expérimentale si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-133">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="a5ad2-134">Paramètres expérimentaux dans les applets de commande</span><span class="sxs-lookup"><span data-stu-id="a5ad2-134">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="a5ad2-135">L' `Experimental` attribut peut également être appliqué à des paramètres individuels.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-135">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="a5ad2-136">Cela vous permet de créer un ensemble expérimental de paramètres pour une applet de commande existante plutôt qu’une applet de commande entièrement nouvelle.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-136">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="a5ad2-137">Voici un exemple en C# :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-137">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="a5ad2-138">Voici un exemple différent dans le script PowerShell :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-138">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="a5ad2-139">Vérification de l’activation d’une fonctionnalité expérimentale</span><span class="sxs-lookup"><span data-stu-id="a5ad2-139">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="a5ad2-140">Dans votre code, vous devrez vérifier si votre fonctionnalité expérimentale est activée avant de prendre les mesures appropriées.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-140">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="a5ad2-141">Vous pouvez déterminer si une fonctionnalité expérimentale est activée à l’aide de la `IsEnabled()` méthode statique sur la `System.Management.Automation.ExperimentalFeature` classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad2-141">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="a5ad2-142">Voici un exemple en C# :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-142">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="a5ad2-143">Voici un exemple de script PowerShell :</span><span class="sxs-lookup"><span data-stu-id="a5ad2-143">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="a5ad2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5ad2-144">See also</span></span>

[<span data-ttu-id="a5ad2-145">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="a5ad2-145">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="a5ad2-146">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="a5ad2-146">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="a5ad2-147">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="a5ad2-147">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

