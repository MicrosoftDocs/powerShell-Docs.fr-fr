---
title: Directives de développement Advisory | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854857"
---
# <a name="advisory-development-guidelines"></a>Instructions dont le suivi est conseillé pour le développement

Cette section décrit les instructions qui vous aideront à assurer une bonne expérience des utilisateurs et de développement. Parfois, ils peuvent s’appliquer, et parfois ils ne le peuvent pas.

## <a name="design-guidelines"></a>Règles de conception

Les instructions suivantes doivent être considérées lors de la conception des applets de commande. Lorsque vous trouvez une indication de conception qui s’appliquent à votre situation, veillez à consulter les instructions de Code pour obtenir des instructions similaires.

### <a name="support-an-inputobject-parameter-ad01"></a>Prend en charge un paramètre InputObject (AD01)

Étant donné que Windows PowerShell fonctionne directement avec les objets Microsoft .NET Framework, un objet .NET Framework est souvent disponible que correspond exactement le type de l’utilisateur doit effectuer une opération particulière. `InputObject` est le nom standard pour un paramètre qui accepte un tel objet en tant qu’entrée. Par exemple, l’exemple **Stop-Process** applet de commande dans le [StopProc didacticiel](./stopproc-tutorial.md) définit un `InputObject` paramètre de type de processus qui prend en charge de l’entrée du pipeline. L’utilisateur peut obtenir un ensemble d’objets de processus, les manipuler pour sélectionner les objets spécifiques à arrêter, puis les passer à la **Stop-Process** applet de commande directement.

### <a name="support-the-force-parameter-ad02"></a>Prise en charge le paramètre Force (AD02)

Parfois, une applet de commande doit protéger l’utilisateur d’effectuer une opération demandée. Ce type une applet de commande doit prendre en charge un `Force` paramètre pour autoriser l’utilisateur de substituer cette protection si l’utilisateur dispose des autorisations nécessaires pour effectuer l’opération.

Par exemple, le [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) applet de commande ne supprime pas normalement un fichier en lecture seule. Toutefois, cette applet de commande prend en charge un `Force` paramètre pour un utilisateur peut forcer la suppression d’un fichier en lecture seule. Si l’utilisateur a déjà autorisé à modifier l’attribut en lecture seule, et l’utilisateur supprime le fichier, utilisez le `Force` paramètre simplifie l’opération. Toutefois, si l’utilisateur n’est pas autorisé à supprimer le fichier, le `Force` paramètre n’a aucun effet.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Gérer les informations d’identification via Windows PowerShell (AD03)

