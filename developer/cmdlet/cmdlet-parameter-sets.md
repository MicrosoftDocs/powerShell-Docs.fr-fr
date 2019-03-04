---
title: Jeux de paramètres de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857265"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="29cb5-102">Jeux de paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="29cb5-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="29cb5-103">Windows PowerShell utilise des jeux de paramètres pour vous permettre d’écrire une seule applet de commande qui peut effectuer des actions différentes pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="29cb5-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="29cb5-104">Jeux de paramètres permettent d’exposer des paramètres différents pour l’utilisateur et pour retourner des informations différentes en fonction des paramètres spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="29cb5-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="29cb5-105">Exemples de jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="29cb5-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="29cb5-106">Par exemple, le `Get-EventLog` applet de commande (fourni par Windows PowerShell) renvoie des informations différentes selon que l’utilisateur spécifie le `List` ou `LogName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="29cb5-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="29cb5-107">Si le `List` paramètre est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux eux-mêmes, mais pas les informations d’événements qu’ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="29cb5-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="29cb5-108">Si le `LogName` paramètre est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements spécifique.</span><span class="sxs-lookup"><span data-stu-id="29cb5-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="29cb5-109">Le `List` et `LogName` paramètres identifient deux jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="29cb5-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="29cb5-110">Paramètre unique</span><span class="sxs-lookup"><span data-stu-id="29cb5-110">Unique Parameter</span></span>

<span data-ttu-id="29cb5-111">Chaque jeu de paramètres doit avoir un paramètre unique que le runtime Windows PowerShell peut utiliser pour exposer le jeu de paramètres approprié.</span><span class="sxs-lookup"><span data-stu-id="29cb5-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="29cb5-112">Si possible, le paramètre unique doit être un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="29cb5-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="29cb5-113">Lorsqu’un paramètre est obligatoire, l’utilisateur est obligé de spécifier le paramètre, et le runtime de Windows PowerShell peut utiliser ce paramètre pour identifier le paramètre défini à utiliser.</span><span class="sxs-lookup"><span data-stu-id="29cb5-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="29cb5-114">Le paramètre unique ne peut pas être obligatoire si votre applet de commande est conçue pour être exécutée sans spécifier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="29cb5-115">Plusieurs jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="29cb5-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="29cb5-116">Dans l’illustration suivante, la colonne de gauche montre trois jeux de paramètres valide.</span><span class="sxs-lookup"><span data-stu-id="29cb5-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="29cb5-117">Le paramètre A est unique pour le premier jeu de paramètres, paramètre B est unique pour le deuxième jeu de paramètres, et paramètre C est unique pour le troisième jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="29cb5-118">Toutefois, dans la colonne de droite, les jeux de paramètres n’ont pas d’un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="29cb5-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="29cb5-120">Jeu de paramètres requis</span><span class="sxs-lookup"><span data-stu-id="29cb5-120">Parameter Set Requirements</span></span>

<span data-ttu-id="29cb5-121">Les conditions suivantes s’appliquent à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="29cb5-122">Chaque jeu de paramètres doit avoir au moins un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="29cb5-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="29cb5-123">Si possible, vérifiez ce paramètre pour un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="29cb5-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="29cb5-124">Un jeu de paramètres qui contient plusieurs paramètres positionnels doit définir des positions uniques pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="29cb5-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="29cb5-125">Aucun deux paramètres positionnels ne peuvent spécifier la même position.</span><span class="sxs-lookup"><span data-stu-id="29cb5-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="29cb5-126">Qu’un seul paramètre dans un jeu peut déclarer la `ValueFromPipeline` mot clé avec la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="29cb5-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="29cb5-127">Plusieurs paramètres peuvent définir le `ValueFromPipelineByPropertyName` mot clé avec la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="29cb5-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="29cb5-128">Si aucun jeu de paramètres n’est spécifié pour un paramètre, le paramètre appartient à tous les jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="29cb5-129">Jeux de paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="29cb5-129">Default Parameter Sets</span></span>

<span data-ttu-id="29cb5-130">Lorsque plusieurs jeux de paramètres est définis, vous pouvez utiliser le `DefaultParameterSetName` mot clé de l’attribut de l’applet de commande pour spécifier le jeu de paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="29cb5-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="29cb5-131">Windows PowerShell utilise le paramètre par défaut défini s’il ne peut pas déterminer le paramètre défini pour utiliser basé sur les informations fournies par la commande.</span><span class="sxs-lookup"><span data-stu-id="29cb5-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="29cb5-132">Pour plus d’informations sur l’attribut de l’applet de commande, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="29cb5-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="29cb5-133">Déclarer des jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="29cb5-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="29cb5-134">Pour créer un jeu de paramètres, vous devez spécifier le `ParameterSetName` mot clé lorsque vous déclarez l’attribut de paramètre pour chaque paramètre dans le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="29cb5-135">Pour les paramètres qui appartiennent à plusieurs jeux de paramètres, ajoutez un attribut de paramètre pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="29cb5-136">Cela vous permet de définir le paramètre différemment pour chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="29cb5-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="29cb5-137">Par exemple, vous pouvez définir un paramètre comme obligatoires dans un jeu et facultatifs dans une autre.</span><span class="sxs-lookup"><span data-stu-id="29cb5-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="29cb5-138">Toutefois, chaque jeu de paramètres doit contenir un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="29cb5-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="29cb5-139">Dans l’exemple suivant, le `UserName` paramètre est le paramètre unique de l’ensemble de paramètres Test01 et le `ComputerName` paramètre est le paramètre unique de l’ensemble de paramètres Test02.</span><span class="sxs-lookup"><span data-stu-id="29cb5-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="29cb5-140">Le `SharedParam` appartient aux deux ensembles de paramètre et est obligatoire pour le paramètre de Test01 défini mais facultatif pour le jeu de paramètres Test02.</span><span class="sxs-lookup"><span data-stu-id="29cb5-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

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
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```