---
title: Schéma de ressource publique | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080575"
---
# <a name="public-resource-schema"></a>Schéma des ressources publiques

IIS Management OData utilise MOF pour définir les ressources et leurs propriétés. Les propriétés d’une entité de gestion OData correspondent directement aux propriétés du type managé retourné par l’applet de commande sous-jacente.

## <a name="defining-a-resource"></a>Définition d’une ressource

Chaque ressource correspond à un objet retourné par une applet de commande Windows PowerShell. Dans la fichier MOF de la ressource publique, vous définissez une ressource en déclarant une classe. La classe se compose des propriétés qui correspondent aux propriétés de l’objet. Par exemple, dans l’exemple suivant, le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) classe est représentée par le fichier MOF suivant.

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

Chaque nom de propriété est précédé d’un type de données. Dans cet exemple, les types de données correspondent aux types de données primitifs CLR dans .NET Framework, mais les propriétés peuvent être également des références à d’autres ressources ou les types complexes, qui sont tous deux décrits plus loin.

Le `Key` qualificateur indique qu’une propriété est utilisée pour identifier de manière unique une instance de ressource. Une ressource peut avoir plusieurs clés.

Le `Required` qualificateur indique que la propriété est requise. Si une propriété est étiquetée avec le `Key` qualificateur, il est considéré comme requis et le `Required` qualificateur n’est pas nécessaire.

### <a name="complex-data-types"></a>Types de données complexes

Propriétés d’entités peuvent avoir des types de données complexes. Types de données complexes sont des types qui sont composés d’autres types, similaires aux structs dans le langage de programmation C. Un type complexe est déclaré dans le fichier MOF en tant que classe avec le `ComplexType` qualificateur, comme dans l’exemple suivant.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Pour déclarer une propriété d’entité comme un type complexe, vous la déclarer comme un `string` type avec le `EmbeddedInstance` qualificateur, y compris le nom du type complexe. L’exemple suivant illustre la déclaration d’une propriété de la `PswsTest_ProcessModule` type déclaré dans l’exemple précédent.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Association d’entités

Vous pouvez associer les deux entités à l’aide de l’Association et ClasseAssociation qualificateurs. Pour plus d’informations, consultez [associant des entités de gestion OData](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Types dérivés

Vous pouvez dériver un type à partir d’un autre type. Le type dérivé hérite de toutes les propriétés du type dont il dérive en plus des propriétés dérivées explicitement. L’exemple suivant montre une déclaration de type, puis une déclaration de deux types dérivés de ce type.

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```