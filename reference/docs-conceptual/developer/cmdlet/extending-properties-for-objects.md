---
title: Extension des propriétés des objets | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364448"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="09571-102">Extension des propriétés pour les objets</span><span class="sxs-lookup"><span data-stu-id="09571-102">Extending Properties for Objects</span></span>

<span data-ttu-id="09571-103">Lorsque vous étendez .NET Framework objets, vous pouvez ajouter des propriétés d’alias, des propriétés de code, des propriétés de note, des propriétés de script et des jeux de propriétés aux objets.</span><span class="sxs-lookup"><span data-stu-id="09571-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="09571-104">Le code XML qui définit ces propriétés est décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="09571-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="09571-105">Les exemples des sections suivantes proviennent du fichier de types de `Types.ps1xml` par défaut dans le répertoire d’installation de PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="09571-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="09571-106">Pour plus d’informations, consultez [à propos des types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="09571-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="09571-107">Propriétés de l’alias</span><span class="sxs-lookup"><span data-stu-id="09571-107">Alias properties</span></span>

<span data-ttu-id="09571-108">Une propriété d’alias définit un nouveau nom pour une propriété existante.</span><span class="sxs-lookup"><span data-stu-id="09571-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="09571-109">Dans l’exemple suivant, la propriété **Count** est ajoutée au type [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="09571-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="09571-110">L’élément [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) définit la propriété étendue en tant que propriété d’alias.</span><span class="sxs-lookup"><span data-stu-id="09571-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="09571-111">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="09571-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="09571-112">Et, l’élément [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) spécifie la propriété existante qui est référencée par l’alias.</span><span class="sxs-lookup"><span data-stu-id="09571-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="09571-113">Vous pouvez également ajouter l’élément `AliasProperty` aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.</span><span class="sxs-lookup"><span data-stu-id="09571-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="09571-114">Propriétés de code</span><span class="sxs-lookup"><span data-stu-id="09571-114">Code properties</span></span>

<span data-ttu-id="09571-115">Une propriété de code fait référence à une propriété statique d’un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09571-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="09571-116">Dans l’exemple suivant, la propriété **mode** est ajoutée au type [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="09571-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="09571-117">L’élément [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) définit la propriété étendue en tant que propriété de code.</span><span class="sxs-lookup"><span data-stu-id="09571-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="09571-118">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="09571-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="09571-119">Et, l’élément [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) définit la méthode statique qui est référencée par la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="09571-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="09571-120">Vous pouvez également ajouter l’élément `CodeProperty` aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.</span><span class="sxs-lookup"><span data-stu-id="09571-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="09571-121">Noter les propriétés</span><span class="sxs-lookup"><span data-stu-id="09571-121">Note properties</span></span>

<span data-ttu-id="09571-122">Une propriété de note définit une propriété qui a une valeur statique.</span><span class="sxs-lookup"><span data-stu-id="09571-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="09571-123">Dans l’exemple suivant, la propriété **Status** , dont la valeur est Always **Success**, est ajoutée au type [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="09571-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="09571-124">L’élément [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) définit la propriété étendue en tant que propriété de note.</span><span class="sxs-lookup"><span data-stu-id="09571-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="09571-125">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="09571-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="09571-126">L’élément [value](/dotnet/api/system.management.automation.psnoteproperty.value) spécifie la valeur statique de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="09571-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="09571-127">L’élément `NoteProperty` peut également être ajouté aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.</span><span class="sxs-lookup"><span data-stu-id="09571-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="09571-128">Propriétés du script</span><span class="sxs-lookup"><span data-stu-id="09571-128">Script properties</span></span>

<span data-ttu-id="09571-129">Une propriété de script définit une propriété dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="09571-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="09571-130">Dans l’exemple suivant, la propriété **VERSIONINFO** est ajoutée au type [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="09571-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="09571-131">L’élément [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) définit la propriété étendue en tant que propriété de script.</span><span class="sxs-lookup"><span data-stu-id="09571-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="09571-132">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom de la propriété étendue.</span><span class="sxs-lookup"><span data-stu-id="09571-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="09571-133">Et, l’élément [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) spécifie le script qui génère la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="09571-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="09571-134">Vous pouvez également ajouter l’élément `ScriptProperty` aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.</span><span class="sxs-lookup"><span data-stu-id="09571-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="09571-135">Jeux de propriétés</span><span class="sxs-lookup"><span data-stu-id="09571-135">Property sets</span></span>

<span data-ttu-id="09571-136">Un jeu de propriétés définit un groupe de propriétés étendues qui peuvent être référencées par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="09571-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="09571-137">Par exemple, le paramètre de **propriété** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
peut spécifier un jeu de propriétés spécifique à afficher.</span><span class="sxs-lookup"><span data-stu-id="09571-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="09571-138">Quand un jeu de propriétés est spécifié, seules les propriétés qui appartiennent à l’ensemble sont affichées.</span><span class="sxs-lookup"><span data-stu-id="09571-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="09571-139">Il n’existe aucune restriction sur le nombre de jeux de propriétés qui peuvent être définis pour un objet.</span><span class="sxs-lookup"><span data-stu-id="09571-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="09571-140">Toutefois, les jeux de propriétés utilisés pour définir les propriétés d’affichage par défaut d’un objet doivent être spécifiés dans le jeu de membres **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="09571-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="09571-141">Dans le fichier de types de `Types.ps1xml`, les noms de jeu de propriétés par défaut sont **DefaultDisplayProperty**, **DefaultDisplayPropertySet**et **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="09571-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="09571-142">Tous les jeux de propriétés supplémentaires que vous ajoutez au jeu de membres **PSStandardMembers** sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="09571-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="09571-143">Dans l’exemple suivant, le jeu de propriétés **DefaultDisplayPropertySet** est ajouté au jeu de membres **PSStandardMembers** du type [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="09571-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="09571-144">L’élément [PropertySet](/dotnet/api/system.management.automation.pspropertyset) définit le groupe de propriétés.</span><span class="sxs-lookup"><span data-stu-id="09571-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="09571-145">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom du jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="09571-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="09571-146">Et, l’élément [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) spécifie les propriétés de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="09571-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="09571-147">Vous pouvez également ajouter l’élément `PropertySet` aux membres de l’élément [type](/dotnet/api/system.management.automation.pstypename) .</span><span class="sxs-lookup"><span data-stu-id="09571-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="09571-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09571-148">See also</span></span>

[<span data-ttu-id="09571-149">À propos des types. ps1xml</span><span class="sxs-lookup"><span data-stu-id="09571-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="09571-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="09571-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="09571-151">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="09571-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
