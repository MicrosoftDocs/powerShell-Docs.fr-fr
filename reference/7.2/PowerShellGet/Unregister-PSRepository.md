---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598148"
---
# <span data-ttu-id="d3c50-102">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3c50-102">Unregister-PSRepository</span></span>

## <span data-ttu-id="d3c50-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d3c50-103">SYNOPSIS</span></span>
<span data-ttu-id="d3c50-104">Annule l’enregistrement d’un référentiel.</span><span class="sxs-lookup"><span data-stu-id="d3c50-104">Unregisters a repository.</span></span>

## <span data-ttu-id="d3c50-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d3c50-105">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="d3c50-106">Description</span><span class="sxs-lookup"><span data-stu-id="d3c50-106">DESCRIPTION</span></span>

<span data-ttu-id="d3c50-107">L' `Unregister-PSRepository` applet de commande annule l’inscription d’un référentiel pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d3c50-107">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="d3c50-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d3c50-108">EXAMPLES</span></span>

### <span data-ttu-id="d3c50-109">Exemple 1 : annuler l’inscription d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="d3c50-109">Example 1: Unregister a repository</span></span>

<span data-ttu-id="d3c50-110">Cet exemple annule l’inscription du dépôt nommé myNuGetSource.</span><span class="sxs-lookup"><span data-stu-id="d3c50-110">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="d3c50-111">Exemple 2 : annuler l’inscription de tous les référentiels</span><span class="sxs-lookup"><span data-stu-id="d3c50-111">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="d3c50-112">Cet exemple utilise `Get-PSRepository` pour récupérer tous les dépôts inscrits et utilise l’opérateur de pipeline pour les transmettre à `Unregister-PSRepository` pour annuler leur inscription.</span><span class="sxs-lookup"><span data-stu-id="d3c50-112">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="d3c50-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d3c50-113">PARAMETERS</span></span>

### <span data-ttu-id="d3c50-114">-Name</span><span class="sxs-lookup"><span data-stu-id="d3c50-114">-Name</span></span>

<span data-ttu-id="d3c50-115">Spécifie un tableau de noms des référentiels à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d3c50-115">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="d3c50-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d3c50-116">CommonParameters</span></span>

<span data-ttu-id="d3c50-117">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d3c50-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d3c50-118">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d3c50-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d3c50-119">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d3c50-119">INPUTS</span></span>

### <span data-ttu-id="d3c50-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d3c50-120">System.String[]</span></span>

## <span data-ttu-id="d3c50-121">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d3c50-121">OUTPUTS</span></span>

### <span data-ttu-id="d3c50-122">System.Object</span><span class="sxs-lookup"><span data-stu-id="d3c50-122">System.Object</span></span>

## <span data-ttu-id="d3c50-123">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d3c50-123">NOTES</span></span>

## <span data-ttu-id="d3c50-124">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d3c50-124">RELATED LINKS</span></span>

[<span data-ttu-id="d3c50-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3c50-125">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="d3c50-126">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3c50-126">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="d3c50-127">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d3c50-127">Set-PSRepository</span></span>](Set-PSRepository.md)
