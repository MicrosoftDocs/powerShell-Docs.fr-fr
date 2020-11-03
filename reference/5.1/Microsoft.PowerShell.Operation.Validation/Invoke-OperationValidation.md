---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/invoke-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-OperationValidation
ms.openlocfilehash: 6c9d4001392de48032a0fe1ba3667db90ea614fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203429"
---
# <span data-ttu-id="e2f9f-103">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="e2f9f-103">Invoke-OperationValidation</span></span>

## <span data-ttu-id="e2f9f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e2f9f-104">SYNOPSIS</span></span>

<span data-ttu-id="e2f9f-105">Appelle les tests de l’infrastructure de validation des opérations.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-105">Invokes Operation Validation Framework tests.</span></span>

## <span data-ttu-id="e2f9f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e2f9f-106">SYNTAX</span></span>

### <span data-ttu-id="e2f9f-107">FileAndTest (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e2f9f-107">FileAndTest (Default)</span></span>

```
Invoke-OperationValidation [-TestInfo <PSObject[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e2f9f-108">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="e2f9f-108">Path</span></span>

```
Invoke-OperationValidation [-testFilePath <String[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e2f9f-109">UseGetOperationTest</span><span class="sxs-lookup"><span data-stu-id="e2f9f-109">UseGetOperationTest</span></span>

```
Invoke-OperationValidation [-ModuleName <String[]>] [-TestType <String[]>] [-IncludePesterOutput] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e2f9f-110">Description</span><span class="sxs-lookup"><span data-stu-id="e2f9f-110">DESCRIPTION</span></span>

<span data-ttu-id="e2f9f-111">L’applet de commande **Invoke-OperationValidation** appelle les tests de l’infrastructure de validation des opérations pour un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-111">The **Invoke-OperationValidation** cmdlet invokes Operation Validation Framework tests for a specified module.</span></span>

## <span data-ttu-id="e2f9f-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e2f9f-112">EXAMPLES</span></span>

### <span data-ttu-id="e2f9f-113">Exemple 1 : appeler un test de validation d’opération</span><span class="sxs-lookup"><span data-stu-id="e2f9f-113">Example 1: Invoke an Operation Validation test</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "OperationValidation" | Invoke-OperationValidation -IncludePesterOutput
Describing Simple Test Suite
 [+] first Operational test 20ms
 [+] second Operational test 19ms
 [+] third Operational test 9ms
Tests completed in 48ms
Passed: 3 Failed: 0 Skipped: 0 Pending: 0
Describing Scenario targeted tests
   Context The RemoteAccess service
    [+] The service is running 37ms
   Context The Firewall Rules
    [+] A rule for TCP port 3389 is enabled 1.19s
    [+] A rule for UDP port 3389 is enabled 11ms
Tests completed in 1.24s
Passed: 3 Failed: 0 Skipped: 0 Pending: 0




   Module: OperationValidation




Result  Name
------- --------
Passed  Simple Test Suite::first Operational test
Passed  Simple Test Suite::second Operational test
Passed  Simple Test Suite::third Operational test
Passed  Scenario targeted tests:The RemoteAccess service:The service is running
Passed  Scenario targeted tests:The Firewall Rules:A rule for TCP port 3389 is enabled
Passed  Scenario targeted tests:The Firewall Rules:A rule for UDP port 3389 is enabled
```

<span data-ttu-id="e2f9f-114">Cette commande obtient le module nommé OperationValidation et utilise l’opérateur de pipeline pour le passer à l’applet de commande **Invoke-OperationValidation** , qui exécute le test.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-114">This command gets the module named OperationValidation, and uses the pipeline operator to pass it to the **Invoke-OperationValidation** cmdlet, which runs the test.</span></span>

## <span data-ttu-id="e2f9f-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e2f9f-115">PARAMETERS</span></span>

### <span data-ttu-id="e2f9f-116">-IncludePesterOutput</span><span class="sxs-lookup"><span data-stu-id="e2f9f-116">-IncludePesterOutput</span></span>

<span data-ttu-id="e2f9f-117">Comprend la sortie de test pester.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-117">Includes Pester test output.</span></span>
<span data-ttu-id="e2f9f-118">La valeur par défaut est $False.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-118">The default is $False.</span></span>

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

### <span data-ttu-id="e2f9f-119">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="e2f9f-119">-ModuleName</span></span>

<span data-ttu-id="e2f9f-120">Spécifie un tableau de noms de modules.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-120">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2f9f-121">-testFilePath</span><span class="sxs-lookup"><span data-stu-id="e2f9f-121">-testFilePath</span></span>

<span data-ttu-id="e2f9f-122">Spécifie le chemin d’accès d’un fichier de test de Framework de validation d’opération.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-122">Specifies the path of an Operation Validation Framework test file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e2f9f-123">-TestInfo</span><span class="sxs-lookup"><span data-stu-id="e2f9f-123">-TestInfo</span></span>

<span data-ttu-id="e2f9f-124">Spécifie un objet personnalisé qui spécifie le chemin d’accès au fichier et le nom du test à exécuter.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-124">Specifies a custom object that specifies the path to the file and the name of the test to run.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: FileAndTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e2f9f-125">-TestType</span><span class="sxs-lookup"><span data-stu-id="e2f9f-125">-TestType</span></span>

<span data-ttu-id="e2f9f-126">Spécifie un tableau de types de test.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-126">Specifies an array of test types.</span></span>
<span data-ttu-id="e2f9f-127">Les valeurs valides sont simple, complète ou les deux.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-127">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="e2f9f-128">La valeur par défaut est « simple, complète ».</span><span class="sxs-lookup"><span data-stu-id="e2f9f-128">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2f9f-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e2f9f-129">-Confirm</span></span>

<span data-ttu-id="e2f9f-130">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-130">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2f9f-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e2f9f-131">-WhatIf</span></span>

<span data-ttu-id="e2f9f-132">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e2f9f-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-133">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2f9f-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e2f9f-134">CommonParameters</span></span>
<span data-ttu-id="e2f9f-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e2f9f-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e2f9f-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e2f9f-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e2f9f-137">INPUTS</span></span>

### <span data-ttu-id="e2f9f-138">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="e2f9f-138">PSCustomObject</span></span>

<span data-ttu-id="e2f9f-139">Vous pouvez diriger la sortie de la commande **OperationValidation** vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-139">You can pipe the output of **Get-OperationValidation** to this cmdlet.</span></span>

## <span data-ttu-id="e2f9f-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e2f9f-140">OUTPUTS</span></span>

### <span data-ttu-id="e2f9f-141">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="e2f9f-141">PSCustomObject</span></span>

<span data-ttu-id="e2f9f-142">Le **PSCustomObject** décrit si la validation a réussi.</span><span class="sxs-lookup"><span data-stu-id="e2f9f-142">The **PSCustomObject** describes whether the validation was successful.</span></span>

## <span data-ttu-id="e2f9f-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e2f9f-143">NOTES</span></span>

## <span data-ttu-id="e2f9f-144">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e2f9f-144">RELATED LINKS</span></span>

[<span data-ttu-id="e2f9f-145">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="e2f9f-145">Get-OperationValidation</span></span>](Get-OperationValidation.md)
