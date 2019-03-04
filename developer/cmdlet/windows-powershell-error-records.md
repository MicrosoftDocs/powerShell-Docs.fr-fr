---
title: Erreur de Windows PowerShell enregistre | Microsoft Docs
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
ms.openlocfilehash: bbe04a8fb556f0f6807bc0eae6634e3cf505759e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861975"
---
# <a name="windows-powershell-error-records"></a>Enregistrements d’erreurs Windows PowerShell

Applets de commande doit passer un [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet qui identifie la condition d’erreur pour les erreurs avec fin d’exécution et sans fin d’exécution.

Le [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet contient les informations suivantes :

- Exception qui décrit l’erreur. Souvent, il s’agit d’une exception qui l’applet de commande interceptées et converti en un enregistrement d’erreur. Chaque enregistrement d’erreur doit contenir une exception.

Si l’applet de commande ne pas intercepter une exception, il doit créer une exception et choisissez la classe d’exception qui décrit le mieux la condition d’erreur. Toutefois, vous n’avez pas besoin lever l’exception, car il est accessible via la [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriété de la [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet.

- Un identificateur de l’erreur qui fournit un indicateur ciblé utilisables pour faciliter le diagnostic et les scripts Windows PowerShell pour gérer les conditions d’erreur spécifiques avec les gestionnaires d’erreurs spécifiques. Chaque enregistrement d’erreur doit contenir un identificateur de l’erreur (voir l’identificateur de l’erreur).

- Une catégorie d’erreur qui fournit un indicateur général qui peut être utilisé pour faciliter le diagnostic. Chaque enregistrement d’erreur doit spécifier une catégorie d’erreur (voir la catégorie d’erreur).

- Un message d’erreur facultatif de remplacement et l’action recommandée (voir le Message d’erreur de remplacement).

- Informations d’appel facultatif sur l’applet de commande qui a généré l’erreur. Ces informations sont spécifiées par Windows PowerShell (voir le Message d’appel).

- L’objet cible qui était traitée lorsque l’erreur s’est produite. Cela peut être l’objet d’entrée, ou il peut être un autre objet votre applet de commande était en cours. Par exemple, pour la commande `remove-item -recurse c:\somedirectory`, l’erreur peut être une instance d’un objet FileInfo pour « c:\somedirectory\lockedfile ». Les informations d’objet cible sont facultatives.

## <a name="error-identifier"></a>Identificateur de l’erreur

Lorsque vous créez un enregistrement d’erreur, spécifiez un identificateur qui désigne la condition d’erreur dans votre applet de commande. Windows PowerShell associe l’identificateur ciblé par le nom de votre applet de commande pour créer un identificateur d’erreur complet. Identificateur de l’erreur qualifié complet est accessible via la [System.Management.Automation.Errorrecord.Fullyqualifiederrorid*](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) propriété de la [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)objet. Identificateur de l’erreur n’est pas disponible par lui-même. Il est disponible uniquement dans le cadre de l’identificateur d’erreur complet.

Utilisez les instructions suivantes pour générer des identificateurs d’erreur lorsque vous créez des enregistrements d’erreur :

- Rendre les identificateurs d’erreur spécifique à une condition d’erreur. Cibler les identificateurs d’erreur pour faciliter le diagnostic et pour les scripts qui gèrent les conditions d’erreur spécifiques avec les gestionnaires d’erreurs spécifiques. Un utilisateur doit être en mesure d’utiliser l’identificateur de l’erreur pour identifier l’erreur et sa source. Identificateurs d’erreur également activer la création de rapports pour les conditions d’erreur spécifiques à partir des exceptions existantes afin que les nouveaux sous-classes d’exception ne sont pas nécessaires.

- En règle générale, affecter des identificateurs d’erreur différents pour différents chemins de code. L’utilisateur final tire parti des identificateurs spécifiques. Souvent, chaque chemin de code qui appelle [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) a son propre identificateur. En règle générale, définissez un nouvel identificateur lorsque vous définissez une nouvelle chaîne de modèle pour le message d’erreur et vice versa. N’utilisez pas le message d’erreur en tant qu’identificateur.

- Lorsque vous publiez le code à l’aide d’un identificateur d’erreur particulier, vous établissez que la sémantique d’erreurs avec cet identificateur pour votre produit complète prend en charge le cycle de vie. Ne réutilisez pas dans un contexte qui est sémantiquement différente selon le contexte d’origine. Si la sémantique de cette erreur modifier, créer, puis utilisez un nouvel identificateur.

- Vous devez généralement utiliser un identificateur de l’erreur particulière uniquement pour les exceptions d’un type particulier de CLR. Si le type de l’exception ou le type de l’objet cible change, créer, puis utilisez un nouvel identificateur.

- Choisissez le texte pour votre identificateur d’erreur plus concise correspond à l’erreur que vous signalez. Utilisez les conventions de dénomination et la mise en majuscules standard de .NET Framework. N’utilisez pas les espaces blancs ou des signes de ponctuation. Ne localisez pas les identificateurs d’erreur.

- Ne générez pas les identificateurs d’erreur dynamiquement d’une manière non reproductibles. Par exemple, n’intègrent pas les informations d’erreur comme un ID de processus. Identificateurs d’erreur sont utiles uniquement si elles correspondent aux identificateurs erreur vues par d’autres utilisateurs qui rencontrent la même condition d’erreur.

## <a name="error-category"></a>Catégorie d’erreur

Lorsque vous créez un enregistrement d’erreur, spécifiez la catégorie de l’erreur en utilisant l’une des constantes définies par le [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) énumération. Windows PowerShell utilise la catégorie d’erreur pour afficher les informations d’erreur lorsque les utilisateurs définissent le `$ErrorView` à la variable `"CategoryView"`.

Évitez d’utiliser le [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) constante. Si vous avez toutes les informations sur l’erreur ou sur l’opération qui a provoqué l’erreur, choisissez la catégorie qui décrit le mieux l’erreur ou l’opération, même si la catégorie n’est pas une correspondance parfaite.

Les informations affichées par Windows PowerShell correspond à la chaîne d’affichage des catégories et est générées à partir des propriétés de la [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) classe. (Cette classe est accessible via l’erreur [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriété.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

La liste suivante décrit les informations affichées :

- Catégorie : Défini par le Windows PowerShell [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) constante.

- TargetName : Par défaut, le nom de l’objet de l’applet de commande traitait lorsque l’erreur s’est produite. Ou bien, une autre chaîne définie par l’applet de commande.

- TargetType: Par défaut, le type de l’objet cible. Ou bien, une autre chaîne définie par l’applet de commande.

- Activité : Par défaut, le nom de l’applet de commande qui a créé l’enregistrement d’erreur. Ou une autre chaîne définie par l’applet de commande.

- Raison : Par défaut, le type d’exception. Ou bien, une autre chaîne définie par l’applet de commande.

## <a name="replacement-error-message"></a>Message d’erreur de remplacement

Lorsque vous développez un enregistrement d’erreur pour une applet de commande, le message d’erreur par défaut pour l’erreur provient le texte du message par défaut dans le [System.Exception.Message](/dotnet/api/System.Exception.Message) propriété. Il s’agit d’une propriété en lecture seule dont texte du message est destiné uniquement à des fins (selon les indications du .NET Framework). Nous vous recommandons de créer un message d’erreur qui remplace ou complète le texte du message par défaut. Vérifiez le message plus conviviales et plus spécifiques à l’applet de commande.

Le message de remplacement est fourni par un [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) objet. Utilisez un des constructeurs suivants de cet objet, car ils fournissent des informations de localisation supplémentaire qui peuvent être utilisées par Windows PowerShell.

- [ErrorDetails.ErrorDetails (applet de commande, chaîne, chaîne, objet\[System.Management.Automation.Errordetails.%23Ctor%28System.Management.Automation.Cmdlet%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29 ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Utilisez ce constructeur si votre chaîne de modèle est une chaîne de ressource dans le même assembly dans lequel l’applet de commande est implémentée ou si vous souhaitez charger la chaîne de modèle via une substitution de la [System.Management.Automation.Cmdlet.Getresourcestring* ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) (méthode).

- [ErrorDetails.ErrorDetails (Assembly, chaîne, chaîne, objet\[System.Management.Automation.Errordetails.%23Ctor%28System.Reflection.Assembly%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29 ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Utilisez ce constructeur si la chaîne de modèle est dans un autre assembly et que vous ne le chargez pas via une substitution de [System.Management.Automation.Cmdlet.Getresourcestring*](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Le message de remplacement doit respecter les règles de conception de .NET Framework pour l’écriture de messages d’exception avec une petite différence. L’état de directives messages d’exception doivent être écrit pour les développeurs. Ces messages de remplacement doivent être écrit pour l’utilisateur de l’applet de commande.

Le message d’erreur de remplacement doit être ajouté avant le [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) méthodes sont appelées. . Pour ajouter un message de remplacement, définissez la [System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) propriété de l’enregistrement d’erreur. Lorsque cette propriété est définie, Windows PowerShell affiche le [System.Management.Automation.Errordetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) propriété au lieu du texte du message par défaut.

## <a name="recommended-action-information"></a>Informations sur l’Action de recommandé

Le [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) objet peut fournir également des informations sur les actions qui sont recommandées lorsque l’erreur se produit.

## <a name="invocation-information"></a>Informations d’appel

Quand une applet de commande utilise [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) pour signaler un enregistrement d’erreur, Windows PowerShell ajoute automatiquement des informations qui décrivent la commande qui a été appelée lors de l’erreur s’est produite. Ces informations sont fournies par un [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) objet qui contient le nom de l’applet de commande qui a été appelée par la commande, la commande elle-même et des informations sur le pipeline ou d’un script. Cette propriété est en lecture seule.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
