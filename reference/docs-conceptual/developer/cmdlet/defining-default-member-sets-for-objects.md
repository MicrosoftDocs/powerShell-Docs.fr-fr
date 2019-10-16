---
title: Définition des jeux de membres par défaut pour les objets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369778"
---
# <a name="defining-default-member-sets-for-objects"></a>Définition de jeux de membres par défaut pour les objets

Le jeu de membres PSStandardMembers est utilisé par Windows PowerShell pour définir les jeux de propriétés par défaut d’un objet. Les jeux de propriétés par défaut peuvent être utilisés par des commandes telles que les applets de commande de mise en forme pour afficher uniquement les propriétés définies par le jeu de propriétés. Les jeux de propriétés par défaut sont DefaultDisplayProperty, DefaultDisplayPropertySet et DefaultKeyPropertySet. Windows PowerShell ignore tous les autres jeux de membres et tous les autres jeux de propriétés ajoutés au jeu de membres PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Jeu de membres pour System. Diagnostics. Process

Dans l’exemple suivant, le jeu de membres PSStandardMembers définit le jeu de propriétés DefaultDisplayPropertySet pour les objets [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) . Ce jeu de propriétés est utilisé par l’applet [de commande Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .

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

La sortie suivante montre les propriétés par défaut retournées par l’applet [de commande Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) . Seules les propriétés `Id`, `Handles`, `CPU` et `Name` sont retournées pour chaque objet processus.

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
