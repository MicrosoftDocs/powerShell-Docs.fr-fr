---
title: Enregistrements d’erreurs Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369108"
---
# <a name="windows-powershell-error-records"></a>Enregistrements d’erreurs Windows PowerShell

Les applets de commande doivent passer un objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) qui identifie la condition d’erreur pour les erreurs de fin et sans fin d’achèvement.

L’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) contient les informations suivantes :

- Exception qui décrit l’erreur. Il s’agit souvent d’une exception que l’applet de commande a interceptée et convertie en enregistrement d’erreur. Chaque enregistrement d’erreur doit contenir une exception.

Si l’applet de commande n’a pas intercepté d’exception, elle doit créer une nouvelle exception et choisir la classe d’exception qui décrit le mieux la condition d’erreur. Toutefois, vous n’avez pas besoin de lever l’exception, car elle est accessible par le biais de la propriété [System. Management. Automation. ErrorRecord. exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) de l’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

- Identificateur d’erreur qui fournit un indicateur ciblé qui peut être utilisé à des fins de diagnostic et par les scripts Windows PowerShell pour gérer des conditions d’erreur spécifiques avec des gestionnaires d’erreurs spécifiques. Chaque enregistrement d’erreur doit contenir un identificateur d’erreur (voir identificateur d’erreur).

- Catégorie d’erreur qui fournit un indicateur général qui peut être utilisé à des fins de diagnostic. Chaque enregistrement d’erreur doit spécifier une catégorie d’erreur (voir la catégorie d’erreur).

- Un message d’erreur de remplacement facultatif et une action recommandée (voir le message d’erreur de remplacement).

- Informations d’appel facultatives sur l’applet de commande qui a levé l’erreur. Ces informations sont spécifiées par Windows PowerShell (voir message d’appel).

- Objet cible qui était en cours de traitement lorsque l’erreur s’est produite. Il peut s’agir de l’objet d’entrée ou d’un autre objet que votre applet de commande traitait. Par exemple, pour la commande `remove-item -recurse c:\somedirectory`, l’erreur peut être une instance d’un objet FileInfo pour « c:\somedirectory\lockedfile ». Les informations de l’objet cible sont facultatives.

## <a name="error-identifier"></a>Identificateur d’erreur

Lorsque vous créez un enregistrement d’erreur, spécifiez un identificateur qui désigne la condition d’erreur dans votre applet de commande. Windows PowerShell combine l’identificateur ciblé et le nom de votre applet de commande pour créer un identificateur d’erreur complet. L’identificateur d’erreur complet est accessible via la propriété [System. Management. Automation. ErrorRecord. FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) de l’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . L’identificateur d’erreur n’est pas disponible par lui-même. Elle est disponible uniquement dans le cadre de l’identificateur d’erreur complet.

Utilisez les instructions suivantes pour générer des identificateurs d’erreur lorsque vous créez des enregistrements d’erreurs :

- Définissez des identificateurs d’erreur spécifiques à une condition d’erreur. Ciblez les identificateurs d’erreur à des fins de diagnostic et pour les scripts qui gèrent des conditions d’erreur spécifiques avec des gestionnaires d’erreurs spécifiques. Un utilisateur doit être en mesure d’utiliser l’identificateur d’erreur pour identifier l’erreur et sa source. Les identificateurs d’erreur activent également la création de rapports pour des conditions d’erreur spécifiques à partir d’exceptions existantes afin que les nouvelles sous-classes d’exception ne soient pas requises.

- En général, assignez des identificateurs d’erreur différents à des chemins de code différents. L’utilisateur final bénéficie d’identificateurs spécifiques. Souvent, chaque chemin de code qui appelle [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) de commande. ThrowTerminatingError * a son propre identificateur. En règle générale, définissez un nouvel identificateur lorsque vous définissez une nouvelle chaîne de modèle pour le message d’erreur, et vice-versa. N’utilisez pas le message d’erreur comme identificateur.

- Lorsque vous publiez du code à l’aide d’un identificateur d’erreur particulier, vous établissez la sémantique des erreurs avec cet identificateur pour votre cycle de vie de support produit complet. Ne la réutilisez pas dans un contexte qui est sémantiquement différent du contexte d’origine. Si la sémantique de cette erreur change, créez et utilisez un nouvel identificateur.

- En général, vous devez utiliser un identificateur d’erreur particulier uniquement pour les exceptions d’un type CLR particulier. Si le type de l’exception ou le type de l’objet cible change, créez et utilisez un nouvel identificateur.

- Choisissez le texte de votre identificateur d’erreur qui correspond de façon concise à l’erreur que vous signalez. Utilisez des conventions de mise en majuscules et de noms de .NET Framework standard. N’utilisez pas d’espace blanc ou de ponctuation. Ne Localisez pas les identificateurs d’erreur.

