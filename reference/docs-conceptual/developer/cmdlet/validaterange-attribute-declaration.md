---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidateRange
description: Déclaration de l’attribut ValidateRange
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660601"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="25d3f-103">Déclaration de l’attribut ValidateRange</span><span class="sxs-lookup"><span data-stu-id="25d3f-103">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="25d3f-104">L’attribut ValidateRange spécifie les valeurs minimales et maximales (la plage) pour l’argument du paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="25d3f-104">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="25d3f-105">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25d3f-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="25d3f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25d3f-106">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="25d3f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25d3f-107">Parameters</span></span>

<span data-ttu-id="25d3f-108">`MinRange` ([System. Object](/dotnet/api/system.object)) requis.</span><span class="sxs-lookup"><span data-stu-id="25d3f-108">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="25d3f-109">Spécifie la valeur minimale autorisée.</span><span class="sxs-lookup"><span data-stu-id="25d3f-109">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="25d3f-110">`MaxRange` ([System. Object](/dotnet/api/system.object)) requis.</span><span class="sxs-lookup"><span data-stu-id="25d3f-110">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="25d3f-111">Spécifie la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="25d3f-111">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="25d3f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="25d3f-112">Remarks</span></span>

- <span data-ttu-id="25d3f-113">Le runtime Windows PowerShell lève une erreur de construction quand la valeur du `MinRange` paramètre est supérieure à la valeur du `MaxRange` paramètre.</span><span class="sxs-lookup"><span data-stu-id="25d3f-113">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="25d3f-114">Le runtime Windows PowerShell lève une erreur de validation dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="25d3f-114">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="25d3f-115">Lorsque la valeur de l’argument est inférieure à la `MinRange` limite ou supérieure à la `MaxRange` limite.</span><span class="sxs-lookup"><span data-stu-id="25d3f-115">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="25d3f-116">Lorsque l’argument n’est pas du même type que les `MinRange` paramètres et `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="25d3f-116">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="25d3f-117">L’attribut ValidateRange est défini par la classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="25d3f-117">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="25d3f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25d3f-118">See Also</span></span>

[<span data-ttu-id="25d3f-119">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="25d3f-119">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="25d3f-120">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25d3f-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
