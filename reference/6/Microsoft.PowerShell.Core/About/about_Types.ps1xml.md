---
description: Explique comment utiliser `Types.ps1xml` des fichiers pour étendre les types d’objets utilisés dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1xml
ms.openlocfilehash: 6b150626f41b61d4e91f20e7d5e93af04298369c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206829"
---
# <a name="about-typesps1xml"></a><span data-ttu-id="2fb7a-104">À propos de Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="2fb7a-104">About Types.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="2fb7a-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="2fb7a-105">Short description</span></span>
<span data-ttu-id="2fb7a-106">Explique comment utiliser `Types.ps1xml` des fichiers pour étendre les types d’objets utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-106">Explains how to use `Types.ps1xml` files to extend the types of objects that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2fb7a-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="2fb7a-107">Long description</span></span>

<span data-ttu-id="2fb7a-108">Les données de type étendus définissent des propriétés et des méthodes supplémentaires (« membres ») des types d’objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-108">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="2fb7a-109">Il existe deux techniques pour ajouter des données de type étendu à une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-109">There are two techniques for adding extended type data to a PowerShell session.</span></span>

- <span data-ttu-id="2fb7a-110">`Types.ps1xml` fichier : fichier XML qui définit les données de type étendu.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-110">`Types.ps1xml` file: An XML file that defines extended type data.</span></span>
- <span data-ttu-id="2fb7a-111">`Update-TypeData`: Applet de commande qui recharge des `Types.ps1xml` fichiers et définit des données étendues pour les types de la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-111">`Update-TypeData`: A cmdlet that reloads `Types.ps1xml` files and defines extended data for types in the current session.</span></span>

<span data-ttu-id="2fb7a-112">Cette rubrique décrit les `Types.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-112">This topic describes `Types.ps1xml` files.</span></span> <span data-ttu-id="2fb7a-113">Pour plus d’informations sur l’utilisation `Update-TypeData` de l’applet de commande pour ajouter des données de type étendu dynamique à la session active [, consultez Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-113">For more information about using the `Update-TypeData` cmdlet to add dynamic extended type data to the current session see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

## <a name="about-extended-type-data"></a><span data-ttu-id="2fb7a-114">À propos des données de type étendu</span><span class="sxs-lookup"><span data-stu-id="2fb7a-114">About extended type data</span></span>

<span data-ttu-id="2fb7a-115">Les données de type étendus définissent des propriétés et des méthodes supplémentaires (« membres ») des types d’objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-115">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="2fb7a-116">Vous pouvez étendre n’importe quel type pris en charge par PowerShell et utiliser les propriétés et les méthodes ajoutées de la même façon que vous utilisez les propriétés définies sur les types d’objets.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-116">You can extend any type that is supported by PowerShell and use the added properties and methods in the same way that you use the properties that are defined on the object types.</span></span>

<span data-ttu-id="2fb7a-117">Par exemple, PowerShell ajoute une propriété **DateTime** à tous les `System.DateTime` objets, tels que ceux que l' `Get-Date` applet de commande retourne.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-117">For example, PowerShell adds a **DateTime** property to all `System.DateTime` objects, such as the ones that the `Get-Date` cmdlet returns.</span></span>

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

<span data-ttu-id="2fb7a-118">Vous ne trouverez pas la propriété **DateTime** dans la description de la structure [System. DateTime](/dotnet/api/system.datetime) , car PowerShell ajoute la propriété et n’est visible que dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-118">You won't find the **DateTime** property in the description of the [System.DateTime](/dotnet/api/system.datetime) structure, because PowerShell adds the property and it is visible only in PowerShell.</span></span>

<span data-ttu-id="2fb7a-119">PowerShell définit en interne un ensemble de types étendus par défaut.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-119">PowerShell internally defines a default set of extended types.</span></span> <span data-ttu-id="2fb7a-120">Ces informations de type sont chargées dans chaque session PowerShell au démarrage.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-120">This type information is loaded in every PowerShell session at startup.</span></span> <span data-ttu-id="2fb7a-121">La propriété **DateTime** fait partie de cet ensemble par défaut.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-121">The **DateTime** property is part of this default set.</span></span> <span data-ttu-id="2fb7a-122">Avant PowerShell 6, les définitions de type étaient stockées `Types.ps1xml` dans le répertoire d’installation de PowerShell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-122">Prior to PowerShell 6, the type definitions were stored the `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`).</span></span>

## <a name="adding-extended-type-data-to-powershell"></a><span data-ttu-id="2fb7a-123">Ajout de données de type étendu à PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fb7a-123">Adding extended type data to PowerShell</span></span>

<span data-ttu-id="2fb7a-124">Il existe trois sources de données de type étendu dans les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-124">There are three sources of extended type data in PowerShell sessions.</span></span>

- <span data-ttu-id="2fb7a-125">Le défini par PowerShell et est chargé automatiquement dans chaque session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-125">The defined by PowerShell and is loaded automatically into every PowerShell session.</span></span> <span data-ttu-id="2fb7a-126">À partir de PowerShell 6, ces informations sont compilées dans PowerShell et ne sont plus fournies dans un `Types.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-126">Beginning with PowerShell 6, this information is compiled into PowerShell and is no longer shipped in a `Types.ps1xml` file.</span></span>

