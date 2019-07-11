---
title: Définition de méthodes par défaut des objets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733979"
---
# <a name="defining-default-methods-for-objects"></a>Définition de méthodes par défaut pour les objets

Lorsque vous étendez des objets .NET Framework, vous pouvez ajouter des méthodes de code et les méthodes de script pour les objets. Le code XML qui est utilisé pour définir ces méthodes est décrite dans les sections suivantes.

> [!NOTE]
> Les exemples dans les sections suivantes sont à partir du fichier de types Types.ps1xml dans le répertoire d’installation de Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Méthodes de code

Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.

Dans l’exemple suivant, le **ConvertLargeIntegerToInt64** méthode est ajoutée à la [System.Xml.Xmlnode ? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type. Le [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) élément définit la méthode étendue en tant qu’une méthode de code. Le [nom](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) élément spécifie le nom de la méthode étendue. Et, le [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) élément spécifie la méthode statique. (Vous pouvez également ajouter le [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) élément aux membres de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) élément.)

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Méthodes de script

Une méthode de script définit une méthode dont la valeur est la sortie d’un script. Dans l’exemple suivant, le **ConvertToDateTime** méthode est ajoutée à la [System.Management.Managementobject ? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type. Le [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) élément définit la méthode étendue en tant qu’une méthode de script. Le [nom](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) élément spécifie le nom de la méthode étendue. Et, le [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) élément spécifie le script qui génère la valeur de la méthode. (Vous pouvez également ajouter le [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) élément aux membres de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) élément.)

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
