---
title: Conseils pour le développement d’avis | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370038"
---
# <a name="advisory-development-guidelines"></a>Instructions dont le suivi est conseillé pour le développement

Cette section décrit les instructions que vous devez prendre en compte pour garantir une bonne expérience en matière de développement et d’expérience utilisateur. Parfois, ils peuvent s’appliquer et parfois non.

## <a name="design-guidelines"></a>Instructions de conception

Les instructions suivantes doivent être prises en compte lors de la conception des applets de commande. Lorsque vous trouvez une instruction de conception qui s’applique à votre situation, veillez à consulter les instructions de code pour obtenir des instructions similaires.

### <a name="support-an-inputobject-parameter-ad01"></a>Prendre en charge un paramètre InputObject (AD01)

Étant donné que Windows PowerShell fonctionne directement avec les objets Microsoft .NET Framework, un objet .NET Framework est souvent disponible et correspond exactement au type dont l’utilisateur a besoin pour effectuer une opération particulière. `InputObject` est le nom standard d’un paramètre qui prend ce type d’objet comme entrée. Par exemple, l’applet de commande **Stop-proc** du [didacticiel StopProc](./stopproc-tutorial.md) définit un paramètre `InputObject` de type process qui prend en charge l’entrée du pipeline. L’utilisateur peut obtenir un ensemble d’objets de processus, les manipuler pour sélectionner les objets exacts à arrêter, puis les transmettre directement à l’applet de commande **Stop-proc** .

### <a name="support-the-force-parameter-ad02"></a>Prendre en charge le paramètre Force (AD02)

Parfois, une applet de commande doit protéger l’utilisateur pour effectuer une opération demandée. Une telle applet de commande doit prendre en charge un paramètre `Force` pour permettre à l’utilisateur de remplacer cette protection si l’utilisateur dispose des autorisations nécessaires pour effectuer l’opération.

Par exemple, l’applet de [commande Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) ne supprime normalement pas un fichier en lecture seule. Toutefois, cette applet de commande prend en charge un paramètre `Force` pour permettre à un utilisateur de forcer la suppression d’un fichier en lecture seule. Si l’utilisateur a déjà l’autorisation de modifier l’attribut de lecture seule et que l’utilisateur supprime le fichier, l’utilisation du paramètre `Force` simplifie l’opération. Toutefois, si l’utilisateur n’est pas autorisé à supprimer le fichier, le paramètre `Force` n’a aucun effet.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Gérer les informations d’identification par le biais de Windows PowerShell (AD03)

