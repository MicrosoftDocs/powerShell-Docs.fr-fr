---
title: Déclaration d’attribut ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692377"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="78410-102">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="78410-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="78410-103">L’attribut ValidateCount spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="78410-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="78410-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78410-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="78410-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78410-105">Parameters</span></span>

<span data-ttu-id="78410-106">`MinLength`([System. Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="78410-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="78410-107">Spécifie le nombre minimal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="78410-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="78410-108">`MaxLength`([System. Int32][]) requis.</span><span class="sxs-lookup"><span data-stu-id="78410-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="78410-109">Spécifie le nombre maximal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="78410-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="78410-110">Notes</span><span class="sxs-lookup"><span data-stu-id="78410-110">Remarks</span></span>

- <span data-ttu-id="78410-111">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [Comment valider un nombre d’arguments][].</span><span class="sxs-lookup"><span data-stu-id="78410-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="78410-112">Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.</span><span class="sxs-lookup"><span data-stu-id="78410-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="78410-113">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="78410-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="78410-114">Les `MinLength` `MaxLength` paramètres d’attribut et ne sont pas de type [System. Int32][].</span><span class="sxs-lookup"><span data-stu-id="78410-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="78410-115">La valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="78410-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="78410-116">L’attribut ValidateCount est défini par la classe [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="78410-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="78410-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78410-117">See Also</span></span>

<span data-ttu-id="78410-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="78410-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="78410-119">[Guide pratique pour valider un nombre d’arguments][]</span><span class="sxs-lookup"><span data-stu-id="78410-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="78410-120">[Écriture d’une applet de commande Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="78410-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Guide pratique pour valider un nombre d’arguments]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Écriture d’une applet de commande Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
