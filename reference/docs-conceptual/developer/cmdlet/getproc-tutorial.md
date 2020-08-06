---
title: Didacticiel GetProc | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cc99cb4de8e3b8fcab8eac28b21162764aecd8a1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784263"
---
# <a name="getproc-tutorial"></a>Tutoriel GetProc

Cette section fournit un didacticiel sur la création d’une applet de commande obtenir-proc qui est très similaire à l’applet de commande [« obtenir-traiter »](/powershell/module/Microsoft.PowerShell.Management/Get-Process) fournie par Windows PowerShell. Ce didacticiel fournit des fragments de code qui illustrent la façon dont les applets de commande sont implémentées, ainsi qu’une explication du code.

## <a name="topics-in-this-tutorial"></a>Rubriques de ce didacticiel

Les rubriques de ce didacticiel sont conçues pour être lues de manière séquentielle, chaque rubrique reposant sur ce qui a été abordé dans la rubrique précédente.

[Création d’une applet de commande sans paramètres](./creating-a-cmdlet-without-parameters.md) Cette section décrit comment créer une applet de commande qui récupère des informations à partir de l’ordinateur local sans utiliser de paramètres, puis écrit les informations dans le pipeline.

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md) Cette section décrit comment ajouter un paramètre à l’applet de commande obtenir-proc afin que l’applet de commande puisse traiter l’entrée en fonction d’objets explicites passés à l’applet de commande. L’implémentation décrite ici récupère les processus en fonction de leur nom, puis écrit les informations dans le pipeline.

[Ajout de paramètres qui traitent l’entrée de pipeline](./adding-parameters-that-process-pipeline-input.md) Cette section décrit comment ajouter un paramètre à l’applet de commande obtenir-proc afin que l’applet de commande puisse traiter les objets qui lui sont transmis via le pipeline. L’applet de commande d’implémentation décrite ici récupère les processus en fonction des objets passés à l’applet de commande, puis écrit les informations dans le pipeline.

[Ajout d’un rapport d’erreurs qui ne se termine pas à votre applet de](./adding-non-terminating-error-reporting-to-your-cmdlet.md) commande Cette section décrit comment ajouter un rapport d’erreurs qui ne se termine pas à une applet de commande. L’implémentation décrite ici détecte les erreurs de non-terminaison qui se produisent lors du traitement de l’entrée et écrit un enregistrement d’erreur dans le flux d’erreurs.

## <a name="see-also"></a>Voir aussi

[Création d’une applet de commande sans paramètre](./creating-a-cmdlet-without-parameters.md)

[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md)

[Ajout de paramètres qui traitent l’entrée du pipeline](./adding-parameters-that-process-pipeline-input.md)

[Ajout d’un rapport d’erreurs qui ne se termine pas à votre applet de commande](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
