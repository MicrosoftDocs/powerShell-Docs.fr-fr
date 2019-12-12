---
title: Comment importer des applets de commande à l’aide de modules | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364458"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Guide pratique pour importer des applets de commande avec des modules

Cet article explique comment importer des applets de commande dans une session PowerShell à l’aide d’un module binaire.

> [!NOTE]
> Les membres des modules peuvent inclure des applets de commande, des fournisseurs, des fonctions, des variables, des alias et bien plus encore. Les composants logiciels enfichables peuvent contenir uniquement des applets de commande et des fournisseurs.

## <a name="how-to-load-cmdlets-using-a-module"></a>Comment charger des applets de commande à l’aide d’un module

1. Créez un dossier de module portant le même nom que le fichier d’assembly dans lequel les applets de commande sont implémentées. Dans cette procédure, le dossier de module est créé dans le dossier Windows `system32`.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Assurez-vous que la variable d’environnement `PSModulePath` comprend le chemin d’accès à votre nouveau dossier de module. Par défaut, le dossier système est déjà ajouté à la variable d’environnement `PSModulePath`. Pour afficher les `PSModulePath`, tapez : `$env:PSModulePath`.

1. Copiez l’assembly de l’applet de commande dans le dossier du module.

1. Ajoutez un fichier manifeste de module (`.psd1`) dans le dossier racine du module. PowerShell utilise le manifeste de module pour importer votre module. Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](../module/how-to-write-a-powershell-module-manifest.md).

1. Exécutez la commande suivante pour ajouter les applets de commande à la session :

   `Import-Module [Module_Name]`

   Cette procédure peut être utilisée pour tester vos applets de commande. Elle ajoute toutes les applets de commande de l’assembly à la session. Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Voir aussi

[Comment écrire un manifeste de module PowerShell](../module/how-to-write-a-powershell-module-manifest.md)

[Importation d’un module PowerShell](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Installation des modules](../module/installing-a-powershell-module.md)

[Modification du chemin d’installation de PSModulePath](../module/modifying-the-psmodulepath-installation-path.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
