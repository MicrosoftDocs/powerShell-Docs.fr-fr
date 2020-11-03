---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: b6111929a2995432ff92758ce8b014f38882792f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202166"
---
# <span data-ttu-id="f7573-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="f7573-103">Start-Sleep</span></span>

## <span data-ttu-id="f7573-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f7573-104">SYNOPSIS</span></span>
<span data-ttu-id="f7573-105">Interrompt l'activité dans un script ou une session pour la période spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f7573-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="f7573-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7573-106">SYNTAX</span></span>

### <span data-ttu-id="f7573-107">Secondes (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f7573-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="f7573-108">Millisecondes</span><span class="sxs-lookup"><span data-stu-id="f7573-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="f7573-109">Description</span><span class="sxs-lookup"><span data-stu-id="f7573-109">DESCRIPTION</span></span>

<span data-ttu-id="f7573-110">L' `Start-Sleep` applet de commande suspend l’activité dans un script ou une session pour la période spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f7573-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="f7573-111">Vous pouvez l'utiliser pour de nombreuses tâches, comme attendre qu'une opération se termine ou soit suspendue avant de répéter une opération.</span><span class="sxs-lookup"><span data-stu-id="f7573-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="f7573-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f7573-112">EXAMPLES</span></span>

### <span data-ttu-id="f7573-113">Exemple 1 : mettre en veille toutes les commandes pendant 15 secondes</span><span class="sxs-lookup"><span data-stu-id="f7573-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="f7573-114">Exemple 2 : mettre en veille toutes les commandes pendant 1,5 secondes</span><span class="sxs-lookup"><span data-stu-id="f7573-114">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="f7573-115">Dans cet exemple, toutes les commandes de la session sont en veille pendant une demi-seconde.</span><span class="sxs-lookup"><span data-stu-id="f7573-115">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="f7573-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7573-116">PARAMETERS</span></span>

### <span data-ttu-id="f7573-117">-Millisecondes</span><span class="sxs-lookup"><span data-stu-id="f7573-117">-Milliseconds</span></span>

<span data-ttu-id="f7573-118">Spécifie la durée pendant laquelle la ressource reste en veille en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="f7573-118">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="f7573-119">Le paramètre peut être abrégé en **m** .</span><span class="sxs-lookup"><span data-stu-id="f7573-119">The parameter can be abbreviated as **m** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f7573-120">-Secondes</span><span class="sxs-lookup"><span data-stu-id="f7573-120">-Seconds</span></span>

<span data-ttu-id="f7573-121">Spécifie la durée pendant laquelle la ressource reste en veille en secondes.</span><span class="sxs-lookup"><span data-stu-id="f7573-121">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="f7573-122">Vous pouvez omettre le nom du paramètre ou vous pouvez l’abréger en tant que **s** .</span><span class="sxs-lookup"><span data-stu-id="f7573-122">You can omit the parameter name or you can abbreviate it as **s** .</span></span> <span data-ttu-id="f7573-123">À compter de PowerShell 6.2.0, ce paramètre accepte à présent des valeurs fractionnaires.</span><span class="sxs-lookup"><span data-stu-id="f7573-123">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f7573-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7573-124">CommonParameters</span></span>

<span data-ttu-id="f7573-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7573-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7573-126">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="f7573-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f7573-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f7573-127">INPUTS</span></span>

### <span data-ttu-id="f7573-128">System.Int32</span><span class="sxs-lookup"><span data-stu-id="f7573-128">System.Int32</span></span>

<span data-ttu-id="f7573-129">Vous pouvez diriger le nombre de secondes jusqu’à `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="f7573-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="f7573-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f7573-130">OUTPUTS</span></span>

### <span data-ttu-id="f7573-131">Aucun</span><span class="sxs-lookup"><span data-stu-id="f7573-131">None</span></span>

<span data-ttu-id="f7573-132">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="f7573-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f7573-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f7573-133">NOTES</span></span>

- <span data-ttu-id="f7573-134">Vous pouvez également faire référence à `Start-Sleep` par son alias intégré, `sleep` .</span><span class="sxs-lookup"><span data-stu-id="f7573-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="f7573-135">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="f7573-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="f7573-136">`Ctrl+C` s’arrête sur `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="f7573-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="f7573-137">`Ctrl+C` ne s’arrête pas `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="f7573-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="f7573-138">Pour plus d’informations, consultez [méthode Thread. Sleep](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="f7573-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="f7573-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f7573-139">RELATED LINKS</span></span>

