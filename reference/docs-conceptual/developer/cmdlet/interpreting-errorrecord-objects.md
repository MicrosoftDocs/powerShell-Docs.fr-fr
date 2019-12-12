---
title: Interprétation des objets ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365418"
---
# <a name="interpreting-errorrecord-objects"></a>Interprétation des objets ErrorRecord

Dans la plupart des cas, un objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) représente une erreur sans fin d’exécution générée par une commande ou un script. Les erreurs de fin peuvent également spécifier des informations supplémentaires dans un ErrorRecord via l’interface [System. Management. Automation. Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) .

Si vous souhaitez écrire un gestionnaire d’erreurs dans votre script ou un hôte pour gérer des erreurs spécifiques qui se produisent pendant l’exécution de la commande ou du script, vous devez interpréter l’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) pour déterminer s’il représente la classe d’erreur que vous souhaitez gérer.

Lorsqu’une applet de commande rencontre une erreur de fin ou sans fin d’achèvement, elle doit créer un enregistrement d’erreur qui décrit la condition d’erreur. L’application hôte doit examiner ces enregistrements d’erreur et exécuter toute action qui atténue l’erreur. L’application hôte doit également examiner les enregistrements d’erreur pour les erreurs sans fin d’exécution qui n’ont pas réussi à traiter un enregistrement mais qui ont pu continuer, et il doit examiner les enregistrements d’erreur pour les erreurs de fin qui ont provoqué l’arrêt du pipeline.

> [!NOTE]
> Pour les erreurs de fin, l’applet de commande appelle la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) de commande. ThrowTerminatingError *. Pour les erreurs sans fin d’achèvement, l’applet de commande appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) .

## <a name="error-record-design"></a>Conception des enregistrements d’erreurs

Les enregistrements d’erreurs sont conçus pour fournir des informations supplémentaires sur l’erreur qui ne sont pas disponibles dans les exceptions, tout en veillant à ce que les informations combinées dans chaque enregistrement d’erreur soient uniques. Cet unicité permet à l’application hôte d’inspecter les différentes parties de l’enregistrement d’erreur afin de pouvoir identifier la condition d’erreur et l’action que l’hôte doit entreprendre.

## <a name="interpreting-error-records"></a>Interprétation des enregistrements d’erreurs

Vous pouvez examiner plusieurs parties de l’enregistrement d’erreur pour identifier l’erreur. Ces éléments sont les suivants :

- Catégorie d’erreur

- Exception d’erreur

- Identificateur d’erreur qualifié complet (FQID)

- Autres informations

### <a name="the-error-category"></a>Catégorie d’erreur

La catégorie d’erreur de l’enregistrement d’erreur est l’une des constantes prédéfinies fournies par l’énumération [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Ces informations sont disponibles par le biais de la propriété [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) de l’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

L’applet de commande peut spécifier les catégories CloseError, OpenError, InvalidType, ReadError et WriteError, ainsi que d’autres catégories d’erreur. L’application hôte peut utiliser la catégorie d’erreur pour capturer des groupes d’erreurs.

### <a name="the-exception"></a>L’exception

L’exception incluse dans l’enregistrement d’erreur est fournie par l’applet de commande et est accessible via la propriété [System. Management. Automation. ErrorRecord. exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) de l’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Les applications hôtes peuvent utiliser le mot clé `is` pour identifier que l’exception est d’une classe spécifique ou d’une classe dérivée. Il est préférable de créer une branche sur le type d’exception, comme illustré dans l’exemple suivant.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

De cette façon, vous interceptez les classes dérivées. Toutefois, il existe des problèmes si l’exception est désérialisée.

### <a name="the-fqid"></a>FQID

FQID est l’information la plus spécifique que vous pouvez utiliser pour identifier l’erreur. Il s’agit d’une chaîne qui contient un identificateur défini par une applet de commande, le nom de la classe d’applet de commande et la source qui a signalé l’erreur. En général, un enregistrement d’erreur est analogue à un enregistrement d’événement d’un journal des événements Windows. Le FQID est analogue au tuple suivant, qui identifie la classe de l’enregistrement d’événement : (*nom du journal*, *source*, ID de l' *événement*).

Le FQID est conçu pour être inspecté comme une chaîne unique. Toutefois, il existe des cas dans lesquels l’identificateur d’erreur est conçu pour être analysé par l’application hôte. L’exemple suivant est un identificateur d’erreur qualifié complet bien formé.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Dans l’exemple précédent, le premier jeton est l’identificateur d’erreur, qui est suivi du nom de la classe d’applet de commande. L’identificateur d’erreur peut être un jeton unique, ou il peut s’agir d’un identificateur séparé par des points qui permet la création de branches pour l’inspection de l’identificateur. N’utilisez pas d’espaces ni de signes de ponctuation dans l’identificateur d’erreur. Il est particulièrement important de ne pas utiliser de virgule. une virgule est utilisée par Windows PowerShell pour séparer l’identificateur et le nom de la classe de l’applet de commande.

### <a name="other-information"></a>Autres informations

L’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) peut également fournir des informations qui décrivent l’environnement dans lequel l’erreur s’est produite. Ces informations incluent des éléments tels que les détails de l’erreur, les informations d’appel et l’objet cible qui était en cours de traitement lorsque l’erreur s’est produite. Bien que ces informations puissent être utiles à l’application hôte, elles ne sont généralement pas utilisées pour identifier l’erreur. Ces informations sont disponibles par le biais des propriétés suivantes :

[System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System. Management. Automation. ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System. Management. Automation. ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Ajout d’un rapport d’erreurs sans fin d’achèvement à votre applet de commande](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