Une applet de commande doit définir un `Credential` paramètre pour représenter les informations d’identification. Ce paramètre doit être de type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) et doit être défini à l’aide d’une déclaration d’attribut d’informations d’identification. Cette prise en charge invite automatiquement l’utilisateur pour le nom d’utilisateur, le mot de passe ou les deux lorsqu’une information d’identification complète n’est pas fournie directement. Pour plus d’informations sur l’attribut d’informations d’identification, consultez [déclaration d’attribut d’informations d’identification](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Prend en charge les paramètres d’encodage (AD04)

Si votre applet de commande lit ou écrit du texte vers ou à partir d’une forme binaire, telles que l’écriture ou de lecture à partir d’un fichier dans un système de fichiers, puis votre applet de commande doit avoir le paramètre Encoding qui spécifie la façon dont le texte est encodé sous la forme binaire.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Applets de commande de test doit retourner une valeur booléenne (AD05)

Applets de commande qui effectuent des tests par rapport à leurs ressources doit retourner un [System.Boolean](/dotnet/api/System.Boolean) tapez au pipeline afin qu’ils peuvent être utilisés dans des expressions conditionnelles.

## <a name="code-guidelines"></a>Instructions de code

Les instructions suivantes doivent être considérées lors de l’écriture de code de l’applet de commande. Lorsque vous trouvez une indication qui s’appliquent à votre situation, veillez à examiner les règles de conception pour obtenir des instructions similaires.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Suivez les Conventions de nom de la classe de l’applet de commande (AC01)

En suivant les conventions d’affectation de noms standard, vous rendez vos applets de commande plus détectable, et vous aider à l’utilisateur de comprendre exactement ce que font les applets de commande. Cette pratique est particulièrement importante pour les autres développeurs à l’aide de Windows PowerShell, car les applets de commande sont des types publics.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Définir une applet de commande dans le Namespace Correct

Vous définissez normalement la classe pour une applet de commande dans un espace de noms .NET Framework qui ajoute ». Commandes » pour l’espace de noms qui représente le produit dans lequel s’exécute l’applet de commande. Par exemple, les applets de commande qui sont inclus avec Windows PowerShell sont définies dans le `Microsoft.PowerShell.Commands` espace de noms.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nommez la classe d’applet de commande doit correspondre au nom de l’applet de commande

Lorsque vous nommez la classe .NET Framework qui implémente une applet de commande, nommez la classe «*\<verbe >**\<Noun >**\<commande >*», où vous remplacez le  *\<Verbe >* et  *\<Noun >* des espaces réservés avec le verbe et substantif, utilisé pour le nom de l’applet de commande. Par exemple, le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande est implémentée par une classe appelée `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Si aucune entrée de Pipeline ne substituer la méthode BeginProcessing (AC02)

Si votre applet de commande n’accepte pas d’entrée provenant du pipeline, le traitement doit être implémenté dans le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode). Utilisation de cette méthode permet de conserver l’ordre entre les applets de commande Windows PowerShell. La première applet de commande dans le pipeline retourne toujours ses objets avant les autres applets de commande dans le pipeline chance de démarrer leur traitement.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Pour gérer les demandes d’arrêt substituent la méthode StopProcessing (AC03)

Remplacer le [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) méthode afin que votre applet de commande peut gérer le signal d’arrêt. Certaines applets de commande prennent beaucoup de temps pour terminer leur opération, et ils permettent de beaucoup de temps passer entre les appels à l’exécution de Windows PowerShell, telles que lorsque l’applet de commande bloque le thread dans les appels RPC longue. Cela inclut les applets de commande qui effectuent des appels à la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode), à la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode) et à d’autres commentaires mécanismes qui peuvent prendre beaucoup de temps. Dans ce cas l’utilisateur devra peut-être envoyer un signal d’arrêt à ces applets de commande.

### <a name="implement-the-idisposable-interface-ac04"></a>Implémenter l’Interface IDisposable (AC04)

Si votre applet de commande possède des objets qui ne sont pas supprimés de (écrit dans le pipeline) par le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode), votre applet de commande peut nécessiter la suppression d’objets supplémentaires. Par exemple, si votre applet de commande ouvre un handle de fichier dans son [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode) et conserve le handle ouvrir pour une utilisation par le [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode), ce handle doit être fermé à la fin du traitement.

Le runtime Windows PowerShell n’appelle pas toujours le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode). Par exemple, le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode ne peut pas être appelée si l’applet de commande est annulée à mi-chemin via son fonctionnement, ou si un arrêt de l’erreur se produit dans n’importe quelle partie de l’applet de commande. Par conséquent, la classe .NET Framework pour une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle d’interface, y compris le finaliseur, afin que le runtime Windows PowerShell peut appeler à la fois le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) et [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) méthodes à la fin du traitement.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Utiliser des Types de paramètres de sérialisation conviviale (AC05)

Pour prendre en charge votre applet de commande en cours d’exécution sur des ordinateurs distants, utilisez les types qui peuvent être facilement sérialisées sur l’ordinateur client et puis réalimentées sur l’ordinateur serveur. Les types de suivi sont adapté à la sérialisation.

Types primitifs :

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 et UInt64.

- Valeur booléenne, Guid, Byte [], intervalle de temps, DateTime, Uri et Version.

- Char, String, XmlDocument.

Types rehydratable intégrés :

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Autres types :

- SecureString

- Conteneurs (listes et les dictionnaires de type ci-dessus)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Utilisez SecureString pour les données sensibles (AC06)

Lors de la gestion des données sensibles de toujours utiliser le [System.Security.Securestring](/dotnet/api/System.Security.SecureString) type de données. Cela peut inclure les entrées de pipeline pour les paramètres, ainsi que le renvoi de données sensibles dans le pipeline.

## <a name="see-also"></a>Voir aussi

[Directives de développement requis](./required-development-guidelines.md)

[Directives de développement vous êtes vivement invité](./strongly-encouraged-development-guidelines.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
