---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: e24bb117b4d4277adc359c130789cf7ee03b1fd6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204134"
---
# <span data-ttu-id="9a5e7-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="9a5e7-103">Get-PSRepository</span></span>

## <span data-ttu-id="9a5e7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9a5e7-104">SYNOPSIS</span></span>
<span data-ttu-id="9a5e7-105">Obtient les référentiels PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-105">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="9a5e7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a5e7-106">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="9a5e7-107">Description</span><span class="sxs-lookup"><span data-stu-id="9a5e7-107">DESCRIPTION</span></span>

<span data-ttu-id="9a5e7-108">L’applet de commande **obtenir-PSRepository** obtient les référentiels de module PowerShell qui sont inscrits pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-108">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="9a5e7-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9a5e7-109">EXAMPLES</span></span>

### <span data-ttu-id="9a5e7-110">Exemple 1 : récupération de tous les référentiels de modules</span><span class="sxs-lookup"><span data-stu-id="9a5e7-110">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="9a5e7-111">Cette commande obtient tous les référentiels de module inscrits pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-111">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="9a5e7-112">Exemple 2 : récupérer des référentiels de module par nom</span><span class="sxs-lookup"><span data-stu-id="9a5e7-112">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="9a5e7-113">Cette commande obtient tous les référentiels de modules qui incluent NuGet dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-113">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="9a5e7-114">Exemple 3 : obtenir un référentiel de module et mettre en forme la sortie</span><span class="sxs-lookup"><span data-stu-id="9a5e7-114">Example 3: Get a module repository and format the output</span></span>

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

<span data-ttu-id="9a5e7-115">Cette commande obtient le référentiel nommé Local01 et utilise l’opérateur de pipeline pour passer cet objet à l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-115">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="9a5e7-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a5e7-116">PARAMETERS</span></span>

### <span data-ttu-id="9a5e7-117">-Name</span><span class="sxs-lookup"><span data-stu-id="9a5e7-117">-Name</span></span>

<span data-ttu-id="9a5e7-118">Spécifie les noms des référentiels à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-118">Specifies the names of the repositories to get.</span></span>

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

### <span data-ttu-id="9a5e7-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a5e7-119">CommonParameters</span></span>

<span data-ttu-id="9a5e7-120">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9a5e7-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a5e7-121">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9a5e7-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a5e7-122">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9a5e7-122">INPUTS</span></span>

### <span data-ttu-id="9a5e7-123">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9a5e7-123">System.String[]</span></span>

## <span data-ttu-id="9a5e7-124">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9a5e7-124">OUTPUTS</span></span>

### <span data-ttu-id="9a5e7-125">System.Object</span><span class="sxs-lookup"><span data-stu-id="9a5e7-125">System.Object</span></span>

## <span data-ttu-id="9a5e7-126">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9a5e7-126">NOTES</span></span>

## <span data-ttu-id="9a5e7-127">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9a5e7-127">RELATED LINKS</span></span>

[<span data-ttu-id="9a5e7-128">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="9a5e7-128">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="9a5e7-129">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="9a5e7-129">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="9a5e7-130">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="9a5e7-130">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

