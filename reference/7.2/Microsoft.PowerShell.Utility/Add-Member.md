---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 4e9e5ec6d188bec0b4032151fb92e6995d8efbb8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603882"
---
# <span data-ttu-id="51c03-102">Add-Member</span><span class="sxs-lookup"><span data-stu-id="51c03-102">Add-Member</span></span>

## <span data-ttu-id="51c03-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="51c03-103">SYNOPSIS</span></span>
<span data-ttu-id="51c03-104">Ajoute des propriétés et des méthodes personnalisées à une instance d’un objet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51c03-104">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="51c03-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="51c03-105">SYNTAX</span></span>

### <span data-ttu-id="51c03-106">TypeNameSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="51c03-106">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="51c03-107">NotePropertyMultiMemberSet</span><span class="sxs-lookup"><span data-stu-id="51c03-107">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="51c03-108">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="51c03-108">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="51c03-109">PEL</span><span class="sxs-lookup"><span data-stu-id="51c03-109">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="51c03-110">Description</span><span class="sxs-lookup"><span data-stu-id="51c03-110">DESCRIPTION</span></span>

<span data-ttu-id="51c03-111">L' `Add-Member` applet de commande vous permet d’ajouter des membres (propriétés et méthodes) à une instance d’un objet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51c03-111">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="51c03-112">Par exemple, vous pouvez ajouter un membre NoteProperty qui contient une description de l’objet ou un membre **ScriptMethod** qui exécute un script pour modifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="51c03-112">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="51c03-113">Pour utiliser `Add-Member` , redirigez l’objet vers `Add-Member` ou utilisez le paramètre **InputObject** pour spécifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="51c03-113">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="51c03-114">Le paramètre **MemberType** indique le type de membre que vous souhaitez ajouter.</span><span class="sxs-lookup"><span data-stu-id="51c03-114">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="51c03-115">Le paramètre **Name** attribue un nom au nouveau membre et le paramètre **value** définit la valeur du membre.</span><span class="sxs-lookup"><span data-stu-id="51c03-115">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="51c03-116">Les propriétés et méthodes que vous ajoutez le sont uniquement à l'instance spécifique de l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="51c03-116">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="51c03-117">`Add-Member` ne modifie pas le type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="51c03-117">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="51c03-118">Pour créer un nouveau type d’objet, utilisez l’applet de commande `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="51c03-118">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="51c03-119">Vous pouvez également utiliser l' `Export-Clixml` applet de commande pour enregistrer l’instance de l’objet, y compris les membres supplémentaires, dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="51c03-119">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="51c03-120">Vous pouvez ensuite utiliser l' `Import-Clixml` applet de commande pour recréer l’instance de l’objet à partir des informations stockées dans le fichier exporté.</span><span class="sxs-lookup"><span data-stu-id="51c03-120">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="51c03-121">À compter de Windows PowerShell 3,0, `Add-Member` dispose de nouvelles fonctionnalités qui facilitent l’ajout de propriétés de note aux objets.</span><span class="sxs-lookup"><span data-stu-id="51c03-121">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="51c03-122">Vous pouvez utiliser les paramètres **NotePropertyName** et **NotePropertyValue** pour définir une propriété de note ou le paramètre **NotePropertyMembers**, qui utilise une table de hachage des noms et valeurs des propriétés de note.</span><span class="sxs-lookup"><span data-stu-id="51c03-122">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="51c03-123">Par ailleurs, à compter de Windows PowerShell 3.0, le paramètre **PassThru**, qui génère un objet de sortie, est moins utile.</span><span class="sxs-lookup"><span data-stu-id="51c03-123">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="51c03-124">`Add-Member` Ajoute désormais les nouveaux membres directement à l’objet d’entrée de plus de types.</span><span class="sxs-lookup"><span data-stu-id="51c03-124">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="51c03-125">Pour plus d'informations, consultez la description du paramètre **PassThru**.</span><span class="sxs-lookup"><span data-stu-id="51c03-125">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="51c03-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="51c03-126">EXAMPLES</span></span>

### <span data-ttu-id="51c03-127">Exemple 1 : ajouter une propriété de note à un PSObject</span><span class="sxs-lookup"><span data-stu-id="51c03-127">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="51c03-128">L’exemple suivant ajoute une propriété de note **Status** avec la valeur « Done » à l’objet **FileInfo** qui représente le `Test.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="51c03-128">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="51c03-129">La première commande utilise l' `Get-ChildItem` applet de commande pour obtenir un objet **FileInfo** représentant le `Test.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="51c03-129">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="51c03-130">Elle l’enregistre dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="51c03-130">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="51c03-131">La deuxième commande ajoute la propriété de note à l’objet dans `$a` .</span><span class="sxs-lookup"><span data-stu-id="51c03-131">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="51c03-132">La troisième commande utilise la notation par points pour récupérer la valeur de la propriété **Status** de l’objet dans `$a` .</span><span class="sxs-lookup"><span data-stu-id="51c03-132">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="51c03-133">Comme le montre la sortie, la valeur est « done ».</span><span class="sxs-lookup"><span data-stu-id="51c03-133">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="51c03-134">Exemple 2 : ajouter une propriété d’alias à un PSObject</span><span class="sxs-lookup"><span data-stu-id="51c03-134">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="51c03-135">L’exemple suivant ajoute une propriété d’alias de **taille** à l’objet qui représente le `Test.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="51c03-135">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="51c03-136">La nouvelle propriété est un alias de la propriété **Length** .</span><span class="sxs-lookup"><span data-stu-id="51c03-136">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="51c03-137">La première commande utilise l' `Get-ChildItem` applet de commande pour récupérer l' `Test.txt` objet **FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="51c03-137">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="51c03-138">La deuxième commande ajoute la propriété **Size** alias.</span><span class="sxs-lookup"><span data-stu-id="51c03-138">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="51c03-139">La troisième commande utilise la notation par points pour récupérer la valeur de la nouvelle propriété **Size** .</span><span class="sxs-lookup"><span data-stu-id="51c03-139">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="51c03-140">Exemple 3 : ajouter une propriété de note StringUse à une chaîne</span><span class="sxs-lookup"><span data-stu-id="51c03-140">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="51c03-141">Cet exemple ajoute la propriété de note **StringUse** à une chaîne.</span><span class="sxs-lookup"><span data-stu-id="51c03-141">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="51c03-142">Étant donné que `Add-Member` ne peut pas ajouter de types aux objets d’entrée de **chaîne** , vous pouvez spécifier le paramètre **PassThru** pour générer un objet de sortie.</span><span class="sxs-lookup"><span data-stu-id="51c03-142">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="51c03-143">La dernière commande de l'exemple affiche la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="51c03-143">The last command in the example displays the new property.</span></span>

