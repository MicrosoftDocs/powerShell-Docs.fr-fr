---
title: Exemples de cmdlets | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7a4fb91cb316bf4231df0bb4446b9a7cd54cf647
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89235980"
---
# <a name="cmdlet-samples"></a>Exemples d’applets de commande

Cette section décrit un exemple de code fourni dans le SDK Windows PowerShell 2.0. Vous pouvez copier le code à partir des rubriques de cette section ou ouvrir les fichiers sources installés avec le SDK. Le [Kit de développement logiciel (SDK) de Windows PowerShell 2.0](https://www.microsoft.com/download/details.aspx?id=2560) fournit des fichiers Lisez-moi, des fichiers sources et des fichiers de projet Visual Studio pour chaque exemple. Une fois le SDK installé, vous trouverez les exemples dans le dossier `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

## <a name="in-this-section"></a>Dans cette section

[Exemple GetProcessSample01](./getprocesssample01-sample.md) Cet exemple montre comment écrire une cmdlet qui récupère les processus sur l’ordinateur local.

[Exemple GetProcessSample02](./getprocesssample02-sample.md) Cet exemple montre comment écrire une cmdlet qui récupère les processus sur l’ordinateur local. Il fournit un paramètre Name qui peut être utilisé pour spécifier les processus à récupérer.

[Exemple GetProcessSample03](./getprocesssample03-sample.md) Cet exemple montre comment écrire une cmdlet qui récupère les processus sur l’ordinateur local. Il fournit un paramètre Name qui peut accepter un objet du pipeline ou une valeur à partir d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre.

[Exemple GetProcessSample04](./getprocesssample04-sample.md) Cet exemple montre comment écrire une cmdlet qui récupère les processus sur l’ordinateur local. Il génère une erreur sans fin si une erreur se produit lors de la récupération d’un processus.

[Exemple GetProcessSample05](./getprocesssample05-sample.md) Cet exemple montre une version complète de la cmdlet Get-Proc.

[Exemple StopProcessSample01](./stopprocesssample01-sample.md) Cet exemple montre comment écrire une cmdlet qui demande à l’utilisateur de fournir des commentaires avant de tenter d’arrêter un processus, et comment implémenter un paramètre `PassThru` qui indique que l’utilisateur souhaite que la cmdlet retourne un objet.

[Exemple StopProcessSample02](./stopprocesssample02-sample.md) Cet exemple montre comment écrire une cmdlet qui écrit des messages de débogage, de commentaires et d’avertissement lors de l’arrêt des processus sur l’ordinateur local.

[Exemple StopProcessSample03](./stopprocesssample03-sample.md) Cet exemple montre comment écrire une cmdlet dont les paramètres ont des alias et qui prennent en charge les caractères génériques.

[Exemple StopProcessSample04](./stopprocesssample04-sample.md) Cet exemple montre comment écrire une cmdlet qui déclare des jeux de paramètres, spécifie le jeu de paramètres par défaut et peut accepter un objet d’entrée.

[Exemple Events01](./events01-sample.md) Cet exemple montre comment créer une cmdlet qui permet à l’utilisateur de s’inscrire aux événements déclenchés par [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Avec cette cmdlet, les utilisateurs peuvent, par exemple, inscrire une action à exécuter lorsqu’un fichier est créé dans un répertoire spécifique. Cet exemple est dérivé de la classe de base [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase).

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
