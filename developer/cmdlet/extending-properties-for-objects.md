---
title: Étendre les propriétés des objets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057295"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="65acb-102">Extension des propriétés pour les objets</span><span class="sxs-lookup"><span data-stu-id="65acb-102">Extending Properties for Objects</span></span>

<span data-ttu-id="65acb-103">Lorsque vous étendez des objets .NET Framework, vous pouvez ajouter alias propriétés, les propriétés de code, propriétés de note, propriétés de script et jeux de propriétés aux objets.</span><span class="sxs-lookup"><span data-stu-id="65acb-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="65acb-104">Le code XML qui est utilisé pour définir ces propriétés est décrite dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="65acb-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="65acb-105">Les exemples dans les sections suivantes sont à partir du fichier de types par défaut Types.ps1xml dans le répertoire d’installation de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="65acb-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="65acb-106">Propriétés d’alias</span><span class="sxs-lookup"><span data-stu-id="65acb-106">Alias Properties</span></span>

<span data-ttu-id="65acb-107">Une propriété d’alias définit un nouveau nom pour une propriété existante.</span><span class="sxs-lookup"><span data-stu-id="65acb-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="65acb-108">Dans l’exemple suivant, le `Count` propriété est ajoutée à la [System.Array ? Displayproperty = Fullname](/dotnet/api/System.Array) type.</span><span class="sxs-lookup"><span data-stu-id="65acb-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="65acb-109">Le [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) élément définit la propriété étendue comme une propriété d’alias.</span><span class="sxs-lookup"><span data-stu-id="65acb-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="65acb-110">Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="65acb-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="65acb-111">Et, le [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) élément spécifie la propriété existante qui est référencée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="65acb-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="65acb-112">(Vous pouvez également ajouter le [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)</span><span class="sxs-lookup"><span data-stu-id="65acb-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="65acb-113">Propriétés du code</span><span class="sxs-lookup"><span data-stu-id="65acb-113">Code Properties</span></span>

<span data-ttu-id="65acb-114">Une propriété de code fait référence à une propriété statique d’un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65acb-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="65acb-115">Dans l’exemple suivant, le `Node` propriété est ajoutée à la [System.IO.Directoryinfo ? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span><span class="sxs-lookup"><span data-stu-id="65acb-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="65acb-116">Le [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) élément définit la propriété étendue en tant que code propriété.</span><span class="sxs-lookup"><span data-stu-id="65acb-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="65acb-117">Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="65acb-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="65acb-118">Et, le [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) élément définit la méthode statique qui est référencée par la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="65acb-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="65acb-119">(Vous pouvez également ajouter le [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)</span><span class="sxs-lookup"><span data-stu-id="65acb-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="65acb-120">Propriétés de note</span><span class="sxs-lookup"><span data-stu-id="65acb-120">Note Properties</span></span>

<span data-ttu-id="65acb-121">Une propriété de note définit une propriété qui a une valeur statique.</span><span class="sxs-lookup"><span data-stu-id="65acb-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="65acb-122">Dans l’exemple suivant, le `Status` propriété (dont la valeur est toujours « Success ») est ajoutée à la [System.IO.Directoryinfo ? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span><span class="sxs-lookup"><span data-stu-id="65acb-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="65acb-123">Le [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) élément définit la propriété étendue comme une propriété de note ; le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété étendue ; et le [valeur](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) élément Spécifie la valeur statique de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="65acb-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="65acb-124">(Le [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) élément peut également être ajouté aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)</span><span class="sxs-lookup"><span data-stu-id="65acb-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="65acb-125">Propriétés du script</span><span class="sxs-lookup"><span data-stu-id="65acb-125">Script Properties</span></span>

<span data-ttu-id="65acb-126">Une propriété de script définit une propriété dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="65acb-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="65acb-127">Dans l’exemple suivant, le `VersionInfo` propriété est ajoutée à la [System.IO.FileInfo ? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) type.</span><span class="sxs-lookup"><span data-stu-id="65acb-127">In the following example, the `VersionInfo` property is added to the [System.IO.FileInfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="65acb-128">Le [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) élément définit la propriété étendue comme une propriété de script.</span><span class="sxs-lookup"><span data-stu-id="65acb-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="65acb-129">Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="65acb-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="65acb-130">Et, le [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) élément spécifie le script qui génère la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="65acb-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="65acb-131">(Vous pouvez également ajouter le [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)</span><span class="sxs-lookup"><span data-stu-id="65acb-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="65acb-132">Jeux de propriétés</span><span class="sxs-lookup"><span data-stu-id="65acb-132">Property Sets</span></span>

<span data-ttu-id="65acb-133">Un jeu de propriétés définit un groupe de propriétés étendues qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="65acb-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="65acb-134">Par exemple, le `Property` paramètre de la [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) applet de commande peut spécifier une propriété spécifique définie pour être affichée.</span><span class="sxs-lookup"><span data-stu-id="65acb-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="65acb-135">Lorsqu’un jeu de propriétés est spécifié, uniquement les propriétés qui appartiennent au jeu sont affichées.</span><span class="sxs-lookup"><span data-stu-id="65acb-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="65acb-136">Il n’existe aucune restriction sur le nombre de jeux de propriétés qui peuvent être définis pour un objet.</span><span class="sxs-lookup"><span data-stu-id="65acb-136">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="65acb-137">Toutefois, les jeux de propriétés utilisées pour définir les propriétés d’affichage par défaut d’un objet doivent être spécifiés dans le jeu de membres PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="65acb-137">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="65acb-138">Dans le fichier de types Types.ps1xml, les noms de jeu de propriétés par défaut incluent DefaultDisplayProperty, DefaultDisplayPropertySet et DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="65acb-138">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="65acb-139">Les jeux de propriétés supplémentaires que vous ajoutez au jeu de membres PSStandardMembers est ignorés.</span><span class="sxs-lookup"><span data-stu-id="65acb-139">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="65acb-140">Dans l’exemple suivant, le jeu de propriétés DefaultDisplayPropertySet est ajouté au jeu de membres PSStandardMembers de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span><span class="sxs-lookup"><span data-stu-id="65acb-140">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="65acb-141">Le [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) élément définit le groupe de propriétés.</span><span class="sxs-lookup"><span data-stu-id="65acb-141">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="65acb-142">Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="65acb-142">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="65acb-143">Et, le [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) élément spécifie les propriétés de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="65acb-143">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="65acb-144">(Vous pouvez également ajouter le [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) élément aux membres de la [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) élément.)</span><span class="sxs-lookup"><span data-stu-id="65acb-144">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="65acb-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65acb-145">See Also</span></span>

[<span data-ttu-id="65acb-146">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="65acb-146">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
