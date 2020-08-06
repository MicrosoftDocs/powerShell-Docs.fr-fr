---
title: Déclaration d’attribut ValidateSet | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787765"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="b94fb-102">Déclaration de l’attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="b94fb-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="b94fb-103">L’attribut ValidateSetAttribute spécifie un ensemble de valeurs possibles pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b94fb-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="b94fb-104">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b94fb-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="b94fb-105">Lorsque cet attribut est spécifié, le runtime Windows PowerShell détermine si l’argument fourni pour le paramètre d’applet de commande correspond à un élément dans l’ensemble d’éléments fourni.</span><span class="sxs-lookup"><span data-stu-id="b94fb-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="b94fb-106">L’applet de commande est exécutée uniquement si l’argument de paramètre correspond à un élément du jeu.</span><span class="sxs-lookup"><span data-stu-id="b94fb-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="b94fb-107">Si aucune correspondance n’est trouvée, une erreur est générée par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b94fb-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="b94fb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b94fb-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="b94fb-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b94fb-109">Parameters</span></span>

<span data-ttu-id="b94fb-110">`ValidValues`([System. String](/dotnet/api/System.String)) requis.</span><span class="sxs-lookup"><span data-stu-id="b94fb-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="b94fb-111">Spécifie les valeurs d’élément de paramètre valides.</span><span class="sxs-lookup"><span data-stu-id="b94fb-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="b94fb-112">L’exemple suivant montre comment spécifier un élément ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="b94fb-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="b94fb-113">`IgnoreCase`([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="b94fb-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="b94fb-114">La valeur par défaut `true` indique que la casse est ignorée.</span><span class="sxs-lookup"><span data-stu-id="b94fb-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="b94fb-115">La valeur de `false` rend l’applet de commande sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="b94fb-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="b94fb-116">Notes</span><span class="sxs-lookup"><span data-stu-id="b94fb-116">Remarks</span></span>

- <span data-ttu-id="b94fb-117">Cet attribut ne peut être utilisé qu’une seule fois par paramètre.</span><span class="sxs-lookup"><span data-stu-id="b94fb-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="b94fb-118">Si la valeur de paramètre est un tableau, chaque élément du tableau doit correspondre à un élément de l’ensemble d’attributs.</span><span class="sxs-lookup"><span data-stu-id="b94fb-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="b94fb-119">L’attribut ValidateSetAttribute est défini par la classe [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="b94fb-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b94fb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b94fb-120">See Also</span></span>

[<span data-ttu-id="b94fb-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="b94fb-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="b94fb-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b94fb-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