- <span data-ttu-id="2fb7a-127">Les `Types.ps1xml` fichiers que les modules exportent sont chargés quand le module est importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-127">The `Types.ps1xml` files that modules export are loaded when the module is imported into the current session.</span></span>

- <span data-ttu-id="2fb7a-128">Les données de type étendu qui sont définies à l’aide de l' `Update-TypeData` applet de commande sont ajoutées uniquement à la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-128">Extended type data that is defined by using the `Update-TypeData` cmdlet is added only to the current session.</span></span> <span data-ttu-id="2fb7a-129">Il n’est pas enregistré dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-129">It is not saved in a file.</span></span>

<span data-ttu-id="2fb7a-130">Dans la session, les données de type étendu des trois sources sont appliquées aux objets de la même façon et sont disponibles sur tous les objets des types spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-130">In the session, the extended type data from the three sources is applied to objects in the same way and is available on all objects of the specified types.</span></span>

## <a name="the-typedata-cmdlets"></a><span data-ttu-id="2fb7a-131">Applets de commande TypeData</span><span class="sxs-lookup"><span data-stu-id="2fb7a-131">The TypeData cmdlets</span></span>

<span data-ttu-id="2fb7a-132">Les applets de commande suivantes sont incluses dans le module **Microsoft. PowerShell. Utility** dans PowerShell 3,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-132">The following cmdlets are included in the **Microsoft.PowerShell.Utility** module in PowerShell 3.0 and later.</span></span>

- <span data-ttu-id="2fb7a-133">`Get-TypeData`: Obtient les données de type étendu dans la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-133">`Get-TypeData`: Gets extended type data in the current session.</span></span>
- <span data-ttu-id="2fb7a-134">`Update-TypeData`: Recharge les `Types.ps1xml` fichiers.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-134">`Update-TypeData`: Reloads `Types.ps1xml` files.</span></span> <span data-ttu-id="2fb7a-135">Ajoute des données de type étendu à la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-135">Adds extended type data to the current session.</span></span>
- <span data-ttu-id="2fb7a-136">`Remove-TypeData`: Supprime les données de type étendu de la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-136">`Remove-TypeData`: Removes extended type data from the current session.</span></span>

<span data-ttu-id="2fb7a-137">Pour plus d’informations sur ces applets de commande, consultez la rubrique d’aide pour chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-137">For more information about these cmdlets, see the help topic for each cmdlet.</span></span>

## <a name="built-in-typesps1xml-files"></a><span data-ttu-id="2fb7a-138">Fichiers XML Types.ps1intégrés</span><span class="sxs-lookup"><span data-stu-id="2fb7a-138">Built-in Types.ps1xml files</span></span>

