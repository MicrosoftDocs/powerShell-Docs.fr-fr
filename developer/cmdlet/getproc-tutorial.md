---
title: Didacticiel de GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068094"
---
# <a name="getproc-tutorial"></a>Tutoriel GetProc

Cette section fournit un didacticiel pour la création d’une applet de commande Get-Process qui est très similaire à la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande fournie par Windows PowerShell. Ce didacticiel fournit des fragments de code qui illustrent la façon dont les applets de commande sont implémentées et une explication du code.

## <a name="topics-in-this-tutorial"></a>Rubriques de ce didacticiel

Les rubriques de ce didacticiel sont conçus pour être lu de manière séquentielle, avec chaque rubrique hommage à ce qui a été présenté dans la rubrique précédente.

[Création d’une applet de commande sans paramètres](./creating-a-cmdlet-without-parameters.md) cette section décrit comment créer une applet de commande qui Récupère des informations à partir de l’ordinateur local sans l’utilisation de paramètres, puis écrit les informations dans le pipeline.

[Ajout de paramètres de processus de ligne de commande Input](./adding-parameters-that-process-command-line-input.md) cette section décrit comment ajouter un paramètre à l’applet de commande Get-Process afin que l’applet de commande peut traiter des données basés sur des objets explicites passés à l’applet de commande. L’implémentation décrite ici récupère les processus en fonction de leur nom, puis écrit les informations dans le pipeline.

[Ajout de paramètres de cette entrée de Pipeline de processus](./adding-parameters-that-process-pipeline-input.md) cette section décrit comment ajouter un paramètre à l’applet de commande Get-Process afin que l’applet de commande peut traiter les objets transmis via le pipeline. L’applet de commande de mise en œuvre décrite ici récupère des processus basés sur les objets passés à l’applet de commande, puis écrit les informations dans le pipeline.

[Ajout de rapports d’erreurs sans fin d’exécution à votre applet de commande](./adding-non-terminating-error-reporting-to-your-cmdlet.md) cette section décrit comment ajouter des rapports à une applet de commande d’erreurs sans fin d’exécution. L’implémentation décrite ici détecte les erreurs qui se produisent lors du traitement d’entrée et écrit un enregistrement d’erreur dans le flux d’erreurs.

## <a name="see-also"></a>Voir aussi

[Création d’une applet de commande sans paramètres](./creating-a-cmdlet-without-parameters.md)

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Ajout de paramètres d’entrée de Pipeline de processus](./adding-parameters-that-process-pipeline-input.md)

[Ajout de rapports à votre applet de commande d’erreurs sans fin d’exécution](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
