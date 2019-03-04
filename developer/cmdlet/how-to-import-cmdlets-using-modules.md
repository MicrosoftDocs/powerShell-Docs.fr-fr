---
title: Comment importer les applets de commande à l’aide de Modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859145"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Guide pratique pour importer des applets de commande avec des modules

Cette rubrique décrit comment importer les applets de commande à une session Windows PowerShell à l’aide d’un module binaire.

> [!NOTE]
> Les membres des modules peuvent inclure des applets de commande, fournisseurs, fonctions, des variables, alias et bien plus encore. Composants logiciel enfichables peuvent contenir uniquement des applets de commande et des fournisseurs.

## <a name="how-to-load-cmdlets-using-a-module"></a>Comment charger des applets de commande à l’aide d’un module

1. Créez un dossier de module qui porte le même nom que le fichier d’assembly dans lequel les applets de commande sont implémentées. Dans cette procédure, le dossier de module est créé dans le `system32` dossier.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Assurez-vous que le `PSModulePath` variable d’environnement inclut le chemin d’accès à votre nouveau dossier de module. Par défaut, le dossier du système est déjà ajouté à la `PSModulePath` variable d’environnement.

3. Copiez l’assembly de l’applet de commande dans le dossier de module.

4. Exécutez la commande suivante pour ajouter les applets de commande à la session :

   `import-module [Module_Name]`

   Cette procédure peut être utilisée pour tester vos applets de commande. Il ajoute toutes les applets de commande dans l’assembly à la session. Pour plus d’informations sur les modules, consultez les différents types de modules, les différentes façons de charger des modules et comment limiter les éléments d’un module sont exportées, [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Installation des Modules](../module/installing-a-powershell-module.md)