---
description: La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des fonctionnalités expérimentales
ms.openlocfilehash: e53af155c2a8691e2e4d4cc6f47bfd5932801db9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208218"
---
# <a name="experimental-features"></a>Fonctionnalités expérimentales

La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.

Une fonctionnalité expérimentale est une fonctionnalité dans laquelle la conception n’est pas finalisée. Les utilisateurs peuvent tester la fonctionnalité et fournir des commentaires. Lorsqu’une fonctionnalité expérimentale est finalisée, les modifications apportées à la conception deviennent des changements cassants. Les fonctionnalités expérimentales ne sont pas destinées à être utilisées en production, car les changements peuvent être cassants.

Les fonctionnalités expérimentales sont désactivées par défaut et doivent être activées explicitement par l’utilisateur ou l’administrateur du système.

Les fonctionnalités expérimentales activées sont répertoriées dans le `powershell.config.json` fichier de `$PSHOME` pour tous les utilisateurs ou dans le fichier de configuration spécifique à l’utilisateur pour un utilisateur spécifique.

> [!NOTE]
> Les fonctionnalités expérimentales activées dans le fichier de configuration utilisateur sont prioritaires sur les fonctionnalités expérimentales figurant dans le fichier de configuration système.

## <a name="the-experimental-attribute"></a>Attribut expérimental

Utilisez l' `Experimental` attribut pour déclarer du code comme expérimental.

Utilisez la syntaxe suivante pour déclarer l' `Experimental` attribut qui fournit le nom de la fonctionnalité expérimentale et l’action à exécuter si la fonctionnalité expérimentale est activée :

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

Pour les modules, `NameOfExperimentalFeature` doit respecter la forme `<modulename>.<experimentname>` . Le `ExperimentAction` paramètre doit être spécifié et les seules valeurs valides sont :

- `Show` signifie que cette fonctionnalité expérimentale est affichée si la fonctionnalité est activée.
- `Hide` signifie masquer cette fonctionnalité expérimentale si la fonctionnalité est activée.

### <a name="declaring-experimental-features-in-modules-written-in-c"></a>Déclaration de fonctionnalités expérimentales dans les modules écrits en C\#

Les auteurs de modules qui veulent utiliser les indicateurs de fonctionnalité expérimentale peuvent déclarer une applet de commande comme expérimentale à l’aide de l' `Experimental` attribut.

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a>Déclaration de fonctionnalités expérimentales dans les modules écrits dans PowerShell

Le module écrit dans PowerShell peut également utiliser l' `Experimental` attribut pour déclarer des applets de commande expérimentales :

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a>Fonctionnalités expérimentales mutuellement exclusives

Dans certains cas, une fonctionnalité expérimentale ne peut pas coexister côte à côte avec une fonctionnalité existante ou une autre fonctionnalité expérimentale.

Par exemple, vous pouvez avoir une applet de commande expérimentale qui remplace une applet de commande existante. Les deux versions ne peuvent pas coexister côte à côte. Le `ExperimentAction.Hide` paramètre autorise l’activation d’une seule des deux applets de commande à la fois.

Dans cet exemple, nous créons une applet de commande expérimentale `Invoke-WebRequest` .
`InvokeWebRequestCommand` contient l’implémentation non expérimentale.
`InvokeWebRequestCommandV2` contient la version expérimentale de l’applet de commande.

L’utilisation de permet l' `ExperimentAction.Hide` activation d’une seule des deux fonctionnalités à la fois :

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

Lorsque la `MyWebCmdlets.PSWebCmdletV2` fonctionnalité expérimentale est activée, l' `InvokeWebRequestCommand` implémentation existante est masquée et le `InvokeWebRequestCommandV2` fournit l’implémentation de `Invoke-WebRequest` .

Cela permet aux utilisateurs d’essayer la nouvelle cmdlet et de fournir des commentaires, puis de revenir à la version non expérimentale si nécessaire.

### <a name="experimental-parameters-in-cmdlets"></a>Paramètres expérimentaux dans les applets de commande

L' `Experimental` attribut peut également être appliqué à des paramètres individuels. Cela vous permet de créer un ensemble expérimental de paramètres pour une applet de commande existante plutôt qu’une applet de commande entièrement nouvelle.

Voici un exemple en C# :

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

Voici un exemple différent dans le script PowerShell :

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a>Vérification de l’activation d’une fonctionnalité expérimentale

Dans votre code, vous devrez vérifier si votre fonctionnalité expérimentale est activée avant de prendre les mesures appropriées. Vous pouvez déterminer si une fonctionnalité expérimentale est activée à l’aide de la `IsEnabled()` méthode statique sur la `System.Management.Automation.ExperimentalFeature` classe.

Voici un exemple en C# :

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

Voici un exemple de script PowerShell :

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a>Voir aussi

[Enable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[Disable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[Get-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)
