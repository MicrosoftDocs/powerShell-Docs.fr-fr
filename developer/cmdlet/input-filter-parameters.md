---
title: Paramètres de filtre d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854465"
---
# <a name="input-filter-parameters"></a>Paramètres de filtre d’entrée

Une applet de commande permettre définir `Filter`, `Include`, et `Exclude` paramètres qui filtrent l’ensemble des objets d’entrée qui affecte l’applet de commande.

En règle générale, le jeu d’objets d’entrée est spécifié par un `InputObject`, `Path`, ou `Name` paramètre. Par exemple, une applet de commande peut avoir un `Path` paramètre qui accepte plusieurs chemins d’accès à l’aide des caractères génériques et chaque chemin pointe vers un objet d’entrée. Utilisés conjointement, le `Filter`, `Include`, et `Exclude` davantage de paramètres qualifier les chemins d’accès de l’applet de commande fonctionne sur chaque fois qu’elle est appelée.

## <a name="include-and-exclude-parameters"></a>Inclure et exclure des paramètres

Le `Include` et `Exclude` paramètres identifient les objets qui sont inclus ou exclus de l’ensemble d’objets d’entrée passés à l’applet de commande. Utilisez ces paramètres lorsque le filtre peut être exprimé en langage générique standard. (Pour plus d’informations sur les caractères génériques, consultez [prenant en charge les caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Le `Include` paramètre inclut tous les objets dont les noms correspondent au filtre de l’inclusion. Le `Exclude` paramètre exclut tous les objets dont les noms correspondent au filtre.

## <a name="filter-parameter"></a>Paramètre de filtre

Le `Filter` paramètre spécifie un filtre qui n’est pas exprimé en langage générique standard. Par exemple, les filtres d’Active Directory Service Interfaces (ADSI) ou SQL peuvent être passées à l’applet de commande via son `Filter` paramètre. Dans les applets de commande fournies par Windows PowerShell, ces filtres sont spécifiés par les fournisseurs Windows PowerShell qui utilisent l’applet de commande pour accéder à un magasin de données. Chaque fournisseur définit généralement son propre filtre.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrage si aucun jeu d’objets d’entrée n’est spécifié

Si aucun jeu d’objets d’entrée n’est spécifié, cela signifie généralement filtrer par rapport à tous les objets. Pour plus d’informations, consultez[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)