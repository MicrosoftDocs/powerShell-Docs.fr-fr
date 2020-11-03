---
description: Explique comment créer des objets dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 8903af794c83e4c84709e3eeb21489557458e988
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208001"
---
# <a name="about-object-creation"></a><span data-ttu-id="6414c-104">À propos de la création d’objets</span><span class="sxs-lookup"><span data-stu-id="6414c-104">About Object Creation</span></span>

## <a name="short-description"></a><span data-ttu-id="6414c-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="6414c-105">Short description</span></span>

<span data-ttu-id="6414c-106">Explique comment créer des objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6414c-106">Explains how to create objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="6414c-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="6414c-107">Long description</span></span>

<span data-ttu-id="6414c-108">Vous pouvez créer des objets dans PowerShell et utiliser les objets que vous créez dans les commandes et les scripts.</span><span class="sxs-lookup"><span data-stu-id="6414c-108">You can create objects in PowerShell and use the objects that you create in commands and scripts.</span></span>

<span data-ttu-id="6414c-109">Il existe plusieurs façons de créer des objets, cette liste n’est pas définitive :</span><span class="sxs-lookup"><span data-stu-id="6414c-109">There are many ways to create objects, this list is not definitive:</span></span>

- <span data-ttu-id="6414c-110">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): crée une instance d’un objet .NET Framework ou d’un objet com.</span><span class="sxs-lookup"><span data-stu-id="6414c-110">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): Creates an instance of a .NET Framework object or COM object.</span></span>
- <span data-ttu-id="6414c-111">[Importation-CSV](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): crée des objets personnalisés ( **PSCustomObject** ) à partir des éléments définis comme valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="6414c-111">[Import-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv)/
  [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): Creates custom objects ( **PSCustomObject** ) from the items defined as comma separated values.</span></span>
- <span data-ttu-id="6414c-112">[ConvertFrom-JSON](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): crée des objets personnalisés définis en JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="6414c-112">[ConvertFrom-Json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): Creates custom objects defined in JavaScript Object Notation (JSON).</span></span>
- <span data-ttu-id="6414c-113">[ConvertFrom-String](xref:Microsoft.PowerShell.Utility.ConvertFrom-String): reposant sur [FlashExtract](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples), `ConvertFrom-String` crée des objets personnalisés à partir de données de chaîne structurées.</span><span class="sxs-lookup"><span data-stu-id="6414c-113">[ConvertFrom-String](xref:Microsoft.PowerShell.Utility.ConvertFrom-String): Built on top of [FlashExtract](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples), `ConvertFrom-String` creates custom objects from structured string data.</span></span>
  <span data-ttu-id="6414c-114">Cette rubrique illustre et décrit chacune de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="6414c-114">This topic will demonstrate and discuss each of these methods.</span></span>
