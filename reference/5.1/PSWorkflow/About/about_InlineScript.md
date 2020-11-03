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
# <a name="about-inlinescript"></a><span data-ttu-id="e1d70-104">À propos de InlineScript</span><span class="sxs-lookup"><span data-stu-id="e1d70-104">About InlineScript</span></span>

## <a name="short-description"></a><span data-ttu-id="e1d70-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="e1d70-105">Short description</span></span>

<span data-ttu-id="e1d70-106">Décrit l' `InlineScript` activité qui exécute des commandes PowerShell dans un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e1d70-106">Describes the `InlineScript` activity, that runs PowerShell commands in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="e1d70-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="e1d70-107">Long description</span></span>

<span data-ttu-id="e1d70-108">L' `InlineScript` activité exécute les commandes dans le flux de travail d’une session PowerShell partagée.</span><span class="sxs-lookup"><span data-stu-id="e1d70-108">The `InlineScript` activity runs commands in a shared PowerShell session's workflow.</span></span> <span data-ttu-id="e1d70-109">`InlineScript` est valide uniquement dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="e1d70-109">`InlineScript` is only valid in workflows.</span></span>

## <a name="syntax"></a><span data-ttu-id="e1d70-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1d70-110">Syntax</span></span>

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a><span data-ttu-id="e1d70-111">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="e1d70-111">Detailed description</span></span>

<span data-ttu-id="e1d70-112">L' `InlineScript` activité exécute les commandes dans une session PowerShell partagée.</span><span class="sxs-lookup"><span data-stu-id="e1d70-112">The `InlineScript` activity runs commands in a shared PowerShell session.</span></span> <span data-ttu-id="e1d70-113">Vous pouvez l’inclure dans un flux de travail pour exécuter des commandes qui partagent des données et des commandes qui ne sont autrement pas valides dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="e1d70-113">You can include it in a workflow to run commands that share data and commands that aren't otherwise valid in a workflow.</span></span>

<span data-ttu-id="e1d70-114">Le `InlineScript` bloc de script peut inclure toutes les commandes et expressions PowerShell valides.</span><span class="sxs-lookup"><span data-stu-id="e1d70-114">The `InlineScript` script block can include all valid PowerShell commands and expressions.</span></span> <span data-ttu-id="e1d70-115">Étant donné que les commandes et les expressions d’un `InlineScript` bloc de script s’exécutent dans la même session, elles partagent l’ensemble de l’État et des données, y compris les modules importés et les valeurs des variables.</span><span class="sxs-lookup"><span data-stu-id="e1d70-115">Because the commands and expressions in an `InlineScript` script block run in the same session, they share all state and data, including imported modules and the values of variables.</span></span>

<span data-ttu-id="e1d70-116">Vous pouvez placer une `InlineScript` activité n’importe où dans un workflow ou dans un workflow imbriqué, y compris dans une instruction de boucle ou de contrôle, ou dans un bloc de script parallèle ou de séquence.</span><span class="sxs-lookup"><span data-stu-id="e1d70-116">You can place an `InlineScript` activity anywhere in a workflow or nested workflow, including inside a loop or control statement or a Parallel or Sequence script block.</span></span>