<span data-ttu-id="2fb7a-139">Les `Types.ps1xml` fichiers du `$PSHOME` répertoire sont ajoutés automatiquement à chaque session.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-139">The `Types.ps1xml` files in the `$PSHOME` directory are added automatically to every session.</span></span>

<span data-ttu-id="2fb7a-140">Le `Types.ps1xml` fichier dans le répertoire d’installation de PowerShell ( `$PSHOME` ) est un fichier texte basé sur XML qui vous permet d’ajouter des propriétés et des méthodes aux objets utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-140">The `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`) is an XML-based text file that lets you add properties and methods to the objects that are used in PowerShell.</span></span> <span data-ttu-id="2fb7a-141">PowerShell contient des fichiers intégrés `Types.ps1xml` qui ajoutent plusieurs éléments aux types .net, mais vous pouvez créer des `Types.ps1xml` fichiers supplémentaires pour étendre davantage les types.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-141">PowerShell has built-in `Types.ps1xml` files that add several elements to the .NET types, but you can create additional `Types.ps1xml` files to further extend the types.</span></span>

<span data-ttu-id="2fb7a-142">Par exemple, par défaut, les objets de tableau ( `System.Array` ) ont une propriété **Length** qui indique le nombre d’objets dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-142">For example, by default, array objects (`System.Array`) have a **Length** property that lists the number of objects in the array.</span></span> <span data-ttu-id="2fb7a-143">Toutefois, étant donné que la **longueur** du nom ne décrit pas clairement la propriété, PowerShell ajoute une propriété d’alias **Count nommée Count** qui affiche la même valeur.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-143">However, because the name **Length** does not clearly describe the property, PowerShell adds an alias property named **Count** that displays the same value.</span></span> <span data-ttu-id="2fb7a-144">Le code XML suivant ajoute la propriété **Count** au `System.Array` type.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-144">The following XML adds the **Count** property to the `System.Array` type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-145">Pour obtenir le nouvel **AliasProperty** , utilisez une `Get-Member` commande sur n’importe quel tableau, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-145">To get the new **AliasProperty** , use a `Get-Member` command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="2fb7a-146">La commande retourne les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-146">The command returns the following results.</span></span>

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

<span data-ttu-id="2fb7a-147">Par conséquent, vous pouvez utiliser la propriété **Count** ou la propriété **Length** des tableaux dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-147">As a result, you can use either the **Count** property or the **Length** property of arrays in PowerShell.</span></span> <span data-ttu-id="2fb7a-148">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2fb7a-148">For example:</span></span>

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a><span data-ttu-id="2fb7a-149">Création de fichiers XML Types.ps1</span><span class="sxs-lookup"><span data-stu-id="2fb7a-149">Creating new Types.ps1xml files</span></span>

<span data-ttu-id="2fb7a-150">Les `.ps1xml` fichiers qui sont installés avec PowerShell sont signés numériquement pour empêcher la falsification, car la mise en forme peut inclure des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-150">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="2fb7a-151">Par conséquent, pour ajouter une propriété ou une méthode à un type .NET, créez vos propres `Types.ps1xml` fichiers, puis ajoutez-les à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-151">Therefore, to add a property or method to a .NET type, create your own `Types.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="2fb7a-152">Pour créer un nouveau fichier, commencez par copier un `Types.ps1xml` fichier existant.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-152">To create a new file, start by copying an existing `Types.ps1xml` file.</span></span> <span data-ttu-id="2fb7a-153">Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une `.ps1xml` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-153">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="2fb7a-154">Vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de PowerShell ( `$PSHOME` ) ou dans un sous-répertoire du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-154">You can place the new file in any directory that is accessible to PowerShell, but it is useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="2fb7a-155">Une fois que vous avez enregistré le nouveau fichier, utilisez l' `Update-TypeData` applet de commande pour ajouter le nouveau fichier à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-155">When you have saved the new file, use the `Update-TypeData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="2fb7a-156">Si vous souhaitez que vos types aient la priorité sur les types intégrés définis, utilisez le paramètre **PrependData** de l’applet de commande `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-156">If you want your types to take precedence over the built-in types that are defined, use the **PrependData** parameter of the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="2fb7a-157">`Update-TypeData` affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-157">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="2fb7a-158">Pour apporter la modification à toutes les sessions ultérieures, exportez la console ou ajoutez la `Update-TypeData` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-158">To make the change to all future sessions, export the console, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

## <a name="typesps1xml-and-add-member"></a><span data-ttu-id="2fb7a-159">Types.ps1XML et Add-Member</span><span class="sxs-lookup"><span data-stu-id="2fb7a-159">Types.ps1xml and Add-Member</span></span>

<span data-ttu-id="2fb7a-160">Les `Types.ps1xml` fichiers ajoutent des propriétés et des méthodes à toutes les instances des objets du type .net spécifié dans la session PowerShell concernée.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-160">The `Types.ps1xml` files add properties and methods to all the instances of the objects of the specified .NET type in the affected PowerShell session.</span></span> <span data-ttu-id="2fb7a-161">Toutefois, si vous devez ajouter des propriétés ou des méthodes uniquement à une instance d’un objet, utilisez l’applet de commande `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-161">However, if you need to add properties or methods only to one instance of an object, use the `Add-Member` cmdlet.</span></span>

