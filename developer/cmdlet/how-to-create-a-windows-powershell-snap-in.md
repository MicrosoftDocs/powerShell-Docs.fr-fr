---
title: Comment créer un composant logiciel enfichable PowerShell Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067992"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Guide pratique pour créer un composant logiciel enfichable Windows PowerShell

Un composant logiciel enfichable Windows PowerShell fournit un mécanisme pour l’inscription des ensembles d’applets de commande et un autre fournisseur Windows PowerShell avec l’interpréteur de commandes, en étendant les fonctionnalités de l’interpréteur de commandes. Un composant logiciel enfichable Windows PowerShell peut s’inscrire les applets de commande et les fournisseurs dans un assembly unique, ou il peut s’inscrire à une liste spécifique des applets de commande et des fournisseurs.

Assemblys de composant logiciel enfichable doivent être installés dans un répertoire protégé, comme ils le seraient avec d’autres systèmes d’exploitation. Sinon, les utilisateurs malveillants peuvent remplacer un assembly avec du code unsafe.

## <a name="windows-powershell-snap-in-classes"></a>Classes de composant logiciel enfichable PowerShell Windows

Windows PowerShell toutes enfichable classes dérivent les [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.

## <a name="examples"></a>Exemples

[Écriture d’un composant logiciel enfichable PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Cet exemple montre comment créer un composant logiciel enfichable qui est utilisé pour inscrire les applets de commande et les fournisseurs dans un assembly.

[Écriture d’un composant logiciel enfichable PowerShell Windows personnalisée](./writing-a-custom-windows-powershell-snap-in.md): Cet exemple montre comment créer un enfichable personnalisé qui est utilisé pour inscrire un ensemble spécifique d’applets de commande et les fournisseurs qui peuvent ou ne pas existent dans un assembly unique.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[L’inscription des applets de commande](./registering-cmdlets.md)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
