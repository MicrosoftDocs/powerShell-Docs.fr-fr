---
title: Le nom d’un fichier CAB d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794755"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Guide pratique pour nommer un fichier CAB d’aide actualisable

Cette rubrique explique le format de nom requis pour le fichier CAB de l’aide actualisable (. Fichiers CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Guide pratique pour nommer un fichier CAB d’aide actualisable

Fichier CAB actualisable (. Fichier CAB) doit avoir un nom au format suivant.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Voici les éléments du nom.

ModuleName la valeur de la **nom** propriété de la **ModuleInfo** de l’objet qui le [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande renvoie.

ModuleGUID la valeur de la **GUID** clés dans le manifeste de module.

Culture UICulture l’interface utilisateur des fichiers d’aide dans le fichier CAB. Cette valeur doit correspondre à la valeur de l’un de le **UICulture** éléments dans le fichier XML HelpInfo du module.

Par exemple, si le nom du module est « TestModule », le GUID du module est 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 et la culture d’interface utilisateur est « en-US », le nom du fichier CAB serait :

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`