<span data-ttu-id="51c03-144">Cet exemple utilise le paramètre **NotePropertyMembers** .</span><span class="sxs-lookup"><span data-stu-id="51c03-144">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="51c03-145">La valeur du paramètre **NotePropertyMembers** est une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="51c03-145">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="51c03-146">La clé est le nom de la propriété de note, **StringUse**, et la valeur est la valeur de la propriété de note, **Display**.</span><span class="sxs-lookup"><span data-stu-id="51c03-146">The key is the note property name, **StringUse**, and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="51c03-147">Exemple 4 : ajouter une méthode de script à un objet FileInfo</span><span class="sxs-lookup"><span data-stu-id="51c03-147">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="51c03-148">Cet exemple ajoute la méthode de script **SizeInMB** à un objet **FileInfo** qui calcule la taille du fichier au mégaoctet le plus proche.</span><span class="sxs-lookup"><span data-stu-id="51c03-148">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="51c03-149">La deuxième commande crée un **scriptblock** qui utilise la méthode statique **Round** du `[math]` type pour arrondir la taille du fichier à la deuxième décimale.</span><span class="sxs-lookup"><span data-stu-id="51c03-149">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="51c03-150">Le paramètre de **valeur** utilise également la `$This` variable automatique, qui représente l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="51c03-150">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="51c03-151">La `$This` variable est valide uniquement dans les blocs de script qui définissent de nouvelles propriétés et méthodes.</span><span class="sxs-lookup"><span data-stu-id="51c03-151">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="51c03-152">La dernière commande utilise la notation par points pour appeler la nouvelle méthode de script **SizeInMB** sur l’objet dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="51c03-152">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="51c03-153">Exemple 5 : copier toutes les propriétés d’un objet vers un autre</span><span class="sxs-lookup"><span data-stu-id="51c03-153">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="51c03-154">Cette fonction copie toutes les propriétés d'un objet dans un autre objet.</span><span class="sxs-lookup"><span data-stu-id="51c03-154">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="51c03-155">La `foreach` boucle utilise l' `Get-Member` applet de commande pour récupérer chacune des propriétés de l’objet **from** .</span><span class="sxs-lookup"><span data-stu-id="51c03-155">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="51c03-156">Les commandes de la `foreach` boucle sont exécutées en série sur chacune des propriétés.</span><span class="sxs-lookup"><span data-stu-id="51c03-156">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="51c03-157">La `Add-Member` commande ajoute la propriété de l’objet **from** à l’objet **to** en tant **que NoteProperty**.</span><span class="sxs-lookup"><span data-stu-id="51c03-157">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="51c03-158">La valeur est copiée à l’aide du paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="51c03-158">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="51c03-159">Elle utilise le paramètre **force** pour ajouter des membres avec le même nom de membre.</span><span class="sxs-lookup"><span data-stu-id="51c03-159">It uses the **Force** parameter to add members with the same member name.</span></span>

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### <span data-ttu-id="51c03-160">Exemple 6 : créer un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="51c03-160">Example 6: Create a custom object</span></span>

