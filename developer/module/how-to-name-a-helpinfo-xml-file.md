---
title: Le nom d’un fichier XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082394"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Guide pratique pour nommer un fichier XML HelpInfo

Cette rubrique explique le format de nom requis pour les fichiers d’informations d’aide actualisable, communément appelé fichiers HelpInfo XML.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Guide pratique pour nommer un fichier XML HelpInfo

Un fichier XML HelpInfo doit avoir un nom au format suivant.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Voici les éléments du nom.

ModuleName la valeur de la **nom** propriété de la **ModuleInfo** de l’objet qui le [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande renvoie.

ModuleGUID la valeur de la **GUID** clés dans le manifeste de module.

Par exemple, si le nom du module est « TestModule » et le GUID du module est bfc1bebf07f9 du a46b 4914 9cabb9ad f2ac, le nom du fichier XML HelpInfo du module serait :

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`