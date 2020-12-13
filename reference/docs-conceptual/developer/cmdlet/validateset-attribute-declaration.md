---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidateSet
description: Déclaration de l’attribut ValidateSet
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660468"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="ed000-103">Déclaration de l’attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="ed000-103">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="ed000-104">L’attribut ValidateSetAttribute spécifie un ensemble de valeurs possibles pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ed000-104">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="ed000-105">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed000-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="ed000-106">Lorsque cet attribut est spécifié, le runtime Windows PowerShell détermine si l’argument fourni pour le paramètre d’applet de commande correspond à un élément dans l’ensemble d’éléments fourni.</span><span class="sxs-lookup"><span data-stu-id="ed000-106">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="ed000-107">L’applet de commande est exécutée uniquement si l’argument de paramètre correspond à un élément du jeu.</span><span class="sxs-lookup"><span data-stu-id="ed000-107">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="ed000-108">Si aucune correspondance n’est trouvée, une erreur est générée par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed000-108">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed000-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed000-109">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="ed000-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed000-110">Parameters</span></span>

<span data-ttu-id="ed000-111">`ValidValues` ([System. String](/dotnet/api/System.String)) requis.</span><span class="sxs-lookup"><span data-stu-id="ed000-111">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="ed000-112">Spécifie les valeurs d’élément de paramètre valides.</span><span class="sxs-lookup"><span data-stu-id="ed000-112">Specifies the valid parameter element values.</span></span> <span data-ttu-id="ed000-113">L’exemple suivant montre comment spécifier un élément ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="ed000-113">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="ed000-114">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="ed000-114">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="ed000-115">La valeur par défaut `true` indique que la casse est ignorée.</span><span class="sxs-lookup"><span data-stu-id="ed000-115">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="ed000-116">La valeur de `false` rend l’applet de commande sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="ed000-116">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed000-117">Notes</span><span class="sxs-lookup"><span data-stu-id="ed000-117">Remarks</span></span>

- <span data-ttu-id="ed000-118">Cet attribut ne peut être utilisé qu’une seule fois par paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed000-118">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="ed000-119">Si la valeur de paramètre est un tableau, chaque élément du tableau doit correspondre à un élément de l’ensemble d’attributs.</span><span class="sxs-lookup"><span data-stu-id="ed000-119">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="ed000-120">L’attribut ValidateSetAttribute est défini par la classe [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ed000-120">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed000-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed000-121">See Also</span></span>

[<span data-ttu-id="ed000-122">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="ed000-122">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="ed000-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed000-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
