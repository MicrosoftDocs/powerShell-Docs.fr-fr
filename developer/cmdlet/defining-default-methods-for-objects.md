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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861405"
---
# <a name="defining-default-methods-for-objects"></a>Définition de méthodes par défaut pour les objets

Lorsque vous étendez des objets .NET Framework, vous pouvez ajouter des méthodes de code et les méthodes de script pour les objets. Le code XML qui est utilisé pour définir ces méthodes est décrite dans les sections suivantes.

> [!NOTE]
> Les exemples dans les sections suivantes sont à partir du fichier de types Types.ps1xml dans le répertoire d’installation de Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Méthodes de code

Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.

Dans l’exemple suivant, le **ConvertLargeIntegerToInt64** méthode est ajoutée à la [System.Xml.Xmlnode ? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type. Le [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) élément définit la méthode étendue en tant qu’une méthode de code. Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la méthode étendue. Et, le [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) élément spécifie la méthode statique. (Vous pouvez également ajouter le [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)

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

Une méthode de script définit une méthode dont la valeur est la sortie d’un script. Dans l’exemple suivant, le **ConvertToDateTime** méthode est ajoutée à la [System.Management.Managementobject ? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type. Le [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) élément définit la méthode étendue en tant qu’une méthode de script. Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la méthode étendue. Et, le [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) élément spécifie le script qui génère la valeur de la méthode. (Vous pouvez également ajouter le [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)

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