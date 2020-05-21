---
title: Comment nommer un fichier CAB d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560557"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Guide pratique pour nommer un fichier CAB d’aide actualisable

Cette rubrique explique le format de nom requis pour le fichier cab d’aide pouvant être mis à jour (. CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Guide pratique pour nommer un fichier CAB d’aide actualisable

Un fichier CAB pouvant être mis à jour (. CAB) doit avoir un nom au format suivant.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Les éléments du nom sont les suivants.

ModuleName la valeur de la propriété **Name** de l’objet **ModuleInfo** [retourné par l’applet de](/powershell/module/Microsoft.PowerShell.Core/Get-Module) commande.

ModuleGUID la valeur de la clé **GUID** dans le manifeste de module.

UICulture la culture d’interface utilisateur des fichiers d’aide dans le fichier CAB. Cette valeur doit correspondre à la valeur de l’un des éléments **UICulture** dans le fichier XML HelpInfo du module.

Par exemple, si le nom du module est « TestModule », le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, et la culture de l’interface utilisateur est « en-US », le nom du fichier CAB est le suivant :

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
