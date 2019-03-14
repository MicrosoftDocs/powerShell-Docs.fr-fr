---
title: Le chargement et l’exportation de données mise en forme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 86a0e8b7e8967280daa57faf5c323efcd3b1368b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794193"
---
# <a name="loading-and-exporting-formatting-data"></a>Chargement et exportation de données de mise en forme

Une fois que vous avez créé votre fichier de mise en forme, vous devez mettre à jour les données de format de la session en chargeant vos fichiers dans la session active. (Les fichiers de mise en forme fournies par Windows PowerShell sont chargés par des composants logiciels enfichables qui sont enregistrés lorsque la session active est ouvert.) Une fois que les données de format de la session active sont mis à jour, Windows PowerShell utilise ces données pour afficher les objets .NET associés aux affichages définis dans les fichiers de mise en forme chargés. Il n’existe aucune limite au nombre de fichiers de mise en forme que vous pouvez charger dans la session active. En plus de la mise à jour les données de mise en forme, vous pouvez exporter les données de format dans la session active dans un fichier de mise en forme.

## <a name="loading-format-data"></a>Chargement des données de format

Fichiers de mise en forme peuvent être chargées dans la session active à l’aide des méthodes suivantes :

- Vous pouvez importer le fichier de mise en forme dans la session active à partir de la ligne de commande. Utilisez le [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) applet de commande comme décrit dans la procédure suivante.

- Vous pouvez créer un manifeste de module qui fait référence à votre fichier de mise en forme. Modules permettent de vous mise en forme de fichiers pour la distribution du package. Utilisez le [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) applet de commande pour créer le manifeste et le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande pour charger le module dans la session active. Pour plus d’informations sur les modules, consultez [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).

- Vous pouvez créer un composant logiciel enfichable qui fait référence à votre fichier de mise en forme. Utilisez le [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) à référencer vos fichiers de mise en forme. Il est vivement recommandé d’utiliser des modules aux applets de commande de package et la mise en forme associée et des fichiers de types pour la distribution. Pour plus d’informations sur les modules, consultez [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).

- Si vous appelez des commandes par programmation, vous pouvez ajouter une entrée de fichier de mise en forme à l’état de session initiale de l’instance d’exécution où les commandes sont exécutées. Pour plus d’informations sur le type .NET utilisé pour ajouter le fichier de mise en forme, consultez la [System.Management.Automation.Runspaces.Sessionstateformatentry ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) classe.

Quand un fichier de mise en forme est chargé, il est ajouté à une liste interne que Windows PowerShell utilise pour déterminer la vue à utiliser lors de l’affichage des objets sur la ligne de commande. Vous pouvez ajouter votre fichier de mise en forme au début de la liste, ou vous pouvez l’ajouter à la fin de la liste. Il est important si vous chargez des fichiers de mise en forme qui définit une vue pour un objet qui a une vue existante définie, par exemple lorsque vous souhaitez modifier la façon dont un objet qui est retourné par une applet de commande Windows PowerShell core est de savoir où votre fichier de mise en forme est ajoutée à cette liste  affiché. Si vous chargez un fichier de mise en forme qui définit la vue uniquement pour un objet, vous pouvez utiliser une des méthodes décrites précédemment.  Si vous chargez un fichier de mise en forme qui définit une autre vue pour un objet, vous devez utiliser le [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) applet de commande et ajoutez au début de votre fichier au début de la liste.

## <a name="storing-your-formatting-file"></a>Stockage de votre fichier de mise en forme

Il n’existe aucune exigence d’où vos fichiers de mise en forme sont stockés sur le disque. Toutefois, il est fortement recommandé de les stocker dans le dossier suivant : `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Chargement d’un fichier de format à l’aide d’importation-FormatData

1. Store de votre fichier de mise en forme sur le disque.

2. Exécutez le [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) applet de commande en utilisant l’une des commandes suivantes.

   Pour ajouter votre mise en forme de fichier au début de la liste utiliser cette commande. Utilisez cette commande si vous modifiez la façon dont un objet est affiché.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Pour ajouter votre mise en forme de fichier à la fin de la liste utiliser cette commande.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Une fois que vous avez ajouté un fichier en utilisant le [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) applet de commande, vous ne pouvez pas supprimer le fichier dans la liste alors que la session est ouverte. Vous devez fermer la session pour supprimer le fichier de mise en forme dans la liste.

## <a name="exporting-format-data"></a>Exportation de données de format

Insérez le corps de la section ici.
