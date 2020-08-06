---
title: Comment déclarer des paramètres d’applet de commande | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 97e86a1eb715f149a8383a1a4529c00da4f0eba8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774386"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="9aeda-102">Guide pratique pour déclarer des paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="9aeda-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="9aeda-103">Ces exemples montrent comment déclarer des paramètres nommés, positionnels, obligatoires, facultatifs et de commutateur.</span><span class="sxs-lookup"><span data-stu-id="9aeda-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="9aeda-104">Ces exemples montrent également comment définir un alias de paramètre.</span><span class="sxs-lookup"><span data-stu-id="9aeda-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="9aeda-105">Comment déclarer un paramètre nommé</span><span class="sxs-lookup"><span data-stu-id="9aeda-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="9aeda-106">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9aeda-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="9aeda-107">Lorsque vous ajoutez l’attribut de paramètre, omettez le `Position` mot clé de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="9aeda-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="9aeda-108">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9aeda-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="9aeda-109">Comment déclarer un paramètre positionnel</span><span class="sxs-lookup"><span data-stu-id="9aeda-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="9aeda-110">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9aeda-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="9aeda-111">Lorsque vous ajoutez l’attribut de paramètre, définissez le `Position` mot clé sur la position de l’argument.</span><span class="sxs-lookup"><span data-stu-id="9aeda-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="9aeda-112">La valeur 0 indique la première position.</span><span class="sxs-lookup"><span data-stu-id="9aeda-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="9aeda-113">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9aeda-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="9aeda-114">Comment déclarer un paramètre obligatoire</span><span class="sxs-lookup"><span data-stu-id="9aeda-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="9aeda-115">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9aeda-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="9aeda-116">Lorsque vous ajoutez l’attribut de paramètre, affectez au `Mandatory` mot clé la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="9aeda-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="9aeda-117">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9aeda-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="9aeda-118">Comment déclarer un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="9aeda-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="9aeda-119">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9aeda-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="9aeda-120">Lorsque vous ajoutez l’attribut de paramètre, omettez le `Mandatory` mot clé.</span><span class="sxs-lookup"><span data-stu-id="9aeda-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="9aeda-121">Comment déclarer un paramètre de commutateur</span><span class="sxs-lookup"><span data-stu-id="9aeda-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="9aeda-122">Définissez une propriété publique en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter), puis déclarez l’attribut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="9aeda-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="9aeda-123">Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9aeda-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="9aeda-124">Comment déclarer un paramètre avec des alias</span><span class="sxs-lookup"><span data-stu-id="9aeda-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="9aeda-125">Définissez une propriété publique comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9aeda-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="9aeda-126">Ajoutez un attribut alias qui répertorie les alias pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="9aeda-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="9aeda-127">Dans cet exemple, trois alias sont définis pour le même paramètre.</span><span class="sxs-lookup"><span data-stu-id="9aeda-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="9aeda-128">Le premier alias fournit un raccourci.</span><span class="sxs-lookup"><span data-stu-id="9aeda-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="9aeda-129">Le deuxième et le troisième alias fournissent des noms que vous pouvez utiliser pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="9aeda-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="9aeda-130">Pour plus d’informations sur l’attribut alias, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9aeda-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9aeda-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aeda-131">See Also</span></span>

[<span data-ttu-id="9aeda-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9aeda-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="9aeda-133">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="9aeda-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="9aeda-134">Déclaration de l’attribut Alias</span><span class="sxs-lookup"><span data-stu-id="9aeda-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="9aeda-135">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9aeda-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
