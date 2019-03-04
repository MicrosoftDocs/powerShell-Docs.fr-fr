---
title: Exemples de l’instance d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857335"
---
# <a name="runspace-samples"></a>Exemples d’instances d’exécution

Cette section inclut des exemples de code qui montre comment utiliser différents types d’instances d’exécution pour exécuter des commandes de façon synchrone et asynchrone. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console puis copier le code dans les rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

> [!NOTE]
> Pour obtenir des exemples d’applications hôtes qui créent des interfaces de l’hôte personnalisé, consultez [exemples d’hôtes personnalisés](./custom-host-samples.md).

 [Runspace01 exemple](./runspace01-sample.md) cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande synchrone et afficher sa sortie dans une console fenêtre.

 [Exemple de Runspace02](./runspace02-sample.md) cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) applets de commande de façon synchrone. Les résultats de ces commandes s’affiche à l’aide un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) contrôle.

 [Exemple de Runspace03](./runspace03-sample.md) cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution. Le script reçoit une liste de noms de processus et récupère ensuite ces processus. Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.

 [Exemple de Runspace04](./runspace04-sample.md) cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter des commandes et comment intercepter les erreurs avec fin d’exécution qui sont levées pendant l’exécution de commandes. Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide. Par conséquent aucuns objets ne sont retournés et une erreur avec fin d’exécution est levée.

 [Exemple de Runspace05](./runspace05-sample.md) cet exemple montre comment ajouter un composant logiciel enfichable à une [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet afin que l’applet de commande de l’utilisation du composant logiciel enfichable est disponible lorsque l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une applet de commande Get-Process (définie par le [exemple GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) qui est exécutée de façon synchrone à l’aide un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

 [Exemple de Runspace06](./runspace06-sample.md) cet exemple montre comment ajouter un module à un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) afin que le module est chargé de l’ouverture de l’instance d’exécution de l’objet. Le module fournit une applet de commande Get-Process (définie par le [exemple GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) qui est exécutée de façon synchrone à l’aide un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

 [Exemple de Runspace07](./runspace07-sample.md) cet exemple montre comment créer une instance d’exécution et ensuite utiliser cette instance d’exécution pour exécuter deux applets de commande de façon synchrone à l’aide un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

 [Exemple de Runspace08](./runspace08-sample.md) cet exemple montre comment ajouter des commandes et arguments au pipeline d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet et comment exécuter les commandes de façon synchrone.

 [Exemple de Runspace09](./runspace09-sample.md) cet exemple montre comment ajouter un script au pipeline d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet et comment exécuter le script de façon asynchrone. Des événements sont utilisés pour gérer la sortie du script.

 [Runspace10 exemple](./runspace10-sample.md) cet exemple montre comment créer un état de session initial par défaut, l’ajout d’une applet de commande pour le [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), comment créer une instance d’exécution qui utilise le état de session initial et comment exécuter la commande en utilisant un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

 [Exemple de Runspace11](./runspace11-sample.md) cet exemple montre comment utiliser le [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) classe pour créer une commande de proxy qui appelle une applet de commande existante, mais limite l’ensemble des paramètres disponibles. La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte. Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.

## <a name="see-also"></a>Voir aussi
