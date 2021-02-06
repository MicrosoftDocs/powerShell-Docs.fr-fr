---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: fe5fc0feb34fda87dab987f33140992a346017a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597990"
---
# <span data-ttu-id="d77ab-102">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d77ab-102">Get-InstalledScript</span></span>

## <span data-ttu-id="d77ab-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d77ab-103">SYNOPSIS</span></span>
<span data-ttu-id="d77ab-104">Obtient un script installé.</span><span class="sxs-lookup"><span data-stu-id="d77ab-104">Gets an installed script.</span></span>

## <span data-ttu-id="d77ab-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d77ab-105">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="d77ab-106">Description</span><span class="sxs-lookup"><span data-stu-id="d77ab-106">DESCRIPTION</span></span>

<span data-ttu-id="d77ab-107">L’applet de commande **InstalledScript** obtient les scripts installés pour les étendues CurrentUser et ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="d77ab-107">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="d77ab-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d77ab-108">EXAMPLES</span></span>

### <span data-ttu-id="d77ab-109">Exemple 1 : récupération de tous les scripts installés</span><span class="sxs-lookup"><span data-stu-id="d77ab-109">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="d77ab-110">Cette commande obtient tous les scripts installés.</span><span class="sxs-lookup"><span data-stu-id="d77ab-110">This command gets all installed scripts.</span></span>

### <span data-ttu-id="d77ab-111">Exemple 2 : récupérer les scripts installés par nom</span><span class="sxs-lookup"><span data-stu-id="d77ab-111">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="d77ab-112">Cette commande obtient les scripts dont le nom commence par required-générer un script.</span><span class="sxs-lookup"><span data-stu-id="d77ab-112">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="d77ab-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d77ab-113">PARAMETERS</span></span>

### <span data-ttu-id="d77ab-114">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="d77ab-114">-AllowPrerelease</span></span>

<span data-ttu-id="d77ab-115">Comprend dans les scripts de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="d77ab-115">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="d77ab-116">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d77ab-116">-MaximumVersion</span></span>

<span data-ttu-id="d77ab-117">Spécifie la version maximale ou la dernière version d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="d77ab-117">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="d77ab-118">Les paramètres *MaximumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d77ab-118">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="d77ab-119">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d77ab-119">-MinimumVersion</span></span>

<span data-ttu-id="d77ab-120">Spécifie la version minimale d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="d77ab-120">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="d77ab-121">Les paramètres *MinimumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d77ab-121">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="d77ab-122">-Name</span><span class="sxs-lookup"><span data-stu-id="d77ab-122">-Name</span></span>

<span data-ttu-id="d77ab-123">Spécifie un tableau de noms de scripts à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d77ab-123">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="d77ab-124">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="d77ab-124">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="d77ab-125">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d77ab-125">-RequiredVersion</span></span>

<span data-ttu-id="d77ab-126">Spécifie la version exacte d’un script à obtenir.</span><span class="sxs-lookup"><span data-stu-id="d77ab-126">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="d77ab-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d77ab-127">CommonParameters</span></span>

<span data-ttu-id="d77ab-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d77ab-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d77ab-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d77ab-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d77ab-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d77ab-130">INPUTS</span></span>

### <span data-ttu-id="d77ab-131">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d77ab-131">System.String[]</span></span>

### <span data-ttu-id="d77ab-132">System.String</span><span class="sxs-lookup"><span data-stu-id="d77ab-132">System.String</span></span>

## <span data-ttu-id="d77ab-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d77ab-133">OUTPUTS</span></span>

### <span data-ttu-id="d77ab-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="d77ab-134">System.Object</span></span>

## <span data-ttu-id="d77ab-135">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d77ab-135">NOTES</span></span>

## <span data-ttu-id="d77ab-136">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d77ab-136">RELATED LINKS</span></span>

[<span data-ttu-id="d77ab-137">Install-Script</span><span class="sxs-lookup"><span data-stu-id="d77ab-137">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="d77ab-138">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="d77ab-138">Uninstall-Script</span></span>](Uninstall-Script.md)

