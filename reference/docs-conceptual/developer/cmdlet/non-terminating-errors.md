---
title: Erreurs sans fin d’arrêt | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d74c248e6ef54151400b8060d76524e89d87352c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786558"
---
# <a name="non-terminating-errors"></a>Erreur sans fin d’exécution

Cette rubrique décrit la méthode utilisée pour signaler des erreurs sans fin d’achèvement. Elle explique également comment appeler la méthode à partir de l’applet de commande.

Lorsqu’une erreur sans fin d’exécution se produit, l’applet de commande doit signaler cette erreur en appelant la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) . Lorsque l’applet de commande signale une erreur sans fin d’exécution, l’applet de commande peut continuer à fonctionner sur cet objet d’entrée et sur d’autres objets de pipeline entrants. Si l’applet de commande appelle la méthode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , l’applet de commande peut écrire un enregistrement d’erreur qui décrit la condition qui a provoqué l’erreur sans fin d’achèvement. Pour plus d’informations sur les enregistrements d’erreurs, consultez la page [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).

Les applets de commande peuvent appeler [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) si nécessaire à partir de leurs méthodes de traitement d’entrée. Toutefois, les applets de commande peuvent appeler [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) uniquement à partir du thread qui a appelé la méthode de traitement d’entrée System. Management. Automation. cmdlet. [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), System. [Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)ou [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . N’appelez pas [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) à partir d’un autre thread. À la place, communiquez les erreurs au thread principal.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
