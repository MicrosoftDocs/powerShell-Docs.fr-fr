---
ms.date: 09/13/2016
ms.topic: reference
title: Paramètres de filtre d’entrée
description: Paramètres de filtre d’entrée
ms.openlocfilehash: 419ffea2afb4aa534a3e19ecdfce6d6af1da46a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648538"
---
# <a name="input-filter-parameters"></a>Paramètres de filtre d’entrée

Une applet de commande peut définir `Filter` `Include` `Exclude` des paramètres, et qui filtrent le jeu d’objets d’entrée que l’applet de commande affecte.

En règle générale, le jeu d’objets d’entrée est spécifié par un `InputObject` `Path` paramètre, ou `Name` . Par exemple, une applet de commande peut avoir un `Path` paramètre qui accepte plusieurs chemins d’accès à l’aide de caractères génériques, et chaque chemin d’accès pointe vers un objet d’entrée. Utilisés ensemble, les `Filter` `Include` paramètres, et `Exclude` qualifient plus en détail les chemins d’accès que l’applet de commande utilise chaque fois qu’elle est appelée.

## <a name="include-and-exclude-parameters"></a>Paramètres include et Exclude

Les `Include` `Exclude` paramètres et identifient les objets qui sont inclus ou exclus de l’ensemble d’objets d’entrée passés à l’applet de commande. Utilisez ces paramètres lorsque le filtre peut être exprimé dans le langage générique standard. (Pour plus d’informations sur les caractères génériques, consultez [prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md)commande.) Le `Include` paramètre comprend tous les objets dont les noms correspondent au filtre d’inclusion. Le `Exclude` paramètre exclut tous les objets dont les noms correspondent au filtre.

## <a name="filter-parameter"></a>Paramètre de filtre

Le `Filter` paramètre spécifie un filtre qui n’est pas exprimé dans le langage générique standard. Par exemple, les interfaces de service Active Directory (ADSI) ou les filtres SQL peuvent être passés à l’applet de commande par le biais de son `Filter` paramètre. Dans les applets de commande fournies par Windows PowerShell, ces filtres sont spécifiés par les fournisseurs Windows PowerShell qui utilisent l’applet de commande pour accéder à un magasin de données. Chaque fournisseur définit généralement son propre filtre.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrage si aucun jeu d’objets d’entrée n’est spécifié

Si aucun jeu d’objets d’entrée n’est spécifié, cela signifie généralement que vous filtrez par rapport à tous les objets. Pour plus d’informations, consultez la rubrique[obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