<span data-ttu-id="51c03-161">Cet exemple crée un objet personnalisé de **ressource** .</span><span class="sxs-lookup"><span data-stu-id="51c03-161">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="51c03-162">L' `New-Object` applet de commande crée un **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="51c03-162">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="51c03-163">L’exemple enregistre le **PSObject** dans la `$Asset` variable.</span><span class="sxs-lookup"><span data-stu-id="51c03-163">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="51c03-164">La deuxième commande utilise l' `[ordered]` accélérateur de type pour créer un dictionnaire ordonné de noms et de valeurs.</span><span class="sxs-lookup"><span data-stu-id="51c03-164">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="51c03-165">La commande enregistre le résultat dans la `$D` variable.</span><span class="sxs-lookup"><span data-stu-id="51c03-165">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="51c03-166">La troisième commande utilise le paramètre **NotePropertyMembers** de l' `Add-Member` applet de commande pour ajouter le dictionnaire dans la `$D` variable au **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="51c03-166">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="51c03-167">La propriété **TypeName** assigne un nouveau nom, **Asset**, au **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="51c03-167">The **TypeName** property assigns a new name, **Asset**, to the **PSObject**.</span></span>

<span data-ttu-id="51c03-168">La dernière commande envoie le nouvel objet **Asset** à l' `Get-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="51c03-168">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="51c03-169">La sortie indique que l’objet a un nom de type de **ressource** et les propriétés de note que nous avons définies dans le dictionnaire trié.</span><span class="sxs-lookup"><span data-stu-id="51c03-169">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## <span data-ttu-id="51c03-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51c03-170">PARAMETERS</span></span>

### <span data-ttu-id="51c03-171">-Force</span><span class="sxs-lookup"><span data-stu-id="51c03-171">-Force</span></span>

<span data-ttu-id="51c03-172">Indique que cette applet de commande ajoute un nouveau membre même si l’objet a un membre personnalisé portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="51c03-172">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="51c03-173">Vous ne pouvez pas utiliser le paramètre **force** pour remplacer un membre standard d’un type.</span><span class="sxs-lookup"><span data-stu-id="51c03-173">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-174">-InputObject</span><span class="sxs-lookup"><span data-stu-id="51c03-174">-InputObject</span></span>

