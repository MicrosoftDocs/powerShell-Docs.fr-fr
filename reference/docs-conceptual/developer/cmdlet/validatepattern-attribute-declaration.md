---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidatePattern
description: Déclaration de l’attribut ValidatePattern
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646164"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="0e4f6-103">Déclaration de l’attribut ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="0e4f6-103">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="0e4f6-104">L’attribut ValidatePattern spécifie un modèle d’expression régulière qui valide l’argument d’un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-104">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="0e4f6-105">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="0e4f6-106">Quand ValidatePattern est appelé dans une applet de commande, le runtime Windows PowerShell convertit l’argument du paramètre d’applet de commande en une chaîne, puis compare cette chaîne au modèle fourni par l’attribut ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-106">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="0e4f6-107">L’applet de commande est exécutée uniquement si la représentation sous forme de chaîne convertie de l’argument et du modèle fourni correspond à.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-107">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="0e4f6-108">Si elles ne correspondent pas, une erreur est générée par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-108">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e4f6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e4f6-109">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="0e4f6-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e4f6-110">Parameters</span></span>

<span data-ttu-id="0e4f6-111">`RegexString` ([System. String](/dotnet/api/System.String)) requis.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-111">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="0e4f6-112">Spécifie une expression régulière qui valide l’argument du paramètre.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-112">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="0e4f6-113">Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-113">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="0e4f6-114">Spécifie une combinaison d’opérations de bits d’indicateurs [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) qui spécifient des options d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-114">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e4f6-115">Notes</span><span class="sxs-lookup"><span data-stu-id="0e4f6-115">Remarks</span></span>

- <span data-ttu-id="0e4f6-116">Cet attribut ne peut être utilisé qu’une seule fois par paramètre.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-116">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="0e4f6-117">Vous pouvez utiliser le `Option` paramètre de l’attribut pour définir plus précisément le modèle.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-117">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="0e4f6-118">Par exemple, vous pouvez rendre le modèle sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-118">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="0e4f6-119">Si cet attribut est appliqué à une collection, chaque élément de la collection doit correspondre au modèle.</span><span class="sxs-lookup"><span data-stu-id="0e4f6-119">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="0e4f6-120">L’attribut ValidatePattern est défini par la classe [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0e4f6-120">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e4f6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e4f6-121">See Also</span></span>

[<span data-ttu-id="0e4f6-122">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="0e4f6-122">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="0e4f6-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e4f6-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
