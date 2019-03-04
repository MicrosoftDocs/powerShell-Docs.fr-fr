---
title: Schéma de ressource publique | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859545"
---
# <a name="public-resource-schema"></a><span data-ttu-id="c208d-102">Schéma des ressources publiques</span><span class="sxs-lookup"><span data-stu-id="c208d-102">Public Resource Schema</span></span>

<span data-ttu-id="c208d-103">IIS Management OData utilise MOF pour définir les ressources et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="c208d-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="c208d-104">Les propriétés d’une entité de gestion OData correspondent directement aux propriétés du type managé retourné par l’applet de commande sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="c208d-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="c208d-105">Définition d’une ressource</span><span class="sxs-lookup"><span data-stu-id="c208d-105">Defining a resource</span></span>

<span data-ttu-id="c208d-106">Chaque ressource correspond à un objet retourné par une applet de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c208d-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="c208d-107">Dans le fichier MOF de la ressource de publc, vous définissez une ressource en déclarant une classe.</span><span class="sxs-lookup"><span data-stu-id="c208d-107">In the publc resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="c208d-108">La classe se compose des propriétés qui correspondent aux propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c208d-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="c208d-109">Par exemple, dans l’exemple suivant, le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) classe est représentée par le fichier MOF suivant.</span><span class="sxs-lookup"><span data-stu-id="c208d-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="c208d-110">Chaque nom de propriété est précédé d’un type de données.</span><span class="sxs-lookup"><span data-stu-id="c208d-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="c208d-111">Dans cet exemple, les types de données correspondent aux types de données primitifs CLR dans .NET Framework, mais les propriétés peuvent être également des références à d’autres ressources ou les types complexes, qui sont tous deux décrits plus loin.</span><span class="sxs-lookup"><span data-stu-id="c208d-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="c208d-112">Le `Key` qualificateur indique qu’une propriété est utilisée pour identifier de manière unique une instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="c208d-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="c208d-113">Une ressource peut avoir plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="c208d-113">A resource can have more than one key.</span></span>

<span data-ttu-id="c208d-114">Le `Required` qualificateur indique que la propriété est requise.</span><span class="sxs-lookup"><span data-stu-id="c208d-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="c208d-115">Si une propriété est étiquetée avec le `Key` qualificateur, il est considéré comme requis et le `Required` qualificateur n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c208d-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="c208d-116">Types de données complexes</span><span class="sxs-lookup"><span data-stu-id="c208d-116">Complex data types</span></span>

<span data-ttu-id="c208d-117">Propriétés d’entités peuvent avoir des types de données complexes.</span><span class="sxs-lookup"><span data-stu-id="c208d-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="c208d-118">Types de données complexes sont des types qui sont composés d’autres types, similaires aux structs dans le langage de programmation C.</span><span class="sxs-lookup"><span data-stu-id="c208d-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="c208d-119">Un type complexe est déclaré dans le fichier MOF en tant que classe avec le `ComplexType` qualificateur, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c208d-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="c208d-120">Pour déclarer une propriété d’entité comme un type complexe, vous la déclarer comme un `string` type avec le `EmbeddedInstance` qualificateur, y compris le nom du type complexe.</span><span class="sxs-lookup"><span data-stu-id="c208d-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="c208d-121">Le hshows exemple suit la déclaration d’une propriété de la `PswsTest_ProcessModule` type déclaré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="c208d-121">The following example hshows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="c208d-122">Association d’entités</span><span class="sxs-lookup"><span data-stu-id="c208d-122">Associating entities</span></span>

<span data-ttu-id="c208d-123">Vous pouvez associer les deux entités à l’aide de l’Association et AssocationClass qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="c208d-123">You can associate two entities by using the Association and AssocationClass qualifiers.</span></span> <span data-ttu-id="c208d-124">Pour plus d’informations, consultez [associant des entités de gestion OData](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="c208d-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="c208d-125">Types dérivés</span><span class="sxs-lookup"><span data-stu-id="c208d-125">Derived types</span></span>

<span data-ttu-id="c208d-126">Vous pouvez dériver un type à partir d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="c208d-126">You can derive a type from another type.</span></span> <span data-ttu-id="c208d-127">Le type dérivé hérite de toutes les propriétés du type dont il dérive en plus des propriétés dérivées explicitement.</span><span class="sxs-lookup"><span data-stu-id="c208d-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="c208d-128">L’exemple suivant montre une déclaration de type, puis une déclaration de deux types dérivés de ce type.</span><span class="sxs-lookup"><span data-stu-id="c208d-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

[Key] String ProductName;

};

Class DairyProduct : Product {

Uint16 PercentFat;
};
Class POPProduct : Product {

Boolean IsCarbonated;
};

```