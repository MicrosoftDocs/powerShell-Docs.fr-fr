---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203430"
---
# <span data-ttu-id="bb75f-103">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="bb75f-103">Get-OperationValidation</span></span>

## <span data-ttu-id="bb75f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bb75f-104">SYNOPSIS</span></span>
<span data-ttu-id="bb75f-105">Obtient les tests de l’infrastructure de validation des opérations.</span><span class="sxs-lookup"><span data-stu-id="bb75f-105">Gets Operation Validation Framework tests.</span></span>

## <span data-ttu-id="bb75f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb75f-106">SYNTAX</span></span>

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="bb75f-107">Description</span><span class="sxs-lookup"><span data-stu-id="bb75f-107">DESCRIPTION</span></span>
<span data-ttu-id="bb75f-108">L’applet de commande **obtenir-OperationValidation** obtient les tests de l’infrastructure de validation des opérations pour les modules installés.</span><span class="sxs-lookup"><span data-stu-id="bb75f-108">The **Get-OperationValidation** cmdlet gets Operation Validation Framework tests for installed modules.</span></span>

<span data-ttu-id="bb75f-109">Les modules qui incluent un dossier Diagnostics sont inspectés pour rechercher les tests pester dans le sous-dossier simple ou complet, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="bb75f-109">Modules that include a Diagnostics folder are inspected for Pester tests in the Simple or Comprehensive subfolder, or both.</span></span>

## <span data-ttu-id="bb75f-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bb75f-110">EXAMPLES</span></span>

### <span data-ttu-id="bb75f-111">Exemple 1 : récupérer les tests de validation de l’opération</span><span class="sxs-lookup"><span data-stu-id="bb75f-111">Example 1: Get Operation Validation tests</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

<span data-ttu-id="bb75f-112">Cette commande obtient les tests de validation à partir du module nommé AddNumbers dans le dossier C:\temp\modules.</span><span class="sxs-lookup"><span data-stu-id="bb75f-112">This command gets validation tests from the module named AddNumbers in the C:\temp\modules folder.</span></span>

## <span data-ttu-id="bb75f-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb75f-113">PARAMETERS</span></span>

### <span data-ttu-id="bb75f-114">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="bb75f-114">-ModuleName</span></span>
<span data-ttu-id="bb75f-115">Spécifie un tableau de noms de modules.</span><span class="sxs-lookup"><span data-stu-id="bb75f-115">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb75f-116">-TestType</span><span class="sxs-lookup"><span data-stu-id="bb75f-116">-TestType</span></span>
<span data-ttu-id="bb75f-117">Spécifie un tableau de types de test.</span><span class="sxs-lookup"><span data-stu-id="bb75f-117">Specifies an array of test types.</span></span>
<span data-ttu-id="bb75f-118">Les valeurs valides sont simple, complète ou les deux.</span><span class="sxs-lookup"><span data-stu-id="bb75f-118">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="bb75f-119">La valeur par défaut est « simple, complète ».</span><span class="sxs-lookup"><span data-stu-id="bb75f-119">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb75f-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb75f-120">CommonParameters</span></span>
<span data-ttu-id="bb75f-121">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb75f-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb75f-122">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bb75f-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb75f-123">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bb75f-123">INPUTS</span></span>

### <span data-ttu-id="bb75f-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="bb75f-124">None</span></span>
<span data-ttu-id="bb75f-125">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bb75f-125">You cannot pipe any input to this cmdlet.</span></span>

## <span data-ttu-id="bb75f-126">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bb75f-126">OUTPUTS</span></span>

### <span data-ttu-id="bb75f-127">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="bb75f-127">PSCustomObject</span></span>
<span data-ttu-id="bb75f-128">Le **PSCustomObject** décrit la validation.</span><span class="sxs-lookup"><span data-stu-id="bb75f-128">The **PSCustomObject** describes the validation.</span></span>

## <span data-ttu-id="bb75f-129">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bb75f-129">NOTES</span></span>

## <span data-ttu-id="bb75f-130">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bb75f-130">RELATED LINKS</span></span>

[<span data-ttu-id="bb75f-131">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="bb75f-131">Invoke-OperationValidation</span></span>](Invoke-OperationValidation.md)
