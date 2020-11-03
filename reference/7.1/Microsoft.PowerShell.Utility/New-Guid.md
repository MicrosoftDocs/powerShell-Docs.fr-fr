---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 2a289500020f069231023fbabaa5401ee0759697
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200970"
---
# <span data-ttu-id="09a53-103">New-Guid</span><span class="sxs-lookup"><span data-stu-id="09a53-103">New-Guid</span></span>

## <span data-ttu-id="09a53-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="09a53-104">SYNOPSIS</span></span>
<span data-ttu-id="09a53-105">Crée un GUID.</span><span class="sxs-lookup"><span data-stu-id="09a53-105">Creates a GUID.</span></span>

## <span data-ttu-id="09a53-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="09a53-106">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="09a53-107">Description</span><span class="sxs-lookup"><span data-stu-id="09a53-107">DESCRIPTION</span></span>

<span data-ttu-id="09a53-108">L’applet **de commande New-GUID** crée un identificateur global unique (Guid) aléatoire.</span><span class="sxs-lookup"><span data-stu-id="09a53-108">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="09a53-109">Si vous avez besoin d’un ID unique dans un script, vous pouvez créer un GUID, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="09a53-109">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="09a53-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="09a53-110">EXAMPLES</span></span>

### <span data-ttu-id="09a53-111">Exemple 1 : créer un GUID</span><span class="sxs-lookup"><span data-stu-id="09a53-111">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="09a53-112">Cette commande crée un GUID aléatoire.</span><span class="sxs-lookup"><span data-stu-id="09a53-112">This command creates a random GUID.</span></span>
<span data-ttu-id="09a53-113">Vous pouvez également stocker la sortie de cette applet de commande dans une variable à utiliser ailleurs dans un script.</span><span class="sxs-lookup"><span data-stu-id="09a53-113">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="09a53-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09a53-114">PARAMETERS</span></span>

### <span data-ttu-id="09a53-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09a53-115">CommonParameters</span></span>

<span data-ttu-id="09a53-116">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="09a53-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09a53-117">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="09a53-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09a53-118">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="09a53-118">INPUTS</span></span>

## <span data-ttu-id="09a53-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="09a53-119">OUTPUTS</span></span>

### <span data-ttu-id="09a53-120">System.Guid</span><span class="sxs-lookup"><span data-stu-id="09a53-120">System.Guid</span></span>

<span data-ttu-id="09a53-121">Cette applet de commande retourne un GUID.</span><span class="sxs-lookup"><span data-stu-id="09a53-121">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="09a53-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="09a53-122">NOTES</span></span>

## <span data-ttu-id="09a53-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="09a53-123">RELATED LINKS</span></span>

