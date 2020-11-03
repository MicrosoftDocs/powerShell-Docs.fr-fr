---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93206034"
---
# <span data-ttu-id="87035-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="87035-103">Get-Verb</span></span>

## <span data-ttu-id="87035-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="87035-104">SYNOPSIS</span></span>
<span data-ttu-id="87035-105">Obtient les verbes PowerShell approuvés.</span><span class="sxs-lookup"><span data-stu-id="87035-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="87035-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="87035-106">SYNTAX</span></span>

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="87035-107">Description</span><span class="sxs-lookup"><span data-stu-id="87035-107">DESCRIPTION</span></span>

<span data-ttu-id="87035-108">La `Get-Verb` fonction obtient les verbes dont l’utilisation est approuvée dans les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87035-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="87035-109">PowerShell recommande l’applet de commande et les noms de fonctions ont le format Verb-Noun et incluent un verbe approuvé.</span><span class="sxs-lookup"><span data-stu-id="87035-109">PowerShell recommends cmdlet and function names have the Verb-Noun format and include an approved verb.</span></span> <span data-ttu-id="87035-110">Cette pratique rend les noms des commandes plus cohérents, prévisibles et plus faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="87035-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="87035-111">Les commandes qui utilisent des verbes non approuvés s’exécutent dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87035-111">Commands that use unapproved verbs run in PowerShell.</span></span> <span data-ttu-id="87035-112">Toutefois, lorsque vous importez un module qui comprend une commande dont le nom contient un verbe non approuvé, la `Import-Module` commande affiche un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="87035-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="87035-113">La liste de verbes `Get-Verb` retournée peut ne pas être terminée.</span><span class="sxs-lookup"><span data-stu-id="87035-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="87035-114">Pour obtenir une liste actualisée des verbes PowerShell approuvés avec des descriptions, consultez [verbes approuvés](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) dans le Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="87035-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="87035-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="87035-115">EXAMPLES</span></span>

### <span data-ttu-id="87035-116">Exemple 1 : obtenir une liste de tous les verbes</span><span class="sxs-lookup"><span data-stu-id="87035-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="87035-117">Exemple 2 : obtenir la liste des verbes approuvés qui commencent par « un »</span><span class="sxs-lookup"><span data-stu-id="87035-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### <span data-ttu-id="87035-118">Exemple 3 : récupération de tous les verbes approuvés dans le groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="87035-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### <span data-ttu-id="87035-119">Exemple 4 : recherche toutes les commandes dans un module qui ont des verbes non approuvés</span><span class="sxs-lookup"><span data-stu-id="87035-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="87035-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87035-120">PARAMETERS</span></span>

### <span data-ttu-id="87035-121">-verbe</span><span class="sxs-lookup"><span data-stu-id="87035-121">-verb</span></span>

<span data-ttu-id="87035-122">Obtient uniquement les verbes spécifiés.</span><span class="sxs-lookup"><span data-stu-id="87035-122">Gets only the specified verbs.</span></span>
<span data-ttu-id="87035-123">Entrez le nom d'un verbe ou d'un modèle de nom.</span><span class="sxs-lookup"><span data-stu-id="87035-123">Enter the name of a verb or a name pattern.</span></span>
<span data-ttu-id="87035-124">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="87035-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## <span data-ttu-id="87035-125">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="87035-125">INPUTS</span></span>

### <span data-ttu-id="87035-126">Aucun</span><span class="sxs-lookup"><span data-stu-id="87035-126">None</span></span>

## <span data-ttu-id="87035-127">SORTIES</span><span class="sxs-lookup"><span data-stu-id="87035-127">OUTPUTS</span></span>

### <span data-ttu-id="87035-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="87035-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span></span>

## <span data-ttu-id="87035-129">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="87035-129">NOTES</span></span>

<span data-ttu-id="87035-130">`Get-Verb` retourne une version modifiée d’un objet Microsoft. PowerShell. Commands. MemberDefinition.</span><span class="sxs-lookup"><span data-stu-id="87035-130">`Get-Verb` returns a modified version of a Microsoft.PowerShell.Commands.MemberDefinition object.</span></span>
<span data-ttu-id="87035-131">L'objet ne possède pas les propriétés standard d'un objet MemberDefinition.</span><span class="sxs-lookup"><span data-stu-id="87035-131">The object does not have the standard properties of a MemberDefinition object.</span></span> <span data-ttu-id="87035-132">Au lieu de cela, il possède des propriétés Verb et Group.</span><span class="sxs-lookup"><span data-stu-id="87035-132">Instead it has Verb and Group properties.</span></span> <span data-ttu-id="87035-133">La propriété Verb contient une chaîne avec le nom du verbe.</span><span class="sxs-lookup"><span data-stu-id="87035-133">The Verb property contains a string with the verb name.</span></span> <span data-ttu-id="87035-134">La propriété Group contient une chaîne avec le groupe du verbe.</span><span class="sxs-lookup"><span data-stu-id="87035-134">The Group property contains a string with the verb group.</span></span>

<span data-ttu-id="87035-135">Les verbes PowerShell sont affectés à un groupe en fonction de leur utilisation la plus courante.</span><span class="sxs-lookup"><span data-stu-id="87035-135">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="87035-136">Les groupes sont conçus pour faciliter la recherche et la comparaison des verbes, sans limiter leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="87035-136">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="87035-137">Vous pouvez utiliser n'importe quel verbe approuvé pour n'importe quel type de commande.</span><span class="sxs-lookup"><span data-stu-id="87035-137">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="87035-138">Chaque verbe PowerShell est affecté à l’un des groupes suivants.</span><span class="sxs-lookup"><span data-stu-id="87035-138">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="87035-139">Commun : définissez des actions génériques qui peuvent s’appliquer à presque n’importe quelle applet de commande, telle que Add.</span><span class="sxs-lookup"><span data-stu-id="87035-139">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="87035-140">Communications : définissez les actions qui s’appliquent aux communications, telles que Connect.</span><span class="sxs-lookup"><span data-stu-id="87035-140">Communications:  Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="87035-141">Données : définissez les actions qui s’appliquent à la gestion des données, telles que la sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="87035-141">Data:  Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="87035-142">Diagnostic : définissez les actions qui s’appliquent aux diagnostics, telles que le débogage.</span><span class="sxs-lookup"><span data-stu-id="87035-142">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="87035-143">Cycle de vie : définissez les actions qui s’appliquent au cycle de vie d’une applet de commande, comme complet.</span><span class="sxs-lookup"><span data-stu-id="87035-143">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="87035-144">Sécurité : définissez les actions qui s’appliquent à la sécurité, telles que REVOKE.</span><span class="sxs-lookup"><span data-stu-id="87035-144">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="87035-145">Autre : définissez d’autres types d’actions.</span><span class="sxs-lookup"><span data-stu-id="87035-145">Other: Define other types of actions.</span></span>

<span data-ttu-id="87035-146">Certaines des applets de commande installées avec PowerShell, telles que `Tee-Object` et `Where-Object` , utilisent des verbes non approuvés.</span><span class="sxs-lookup"><span data-stu-id="87035-146">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="87035-147">Ces applets de commande sont des exceptions historiques et leurs verbes sont classés comme **réservés** .</span><span class="sxs-lookup"><span data-stu-id="87035-147">These cmdlets are historic exceptions and their verbs are classified as **reserved** .</span></span>

## <span data-ttu-id="87035-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="87035-148">RELATED LINKS</span></span>

[<span data-ttu-id="87035-149">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="87035-149">Import-Module</span></span>](import-module.md)
