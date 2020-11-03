---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: 3260b3d8333e8a79fdf603c372d1e3e50aa0dabc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205174"
---
# <span data-ttu-id="e0f75-102">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e0f75-102">Disable-ExperimentalFeature</span></span>

## <span data-ttu-id="e0f75-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e0f75-103">SYNOPSIS</span></span>
<span data-ttu-id="e0f75-104">Désactivez une fonctionnalité expérimentale au démarrage de la nouvelle instance de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0f75-104">Disable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="e0f75-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0f75-105">SYNTAX</span></span>

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e0f75-106">Description</span><span class="sxs-lookup"><span data-stu-id="e0f75-106">DESCRIPTION</span></span>

<span data-ttu-id="e0f75-107">L' `Disable-ExperimentalFeature` applet de commande désactive les fonctionnalités expérimentales en supprimant les fonctionnalités expérimentales nommées du `powershell.config.json` fichier de paramètres lu lors du démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0f75-107">The `Disable-ExperimentalFeature` cmdlet disables experimental features by removing the named experimental features from the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="e0f75-108">Cette applet de commande a été introduite dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="e0f75-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="e0f75-109">Les modifications apportées à l’état de la fonctionnalité expérimentale prennent effet uniquement au redémarrage de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0f75-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="e0f75-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e0f75-110">EXAMPLES</span></span>

### <span data-ttu-id="e0f75-111">Exemple 1 : désactiver une fonctionnalité expérimentale</span><span class="sxs-lookup"><span data-stu-id="e0f75-111">Example 1: Disable an experimental feature</span></span>

<span data-ttu-id="e0f75-112">Dans cet exemple, si cette fonctionnalité expérimentale était activée précédemment, le `powershell.config.json` fichier est mis à jour pour que l’utilisateur n’active pas cette fonctionnalité une fois PowerShell redémarré.</span><span class="sxs-lookup"><span data-stu-id="e0f75-112">In this example, if this experimental feature was previously enabled, then the `powershell.config.json` file is updated for the user to not enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="e0f75-113">En cas de réussite, rien n’est affiché dans le pipeline et un seul message d’avertissement s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e0f75-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="e0f75-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0f75-114">PARAMETERS</span></span>

### <span data-ttu-id="e0f75-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e0f75-115">-Confirm</span></span>

<span data-ttu-id="e0f75-116">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0f75-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e0f75-117">-Name</span><span class="sxs-lookup"><span data-stu-id="e0f75-117">-Name</span></span>

<span data-ttu-id="e0f75-118">Nom ou noms des fonctionnalités expérimentales à désactiver.</span><span class="sxs-lookup"><span data-stu-id="e0f75-118">The name or names of the experimental features to disable.</span></span>

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

### <span data-ttu-id="e0f75-119">-Étendue</span><span class="sxs-lookup"><span data-stu-id="e0f75-119">-Scope</span></span>

<span data-ttu-id="e0f75-120">Détermine `powershell.config.json` la mise à jour qui affecte tous les utilisateurs ou uniquement l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e0f75-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

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

### <span data-ttu-id="e0f75-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e0f75-121">-WhatIf</span></span>

<span data-ttu-id="e0f75-122">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e0f75-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e0f75-123">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e0f75-123">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e0f75-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0f75-124">CommonParameters</span></span>

<span data-ttu-id="e0f75-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0f75-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0f75-126">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e0f75-126">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0f75-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e0f75-127">INPUTS</span></span>

### <span data-ttu-id="e0f75-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e0f75-128">ExperimentalFeature</span></span>

<span data-ttu-id="e0f75-129">Les instances de canal de ExperimentalFeature de l’applet de commande `Get-ExperimentalFeature` à désactiver.</span><span class="sxs-lookup"><span data-stu-id="e0f75-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to disable.</span></span>

## <span data-ttu-id="e0f75-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e0f75-130">OUTPUTS</span></span>

### <span data-ttu-id="e0f75-131">Aucun</span><span class="sxs-lookup"><span data-stu-id="e0f75-131">None</span></span>

<span data-ttu-id="e0f75-132">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e0f75-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="e0f75-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e0f75-133">NOTES</span></span>

<span data-ttu-id="e0f75-134">Les modifications apportées à l’état d’une fonctionnalité expérimentale prennent uniquement effet au redémarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0f75-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="e0f75-135">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e0f75-135">RELATED LINKS</span></span>

[<span data-ttu-id="e0f75-136">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e0f75-136">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)

[<span data-ttu-id="e0f75-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e0f75-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

