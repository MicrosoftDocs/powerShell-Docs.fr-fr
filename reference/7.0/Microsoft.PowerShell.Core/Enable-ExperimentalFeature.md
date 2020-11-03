---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 79884c73bc6e010eb218f1b722d26e0aaa05ef53
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201778"
---
# <span data-ttu-id="8c5e1-102">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="8c5e1-102">Enable-ExperimentalFeature</span></span>

## <span data-ttu-id="8c5e1-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8c5e1-103">SYNOPSIS</span></span>
<span data-ttu-id="8c5e1-104">Activez une fonctionnalité expérimentale au démarrage de la nouvelle instance de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-104">Enable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="8c5e1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c5e1-105">SYNTAX</span></span>

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8c5e1-106">Description</span><span class="sxs-lookup"><span data-stu-id="8c5e1-106">DESCRIPTION</span></span>

<span data-ttu-id="8c5e1-107">L' `Enable-ExperimentalFeature` applet de commande active les fonctionnalités expérimentales en ajoutant les fonctionnalités expérimentales nommées au `powershell.config.json` fichier de paramètres lu au démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-107">The `Enable-ExperimentalFeature` cmdlet enables experimental features by adding the named experimental features to the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="8c5e1-108">Cette applet de commande a été introduite dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="8c5e1-109">Les modifications apportées à l’état de la fonctionnalité expérimentale prennent effet uniquement au redémarrage de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c5e1-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="8c5e1-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8c5e1-110">EXAMPLES</span></span>

### <span data-ttu-id="8c5e1-111">Exemple 1 : activer une fonctionnalité expérimentale</span><span class="sxs-lookup"><span data-stu-id="8c5e1-111">Example 1: Enable an experimental feature</span></span>

<span data-ttu-id="8c5e1-112">Dans cet exemple, si cette fonctionnalité expérimentale était précédemment désactivée, le `powershell.config.json` fichier est mis à jour pour permettre à l’utilisateur d’activer cette fonctionnalité une fois PowerShell redémarré.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-112">In this example, if this experimental feature was previously disabled, then the `powershell.config.json` file is updated for the user to enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="8c5e1-113">En cas de réussite, rien n’est affiché dans le pipeline et un seul message d’avertissement s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="8c5e1-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c5e1-114">PARAMETERS</span></span>

### <span data-ttu-id="8c5e1-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8c5e1-115">-Confirm</span></span>

<span data-ttu-id="8c5e1-116">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-116">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c5e1-117">-Name</span><span class="sxs-lookup"><span data-stu-id="8c5e1-117">-Name</span></span>

<span data-ttu-id="8c5e1-118">Nom ou noms des fonctionnalités expérimentales à activer.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-118">The name or names of the experimental features to enable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c5e1-119">-Étendue</span><span class="sxs-lookup"><span data-stu-id="8c5e1-119">-Scope</span></span>

<span data-ttu-id="8c5e1-120">Détermine `powershell.config.json` la mise à jour qui affecte tous les utilisateurs ou uniquement l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c5e1-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8c5e1-121">-WhatIf</span></span>

<span data-ttu-id="8c5e1-122">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8c5e1-123">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-123">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c5e1-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c5e1-124">CommonParameters</span></span>

<span data-ttu-id="8c5e1-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c5e1-126">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c5e1-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c5e1-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8c5e1-127">INPUTS</span></span>

### <span data-ttu-id="8c5e1-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="8c5e1-128">ExperimentalFeature</span></span>

<span data-ttu-id="8c5e1-129">Les instances de canal de ExperimentalFeature à partir de l' `Get-ExperimentalFeature` applet de commande pour activer.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to enable.</span></span>

## <span data-ttu-id="8c5e1-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8c5e1-130">OUTPUTS</span></span>

### <span data-ttu-id="8c5e1-131">Aucun</span><span class="sxs-lookup"><span data-stu-id="8c5e1-131">None</span></span>

<span data-ttu-id="8c5e1-132">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="8c5e1-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8c5e1-133">NOTES</span></span>

<span data-ttu-id="8c5e1-134">Les modifications apportées à l’état d’une fonctionnalité expérimentale prennent uniquement effet au redémarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c5e1-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="8c5e1-135">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8c5e1-135">RELATED LINKS</span></span>

[<span data-ttu-id="8c5e1-136">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="8c5e1-136">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="8c5e1-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="8c5e1-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)
