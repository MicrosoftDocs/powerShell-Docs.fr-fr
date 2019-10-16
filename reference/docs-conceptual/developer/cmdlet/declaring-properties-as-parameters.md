---
title: Déclaration des propriétés en tant que paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365748"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="940d1-102">Déclaration des propriétés en tant que paramètres</span><span class="sxs-lookup"><span data-stu-id="940d1-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="940d1-103">Cette rubrique fournit des informations de base que vous devez comprendre avant de déclarer les paramètres d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="940d1-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="940d1-104">Pour déclarer les paramètres d’une applet de commande dans votre classe d’applet de commande, définissez les propriétés publiques qui représentent chaque paramètre, puis ajoutez un ou plusieurs attributs de paramètre à chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="940d1-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="940d1-105">Le runtime Windows PowerShell utilise les attributs de paramètre pour identifier la propriété en tant que paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="940d1-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="940d1-106">La syntaxe de base pour déclarer l’attribut de paramètre est `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="940d1-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="940d1-107">Voici un exemple de propriété définie en tant que paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="940d1-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="940d1-108">Voici quelques points à retenir sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="940d1-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="940d1-109">Un paramètre doit être explicitement marqué comme public.</span><span class="sxs-lookup"><span data-stu-id="940d1-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="940d1-110">Les paramètres qui ne sont pas marqués comme étant par défaut publics comme internes et ne seront pas trouvés par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="940d1-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="940d1-111">Les paramètres doivent être définis en tant que types Microsoft .NET Framework pour fournir une meilleure validation des paramètres.</span><span class="sxs-lookup"><span data-stu-id="940d1-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="940d1-112">Par exemple, les paramètres qui sont limités à une valeur d’un ensemble de valeurs doivent être définis en tant que type énumération.</span><span class="sxs-lookup"><span data-stu-id="940d1-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="940d1-113">Les paramètres qui acceptent une valeur Uniform Resource Identifier (URI) doivent être de type [System. Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="940d1-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="940d1-114">Évitez les paramètres de chaîne de base pour toutes les propriétés de texte de forme libre.</span><span class="sxs-lookup"><span data-stu-id="940d1-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="940d1-115">Vous pouvez ajouter un paramètre à un nombre quelconque de jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="940d1-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="940d1-116">Pour plus d’informations sur les jeux de paramètres, consultez [jeux de paramètres d’applet](./cmdlet-parameter-sets.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="940d1-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="940d1-117">Windows PowerShell fournit également un ensemble de paramètres communs qui sont automatiquement disponibles pour chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="940d1-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="940d1-118">Pour plus d’informations sur ces paramètres et leurs alias, consultez [paramètres communs des applets](./common-parameter-names.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="940d1-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="940d1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="940d1-119">See Also</span></span>

[<span data-ttu-id="940d1-120">Paramètres communs de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="940d1-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="940d1-121">Types de paramètre d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="940d1-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="940d1-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="940d1-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
