---
ms.date: 09/13/2016
ms.topic: reference
title: Définition de jeux de membres par défaut pour les objets
description: Définition de jeux de membres par défaut pour les objets
ms.openlocfilehash: 919f7ba65322c6a56a27e046fb211bde151abf7d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653129"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="418ce-103">Définition de jeux de membres par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="418ce-103">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="418ce-104">Le jeu de membres PSStandardMembers est utilisé par Windows PowerShell pour définir les jeux de propriétés par défaut d’un objet.</span><span class="sxs-lookup"><span data-stu-id="418ce-104">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="418ce-105">Les jeux de propriétés par défaut peuvent être utilisés par des commandes telles que les applets de commande de mise en forme pour afficher uniquement les propriétés définies par le jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="418ce-105">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="418ce-106">Les jeux de propriétés par défaut sont DefaultDisplayProperty, DefaultDisplayPropertySet et DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="418ce-106">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="418ce-107">Windows PowerShell ignore tous les autres jeux de membres et tous les autres jeux de propriétés ajoutés au jeu de membres PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="418ce-107">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="418ce-108">Jeu de membres pour System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="418ce-108">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="418ce-109">Dans l’exemple suivant, le jeu de membres PSStandardMembers définit le jeu de propriétés DefaultDisplayPropertySet pour les objets [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="418ce-109">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="418ce-110">Ce jeu de propriétés est utilisé par l’applet [de commande Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="418ce-110">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="418ce-111">La sortie suivante montre les propriétés par défaut retournées par l’applet [de commande Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="418ce-111">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="418ce-112">Seules les `Id` `Handles` Propriétés,, `CPU` et `Name` sont retournées pour chaque objet processus.</span><span class="sxs-lookup"><span data-stu-id="418ce-112">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="418ce-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="418ce-113">See Also</span></span>

[<span data-ttu-id="418ce-114">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="418ce-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
