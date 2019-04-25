---
title: Déclaration d’attribut de ValidatePattern | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067125"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="b7fa9-102">Déclaration de l’attribut ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="b7fa9-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="b7fa9-103">L’attribut ValidatePattern spécifie un modèle d’expression régulière qui valide l’argument d’un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="b7fa9-104">Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="b7fa9-105">Lorsque ValidatePattern est appelé au sein d’une applet de commande, le runtime Windows PowerShell convertit l’argument du paramètre d’applet de commande en une chaîne et compare ensuite cette chaîne pour le modèle fourni par l’attribut ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="b7fa9-106">L’applet de commande est exécutée uniquement si correspond à la représentation sous forme de chaîne convertie de l’argument et le modèle fourni.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="b7fa9-107">Si elles ne correspondent pas, une erreur est levée par le runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7fa9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7fa9-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="b7fa9-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7fa9-109">Parameters</span></span>

<span data-ttu-id="b7fa9-110">`RegexString` ([System.String](/dotnet/api/System.String)) requis.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="b7fa9-111">Spécifie une expression régulière qui valide l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="b7fa9-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) paramètre nommé facultatif.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="b7fa9-113">Spécifie une combinaison au niveau du bit de [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) indicateurs qui spécifient les options des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7fa9-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7fa9-114">Remarks</span></span>

- <span data-ttu-id="b7fa9-115">Cet attribut peut être utilisé qu’une seule fois par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="b7fa9-116">Vous pouvez utiliser le `Option` paramètre de l’attribut à définir le modèle.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="b7fa9-117">Par exemple, vous pouvez rendre le modèle respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="b7fa9-118">Si cet attribut est appliqué à une collection, chaque élément dans la collection doit correspondre au modèle.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="b7fa9-119">L’attribut ValidatePattern est défini par le [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="b7fa9-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7fa9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7fa9-120">See Also</span></span>

[<span data-ttu-id="b7fa9-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="b7fa9-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="b7fa9-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7fa9-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
