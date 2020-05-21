---
title: Déclaration d’attribut ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a1a494534169b2da470286020dfacfa8e9084839
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692325"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="ef724-102">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="ef724-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="ef724-103">L’attribut ValidateLength spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ef724-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="ef724-104">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef724-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef724-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef724-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ef724-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef724-106">Parameters</span></span>

<span data-ttu-id="ef724-107">`MinLength`([System. Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="ef724-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ef724-108">Spécifie le nombre minimal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="ef724-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="ef724-109">`MaxLength`([System. Int32](/dotnet/api/System.Int32)) requis.</span><span class="sxs-lookup"><span data-stu-id="ef724-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ef724-110">Spécifie le nombre maximal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="ef724-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef724-111">Notes</span><span class="sxs-lookup"><span data-stu-id="ef724-111">Remarks</span></span>

- <span data-ttu-id="ef724-112">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de validation d’entrée](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="ef724-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="ef724-113">Lorsque cet attribut n’est pas utilisé, l’argument du paramètre correspondant peut avoir n’importe quelle longueur.</span><span class="sxs-lookup"><span data-stu-id="ef724-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="ef724-114">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ef724-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="ef724-115">Lorsque la valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="ef724-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="ef724-116">Lorsque le `MaxLength` paramètre d’attribut a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="ef724-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="ef724-117">Lorsque l’argument n’est pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ef724-117">When the argument is not a string.</span></span>

- <span data-ttu-id="ef724-118">L’attribut ValidateLength est défini par la classe [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ef724-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef724-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef724-119">See Also</span></span>

[<span data-ttu-id="ef724-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="ef724-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="ef724-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef724-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
