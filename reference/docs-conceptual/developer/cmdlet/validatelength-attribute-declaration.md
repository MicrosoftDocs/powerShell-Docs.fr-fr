---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidateLength
description: Déclaration de l’attribut ValidateLength
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646189"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="0f515-103">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="0f515-103">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="0f515-104">L’attribut ValidateLength spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0f515-104">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="0f515-105">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f515-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f515-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f515-106">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="0f515-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f515-107">Parameters</span></span>

<span data-ttu-id="0f515-108">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="0f515-108">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="0f515-109">Spécifie le nombre minimal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="0f515-109">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="0f515-110">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="0f515-110">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="0f515-111">Spécifie le nombre maximal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="0f515-111">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f515-112">Notes</span><span class="sxs-lookup"><span data-stu-id="0f515-112">Remarks</span></span>

- <span data-ttu-id="0f515-113">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de validation d’entrée](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="0f515-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="0f515-114">Lorsque cet attribut n’est pas utilisé, l’argument du paramètre correspondant peut avoir n’importe quelle longueur.</span><span class="sxs-lookup"><span data-stu-id="0f515-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="0f515-115">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f515-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="0f515-116">Lorsque la valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="0f515-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="0f515-117">Lorsque le `MaxLength` paramètre d’attribut a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="0f515-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="0f515-118">Lorsque l’argument n’est pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="0f515-118">When the argument is not a string.</span></span>

- <span data-ttu-id="0f515-119">L’attribut ValidateLength est défini par la classe [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0f515-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f515-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f515-120">See Also</span></span>

[<span data-ttu-id="0f515-121">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="0f515-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="0f515-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f515-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
