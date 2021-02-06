---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 6aba1c87a5d711cbfe84f9f6f6d1051acbcd524a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595743"
---
# <span data-ttu-id="8839b-102">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="8839b-102">Get-Verb</span></span>

## <span data-ttu-id="8839b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8839b-103">SYNOPSIS</span></span>
<span data-ttu-id="8839b-104">Obtient les verbes PowerShell approuvés.</span><span class="sxs-lookup"><span data-stu-id="8839b-104">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="8839b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8839b-105">SYNTAX</span></span>

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8839b-106">Description</span><span class="sxs-lookup"><span data-stu-id="8839b-106">DESCRIPTION</span></span>

<span data-ttu-id="8839b-107">La `Get-Verb` fonction obtient les verbes dont l’utilisation est approuvée dans les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8839b-107">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="8839b-108">Il est recommandé que les noms des applets de commande et des fonctions PowerShell aient le `Verb-Noun` format et incluent un verbe approuvé.</span><span class="sxs-lookup"><span data-stu-id="8839b-108">It is recommended that PowerShell cmdlet and function names have the `Verb-Noun` format and include an approved verb.</span></span> <span data-ttu-id="8839b-109">Cette pratique rend les noms des commandes plus cohérents, prévisibles et plus faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8839b-109">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="8839b-110">Les commandes qui utilisent des verbes non approuvés, s’exécutent toujours dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8839b-110">Commands that use unapproved verbs, still run in PowerShell.</span></span> <span data-ttu-id="8839b-111">Toutefois, lorsque vous importez un module qui comprend une commande dont le nom contient un verbe non approuvé, la `Import-Module` commande affiche un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="8839b-111">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="8839b-112">La liste de verbes `Get-Verb` retournée peut ne pas être terminée.</span><span class="sxs-lookup"><span data-stu-id="8839b-112">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="8839b-113">Pour obtenir une liste actualisée des verbes PowerShell approuvés avec des descriptions, consultez [verbes approuvés](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) dans le Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="8839b-113">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="8839b-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="8839b-114">Examples</span></span>

### <span data-ttu-id="8839b-115">Exemple 1 : obtenir une liste de tous les verbes</span><span class="sxs-lookup"><span data-stu-id="8839b-115">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="8839b-116">Exemple 2 : obtenir la liste des verbes approuvés qui commencent par « un »</span><span class="sxs-lookup"><span data-stu-id="8839b-116">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="8839b-117">Exemple 3 : récupération de tous les verbes approuvés dans le groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="8839b-117">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="8839b-118">Exemple 4 : recherche toutes les commandes dans un module qui ont des verbes non approuvés</span><span class="sxs-lookup"><span data-stu-id="8839b-118">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="8839b-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8839b-119">PARAMETERS</span></span>

### <span data-ttu-id="8839b-120">-Verbe</span><span class="sxs-lookup"><span data-stu-id="8839b-120">-Verb</span></span>

<span data-ttu-id="8839b-121">Obtient uniquement les verbes spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8839b-121">Gets only the specified verbs.</span></span> <span data-ttu-id="8839b-122">Entrez le nom d'un verbe ou d'un modèle de nom.</span><span class="sxs-lookup"><span data-stu-id="8839b-122">Enter the name of a verb or a name pattern.</span></span> <span data-ttu-id="8839b-123">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8839b-123">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8839b-124">-Group</span><span class="sxs-lookup"><span data-stu-id="8839b-124">-Group</span></span>

<span data-ttu-id="8839b-125">Obtient uniquement les groupes spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8839b-125">Gets only the specified groups.</span></span> <span data-ttu-id="8839b-126">Entrez le nom d’un groupe.</span><span class="sxs-lookup"><span data-stu-id="8839b-126">Enter the name of a group.</span></span> <span data-ttu-id="8839b-127">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="8839b-127">Wildcards are not allowed.</span></span>

<span data-ttu-id="8839b-128">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="8839b-128">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8839b-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8839b-129">CommonParameters</span></span>

<span data-ttu-id="8839b-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8839b-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8839b-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8839b-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8839b-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8839b-132">INPUTS</span></span>

### <span data-ttu-id="8839b-133">None</span><span class="sxs-lookup"><span data-stu-id="8839b-133">None</span></span>

## <span data-ttu-id="8839b-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8839b-134">OUTPUTS</span></span>

### <span data-ttu-id="8839b-135">System. Management. Automation. VerbInfo</span><span class="sxs-lookup"><span data-stu-id="8839b-135">System.Management.Automation.VerbInfo</span></span>

## <span data-ttu-id="8839b-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8839b-136">NOTES</span></span>

<span data-ttu-id="8839b-137">Les verbes PowerShell sont affectés à un groupe en fonction de leur utilisation la plus courante.</span><span class="sxs-lookup"><span data-stu-id="8839b-137">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="8839b-138">Les groupes sont conçus pour faciliter la recherche et la comparaison des verbes, sans limiter leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="8839b-138">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="8839b-139">Vous pouvez utiliser n'importe quel verbe approuvé pour n'importe quel type de commande.</span><span class="sxs-lookup"><span data-stu-id="8839b-139">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="8839b-140">Chaque verbe PowerShell est affecté à l’un des groupes suivants.</span><span class="sxs-lookup"><span data-stu-id="8839b-140">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="8839b-141">Commun : définissez des actions génériques qui peuvent s’appliquer à presque n’importe quelle applet de commande, telle que Add.</span><span class="sxs-lookup"><span data-stu-id="8839b-141">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="8839b-142">Communications : définissez les actions qui s’appliquent aux communications, telles que Connect.</span><span class="sxs-lookup"><span data-stu-id="8839b-142">Communications: Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="8839b-143">Données : définissez les actions qui s’appliquent à la gestion des données, telles que la sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="8839b-143">Data: Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="8839b-144">Diagnostic : définissez les actions qui s’appliquent aux diagnostics, telles que le débogage.</span><span class="sxs-lookup"><span data-stu-id="8839b-144">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="8839b-145">Cycle de vie : définissez les actions qui s’appliquent au cycle de vie d’une applet de commande, comme complet.</span><span class="sxs-lookup"><span data-stu-id="8839b-145">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="8839b-146">Sécurité : définissez les actions qui s’appliquent à la sécurité, telles que REVOKE.</span><span class="sxs-lookup"><span data-stu-id="8839b-146">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="8839b-147">Autre : définissez d’autres types d’actions.</span><span class="sxs-lookup"><span data-stu-id="8839b-147">Other: Define other types of actions.</span></span>

<span data-ttu-id="8839b-148">Certaines des applets de commande installées avec PowerShell, telles que `Tee-Object` et `Where-Object` , utilisent des verbes non approuvés.</span><span class="sxs-lookup"><span data-stu-id="8839b-148">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="8839b-149">Ces applets de commande sont des exceptions historiques et leurs verbes sont classés comme **réservés**.</span><span class="sxs-lookup"><span data-stu-id="8839b-149">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="8839b-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8839b-150">RELATED LINKS</span></span>

[<span data-ttu-id="8839b-151">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="8839b-151">Import-Module</span></span>](../microsoft.powershell.core/import-module.md)

