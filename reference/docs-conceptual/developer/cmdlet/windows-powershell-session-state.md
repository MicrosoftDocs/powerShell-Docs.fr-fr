---
title: État de session Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.openlocfilehash: 7436e3ebd0e099ead81f9fea01a0a2994b982213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783940"
---
# <a name="windows-powershell-session-state"></a>État de session Windows PowerShell

L’état de session fait référence à la configuration actuelle d’une session ou d’un module Windows PowerShell. Une session Windows PowerShell est l’environnement d’exploitation qui est utilisé de manière interactive par l’utilisateur de la ligne de commande ou par programme par une application hôte. L’état de session d’une session est appelé état de session global.

Du point de vue du développeur, une session Windows PowerShell fait référence au délai entre le moment où une application hôte ouvre une instance d’exécution Windows PowerShell et le moment où elle ferme l’instance d’exécution. Vu d’une autre façon, la session est la durée de vie d’une instance du moteur Windows PowerShell qui est appelée alors que l’instance d’exécution existe.

## <a name="module-session-state"></a>État de session de module

Les États de session de module sont créés chaque fois que le module ou l’un de ses modules imbriqués est importé dans la session. Lorsqu’un module exporte un élément tel qu’une applet de commande, une fonction ou un script, une référence à cet élément est ajoutée à l’état de session global de la session. Toutefois, lorsque l’élément est exécuté, il est exécuté dans l’état de session du module.

## <a name="session-state-data"></a>Données d’état de session

Les données d’état de session peuvent être publiques ou privées. Les données publiques sont disponibles pour les appels en dehors de l’état de session, tandis que les données privées sont uniquement disponibles pour les appels à partir de l’état de session. Par exemple, un module peut avoir une fonction privée qui peut être appelée uniquement par le module ou uniquement en interne par un élément public qui a été exporté. Cela est similaire aux membres privés et publics d’un type de .NET Framework.

Les données d’état de session sont stockées par l’instance actuelle du moteur d’exécution dans le contexte de la session Windows PowerShell actuelle. Les données d’état de session se composent des éléments suivants :

- Informations sur le chemin

- Informations sur le lecteur

- Informations sur le fournisseur Windows PowerShell

- Informations sur les modules importés et les références aux éléments de module (tels que les applets de commande, les fonctions et les scripts) qui sont exportées par le module. Ces informations et ces références concernent uniquement l’état de session global.

- Informations sur les variables d’état de session

## <a name="accessing-session-state-data-within-cmdlets"></a>Accès aux données d’état de session dans les applets de commande

Les applets de commande peuvent accéder aux données d’état de session, soit indirectement par le biais de la propriété [System. Management. Automation. PSCmdlet. SessionState *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) de la classe cmdlet, soit directement via la classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) . La classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) fournit des propriétés qui peuvent être utilisées pour examiner les différents types de données d’état de session.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. PSCmdlet. SessionState](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System. Management. Automation. SessionState ? Displayproperty = FullName](/dotnet/api/System.Management.Automation.SessionState)

[Applets de commande Windows PowerShell](./cmdlet-overview.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Kit de développement logiciel Windows PowerShell Shell](../windows-powershell-reference.md)
