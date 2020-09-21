---
ms.date: 07/29/2020
title: Nouvelles fonctionnalités de langage dans PowerShell 5.0
ms.openlocfilehash: dada39c4121a810c7ce87a642f232934152104e5
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410170"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="3cd95-102">Nouvelles fonctionnalités de langage dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3cd95-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="3cd95-103">PowerShell 5.0 offre la possibilité de définir des classes et d’autres types définis par l’utilisateur suivant une syntaxe et une sémantique formelles similaires à celles des autres langages de programmation orientés objet.</span><span class="sxs-lookup"><span data-stu-id="3cd95-103">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="3cd95-104">L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.</span><span class="sxs-lookup"><span data-stu-id="3cd95-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

<span data-ttu-id="3cd95-105">PowerShell 5.0 offre les nouveaux éléments de langage suivants dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="3cd95-105">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="3cd95-106">Mot clé classe</span><span class="sxs-lookup"><span data-stu-id="3cd95-106">Class keyword</span></span>

<span data-ttu-id="3cd95-107">Le mot clé `class` définit une nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="3cd95-107">The `class` keyword defines a new class.</span></span> <span data-ttu-id="3cd95-108">Il s’agit d’un véritable type .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cd95-108">This is a true .NET Framework type.</span></span> <span data-ttu-id="3cd95-109">Les membres de la classe sont publics, mais uniquement dans l’étendue du module.</span><span class="sxs-lookup"><span data-stu-id="3cd95-109">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="3cd95-110">Il n’est pas possible de faire référence au nom de type sous forme de chaîne (par exemple, `New-Object` ne fonctionne pas) ou, dans cette version, d’utiliser un littéral de type (par exemple, `[MyClass]`) en dehors du fichier de script ou du module dans lequel la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="3cd95-110">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="3cd95-111">Mot clé Enum et énumérations</span><span class="sxs-lookup"><span data-stu-id="3cd95-111">Enum keyword and enumerations</span></span>

<span data-ttu-id="3cd95-112">La prise en charge du mot clé `enum` a été ajoutée. Il utilise le saut de ligne comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="3cd95-112">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="3cd95-113">Il n’est pas possible à l’heure actuelle de définir un énumérateur par lui-même.</span><span class="sxs-lookup"><span data-stu-id="3cd95-113">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="3cd95-114">Vous pouvez en revanche l’initialiser à partir d’un autre enum, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3cd95-114">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="3cd95-115">Par ailleurs, le type de base n’est pas spécifiable ; il s’agit toujours de `[int]`.</span><span class="sxs-lookup"><span data-stu-id="3cd95-115">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="3cd95-116">Une valeur d’énumérateur doit être une constante au moment de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="3cd95-116">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="3cd95-117">Il ne peut pas s’agir du résultat d’une commande appelée.</span><span class="sxs-lookup"><span data-stu-id="3cd95-117">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="3cd95-118">Les énumérations prennent en charge les opérations arithmétiques, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3cd95-118">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="3cd95-119">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="3cd95-119">Import-DscResource</span></span>

<span data-ttu-id="3cd95-120">`Import-DscResource` est maintenant un mot clé véritablement dynamique.</span><span class="sxs-lookup"><span data-stu-id="3cd95-120">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="3cd95-121">PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="3cd95-121">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="3cd95-122">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="3cd95-122">ImplementingAssembly</span></span>

<span data-ttu-id="3cd95-123">Un nouveau champ, **ImplementingAssembly**, a été ajouté à **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="3cd95-123">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="3cd95-124">Elle a comme valeur l’assembly dynamique créé pour un module de script si le script définit des classes, ou l’assembly chargé pour les modules binaires.</span><span class="sxs-lookup"><span data-stu-id="3cd95-124">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="3cd95-125">Il n’est pas défini quand **ModuleType** a la valeur **Manifest**.</span><span class="sxs-lookup"><span data-stu-id="3cd95-125">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="3cd95-126">La réflexion sur le champ **ImplementingAssembly** découvre des ressources dans un module.</span><span class="sxs-lookup"><span data-stu-id="3cd95-126">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="3cd95-127">Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.</span><span class="sxs-lookup"><span data-stu-id="3cd95-127">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

## <a name="further-reading"></a><span data-ttu-id="3cd95-128">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3cd95-128">Further reading</span></span>

- [<span data-ttu-id="3cd95-129">À propos des classes</span><span class="sxs-lookup"><span data-stu-id="3cd95-129">about_Classes</span></span>](/powershell/module/microsoft.powershell.core/about/about_classes)
- [<span data-ttu-id="3cd95-130">À propos de l’énumération</span><span class="sxs-lookup"><span data-stu-id="3cd95-130">about_Enum</span></span>](/powershell/module/microsoft.powershell.core/about/about_enum)
- [<span data-ttu-id="3cd95-131">À propos des classes et de DSC</span><span class="sxs-lookup"><span data-stu-id="3cd95-131">about_Classes_and_DSC</span></span>](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
