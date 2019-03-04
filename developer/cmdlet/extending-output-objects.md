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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861925"
---
# <a name="extending-output-objects"></a><span data-ttu-id="62975-102">Extension des objets de sortie</span><span class="sxs-lookup"><span data-stu-id="62975-102">Extending Output Objects</span></span>

<span data-ttu-id="62975-103">Vous pouvez étendre les objets .NET Framework qui sont retournés par les applets de commande, les fonctions et les scripts à l’aide de fichiers de types (.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="62975-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="62975-104">Fichiers de types sont des fichiers XML qui vous permettent d’ajouter des propriétés et des méthodes aux objets existants.</span><span class="sxs-lookup"><span data-stu-id="62975-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="62975-105">Par exemple, Windows PowerShell fournit le fichier Types.ps1xml, qui ajoute des éléments à plusieurs objets de .NET Framework existantes.</span><span class="sxs-lookup"><span data-stu-id="62975-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="62975-106">Le fichier Types.ps1xml se trouve dans le répertoire d’installation de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="62975-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="62975-107">Vous pouvez créer votre propre fichier de types pour étendre ces objets ou pour étendre les autres objets.</span><span class="sxs-lookup"><span data-stu-id="62975-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="62975-108">Lorsque vous étendez un objet à l’aide d’un fichier de types, n’importe quelle instance de l’objet est étendue avec les nouveaux éléments.</span><span class="sxs-lookup"><span data-stu-id="62975-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="62975-109">Extension de l’objet System.Array</span><span class="sxs-lookup"><span data-stu-id="62975-109">Extending the System.Array Object</span></span>

<span data-ttu-id="62975-110">L’exemple suivant montre comment Windows PowerShell étend la [System.Array](/dotnet/api/System.Array) objet dans le fichier Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="62975-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="62975-111">Par défaut, [System.Array](/dotnet/api/System.Array) objets ont une `Length` propriété qui indique le nombre d’objets dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="62975-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="62975-112">Toutefois, étant donné que la nom « longueur de » ne décrit pas clairement la propriété, Windows PowerShell ajoute le `Count` propriété d’alias, qui affiche la même valeur que le `Length` propriété.</span><span class="sxs-lookup"><span data-stu-id="62975-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="62975-113">Le code XML suivant ajoute le `Count` propriété le [System.Array](/dotnet/api/System.Array) type.</span><span class="sxs-lookup"><span data-stu-id="62975-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="62975-114">Pour afficher cette nouvelle propriété d’alias, utilisez un [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) commande sur n’importe quel tableau, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="62975-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="62975-115">La commande retourne les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="62975-115">The command returns the following results.</span></span>
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
<span data-ttu-id="62975-116">Vous pouvez utiliser la `Count` propriété ou le `Length` propriété afin de déterminer le nombre d’objets est dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="62975-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="62975-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="62975-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="62975-118">Fichiers de Types personnalisés</span><span class="sxs-lookup"><span data-stu-id="62975-118">Custom Types Files</span></span>

<span data-ttu-id="62975-119">Pour créer un fichier de types personnalisés, démarrez en copiant un fichier de types existant.</span><span class="sxs-lookup"><span data-stu-id="62975-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="62975-120">Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une extension de nom de fichier .ps1xml.</span><span class="sxs-lookup"><span data-stu-id="62975-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="62975-121">Lorsque vous copiez le fichier, vous pouvez placer le nouveau fichier dans n’importe quel répertoire est accessible à Windows PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de Windows PowerShell (`$pshome`) ou dans un sous-répertoire du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="62975-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="62975-122">Pour ajouter vos propres types étendus dans le fichier, ajoutez un élément de types pour chaque objet que vous souhaitez étendre.</span><span class="sxs-lookup"><span data-stu-id="62975-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="62975-123">Les rubriques suivantes fournissent des exemples.</span><span class="sxs-lookup"><span data-stu-id="62975-123">The following topics provide examples.</span></span>

- <span data-ttu-id="62975-124">Pour plus d’informations sur l’ajout de propriétés et des jeux de propriétés, consultez [propriétés étendues](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="62975-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="62975-125">Pour plus d’informations sur l’ajout de méthodes, consultez [méthodes étendu](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="62975-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="62975-126">Pour plus d’informations sur l’ajout de jeux de membres, consultez [étendue membre définit](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="62975-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="62975-127">Une fois que vous définissez vos propres types étendus, utilisez une des méthodes suivantes pour rendre vos objets étendus disponibles :</span><span class="sxs-lookup"><span data-stu-id="62975-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="62975-128">Pour rendre votre fichier de types étendus disponibles à la session active, utilisez la [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) applet de commande pour ajouter le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="62975-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="62975-129">Si vous souhaitez que vos types sont prioritaires sur les types qui sont définis dans des autres types de fichiers (y compris le fichier Types.ps1xml), utilisez le `PrependData` paramètre de la [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="62975-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="62975-130">Pour rendre votre fichier de types étendus disponible pour toutes les futures sessions, ajoutez le fichier de types à un module, exporter la session active ou ajouter le [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) commande à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62975-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="62975-131">Signature des fichiers de Types</span><span class="sxs-lookup"><span data-stu-id="62975-131">Signing Types Files</span></span>

<span data-ttu-id="62975-132">Fichiers de types doivent être signés numériquement pour empêcher toute falsification, car le code XML peut inclure des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="62975-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="62975-133">Pour plus d’informations sur l’ajout de signatures numériques, consultez [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="62975-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="62975-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62975-134">See Also</span></span>

[<span data-ttu-id="62975-135">Définition des propriétés par défaut des objets</span><span class="sxs-lookup"><span data-stu-id="62975-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="62975-136">Définition de méthodes par défaut des objets</span><span class="sxs-lookup"><span data-stu-id="62975-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="62975-137">Définition de jeux de membres par défaut des objets</span><span class="sxs-lookup"><span data-stu-id="62975-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="62975-138">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62975-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