<span data-ttu-id="2fb7a-162">Pour plus d’informations, consultez [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-162">For more information, see [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member).</span></span>

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a><span data-ttu-id="2fb7a-163">Exemple : ajout d’un membre Age à des objets FileInfo</span><span class="sxs-lookup"><span data-stu-id="2fb7a-163">Example: Adding an Age member to FileInfo objects</span></span>

<span data-ttu-id="2fb7a-164">Cet exemple montre comment ajouter une propriété **Age** aux objets **System. IO. FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-164">This example shows how to add an **Age** property to **System.IO.FileInfo** objects.</span></span> <span data-ttu-id="2fb7a-165">L’ancienneté d’un fichier correspond à la différence entre son heure de création et l’heure actuelle en jours.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-165">The age of a file is the difference between its creation time and the current time in days.</span></span>

<span data-ttu-id="2fb7a-166">Étant donné que la propriété **Age** est calculée à l’aide d’un bloc de script, recherchez une `<ScriptProperty>` balise à utiliser comme modèle pour la nouvelle propriété **Age** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-166">Because the **Age** property is calculated by using a script block, find a `<ScriptProperty>` tag to use as a model for the new **Age** property.</span></span>

<span data-ttu-id="2fb7a-167">Enregistrez le code XML suivant dans le fichier `$PSHOME\MyTypes.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-167">Save the follow XML code to the file `$PSHOME\MyTypes.ps1xml`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

<span data-ttu-id="2fb7a-168">Exécutez `Update-TypeData` pour ajouter le nouveau `Types.ps1xml` fichier à la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-168">Run `Update-TypeData` to add the new `Types.ps1xml` file to the current session.</span></span> <span data-ttu-id="2fb7a-169">La commande utilise le paramètre **PrependData** pour placer le nouveau fichier dans un ordre de priorité plus élevé que les définitions d’origine.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-169">The command uses the **PrependData** parameter to place the new file in a precedence order higher than the original definitions.</span></span>

<span data-ttu-id="2fb7a-170">Pour plus d’informations sur `Update-TypeData` , voir [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-170">For more information about `Update-TypeData`, see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

<span data-ttu-id="2fb7a-171">Pour tester la modification, exécutez une `Get-ChildItem` commande pour obtenir le PowerShell.exe fichier dans le `$PSHOME` répertoire, puis dirigez le fichier vers l' `Format-List` applet de commande pour répertorier toutes les propriétés du fichier.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-171">To test the change, run a `Get-ChildItem` command to get the PowerShell.exe file in the `$PSHOME` directory, and then pipe the file to the `Format-List` cmdlet to list all of the properties of the file.</span></span> <span data-ttu-id="2fb7a-172">Suite à la modification, la propriété **Age** apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-172">As a result of the change, the **Age** property appears in the list.</span></span>

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a><span data-ttu-id="2fb7a-173">XML dans Types.ps1fichiers XML</span><span class="sxs-lookup"><span data-stu-id="2fb7a-173">The XML in Types.ps1xml files</span></span>

<span data-ttu-id="2fb7a-174">La définition de schéma complète se trouve dans [types. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) dans le référentiel de code source PowerShell sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-174">The full schema definition can be found in [Types.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="2fb7a-175">La `<Types>` balise englobe tous les types définis dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-175">The `<Types>` tag encloses all of the types that are defined in the file.</span></span> <span data-ttu-id="2fb7a-176">Il ne doit y avoir qu’une seule `<Types>` balise.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-176">There should be only one `<Types>` tag.</span></span>

<span data-ttu-id="2fb7a-177">Chaque type .NET mentionné dans le fichier doit être représenté par une `<Type>` balise.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-177">Each .NET type mentioned in the file should be represented by a `<Type>` tag.</span></span>

<span data-ttu-id="2fb7a-178">Les balises de type doivent contenir les balises suivantes :</span><span class="sxs-lookup"><span data-stu-id="2fb7a-178">The type tags must contain the following tags:</span></span>

<span data-ttu-id="2fb7a-179">`<Name>`: Encadre le nom du type .NET affecté.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-179">`<Name>`: Encloses the name of the affected .NET type.</span></span>

<span data-ttu-id="2fb7a-180">`<Members>`: Encadre les balises pour les nouvelles propriétés et méthodes définies pour le type .NET.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-180">`<Members>`: Encloses the tags for the new properties and methods that are defined for the .NET type.</span></span>

<span data-ttu-id="2fb7a-181">Les balises de membre suivantes peuvent se trouver à l’intérieur de la `<Members>` balise.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-181">Any of the following member tags can be inside the `<Members>` tag.</span></span>

<span data-ttu-id="2fb7a-182">`<AliasProperty>`: Définit un nouveau nom pour une propriété existante.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-182">`<AliasProperty>`: Defines a new name for an existing property.</span></span>

<span data-ttu-id="2fb7a-183">La `<AliasProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<ReferencedMemberName>` balise qui spécifie la propriété existante.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-183">The `<AliasProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<ReferencedMemberName>` tag that specifies the existing property.</span></span>

<span data-ttu-id="2fb7a-184">Par exemple, la propriété **Count** alias est un alias pour la propriété **Length** des objets Array.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-184">For example, the **Count** alias property is an alias for the **Length** property of array objects.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-185">`<CodeMethod>`: Référence une méthode statique d’une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-185">`<CodeMethod>`:  References a static method of a .NET class.</span></span>

<span data-ttu-id="2fb7a-186">La `<CodeMethod>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle méthode et une `<GetCodeReference>` balise qui spécifie le code dans lequel la méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-186">The `<CodeMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<GetCodeReference>` tag that specifies the code in which the method is defined.</span></span>

<span data-ttu-id="2fb7a-187">Par exemple, la propriété **mode** d' `System.IO.DirectoryInfo` objets est une propriété de code définie dans le fournisseur de système de fichiers PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-187">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-188">`<CodeProperty>`: Référence une méthode statique d’une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-188">`<CodeProperty>`: References a static method of a .NET class.</span></span>

<span data-ttu-id="2fb7a-189">La `<CodeProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<GetCodeReference>` balise qui spécifie le code dans lequel la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-189">The `<CodeProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetCodeReference>` tag that specifies the code in which the property is defined.</span></span>

<span data-ttu-id="2fb7a-190">Par exemple, la propriété **mode** d' `System.IO.DirectoryInfo` objets est une propriété de code définie dans le fournisseur de système de fichiers PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-190">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-191">`<MemberSet>`: Définit une collection de membres (propriétés et méthodes).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-191">`<MemberSet>`: Defines a collection of members (properties and methods).</span></span>

<span data-ttu-id="2fb7a-192">Les `<MemberSet>` balises apparaissent dans les `<Members>` balises primaires.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-192">The `<MemberSet>` tags appear within the primary `<Members>` tags.</span></span> <span data-ttu-id="2fb7a-193">Les balises doivent contenir une `<Name>` balise entourant le nom de l’ensemble de membres et une `<Members>` balise secondaire qui entoure les membres (propriétés et méthodes) dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-193">The tags must enclose a `<Name>` tag surrounding the name of the member set and a secondary `<Members>` tag that surround the members (properties and methods) in the set.</span></span> <span data-ttu-id="2fb7a-194">Les balises qui créent une propriété (telle que `<NoteProperty>` ou `<ScriptProperty>` ) ou une méthode (telle que `<Method>` ou `<ScriptMethod>` ) peuvent être membres du jeu.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-194">Any of the tags that create a property (such as `<NoteProperty>` or `<ScriptProperty>`) or a method (such as `<Method>` or `<ScriptMethod>`) can be members of the set.</span></span>

<span data-ttu-id="2fb7a-195">Dans `Types.ps1xml` les fichiers, la `<MemberSet>` balise est utilisée pour définir les vues par défaut des objets .net dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-195">In `Types.ps1xml` files, the `<MemberSet>` tag is used to define the default views of the .NET objects in PowerShell.</span></span> <span data-ttu-id="2fb7a-196">Dans ce cas, le nom du jeu de membres (la valeur dans les `<Name>` balises) est toujours **PsStandardMembers** et les noms des propriétés (la valeur de la `<Name>` balise) sont l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2fb7a-196">In this case, the name of the member set (the value within the `<Name>` tags) is always **PsStandardMembers** , and the names of the properties (the value of the `<Name>` tag) are one of the following:</span></span>

- <span data-ttu-id="2fb7a-197">`DefaultDisplayProperty`: Propriété unique d’un objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-197">`DefaultDisplayProperty`: A single property of an object.</span></span>

- <span data-ttu-id="2fb7a-198">`DefaultDisplayPropertySet`: Une ou plusieurs propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-198">`DefaultDisplayPropertySet`: One or more properties of an object.</span></span>

- <span data-ttu-id="2fb7a-199">`DefaultKeyPropertySet`: Une ou plusieurs propriétés clés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-199">`DefaultKeyPropertySet`: One or more key properties of an object.</span></span> <span data-ttu-id="2fb7a-200">Une propriété de clé identifie des instances de valeurs de propriété, telles que le nombre d’ID d’éléments dans un historique de session.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-200">A key property identifies instances of property values, such as the ID number of items in a session history.</span></span>

<span data-ttu-id="2fb7a-201">Par exemple, le code XML suivant définit l’affichage par défaut des services ( `System.ServiceProcess.ServiceController` objets) retournés par l’applet de commande `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-201">For example, the following XML defines the default display of services (`System.ServiceProcess.ServiceController` objects) that are returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="2fb7a-202">Il définit un jeu de membres nommé **PsStandardMembers** qui se compose d’une propriété par défaut définie avec les propriétés **Status** , **Name** et **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-202">It defines a member set named **PsStandardMembers** that consists of a default property set with the **Status** , **Name** , and **DisplayName** properties.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-203">`<Method>`: Référence une méthode native de l’objet sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-203">`<Method>`: References a native method of the underlying object.</span></span>

<span data-ttu-id="2fb7a-204">`<Methods>`: Collection des méthodes de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-204">`<Methods>`: A collection of the methods of the object.</span></span>

<span data-ttu-id="2fb7a-205">`<NoteProperty>`: Définit une propriété avec une valeur statique.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-205">`<NoteProperty>`: Defines a property with a static value.</span></span>

<span data-ttu-id="2fb7a-206">La `<NoteProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<Value>` balise qui spécifie la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-206">The `<NoteProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<Value>` tag that specifies the value of the property.</span></span>

<span data-ttu-id="2fb7a-207">Par exemple, le code XML suivant crée une propriété **Status** pour les objets **System. IO. DirectoryInfo** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-207">For example, the following XML creates a **Status** property for **System.IO.DirectoryInfo** objects.</span></span> <span data-ttu-id="2fb7a-208">La valeur de la propriété **Status** est toujours **Success** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-208">The value of the **Status** property is always **Success** .</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-209">`<ParameterizedProperty>`: Les propriétés qui acceptent des arguments et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-209">`<ParameterizedProperty>`: Properties that take arguments and return a value.</span></span>

<span data-ttu-id="2fb7a-210">`<Properties>`: Collection des propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-210">`<Properties>`: A collection of the properties of the object.</span></span>

<span data-ttu-id="2fb7a-211">`<Property>`: Propriété de l’objet de base.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-211">`<Property>`: A property of the base object.</span></span>

<span data-ttu-id="2fb7a-212">`<PropertySet>`: Définit une collection de propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-212">`<PropertySet>`: Defines a collection of properties of the object.</span></span>

<span data-ttu-id="2fb7a-213">La `<PropertySet>` balise doit avoir une `<Name>` balise qui spécifie le nom du jeu de propriétés et une `<ReferencedProperty>` étiquette qui spécifie les propriétés.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-213">The `<PropertySet>` tag must have a `<Name>` tag that specifies the name of the property set and a `<ReferencedProperty>` tag that specifies the properties.</span></span> <span data-ttu-id="2fb7a-214">Les noms des propriétés sont placés dans la `<Name>` balise.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-214">The names of the properties are enclosed in `<Name>` tag.</span></span>

<span data-ttu-id="2fb7a-215">Dans `Types.ps1xml` , les `<PropertySet>` balises sont utilisées pour définir des ensembles de propriétés pour l’affichage par défaut d’un objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-215">In `Types.ps1xml`, `<PropertySet>` tags are used to define sets of properties for the default display of an object.</span></span> <span data-ttu-id="2fb7a-216">Vous pouvez identifier la valeur par défaut affichée par la valeur **PsStandardMembers** dans la `<Name>` balise d’une `<MemberSet>` balise.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-216">You can identify the default displays by the value **PsStandardMembers** in the `<Name>` tag of a `<MemberSet>` tag.</span></span>

<span data-ttu-id="2fb7a-217">Par exemple, le code XML suivant crée une propriété **Status** pour l' `System.IO.DirectoryInfo` objet.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-217">For example, the following XML creates a **Status** property for the `System.IO.DirectoryInfo` object.</span></span> <span data-ttu-id="2fb7a-218">La valeur de la propriété **Status** est toujours **Success** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-218">The value of the **Status** property is always **Success** .</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-219">`<ScriptMethod>`: Définit une méthode dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-219">`<ScriptMethod>`: Defines a method whose value is the output of a script.</span></span>

<span data-ttu-id="2fb7a-220">La `<ScriptMethod>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle méthode et une `<Script>` balise qui encadre le bloc de script qui retourne le résultat de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-220">The `<ScriptMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<Script>` tag that encloses the script block that returns the method result.</span></span>

<span data-ttu-id="2fb7a-221">Par exemple, les `ConvertToDateTime` `ConvertFromDateTime` méthodes et de Management Objects ( `System.System.Management.ManagementObject` ) sont des méthodes de script qui utilisent les `ToDateTime` `ToDmtfDateTime` méthodes statiques et de la `System.Management.ManagementDateTimeConverter` classe.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-221">For example, the `ConvertToDateTime` and `ConvertFromDateTime` methods of management objects (`System.System.Management.ManagementObject`) are script methods that use the `ToDateTime` and `ToDmtfDateTime` static methods of the `System.Management.ManagementDateTimeConverter` class.</span></span>

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

<span data-ttu-id="2fb7a-222">`<ScriptProperty>`: Définit une propriété dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-222">`<ScriptProperty>`: Defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="2fb7a-223">La `<ScriptProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<GetScriptBlock>` balise qui encadre le bloc de script qui retourne la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-223">The `<ScriptProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetScriptBlock>` tag that encloses the script block that returns the property value.</span></span>

<span data-ttu-id="2fb7a-224">Par exemple, la **propriété VERSIONINFO** de l' **objet System. IO. FileInfo** est une propriété de script qui résulte de l’utilisation de la propriété **FullName** de la méthode statique **GetVersionInfo** des objets **System. Diagnostics. FileVersionInfo** .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-224">For example, the **VersionInfo** property of the **System.IO.FileInfo** object is a script property that results from using the **FullName** property of the **GetVersionInfo** static method of **System.Diagnostics.FileVersionInfo** objects.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

<span data-ttu-id="2fb7a-225">Pour plus d’informations, consultez le [Kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-225">For more information, see the [Windows PowerShell Software Development Kit (SDK)](/powershell/scripting/developer/windows-powershell).</span></span>

## <a name="update-typedata"></a><span data-ttu-id="2fb7a-226">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="2fb7a-226">Update-TypeData</span></span>

<span data-ttu-id="2fb7a-227">Pour charger vos `Types.ps1xml` fichiers dans une session PowerShell, exécutez l' `Update-TypeData` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-227">To load your `Types.ps1xml` files into a PowerShell session, run the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="2fb7a-228">Si vous souhaitez que les types de votre fichier aient la priorité sur les types dans le `Types.ps1xml` fichier intégré, ajoutez le paramètre **PrependData** de `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-228">If you want the types in your file to take precedence over types in the built-in `Types.ps1xml` file, add the **PrependData** parameter of `Update-TypeData`.</span></span> <span data-ttu-id="2fb7a-229">`Update-TypeData` affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-229">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="2fb7a-230">Pour apporter la modification à toutes les sessions ultérieures, exportez la session ou ajoutez la `Update-TypeData` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-230">To make the change to all future sessions, export the session, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

<span data-ttu-id="2fb7a-231">Les exceptions qui se produisent dans les propriétés, ou à partir de l’ajout de propriétés à une `Update-TypeData` commande, ne signalent pas les erreurs à `StdErr` .</span><span class="sxs-lookup"><span data-stu-id="2fb7a-231">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors to `StdErr`.</span></span> <span data-ttu-id="2fb7a-232">Cela permet de supprimer des exceptions qui se produisent dans de nombreux types courants durant la mise en forme et la sortie.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-232">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="2fb7a-233">Si vous obtenez des propriétés .NET, vous pouvez contourner la suppression des exceptions en utilisant la syntaxe de méthode à la place, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2fb7a-233">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

```powershell
"hello".get_Length()
```

<span data-ttu-id="2fb7a-234">Notez que la syntaxe de méthode peut uniquement être utilisée avec des propriétés .NET.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-234">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="2fb7a-235">Les propriétés ajoutées en exécutant l’applet de commande `Update-TypeData` ne peuvent pas utiliser la syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-235">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

## <a name="signing-a-typesps1xml-file"></a><span data-ttu-id="2fb7a-236">Signature d’un fichier XML Types.ps1</span><span class="sxs-lookup"><span data-stu-id="2fb7a-236">Signing a Types.ps1xml file</span></span>

<span data-ttu-id="2fb7a-237">Pour protéger les utilisateurs de votre `Types.ps1xml` fichier, vous pouvez signer le fichier à l’aide d’une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="2fb7a-237">To protect users of your `Types.ps1xml` file, you can sign the file using a digital signature.</span></span> <span data-ttu-id="2fb7a-238">Pour plus d’informations, consultez [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="2fb7a-238">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb7a-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fb7a-239">See also</span></span>

[<span data-ttu-id="2fb7a-240">about_Signing</span><span class="sxs-lookup"><span data-stu-id="2fb7a-240">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="2fb7a-241">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="2fb7a-241">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)

[<span data-ttu-id="2fb7a-242">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2fb7a-242">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[<span data-ttu-id="2fb7a-243">Get-Member</span><span class="sxs-lookup"><span data-stu-id="2fb7a-243">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="2fb7a-244">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="2fb7a-244">Get-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[<span data-ttu-id="2fb7a-245">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="2fb7a-245">Remove-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[<span data-ttu-id="2fb7a-246">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="2fb7a-246">Update-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Update-TypeData)
