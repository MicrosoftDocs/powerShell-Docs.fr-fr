---
title: Types de sortie de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853925"
---
# <a name="types-of-cmdlet-output"></a>Types de sortie de l’applet de commande

PowerShell fournit plusieurs méthodes qui peuvent être appelées par les applets de commande pour générer la sortie. Ces méthodes utilisent une opération spécifique à écrire leur sortie dans un flux de données spécifiques, telles que le flux de données de réussite ou le flux de données d’erreur. Cet article décrit les types de sortie et les méthodes utilisées pour les générer.

## <a name="types-of-output"></a>Types de sortie

### <a name="success-output"></a>Sortie réussie

Applets de commande peut signaler la réussite en retournant un objet qui peut être traité par la commande suivante dans le pipeline. Une fois que l’applet de commande a exécuté avec succès de son action, l’applet de commande appelle le [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode). Nous vous recommandons d’appeler cette méthode au lieu du [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) ou [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) méthodes.

Vous pouvez fournir un **PassThru** changez le paramètre pour les applets de commande qui ne retournent pas généralement les objets.
Lorsque le **PassThru** du paramètre de commutateur est spécifié sur la ligne de commande, l’applet de commande doit retourner un objet. Pour obtenir un exemple d’applet de commande qui a un **PassThru** paramètre, consultez [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Sortie d’erreur

Applets de commande peuvent signaler les erreurs. En cas d’erreur avec fin d’exécution, l’applet de commande lève une exception. Lorsqu’une erreur sans fin d’exécution se produit, l’applet de commande appelle le [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) méthode pour envoyer un enregistrement d’erreur dans le flux de données d’erreur. Pour plus d’informations sur le rapport d’erreurs, consultez [Concepts de création de rapports d’erreur](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Sortie détaillée

Applets de commande peuvent fournir des informations utiles pour vous alors que l’applet de commande traite correctement les enregistrements en appelant le [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (méthode). La méthode génère des messages détaillés qui indiquent la façon dont l’action s’exécute.

Par défaut, les messages détaillés ne sont pas affichés. Vous pouvez spécifier le **Verbose** paramètre lors de l’exécution de l’applet de commande pour afficher ces messages. **Verbose** est un paramètre commun qui est disponible pour toutes les applets de commande.

### <a name="progress-output"></a>Sortie de la progression

Applets de commande peut fournir des informations de progression pour vous lors de l’applet de commande effectue des tâches qui prennent un certain temps, telles que la copie d’un répertoire de manière récursive. Pour afficher des informations de progression l’applet de commande appelle le [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (méthode).

### <a name="debug-output"></a>Sortie de débogage

Applets de commande peuvent fournir des messages de débogage qui sont utiles lors du dépannage le code de l’applet de commande. Pour afficher des informations de débogage l’applet de commande appelle le [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (méthode).

Par défaut, les messages de débogage ne sont pas affichés. Vous pouvez spécifier le **déboguer** paramètre lors de l’exécution de l’applet de commande pour afficher ces messages. **Déboguer** est un paramètre commun qui est disponible pour toutes les applets de commande.

### <a name="warning-output"></a>Sortie de l’avertissement

Applets de commande peut afficher des messages d’avertissement en appelant le [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) (méthode).

Par défaut, les messages d’avertissement sont affichés. Toutefois, vous pouvez configurer des messages d’avertissement à l’aide de la `$WarningPreference` variable ou à l’aide de la **Verbose** et **déboguer** paramètres lors de l’applet de commande est appelée.

## <a name="displaying-output"></a>Affichage de sortie

Pour tous les appels de méthode d’écriture, l’affichage de contenu est déterminé par les variables d’exécution spécifique. L’exception est le [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode). À l’aide de ces variables, vous pouvez rendre approprié écrire un appel à l’endroit approprié dans votre code et sans vous soucier lorsqu’ou si la sortie doit être affichée.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>L’accès à la fonctionnalité de sortie d’une application hôte

Vous pouvez également concevoir une applet de commande pour accéder directement à la fonctionnalité de sortie d’une application hôte via le service d’exécution PowerShell. À l’aide de l’hôte API fournies par PowerShell au lieu de [System.Console](/dotnet/api/System.Console) ou [System.Windows.Forms](/dotnet/api/System.Windows.Forms) garantit que votre applet de commande fonctionne avec un large éventail d’hôtes. Par exemple : le **powershell.exe** hôte de la console, le **powershell_ise.exe** hôte graphique, l’hôte de communication à distance PowerShell et des hôtes de fournisseurs tiers.

## <a name="see-also"></a>Voir aussi

[Concepts de création de rapports d’erreur](./error-reporting-concepts.md)

[Vue d’ensemble de l’applet de commande](./cmdlet-overview.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)