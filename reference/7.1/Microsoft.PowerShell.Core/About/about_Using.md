---
description: Vous permet d’indiquer les espaces de noms qui sont utilisés dans la session.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: eaf983ad03676b4ac57a3b35bc44f72036da55b4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207450"
---
# <a name="about-using"></a><span data-ttu-id="91ae3-104">À propos de l’utilisation de</span><span class="sxs-lookup"><span data-stu-id="91ae3-104">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="91ae3-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="91ae3-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="91ae3-106">Vous permet d’indiquer les espaces de noms qui sont utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="91ae3-106">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="91ae3-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="91ae3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="91ae3-108">L' `using` instruction vous permet de spécifier les espaces de noms qui sont utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="91ae3-108">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="91ae3-109">L’ajout d’espaces de noms simplifie l’utilisation des classes et membres .NET et vous permet d’importer des classes à partir de modules de script et d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="91ae3-109">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="91ae3-110">Les `using` instructions doivent précéder toutes les autres instructions dans un script.</span><span class="sxs-lookup"><span data-stu-id="91ae3-110">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="91ae3-111">L' `using` instruction ne doit pas être confondue avec le `using:` modificateur de portée pour les variables.</span><span class="sxs-lookup"><span data-stu-id="91ae3-111">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="91ae3-112">Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="91ae3-112">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="91ae3-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91ae3-113">Syntax</span></span>

<span data-ttu-id="91ae3-114">Pour spécifier des espaces de noms .NET à partir desquels résoudre les types :</span><span class="sxs-lookup"><span data-stu-id="91ae3-114">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="91ae3-115">Pour charger des classes à partir d’un module PowerShell :</span><span class="sxs-lookup"><span data-stu-id="91ae3-115">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="91ae3-116">Pour précharger des types à partir d’un assembly .NET :</span><span class="sxs-lookup"><span data-stu-id="91ae3-116">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="91ae3-117">La spécification d’un espace de noms facilite la référence des types par leurs noms courts.</span><span class="sxs-lookup"><span data-stu-id="91ae3-117">Specifying a namespace makes it easier to reference types by their short names.</span></span>

<span data-ttu-id="91ae3-118">Le chargement d’un assembly précharge les types .NET de cet assembly dans un script au moment de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="91ae3-118">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="91ae3-119">Cela vous permet de créer de nouvelles classes PowerShell qui utilisent des types de l’assembly préchargé.</span><span class="sxs-lookup"><span data-stu-id="91ae3-119">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="91ae3-120">Si vous ne créez pas de nouvelles classes PowerShell, utilisez `Add-Type` plutôt l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="91ae3-120">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="91ae3-121">Pour plus d’informations, consultez [Add-type](xref:Microsoft.PowerShell.Utility.Add-Type).</span><span class="sxs-lookup"><span data-stu-id="91ae3-121">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="91ae3-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="91ae3-122">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="91ae3-123">Exemple 1 : ajouter des espaces de noms pour la résolution TypeName</span><span class="sxs-lookup"><span data-stu-id="91ae3-123">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="91ae3-124">Le script suivant obtient le hachage de chiffrement pour la chaîne « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="91ae3-124">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="91ae3-125">Notez comment `using namespace System.Text` et `using namespace System.IO` simplifient les références à `[UnicodeEncoding]` dans `System.Text` et `[Stream]` et à `[MemoryStream]` dans `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="91ae3-125">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="91ae3-126">Exemple 2 : charger des classes à partir d’un module de script</span><span class="sxs-lookup"><span data-stu-id="91ae3-126">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="91ae3-127">Dans cet exemple, nous disposons d’un module de script PowerShell nommé **CardGames** qui définit les classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="91ae3-127">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="91ae3-128">**CardGames. Deck**</span><span class="sxs-lookup"><span data-stu-id="91ae3-128">**CardGames.Deck**</span></span>
- <span data-ttu-id="91ae3-129">**CardGames. carte**</span><span class="sxs-lookup"><span data-stu-id="91ae3-129">**CardGames.Card**</span></span>

<span data-ttu-id="91ae3-130">`Import-Module` et l' `#requires` instruction importent uniquement les fonctions de module, les alias et les variables, comme défini par le module.</span><span class="sxs-lookup"><span data-stu-id="91ae3-130">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="91ae3-131">Les classes ne sont pas importées.</span><span class="sxs-lookup"><span data-stu-id="91ae3-131">Classes are not imported.</span></span> <span data-ttu-id="91ae3-132">La `using module` commande importe le module et charge également les définitions de classe.</span><span class="sxs-lookup"><span data-stu-id="91ae3-132">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="91ae3-133">Exemple 3 : charger des classes à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="91ae3-133">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="91ae3-134">Cet exemple charge un assembly afin que ses classes puissent être utilisées pour créer de nouvelles classes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91ae3-134">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="91ae3-135">Le script suivant crée une nouvelle classe PowerShell dérivée de la classe **DirectoryContext** .</span><span class="sxs-lookup"><span data-stu-id="91ae3-135">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```

