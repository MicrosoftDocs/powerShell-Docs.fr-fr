---
title: Déclaration d’attribut ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369158"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="d85f8-102">Déclaration de l’attribut ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="d85f8-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="d85f8-103">L’attribut ValidatePattern spécifie un modèle d’expression régulière qui valide l’argument d’un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d85f8-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="d85f8-104">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d85f8-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="d85f8-105">Quand ValidatePattern est appelé dans une applet de commande, le runtime Windows PowerShell convertit l’argument du paramètre d’applet de commande en une chaîne, puis compare cette chaîne au modèle fourni par l’attribut ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="d85f8-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="d85f8-106">L’applet de commande est exécutée uniquement si la représentation sous forme de chaîne convertie de l’argument et du modèle fourni correspond à.</span><span class="sxs-lookup"><span data-stu-id="d85f8-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="d85f8-107">Si elles ne correspondent pas, une erreur est générée par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d85f8-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="d85f8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d85f8-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="d85f8-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d85f8-109">Parameters</span></span>

<span data-ttu-id="d85f8-110">`RegexString` ([System. String](/dotnet/api/System.String)) requis.</span><span class="sxs-lookup"><span data-stu-id="d85f8-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="d85f8-111">Spécifie une expression régulière qui valide l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="d85f8-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="d85f8-112">Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="d85f8-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="d85f8-113">Spécifie une combinaison d’opérations de bits d’indicateurs [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) qui spécifient des options d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d85f8-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="d85f8-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d85f8-114">Remarks</span></span>

- <span data-ttu-id="d85f8-115">Cet attribut ne peut être utilisé qu’une seule fois par paramètre.</span><span class="sxs-lookup"><span data-stu-id="d85f8-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="d85f8-116">Vous pouvez utiliser le paramètre `Option` de l’attribut pour définir plus précisément le modèle.</span><span class="sxs-lookup"><span data-stu-id="d85f8-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="d85f8-117">Par exemple, vous pouvez rendre le modèle sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="d85f8-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="d85f8-118">Si cet attribut est appliqué à une collection, chaque élément de la collection doit correspondre au modèle.</span><span class="sxs-lookup"><span data-stu-id="d85f8-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="d85f8-119">L’attribut ValidatePattern est défini par la classe [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d85f8-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d85f8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d85f8-120">See Also</span></span>

[<span data-ttu-id="d85f8-121">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="d85f8-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="d85f8-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d85f8-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
