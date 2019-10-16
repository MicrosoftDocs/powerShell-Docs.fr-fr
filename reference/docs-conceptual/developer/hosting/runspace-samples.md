---
title: Exemples d’instances d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360998"
---
# <a name="runspace-samples"></a>Exemples d’instances d’exécution

Cette section comprend un exemple de code qui montre comment utiliser différents types de instances d’exécution pour exécuter des commandes de façon synchrone et asynchrone. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console, puis copier le code à partir des rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

> [!NOTE]
> Pour obtenir des exemples d’applications hôtes qui créent des interfaces hôtes personnalisées, consultez la page [exemples d’hôte personnalisé](./custom-host-samples.md).

 [Exemple Runspace01](./runspace01-sample.md) Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter l’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de façon synchrone et afficher sa sortie dans une fenêtre de console.

 [Exemple Runspace02](./runspace02-sample.md) Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter les applets de commande d' [obtention-processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et de [Tri-objet](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) de façon synchrone. Les résultats de ces commandes s’affichent à l’aide d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

 [Exemple Runspace03](./runspace03-sample.md) Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution. Le script reçoit une liste de noms de processus et récupère ensuite ces processus. Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.

 [Exemple Runspace04](./runspace04-sample.md) Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter des commandes et comment intercepter les erreurs de fin levées lors de l’exécution des commandes. Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide. En conséquence, aucun objet n’est retourné et une erreur de fin est levée.

 [Exemple Runspace05](./runspace05-sample.md) Cet exemple montre comment ajouter un composant logiciel enfichable à un objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) afin que l’applet de commande du composant logiciel enfichable soit disponible lorsque l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une applet de commande Run-proc (définie par l' [exemple GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) qui est exécutée de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Exemple Runspace06](./runspace06-sample.md) Cet exemple montre comment ajouter un module à un objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) afin que le module soit chargé lorsque l’instance d’exécution est ouverte. Le module fournit une applet de commande « obtenir-proc » (définie par l' [exemple GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) qui est exécutée de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Exemple Runspace07](./runspace07-sample.md) Cet exemple montre comment créer une instance d’exécution, puis utiliser cette instance d’exécution pour exécuter deux applets de commande de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Exemple Runspace08](./runspace08-sample.md) Cet exemple montre comment ajouter des commandes et des arguments au pipeline d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) et comment exécuter les commandes de façon synchrone.

 [Exemple Runspace09](./runspace09-sample.md) Cet exemple montre comment ajouter un script au pipeline d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) et comment exécuter le script de manière asynchrone. Des événements sont utilisés pour gérer la sortie du script.

 [Exemple Runspace10](./runspace10-sample.md) Cet exemple montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande à l’aide d’un Objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Exemple Runspace11](./runspace11-sample.md) Cette rubrique montre comment utiliser la classe [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) pour créer une commande de proxy qui appelle une applet de commande existante, mais qui limite l’ensemble des paramètres disponibles. La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte. Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.

## <a name="see-also"></a>Voir aussi
