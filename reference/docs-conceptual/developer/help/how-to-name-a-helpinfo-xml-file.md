---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour nommer un fichier XML HelpInfo
description: Guide pratique pour nommer un fichier XML HelpInfo
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659037"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Guide pratique pour nommer un fichier XML HelpInfo

Cette rubrique décrit le format de nom requis pour les fichiers d’informations d’aide pouvant être mis à jour, communément appelés fichiers XML HelpInfo.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Guide pratique pour nommer un fichier XML HelpInfo

Un fichier XML HelpInfo doit avoir un nom au format suivant.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Les éléments du nom sont les suivants.

- `<ModuleName>` -La valeur de la propriété **Name** de l’objet **ModuleInfo** retourné par l’applet de commande [« obten-module »](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .

- `<ModuleGUID>` -La valeur de la clé **GUID** dans le manifeste de module.

Par exemple, si le nom du module est « TestModule » et que le GUID du module est 9cabb9ad-f2ac-4914-A46B-bfc1bebf07f9, le nom du fichier XML HelpInfo du module serait :

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
