---
title: Arrêt des erreurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: c593da1f7bdb6ddf09ba8d5de92af730687dbc8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859235"
---
# <a name="terminating-errors"></a>Erreur avec fin d’exécution

Cette rubrique décrit la méthode utilisée pour signaler les erreurs de fin d’exécution. Elle explique également comment appeler la méthode à partir de l’applet de commande, et il traite les exceptions qui peuvent être retournées par le runtime de Windows PowerShell lorsque la méthode est appelée.

Lorsqu’une fin erreur se produit, l’applet de commande doit signaler l’erreur en appelant le [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (méthode). Cette méthode permet à l’applet de commande Envoyer un enregistrement d’erreur qui décrit la condition ayant provoqué l’erreur avec fin d’exécution. Pour plus d’informations sur les enregistrements d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).

Lorsque le [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) est appelée, le runtime Windows PowerShell arrête l’exécution du pipeline définitivement et lève un [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception. Toute tentative ultérieure de l’appeler [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), ou plusieurs autres API provoque ces appels lève un [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception.

Le [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception peut également se produire si une autre applet de commande dans le pipeline signale une erreur avec fin d’exécution, si l’utilisateur a demandé d’arrêter le pipeline, ou si le pipeline a été arrêté. avant la fin pour une raison quelconque. L’applet de commande n’a pas besoin d’intercepter le [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception, sauf si elle doit ouvrir Nettoyage des ressources ou son état interne.

Applets de commande peut écrire n’importe quel nombre d’objets de sortie ou des erreurs sans fin d’exécution avant de signaler une erreur avec fin d’exécution. Toutefois, l’erreur avec fin d’exécution s’arrête définitivement le pipeline et aucune sortie supplémentaire, fin d’exécution, les erreurs ou les erreurs sans fin d’exécution peuvent être signalées.

Applets de commande peut appeler [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) uniquement à partir du thread qui a appelé le [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode de traitement d’entrée. N’essayez pas d’appeler [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ou [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) à partir d’un autre thread. Au lieu de cela, les erreurs doivent être communiquées au thread principal.

Il est possible pour une applet de commande pour lever une exception dans son implémentation de la [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode). Toute exception levée à partir de ces méthodes (à l’exception de certaines conditions d’erreur grave qui arrêter l’hôte Windows PowerShell) est interprétée comme une erreur avec fin d’exécution qui arrête le pipeline, mais pas Windows PowerShell dans sa globalité. (Cela s’applique uniquement au thread principal applet de commande. Les exceptions non interceptées dans les threads engendrés par l’applet de commande, en général, l’arrêter l’hôte Windows PowerShell.) Nous vous recommandons d’utiliser [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) au lieu de lever une exception, car l’enregistrement d’erreur fournit des informations supplémentaires sur la condition d’erreur, qui est utile pour l’utilisateur final. Applets de commande doivent respecter les instructions de code managé par rapport à la mise en cache et la gestion des exceptions de tous les (`catch (Exception e)`). Seules les exceptions de types connus et attendus convertissent des enregistrements d’erreur.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell erreur enregistrements](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
