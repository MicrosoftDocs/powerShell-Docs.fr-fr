---
title: Types de paramètres d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369308"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="ad38e-102">Types de paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="ad38e-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="ad38e-103">Cette rubrique décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="ad38e-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="ad38e-104">Les paramètres d’applet de commande peuvent être positionnels, nommés, obligatoires, facultatifs ou commutateurs.</span><span class="sxs-lookup"><span data-stu-id="ad38e-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="ad38e-105">Paramètres positionnels et nommés</span><span class="sxs-lookup"><span data-stu-id="ad38e-105">Positional and Named Parameters</span></span>

<span data-ttu-id="ad38e-106">Tous les paramètres d’applet de commande sont des paramètres nommés ou positionnels.</span><span class="sxs-lookup"><span data-stu-id="ad38e-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="ad38e-107">Pour un paramètre nommé, vous devez taper le nom du paramètre et l’argument lors de l’appel de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad38e-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="ad38e-108">Un paramètre positionnel requiert uniquement que vous tapez les arguments dans l’ordre relatif.</span><span class="sxs-lookup"><span data-stu-id="ad38e-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="ad38e-109">Le système mappe ensuite le premier argument sans nom au premier paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="ad38e-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="ad38e-110">Le système mappe le deuxième argument sans nom au deuxième paramètre sans nom, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ad38e-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="ad38e-111">Par défaut, tous les paramètres d’applet de commande sont des paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="ad38e-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="ad38e-112">Pour définir un paramètre nommé, omettez le mot clé `Position` dans la déclaration d’attribut de **paramètre** , comme indiqué dans la déclaration de paramètre suivante.</span><span class="sxs-lookup"><span data-stu-id="ad38e-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ad38e-113">Pour définir un paramètre positionnel, ajoutez le mot clé `Position` dans la déclaration attribute Parameter, puis spécifiez une position.</span><span class="sxs-lookup"><span data-stu-id="ad38e-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="ad38e-114">Dans l’exemple suivant, le paramètre `UserName` est déclaré en tant que paramètre positionnel avec la position 0.</span><span class="sxs-lookup"><span data-stu-id="ad38e-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="ad38e-115">Cela signifie que le premier argument de l’appel sera automatiquement lié à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="ad38e-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="ad38e-116">Une bonne conception d’applets de commande recommande que les paramètres les plus utilisés soient déclarés en tant que paramètres positionnels afin que l’utilisateur n’ait pas à entrer le nom du paramètre lors de l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad38e-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="ad38e-117">Les paramètres positionnels et nommés acceptent des arguments uniques ou plusieurs arguments séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="ad38e-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="ad38e-118">Plusieurs arguments sont autorisés uniquement si le paramètre accepte une collection telle qu’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="ad38e-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="ad38e-119">Vous pouvez mélanger des paramètres positionnels et nommés dans la même applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad38e-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="ad38e-120">Dans ce cas, le système récupère d’abord les arguments nommés, puis tente de mapper les arguments sans nom restants aux paramètres positionnels.</span><span class="sxs-lookup"><span data-stu-id="ad38e-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="ad38e-121">Les commandes suivantes illustrent les différentes façons dont vous pouvez spécifier des arguments uniques et multiples pour les paramètres de l’applet de commande `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="ad38e-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="ad38e-122">Notez que dans les deux derniers exemples, **-Name** n’a pas besoin d’être spécifié, car le paramètre `Name` est défini en tant que paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="ad38e-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="ad38e-123">Paramètres obligatoires et facultatifs</span><span class="sxs-lookup"><span data-stu-id="ad38e-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="ad38e-124">Vous pouvez également définir des paramètres d’applet de commande en tant que paramètres obligatoires ou facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ad38e-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="ad38e-125">(Un paramètre obligatoire doit être spécifié avant que le runtime Windows PowerShell appelle l’applet de commande.)  Par défaut, les paramètres sont définis comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ad38e-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="ad38e-126">Pour définir un paramètre obligatoire, ajoutez le mot clé `Mandatory` dans la déclaration Attribute de paramètre et affectez-lui la valeur `true`, comme indiqué dans la déclaration de paramètre suivante.</span><span class="sxs-lookup"><span data-stu-id="ad38e-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ad38e-127">Pour définir un paramètre facultatif, omettez le mot clé `Mandatory` dans la déclaration attribute **Parameter** , comme indiqué dans la déclaration de paramètre suivante.</span><span class="sxs-lookup"><span data-stu-id="ad38e-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="ad38e-128">Paramètres de commutateur</span><span class="sxs-lookup"><span data-stu-id="ad38e-128">Switch Parameters</span></span>

<span data-ttu-id="ad38e-129">Windows PowerShell fournit un type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter) qui vous permet de définir un paramètre dont la valeur est automatiquement définie sur `false` si le paramètre n’est pas spécifié lors de l’appel de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad38e-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="ad38e-130">Dans la mesure du possible, utilisez des paramètres de commutateur à la place des paramètres booléens.</span><span class="sxs-lookup"><span data-stu-id="ad38e-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="ad38e-131">Prenons l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ad38e-131">Consider the following sample.</span></span> <span data-ttu-id="ad38e-132">Par défaut, plusieurs applets de commande Windows PowerShell ne transmettent pas un objet de sortie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad38e-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="ad38e-133">Toutefois, ces applets de commande ont un paramètre de commutateur `PassThru` qui remplace le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="ad38e-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="ad38e-134">Si le paramètre `PassThru` est spécifié lors de l’appel de ces applets de commande, l’applet de commande renvoie un objet de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad38e-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="ad38e-135">Si vous avez besoin que le paramètre ait une valeur par défaut de `true` lorsque le paramètre n’est pas spécifié dans l’appel, envisagez d’inverser le sens du paramètre.</span><span class="sxs-lookup"><span data-stu-id="ad38e-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="ad38e-136">Par exemple, au lieu de définir l’attribut de paramètre sur une valeur booléenne de `true`, déclarez la propriété en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter) , puis définissez la valeur par défaut du paramètre sur `false`.</span><span class="sxs-lookup"><span data-stu-id="ad38e-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="ad38e-137">Pour définir un paramètre de commutateur, déclarez la propriété en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter) , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ad38e-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="ad38e-138">Pour que l’applet de commande agisse sur le paramètre quand elle est spécifiée, utilisez la structure suivante dans l’une des méthodes de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ad38e-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="ad38e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad38e-139">See Also</span></span>

[<span data-ttu-id="ad38e-140">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad38e-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
