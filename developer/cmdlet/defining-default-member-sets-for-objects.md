---
title: Définition de membre par défaut définit pour les objets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859795"
---
# <a name="defining-default-member-sets-for-objects"></a>Définition de jeux de membres par défaut pour les objets

Le jeu de membres PSStandardMembers est utilisé par Windows PowerShell pour définir les jeux de propriétés par défaut pour un objet. Les jeux de propriétés par défaut peuvent être utilisés par les commandes telles que les applets de commande de mise en forme pour afficher uniquement les propriétés qui sont définies par le jeu de propriétés. Les jeux de propriétés par défaut incluent DefaultDisplayProperty, DefaultDisplayPropertySet et DefaultKeyPropertySet. Windows PowerShell ignore tous les autres jeux de membres et les autres jeux de propriétés ajoutées au jeu de membres PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Jeu de membres pour System.Diagnostics.Process

Dans l’exemple suivant, le jeu de membres PSStandardMembers définit la propriété DefaultDisplayPropertySet pour [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objets. Ce jeu de propriétés est utilisé par le [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande.
Dans l’exemple suivant, le jeu de membres PSStandardMembers définit la propriété DefaultDisplayPropertySet pour [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objets. Ce jeu de propriétés est utilisé par le [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande.

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

La sortie suivante montre les propriétés par défaut retournées par la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande. Uniquement les `Id`, `Handles`, `CPU`, et `Name` propriétés sont retournées pour chaque objet processus.
La sortie suivante montre les propriétés par défaut retournées par la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande. Uniquement les `Id`, `Handles`, `CPU`, et `Name` propriétés sont retournées pour chaque objet processus.

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
