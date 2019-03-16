---
title: État de Session Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059539"
---
# <a name="windows-powershell-session-state"></a>État de session Windows PowerShell

État de session fait référence à la configuration actuelle d’une session Windows PowerShell ou d’un module. Une session Windows PowerShell est l’environnement d’exploitation qui est utilisé de manière interactive par l’utilisateur en ligne de commande ou par programme par une application hôte. L’état de session pour une session est appelé l’état de session global.

À partir d’un point de vue du développeur, une session Windows PowerShell fait référence à la durée entre lorsqu’une application hôte ouvre une instance d’exécution Windows PowerShell et lorsqu’il ferme l’instance d’exécution. Examiné une autre façon, la session est la durée de vie d’une instance du moteur Windows PowerShell qui est appelée alors que l’instance d’exécution existe.

## <a name="module-session-state"></a>État de Session de module

États de session de module sont créés chaque fois que le module ou l’un de ses modules imbriqués est importé dans la session. Lorsqu’un module exporte un élément tel qu’une applet de commande, une fonction ou un script, une référence à cet élément est ajoutée à l’état de session global de la session. Toutefois, lorsque l’élément est exécuté, il est exécuté au sein de l’état de session du module.

## <a name="session-state-data"></a>Données d’état de session

Données d’état de session peuvent être public ou privé. Données publiques sont disponibles pour les appels depuis l’extérieur de l’état de session tandis que les données privées sont disponibles uniquement pour les appels à partir de l’état de session. Par exemple, un module peut avoir une fonction privée qui peut être appelée uniquement par le module uniquement en interne ou par un élément publique qui a été exporté. Cela est similaire aux membres privés et publics d’un type .NET Framework.

Données d’état de session sont stockées par l’instance actuelle du moteur d’exécution dans le contexte de la session Windows PowerShell. Données d’état de session se composent des éléments suivants :

- Informations de chemin d’accès

- Informations sur le lecteur

- Informations sur le fournisseur Windows PowerShell

- Informations sur les modules importés et les références aux éléments de module (par exemple, les applets de commande, des fonctions et des scripts) qui sont exportées par le module. Ces informations et ces références sont pour l’état de session global uniquement.

- Informations de variable d’état de session

## <a name="accessing-session-state-data-within-cmdlets"></a>L’accès aux données d’état de Session dans les applets de commande

Applets de commande peuvent accéder aux données de l’état de session soit indirectement par le biais du [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) propriété de la classe de l’applet de commande ou directement via le [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe. Le [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fournit des propriétés qui peuvent être utilisées pour examiner les différents types de données d’état de session.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Applets de commande Windows PowerShell](./cmdlet-overview.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
