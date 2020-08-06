---
title: Création de instances d’exécution | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779571"
---
# <a name="creating-runspaces"></a>Création d’instances d’exécution

Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelées par une application hôte. Cet environnement comprend les commandes et les données qui sont actuellement présentes, ainsi que toutes les restrictions de langue qui s’appliquent actuellement.

 Les applications hôtes peuvent utiliser l’instance d’exécution par défaut fournie par Windows PowerShell, qui comprend toutes les commandes de base disponibles, ou créer une instance d’exécution personnalisée qui comprend uniquement un sous-ensemble des commandes disponibles. Pour créer une instance d’exécution personnalisée, vous devez créer un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) et l’assigner à votre instance d’exécution.

## <a name="runspace-tasks"></a>Tâches d’exécution

1. [Création d’un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Création d’une instance d’exécution contrainte](./creating-a-constrained-runspace.md)

3. [Création de plusieurs instances d’exécution](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Voir aussi
