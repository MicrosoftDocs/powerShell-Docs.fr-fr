---
title: Déclaration d’attribut de ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861205"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="4376b-102">Déclaration de l’attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="4376b-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="4376b-103">L’attribut ValidateSetAttribute spécifie un ensemble de valeurs possibles pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4376b-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="4376b-104">Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4376b-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="4376b-105">Lorsque cet attribut est spécifié, le runtime Windows PowerShell détermine si l’argument fourni pour le paramètre d’applet de commande correspond à un élément dans l’ensemble de l’élément fourni.</span><span class="sxs-lookup"><span data-stu-id="4376b-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="4376b-106">L’applet de commande est exécutée uniquement si l’argument de paramètre correspond à un élément dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="4376b-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="4376b-107">Si aucune correspondance n’est trouvée, une erreur est levée par le runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4376b-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="4376b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4376b-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="4376b-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4376b-109">Parameters</span></span>

<span data-ttu-id="4376b-110">`ValidValues` ([System.String](/dotnet/api/System.String)) requis.</span><span class="sxs-lookup"><span data-stu-id="4376b-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="4376b-111">Spécifie les valeurs d’élément de paramètre valide.</span><span class="sxs-lookup"><span data-stu-id="4376b-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="4376b-112">L’exemple suivant montre comment spécifier un seul élément ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="4376b-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="4376b-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="4376b-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="4376b-114">La valeur par défaut `true` indique que la casse est ignorée.</span><span class="sxs-lookup"><span data-stu-id="4376b-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="4376b-115">La valeur `false` rend l’applet de commande qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="4376b-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="4376b-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="4376b-116">Remarks</span></span>

- <span data-ttu-id="4376b-117">Cet attribut peut être utilisé qu’une seule fois par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4376b-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="4376b-118">Si la valeur du paramètre est un tableau, chaque élément du tableau doit correspondre à un élément de l’ensemble d’attributs.</span><span class="sxs-lookup"><span data-stu-id="4376b-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="4376b-119">L’attribut ValidateSetAttribute est défini par le [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="4376b-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="4376b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4376b-120">See Also</span></span>

[<span data-ttu-id="4376b-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="4376b-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="4376b-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4376b-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
