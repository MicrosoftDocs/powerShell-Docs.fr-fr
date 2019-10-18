---
title: Alias de paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369588"
---
# <a name="parameter-aliases"></a><span data-ttu-id="a3003-102">Alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="a3003-102">Parameter Aliases</span></span>

<span data-ttu-id="a3003-103">Les paramètres d’applet de commande peuvent également avoir des alias.</span><span class="sxs-lookup"><span data-stu-id="a3003-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="a3003-104">Vous pouvez utiliser les alias à la place des noms de paramètres lorsque vous tapez ou spécifiez le paramètre dans une commande.</span><span class="sxs-lookup"><span data-stu-id="a3003-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="a3003-105">Avantages de l’utilisation d’alias</span><span class="sxs-lookup"><span data-stu-id="a3003-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="a3003-106">L’ajout d’alias aux paramètres offre les avantages suivants.</span><span class="sxs-lookup"><span data-stu-id="a3003-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="a3003-107">Vous pouvez fournir un raccourci pour que l’utilisateur n’ait pas à utiliser le nom de paramètre complet lorsque l’applet de commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="a3003-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="a3003-108">Par exemple, vous pouvez utiliser l’alias « CN » à la place du nom de paramètre « ComputerName ».</span><span class="sxs-lookup"><span data-stu-id="a3003-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="a3003-109">Vous pouvez définir plusieurs alias si vous souhaitez fournir des noms différents pour le même paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3003-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="a3003-110">Vous pouvez définir plusieurs alias si vous devez utiliser plusieurs groupes d’utilisateurs qui font référence aux mêmes données de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="a3003-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="a3003-111">Vous pouvez fournir une compatibilité descendante pour les scripts existants si le nom d’un paramètre change.</span><span class="sxs-lookup"><span data-stu-id="a3003-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="a3003-112">En utilisant l’attribut alias avec l’attribut ValueFromPipelineByName, vous pouvez définir un paramètre qui permet à votre applet de commande de créer une liaison avec différents types d’objets.</span><span class="sxs-lookup"><span data-stu-id="a3003-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="a3003-113">Par exemple, imaginons que vous disposiez de deux objets de types différents et que le premier objet comportait une propriété Writer et que le deuxième objet contenait une propriété Editor.</span><span class="sxs-lookup"><span data-stu-id="a3003-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="a3003-114">Si votre applet de commande avait un paramètre qui avait des alias de Writer et d’éditeur et que l’applet de commande acceptait l’entrée de pipeline en fonction des noms de propriété, votre applet de commande pourrait lier les deux objets à l’aide des deux alias de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a3003-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="a3003-115">Pour plus d’informations sur les alias qui peuvent être utilisés avec des paramètres spécifiques, consultez [noms de paramètres communs](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="a3003-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="a3003-116">Définition des alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="a3003-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="a3003-117">Pour définir un alias pour un paramètre, déclarez l’attribut alias, comme indiqué dans la déclaration de paramètre suivante.</span><span class="sxs-lookup"><span data-stu-id="a3003-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="a3003-118">Dans cet exemple, plusieurs alias sont définis pour le même paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3003-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="a3003-119">(Pour plus d’informations, consultez[comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md)commande.)</span><span class="sxs-lookup"><span data-stu-id="a3003-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3003-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3003-120">See Also</span></span>

[<span data-ttu-id="a3003-121">Noms de paramètres communs</span><span class="sxs-lookup"><span data-stu-id="a3003-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="a3003-122">Comment déclarer des paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="a3003-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="a3003-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3003-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)