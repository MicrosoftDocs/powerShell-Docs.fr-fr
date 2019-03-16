---
title: Interprétation des objets d’ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058774"
---
# <a name="interpreting-errorrecord-objects"></a>Interprétation des objets ErrorRecord

Dans la plupart des cas, un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet représente une erreur sans fin d’exécution générée par une commande ou un script. Arrêt des erreurs permettre également spécifier les informations supplémentaires dans ErrorRecord via le [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.

Si vous souhaitez écrire un gestionnaire d’erreurs dans votre script ou un ordinateur hôte pour gérer les erreurs spécifiques qui se produisent pendant l’exécution de commande ou un script, vous devez interpréter les [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet afin de déterminer si elle représente la classe d’erreur que vous souhaitez gérer.

Quand une applet de commande rencontre une fin ou erreur sans fin d’exécution, il doit créer un enregistrement d’erreur qui décrit la condition d’erreur. L’application hôte doit examiner ces enregistrements d’erreur et effectuer toute action atténuera l’erreur. L’application hôte doit également rechercher des enregistrements d’erreur pour les erreurs sans fin d’exécution qui n’a pas pu traiter un enregistrement mais qui ont été en mesure de continuer, et elle doit examiner les enregistrements d’erreur pour les erreurs avec fin d’exécution qui a provoqué le pipeline à arrêter.

> [!NOTE]
> Pour les erreurs avec fin d’exécution, l’applet de commande appelle le [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (méthode). Pour les erreurs sans fin d’exécution, l’applet de commande appelle le [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode).

## <a name="error-record-design"></a>Conception enregistrements d’erreur

Enregistrements d’erreur sont conçus pour fournir des informations d’erreur supplémentaires qui ne sont pas disponibles dans les exceptions tout en garantissant que les informations combinés dans chaque enregistrement d’erreur sont uniques. Ce caractère unique permet à l’application hôte inspecter les différentes parties de l’enregistrement d’erreur afin qu’il peut identifier la condition d’erreur et l’action de l’hôte doit prendre.

## <a name="interpreting-error-records"></a>Interprétation des enregistrements d’erreur

Vous pouvez examiner plusieurs parties de l’enregistrement d’erreur pour identifier l’erreur. Ces parties sont les suivantes :

- La catégorie d’erreur

- L’exception d’erreur

- L’identificateur d’erreur complet (FQID)

- Autres informations

### <a name="the-error-category"></a>La catégorie d’erreur

La catégorie d’erreur de l’enregistrement d’erreur est une des constantes prédéfinies fournies par le [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) énumération. Ces informations sont disponibles via le [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriété de la [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet.

L’applet de commande permettre spécifier les catégories CloseError OpenError, InvalidType, ReadError et WriteError et autres catégories d’erreur. L’application hôte peut utiliser la catégorie d’erreur pour capturer des groupes d’erreurs.

### <a name="the-exception"></a>L’Exception

L’exception incluse dans l’enregistrement d’erreur est fournie par l’applet de commande et est accessible via la [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriété de la [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet.

Les applications hôte peuvent utiliser le `is` mot clé pour identifier l’exception d’une classe spécifique ou d’une classe dérivée. Il est préférable de branche sur le type d’exception, comme indiqué dans l’exemple suivant.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

De cette façon, vous interceptez les classes dérivées. Toutefois, il existe des problèmes si l’exception est désérialisée.

### <a name="the-fqid"></a>Le FQID

Le FQID est les informations plus spécifiques, que vous pouvez utiliser pour identifier l’erreur. C’est une chaîne qui inclut un identificateur défini par l’applet de commande, le nom de la classe de l’applet de commande et la source qui a signalé l’erreur. En règle générale, un enregistrement d’erreur est analogue à un enregistrement d’événement d’un journal des événements de Windows. Le FQID est analogue au tuple suivant, qui identifie la classe de l’enregistrement d’événement : (*nom_journal*, *source*, *ID d’événement*).

Le FQID est conçu pour être inspecté sous forme de chaîne unique. Toutefois, le cas existent dans lequel l’identificateur de l’erreur est conçu pour être analysée par l’application hôte. L’exemple suivant est un identificateur d’erreur complet correct.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Dans l’exemple précédent, le premier jeton est l’identificateur de l’erreur, qui est suivie par le nom de la classe de l’applet de commande. Identificateur de l’erreur peut être un jeton unique, ou il peut être un identificateur séparés par des points qui permet le branchement sur l’inspection de l’identificateur. N’utilisez pas d’espace blanc ou des signes de ponctuation dans l’identificateur de l’erreur. Il est particulièrement important de ne pas utiliser une virgule ; une virgule est utilisée par Windows PowerShell pour séparer l’identificateur et le nom de la classe d’applet de commande.

### <a name="other-information"></a>Autres informations

Le [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet peut également fournir des informations qui décrivent l’environnement dans lequel l’erreur s’est produite. Ces informations incluent des éléments tels que les détails de l’erreur, informations d’appel et l’objet cible qui était traitée lorsque l’erreur s’est produite. Bien que ces informations peuvent être utiles à l’application hôte, il n’est pas généralement utilisé pour identifier l’erreur. Ces informations sont disponibles via les propriétés suivantes :

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Ajout de rapport d’erreurs à votre applet de commande sans terminaison](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
