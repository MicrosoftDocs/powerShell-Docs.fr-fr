---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour créer un composant logiciel enfichable Windows PowerShell
description: Guide pratique pour créer un composant logiciel enfichable Windows PowerShell
ms.openlocfilehash: 29394ebcd2f7c4a547aabcb88685ff494b2c381d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657268"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Guide pratique pour créer un composant logiciel enfichable Windows PowerShell

Un composant logiciel enfichable Windows PowerShell fournit un mécanisme permettant d’inscrire des ensembles d’applets de commande et un autre fournisseur Windows PowerShell avec l’interpréteur de commandes, étendant ainsi les fonctionnalités de l’interpréteur de commandes. Un composant logiciel enfichable Windows PowerShell peut inscrire toutes les applets de commande et tous les fournisseurs dans un assembly unique, ou il peut inscrire une liste spécifique d’applets de commande et de fournisseurs.

Les assemblys de composant logiciel enfichable doivent être installés dans un répertoire protégé, de la même façon qu’avec d’autres systèmes d’exploitation. Dans le cas contraire, les utilisateurs malveillants peuvent remplacer un assembly par du code non sécurisé.

## <a name="windows-powershell-snap-in-classes"></a>Classes du composant logiciel enfichable Windows PowerShell

Toutes les classes de composant logiciel enfichable Windows PowerShell dérivent des classes [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

## <a name="examples"></a>Exemples

[Écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable qui est utilisé pour inscrire toutes les applets de commande et tous les fournisseurs dans un assembly.

[Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé](./writing-a-custom-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable personnalisé qui est utilisé pour inscrire un ensemble spécifique d’applets de commande et de fournisseurs qui peuvent ou non exister dans un assembly unique.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Inscription des applets de commande](./registering-cmdlets.md)

[Kit SDK Windows PowerShell](../windows-powershell-reference.md)
