---
title: Déclaration d’attribut ValidateLength | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.openlocfilehash: 7145dde55e79eeea6e3ceb91dfc1c93043a8857c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786303"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="95f6c-102">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="95f6c-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="95f6c-103">L’attribut ValidateLength spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95f6c-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="95f6c-104">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95f6c-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="95f6c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95f6c-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="95f6c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95f6c-106">Parameters</span></span>

<span data-ttu-id="95f6c-107">`MinLength`([System. Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="95f6c-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="95f6c-108">Spécifie le nombre minimal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="95f6c-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="95f6c-109">`MaxLength`([System. Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="95f6c-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="95f6c-110">Spécifie le nombre maximal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="95f6c-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="95f6c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="95f6c-111">Remarks</span></span>

- <span data-ttu-id="95f6c-112">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de validation d’entrée](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="95f6c-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="95f6c-113">Lorsque cet attribut n’est pas utilisé, l’argument du paramètre correspondant peut avoir n’importe quelle longueur.</span><span class="sxs-lookup"><span data-stu-id="95f6c-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="95f6c-114">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="95f6c-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="95f6c-115">Lorsque la valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="95f6c-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="95f6c-116">Lorsque le `MaxLength` paramètre d’attribut a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="95f6c-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="95f6c-117">Lorsque l’argument n’est pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="95f6c-117">When the argument is not a string.</span></span>

- <span data-ttu-id="95f6c-118">L’attribut ValidateLength est défini par la classe [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="95f6c-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="95f6c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95f6c-119">See Also</span></span>

[<span data-ttu-id="95f6c-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="95f6c-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="95f6c-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95f6c-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