- Ne générez pas dynamiquement des identificateurs d’erreur d’une manière non reproductible. Par exemple, n’incorporez pas d’informations d’erreur comme un ID de processus. Les identificateurs d’erreur sont utiles uniquement s’ils correspondent aux identificateurs d’erreur détectés par d’autres utilisateurs qui rencontrent la même condition d’erreur.

## <a name="error-category"></a>Catégorie d’erreur

Lorsque vous créez un enregistrement d’erreur, spécifiez la catégorie de l’erreur à l’aide de l’une des constantes définies par l’énumération [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) . Windows PowerShell utilise la catégorie d’erreur pour afficher les informations d’erreur lorsque les utilisateurs définissent la variable `$ErrorView` sur `"CategoryView"`.

Évitez d’utiliser la constante **NotSpecified** [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) . Si vous avez des informations sur l’erreur ou sur l’opération à l’origine de l’erreur, choisissez la catégorie qui décrit le mieux l’erreur ou l’opération, même si la catégorie n’est pas parfaite.

Les informations affichées par Windows PowerShell sont appelées « chaîne de vue de catégorie » et sont générées à partir des propriétés de la classe [System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) . (Cette classe est accessible via la propriété Error [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) .)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

La liste suivante décrit les informations affichées :

- Category : une constante [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) définie par Windows PowerShell.

- TargetName : par défaut, nom de l’objet que l’applet de commande traitait lorsque l’erreur s’est produite. Ou une autre chaîne définie par l’applet de commande.

- TargetType : par défaut, le type de l’objet cible. Ou une autre chaîne définie par l’applet de commande.

- Activity : par défaut, il s’agit du nom de l’applet de commande qui a créé l’enregistrement d’erreur. Ou une autre chaîne définie par l’applet de commande.

- Raison : par défaut, le type d’exception. Ou une autre chaîne définie par l’applet de commande.

## <a name="replacement-error-message"></a>Message d’erreur de remplacement

Lorsque vous développez un enregistrement d’erreur pour une applet de commande, le message d’erreur par défaut de l’erreur provient du texte du message par défaut de la propriété [System. exception. message](/dotnet/api/System.Exception.Message) . Il s’agit d’une propriété en lecture seule dont le texte du message est destiné uniquement à des fins de débogage (conformément aux instructions .NET Framework). Nous vous recommandons de créer un message d’erreur qui remplace ou augmente le texte du message par défaut. Rendez le message plus convivial et plus spécifique à l’applet de commande.

Le message de remplacement est fourni par un objet [System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) . Utilisez l’un des constructeurs suivants de cet objet, car ils fournissent des informations de localisation supplémentaires qui peuvent être utilisées par Windows PowerShell.

- [ErrorDetails (cmdlet, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): utilisez ce constructeur si votre chaîne de modèle est une chaîne de ressource dans le même assembly que celui dans lequel l’applet de commande est implémentée ou si vous souhaitez charger la chaîne de modèle par le biais d’une substitution de l' [applet de commande Méthode System. Management. Automation. applet de commande. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) .

- [ErrorDetails (assembly, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): utilisez ce constructeur si la chaîne de modèle se trouve dans un autre assembly et que vous ne la chargez pas par le biais d’une substitution de [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)de commande. GetResourceString.

Le message de remplacement doit respecter les règles de conception de .NET Framework pour l’écriture de messages d’exception avec une petite différence. Les indications stipulent que les messages d’exception doivent être écrits pour les développeurs. Ces messages de remplacement doivent être écrits pour l’utilisateur de l’applet de commande.

Le message d’erreur de remplacement doit être ajouté avant l’appel des méthodes [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de commande. WriteError ou [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Pour ajouter un message de remplacement, définissez la propriété [System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) de l’enregistrement d’erreur. Quand cette propriété est définie, Windows PowerShell affiche la propriété [System. Management. Automation. ErrorDetails. message *](/dotnet/api/System.Management.Automation.ErrorDetails.Message) au lieu du texte du message par défaut.

## <a name="recommended-action-information"></a>Informations sur l’action recommandée

L’objet [System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) peut également fournir des informations sur les actions qui sont recommandées lorsque l’erreur se produit.

## <a name="invocation-information"></a>Informations d’appel

Quand une applet de commande utilise [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) pour signaler un enregistrement d’erreur, Windows PowerShell ajoute automatiquement les informations qui décrivent commande qui a été appelée lorsque l’erreur s’est produite. Ces informations sont fournies par un objet [System. Management. Automation. InvocationInfo](/dotnet/api/System.Management.Automation.InvocationInfo) qui contient le nom de l’applet de commande qui a été appelée par la commande, la commande elle-même et les informations sur le pipeline ou le script. Cette propriété est en lecture seule.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System. Management. Automation. InvocationInfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
