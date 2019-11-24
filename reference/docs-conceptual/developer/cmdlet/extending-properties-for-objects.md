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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364448"
---
# <a name="extending-properties-for-objects"></a>Extension des propriétés pour les objets

Lorsque vous étendez .NET Framework objets, vous pouvez ajouter des propriétés d’alias, des propriétés de code, des propriétés de note, des propriétés de script et des jeux de propriétés aux objets. Le code XML qui définit ces propriétés est décrit dans les sections suivantes.

> [!NOTE]
> Les exemples des sections suivantes proviennent du fichier de types de `Types.ps1xml` par défaut dans le répertoire d’installation de PowerShell (`$PSHOME`). Pour plus d’informations, consultez [à propos des types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Propriétés de l’alias

Une propriété d’alias définit un nouveau nom pour une propriété existante.

Dans l’exemple suivant, la propriété **Count** est ajoutée au type [System. Array](/dotnet/api/System.Array) . L’élément [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) définit la propriété étendue en tant que propriété d’alias. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nouveau nom. Et, l’élément [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) spécifie la propriété existante qui est référencée par l’alias. Vous pouvez également ajouter l’élément `AliasProperty` aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.

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

## <a name="code-properties"></a>Propriétés de code

Une propriété de code fait référence à une propriété statique d’un objet .NET Framework.

Dans l’exemple suivant, la propriété **mode** est ajoutée au type [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . L’élément [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) définit la propriété étendue en tant que propriété de code. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom de la propriété étendue. Et, l’élément [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) définit la méthode statique qui est référencée par la propriété étendue. Vous pouvez également ajouter l’élément `CodeProperty` aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.

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

## <a name="note-properties"></a>Propriétés de la note

Une propriété de note définit une propriété qui a une valeur statique.

Dans l’exemple suivant, la propriété **Status** , dont la valeur est Always **Success**, est ajoutée au type [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . L’élément [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) définit la propriété étendue en tant que propriété de note. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom de la propriété étendue. L’élément [value](/dotnet/api/system.management.automation.psnoteproperty.value) spécifie la valeur statique de la propriété étendue. L’élément `NoteProperty` peut également être ajouté aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.

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

## <a name="script-properties"></a>Propriétés du script

Une propriété de script définit une propriété dont la valeur est la sortie d’un script.

Dans l’exemple suivant, la propriété **VERSIONINFO** est ajoutée au type [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) . L’élément [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) définit la propriété étendue en tant que propriété de script. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom de la propriété étendue. Et, l’élément [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) spécifie le script qui génère la valeur de la propriété. Vous pouvez également ajouter l’élément `ScriptProperty` aux membres de l’élément [jeux](/dotnet/api/system.management.automation.psmemberset) de membres.

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

## <a name="property-sets"></a>Jeux de propriétés

Un jeu de propriétés définit un groupe de propriétés étendues qui peuvent être référencées par le nom de l’ensemble.
Par exemple, le paramètre de **propriété** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
peut spécifier un jeu de propriétés spécifique à afficher. Quand un jeu de propriétés est spécifié, seules les propriétés qui appartiennent à l’ensemble sont affichées.

Il n’existe aucune restriction sur le nombre de jeux de propriétés qui peuvent être définis pour un objet. Toutefois, les jeux de propriétés utilisés pour définir les propriétés d’affichage par défaut d’un objet doivent être spécifiés dans le jeu de membres **PSStandardMembers** . Dans le fichier de types de `Types.ps1xml`, les noms de jeu de propriétés par défaut sont **DefaultDisplayProperty**, **DefaultDisplayPropertySet**et **DefaultKeyPropertySet**. Tous les jeux de propriétés supplémentaires que vous ajoutez au jeu de membres **PSStandardMembers** sont ignorés.

Dans l’exemple suivant, le jeu de propriétés **DefaultDisplayPropertySet** est ajouté au jeu de membres **PSStandardMembers** du type [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . L’élément [PropertySet](/dotnet/api/system.management.automation.pspropertyset) définit le groupe de propriétés. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name) spécifie le nom du jeu de propriétés. Et, l’élément [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) spécifie les propriétés de l’ensemble. Vous pouvez également ajouter l’élément `PropertySet` aux membres de l’élément [type](/dotnet/api/system.management.automation.pstypename) .

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

## <a name="see-also"></a>Voir aussi

[À propos des types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
