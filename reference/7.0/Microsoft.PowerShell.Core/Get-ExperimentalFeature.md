---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 22e1b21f304129d6912557a5dbc825bc4e6202a1
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193915"
---
# <span data-ttu-id="65221-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="65221-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="65221-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="65221-103">SYNOPSIS</span></span>
<span data-ttu-id="65221-104">Obtient des fonctionnalités expérimentales.</span><span class="sxs-lookup"><span data-stu-id="65221-104">Gets experimental features.</span></span>

## <span data-ttu-id="65221-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="65221-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="65221-106">Description</span><span class="sxs-lookup"><span data-stu-id="65221-106">DESCRIPTION</span></span>

<span data-ttu-id="65221-107">L' `Get-ExperimentalFeature` applet de commande retourne toutes les fonctionnalités expérimentales découvertes par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65221-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="65221-108">Les fonctionnalités expérimentales peuvent provenir de modules ou du moteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65221-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="65221-109">Les fonctionnalités expérimentales permettent aux utilisateurs de tester en toute sécurité de nouvelles fonctionnalités et de fournir des commentaires (généralement via GitHub) avant que la conception ne soit considérée comme terminée et que toute modification puisse devenir une modification avec rupture.</span><span class="sxs-lookup"><span data-stu-id="65221-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="65221-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="65221-110">EXAMPLES</span></span>

### <span data-ttu-id="65221-111">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="65221-111">Example 1</span></span>

<span data-ttu-id="65221-112">Obtient la liste des fonctionnalités expérimentales actuellement inscrites et leur état actuel.</span><span class="sxs-lookup"><span data-stu-id="65221-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="65221-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="65221-113">PARAMETERS</span></span>

### <span data-ttu-id="65221-114">-Name</span><span class="sxs-lookup"><span data-stu-id="65221-114">-Name</span></span>

<span data-ttu-id="65221-115">Nom ou noms de fonctionnalités expérimentales spécifiques à retourner.</span><span class="sxs-lookup"><span data-stu-id="65221-115">Name or names of specific experimental features to return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="65221-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65221-116">CommonParameters</span></span>

<span data-ttu-id="65221-117">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="65221-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65221-118">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="65221-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="65221-119">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="65221-119">INPUTS</span></span>

### <span data-ttu-id="65221-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="65221-120">System.String[]</span></span>

<span data-ttu-id="65221-121">Nom ou noms des fonctionnalités expérimentales à retourner.</span><span class="sxs-lookup"><span data-stu-id="65221-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="65221-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="65221-122">OUTPUTS</span></span>

### <span data-ttu-id="65221-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="65221-123">ExperimentalFeature</span></span>

<span data-ttu-id="65221-124">Retourne des instances qui correspondent aux noms demandés ou à toutes les fonctionnalités expérimentales si aucun nom n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="65221-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="65221-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="65221-125">NOTES</span></span>

## <span data-ttu-id="65221-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="65221-126">RELATED LINKS</span></span>

[<span data-ttu-id="65221-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="65221-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="65221-128">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="65221-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
