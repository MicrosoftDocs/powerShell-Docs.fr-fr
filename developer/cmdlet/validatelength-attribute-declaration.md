---
title: Déclaration d’attribut de ValidateLength | Microsoft Docs
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
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067159"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="3bb2f-102">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="3bb2f-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="3bb2f-103">L’attribut ValidateLength Spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="3bb2f-104">Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bb2f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bb2f-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="3bb2f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bb2f-106">Parameters</span></span>

<span data-ttu-id="3bb2f-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) requis.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="3bb2f-108">Spécifie le nombre minimal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="3bb2f-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) requis.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="3bb2f-110">Spécifie le nombre maximal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bb2f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="3bb2f-111">Remarks</span></span>

- <span data-ttu-id="3bb2f-112">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="3bb2f-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="3bb2f-113">Lorsque cet attribut n’est pas utilisé, l’argument de paramètre correspondant peut être de n’importe quelle longueur.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="3bb2f-114">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bb2f-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="3bb2f-115">Lorsque la valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="3bb2f-116">Lorsque le `MaxLength` paramètre d’attribut est défini sur 0.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="3bb2f-117">Lorsque l’argument n’est pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-117">When the argument is not a string.</span></span>

- <span data-ttu-id="3bb2f-118">L’attribut ValidateLength est défini par le [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="3bb2f-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bb2f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bb2f-119">See Also</span></span>

[<span data-ttu-id="3bb2f-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="3bb2f-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="3bb2f-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bb2f-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
