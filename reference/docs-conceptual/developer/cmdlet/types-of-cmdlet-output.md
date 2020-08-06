---
title: Types de sortie de l’applet de commande | Microsoft Docs
ms.date: 01/18/2019
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.openlocfilehash: 8f761fdddd264b7c580c4a860081fdc5d2776ee7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786354"
---
# <a name="types-of-cmdlet-output"></a>Types de sortie de l’applet de commande

PowerShell offre plusieurs méthodes qui peuvent être appelées par les applets de commande pour générer la sortie. Ces méthodes utilisent une opération spécifique pour écrire leur sortie dans un flux de données spécifique, tel que le flux de données de réussite ou le flux de données d’erreur. Cet article décrit les types de sortie et les méthodes utilisées pour les générer.

## <a name="types-of-output"></a>Types de sortie

### <a name="success-output"></a>Sortie de réussite

Les applets de commande peuvent signaler la réussite en retournant un objet qui peut être traité par la commande suivante dans le pipeline. Une fois que l’applet de commande a effectué son action, l’applet de commande appelle la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Nous vous recommandons d’appeler cette méthode à la place des méthodes [System. Console. WriteLine](/dotnet/api/System.Console.WriteLine) ou [System. Management. Automation. Host. PSHostUserInterface. WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) .

Vous pouvez fournir un paramètre de commutateur **PassThru** pour les applets de commande qui ne retournent généralement pas d’objets.
Lorsque le paramètre de commutateur **PassThru** est spécifié sur la ligne de commande, l’applet de commande est invitée à retourner un objet. Pour obtenir un exemple d’applet de commande qui a un paramètre **PassThru** , consultez [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Sortie d’erreur

Les applets de commande peuvent signaler des erreurs. Lorsqu’une erreur se termine, l’applet de commande lève une exception. Lorsqu’une erreur sans fin d’exécution se produit, l’applet de commande appelle la méthode [System. Management. Automation. Provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) pour envoyer un enregistrement d’erreur au flux de données d’erreur. Pour plus d’informations sur le rapport d’erreurs, consultez [concepts du rapport d’erreurs](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Sortie détaillée.

Les applets de commande peuvent vous fournir des informations utiles pendant que l’applet de commande traite correctement les enregistrements en appelant la méthode [System. Management. Automation. applet de commande. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) . La méthode génère des messages détaillés qui indiquent le mode de poursuite de l’action.

Par défaut, les messages détaillés ne sont pas affichés. Vous pouvez spécifier le paramètre **Verbose** lors de l’exécution de l’applet de commande pour afficher ces messages. **Verbose** est un paramètre commun qui est disponible pour toutes les applets de commande.

### <a name="progress-output"></a>Sortie de la progression

Les applets de commande peuvent vous fournir des informations de progression lorsque l’applet de commande exécute des tâches dont l’exécution prend beaucoup de temps, par exemple la copie d’un répertoire de manière récursive. Pour afficher les informations de progression, l’applet de commande appelle la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) de commande. WriteProgress.

### <a name="debug-output"></a>Sortie de débogage

Les applets de commande peuvent fournir des messages de débogage qui sont utiles lors du dépannage du code de l’applet de commande. Pour afficher les informations de débogage, l’applet de commande appelle la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) de commande. WriteDebug.

Par défaut, les messages de débogage ne sont pas affichés. Vous pouvez spécifier le paramètre de **débogage** lors de l’exécution de l’applet de commande pour afficher ces messages. **Debug** est un paramètre courant qui est disponible pour toutes les applets de commande.

### <a name="warning-output"></a>Sortie d’avertissement

Les applets de commande peuvent afficher des messages d’avertissement en appelant la méthode [System. Management. Automation. applet de commande. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

Par défaut, les messages d’avertissement s’affichent. Toutefois, vous pouvez configurer des messages d’avertissement à l’aide de la `$WarningPreference` variable ou à l’aide des paramètres **détaillés** et de **débogage** lorsque l’applet de commande est appelée.

## <a name="displaying-output"></a>Affichage de la sortie

Pour tous les appels de méthode d’écriture, l’affichage du contenu est déterminé par des variables d’exécution spécifiques. L’exception est la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . À l’aide de ces variables, vous pouvez effectuer l’appel d’écriture approprié à l’emplacement approprié dans votre code et vous ne devez pas vous préoccuper de la date ou de l’affichage de la sortie.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Accès aux fonctionnalités de sortie d’une application hôte

Vous pouvez également concevoir une applet de commande pour accéder directement aux fonctionnalités de sortie d’une application hôte par le biais du runtime PowerShell. L’utilisation des API d’hôte fournies par PowerShell au lieu de [System. console](/dotnet/api/System.Console) ou de [System. Windows. Forms](/dotnet/api/System.Windows.Forms) garantit que votre applet de commande fonctionne avec un large éventail d’hôtes. Par exemple : l’hôte de la console **powershell.exe** , l’hôte graphique **powershell_ise.exe** , l’hôte de communication à distance PowerShell et les hôtes tiers.

## <a name="see-also"></a>Voir aussi

[Concepts des rapports d’erreurs](./error-reporting-concepts.md)

[Vue d’ensemble des applets de commande](./cmdlet-overview.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
