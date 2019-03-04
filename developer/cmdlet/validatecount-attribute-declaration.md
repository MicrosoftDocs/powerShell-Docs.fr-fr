---
title: Déclaration d’attribut de ValidateCount | Microsoft Docs
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
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859155"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="5dd35-102">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="5dd35-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="5dd35-103">L’attribut ValidateCount Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5dd35-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="5dd35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dd35-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="5dd35-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5dd35-105">Parameters</span></span>

<span data-ttu-id="5dd35-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="5dd35-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="5dd35-107">Spécifie le nombre minimal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5dd35-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="5dd35-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="5dd35-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="5dd35-109">Spécifie le nombre maximal d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5dd35-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="5dd35-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="5dd35-110">Remarks</span></span>

- <span data-ttu-id="5dd35-111">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="5dd35-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="5dd35-112">Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5dd35-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="5dd35-113">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5dd35-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="5dd35-114">Le `MinLength` et `MaxLength` des paramètres d’attribut ne sont pas de type [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="5dd35-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="5dd35-115">La valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="5dd35-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="5dd35-116">L’attribut ValidateCount est défini par le [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.</span><span class="sxs-lookup"><span data-stu-id="5dd35-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5dd35-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dd35-117">See Also</span></span>

[<span data-ttu-id="5dd35-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="5dd35-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="5dd35-119">Comment déclarer des règles de Validation d’entrée</span><span class="sxs-lookup"><span data-stu-id="5dd35-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="5dd35-120">Comment déclarer des règles de Validation d’entrée</span><span class="sxs-lookup"><span data-stu-id="5dd35-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="5dd35-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd35-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
