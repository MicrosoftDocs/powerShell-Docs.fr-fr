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
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366268"
---
# <a name="public-resource-schema"></a><span data-ttu-id="9a120-102">Schéma des ressources publiques</span><span class="sxs-lookup"><span data-stu-id="9a120-102">Public Resource Schema</span></span>

<span data-ttu-id="9a120-103">La gestion OData utilise MOF pour définir les ressources et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="9a120-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="9a120-104">Les propriétés d’une entité de gestion OData correspondent directement aux propriétés du type managé retourné par l’applet de commande sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="9a120-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="9a120-105">Définition d’une ressource</span><span class="sxs-lookup"><span data-stu-id="9a120-105">Defining a resource</span></span>

<span data-ttu-id="9a120-106">Chaque ressource correspond à un objet retourné par une applet de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a120-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="9a120-107">Dans le fichier MOF des ressources publiques, vous définissez une ressource en déclarant une classe.</span><span class="sxs-lookup"><span data-stu-id="9a120-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="9a120-108">La classe se compose de propriétés qui correspondent aux propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9a120-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="9a120-109">Par exemple, dans l’exemple suivant, la classe [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est représentée par le MOF suivant.</span><span class="sxs-lookup"><span data-stu-id="9a120-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="9a120-110">Chaque nom de propriété est précédé d’un type de données.</span><span class="sxs-lookup"><span data-stu-id="9a120-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="9a120-111">Les types de données de cet exemple correspondent aux types de données CLR primitifs dans le .NET Framework, mais les propriétés peuvent également être des références à d’autres ressources ou types complexes, qui sont tous deux décrits ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9a120-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="9a120-112">Le qualificateur `Key` indique qu’une propriété est utilisée pour identifier de manière unique une instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="9a120-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="9a120-113">Une ressource peut avoir plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="9a120-113">A resource can have more than one key.</span></span>

<span data-ttu-id="9a120-114">Le qualificateur `Required` indique que la propriété est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9a120-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="9a120-115">Si une propriété est étiquetée avec le qualificateur `Key`, elle est considérée comme requise et le qualificateur `Required` n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9a120-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="9a120-116">Types de données complexes</span><span class="sxs-lookup"><span data-stu-id="9a120-116">Complex data types</span></span>

<span data-ttu-id="9a120-117">Les propriétés des entités peuvent avoir des types de données complexes.</span><span class="sxs-lookup"><span data-stu-id="9a120-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="9a120-118">Les types de données complexes sont des types qui sont constitués d’autres types, comme des structs dans le langage de programmation C.</span><span class="sxs-lookup"><span data-stu-id="9a120-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="9a120-119">Un type complexe est déclaré dans le fichier MOF en tant que classe avec le qualificateur `ComplexType`, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9a120-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="9a120-120">Pour déclarer une propriété d’entité en tant que type complexe, vous la déclarez en tant que type `string` avec le qualificateur `EmbeddedInstance`, y compris le nom du type complexe.</span><span class="sxs-lookup"><span data-stu-id="9a120-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="9a120-121">L’exemple suivant illustre la déclaration d’une propriété du type `PswsTest_ProcessModule` déclaré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="9a120-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="9a120-122">Associer des entités</span><span class="sxs-lookup"><span data-stu-id="9a120-122">Associating entities</span></span>

<span data-ttu-id="9a120-123">Vous pouvez associer deux entités à l’aide des qualificateurs Association et AssociationClass.</span><span class="sxs-lookup"><span data-stu-id="9a120-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="9a120-124">Pour plus d’informations, consultez [Association d’entités de gestion OData](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="9a120-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="9a120-125">Types dérivés</span><span class="sxs-lookup"><span data-stu-id="9a120-125">Derived types</span></span>

<span data-ttu-id="9a120-126">Vous pouvez dériver un type à partir d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="9a120-126">You can derive a type from another type.</span></span> <span data-ttu-id="9a120-127">Le type dérivé hérite de toutes les propriétés du type à partir duquel il dérive, en plus des propriétés dérivées explicitement.</span><span class="sxs-lookup"><span data-stu-id="9a120-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="9a120-128">L’exemple suivant illustre une déclaration de type, puis une déclaration de deux types dérivés de ce type.</span><span class="sxs-lookup"><span data-stu-id="9a120-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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