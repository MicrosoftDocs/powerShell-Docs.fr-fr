---
title: Création d’instances d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082938"
---
# <a name="creating-runspaces"></a>Création d’instances d’exécution

Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelés par une application hôte. Cet environnement inclut les commandes et les données qui sont actuellement présentes et des restrictions de langue qui s’appliquent actuellement.

 Héberger des applications peuvent utiliser l’instance d’exécution par défaut qui est fournie par Windows PowerShell, qui inclut toutes les commandes de cœur disponible, ou créez une instance d’exécution personnalisée qui inclut uniquement un sous-ensemble des commandes disponibles. Pour créer une instance d’exécution personnalisée, vous créez un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de l’objet et l’assigner à votre instance d’exécution.

## <a name="runspace-tasks"></a>Tâches de l’instance d’exécution

1. [Création d’un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Création d’une instance d’exécution contrainte](./creating-a-constrained-runspace.md)

3. [Création de plusieurs instances d’exécution](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Voir aussi
