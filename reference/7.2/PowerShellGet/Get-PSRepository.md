---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: 66f840d99b107da22b6771e6327ab68d33a1b368
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595931"
---
# <span data-ttu-id="c6aad-102">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c6aad-102">Get-PSRepository</span></span>

## <span data-ttu-id="c6aad-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c6aad-103">SYNOPSIS</span></span>
<span data-ttu-id="c6aad-104">Obtient les référentiels PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6aad-104">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="c6aad-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c6aad-105">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c6aad-106">Description</span><span class="sxs-lookup"><span data-stu-id="c6aad-106">DESCRIPTION</span></span>

<span data-ttu-id="c6aad-107">L’applet de commande **obtenir-PSRepository** obtient les référentiels de module PowerShell qui sont inscrits pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c6aad-107">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="c6aad-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c6aad-108">EXAMPLES</span></span>

### <span data-ttu-id="c6aad-109">Exemple 1 : récupération de tous les référentiels de modules</span><span class="sxs-lookup"><span data-stu-id="c6aad-109">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="c6aad-110">Cette commande obtient tous les référentiels de module inscrits pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c6aad-110">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="c6aad-111">Exemple 2 : récupérer des référentiels de module par nom</span><span class="sxs-lookup"><span data-stu-id="c6aad-111">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="c6aad-112">Cette commande obtient tous les référentiels de modules qui incluent NuGet dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="c6aad-112">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="c6aad-113">Exemple 3 : obtenir un référentiel de module et mettre en forme la sortie</span><span class="sxs-lookup"><span data-stu-id="c6aad-113">Example 3: Get a module repository and format the output</span></span>

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

<span data-ttu-id="c6aad-114">Cette commande obtient le référentiel nommé Local01 et utilise l’opérateur de pipeline pour passer cet objet à l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="c6aad-114">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="c6aad-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c6aad-115">PARAMETERS</span></span>

### <span data-ttu-id="c6aad-116">-Name</span><span class="sxs-lookup"><span data-stu-id="c6aad-116">-Name</span></span>

<span data-ttu-id="c6aad-117">Spécifie les noms des référentiels à récupérer.</span><span class="sxs-lookup"><span data-stu-id="c6aad-117">Specifies the names of the repositories to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6aad-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6aad-118">CommonParameters</span></span>

<span data-ttu-id="c6aad-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c6aad-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6aad-120">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c6aad-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6aad-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c6aad-121">INPUTS</span></span>

### <span data-ttu-id="c6aad-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c6aad-122">System.String[]</span></span>

## <span data-ttu-id="c6aad-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c6aad-123">OUTPUTS</span></span>

### <span data-ttu-id="c6aad-124">System.Object</span><span class="sxs-lookup"><span data-stu-id="c6aad-124">System.Object</span></span>

## <span data-ttu-id="c6aad-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c6aad-125">NOTES</span></span>

## <span data-ttu-id="c6aad-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c6aad-126">RELATED LINKS</span></span>

[<span data-ttu-id="c6aad-127">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c6aad-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="c6aad-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c6aad-128">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="c6aad-129">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c6aad-129">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