- <span data-ttu-id="6414c-115">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): crée des objets personnalisés définis en tant que paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="6414c-115">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): Creates custom objects defined as key value pairs.</span></span>
- <span data-ttu-id="6414c-116">[Add-type](xref:Microsoft.PowerShell.Utility.Add-Type): vous permet de définir une classe dans votre session PowerShell avec laquelle vous pouvez effectuer une instanciation `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="6414c-116">[Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type): Allows you to define a class in your PowerShell session that you can instantiate with `New-Object`.</span></span>
- <span data-ttu-id="6414c-117">[New-module](xref:Microsoft.PowerShell.Core.New-Module): le paramètre **AsCustomObject** crée un objet personnalisé que vous définissez à l’aide du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="6414c-117">[New-Module](xref:Microsoft.PowerShell.Core.New-Module): The **AsCustomObject** parameter creates a custom object you define using script block.</span></span>
- <span data-ttu-id="6414c-118">[Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): ajoute des propriétés aux objets existants.</span><span class="sxs-lookup"><span data-stu-id="6414c-118">[Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): Adds properties to existing objects.</span></span> <span data-ttu-id="6414c-119">Vous pouvez utiliser `Add-Member` pour créer un objet personnalisé à partir d’un type simple, comme `[System.Int32]` .</span><span class="sxs-lookup"><span data-stu-id="6414c-119">You can use `Add-Member` to create a custom object out of a simple type, like `[System.Int32]`.</span></span>
- <span data-ttu-id="6414c-120">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): sélectionne des propriétés sur un objet.</span><span class="sxs-lookup"><span data-stu-id="6414c-120">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): Selects properties on an object.</span></span> <span data-ttu-id="6414c-121">Vous pouvez utiliser `Select-Object` pour créer des propriétés personnalisées et calculées sur un objet déjà instancié.</span><span class="sxs-lookup"><span data-stu-id="6414c-121">You can use `Select-Object` to create custom and calculated properties on an already instantiated object.</span></span>

<span data-ttu-id="6414c-122">Les méthodes supplémentaires suivantes sont traitées dans cet article :</span><span class="sxs-lookup"><span data-stu-id="6414c-122">The following additional methods are covered in this article:</span></span>

- <span data-ttu-id="6414c-123">En appelant le constructeur d’un type à l’aide d’une `new()` méthode statique</span><span class="sxs-lookup"><span data-stu-id="6414c-123">By calling a type's constructor using a static `new()` method</span></span>
- <span data-ttu-id="6414c-124">Par Cast tables de hachage des noms de propriété et des valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="6414c-124">By typecasting hash tables of property names and property values</span></span>

## <a name="static-new-method"></a><span data-ttu-id="6414c-125">Méthode static New ()</span><span class="sxs-lookup"><span data-stu-id="6414c-125">Static new() method</span></span>

<span data-ttu-id="6414c-126">Tous les types .NET ont une `new()` méthode qui vous permet de construire des instances plus facilement.</span><span class="sxs-lookup"><span data-stu-id="6414c-126">All .NET types have a `new()` method that allows you to construct instances more easily.</span></span> <span data-ttu-id="6414c-127">Vous pouvez également voir tous les constructeurs disponibles pour un type donné.</span><span class="sxs-lookup"><span data-stu-id="6414c-127">You can also see all the available constructors for a given type.</span></span>

<span data-ttu-id="6414c-128">Pour afficher les constructeurs d’un type, spécifiez le `new` nom de la méthode après le nom de type et appuyez sur `<ENTER>` .</span><span class="sxs-lookup"><span data-stu-id="6414c-128">To see the constructors for a type, specify the `new` method name after the type name and press `<ENTER>`.</span></span>

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

<span data-ttu-id="6414c-129">À présent, vous pouvez créer un **System. Uri** en spécifiant le constructeur approprié.</span><span class="sxs-lookup"><span data-stu-id="6414c-129">Now, you can create a **System.Uri** by specifying the appropriate constructor.</span></span>

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

<span data-ttu-id="6414c-130">Vous pouvez utiliser l’exemple suivant pour déterminer les types .NET actuellement chargés pour l’instanciation.</span><span class="sxs-lookup"><span data-stu-id="6414c-130">You can use the following sample to determine what .NET types are currently loaded for you to instantiate.</span></span>

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

<span data-ttu-id="6414c-131">Les objets créés à l’aide de la `new()` méthode peuvent ne pas avoir les mêmes propriétés que les objets du même type qui sont créés par les applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6414c-131">Objects created using the `new()` method may not have the same properties as objects of the same type that are created by PowerShell cmdlets.</span></span> <span data-ttu-id="6414c-132">Les applets de commande PowerShell, les fournisseurs et le système de type étendu peuvent ajouter des propriétés supplémentaires à l’instance.</span><span class="sxs-lookup"><span data-stu-id="6414c-132">PowerShell cmdlets, providers, and Extended Type System can add extra properties to the instance.</span></span>

<span data-ttu-id="6414c-133">Par exemple, le fournisseur FileSystem dans PowerShell ajoute six valeurs **NoteProperty** à l’objet **DirectoryInfo** retourné par `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="6414c-133">For example, the FileSystem provider in PowerShell adds six **NoteProperty** values to the **DirectoryInfo** object returned by `Get-Item`.</span></span>

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="6414c-134">Lorsque vous créez un objet **DirectoryInfo** directement, il ne possède pas ces six valeurs **NoteProperty** .</span><span class="sxs-lookup"><span data-stu-id="6414c-134">When you create a **DirectoryInfo** object directly, it does not have those six **NoteProperty** values.</span></span>

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="6414c-135">Pour plus d’informations sur le système de type étendu, consultez [about_Types.ps1XML](about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="6414c-135">For more information about the Extended Type System, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

<span data-ttu-id="6414c-136">Cette fonctionnalité a été ajoutée dans PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="6414c-136">This feature was added in PowerShell 5.0</span></span>

## <a name="create-objects-from-hash-tables"></a><span data-ttu-id="6414c-137">Créer des objets à partir de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="6414c-137">Create objects from hash tables</span></span>

<span data-ttu-id="6414c-138">Vous pouvez créer un objet à partir d’une table de hachage de propriétés et de valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="6414c-138">You can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="6414c-139">La syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6414c-139">The syntax is as follows:</span></span>

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="6414c-140">Cette méthode fonctionne uniquement pour les classes qui ont un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="6414c-140">This method works only for classes that have a parameterless constructor.</span></span> <span data-ttu-id="6414c-141">Les propriétés de l’objet doivent être publiques et définissables.</span><span class="sxs-lookup"><span data-stu-id="6414c-141">The object properties must be public and settable.</span></span>

<span data-ttu-id="6414c-142">Cette fonctionnalité a été ajoutée dans PowerShell version 3,0</span><span class="sxs-lookup"><span data-stu-id="6414c-142">This feature was added in PowerShell version 3.0</span></span>

## <a name="create-custom-objects-from-hash-tables"></a><span data-ttu-id="6414c-143">Créer des objets personnalisés à partir de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="6414c-143">Create custom objects from hash tables</span></span>

<span data-ttu-id="6414c-144">Les objets personnalisés sont très utiles et sont faciles à créer à l’aide de la méthode de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="6414c-144">Custom objects are very useful and are easy to create using the hash table method.</span></span> <span data-ttu-id="6414c-145">La classe **PSCustomObject** est spécifiquement conçue à cet effet.</span><span class="sxs-lookup"><span data-stu-id="6414c-145">The **PSCustomObject** class is designed specifically for this purpose.</span></span>

<span data-ttu-id="6414c-146">Les objets personnalisés sont un excellent moyen de retourner une sortie personnalisée à partir d’une fonction ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="6414c-146">Custom objects are an excellent way to return customized output from a function or script.</span></span> <span data-ttu-id="6414c-147">Cela est plus utile que le renvoi d’une sortie mise en forme qui ne peut pas être reformatée ou redirigée vers d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="6414c-147">This is more useful than returning formatted output that cannot be reformatted or piped to other commands.</span></span>

<span data-ttu-id="6414c-148">Les commandes dans le `Test-Object function` définissent des valeurs de variables, puis utilisent ces valeurs pour créer un objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6414c-148">The commands in the `Test-Object function` set some variable values and then use those values to create a custom object.</span></span> <span data-ttu-id="6414c-149">Vous pouvez voir cet objet en cours d’utilisation dans la section exemple de la rubrique d’aide de l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="6414c-149">You can see this object in use in the example section of the `Update-Help` cmdlet help topic.</span></span>

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

<span data-ttu-id="6414c-150">La sortie de cette fonction est une collection d’objets personnalisés sous forme de table par défaut.</span><span class="sxs-lookup"><span data-stu-id="6414c-150">The output of this function is a collection of custom objects formatted as a table by default.</span></span>

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

<span data-ttu-id="6414c-151">Les utilisateurs peuvent gérer les propriétés des objets personnalisés de la même manière qu’avec les objets standard.</span><span class="sxs-lookup"><span data-stu-id="6414c-151">Users can manage the properties of the custom objects just as they do with standard objects.</span></span>

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a><span data-ttu-id="6414c-152">Créer des objets non personnalisés à partir de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="6414c-152">Create non-custom objects from hash tables</span></span>

<span data-ttu-id="6414c-153">Vous pouvez également utiliser des tables de hachage pour créer des objets pour les classes non personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6414c-153">You can also use hash tables to create objects for non-custom classes.</span></span> <span data-ttu-id="6414c-154">Lorsque vous créez un objet pour une classe non personnalisée, le nom de type qualifié par un espace de noms est obligatoire, même si vous pouvez omettre un composant d’espace de noms **système** initial.</span><span class="sxs-lookup"><span data-stu-id="6414c-154">When you create an object for a non-custom class, the namespace-qualified type name is required, although you may omit any initial **System** namespace component.</span></span>

<span data-ttu-id="6414c-155">Par exemple, la commande suivante crée un objet d’option de session.</span><span class="sxs-lookup"><span data-stu-id="6414c-155">For example, the following command creates a session option object.</span></span>

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

<span data-ttu-id="6414c-156">Les exigences de la fonctionnalité de table de hachage, en particulier l’exigence de constructeur sans paramètre, éliminent de nombreuses classes existantes.</span><span class="sxs-lookup"><span data-stu-id="6414c-156">The requirements of the hash table feature, especially the parameterless constructor requirement, eliminate many existing classes.</span></span> <span data-ttu-id="6414c-157">Toutefois, la plupart des classes d' _options_ PowerShell sont conçues pour fonctionner avec cette fonctionnalité, ainsi que d’autres classes très utiles, telles que la classe **ProcessStartInfo** .</span><span class="sxs-lookup"><span data-stu-id="6414c-157">However, most PowerShell _option_ classes are designed to work with this feature, as well as other very useful classes, such as the **ProcessStartInfo** class.</span></span>

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

<span data-ttu-id="6414c-158">Vous pouvez également utiliser la fonctionnalité de table de hachage lors de la définition des valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6414c-158">You can also use the hash table feature when setting parameter values.</span></span> <span data-ttu-id="6414c-159">Par exemple, la valeur du paramètre **SessionOption** de `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6414c-159">For example, the value of the **SessionOption** parameter of the `New-PSSession`.</span></span>
<span data-ttu-id="6414c-160">une applet de commande peut être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="6414c-160">cmdlet can be a hash table.</span></span>

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a><span data-ttu-id="6414c-161">Objets génériques</span><span class="sxs-lookup"><span data-stu-id="6414c-161">Generic objects</span></span>

<span data-ttu-id="6414c-162">Vous pouvez également créer des objets génériques dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6414c-162">You can also create generic objects in PowerShell.</span></span> <span data-ttu-id="6414c-163">Les génériques sont des classes, des structures, des interfaces et des méthodes qui possèdent des espaces réservés (ou paramètres de type) pour un ou plusieurs des types qu'ils stockent ou utilisent.</span><span class="sxs-lookup"><span data-stu-id="6414c-163">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span>

<span data-ttu-id="6414c-164">L’exemple suivant crée un objet **dictionnaire** .</span><span class="sxs-lookup"><span data-stu-id="6414c-164">The following example creates a **Dictionary** object.</span></span>

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

<span data-ttu-id="6414c-165">Pour plus d’informations sur les génériques, consultez [génériques dans .net](/dotnet/standard/generics).</span><span class="sxs-lookup"><span data-stu-id="6414c-165">For more information on Generics, see [Generics in .NET](/dotnet/standard/generics).</span></span>

## <a name="see-also"></a><span data-ttu-id="6414c-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6414c-166">See also</span></span>

[<span data-ttu-id="6414c-167">about_Objects</span><span class="sxs-lookup"><span data-stu-id="6414c-167">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="6414c-168">about_Methods</span><span class="sxs-lookup"><span data-stu-id="6414c-168">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="6414c-169">about_Properties</span><span class="sxs-lookup"><span data-stu-id="6414c-169">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="6414c-170">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="6414c-170">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="6414c-171">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="6414c-171">about_Types.ps1xml</span></span>](about_Types.ps1xml.md)
