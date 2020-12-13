---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidateCount
description: Déclaration de l’attribut ValidateCount
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646275"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="8a6f1-103">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="8a6f1-103">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="8a6f1-104">L’attribut ValidateCount spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-104">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a6f1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a6f1-105">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="8a6f1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a6f1-106">Parameters</span></span>

<span data-ttu-id="8a6f1-107">`MinLength` ([System. Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-107">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="8a6f1-108">Spécifie le nombre minimal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-108">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="8a6f1-109">`MaxLength`([System. Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-109">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="8a6f1-110">Spécifie le nombre maximal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-110">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a6f1-111">Notes</span><span class="sxs-lookup"><span data-stu-id="8a6f1-111">Remarks</span></span>

- <span data-ttu-id="8a6f1-112">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [Comment valider un nombre d’arguments][].</span><span class="sxs-lookup"><span data-stu-id="8a6f1-112">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="8a6f1-113">Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-113">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="8a6f1-114">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a6f1-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="8a6f1-115">Les `MinLength` `MaxLength` paramètres d’attribut et ne sont pas de type [System. Int32][].</span><span class="sxs-lookup"><span data-stu-id="8a6f1-115">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="8a6f1-116">La valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="8a6f1-116">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="8a6f1-117">L’attribut ValidateCount est défini par la classe [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="8a6f1-117">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a6f1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a6f1-118">See Also</span></span>

<span data-ttu-id="8a6f1-119">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="8a6f1-119">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="8a6f1-120">[Guide pratique pour valider un nombre d’arguments][]</span><span class="sxs-lookup"><span data-stu-id="8a6f1-120">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="8a6f1-121">[Écriture d’une applet de commande Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="8a6f1-121">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Guide pratique pour valider un nombre d’arguments]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Écriture d’une applet de commande Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
