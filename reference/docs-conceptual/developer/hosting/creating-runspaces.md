---
title: Création de instances d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367578"
---
# <a name="creating-runspaces"></a>Création d’instances d’exécution

Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelées par une application hôte. Cet environnement comprend les commandes et les données qui sont actuellement présentes, ainsi que toutes les restrictions de langue qui s’appliquent actuellement.

 Les applications hôtes peuvent utiliser l’instance d’exécution par défaut fournie par Windows PowerShell, qui comprend toutes les commandes de base disponibles, ou créer une instance d’exécution personnalisée qui comprend uniquement un sous-ensemble des commandes disponibles. Pour créer une instance d’exécution personnalisée, vous créez un objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) et vous l’affectez à votre instance d’exécution.

## <a name="runspace-tasks"></a>Tâches d’exécution

1. [Création d’un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Création d’une instance d’exécution avec restriction](./creating-a-constrained-runspace.md)

3. [Création de plusieurs instances d’exécution](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Voir aussi
