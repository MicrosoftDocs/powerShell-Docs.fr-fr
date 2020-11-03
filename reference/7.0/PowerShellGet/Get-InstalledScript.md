---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: a90ece844d5a271402537f17c601bf2e36b5ed8c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201405"
---
# <span data-ttu-id="9892e-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="9892e-103">Get-InstalledScript</span></span>

## <span data-ttu-id="9892e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9892e-104">SYNOPSIS</span></span>
<span data-ttu-id="9892e-105">Obtient un script installé.</span><span class="sxs-lookup"><span data-stu-id="9892e-105">Gets an installed script.</span></span>

## <span data-ttu-id="9892e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9892e-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="9892e-107">Description</span><span class="sxs-lookup"><span data-stu-id="9892e-107">DESCRIPTION</span></span>

<span data-ttu-id="9892e-108">L’applet de commande **InstalledScript** obtient les scripts installés pour les étendues CurrentUser et ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="9892e-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="9892e-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9892e-109">EXAMPLES</span></span>

### <span data-ttu-id="9892e-110">Exemple 1 : récupération de tous les scripts installés</span><span class="sxs-lookup"><span data-stu-id="9892e-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="9892e-111">Cette commande obtient tous les scripts installés.</span><span class="sxs-lookup"><span data-stu-id="9892e-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="9892e-112">Exemple 2 : récupérer les scripts installés par nom</span><span class="sxs-lookup"><span data-stu-id="9892e-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="9892e-113">Cette commande obtient les scripts dont le nom commence par required-générer un script.</span><span class="sxs-lookup"><span data-stu-id="9892e-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="9892e-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9892e-114">PARAMETERS</span></span>

### <span data-ttu-id="9892e-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9892e-115">-AllowPrerelease</span></span>

<span data-ttu-id="9892e-116">Comprend dans les scripts de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="9892e-116">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="9892e-117">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9892e-117">-MaximumVersion</span></span>

<span data-ttu-id="9892e-118">Spécifie la version maximale ou la dernière version d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="9892e-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="9892e-119">Les paramètres *MaximumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="9892e-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="9892e-120">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9892e-120">-MinimumVersion</span></span>

<span data-ttu-id="9892e-121">Spécifie la version minimale d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="9892e-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="9892e-122">Les paramètres *MinimumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="9892e-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="9892e-123">-Name</span><span class="sxs-lookup"><span data-stu-id="9892e-123">-Name</span></span>

<span data-ttu-id="9892e-124">Spécifie un tableau de noms de scripts à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9892e-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="9892e-125">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="9892e-125">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="9892e-126">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9892e-126">-RequiredVersion</span></span>

<span data-ttu-id="9892e-127">Spécifie la version exacte d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="9892e-127">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="9892e-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9892e-128">CommonParameters</span></span>

<span data-ttu-id="9892e-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9892e-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9892e-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9892e-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9892e-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9892e-131">INPUTS</span></span>

### <span data-ttu-id="9892e-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9892e-132">System.String[]</span></span>

### <span data-ttu-id="9892e-133">System.String</span><span class="sxs-lookup"><span data-stu-id="9892e-133">System.String</span></span>

## <span data-ttu-id="9892e-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9892e-134">OUTPUTS</span></span>

### <span data-ttu-id="9892e-135">System.Object</span><span class="sxs-lookup"><span data-stu-id="9892e-135">System.Object</span></span>

## <span data-ttu-id="9892e-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9892e-136">NOTES</span></span>

## <span data-ttu-id="9892e-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9892e-137">RELATED LINKS</span></span>

[<span data-ttu-id="9892e-138">Install-Script</span><span class="sxs-lookup"><span data-stu-id="9892e-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="9892e-139">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="9892e-139">Uninstall-Script</span></span>](Uninstall-Script.md)
