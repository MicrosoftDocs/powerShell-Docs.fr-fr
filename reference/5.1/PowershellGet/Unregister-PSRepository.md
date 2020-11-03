---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 0d98d7bbb26d5a50542f0e125e912ea6333714c1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203877"
---
# <span data-ttu-id="40ba1-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="40ba1-103">Unregister-PSRepository</span></span>

## <span data-ttu-id="40ba1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="40ba1-104">SYNOPSIS</span></span>
<span data-ttu-id="40ba1-105">Annule l’enregistrement d’un référentiel.</span><span class="sxs-lookup"><span data-stu-id="40ba1-105">Unregisters a repository.</span></span>

## <span data-ttu-id="40ba1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="40ba1-106">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="40ba1-107">Description</span><span class="sxs-lookup"><span data-stu-id="40ba1-107">DESCRIPTION</span></span>

<span data-ttu-id="40ba1-108">L' `Unregister-PSRepository` applet de commande annule l’inscription d’un référentiel pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="40ba1-108">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="40ba1-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="40ba1-109">EXAMPLES</span></span>

### <span data-ttu-id="40ba1-110">Exemple 1 : annuler l’inscription d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="40ba1-110">Example 1: Unregister a repository</span></span>

<span data-ttu-id="40ba1-111">Cet exemple annule l’inscription du dépôt nommé myNuGetSource.</span><span class="sxs-lookup"><span data-stu-id="40ba1-111">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="40ba1-112">Exemple 2 : annuler l’inscription de tous les référentiels</span><span class="sxs-lookup"><span data-stu-id="40ba1-112">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="40ba1-113">Cet exemple utilise `Get-PSRepository` pour récupérer tous les dépôts inscrits et utilise l’opérateur de pipeline pour les transmettre à `Unregister-PSRepository` pour annuler leur inscription.</span><span class="sxs-lookup"><span data-stu-id="40ba1-113">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="40ba1-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="40ba1-114">PARAMETERS</span></span>

### <span data-ttu-id="40ba1-115">-Name</span><span class="sxs-lookup"><span data-stu-id="40ba1-115">-Name</span></span>

<span data-ttu-id="40ba1-116">Spécifie un tableau de noms des référentiels à supprimer.</span><span class="sxs-lookup"><span data-stu-id="40ba1-116">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="40ba1-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40ba1-117">CommonParameters</span></span>

<span data-ttu-id="40ba1-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40ba1-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40ba1-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="40ba1-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40ba1-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="40ba1-120">INPUTS</span></span>

### <span data-ttu-id="40ba1-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="40ba1-121">System.String[]</span></span>

## <span data-ttu-id="40ba1-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="40ba1-122">OUTPUTS</span></span>

### <span data-ttu-id="40ba1-123">System.Object</span><span class="sxs-lookup"><span data-stu-id="40ba1-123">System.Object</span></span>

## <span data-ttu-id="40ba1-124">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="40ba1-124">NOTES</span></span>

## <span data-ttu-id="40ba1-125">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="40ba1-125">RELATED LINKS</span></span>

[<span data-ttu-id="40ba1-126">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="40ba1-126">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="40ba1-127">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="40ba1-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="40ba1-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="40ba1-128">Set-PSRepository</span></span>](Set-PSRepository.md)
