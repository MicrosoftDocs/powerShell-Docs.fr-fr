---
description: Décrit comment utiliser les propriétés d’objet dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: 5c4efd3f94d8ce8fbb7c66db1cc5f91eebd0756e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206958"
---
# <a name="about-properties"></a><span data-ttu-id="64c06-104">À propos des propriétés</span><span class="sxs-lookup"><span data-stu-id="64c06-104">About Properties</span></span>

## <a name="short-description"></a><span data-ttu-id="64c06-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="64c06-105">Short description</span></span>
<span data-ttu-id="64c06-106">Décrit comment utiliser les propriétés d’objet dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c06-106">Describes how to use object properties in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="64c06-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="64c06-107">Long description</span></span>

<span data-ttu-id="64c06-108">PowerShell utilise des collections d’informations structurées appelées objets pour représenter les éléments des magasins de données ou l’état de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="64c06-108">PowerShell uses structured collections of information called objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="64c06-109">En général, vous travaillez avec des objets qui font partie de l’infrastructure Microsoft .NET, mais vous pouvez également créer des objets personnalisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c06-109">Typically, you work with object that are part of the Microsoft .NET Framework, but you can also create custom objects in PowerShell.</span></span>

<span data-ttu-id="64c06-110">L’association entre un élément et son objet est très proche.</span><span class="sxs-lookup"><span data-stu-id="64c06-110">The association between an item and its object is very close.</span></span> <span data-ttu-id="64c06-111">Lorsque vous modifiez un objet, vous modifiez généralement l’élément qu’il représente.</span><span class="sxs-lookup"><span data-stu-id="64c06-111">When you change an object, you usually change the item that it represents.</span></span> <span data-ttu-id="64c06-112">Par exemple, lorsque vous recevez un fichier dans PowerShell, vous n’avez pas le fichier réel.</span><span class="sxs-lookup"><span data-stu-id="64c06-112">For example, when you get a file in PowerShell, you do not get the actual file.</span></span> <span data-ttu-id="64c06-113">Au lieu de cela, vous recevez un objet FileInfo qui représente le fichier.</span><span class="sxs-lookup"><span data-stu-id="64c06-113">Instead, you get a FileInfo object that represents the file.</span></span> <span data-ttu-id="64c06-114">Lorsque vous modifiez l’objet FileInfo, le fichier change également.</span><span class="sxs-lookup"><span data-stu-id="64c06-114">When you change the FileInfo object, the file changes too.</span></span>

<span data-ttu-id="64c06-115">La plupart des objets ont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="64c06-115">Most objects have properties.</span></span> <span data-ttu-id="64c06-116">Les propriétés sont les données associées à un objet.</span><span class="sxs-lookup"><span data-stu-id="64c06-116">Properties are the data that is associated with an object.</span></span> <span data-ttu-id="64c06-117">Les différents types d’objets ont des propriétés différentes.</span><span class="sxs-lookup"><span data-stu-id="64c06-117">Different types of object have different properties.</span></span> <span data-ttu-id="64c06-118">Par exemple, un objet FileInfo, qui représente un fichier, a une propriété **IsReadOnly** qui contient $true si le fichier est l’attribut en lecture seule et $false si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="64c06-118">For example, a FileInfo object, which represents a file, has an **IsReadOnly** property that contains $True if the file the read-only attribute and $False if it does not.</span></span>
<span data-ttu-id="64c06-119">Un objet DirectoryInfo, qui représente un répertoire du système de fichiers, possède une propriété parente qui contient le chemin d’accès au répertoire parent.</span><span class="sxs-lookup"><span data-stu-id="64c06-119">A DirectoryInfo object, which represents a file system directory, has a Parent property that contains the path to the parent directory.</span></span>

### <a name="object-properties"></a><span data-ttu-id="64c06-120">Propriétés de l’objet</span><span class="sxs-lookup"><span data-stu-id="64c06-120">Object properties</span></span>

