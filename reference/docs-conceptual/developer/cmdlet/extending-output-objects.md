---
title: Extension des objets de sortie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369718"
---
# <a name="extending-output-objects"></a><span data-ttu-id="6bb32-102">Extension des objets de sortie</span><span class="sxs-lookup"><span data-stu-id="6bb32-102">Extending Output Objects</span></span>

<span data-ttu-id="6bb32-103">Vous pouvez étendre les objets .NET Framework retournés par les applets de commande, les fonctions et les scripts à l’aide des fichiers de types (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="6bb32-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="6bb32-104">Les fichiers de types sont des fichiers XML qui vous permettent d’ajouter des propriétés et des méthodes aux objets existants.</span><span class="sxs-lookup"><span data-stu-id="6bb32-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="6bb32-105">Par exemple, Windows PowerShell fournit le fichier types. ps1xml, qui ajoute des éléments à plusieurs objets .NET Framework existants.</span><span class="sxs-lookup"><span data-stu-id="6bb32-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="6bb32-106">Le fichier types. ps1xml se trouve dans le répertoire d’installation de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="6bb32-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="6bb32-107">Vous pouvez créer votre propre fichier de types pour étendre davantage ces objets ou pour étendre d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="6bb32-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="6bb32-108">Quand vous étendez un objet à l’aide d’un fichier de types, toute instance de l’objet est étendue avec les nouveaux éléments.</span><span class="sxs-lookup"><span data-stu-id="6bb32-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="6bb32-109">Extension de l’objet System. Array</span><span class="sxs-lookup"><span data-stu-id="6bb32-109">Extending the System.Array Object</span></span>

<span data-ttu-id="6bb32-110">L’exemple suivant montre comment Windows PowerShell étend l’objet [System. Array](/dotnet/api/System.Array) dans le fichier types. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="6bb32-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="6bb32-111">Par défaut, les objets [System. Array](/dotnet/api/System.Array) ont une propriété `Length` qui répertorie le nombre d’objets dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6bb32-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="6bb32-112">Toutefois, étant donné que le nom « length » ne décrit pas clairement la propriété, Windows PowerShell ajoute la propriété d’alias `Count`, qui affiche la même valeur que la propriété `Length`.</span><span class="sxs-lookup"><span data-stu-id="6bb32-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="6bb32-113">Le code XML suivant ajoute la propriété `Count` au type [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="6bb32-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="6bb32-114">Pour afficher cette nouvelle propriété d’alias, utilisez une commande d' [extraction de membre](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) sur n’importe quel tableau, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6bb32-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="6bb32-115">La commande retourne les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="6bb32-115">The command returns the following results.</span></span>
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
<span data-ttu-id="6bb32-116">Vous pouvez utiliser la propriété `Count` ou la propriété `Length` pour déterminer le nombre d’objets contenus dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="6bb32-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="6bb32-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6bb32-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="6bb32-118">Fichiers de types personnalisés</span><span class="sxs-lookup"><span data-stu-id="6bb32-118">Custom Types Files</span></span>

<span data-ttu-id="6bb32-119">Pour créer un fichier de types personnalisés, commencez par copier un fichier de types existant.</span><span class="sxs-lookup"><span data-stu-id="6bb32-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="6bb32-120">Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une extension de nom de fichier. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="6bb32-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="6bb32-121">Lorsque vous copiez le fichier, vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à Windows PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de Windows PowerShell (`$pshome`) ou dans un sous-répertoire du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="6bb32-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="6bb32-122">Pour ajouter vos propres types étendus au fichier, ajoutez un élément types pour chaque objet que vous souhaitez étendre.</span><span class="sxs-lookup"><span data-stu-id="6bb32-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="6bb32-123">Les rubriques suivantes fournissent des exemples.</span><span class="sxs-lookup"><span data-stu-id="6bb32-123">The following topics provide examples.</span></span>

- <span data-ttu-id="6bb32-124">Pour plus d’informations sur l’ajout de propriétés et de jeux de propriétés, consultez [propriétés étendues](./extending-properties-for-objects.md) .</span><span class="sxs-lookup"><span data-stu-id="6bb32-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="6bb32-125">Pour plus d’informations sur l’ajout de méthodes, consultez [méthodes étendues](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6bb32-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="6bb32-126">Pour plus d’informations sur l’ajout de jeux de membres, consultez [jeux de membres étendus](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6bb32-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="6bb32-127">Une fois que vous avez défini vos propres types étendus, utilisez l’une des méthodes suivantes pour rendre vos objets étendus disponibles :</span><span class="sxs-lookup"><span data-stu-id="6bb32-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="6bb32-128">Pour mettre votre fichier de types étendus à la disposition de la session active, utilisez l’applet de commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) pour ajouter le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="6bb32-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="6bb32-129">Si vous souhaitez que vos types aient la priorité sur les types définis dans d’autres types de fichiers (y compris le fichier types. ps1xml), utilisez le paramètre `PrependData` de l’applet de commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="6bb32-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="6bb32-130">Pour mettre votre fichier de types étendus à la disposition de toutes les sessions ultérieures, ajoutez le fichier de types à un module, exportez la session active ou ajoutez la commande [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bb32-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="6bb32-131">Fichiers de types de signature</span><span class="sxs-lookup"><span data-stu-id="6bb32-131">Signing Types Files</span></span>

<span data-ttu-id="6bb32-132">Les fichiers de types doivent être signés numériquement pour empêcher la falsification, car le XML peut inclure des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="6bb32-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="6bb32-133">Pour plus d’informations sur l’ajout de signatures numériques, consultez [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="6bb32-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="6bb32-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bb32-134">See Also</span></span>

[<span data-ttu-id="6bb32-135">Définition des propriétés par défaut des objets</span><span class="sxs-lookup"><span data-stu-id="6bb32-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="6bb32-136">Définition des méthodes par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="6bb32-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="6bb32-137">Définition des jeux de membres par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="6bb32-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="6bb32-138">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6bb32-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
