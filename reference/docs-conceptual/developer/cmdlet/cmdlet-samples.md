---
title: Exemples d’applets de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365878"
---
# <a name="cmdlet-samples"></a>Exemples d’applets de commande

Cette section décrit un exemple de code fourni dans le kit de développement logiciel (SDK) Windows PowerShell 2,0. Vous pouvez copier le code à partir des rubriques de cette section ou ouvrir les fichiers sources installés avec le kit de développement logiciel (SDK). Le [Kit de développement logiciel (SDK) de Windows PowerShell 2,0](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fournit des fichiers Lisez-moi, des fichiers sources et des fichiers de projet Visual Studio pour chaque exemple. Avec le kit de développement logiciel (SDK) installé, vous trouverez les exemples dans le dossier `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

## <a name="in-this-section"></a>Dans cette section

[Exemple GetProcessSample01](./getprocesssample01-sample.md) Cet exemple montre comment écrire une applet de commande qui récupère les processus sur l’ordinateur local.

[Exemple GetProcessSample02](./getprocesssample02-sample.md) Cet exemple montre comment écrire une applet de commande qui récupère les processus sur l’ordinateur local. Il fournit un paramètre Name qui peut être utilisé pour spécifier les processus à récupérer.

[Exemple GetProcessSample03](./getprocesssample03-sample.md) Cet exemple montre comment écrire une applet de commande qui récupère les processus sur l’ordinateur local. Il fournit un paramètre Name qui peut accepter un objet du pipeline ou une valeur d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre.

[Exemple GetProcessSample04](./getprocesssample04-sample.md) Cet exemple montre comment écrire une applet de commande qui récupère les processus sur l’ordinateur local. Elle génère une erreur sans fin d’exécution si une erreur se produit lors de la récupération d’un processus.

[Exemple GetProcessSample05](./getprocesssample05-sample.md) Cet exemple montre une version complète de l’applet de commande obtenir-proc.

[Exemple StopProcessSample01](./stopprocesssample01-sample.md) Cet exemple montre comment écrire une applet de commande qui demande des commentaires à l’utilisateur avant de tenter d’arrêter un processus, et comment implémenter un paramètre `PassThru` qui indique que l’utilisateur souhaite que l’applet de commande retourne un objet.

[Exemple StopProcessSample02](./stopprocesssample02-sample.md) Cet exemple montre comment écrire une applet de commande qui écrit des messages de débogage, de commentaires et d’avertissement lors de l’arrêt des processus sur l’ordinateur local.

[Exemple StopProcessSample03](./stopprocesssample03-sample.md) Cet exemple montre comment écrire une applet de commande dont les paramètres ont des alias et qui prennent en charge les caractères génériques.

[Exemple StopProcessSample04](./stopprocesssample04-sample.md) Cet exemple montre comment écrire une applet de commande qui déclare des jeux de paramètres, spécifie le jeu de paramètres par défaut et peut accepter un objet d’entrée.

[Exemple Events01](./events01-sample.md) Cet exemple montre comment créer une applet de commande qui permet à l’utilisateur de s’inscrire aux événements déclenchés par [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Avec cette applet de commande, les utilisateurs peuvent, par exemple, inscrire une action à exécuter lorsqu’un fichier est créé sous un répertoire spécifique. Cet exemple dérive de la classe de base [Microsoft. PowerShell. Commands. Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
