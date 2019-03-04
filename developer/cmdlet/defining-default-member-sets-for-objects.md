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
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="659f3-102">Définition de jeux de membres par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="659f3-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="659f3-103">Le jeu de membres PSStandardMembers est utilisé par Windows PowerShell pour définir les jeux de propriétés par défaut pour un objet.</span><span class="sxs-lookup"><span data-stu-id="659f3-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="659f3-104">Les jeux de propriétés par défaut peuvent être utilisés par les commandes telles que les applets de commande de mise en forme pour afficher uniquement les propriétés qui sont définies par le jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="659f3-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="659f3-105">Les jeux de propriétés par défaut incluent DefaultDisplayProperty, DefaultDisplayPropertySet et DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="659f3-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="659f3-106">Windows PowerShell ignore tous les autres jeux de membres et les autres jeux de propriétés ajoutées au jeu de membres PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="659f3-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="659f3-107">Jeu de membres pour System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="659f3-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="659f3-108">Dans l’exemple suivant, le jeu de membres PSStandardMembers définit la propriété DefaultDisplayPropertySet pour [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objets.</span><span class="sxs-lookup"><span data-stu-id="659f3-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="659f3-109">Ce jeu de propriétés est utilisé par le [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="659f3-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="659f3-110">Dans l’exemple suivant, le jeu de membres PSStandardMembers définit la propriété DefaultDisplayPropertySet pour [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objets.</span><span class="sxs-lookup"><span data-stu-id="659f3-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="659f3-111">Ce jeu de propriétés est utilisé par le [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="659f3-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="659f3-112">La sortie suivante montre les propriétés par défaut retournées par la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="659f3-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="659f3-113">Uniquement les `Id`, `Handles`, `CPU`, et `Name` propriétés sont retournées pour chaque objet processus.</span><span class="sxs-lookup"><span data-stu-id="659f3-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="659f3-114">La sortie suivante montre les propriétés par défaut retournées par la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="659f3-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="659f3-115">Uniquement les `Id`, `Handles`, `CPU`, et `Name` propriétés sont retournées pour chaque objet processus.</span><span class="sxs-lookup"><span data-stu-id="659f3-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="659f3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="659f3-116">See Also</span></span>

[<span data-ttu-id="659f3-117">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="659f3-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