Une applet de commande doit définir un paramètre `Credential` pour représenter les informations d’identification. Ce paramètre doit être de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) et doit être défini à l’aide d’une déclaration d’attribut Credential. Cette prise en charge invite automatiquement l’utilisateur à entrer le nom d’utilisateur, le mot de passe ou les deux lorsqu’une information d’identification complète n’est pas fournie directement. Pour plus d’informations sur l’attribut Credential, consultez [déclaration d’attribut des informations d’identification](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Paramètres de codage de prise en charge (AD04)

Si votre applet de commande lit ou écrit du texte dans ou à partir d’une forme binaire, telle que l’écriture ou la lecture d’un fichier dans un système de fichiers, votre applet de commande doit avoir un paramètre d’encodage qui spécifie la façon dont le texte est encodé au format binaire.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Les applets de commande de test doivent retourner une valeur booléenne (AD05)

Les applets de commande qui effectuent des tests sur leurs ressources doivent retourner un type [System. Boolean](/dotnet/api/System.Boolean) au pipeline afin qu’elles puissent être utilisées dans les expressions conditionnelles.

## <a name="code-guidelines"></a>Instructions de code

Les recommandations suivantes doivent être prises en compte lors de l’écriture du code de l’applet de commande. Lorsque vous trouvez une indication qui s’applique à votre situation, veillez à consulter les instructions de conception pour obtenir des instructions similaires.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Suivre les conventions d’affectation des noms des classes d’applets de commande (AC01)

En suivant les conventions de nommage standard, vous rendez vos applets de commande plus détectables et vous aidez l’utilisateur à comprendre exactement ce que font les applets de commande. Cette pratique est particulièrement importante pour les autres développeurs qui utilisent Windows PowerShell, car les applets de commande sont des types publics.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Définir une applet de commande dans l’espace de noms approprié

Normalement, vous définissez la classe pour une applet de commande dans un espace de noms .NET Framework qui ajoute «. Commands» à l’espace de noms qui représente le produit dans lequel l’applet de commande s’exécute. Par exemple, les applets de commande incluses dans Windows PowerShell sont définies dans l’espace de noms `Microsoft.PowerShell.Commands`.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nommer la classe d’applet de commande pour qu’elle corresponde au nom de l’applet de commande

Lorsque vous nommez la classe .NET Framework qui implémente une applet de commande, nommez la classe « *\<verbe > **\<substantif >** \<commande*> », où vous remplacez le\<*verbe* > et *\<* nom > les espaces réservés par le verbe et le nom utilisés pour le nom de l’applet de commande. Par exemple, l’applet de commande « [obtenir-process »](/powershell/module/Microsoft.PowerShell.Management/Get-Process) est implémentée par une classe appelée `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Si aucune entrée de pipeline ne remplace la méthode BeginProcessing (AC02)

Si votre applet de commande n’accepte pas d’entrée du pipeline, le traitement doit être implémenté dans la méthode [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) . L’utilisation de cette méthode permet à Windows PowerShell de gérer le classement entre les applets de commande. La première applet de commande du pipeline retourne toujours ses objets avant que les applets de commande restantes dans le pipeline n’aient la possibilité de démarrer leur traitement.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Pour gérer les demandes d’arrêt, remplacez la méthode StopProcessing (AC03)

Remplacez la méthode [System. Management. Automation. applet de commande. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) afin que votre applet de commande puisse gérer le signal d’arrêt. Certaines applets de commande mettent beaucoup de temps à s’exécuter, et elles permettent de passer beaucoup de temps entre les appels au service d’exécution Windows PowerShell, par exemple quand l’applet de commande bloque le thread dans les appels RPC de longue durée. Cela comprend les applets de commande qui effectuent des appels à la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) , à la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) et à d’autres mécanismes de commentaires qui peuvent prendre beaucoup de temps. Dans ce cas, l’utilisateur peut avoir besoin d’envoyer un signal d’arrêt à ces applets de commande.

### <a name="implement-the-idisposable-interface-ac04"></a>Implémenter l’interface IDisposable (AC04)

Si votre applet de commande a des objets qui ne sont pas supprimés (écrits dans le pipeline) par la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , votre applet de commande peut nécessiter une suppression d’objet supplémentaire. Par exemple, si votre applet de commande ouvre un descripteur de fichier dans sa méthode [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) et que le handle est ouvert pour une utilisation par la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , ce descripteur doit être fermé à la fin du traitement.

Le runtime Windows PowerShell n’appelle pas toujours la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing. Par exemple, la méthode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) peut ne pas être appelée si l’applet de commande est annulée au milieu de l’opération ou si une erreur d’arrêt se produit dans une partie de l’applet de commande. Par conséquent, la classe .NET Framework pour une applet de commande qui requiert le nettoyage d’objets doit implémenter le modèle d’interface [System. IDisposable](/dotnet/api/System.IDisposable) complet, y compris le finaliseur, afin que le runtime Windows PowerShell puisse appeler à la fois les méthodes [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) et [System. IDisposable. dispose *](/dotnet/api/System.IDisposable.Dispose) à la fin du traitement.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Utiliser des types de paramètres compatibles avec la sérialisation (AC05)

Pour prendre en charge l’exécution de votre applet de commande sur des ordinateurs distants, utilisez des types qui peuvent être facilement sérialisés sur l’ordinateur client, puis réalimentés sur l’ordinateur serveur. Les types suivants sont compatibles avec la sérialisation.

Types primitifs :

- Byte, SByte, Decimal, Single, double, Int16, Int32, Int64, Uint16, UInt32 et UInt64.

- Boolean, Guid, Byte [], TimeSpan, DateTime, Uri et version.

- Char, String, XmlDocument.

Types rehydratable intégrés :

- PSPrimitiveDictionary

- Paramètre_booléen

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Autres types :

- SecureString

- Conteneurs (listes et dictionnaires du type ci-dessus)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Utiliser SecureString pour les données sensibles (AC06)

Lorsque vous gérez des données sensibles, utilisez toujours le type de données [System. Security. SecureString](/dotnet/api/System.Security.SecureString) . Cela peut inclure l’entrée de pipeline aux paramètres, ainsi que le renvoi de données sensibles au pipeline.

## <a name="see-also"></a>Voir aussi

[Instructions de développement requises](./required-development-guidelines.md)

[Instructions de développement vivement encouragées](./strongly-encouraged-development-guidelines.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
