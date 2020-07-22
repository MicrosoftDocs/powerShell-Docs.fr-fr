---
title: Guide pratique pour nommer un fichier XML HelpInfo
ms.date: 09/12/2016
ms.openlocfilehash: 9505a7f66852a569d25ac0c1be86e68f870a7930
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892929"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Guide pratique pour nommer un fichier XML HelpInfo

Cette rubrique décrit le format de nom requis pour les fichiers d’informations d’aide pouvant être mis à jour, communément appelés fichiers XML HelpInfo.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Guide pratique pour nommer un fichier XML HelpInfo

Un fichier XML HelpInfo doit avoir un nom au format suivant.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Les éléments du nom sont les suivants.

- `<ModuleName>`-La valeur de la propriété **Name** de l’objet **ModuleInfo** retourné par l’applet de commande [« obten-module »](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .

- `<ModuleGUID>`-La valeur de la clé **GUID** dans le manifeste de module.

Par exemple, si le nom du module est « TestModule » et que le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, le nom du fichier XML HelpInfo du module serait :

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
