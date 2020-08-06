---
title: Déclaration d’attribut ValidateCount | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.openlocfilehash: c013a354ee339bd14508fe30549673bc79d5c616
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786320"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="50257-102">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="50257-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="50257-103">L’attribut ValidateCount spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="50257-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="50257-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50257-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="50257-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50257-105">Parameters</span></span>

<span data-ttu-id="50257-106">`MinLength`([System. Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="50257-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="50257-107">Spécifie le nombre minimal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="50257-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="50257-108">`MaxLength`([System. Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="50257-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="50257-109">Spécifie le nombre maximal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="50257-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="50257-110">Notes</span><span class="sxs-lookup"><span data-stu-id="50257-110">Remarks</span></span>

- <span data-ttu-id="50257-111">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [Comment valider un nombre d’arguments][].</span><span class="sxs-lookup"><span data-stu-id="50257-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="50257-112">Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.</span><span class="sxs-lookup"><span data-stu-id="50257-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="50257-113">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="50257-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="50257-114">Les `MinLength` `MaxLength` paramètres d’attribut et ne sont pas de type [System. Int32][].</span><span class="sxs-lookup"><span data-stu-id="50257-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="50257-115">La valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="50257-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="50257-116">L’attribut ValidateCount est défini par la classe [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="50257-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="50257-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50257-117">See Also</span></span>

<span data-ttu-id="50257-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="50257-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="50257-119">[Guide pratique pour valider un nombre d’arguments][]</span><span class="sxs-lookup"><span data-stu-id="50257-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="50257-120">[Écriture d’une applet de commande Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="50257-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Guide pratique pour valider un nombre d’arguments]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Écriture d’une applet de commande Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