<span data-ttu-id="51c03-175">Spécifie l'objet auquel le nouveau membre est ajouté.</span><span class="sxs-lookup"><span data-stu-id="51c03-175">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="51c03-176">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="51c03-176">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-177">-MemberType</span><span class="sxs-lookup"><span data-stu-id="51c03-177">-MemberType</span></span>

<span data-ttu-id="51c03-178">Spécifie le type du membre à ajouter.</span><span class="sxs-lookup"><span data-stu-id="51c03-178">Specifies the type of the member to add.</span></span>
<span data-ttu-id="51c03-179">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="51c03-179">This parameter is required.</span></span>
<span data-ttu-id="51c03-180">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="51c03-180">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="51c03-181">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="51c03-181">NoteProperty</span></span>
- <span data-ttu-id="51c03-182">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="51c03-182">AliasProperty</span></span>
- <span data-ttu-id="51c03-183">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="51c03-183">ScriptProperty</span></span>
- <span data-ttu-id="51c03-184">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="51c03-184">CodeProperty</span></span>
- <span data-ttu-id="51c03-185">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="51c03-185">ScriptMethod</span></span>
- <span data-ttu-id="51c03-186">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="51c03-186">CodeMethod</span></span>

<span data-ttu-id="51c03-187">Pour plus d’informations sur ces valeurs, consultez [énumération PSMemberTypes](/dotnet/api/system.management.automation.psmembertypes) dans le kit de développement logiciel (SDK) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51c03-187">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the PowerShell SDK.</span></span>

<span data-ttu-id="51c03-188">Certains objets n'ont pas chaque type de membre.</span><span class="sxs-lookup"><span data-stu-id="51c03-188">Not all objects have every type of member.</span></span>
<span data-ttu-id="51c03-189">Si vous spécifiez un type de membre que l’objet n’a pas, PowerShell retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="51c03-189">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-190">-Name</span><span class="sxs-lookup"><span data-stu-id="51c03-190">-Name</span></span>

<span data-ttu-id="51c03-191">Spécifie le nom du membre que cette applet de commande ajoute.</span><span class="sxs-lookup"><span data-stu-id="51c03-191">Specifies the name of the member that this cmdlet adds.</span></span>

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-192">-NotePropertyMembers</span><span class="sxs-lookup"><span data-stu-id="51c03-192">-NotePropertyMembers</span></span>

