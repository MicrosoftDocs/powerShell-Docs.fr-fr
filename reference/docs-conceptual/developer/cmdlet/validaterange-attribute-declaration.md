---
title: Déclaration d’attribut ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692012"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="102eb-102">Déclaration de l’attribut ValidateRange</span><span class="sxs-lookup"><span data-stu-id="102eb-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="102eb-103">L’attribut ValidateRange spécifie les valeurs minimales et maximales (la plage) pour l’argument du paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="102eb-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="102eb-104">Cet attribut peut également être utilisé par les fonctions Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="102eb-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="102eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="102eb-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="102eb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="102eb-106">Parameters</span></span>

<span data-ttu-id="102eb-107">`MinRange`([System. Object](/dotnet/api/system.object)) requis.</span><span class="sxs-lookup"><span data-stu-id="102eb-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="102eb-108">Spécifie la valeur minimale autorisée.</span><span class="sxs-lookup"><span data-stu-id="102eb-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="102eb-109">`MaxRange`([System. Object](/dotnet/api/system.object)) requis.</span><span class="sxs-lookup"><span data-stu-id="102eb-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="102eb-110">Spécifie la valeur maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="102eb-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="102eb-111">Notes</span><span class="sxs-lookup"><span data-stu-id="102eb-111">Remarks</span></span>

- <span data-ttu-id="102eb-112">Le runtime Windows PowerShell lève une erreur de construction quand la valeur du `MinRange` paramètre est supérieure à la valeur du `MaxRange` paramètre.</span><span class="sxs-lookup"><span data-stu-id="102eb-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="102eb-113">Le runtime Windows PowerShell lève une erreur de validation dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="102eb-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="102eb-114">Lorsque la valeur de l’argument est inférieure à la `MinRange` limite ou supérieure à la `MaxRange` limite.</span><span class="sxs-lookup"><span data-stu-id="102eb-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="102eb-115">Lorsque l’argument n’est pas du même type que les `MinRange` paramètres et `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="102eb-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="102eb-116">L’attribut ValidateRange est défini par la classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="102eb-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="102eb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="102eb-117">See Also</span></span>

[<span data-ttu-id="102eb-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="102eb-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="102eb-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="102eb-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
