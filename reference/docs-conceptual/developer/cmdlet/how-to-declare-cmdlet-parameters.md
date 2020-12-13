---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour déclarer des paramètres d’applet de commande
description: Guide pratique pour déclarer des paramètres d’applet de commande
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667094"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="e1e7a-103">Guide pratique pour déclarer des paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e1e7a-103">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="e1e7a-104">Ces exemples montrent comment déclarer des paramètres nommés, positionnels, obligatoires, facultatifs et de commutateur.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-104">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="e1e7a-105">Ces exemples montrent également comment définir un alias de paramètre.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-105">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="e1e7a-106">Comment déclarer un paramètre nommé</span><span class="sxs-lookup"><span data-stu-id="e1e7a-106">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="e1e7a-107">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-107">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e1e7a-108">Lorsque vous ajoutez l’attribut de paramètre, omettez le `Position` mot clé de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-108">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e1e7a-109">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e1e7a-109">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="e1e7a-110">Comment déclarer un paramètre positionnel</span><span class="sxs-lookup"><span data-stu-id="e1e7a-110">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="e1e7a-111">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-111">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e1e7a-112">Lorsque vous ajoutez l’attribut de paramètre, définissez le `Position` mot clé sur la position de l’argument.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-112">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="e1e7a-113">La valeur 0 indique la première position.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-113">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e1e7a-114">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e1e7a-114">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="e1e7a-115">Comment déclarer un paramètre obligatoire</span><span class="sxs-lookup"><span data-stu-id="e1e7a-115">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="e1e7a-116">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-116">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e1e7a-117">Lorsque vous ajoutez l’attribut de paramètre, affectez au `Mandatory` mot clé la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="e1e7a-117">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e1e7a-118">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e1e7a-118">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="e1e7a-119">Comment déclarer un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="e1e7a-119">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="e1e7a-120">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-120">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e1e7a-121">Lorsque vous ajoutez l’attribut de paramètre, omettez le `Mandatory` mot clé.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-121">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="e1e7a-122">Comment déclarer un paramètre de commutateur</span><span class="sxs-lookup"><span data-stu-id="e1e7a-122">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="e1e7a-123">Définissez une propriété publique en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter), puis déclarez l’attribut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-123">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="e1e7a-124">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e1e7a-124">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="e1e7a-125">Comment déclarer un paramètre avec des alias</span><span class="sxs-lookup"><span data-stu-id="e1e7a-125">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="e1e7a-126">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-126">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e1e7a-127">Ajoutez un attribut alias qui répertorie les alias pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-127">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="e1e7a-128">Dans cet exemple, trois alias sont définis pour le même paramètre.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-128">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="e1e7a-129">Le premier alias fournit un raccourci.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-129">The first alias provides a shortcut.</span></span> <span data-ttu-id="e1e7a-130">Le deuxième et le troisième alias fournissent des noms que vous pouvez utiliser pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="e1e7a-130">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e1e7a-131">Pour plus d’informations sur l’attribut alias, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e1e7a-131">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1e7a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1e7a-132">See Also</span></span>

[<span data-ttu-id="e1e7a-133">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e1e7a-133">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="e1e7a-134">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="e1e7a-134">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="e1e7a-135">Déclaration de l’attribut Alias</span><span class="sxs-lookup"><span data-stu-id="e1e7a-135">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="e1e7a-136">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1e7a-136">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
