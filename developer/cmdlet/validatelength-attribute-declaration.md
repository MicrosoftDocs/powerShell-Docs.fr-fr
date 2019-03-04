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
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858865"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="d7a81-102">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="d7a81-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="d7a81-103">L’attribut ValidateLength Spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d7a81-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="d7a81-104">Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7a81-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7a81-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7a81-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="d7a81-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7a81-106">Parameters</span></span>

<span data-ttu-id="d7a81-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) requis.</span><span class="sxs-lookup"><span data-stu-id="d7a81-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="d7a81-108">Spécifie le nombre minimal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="d7a81-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="d7a81-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) requis.</span><span class="sxs-lookup"><span data-stu-id="d7a81-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="d7a81-110">Spécifie le nombre maximal de caractères autorisés.</span><span class="sxs-lookup"><span data-stu-id="d7a81-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7a81-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="d7a81-111">Remarks</span></span>

- <span data-ttu-id="d7a81-112">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="d7a81-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="d7a81-113">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="d7a81-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="d7a81-114">Lorsque cet attribut n’est pas utilisé, l’argument de paramètre correspondant peut être de n’importe quelle longueur.</span><span class="sxs-lookup"><span data-stu-id="d7a81-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="d7a81-115">Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7a81-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="d7a81-116">Lorsque la valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.</span><span class="sxs-lookup"><span data-stu-id="d7a81-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="d7a81-117">Lorsque le `MaxLength` paramètre d’attribut est défini sur 0.</span><span class="sxs-lookup"><span data-stu-id="d7a81-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="d7a81-118">Lorsque l’argument n’est pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d7a81-118">When the argument is not a string.</span></span>

- <span data-ttu-id="d7a81-119">L’attribut ValidateLength est défini par le [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="d7a81-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7a81-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7a81-120">See Also</span></span>

[<span data-ttu-id="d7a81-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="d7a81-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="d7a81-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7a81-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