<span data-ttu-id="e1d70-117">L' `InlineScript` activité possède les paramètres communs d’activité, y compris **PSPersist** .</span><span class="sxs-lookup"><span data-stu-id="e1d70-117">The `InlineScript` activity has the activity common parameters, including **PSPersist** .</span></span> <span data-ttu-id="e1d70-118">Toutefois, les commandes et les expressions d’un `InlineScript` bloc de script n’ont pas les fonctionnalités de flux de travail telles que les points de contrôle ou la persistance, ainsi que les paramètres communs de workflow ou d’activité.</span><span class="sxs-lookup"><span data-stu-id="e1d70-118">However, the commands and expressions in an `InlineScript` script block don't have the workflow features such as checkpointing, or persistence, and workflow or activity common parameters.</span></span> <span data-ttu-id="e1d70-119">Pour plus d’informations, consultez [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="e1d70-119">For more information, see [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span></span>

## <a name="inlinescript-variables"></a><span data-ttu-id="e1d70-120">InlineScript, variables</span><span class="sxs-lookup"><span data-stu-id="e1d70-120">InlineScript Variables</span></span>

<span data-ttu-id="e1d70-121">Par défaut, les variables définies dans un workflow ne sont pas visibles pour les commandes du `InlineScript` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="e1d70-121">By default, the variables that are defined in a workflow aren't visible to the commands in the `InlineScript` script block.</span></span> <span data-ttu-id="e1d70-122">Pour rendre les variables de workflow visibles pour `InlineScript` , utilisez le `$Using` modificateur de portée.</span><span class="sxs-lookup"><span data-stu-id="e1d70-122">To make workflow variables visible to the `InlineScript`, use the `$Using` scope modifier.</span></span> <span data-ttu-id="e1d70-123">Le `$Using` modificateur de portée n’est requis qu’une seule fois pour chaque variable dans `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="e1d70-123">The `$Using` scope modifier is required only once for each variable in the `InlineScript`.</span></span>

<span data-ttu-id="e1d70-124">Pour plus d’informations sur le `$Using` modificateur d’étendue, consultez [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e1d70-124">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

<span data-ttu-id="e1d70-125">L’exemple suivant montre que le `$Using` modificateur de portée rend la valeur de la `$a` variable de workflow de niveau supérieur disponible pour les commandes dans le `InlineScript` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="e1d70-125">The following example shows that the `$Using` scope modifier makes the value of the `$a` top-level workflow variable available to the commands in the `InlineScript` script block.</span></span>

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

## <a name="returning-variables-in-inlinescript"></a><span data-ttu-id="e1d70-126">Retour de variables dans InlineScript</span><span class="sxs-lookup"><span data-stu-id="e1d70-126">Returning variables in InlineScript</span></span>

<span data-ttu-id="e1d70-127">`InlineScript` les commandes peuvent modifier la valeur de la variable qui a été importée à partir de la portée du workflow, mais les modifications ne sont pas visibles dans la portée du Workflow.</span><span class="sxs-lookup"><span data-stu-id="e1d70-127">`InlineScript` commands can change the value of the variable that was imported from workflow scope, but the changes aren't visible in workflow scope.</span></span> <span data-ttu-id="e1d70-128">Pour les rendre visibles, renvoyez la valeur modifiée dans la portée du workflow, comme illustré dans l'exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e1d70-128">To make them visible, return the changed value to the workflow scope, as shown in the following example.</span></span>

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
> <span data-ttu-id="e1d70-129">Une instruction avec le `$Using` modificateur de portée doit apparaître avant toute utilisation de la variable dans le `InlineScript` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="e1d70-129">A statement with the `$Using` scope modifier should appear before any use of the variable in the `InlineScript` script block.</span></span>

## <a name="running-in-process"></a><span data-ttu-id="e1d70-130">Exécution in-process</span><span class="sxs-lookup"><span data-stu-id="e1d70-130">Running in-process</span></span>

<span data-ttu-id="e1d70-131">Pour améliorer la fiabilité, les commandes dans le `InlineScript` bloc de script s’exécutent dans leur propre processus, séparément du processus dans lequel le workflow s’exécute, puis renvoient leur sortie au processus de Workflow.</span><span class="sxs-lookup"><span data-stu-id="e1d70-131">To improve reliability, the commands in the `InlineScript` script block run in their own process, separate from the process in which the workflow runs, and then return their output to the workflow process.</span></span>

<span data-ttu-id="e1d70-132">Pour diriger PowerShell afin d’exécuter l' `InlineScript` activité dans le processus de workflow, supprimez la `InlineScript` valeur de la propriété **OutOfProcessActivity** de la configuration de session, par exemple à l’aide de l’applet de commande `New-PSWorkflowExecutionOption` .</span><span class="sxs-lookup"><span data-stu-id="e1d70-132">To direct PowerShell to run the `InlineScript` activity in the workflow process, remove the `InlineScript` value from the **OutOfProcessActivity** property of the session configuration, such as by using the `New-PSWorkflowExecutionOption` cmdlet.</span></span>

### <a name="example"></a><span data-ttu-id="e1d70-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1d70-133">Example</span></span>

<span data-ttu-id="e1d70-134">Le `InlineScript` dans le workflow suivant comprend des commandes qui sont valides dans PowerShell, mais qui ne sont pas valides dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="e1d70-134">The `InlineScript` in the following workflow includes commands that are valid in PowerShell but aren't valid in workflows.</span></span> <span data-ttu-id="e1d70-135">Par exemple, l' `New-Object` applet de commande avec le paramètre **ComObject** .</span><span class="sxs-lookup"><span data-stu-id="e1d70-135">For example, the `New-Object` cmdlet with the **ComObject** parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e1d70-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1d70-136">See also</span></span>

[<span data-ttu-id="e1d70-137">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1d70-137">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)

[<span data-ttu-id="e1d70-138">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="e1d70-138">about_Remote_Variables</span></span>](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[<span data-ttu-id="e1d70-139">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1d70-139">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="e1d70-140">Applets de commande [PSWorkflow](xref:PSWorkflow)</span><span class="sxs-lookup"><span data-stu-id="e1d70-140">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="e1d70-141">Guide des workflows</span><span class="sxs-lookup"><span data-stu-id="e1d70-141">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="e1d70-142">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1d70-142">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