<span data-ttu-id="64c06-121">Pour récupérer les propriétés d’un objet, utilisez l' `Get-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="64c06-121">To get the properties of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="64c06-122">Par exemple, pour obtenir les propriétés d’un objet **FileInfo** , utilisez l' `Get-ChildItem` applet de commande pour obtenir l’objet FileInfo qui représente un fichier.</span><span class="sxs-lookup"><span data-stu-id="64c06-122">For example, to get the properties of a **FileInfo** object, use the `Get-ChildItem` cmdlet to get the FileInfo object that represents a file.</span></span> <span data-ttu-id="64c06-123">Utilisez ensuite un opérateur de pipeline (&#124;) pour envoyer l’objet **FileInfo** à `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="64c06-123">Then, use a pipeline operator (&#124;) to send the **FileInfo** object to `Get-Member`.</span></span> <span data-ttu-id="64c06-124">La commande suivante obtient le fichier PowerShell.exe et l’envoie à `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="64c06-124">The following command gets the PowerShell.exe file and sends it to `Get-Member`.</span></span>
<span data-ttu-id="64c06-125">La \$ variable automatique pshome contient le chemin d’accès du répertoire d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c06-125">The \$Pshome automatic variable contains the path of the PowerShell installation directory.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

<span data-ttu-id="64c06-126">La sortie de la commande répertorie les membres de l’objet **FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="64c06-126">The output of the command lists the members of the **FileInfo** object.</span></span>
<span data-ttu-id="64c06-127">Les membres incluent à la fois les propriétés et les méthodes.</span><span class="sxs-lookup"><span data-stu-id="64c06-127">Members include both properties and methods.</span></span> <span data-ttu-id="64c06-128">Lorsque vous travaillez dans PowerShell, vous avez accès à tous les membres des objets.</span><span class="sxs-lookup"><span data-stu-id="64c06-128">When you work in PowerShell, you have access to all the members of the objects.</span></span>

<span data-ttu-id="64c06-129">Pour obtenir uniquement les propriétés d’un objet et non les méthodes, utilisez le paramètre MemberType de l' `Get-Member` applet de commande avec la valeur « Property », comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="64c06-129">To get only the properties of an object and not the methods, use the MemberType parameter of the `Get-Member` cmdlet with a value of "property", as shown in the following example.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

<span data-ttu-id="64c06-130">Une fois que vous avez trouvé les propriétés, vous pouvez les utiliser dans vos commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c06-130">After you find the properties, you can use them in your PowerShell commands.</span></span>

## <a name="property-values"></a><span data-ttu-id="64c06-131">Valeurs de propriétés</span><span class="sxs-lookup"><span data-stu-id="64c06-131">Property values</span></span>

<span data-ttu-id="64c06-132">Bien que chaque objet d’un type spécifique ait les mêmes propriétés, les valeurs de ces propriétés décrivent l’objet particulier.</span><span class="sxs-lookup"><span data-stu-id="64c06-132">Although every object of a specific type has the same properties, the values of those properties describe the particular object.</span></span> <span data-ttu-id="64c06-133">Par exemple, chaque objet FileInfo a une propriété CreationTime, mais la valeur de cette propriété diffère pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="64c06-133">For example, every FileInfo object has a CreationTime property, but the value of that property differs for each file.</span></span>

<span data-ttu-id="64c06-134">La méthode la plus courante pour récupérer les valeurs des propriétés d’un objet consiste à utiliser la méthode point.</span><span class="sxs-lookup"><span data-stu-id="64c06-134">The most common way to get the values of the properties of an object is to use the dot method.</span></span> <span data-ttu-id="64c06-135">Tapez une référence à l’objet, telle qu’une variable qui contient l’objet ou une commande qui obtient l’objet.</span><span class="sxs-lookup"><span data-stu-id="64c06-135">Type a reference to the object, such as a variable that contains the object, or a command that gets the object.</span></span> <span data-ttu-id="64c06-136">Ensuite, tapez un point (.) suivi du nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="64c06-136">Then, type a dot (.) followed by the property name.</span></span>

<span data-ttu-id="64c06-137">Par exemple, la commande suivante affiche la valeur de la propriété CreationTime du fichier PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="64c06-137">For example, the following command displays the value of the CreationTime property of the PowerShell.exe file.</span></span> <span data-ttu-id="64c06-138">La `Get-ChildItem` commande retourne un objet FileInfo qui représente le fichier PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="64c06-138">The `Get-ChildItem` command returns a FileInfo object that represents the PowerShell.exe file.</span></span> <span data-ttu-id="64c06-139">La commande est placée entre parenthèses pour s’assurer qu’elle est exécutée avant l’accès à toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="64c06-139">The command is enclosed in parentheses to make sure that it is executed before any properties are accessed.</span></span> <span data-ttu-id="64c06-140">La `Get-ChildItem` commande est suivie d’un point et du nom de la propriété CreationTime, comme suit :</span><span class="sxs-lookup"><span data-stu-id="64c06-140">The `Get-ChildItem` command is followed by a dot and the name of the CreationTime property, as follows:</span></span>

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="64c06-141">Vous pouvez également enregistrer un objet dans une variable, puis obtenir ses propriétés à l’aide de la méthode point, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="64c06-141">You can also save an object in a variable and then get its properties by using the dot method, as shown in the following example:</span></span>

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="64c06-142">Vous pouvez également utiliser les `Select-Object` applets de commande et `Format-List` pour afficher les valeurs de propriété d’un objet.</span><span class="sxs-lookup"><span data-stu-id="64c06-142">You can also use the `Select-Object` and `Format-List` cmdlets to display the property values of an object.</span></span> <span data-ttu-id="64c06-143">`Select-Object` et `Format-List` ont chacun un paramètre de **propriété** .</span><span class="sxs-lookup"><span data-stu-id="64c06-143">`Select-Object` and `Format-List` each have a **Property** parameter.</span></span> <span data-ttu-id="64c06-144">Vous pouvez utiliser le paramètre **Property** pour spécifier une ou plusieurs propriétés et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="64c06-144">You can use the **Property** parameter to specify one or more properties and their values.</span></span> <span data-ttu-id="64c06-145">Vous pouvez utiliser le caractère générique ( \* ) pour représenter toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="64c06-145">Or, you can use the wildcard character (\*) to represent all the properties.</span></span>

<span data-ttu-id="64c06-146">Par exemple, la commande suivante affiche les valeurs de toutes les propriétés du fichier PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="64c06-146">For example, the following command displays the values of all the properties of the PowerShell.exe file.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a><span data-ttu-id="64c06-147">Propriétés statiques</span><span class="sxs-lookup"><span data-stu-id="64c06-147">Static properties</span></span>

<span data-ttu-id="64c06-148">Vous pouvez utiliser les propriétés statiques des classes .NET dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c06-148">You can use the static properties of .NET classes in PowerShell.</span></span> <span data-ttu-id="64c06-149">Les propriétés statiques sont des propriétés de classe, contrairement aux propriétés standard, qui sont des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="64c06-149">Static properties are properties of class, unlike standard properties, which are properties of an object.</span></span>

<span data-ttu-id="64c06-150">Pour récupérer les propriétés statiques d’une classe, utilisez le paramètre static de l’applet de commande Get-Member.</span><span class="sxs-lookup"><span data-stu-id="64c06-150">To get the static properties of an class, use the Static parameter of the Get-Member cmdlet.</span></span>

<span data-ttu-id="64c06-151">Par exemple, la commande suivante obtient les propriétés statiques de la `System.DateTime` classe.</span><span class="sxs-lookup"><span data-stu-id="64c06-151">For example, the following command gets the static properties of the `System.DateTime` class.</span></span>

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

<span data-ttu-id="64c06-152">Pour obtenir la valeur d’une propriété statique, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="64c06-152">To get the value of a static property, use the following syntax.</span></span>

```
[<ClassName>]::<Property>
```

<span data-ttu-id="64c06-153">Par exemple, la commande suivante obtient la valeur de la propriété statique UtcNow de la `System.DateTime` classe.</span><span class="sxs-lookup"><span data-stu-id="64c06-153">For example, the following command gets the value of the UtcNow static property of the `System.DateTime` class.</span></span>

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a><span data-ttu-id="64c06-154">Propriétés des collections et des objets scalaires</span><span class="sxs-lookup"><span data-stu-id="64c06-154">Properties of scalar objects and collections</span></span>

<span data-ttu-id="64c06-155">Les propriétés d’un objet (« scalaire ») d’un type particulier sont souvent différentes des propriétés d’une collection d’objets du même type.</span><span class="sxs-lookup"><span data-stu-id="64c06-155">The properties of one ("scalar") object of a particular type are often different from the properties of a collection of objects of the same type.</span></span>
<span data-ttu-id="64c06-156">Par exemple, chaque service possède la propriété **DisplayName** , mais une collection de services n’a pas de propriété **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="64c06-156">For example, every service has as **DisplayName** property, but a collection of services does not have a **DisplayName** property.</span></span>

<span data-ttu-id="64c06-157">La commande suivante obtient la valeur de la propriété **DisplayName** du service « audiosrv ».</span><span class="sxs-lookup"><span data-stu-id="64c06-157">The following command gets the value of the **DisplayName** property of the 'Audiosrv' service.</span></span>

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

<span data-ttu-id="64c06-158">À compter de PowerShell 3,0, PowerShell tente d’éviter les erreurs de script qui résultent des propriétés différentes des collections et des objets scalaires.</span><span class="sxs-lookup"><span data-stu-id="64c06-158">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing properties of scalar objects and collections.</span></span> <span data-ttu-id="64c06-159">La même commande retourne la valeur de la propriété **DisplayName** de chaque service `Get-Service` retourné par.</span><span class="sxs-lookup"><span data-stu-id="64c06-159">The same command returns the value of the **DisplayName** property of every service that `Get-Service` returns.</span></span>

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

<span data-ttu-id="64c06-160">Lorsque vous envoyez un regroupement, mais que vous demandez une propriété qui existe uniquement sur des objets (« scalaires ») uniques, PowerShell retourne la valeur de cette propriété pour chaque objet de la collection.</span><span class="sxs-lookup"><span data-stu-id="64c06-160">When you submit a collection, but request a property that exists only on single ("scalar") objects, PowerShell returns the value of that property for every object in the collection.</span></span>

<span data-ttu-id="64c06-161">Toutes les collections ont une propriété **Count** qui retourne le nombre d’objets présents dans la collection.</span><span class="sxs-lookup"><span data-stu-id="64c06-161">All collections have a **Count** property that returns how many objects are in the collection.</span></span>

```powershell
(Get-Service).Count
```

```output
176
```

<span data-ttu-id="64c06-162">À compter de PowerShell 3,0, si vous demandez la propriété Count ou length des objets zéro ou un objet, PowerShell retourne la valeur correcte.</span><span class="sxs-lookup"><span data-stu-id="64c06-162">Beginning in PowerShell 3.0, if you request the Count or Length property of zero objects or one object, PowerShell returns the correct value.</span></span>

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

<span data-ttu-id="64c06-163">Si une propriété existe sur les objets individuels et sur la collection, seule la propriété de la collection est retournée.</span><span class="sxs-lookup"><span data-stu-id="64c06-163">If a property exists on the individual objects and on the collection, only the collection's property is returned.</span></span>

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

<span data-ttu-id="64c06-164">Cette fonctionnalité fonctionne également sur les méthodes des objets scalaires et des collections.</span><span class="sxs-lookup"><span data-stu-id="64c06-164">This feature also works on methods of scalar objects and collections.</span></span> <span data-ttu-id="64c06-165">Pour plus d’informations, consultez [about_methods](about_methods.md).</span><span class="sxs-lookup"><span data-stu-id="64c06-165">For more information, see [about_Methods](about_methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64c06-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64c06-166">See also</span></span>

[<span data-ttu-id="64c06-167">about_Methods</span><span class="sxs-lookup"><span data-stu-id="64c06-167">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="64c06-168">about_Objects</span><span class="sxs-lookup"><span data-stu-id="64c06-168">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="64c06-169">Get-Member</span><span class="sxs-lookup"><span data-stu-id="64c06-169">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="64c06-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="64c06-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="64c06-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="64c06-171">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)
