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
# <a name="extending-properties-for-objects"></a>Extension des propriétés pour les objets

Lorsque vous étendez des objets .NET Framework, vous pouvez ajouter alias propriétés, les propriétés de code, propriétés de note, propriétés de script et jeux de propriétés aux objets. Le code XML qui est utilisé pour définir ces propriétés est décrite dans les sections suivantes.

> [!NOTE]
> Les exemples dans les sections suivantes sont à partir du fichier de types par défaut Types.ps1xml dans le répertoire d’installation de Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Propriétés d’alias

Une propriété d’alias définit un nouveau nom pour une propriété existante.

Dans l’exemple suivant, le `Count` propriété est ajoutée à la [System.Array ? Displayproperty = Fullname](/dotnet/api/System.Array) type. Le [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) élément définit la propriété étendue comme une propriété d’alias. Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nouveau nom. Et, le [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) élément spécifie la propriété existante qui est référencée par l’alias. (Vous pouvez également ajouter le [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)

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

## <a name="code-properties"></a>Propriétés du code

Une propriété de code fait référence à une propriété statique d’un objet .NET Framework.

Dans l’exemple suivant, le `Node` propriété est ajoutée à la [System.IO.Directoryinfo ? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type. Le [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) élément définit la propriété étendue en tant que code propriété. Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété étendue. Et, le [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) élément définit la méthode statique qui est référencée par la propriété étendue. (Vous pouvez également ajouter le [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)

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

## <a name="note-properties"></a>Propriétés de note

Une propriété de note définit une propriété qui a une valeur statique.

Dans l’exemple suivant, le `Status` propriété (dont la valeur est toujours « Success ») est ajoutée à la [System.IO.Directoryinfo ? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type. Le [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) élément définit la propriété étendue comme une propriété de note ; le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété étendue ; et le [valeur](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) élément Spécifie la valeur statique de la propriété étendue. (Le [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) élément peut également être ajouté aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)

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

Dans l’exemple suivant, le `VersionInfo` propriété est ajoutée à la [System.IO.FileInfo ? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) type. Le [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) élément définit la propriété étendue comme une propriété de script. Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété étendue. Et, le [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) élément spécifie le script qui génère la valeur de propriété. (Vous pouvez également ajouter le [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)

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

Un jeu de propriétés définit un groupe de propriétés étendues qui peuvent être référencés par le nom de l’ensemble. Par exemple, le `Property` paramètre de la [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) applet de commande peut spécifier une propriété spécifique définie pour être affichée. Lorsqu’un jeu de propriétés est spécifié, uniquement les propriétés qui appartiennent au jeu sont affichées.

Il n’existe aucune restriction sur le nombre de jeux de propriétés qui peuvent être définis pour un objet. Toutefois, les jeux de propriétés utilisées pour définir les propriétés d’affichage par défaut d’un objet doivent être spécifiés dans le jeu de membres PSStandardMembers. Dans le fichier de types Types.ps1xml, les noms de jeu de propriétés par défaut incluent DefaultDisplayProperty, DefaultDisplayPropertySet et DefaultKeyPropertySet. Les jeux de propriétés supplémentaires que vous ajoutez au jeu de membres PSStandardMembers est ignorés.

Dans l’exemple suivant, le jeu de propriétés DefaultDisplayPropertySet est ajouté au jeu de membres PSStandardMembers de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type. Le [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) élément définit le groupe de propriétés. Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la propriété. Et, le [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) élément spécifie les propriétés de l’ensemble. (Vous pouvez également ajouter le [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) élément aux membres de la [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) élément.)

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

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
