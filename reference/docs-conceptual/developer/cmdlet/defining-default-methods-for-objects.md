---
title: Définition des méthodes par défaut pour les objets | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 10917de9e897fc1eed362430d63ff5b9cb7e813d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774590"
---
# <a name="defining-default-methods-for-objects"></a>Définition de méthodes par défaut pour les objets

Lorsque vous étendez .NET Framework objets, vous pouvez ajouter des méthodes de code et des méthodes de script aux objets.
Le code XML utilisé pour définir ces méthodes est décrit dans les sections suivantes.

> [!NOTE]
> Les exemples des sections suivantes proviennent du `Types.ps1xml` fichier types dans le répertoire d’installation de Windows PowerShell ( `$PSHOME` ). Pour plus d’informations, consultez [à propos de Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Méthodes de code

Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.

Dans l’exemple suivant, la méthode **ToString** est ajoutée au type de [nœudSystem.Xml.Xml](/dotnet/api/System.Xml.XmlNode) . L’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) définit la méthode étendue comme une méthode de code. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue. Et, l’élément [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) spécifie la méthode statique. Vous pouvez également ajouter l’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

Une méthode de script définit une méthode dont la valeur est la sortie d’un script. Dans l’exemple suivant, la méthode **ConvertToDateTime** est ajoutée au type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . L’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) définit la méthode étendue comme une méthode de script. L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue. Et l’élément [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) spécifie le script qui génère la valeur de la méthode. Vous pouvez également ajouter l’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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
