---
title: Comment déclarer des paramètres d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365678"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="e7801-102">Guide pratique pour déclarer des paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e7801-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="e7801-103">Ces exemples montrent comment déclarer des paramètres nommés, positionnels, obligatoires, facultatifs et de commutateur.</span><span class="sxs-lookup"><span data-stu-id="e7801-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="e7801-104">Ces exemples montrent également comment définir un alias de paramètre.</span><span class="sxs-lookup"><span data-stu-id="e7801-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="e7801-105">Comment déclarer un paramètre nommé</span><span class="sxs-lookup"><span data-stu-id="e7801-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="e7801-106">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7801-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7801-107">Lorsque vous ajoutez l’attribut de paramètre, omettez le mot clé `Position` de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="e7801-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e7801-108">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e7801-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="e7801-109">Comment déclarer un paramètre positionnel</span><span class="sxs-lookup"><span data-stu-id="e7801-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="e7801-110">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7801-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7801-111">Lorsque vous ajoutez l’attribut de paramètre, définissez le mot clé `Position` à la position de l’argument.</span><span class="sxs-lookup"><span data-stu-id="e7801-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="e7801-112">La valeur 0 indique la première position.</span><span class="sxs-lookup"><span data-stu-id="e7801-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e7801-113">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e7801-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="e7801-114">Comment déclarer un paramètre obligatoire</span><span class="sxs-lookup"><span data-stu-id="e7801-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="e7801-115">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7801-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7801-116">Lorsque vous ajoutez l’attribut de paramètre, définissez le mot clé `Mandatory` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="e7801-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e7801-117">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e7801-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="e7801-118">Comment déclarer un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="e7801-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="e7801-119">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7801-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7801-120">Lorsque vous ajoutez l’attribut de paramètre, omettez le mot clé `Mandatory`.</span><span class="sxs-lookup"><span data-stu-id="e7801-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="e7801-121">Comment déclarer un paramètre de commutateur</span><span class="sxs-lookup"><span data-stu-id="e7801-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="e7801-122">Définissez une propriété publique en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter), puis déclarez l’attribut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="e7801-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="e7801-123">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e7801-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="e7801-124">Comment déclarer un paramètre avec des alias</span><span class="sxs-lookup"><span data-stu-id="e7801-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="e7801-125">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7801-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7801-126">Ajoutez un attribut alias qui répertorie les alias pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e7801-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="e7801-127">Dans cet exemple, trois alias sont définis pour le même paramètre.</span><span class="sxs-lookup"><span data-stu-id="e7801-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="e7801-128">Le premier alias fournit un raccourci.</span><span class="sxs-lookup"><span data-stu-id="e7801-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="e7801-129">Le deuxième et le troisième alias fournissent des noms que vous pouvez utiliser pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="e7801-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="e7801-130">Pour plus d’informations sur l’attribut alias, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e7801-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7801-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7801-131">See Also</span></span>

[<span data-ttu-id="e7801-132">System. Management. Automation. Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="e7801-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="e7801-133">Déclaration d’attribut de paramètre</span><span class="sxs-lookup"><span data-stu-id="e7801-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="e7801-134">Déclaration d’attribut d’alias</span><span class="sxs-lookup"><span data-stu-id="e7801-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="e7801-135">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7801-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
