---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: db5dc586f2a165d83c25bdf2addaeb625f9e1ba0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596300"
---
# <span data-ttu-id="8310a-102">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="8310a-102">Get-TypeData</span></span>

## <span data-ttu-id="8310a-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8310a-103">Synopsis</span></span>
<span data-ttu-id="8310a-104">Obtient les données de type étendu dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8310a-104">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="8310a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8310a-105">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8310a-106">Description</span><span class="sxs-lookup"><span data-stu-id="8310a-106">Description</span></span>

<span data-ttu-id="8310a-107">L' `Get-TypeData` applet de commande obtient les données de type étendu dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8310a-107">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="8310a-108">Cela comprend les données de type qui ont été ajoutées à la session par `Types.ps1xml` fichier et les données de type dynamique qui ont été ajoutées à l’aide du paramètre de l’applet de commande `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="8310a-108">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="8310a-109">Vous pouvez utiliser les données de type étendu qui sont `Get-TypeData` retournées pour examiner les données de type dans la session et les envoyer aux `Update-TypeData` applets de commande et `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="8310a-109">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="8310a-110">Les données de type étendu ajoutent des propriétés et des méthodes aux objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8310a-110">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="8310a-111">Vous pouvez utiliser les propriétés et les méthodes ajoutées de la même manière que vous utiliseriez les propriétés et les méthodes qui sont définies dans le type d'objet.</span><span class="sxs-lookup"><span data-stu-id="8310a-111">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="8310a-112">Toutefois, lors de l’écriture de scripts, sachez que les propriétés et les méthodes ajoutées peuvent ne pas être présentes dans chaque session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8310a-112">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="8310a-113">Pour plus d’informations sur les `Types.ps1xml` fichiers, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="8310a-113">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="8310a-114">Pour plus d’informations sur les données de type dynamique ajoutées par l’applet de commande `Update-TypeData` , consultez `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="8310a-114">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="8310a-115">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8310a-115">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="8310a-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="8310a-116">Examples</span></span>

### <span data-ttu-id="8310a-117">Exemple 1 : récupération de toutes les données de type étendu</span><span class="sxs-lookup"><span data-stu-id="8310a-117">Example 1: Get all extended type data</span></span>

<span data-ttu-id="8310a-118">Cet exemple obtient toutes les données de type étendu dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8310a-118">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="8310a-119">Exemple 2 : récupération des types par nom</span><span class="sxs-lookup"><span data-stu-id="8310a-119">Example 2: Get types by name</span></span>

<span data-ttu-id="8310a-120">Cet exemple obtient tous les types dans la session active qui ont des noms qui contiennent des événements.</span><span class="sxs-lookup"><span data-stu-id="8310a-120">This example gets all types in the current session that have names that contain Eventing.</span></span>

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### <span data-ttu-id="8310a-121">Exemple 3 : obtenir le bloc de script qui crée une valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="8310a-121">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="8310a-122">Cet exemple obtient le bloc de script qui crée la valeur de la propriété **eventID** des objets **EventLogEntry** .</span><span class="sxs-lookup"><span data-stu-id="8310a-122">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="8310a-123">Exemple 4 : obtenir le bloc de script qui définit une propriété pour un objet spécifié</span><span class="sxs-lookup"><span data-stu-id="8310a-123">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="8310a-124">Cet exemple obtient le bloc de script qui définit la propriété **DateTime** des objets **System. DateTime** dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8310a-124">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

<span data-ttu-id="8310a-125">La commande utilise l' `Get-TypeData` applet de commande pour obtenir les données de type étendu pour le type **System. DataTime** .</span><span class="sxs-lookup"><span data-stu-id="8310a-125">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="8310a-126">La commande obtient la propriété **Members** de l'objet **TypeData**.</span><span class="sxs-lookup"><span data-stu-id="8310a-126">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="8310a-127">La propriété **members** contient une table de hachage des propriétés et des méthodes qui sont définies par les données de type étendu.</span><span class="sxs-lookup"><span data-stu-id="8310a-127">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="8310a-128">Chaque clé dans la table de hachage Members est un nom de propriété ou de méthode et chaque valeur est la définition de la valeur de propriété ou de méthode.</span><span class="sxs-lookup"><span data-stu-id="8310a-128">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="8310a-129">La commande obtient la clé **DateTime** dans **members** et sa valeur de propriété **GetScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="8310a-129">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="8310a-130">La sortie affiche le bloc de script qui crée la valeur de la propriété **DateTime** de chaque objet **System. DateTime** dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8310a-130">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="8310a-131">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8310a-131">Parameters</span></span>

### <span data-ttu-id="8310a-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="8310a-132">-TypeName</span></span>

<span data-ttu-id="8310a-133">Spécifie les données de type sous forme de tableau uniquement pour les types avec les noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8310a-133">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="8310a-134">Par défaut, `Get-TypeData` obtient tous les types dans la session.</span><span class="sxs-lookup"><span data-stu-id="8310a-134">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="8310a-135">Entrez des noms de types ou des modèles de nom.</span><span class="sxs-lookup"><span data-stu-id="8310a-135">Enter type names or a name patterns.</span></span> <span data-ttu-id="8310a-136">Les noms complets ou les modèles de nom avec des caractères génériques sont requis, même pour les types de l’espace de noms System.</span><span class="sxs-lookup"><span data-stu-id="8310a-136">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="8310a-137">Les caractères génériques sont pris en charge et le nom de paramètre **TypeName** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="8310a-137">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="8310a-138">Vous pouvez également diriger les noms de types vers `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="8310a-138">You can also pipe type names to `Get-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8310a-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8310a-139">CommonParameters</span></span>

<span data-ttu-id="8310a-140">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8310a-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8310a-141">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8310a-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8310a-142">Entrées</span><span class="sxs-lookup"><span data-stu-id="8310a-142">Inputs</span></span>

### <span data-ttu-id="8310a-143">System.String</span><span class="sxs-lookup"><span data-stu-id="8310a-143">System.String</span></span>

<span data-ttu-id="8310a-144">Vous pouvez diriger les noms de types vers `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="8310a-144">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="8310a-145">Sorties</span><span class="sxs-lookup"><span data-stu-id="8310a-145">Outputs</span></span>

### <span data-ttu-id="8310a-146">System. Management. Automation. instances d’exécution. TypeData</span><span class="sxs-lookup"><span data-stu-id="8310a-146">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="8310a-147">Notes</span><span class="sxs-lookup"><span data-stu-id="8310a-147">Notes</span></span>

<span data-ttu-id="8310a-148">`Get-TypeData` Obtient uniquement les données de type étendu dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8310a-148">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="8310a-149">Il n'obtient pas les données de type étendu sur l'ordinateur, mais n'a pas été ajouté à la session active, comme les types étendus qui sont définis dans les modules qui n'ont pas été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8310a-149">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="8310a-150">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="8310a-150">Related links</span></span>

[<span data-ttu-id="8310a-151">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="8310a-151">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="8310a-152">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="8310a-152">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="8310a-153">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="8310a-153">Update-TypeData</span></span>](Update-TypeData.md)

