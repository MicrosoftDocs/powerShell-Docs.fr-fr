---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4d06fdd1d5a616c24a4dd7bec10ea4dadea4062
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598997"
---
# <span data-ttu-id="72695-102">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="72695-102">Start-Sleep</span></span>

## <span data-ttu-id="72695-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="72695-103">SYNOPSIS</span></span>
<span data-ttu-id="72695-104">Interrompt l'activité dans un script ou une session pour la période spécifiée.</span><span class="sxs-lookup"><span data-stu-id="72695-104">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="72695-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="72695-105">SYNTAX</span></span>

### <span data-ttu-id="72695-106">Secondes (par défaut)</span><span class="sxs-lookup"><span data-stu-id="72695-106">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="72695-107">Millisecondes</span><span class="sxs-lookup"><span data-stu-id="72695-107">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="72695-108">Description</span><span class="sxs-lookup"><span data-stu-id="72695-108">DESCRIPTION</span></span>

<span data-ttu-id="72695-109">L' `Start-Sleep` applet de commande suspend l’activité dans un script ou une session pour la période spécifiée.</span><span class="sxs-lookup"><span data-stu-id="72695-109">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="72695-110">Vous pouvez l'utiliser pour de nombreuses tâches, comme attendre qu'une opération se termine ou soit suspendue avant de répéter une opération.</span><span class="sxs-lookup"><span data-stu-id="72695-110">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="72695-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="72695-111">EXAMPLES</span></span>

### <span data-ttu-id="72695-112">Exemple 1 : mettre en veille toutes les commandes pendant 15 secondes</span><span class="sxs-lookup"><span data-stu-id="72695-112">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="72695-113">Exemple 2 : mettre en veille toutes les commandes pendant 1,5 secondes</span><span class="sxs-lookup"><span data-stu-id="72695-113">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="72695-114">Dans cet exemple, toutes les commandes de la session sont en veille pendant une demi-seconde.</span><span class="sxs-lookup"><span data-stu-id="72695-114">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="72695-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72695-115">PARAMETERS</span></span>

### <span data-ttu-id="72695-116">-Millisecondes</span><span class="sxs-lookup"><span data-stu-id="72695-116">-Milliseconds</span></span>

<span data-ttu-id="72695-117">Spécifie la durée pendant laquelle la ressource reste en veille en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="72695-117">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="72695-118">Le paramètre peut être abrégé en **m**.</span><span class="sxs-lookup"><span data-stu-id="72695-118">The parameter can be abbreviated as **m**.</span></span>

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

### <span data-ttu-id="72695-119">-Secondes</span><span class="sxs-lookup"><span data-stu-id="72695-119">-Seconds</span></span>

<span data-ttu-id="72695-120">Spécifie la durée pendant laquelle la ressource reste en veille en secondes.</span><span class="sxs-lookup"><span data-stu-id="72695-120">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="72695-121">Vous pouvez omettre le nom du paramètre ou vous pouvez l’abréger en tant que **s**.</span><span class="sxs-lookup"><span data-stu-id="72695-121">You can omit the parameter name or you can abbreviate it as **s**.</span></span> <span data-ttu-id="72695-122">À compter de PowerShell 6.2.0, ce paramètre accepte à présent des valeurs fractionnaires.</span><span class="sxs-lookup"><span data-stu-id="72695-122">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

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

### <span data-ttu-id="72695-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72695-123">CommonParameters</span></span>

<span data-ttu-id="72695-124">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72695-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72695-125">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="72695-125">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="72695-126">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="72695-126">INPUTS</span></span>

### <span data-ttu-id="72695-127">System.Int32</span><span class="sxs-lookup"><span data-stu-id="72695-127">System.Int32</span></span>

<span data-ttu-id="72695-128">Vous pouvez diriger le nombre de secondes jusqu’à `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="72695-128">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="72695-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="72695-129">OUTPUTS</span></span>

### <span data-ttu-id="72695-130">None</span><span class="sxs-lookup"><span data-stu-id="72695-130">None</span></span>

<span data-ttu-id="72695-131">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="72695-131">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="72695-132">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="72695-132">NOTES</span></span>

- <span data-ttu-id="72695-133">Vous pouvez également faire référence à `Start-Sleep` par son alias intégré, `sleep` .</span><span class="sxs-lookup"><span data-stu-id="72695-133">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="72695-134">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="72695-134">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="72695-135">`Ctrl+C` s’arrête sur `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="72695-135">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="72695-136">`Ctrl+C` ne s’arrête pas `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="72695-136">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="72695-137">Pour plus d’informations, consultez [méthode Thread. Sleep](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="72695-137">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="72695-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="72695-138">RELATED LINKS</span></span>