<span data-ttu-id="51c03-193">Spécifie une table de hachage ou un dictionnaire ordonné de valeurs et de noms de la propriété de note.</span><span class="sxs-lookup"><span data-stu-id="51c03-193">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="51c03-194">Tapez une table de hachage ou un dictionnaire dans lequel les clés sont les noms des propriétés de note et les valeurs sont celles des propriétés de note.</span><span class="sxs-lookup"><span data-stu-id="51c03-194">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="51c03-195">Pour plus d’informations sur les tables de hachage et les dictionnaires ordonnés dans PowerShell, consultez [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="51c03-195">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="51c03-196">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="51c03-196">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-197">-NotePropertyName</span><span class="sxs-lookup"><span data-stu-id="51c03-197">-NotePropertyName</span></span>

<span data-ttu-id="51c03-198">Spécifie le nom de la propriété de note.</span><span class="sxs-lookup"><span data-stu-id="51c03-198">Specifies the note property name.</span></span>

<span data-ttu-id="51c03-199">Utilisez ce paramètre avec le paramètre **NotePropertyValue**.</span><span class="sxs-lookup"><span data-stu-id="51c03-199">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="51c03-200">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="51c03-200">This parameter is optional.</span></span>

<span data-ttu-id="51c03-201">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="51c03-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-202">-NotePropertyValue</span><span class="sxs-lookup"><span data-stu-id="51c03-202">-NotePropertyValue</span></span>

<span data-ttu-id="51c03-203">Spécifie la valeur de la propriété de note.</span><span class="sxs-lookup"><span data-stu-id="51c03-203">Specifies the note property value.</span></span>

<span data-ttu-id="51c03-204">Utilisez ce paramètre avec le paramètre **NotePropertyName** .</span><span class="sxs-lookup"><span data-stu-id="51c03-204">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="51c03-205">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="51c03-205">This parameter is optional.</span></span>

<span data-ttu-id="51c03-206">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="51c03-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-207">-PassThru</span><span class="sxs-lookup"><span data-stu-id="51c03-207">-PassThru</span></span>

<span data-ttu-id="51c03-208">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="51c03-208">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="51c03-209">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="51c03-209">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="51c03-210">Pour la plupart des objets, `Add-Member` ajoute les nouveaux membres à l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="51c03-210">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="51c03-211">Toutefois, lorsque l’objet d’entrée est une chaîne, `Add-Member` ne peut pas ajouter le membre à l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="51c03-211">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="51c03-212">Pour ces objets, utilisez le paramètre **PassThru** pour créer un objet de sortie.</span><span class="sxs-lookup"><span data-stu-id="51c03-212">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="51c03-213">Dans Windows PowerShell 2,0, les `Add-Member` membres ont été ajoutés uniquement au wrapper **PSObject** d’objets, et non à l’objet.</span><span class="sxs-lookup"><span data-stu-id="51c03-213">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="51c03-214">Utilisez le paramètre **PassThru** pour créer un objet de sortie pour tout objet ayant un wrapper **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="51c03-214">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-215">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="51c03-215">-SecondValue</span></span>

<span data-ttu-id="51c03-216">Spécifie des informations supplémentaires facultatives sur les membres **AliasProperty**, **ScriptProperty**, **CodeProperty** ou **CodeMethod**.</span><span class="sxs-lookup"><span data-stu-id="51c03-216">Specifies optional additional information about **AliasProperty**, **ScriptProperty**, **CodeProperty**, or **CodeMethod** members.</span></span>

<span data-ttu-id="51c03-217">S’il est utilisé lors de l’ajout d’un **AliasProperty**, ce paramètre doit être un type de données.</span><span class="sxs-lookup"><span data-stu-id="51c03-217">If used when adding an **AliasProperty**, this parameter must be a data type.</span></span>
<span data-ttu-id="51c03-218">Une conversion vers le type de données spécifié est ajoutée à la valeur de **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="51c03-218">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="51c03-219">Par exemple, si vous ajoutez un **AliasProperty** qui fournit un autre nom pour une propriété de type chaîne, vous pouvez également spécifier un paramètre **SecondValue** de **System. Int32** pour indiquer que la valeur de cette propriété de chaîne doit être convertie en entier quand vous y accédez à l’aide du **AliasProperty** correspondant.</span><span class="sxs-lookup"><span data-stu-id="51c03-219">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="51c03-220">Vous pouvez utiliser le paramètre **SecondValue** pour spécifier un **scriptblock** supplémentaire lors de l’ajout d’un membre **ScriptProperty** .</span><span class="sxs-lookup"><span data-stu-id="51c03-220">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="51c03-221">Le premier **scriptblock**, spécifié dans le paramètre **value** , est utilisé pour obtenir la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="51c03-221">The first **ScriptBlock**, specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="51c03-222">Le deuxième **scriptblock**, spécifié dans le paramètre **SecondValue** , est utilisé pour définir la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="51c03-222">The second **ScriptBlock**, specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-223">-Value</span><span class="sxs-lookup"><span data-stu-id="51c03-223">-Value</span></span>

<span data-ttu-id="51c03-224">Spécifie la valeur initiale du membre ajouté.</span><span class="sxs-lookup"><span data-stu-id="51c03-224">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="51c03-225">Si vous ajoutez un membre **AliasProperty**, **CodeProperty**, **ScriptProperty** ou **CodeMethod** , vous pouvez fournir des informations supplémentaires facultatives à l’aide du paramètre **SecondValue** .</span><span class="sxs-lookup"><span data-stu-id="51c03-225">If you add an **AliasProperty**, **CodeProperty**, **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-226">-TypeName</span><span class="sxs-lookup"><span data-stu-id="51c03-226">-TypeName</span></span>

<span data-ttu-id="51c03-227">Spécifie un nom pour le type.</span><span class="sxs-lookup"><span data-stu-id="51c03-227">Specifies a name for the type.</span></span>

<span data-ttu-id="51c03-228">Quand le type est une classe dans l’espace de noms **système** ou un type qui a un accélérateur de type, vous pouvez entrer le nom abrégé du type.</span><span class="sxs-lookup"><span data-stu-id="51c03-228">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="51c03-229">Sinon, le nom de type complet est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="51c03-229">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="51c03-230">Ce paramètre est effectif uniquement lorsque l' **InputObject** est un **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="51c03-230">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="51c03-231">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="51c03-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c03-232">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51c03-232">CommonParameters</span></span>

<span data-ttu-id="51c03-233">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51c03-233">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51c03-234">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="51c03-234">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="51c03-235">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="51c03-235">INPUTS</span></span>

### <span data-ttu-id="51c03-236">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="51c03-236">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="51c03-237">Vous pouvez diriger tout type d’objet vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="51c03-237">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="51c03-238">SORTIES</span><span class="sxs-lookup"><span data-stu-id="51c03-238">OUTPUTS</span></span>

### <span data-ttu-id="51c03-239">None ou System. Object</span><span class="sxs-lookup"><span data-stu-id="51c03-239">None or System.Object</span></span>

<span data-ttu-id="51c03-240">Quand vous utilisez le paramètre **PassThru** , cette applet de commande retourne l’objet qui vient d’être étendu.</span><span class="sxs-lookup"><span data-stu-id="51c03-240">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="51c03-241">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="51c03-241">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="51c03-242">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="51c03-242">NOTES</span></span>

<span data-ttu-id="51c03-243">Vous pouvez ajouter des membres uniquement aux objets **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="51c03-243">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="51c03-244">Pour déterminer si un objet est un objet **PSObject** , utilisez l' `-is` opérateur.</span><span class="sxs-lookup"><span data-stu-id="51c03-244">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="51c03-245">Par exemple, pour tester un objet stocké dans la `$obj` variable, tapez `$obj -is [PSObject]` .</span><span class="sxs-lookup"><span data-stu-id="51c03-245">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="51c03-246">Les noms des paramètres **MemberType**, **Name**, **value** et **SecondValue** sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="51c03-246">The names of the **MemberType**, **Name**, **Value**, and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="51c03-247">Si vous omettez les noms de paramètres, les valeurs des paramètres sans nom doivent apparaître dans cet ordre : **MemberType**, **Name**, **value** et **SecondValue**.</span><span class="sxs-lookup"><span data-stu-id="51c03-247">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType**, **Name**, **Value**, and **SecondValue**.</span></span>

<span data-ttu-id="51c03-248">Si vous incluez les noms de paramètres, les paramètres peuvent apparaître dans tout ordre.</span><span class="sxs-lookup"><span data-stu-id="51c03-248">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="51c03-249">Vous pouvez utiliser la `$this` variable Automatic dans des blocs de script qui définissent les valeurs des nouvelles propriétés et méthodes.</span><span class="sxs-lookup"><span data-stu-id="51c03-249">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="51c03-250">La `$this` variable fait référence à l’instance de l’objet auquel les propriétés et les méthodes sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="51c03-250">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="51c03-251">Pour plus d’informations sur la `$this` variable, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="51c03-251">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="51c03-252">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="51c03-252">RELATED LINKS</span></span>

[<span data-ttu-id="51c03-253">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="51c03-253">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="51c03-254">Get-Member</span><span class="sxs-lookup"><span data-stu-id="51c03-254">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="51c03-255">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="51c03-255">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="51c03-256">New-Object</span><span class="sxs-lookup"><span data-stu-id="51c03-256">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="51c03-257">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="51c03-257">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)
