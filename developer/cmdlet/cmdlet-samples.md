---
title: Exemples d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058043"
---
# <a name="cmdlet-samples"></a>Exemples d’applets de commande

Cette section décrit l’exemple de code qui est fourni dans le Kit de développement logiciel de Windows PowerShell 2.0. Vous pouvez copier le code dans les rubriques de cette section, ou ouvrir les fichiers de code source installés avec le Kit de développement. Le [Kit de développement logiciel (SDK) Windows PowerShell 2.0](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fournit les fichiers Lisez-moi, les fichiers sources et les fichiers de projet Visual Studio pour chaque échantillon. Avec le Kit de développement SDK, vous pouvez trouver les exemples sous la `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` dossier.

## <a name="in-this-section"></a>Dans cette section

[L’exemple GetProcessSample01](./getprocesssample01-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local.

[L’exemple GetProcessSample02](./getprocesssample02-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local. Il fournit un paramètre de nom qui peut être utilisé pour spécifier les processus à récupérer.

[Exemple de GetProcessSample03](./getprocesssample03-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local. Il fournit un paramètre de nom qui peut accepter un objet provenant du pipeline ou une valeur d’une propriété d’un objet dont le nom propriété est le même que le nom du paramètre.

[Exemple de GetProcessSample04](./getprocesssample04-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local. Il génère une erreur sans fin d’exécution si une erreur se produit lors de la récupération d’un processus.

[Exemple de GetProcessSample05](./getprocesssample05-sample.md) cet exemple montre une version complète de l’applet de commande Get-Process.

[Exemple de StopProcessSample01](./stopprocesssample01-sample.md) cet exemple montre comment écrire une applet de commande qui demande des commentaires à l’utilisateur avant d’essayer d’arrêter un processus et comment implémenter un `PassThru` paramètre qui indique que l’utilisateur souhaite que l’applet de commande pour retourner un objet.

[Exemple de StopProcessSample02](./stopprocesssample02-sample.md) cet exemple montre comment écrire une applet de commande écrit debug, verbose et les messages d’avertissement lors de l’arrêt de processus sur l’ordinateur local.

[Exemple de StopProcessSample03](./stopprocesssample03-sample.md) cet exemple montre comment écrire une applet de commande dont les paramètres ont des alias et qui prennent en charge les caractères génériques.

[Exemple de StopProcessSample04](./stopprocesssample04-sample.md) cet exemple montre comment écrire une applet de commande qui déclare les jeux de paramètres, spécifie le paramètre par défaut définie et peut accepter un objet d’entrée.

[Exemple de Events01](./events01-sample.md) cet exemple montre comment créer une applet de commande qui permet à l’utilisateur à s’inscrire pour les événements déclenchés par [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Avec cette applet de commande les utilisateurs peuvent, par exemple, inscrire une action à exécuter quand un fichier est créé dans un répertoire spécifique. Cet exemple dérive le [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe de base.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
