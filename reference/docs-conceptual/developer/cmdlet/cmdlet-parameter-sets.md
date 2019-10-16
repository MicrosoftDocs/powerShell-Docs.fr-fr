---
title: Jeux de paramètres d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365898"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="cb326-102">Ensembles de paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="cb326-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="cb326-103">PowerShell utilise des jeux de paramètres pour vous permettre d’écrire une applet de commande unique qui peut effectuer différentes actions pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="cb326-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="cb326-104">Les jeux de paramètres vous permettent d’exposer des paramètres différents à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cb326-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="cb326-105">Et pour retourner des informations différentes en fonction des paramètres spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cb326-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="cb326-106">Exemples de jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="cb326-106">Examples of parameter sets</span></span>

<span data-ttu-id="cb326-107">Par exemple, l’applet de commande PowerShell `Get-EventLog` retourne des informations différentes selon que l’utilisateur spécifie le paramètre **List** ou **logname** .</span><span class="sxs-lookup"><span data-stu-id="cb326-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="cb326-108">Si le paramètre **List** est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux, mais pas sur les informations d’événement qu’elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="cb326-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="cb326-109">Si le paramètre **logname** est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements spécifique.</span><span class="sxs-lookup"><span data-stu-id="cb326-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="cb326-110">Les paramètres **List** et **logname** identifient deux jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="cb326-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="cb326-111">Paramètre unique</span><span class="sxs-lookup"><span data-stu-id="cb326-111">Unique parameter</span></span>

<span data-ttu-id="cb326-112">Chaque jeu de paramètres doit avoir un paramètre unique que le runtime PowerShell utilise pour exposer le jeu de paramètres approprié.</span><span class="sxs-lookup"><span data-stu-id="cb326-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="cb326-113">Si possible, le paramètre unique doit être un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cb326-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="cb326-114">Lorsqu’un paramètre est obligatoire, l’utilisateur doit spécifier le paramètre, et le runtime PowerShell utilise ce paramètre pour identifier le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="cb326-115">Le paramètre unique ne peut pas être obligatoire si votre applet de commande est conçue pour s’exécuter sans spécifier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="cb326-116">Jeux de paramètres multiples</span><span class="sxs-lookup"><span data-stu-id="cb326-116">Multiple parameter sets</span></span>

<span data-ttu-id="cb326-117">Dans l’illustration suivante, la colonne de gauche affiche trois jeux de paramètres valides.</span><span class="sxs-lookup"><span data-stu-id="cb326-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="cb326-118">Le **paramètre a** est unique pour le premier jeu de paramètres, le **paramètre B** est unique pour le deuxième jeu de paramètres, et le **paramètre C** est unique pour le troisième jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="cb326-119">Dans la colonne de droite, les jeux de paramètres n’ont pas de paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="cb326-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="cb326-121">Spécifications du jeu de paramètres</span><span class="sxs-lookup"><span data-stu-id="cb326-121">Parameter set requirements</span></span>

<span data-ttu-id="cb326-122">Les exigences suivantes s’appliquent à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="cb326-123">Chaque jeu de paramètres doit avoir au moins un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="cb326-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="cb326-124">Si possible, définissez ce paramètre sur un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cb326-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="cb326-125">Un jeu de paramètres qui contient plusieurs paramètres positionnels doit définir des positions uniques pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="cb326-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="cb326-126">Deux paramètres positionnels ne peuvent pas spécifier la même position.</span><span class="sxs-lookup"><span data-stu-id="cb326-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="cb326-127">Un seul paramètre d’un ensemble peut déclarer le mot clé `ValueFromPipeline` avec une valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="cb326-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="cb326-128">Plusieurs paramètres peuvent définir le mot clé `ValueFromPipelineByPropertyName` avec une valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="cb326-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="cb326-129">Si aucun jeu de paramètres n’est spécifié pour un paramètre, le paramètre appartient à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="cb326-130">Pour une applet de commande ou une fonction, il existe une limite de 32 jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="cb326-131">Jeux de paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="cb326-131">Default parameter sets</span></span>

<span data-ttu-id="cb326-132">Lorsque plusieurs jeux de paramètres sont définis, vous pouvez utiliser le mot clé `DefaultParameterSetName` de l’attribut d' **applet** de commande pour spécifier le jeu de paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="cb326-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="cb326-133">PowerShell utilise le jeu de paramètres par défaut s’il ne peut pas déterminer le jeu de paramètres à utiliser en fonction des informations fournies par la commande.</span><span class="sxs-lookup"><span data-stu-id="cb326-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="cb326-134">Pour plus d’informations sur l’attribut d' **applet** de commande, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="cb326-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="cb326-135">Déclarer des jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="cb326-135">Declaring parameter sets</span></span>

<span data-ttu-id="cb326-136">Pour créer un jeu de paramètres, vous devez spécifier le mot clé `ParameterSetName` lorsque vous déclarez l’attribut de **paramètre** pour chaque paramètre dans le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="cb326-137">Pour les paramètres appartenant à plusieurs jeux de paramètres, ajoutez un attribut de **paramètre** pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="cb326-138">Cet attribut vous permet de définir différemment le paramètre pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb326-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="cb326-139">Par exemple, vous pouvez définir un paramètre comme obligatoire dans un jeu et facultatif dans un autre.</span><span class="sxs-lookup"><span data-stu-id="cb326-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="cb326-140">Toutefois, chaque jeu de paramètres doit contenir un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="cb326-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="cb326-141">Pour plus d’informations, consultez [déclaration d’attribut de paramètre](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cb326-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="cb326-142">Dans l’exemple suivant, le paramètre **username** est le paramètre unique du jeu de paramètres `Test01`, et le paramètre **ComputerName** est le paramètre unique du jeu de paramètres `Test02`.</span><span class="sxs-lookup"><span data-stu-id="cb326-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="cb326-143">Le paramètre **SharedParam** appartient aux deux jeux et est obligatoire pour le jeu de paramètres `Test01`, mais facultatif pour le jeu de paramètres `Test02`.</span><span class="sxs-lookup"><span data-stu-id="cb326-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
