---
description: Décrit l' `InlineScript` activité qui exécute des commandes PowerShell dans un flux de travail.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_inlinescript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_InlineScript
ms.openlocfilehash: 2eaeb02c6441865551b586e27a39c4000826752b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207238"
---
# <a name="about-inlinescript"></a>À propos de InlineScript

## <a name="short-description"></a>Description courte

Décrit l' `InlineScript` activité qui exécute des commandes PowerShell dans un flux de travail.

## <a name="long-description"></a>Description longue

L' `InlineScript` activité exécute les commandes dans le flux de travail d’une session PowerShell partagée. `InlineScript` est valide uniquement dans les workflows.

## <a name="syntax"></a>Syntaxe

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a>Description détaillée

L' `InlineScript` activité exécute les commandes dans une session PowerShell partagée. Vous pouvez l’inclure dans un flux de travail pour exécuter des commandes qui partagent des données et des commandes qui ne sont autrement pas valides dans un Workflow.

Le `InlineScript` bloc de script peut inclure toutes les commandes et expressions PowerShell valides. Étant donné que les commandes et les expressions d’un `InlineScript` bloc de script s’exécutent dans la même session, elles partagent l’ensemble de l’État et des données, y compris les modules importés et les valeurs des variables.

Vous pouvez placer une `InlineScript` activité n’importe où dans un workflow ou dans un workflow imbriqué, y compris dans une instruction de boucle ou de contrôle, ou dans un bloc de script parallèle ou de séquence.

L' `InlineScript` activité possède les paramètres communs d’activité, y compris **PSPersist** . Toutefois, les commandes et les expressions d’un `InlineScript` bloc de script n’ont pas les fonctionnalités de flux de travail telles que les points de contrôle ou la persistance, ainsi que les paramètres communs de workflow ou d’activité. Pour plus d’informations, consultez [about_ActivityCommonParameters](about_ActivityCommonParameters.md).

## <a name="inlinescript-variables"></a>InlineScript, variables

Par défaut, les variables définies dans un workflow ne sont pas visibles pour les commandes du `InlineScript` bloc de script. Pour rendre les variables de workflow visibles pour `InlineScript` , utilisez le `$Using` modificateur de portée. Le `$Using` modificateur de portée n’est requis qu’une seule fois pour chaque variable dans `InlineScript` .

Pour plus d’informations sur le `$Using` modificateur d’étendue, consultez [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).

L’exemple suivant montre que le `$Using` modificateur de portée rend la valeur de la `$a` variable de workflow de niveau supérieur disponible pour les commandes dans le `InlineScript` bloc de script.

```powershell
workflow Test-Workflow {
  $a = 3

  ## Without $Using, the $a workflow variable isn't visible
  ## in inline script.
  InlineScript {"Inline A0 = $a"}

  ## $Using imports the variable and its current value.
  InlineScript {"Inline A1 = $Using:a"}
}

Test-Workflow
```

```output
Inline A0 =
Inline A1 = 3
```

## <a name="returning-variables-in-inlinescript"></a>Retour de variables dans InlineScript

`InlineScript` les commandes peuvent modifier la valeur de la variable qui a été importée à partir de la portée du workflow, mais les modifications ne sont pas visibles dans la portée du Workflow. Pour les rendre visibles, renvoyez la valeur modifiée dans la portée du workflow, comme illustré dans l'exemple ci-dessous.

```powershell
workflow Test-Workflow {
  $a = 3

  ##  Changes to the InlineScript variable value don't
  ##  change the workflow variable.
  InlineScript {
    $a = $Using:a+1;
    "Inline A = $a"
  }
  "Workflow A = $a"

  ##  To change the variable in workflow scope, return the
  ##  new value.
  $a = InlineScript {$b = $Using:a+1; $b}
  "Workflow New A = $a"
}

Test-Workflow
```

```output
Inline A = 4
Workflow A = 3
Workflow New A = 4
```

> [!NOTE]
> Une instruction avec le `$Using` modificateur de portée doit apparaître avant toute utilisation de la variable dans le `InlineScript` bloc de script.

## <a name="running-in-process"></a>Exécution in-process

Pour améliorer la fiabilité, les commandes dans le `InlineScript` bloc de script s’exécutent dans leur propre processus, séparément du processus dans lequel le workflow s’exécute, puis renvoient leur sortie au processus de Workflow.

Pour diriger PowerShell afin d’exécuter l' `InlineScript` activité dans le processus de workflow, supprimez la `InlineScript` valeur de la propriété **OutOfProcessActivity** de la configuration de session, par exemple à l’aide de l’applet de commande `New-PSWorkflowExecutionOption` .

### <a name="example"></a>Exemple

Le `InlineScript` dans le workflow suivant comprend des commandes qui sont valides dans PowerShell, mais qui ne sont pas valides dans les workflows. Par exemple, l' `New-Object` applet de commande avec le paramètre **ComObject** .

```powershell
workflow Test-Workflow
{
  $ie = InlineScript {
    $ie = New-Object -ComObject InternetExplorer.Application -Property @{navigate2="www.microsoft.com"}

    $ie.Visible = $true
  }

  $ie
}

Test-Workflow
```

## <a name="see-also"></a>Voir aussi

[about_ActivityCommonParameters](about_ActivityCommonParameters.md)

[about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

Applets de commande [PSWorkflow](xref:PSWorkflow)

[Guide des workflows](/previous-versions/powershell/scripting/components/workflows-guide)

[Écriture d'un workflow Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
