---
ms.date: 07/09/2020
ms.topic: reference
title: Membres de classe de système de type étendu
description: Membres de classe de système de type étendu
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666839"
---
# <a name="extended-type-system-class-members"></a><span data-ttu-id="cea5a-103">Membres de classe de système de type étendu</span><span class="sxs-lookup"><span data-stu-id="cea5a-103">Extended Type System class members</span></span>

<span data-ttu-id="cea5a-104">ETS fait référence à plusieurs genres de membres dont les types sont définis par l’énumération **PSMemberTypes** .</span><span class="sxs-lookup"><span data-stu-id="cea5a-104">ETS refers to a number of different kinds of members whose types are defined by the **PSMemberTypes** enumeration.</span></span> <span data-ttu-id="cea5a-105">Ces types de membres incluent des propriétés, des méthodes, des membres et des jeux de membres qui sont tous définis par leur propre type CLR.</span><span class="sxs-lookup"><span data-stu-id="cea5a-105">These member types include properties, methods, members, and member sets that are each defined by their own CLR type.</span></span> <span data-ttu-id="cea5a-106">Par exemple, un **NoteProperty** est défini par son propre type **PSNoteProperty** .</span><span class="sxs-lookup"><span data-stu-id="cea5a-106">For example, a **NoteProperty** is defined by its own **PSNoteProperty** type.</span></span> <span data-ttu-id="cea5a-107">Ces types CLR individuels ont à la fois leurs propres propriétés uniques et propriétés communes qui sont héritées de la [classe PSMemberInfo](/dotnet/api/system.management.automation.psmemberinfo).</span><span class="sxs-lookup"><span data-stu-id="cea5a-107">These individual CLR types have both their own unique properties and common properties that are inherited from the [PSMemberInfo class](/dotnet/api/system.management.automation.psmemberinfo).</span></span>

## <a name="the-psmemberinfo-class"></a><span data-ttu-id="cea5a-108">La classe PSMemberInfo</span><span class="sxs-lookup"><span data-stu-id="cea5a-108">The PSMemberInfo class</span></span>

<span data-ttu-id="cea5a-109">La classe **PSMemberInfo** sert de classe de base pour tous les types de membres ETS.</span><span class="sxs-lookup"><span data-stu-id="cea5a-109">The **PSMemberInfo** class serves as a base class for all ETS member types.</span></span> <span data-ttu-id="cea5a-110">Cette classe fournit les propriétés de base suivantes à tous les types CLR de membre.</span><span class="sxs-lookup"><span data-stu-id="cea5a-110">This class provides the following base properties to all member CLR types.</span></span>

- <span data-ttu-id="cea5a-111">Propriété **Name** : nom du membre.</span><span class="sxs-lookup"><span data-stu-id="cea5a-111">**Name** property: The name of the member.</span></span> <span data-ttu-id="cea5a-112">Ce nom peut être défini par l’objet de base ou défini par PowerShell quand des membres adaptés ou des membres étendus sont exposés.</span><span class="sxs-lookup"><span data-stu-id="cea5a-112">This name can be defined by the base-object or defined by PowerShell when adapted members or extended members are exposed.</span></span>
- <span data-ttu-id="cea5a-113">Propriété de **valeur** : valeur retournée par le membre particulier.</span><span class="sxs-lookup"><span data-stu-id="cea5a-113">**Value** property: The value returned from the particular member.</span></span> <span data-ttu-id="cea5a-114">Chaque type de membre définit la manière dont il gère sa valeur de membre.</span><span class="sxs-lookup"><span data-stu-id="cea5a-114">Each member type defines how it handles its member value.</span></span>
- <span data-ttu-id="cea5a-115">Propriété **TypeNameOfValue** : il s’agit du nom du type CLR de la valeur retournée par la propriété Value.</span><span class="sxs-lookup"><span data-stu-id="cea5a-115">**TypeNameOfValue** property: This is the name of the CLR type of the value that is returned by the Value property.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="cea5a-116">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="cea5a-116">Accessing members</span></span>

<span data-ttu-id="cea5a-117">Les collections de membres sont accessibles via les propriétés des **membres**, des **méthodes** et des **Propriétés** de l’objet **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="cea5a-117">Collections of members can be accessed through the **Members**, **Methods**, and **Properties** properties of the **PSObject** object.</span></span>

## <a name="ets-properties"></a><span data-ttu-id="cea5a-118">Propriétés ETS</span><span class="sxs-lookup"><span data-stu-id="cea5a-118">ETS properties</span></span>

<span data-ttu-id="cea5a-119">Les propriétés ETS sont des membres qui peuvent être traités comme une propriété.</span><span class="sxs-lookup"><span data-stu-id="cea5a-119">ETS properties are members that can be treated as a property.</span></span> <span data-ttu-id="cea5a-120">Pour l’essentiel, ils peuvent apparaître sur le côté gauche d’une expression.</span><span class="sxs-lookup"><span data-stu-id="cea5a-120">Essentially, they can appear on the left-hand side of an expression.</span></span> <span data-ttu-id="cea5a-121">Elles incluent des propriétés d’alias, des propriétés de code, des propriétés PowerShell, des propriétés de note et des propriétés de script.</span><span class="sxs-lookup"><span data-stu-id="cea5a-121">They include alias properties, code properties, PowerShell properties, note properties, and script properties.</span></span> <span data-ttu-id="cea5a-122">Pour plus d’informations sur ces types de propriétés, consultez [Propriétés ETS](properties.md).</span><span class="sxs-lookup"><span data-stu-id="cea5a-122">For more information about these types of properties, see [ETS properties](properties.md).</span></span>

## <a name="ets-methods"></a><span data-ttu-id="cea5a-123">Méthodes ETS</span><span class="sxs-lookup"><span data-stu-id="cea5a-123">ETS methods</span></span>

<span data-ttu-id="cea5a-124">Les méthodes ETS sont des membres qui peuvent prendre des arguments, peuvent retourner des résultats et ne peuvent pas apparaître sur le côté gauche d’une expression.</span><span class="sxs-lookup"><span data-stu-id="cea5a-124">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="cea5a-125">Elles incluent les méthodes de code, les méthodes PowerShell et les méthodes de script.</span><span class="sxs-lookup"><span data-stu-id="cea5a-125">They include code methods, PowerShell methods, and script methods.</span></span>
<span data-ttu-id="cea5a-126">Pour plus d’informations sur ces types de méthodes, consultez [méthodes ETS](methods.md).</span><span class="sxs-lookup"><span data-stu-id="cea5a-126">For more information about these types of methods, see [ETS methods](methods.md).</span></span>
