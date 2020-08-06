---
title: Déclaration d’attribut ValidateRange | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.openlocfilehash: 9aeaa6f03c170389ff61a058b505dbcf74df6958
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787782"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="e6461-102">Déclaration de l’attribut ValidateRange</span><span class="sxs-lookup"><span data-stu-id="e6461-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="e6461-103">L’attribut ValidateRange spécifie les valeurs minimales et maximales (la plage) pour l’argument du paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e6461-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="e6461-104">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6461-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6461-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6461-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="e6461-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6461-106">Parameters</span></span>

<span data-ttu-id="e6461-107">`MinRange`([System. Object](/dotnet/api/system.object)) requis.</span><span class="sxs-lookup"><span data-stu-id="e6461-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="e6461-108">Spécifie la valeur minimale autorisée.</span><span class="sxs-lookup"><span data-stu-id="e6461-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="e6461-109">`MaxRange`([System. Object](/dotnet/api/system.object)) requis.</span><span class="sxs-lookup"><span data-stu-id="e6461-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="e6461-110">Spécifie la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="e6461-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6461-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e6461-111">Remarks</span></span>

- <span data-ttu-id="e6461-112">Le runtime Windows PowerShell lève une erreur de construction quand la valeur du `MinRange` paramètre est supérieure à la valeur du `MaxRange` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e6461-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="e6461-113">Le runtime Windows PowerShell lève une erreur de validation dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6461-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="e6461-114">Lorsque la valeur de l’argument est inférieure à la `MinRange` limite ou supérieure à la `MaxRange` limite.</span><span class="sxs-lookup"><span data-stu-id="e6461-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="e6461-115">Lorsque l’argument n’est pas du même type que les `MinRange` paramètres et `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="e6461-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="e6461-116">L’attribut ValidateRange est défini par la classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="e6461-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6461-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6461-117">See Also</span></span>

[<span data-ttu-id="e6461-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="e6461-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="e6461-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6461-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
