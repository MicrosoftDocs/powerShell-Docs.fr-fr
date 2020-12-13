---
ms.date: 09/13/2016
ms.topic: reference
title: Extension des objets de sortie
description: Extension des objets de sortie
ms.openlocfilehash: 9fea476e3032002bd206609313581cc6373dfddc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652906"
---
# <a name="extending-output-objects"></a><span data-ttu-id="dc127-103">Extension des objets de sortie</span><span class="sxs-lookup"><span data-stu-id="dc127-103">Extending Output Objects</span></span>

<span data-ttu-id="dc127-104">Vous pouvez étendre les objets .NET Framework retournés par les applets de commande, les fonctions et les scripts à l’aide des fichiers de types (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="dc127-104">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="dc127-105">Les fichiers de types sont des fichiers XML qui vous permettent d’ajouter des propriétés et des méthodes aux objets existants.</span><span class="sxs-lookup"><span data-stu-id="dc127-105">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="dc127-106">Par exemple, Windows PowerShell fournit le fichier XML Types.ps1, qui ajoute des éléments à plusieurs objets .NET Framework existants.</span><span class="sxs-lookup"><span data-stu-id="dc127-106">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="dc127-107">Le fichier XML Types.ps1se trouve dans le répertoire d’installation de Windows PowerShell ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="dc127-107">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="dc127-108">Vous pouvez créer votre propre fichier de types pour étendre davantage ces objets ou pour étendre d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="dc127-108">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="dc127-109">Quand vous étendez un objet à l’aide d’un fichier de types, toute instance de l’objet est étendue avec les nouveaux éléments.</span><span class="sxs-lookup"><span data-stu-id="dc127-109">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="dc127-110">Extension de l’objet System. Array</span><span class="sxs-lookup"><span data-stu-id="dc127-110">Extending the System.Array Object</span></span>

<span data-ttu-id="dc127-111">L’exemple suivant montre comment Windows PowerShell étend l’objet [System. Array](/dotnet/api/System.Array) dans le fichier XML Types.ps1.</span><span class="sxs-lookup"><span data-stu-id="dc127-111">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="dc127-112">Par défaut, les objets [System. Array](/dotnet/api/System.Array) ont une `Length` propriété qui répertorie le nombre d’objets dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="dc127-112">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="dc127-113">Toutefois, étant donné que le nom « length » ne décrit pas clairement la propriété, Windows PowerShell ajoute la `Count` propriété alias, qui affiche la même valeur que la `Length` propriété.</span><span class="sxs-lookup"><span data-stu-id="dc127-113">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="dc127-114">Le code XML suivant ajoute la `Count` propriété au type [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="dc127-114">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="dc127-115">Pour afficher cette nouvelle propriété d’alias, utilisez une commande d' [extraction de membre](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) sur n’importe quel tableau, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dc127-115">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="dc127-116">La commande retourne les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="dc127-116">The command returns the following results.</span></span>

```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```

<span data-ttu-id="dc127-117">Vous pouvez utiliser la `Count` propriété ou la `Length` propriété pour déterminer le nombre d’objets contenus dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="dc127-117">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="dc127-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="dc127-118">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="dc127-119">Fichiers de types personnalisés</span><span class="sxs-lookup"><span data-stu-id="dc127-119">Custom Types Files</span></span>

<span data-ttu-id="dc127-120">Pour créer un fichier de types personnalisés, commencez par copier un fichier de types existant.</span><span class="sxs-lookup"><span data-stu-id="dc127-120">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="dc127-121">Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une extension de nom de fichier. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="dc127-121">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="dc127-122">Lorsque vous copiez le fichier, vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à Windows PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de Windows PowerShell ( `$pshome` ) ou dans un sous-répertoire du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="dc127-122">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="dc127-123">Pour ajouter vos propres types étendus au fichier, ajoutez un élément types pour chaque objet que vous souhaitez étendre.</span><span class="sxs-lookup"><span data-stu-id="dc127-123">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="dc127-124">Les rubriques suivantes fournissent des exemples.</span><span class="sxs-lookup"><span data-stu-id="dc127-124">The following topics provide examples.</span></span>

- <span data-ttu-id="dc127-125">Pour plus d’informations sur l’ajout de propriétés et de jeux de propriétés, consultez [propriétés étendues](./extending-properties-for-objects.md) .</span><span class="sxs-lookup"><span data-stu-id="dc127-125">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="dc127-126">Pour plus d’informations sur l’ajout de méthodes, consultez [méthodes étendues](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="dc127-126">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="dc127-127">Pour plus d’informations sur l’ajout de jeux de membres, consultez [jeux de membres étendus](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="dc127-127">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="dc127-128">Une fois que vous avez défini vos propres types étendus, utilisez l’une des méthodes suivantes pour rendre vos objets étendus disponibles :</span><span class="sxs-lookup"><span data-stu-id="dc127-128">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="dc127-129">Pour mettre votre fichier de types étendus à la disposition de la session active, utilisez l’applet de commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) pour ajouter le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="dc127-129">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="dc127-130">Si vous souhaitez que vos types aient la priorité sur les types définis dans d’autres types de fichiers (y compris le fichier XML Types.ps1), utilisez le `PrependData` paramètre de l’applet de commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="dc127-130">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="dc127-131">Pour mettre votre fichier de types étendus à la disposition de toutes les sessions ultérieures, ajoutez le fichier de types à un module, exportez la session active ou ajoutez la commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc127-131">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="dc127-132">Fichiers de types de signature</span><span class="sxs-lookup"><span data-stu-id="dc127-132">Signing Types Files</span></span>

<span data-ttu-id="dc127-133">Les fichiers de types doivent être signés numériquement pour empêcher la falsification, car le XML peut inclure des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="dc127-133">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="dc127-134">Pour plus d’informations sur l’ajout de signatures numériques, consultez [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="dc127-134">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="dc127-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc127-135">See Also</span></span>

[<span data-ttu-id="dc127-136">Définition des propriétés par défaut des objets</span><span class="sxs-lookup"><span data-stu-id="dc127-136">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="dc127-137">Définition de méthodes par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="dc127-137">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="dc127-138">Définition de jeux de membres par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="dc127-138">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="dc127-139">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc127-139">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
