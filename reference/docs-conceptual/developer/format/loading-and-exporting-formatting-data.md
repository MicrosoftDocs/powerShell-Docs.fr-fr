---
title: Chargement et exportation de données de mise en forme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365118"
---
# <a name="loading-and-exporting-formatting-data"></a>Chargement et exportation de données de mise en forme

Une fois que vous avez créé votre fichier de mise en forme, vous devez mettre à jour les données de format de la session en chargeant vos fichiers dans la session active. (Les fichiers de mise en forme fournis par Windows PowerShell sont chargés par les composants logiciels enfichables qui sont inscrits lors de l’ouverture de la session active.) Une fois les données de format de la session active mises à jour, Windows PowerShell utilise ces données pour afficher les objets .NET associés aux affichages définis dans les fichiers de mise en forme chargés. Il n’existe aucune limite au nombre de fichiers de mise en forme que vous pouvez charger dans la session active. En plus de mettre à jour les données de mise en forme, vous pouvez exporter les données de format de la session active dans un fichier de mise en forme.

## <a name="loading-format-data"></a>Chargement de données au format

La mise en forme des fichiers peut être chargée dans la session active à l’aide des méthodes suivantes :

- Vous pouvez importer le fichier de mise en forme dans la session active à partir de la ligne de commande. Utilisez l’applet de commande [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) comme décrit dans la procédure suivante.

- Vous pouvez créer un manifeste de module qui fait référence à votre fichier de mise en forme. Les modules vous permettent d’empaqueter des fichiers de mise en forme pour la distribution. Utilisez l’applet de commande [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) pour créer le manifeste, et l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) pour charger le module dans la session active. Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Vous pouvez créer un composant logiciel enfichable qui fait référence à votre fichier de mise en forme. Utilisez [System. Management. Automation. PSSnapin. formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) pour référencer vos fichiers de mise en forme. Il est vivement recommandé d’utiliser des modules pour empaqueter des applets de commande, ainsi que tous les fichiers de mise en forme et de types associés pour la distribution. Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Si vous appelez des commandes par programme, vous pouvez ajouter une entrée de fichier de mise en forme à l’état de session initial de l’instance d’exécution dans laquelle les commandes sont exécutées. Pour plus d’informations sur le type .NET utilisé pour ajouter le fichier de mise en forme, consultez [System. Management. Automation. instances d’exécution. Sessionstateformatentry ? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) Class.

Lorsqu’un fichier de mise en forme est chargé, il est ajouté à une liste interne que Windows PowerShell utilise pour déterminer la vue à utiliser lors de l’affichage des objets sur la ligne de commande. Vous pouvez ajouter votre fichier de mise en forme au début de la liste, ou vous pouvez l’ajouter à la fin de la liste. Il est important de savoir où votre fichier de mise en forme est ajouté à cette liste si vous chargez un fichier de mise en forme qui définit une vue pour un objet qui a une vue existante définie, par exemple lorsque vous souhaitez modifier la façon dont un objet retourné par une applet de commande Windows PowerShell Core est  présentés. Si vous chargez un fichier de mise en forme qui définit la seule vue d’un objet, vous pouvez utiliser l’une des méthodes décrites précédemment.  Si vous chargez un fichier de mise en forme qui définit une autre vue pour un objet, vous devez utiliser l’applet de commande [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) et ajouter votre fichier au début de la liste.

## <a name="storing-your-formatting-file"></a>Stockage de votre fichier de mise en forme

L’emplacement de stockage des fichiers de mise en forme sur le disque n’est pas obligatoire. Toutefois, il est fortement recommandé de les stocker dans le dossier suivant : `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Chargement d’un fichier de format à l’aide de Import-FormatData

1. Stockez votre fichier de mise en forme sur le disque.

2. Exécutez l’applet de commande [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) à l’aide de l’une des commandes suivantes.

   Pour ajouter votre fichier de mise en forme au début de la liste, utilisez cette commande. Utilisez cette commande si vous modifiez le mode d’affichage d’un objet.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Pour ajouter votre fichier de mise en forme à la fin de la liste, utilisez cette commande.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Une fois que vous avez ajouté un fichier à l’aide de l’applet de commande [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) , vous ne pouvez pas supprimer le fichier de la liste pendant que la session est ouverte. Vous devez fermer la session pour supprimer le fichier de mise en forme de la liste.

## <a name="exporting-format-data"></a>Exportation de données au format

Insérez le corps de la section ici.
