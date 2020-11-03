---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: 6b99eb73fb126b67b97fc360b2f0474710b4cc52
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204137"
---
# <span data-ttu-id="feb91-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="feb91-103">Get-InstalledScript</span></span>

## <span data-ttu-id="feb91-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="feb91-104">SYNOPSIS</span></span>
<span data-ttu-id="feb91-105">Obtient un script installé.</span><span class="sxs-lookup"><span data-stu-id="feb91-105">Gets an installed script.</span></span>

## <span data-ttu-id="feb91-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="feb91-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="feb91-107">Description</span><span class="sxs-lookup"><span data-stu-id="feb91-107">DESCRIPTION</span></span>

<span data-ttu-id="feb91-108">L’applet de commande **InstalledScript** obtient les scripts installés pour les étendues CurrentUser et ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="feb91-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="feb91-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="feb91-109">EXAMPLES</span></span>

### <span data-ttu-id="feb91-110">Exemple 1 : récupération de tous les scripts installés</span><span class="sxs-lookup"><span data-stu-id="feb91-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="feb91-111">Cette commande obtient tous les scripts installés.</span><span class="sxs-lookup"><span data-stu-id="feb91-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="feb91-112">Exemple 2 : récupérer les scripts installés par nom</span><span class="sxs-lookup"><span data-stu-id="feb91-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="feb91-113">Cette commande obtient les scripts dont le nom commence par required-générer un script.</span><span class="sxs-lookup"><span data-stu-id="feb91-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="feb91-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="feb91-114">PARAMETERS</span></span>

### <span data-ttu-id="feb91-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="feb91-115">-AllowPrerelease</span></span>

<span data-ttu-id="feb91-116">Comprend dans les scripts de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="feb91-116">Includes in the results scripts marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="feb91-117">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="feb91-117">-MaximumVersion</span></span>

<span data-ttu-id="feb91-118">Spécifie la version maximale ou la dernière version d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="feb91-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="feb91-119">Les paramètres *MaximumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="feb91-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="feb91-120">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="feb91-120">-MinimumVersion</span></span>

<span data-ttu-id="feb91-121">Spécifie la version minimale d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="feb91-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="feb91-122">Les paramètres *MinimumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="feb91-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="feb91-123">-Name</span><span class="sxs-lookup"><span data-stu-id="feb91-123">-Name</span></span>

<span data-ttu-id="feb91-124">Spécifie un tableau de noms de scripts à récupérer.</span><span class="sxs-lookup"><span data-stu-id="feb91-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="feb91-125">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="feb91-125">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="feb91-126">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="feb91-126">-RequiredVersion</span></span>

<span data-ttu-id="feb91-127">Spécifie la version exacte d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="feb91-127">Specifies the exact version of a script to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="feb91-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="feb91-128">CommonParameters</span></span>

<span data-ttu-id="feb91-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="feb91-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="feb91-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="feb91-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="feb91-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="feb91-131">INPUTS</span></span>

### <span data-ttu-id="feb91-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="feb91-132">System.String[]</span></span>

### <span data-ttu-id="feb91-133">System.String</span><span class="sxs-lookup"><span data-stu-id="feb91-133">System.String</span></span>

## <span data-ttu-id="feb91-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="feb91-134">OUTPUTS</span></span>

### <span data-ttu-id="feb91-135">System.Object</span><span class="sxs-lookup"><span data-stu-id="feb91-135">System.Object</span></span>

## <span data-ttu-id="feb91-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="feb91-136">NOTES</span></span>

## <span data-ttu-id="feb91-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="feb91-137">RELATED LINKS</span></span>

[<span data-ttu-id="feb91-138">Install-Script</span><span class="sxs-lookup"><span data-stu-id="feb91-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="feb91-139">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="feb91-139">Uninstall-Script</span></span>](Uninstall-Script.md)

