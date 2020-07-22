---
title: Guide pratique pour nommer un fichier CAB d’aide actualisable
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892997"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Guide pratique pour nommer un fichier CAB d’aide actualisable

Cette rubrique explique le format de nom requis pour les fichiers CAB de l’aide actualisable ( `.CAB` ).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Guide pratique pour nommer un fichier CAB d’aide actualisable

Un fichier cabinet () pouvant être mis `.CAB` à jour doit avoir un nom au format suivant.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Les éléments du nom sont les suivants.

- `<ModuleName>`-La valeur de la propriété **Name** de l’objet **ModuleInfo** retourné par l’applet de commande [« obten-module »](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .
- `<ModuleGUID>`-La valeur de la clé **GUID** dans le manifeste de module.
- `<UICulture>`-La culture d’interface utilisateur des fichiers d’aide dans le fichier CAB. Cette valeur doit correspondre à la valeur de l’un des éléments **UICulture** dans le fichier XML HelpInfo du module.

Par exemple, si le nom du module est « TestModule », le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, et la culture de l’interface utilisateur est « en-US », le nom du fichier CAB est le suivant :

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
