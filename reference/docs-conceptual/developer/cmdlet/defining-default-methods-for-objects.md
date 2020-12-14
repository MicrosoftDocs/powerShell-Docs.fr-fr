---
ms.date: 09/13/2016
ms.topic: reference
title: Définition de méthodes par défaut pour les objets
description: Définition de méthodes par défaut pour les objets
ms.openlocfilehash: c65ca91a7038f32d8c3ef62cfe7881e5ad4dba5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355525"
---
# <a name="defining-default-methods-for-objects"></a>Définition de méthodes par défaut pour les objets

Lorsque vous étendez .NET Framework objets, vous pouvez ajouter des méthodes de code et des méthodes de script aux objets.
Le code XML utilisé pour définir ces méthodes est décrit dans les sections suivantes.

> [!NOTE]
> Les exemples des sections suivantes proviennent du `Types.ps1xml` fichier types dans le répertoire d’installation de Windows PowerShell ( `$PSHOME` ). Pour plus d’informations, consultez [à propos de Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Méthodes de code

Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.

Dans l’exemple suivant, la méthode **ToString** est ajoutée au type de [ nœudSystem.Xml.Xml](/dotnet/api/System.Xml.XmlNode) . L’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) définit la méthode étendue comme une méthode de code. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue. Et, l’élément [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) spécifie la méthode statique. Vous pouvez également ajouter l’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) .

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Méthodes de script

Une méthode de script définit une méthode dont la valeur est la sortie d’un script. Dans l’exemple suivant, la méthode **ConvertToDateTime** est ajoutée au type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . L’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) définit la méthode étendue comme une méthode de script. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue. Et l’élément [script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) spécifie le script qui génère la valeur de la méthode. Vous pouvez également ajouter l’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) .

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
  </Members>
</Type>
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
