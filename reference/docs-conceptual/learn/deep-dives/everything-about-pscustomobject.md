---
title: Tout ce que vous avez toujours voulu savoir sur PSCustomObject
description: PSCustomObject est un moyen simple de créer des données structurées.
ms.date: 10/05/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 8086541bf93b4d3f878c9a3f7ca4300dc452a80b
ms.sourcegitcommit: 08c63095f54916013634d6703f2523779815f4b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99424469"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="fc0d6-103">Tout ce que vous avez toujours voulu savoir sur PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fc0d6-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="fc0d6-104">`PSCustomObject` est un très bon outil à ajouter à votre gamme d’outils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="fc0d6-105">Commençons par les concepts de base, puis nous passerons aux fonctionnalités plus avancées.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="fc0d6-106">L’idée sous-jacente de l’utilisation d’un `PSCustomObject` est d’avoir un moyen simple pour créer des données structurées.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="fc0d6-107">Jetez un coup d’œil au premier exemple et vous aurez une meilleure idée de ce que cela signifie.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="fc0d6-108">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="fc0d6-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="fc0d6-109">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="fc0d6-110">Consultez son blog sur [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="fc0d6-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="fc0d6-111">Création d’un PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fc0d6-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="fc0d6-112">J’aime bien utiliser `[PSCustomObject]` dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="fc0d6-113">La création d’un objet utilisable n’a jamais été aussi facile.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="fc0d6-114">Pour cette raison, je vais passer sous silence toutes les autres façons de créer un objet, mais je dois mentionner que la plupart de ces exemples sont en PowerShell 3.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="fc0d6-115">Cette méthode fonctionne bien pour moi, car j’utilise des tables de hachage pour à peu près tout.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="fc0d6-116">Mais il y a des fois où je voudrais que PowerShell traite les tables de hachage comme un objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="fc0d6-117">Là où vous remarquez d’abord la différence est quand vous voulez utiliser `Format-Table` ou `Export-CSV`, et que vous réalisez qu’une table de hachage est simplement une collection de paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="fc0d6-118">Vous pouvez ensuite accéder aux valeurs et les utiliser comme vous le feriez avec un objet normal.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="fc0d6-119">Conversion d’une table de hachage</span><span class="sxs-lookup"><span data-stu-id="fc0d6-119">Converting a hashtable</span></span>

<span data-ttu-id="fc0d6-120">Tant que nous traitons de ce sujet : savez-vous que vous pouvez faire ceci :</span><span class="sxs-lookup"><span data-stu-id="fc0d6-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="fc0d6-121">Je préfère créer l’objet entièrement, mais vous devez parfois utiliser d’abord une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="fc0d6-122">Cet exemple fonctionne, car le constructeur prend une table de hachage pour les propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="fc0d6-123">Il est important de remarquer que si cette méthode fonctionne, elle n’est pas exactement équivalente.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="fc0d6-124">La plus grande différence est que l’ordre des propriétés n’est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="fc0d6-125">Approche héritée</span><span class="sxs-lookup"><span data-stu-id="fc0d6-125">Legacy approach</span></span>

<span data-ttu-id="fc0d6-126">Vous avez peut-être vu des personnes utiliser `New-Object` pour créer des objets personnalisés.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="fc0d6-127">Cette façon de faire est un peu lente, mais elle peut être votre meilleure option sur les premières versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="fc0d6-128">Enregistrement dans un fichier</span><span class="sxs-lookup"><span data-stu-id="fc0d6-128">Saving to a file</span></span>

<span data-ttu-id="fc0d6-129">Je trouve que la meilleure façon d’enregistrer une table de hachage dans un fichier est de l’enregistrer au format JSON.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="fc0d6-130">Vous pouvez la réimporter dans un `[PSCustomObject]`</span><span class="sxs-lookup"><span data-stu-id="fc0d6-130">You can import it back into a `[PSCustomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1 | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="fc0d6-131">Je présente d’autres moyens d’enregistrer des objets dans un fichier dans mon article sur [Les nombreuses façons de lire et d’écrire des fichiers][].</span><span class="sxs-lookup"><span data-stu-id="fc0d6-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="fc0d6-132">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="fc0d6-133">Ajout de propriétés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-133">Adding properties</span></span>

<span data-ttu-id="fc0d6-134">Vous pouvez toujours ajouter de nouvelles propriétés à votre `PSCustomObject` avec `Add-Member`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name 'ID' -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="fc0d6-135">Supprimer des propriétés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-135">Remove properties</span></span>

<span data-ttu-id="fc0d6-136">Vous pouvez aussi supprimer des propriétés dans un objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="fc0d6-137">`psobject` est une propriété masquée qui vous permet d’accéder aux métadonnées de l’objet de base.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="fc0d6-138">Énumération des noms des propriétés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-138">Enumerating property names</span></span>

<span data-ttu-id="fc0d6-139">Vous avez parfois besoin d’une liste de tous les noms des propriétés sur un objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="fc0d6-140">Nous pouvons également obtenir cette même liste à partir de la propriété `psobject`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="fc0d6-141">Accès dynamique aux propriétés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-141">Dynamically accessing properties</span></span>

<span data-ttu-id="fc0d6-142">J’ai déjà mentionné que vous pouvez accéder directement aux valeurs des propriétés.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="fc0d6-143">Vous pouvez aussi utiliser une chaîne pour le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="fc0d6-144">Nous pouvons aller plus loin et utiliser une variable pour le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="fc0d6-145">Je sais que ça paraît étrange, mais cela fonctionne.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomobject-into-a-hashtable"></a><span data-ttu-id="fc0d6-146">Convertir PSCustomObject en table de hachage</span><span class="sxs-lookup"><span data-stu-id="fc0d6-146">Convert PSCustomObject into a hashtable</span></span>

<span data-ttu-id="fc0d6-147">Pour continuer à partir de la dernière section, vous pouvez parcourir dynamiquement les propriétés et créer une table de hachage à partir de celles-ci.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="fc0d6-148">Test des propriétés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-148">Testing for properties</span></span>

<span data-ttu-id="fc0d6-149">Si vous avez besoin de savoir si une propriété existe, vous pouvez simplement vérifier que cette propriété a une valeur.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="fc0d6-150">Toutefois, comme la valeur peut être `$null`, vous pouvez vérifier si elle existe en la recherchant dans `psobject.properties`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-150">But if the value could be `$null` you can check to see if it exists by checking the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID').Count )
```

## <a name="adding-object-methods"></a><span data-ttu-id="fc0d6-151">Ajout de méthodes d’objet</span><span class="sxs-lookup"><span data-stu-id="fc0d6-151">Adding object methods</span></span>

<span data-ttu-id="fc0d6-152">Si vous devez ajouter une méthode de script à un objet, vous pouvez le faire avec `Add-Member` et un `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="fc0d6-153">Vous devez utiliser la variable automatique `this` pour référencer l’objet actif.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="fc0d6-154">Voici un `scriptblock` pour transformer un objet en table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="fc0d6-155">(même code que dans le dernier exemple)</span><span class="sxs-lookup"><span data-stu-id="fc0d6-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="fc0d6-156">Ensuite, nous l’ajoutons à notre objet en tant que propriété de script.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="fc0d6-157">Nous pouvons ensuite appeler notre fonction comme suit :</span><span class="sxs-lookup"><span data-stu-id="fc0d6-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="fc0d6-158">Objets et types valeur</span><span class="sxs-lookup"><span data-stu-id="fc0d6-158">Objects vs Value types</span></span>

<span data-ttu-id="fc0d6-159">Les objets et les types valeur ne gèrent pas les affectations de variables de la même façon.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="fc0d6-160">Si vous affectez des types valeur entre eux, seule la valeur est copiée dans la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="fc0d6-161">Dans ce cas, `$first` vaut 1 et `$second` vaut 2.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="fc0d6-162">Les variables d’objet contiennent une référence à l’objet réel.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="fc0d6-163">Quand vous affectez un objet à une nouvelle variable, elle fait toujours référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="fc0d6-164">Comme `$third` et `$fourth` référencent la même instance d’un objet, `$third.key` et `$fourth.Key` valent tous deux 4.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="fc0d6-165">psobject.copy()</span><span class="sxs-lookup"><span data-stu-id="fc0d6-165">psobject.copy()</span></span>

<span data-ttu-id="fc0d6-166">Si vous avez besoin d’une copie réelle d’un objet, vous pouvez le cloner.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="fc0d6-167">Le clonage crée une copie superficielle de l’objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="fc0d6-168">Ils ont maintenant des instances différentes et dans cet exemple, `$third.key` vaut 3 et `$fourth.Key` vaut 4.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="fc0d6-169">J’appelle ceci une copie superficielle, car si vous avez des objets imbriqués</span><span class="sxs-lookup"><span data-stu-id="fc0d6-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="fc0d6-170">(où les propriétés contiennent d’autres objets),</span><span class="sxs-lookup"><span data-stu-id="fc0d6-170">(where the properties contain other objects).</span></span> <span data-ttu-id="fc0d6-171">seules les valeurs du plus haut niveau sont copiées.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-171">Only the top-level values are copied.</span></span> <span data-ttu-id="fc0d6-172">Les objets enfants se référencent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="fc0d6-173">PSTypeName pour les types d’objets personnalisés</span><span class="sxs-lookup"><span data-stu-id="fc0d6-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="fc0d6-174">Maintenant que nous disposons d’un objet, nous pouvons effectuer quelques autres opérations qui ne sont peut-être pas si évidentes.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="fc0d6-175">La première chose à faire est de lui donner un `PSTypeName`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="fc0d6-176">Voici comment je vois procéder la plupart des gens :</span><span class="sxs-lookup"><span data-stu-id="fc0d6-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="fc0d6-177">J’ai récemment découvert une autre façon de le faire à partir de ce [Posté par /u/markekraus][].</span><span class="sxs-lookup"><span data-stu-id="fc0d6-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="fc0d6-178">J’ai un peu investigué et j’ai trouvé d’autres billets sur l’idée de [Adam Bertram][] et [Mike Shepard][], où ils parlent de cette approche qui vous permet de le définir inline.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="fc0d6-179">J’aime bien la façon dont cela s’intègre parfaitement dans le langage.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="fc0d6-180">Maintenant que nous disposons d’un objet avec un nom de type correct, nous pouvons effectuer d’autres opérations.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

> [!NOTE]
> <span data-ttu-id="fc0d6-181">Vous pouvez également créer des types PowerShell personnalisés à l’aide de classes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-181">You can also create custom PowerShell types using PowerShell classes.</span></span> <span data-ttu-id="fc0d6-182">Pour plus d’informations, consultez [Présentation des classes PowerShell](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).</span><span class="sxs-lookup"><span data-stu-id="fc0d6-182">For more information, see [PowerShell Class Overview](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="fc0d6-183">Utilisation de DefaultPropertySet (la méthode longue)</span><span class="sxs-lookup"><span data-stu-id="fc0d6-183">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="fc0d6-184">PowerShell décide pour nous des propriétés à afficher par défaut.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-184">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="fc0d6-185">Un grand nombre de commandes natives ont un [fichier de mise en forme][] `.ps1xml` qui effectue tout ce gros travail de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-185">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="fc0d6-186">Selon ce [Posté par Boe Prox][], il existe un autre moyen d’effectuer cette opération sur notre objet personnalisé en utilisant simplement PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-186">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="fc0d6-187">Nous pouvons lui fournir un `MemberSet` qu’il va utiliser.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-187">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet('DefaultDisplayPropertySet',[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="fc0d6-188">Maintenant, quand mon objet apparaît dans le shell de commandes, il ne montre par défaut que ces seules propriétés.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-188">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="fc0d6-189">Update-TypeData avec DefaultPropertySet</span><span class="sxs-lookup"><span data-stu-id="fc0d6-189">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="fc0d6-190">C’est bien, mais j’ai récemment vu un meilleur moyen en regardant [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span><span class="sxs-lookup"><span data-stu-id="fc0d6-190">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="fc0d6-191">Jeffrey utilisait [Update-TypeData][] pour spécifier les propriétés par défaut.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-191">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="fc0d6-192">C’est tellement simple que je pourrais pratiquement m’en rappeler si je n’avais pas ce billet comme référence rapide.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-192">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="fc0d6-193">Je peux maintenant créer facilement des objets avec un grand nombre de propriétés et en avoir néanmoins une vue bien propre quand je les regarde dans le shell.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-193">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="fc0d6-194">Si j’ai besoin d’accéder à ces autres propriétés ou de les voir, elles sont cependant toujours là.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-194">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="fc0d6-195">Update-TypeData avec ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="fc0d6-195">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="fc0d6-196">Une autre chose que j’ai tirée de cette vidéo était la création de propriétés de script pour vos objets.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-196">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="fc0d6-197">C’est le bon moment pour souligner que cela fonctionne également pour les objets existants.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-197">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="fc0d6-198">Vous pouvez faire cela avant que votre objet soit créé ou bien après : cela fonctionne dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-198">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="fc0d6-199">Voici ce qui diffère de l’utilisation de `Add-Member` avec une propriété de script.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-199">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="fc0d6-200">Quand vous utilisez `Add-Member` de la façon dont j’ai parlé plus haut, il existe seulement sur cette instance spécifique de l’objet.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-200">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="fc0d6-201">Celui-ci s’applique à tous les objets avec ce `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-201">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="fc0d6-202">Paramètres de fonction</span><span class="sxs-lookup"><span data-stu-id="fc0d6-202">Function parameters</span></span>

<span data-ttu-id="fc0d6-203">Vous pouvez maintenant utiliser ces types personnalisés pour les paramètres dans vos fonctions et vos scripts.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-203">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="fc0d6-204">Vous pouvez avoir une fonction qui crée ces objets personnalisés, puis les passer à d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-204">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="fc0d6-205">PowerShell exige que l’objet soit du type que vous avez spécifié.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-205">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="fc0d6-206">Il génère une erreur de validation si le type ne correspond pas automatiquement, pour vous éviter de le tester dans votre code.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-206">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="fc0d6-207">Un bon exemple où on laisse PowerShell faire ce qu’il fait le mieux.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-207">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="fc0d6-208">OutputType pour les fonctions</span><span class="sxs-lookup"><span data-stu-id="fc0d6-208">Function OutputType</span></span>

<span data-ttu-id="fc0d6-209">Vous pouvez également définir un `OutputType` pour vos fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-209">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="fc0d6-210">La valeur de l’attribut **OutputType** n’est qu’une note de documentation.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-210">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="fc0d6-211">Elle n’est pas dérivée du code de la fonction et n’est pas comparée à la sortie réelle de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-211">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="fc0d6-212">La raison principale pour laquelle vous utilisez un type de sortie est de faire en sorte que les méta-informations sur votre fonction reflètent vos intentions.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-212">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="fc0d6-213">Par exemple, `Get-Command` et `Get-Help` peuvent en tirer parti dans votre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-213">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="fc0d6-214">Si vous voulez plus d’informations, consultez l’aide pour celui-ci : [about_Functions_OutputTypeAttribute][].</span><span class="sxs-lookup"><span data-stu-id="fc0d6-214">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="fc0d6-215">Cela dit, si vous utilisez Pester pour effectuer les tests unitaires de vos fonctions, il serait judicieux de vérifier que les objets en sortie correspondent à votre **OutputType**.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-215">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="fc0d6-216">Cela pourrait intercepter les variables qui arrivent dans le pipe alors qu’elles ne le devraient pas.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-216">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="fc0d6-217">Réflexions finales</span><span class="sxs-lookup"><span data-stu-id="fc0d6-217">Closing thoughts</span></span>

<span data-ttu-id="fc0d6-218">Le contexte de tout ceci concernait `[PSCustomObject]`, mais beaucoup de ces informations s’appliquent aux objets en général.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-218">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="fc0d6-219">J’ai vu la plupart de ces fonctionnalités en passant, mais je ne les avait jamais vues présentées sous la forme d’une collection d’informations sur `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-219">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="fc0d6-220">Pas plus tard que la semaine dernière, je suis tombé sur une autre fonctionnalité et j’ai été étonné de ne pas l’avoir déjà vue.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-220">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="fc0d6-221">Je voulais rassembler toutes ces idées pour vous en donner la vision la plus large possible et pour vous les faire découvrir si jamais vous avez l’occasion de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-221">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="fc0d6-222">J’espère que vous avez appris quelque chose et que vous pourrez vous en servir dans vos scripts.</span><span class="sxs-lookup"><span data-stu-id="fc0d6-222">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Posté par Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[Fichier de mise en forme]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[Les nombreuses façons de lire et d’écrire des fichiers]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[Posté par /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
