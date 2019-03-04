---
title: Instructions de développement requises | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: a4b228be91bba27670b26fe21e765ae942afe968
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860715"
---
# <a name="required-development-guidelines"></a>Instructions dont le suivi est impératif pour le développement

Les instructions suivantes doivent être suivies lorsque vous écrivez vos applets de commande. Ils sont divisés en instructions pour la conception des applets de commande et des instructions pour l’écriture de votre code de l’applet de commande. Si vous ne suivez pas ces instructions, vos applets de commande peut échouer, et vos utilisateurs devront peut-être une mauvaise expérience lorsqu’ils utilisent vos applets de commande.

## <a name="in-this-topic"></a>Dans cette rubrique

### <a name="design-guidelines"></a>Règles de conception

- [Utilisez uniquement les verbes approuvés (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Noms d’applet de commande : Les caractères qui ne peut pas être utilisés (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Les noms de paramètres qui ne peut pas être utilisés (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Prise en charge les demandes de confirmations (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Prend en charge le paramètre Force pour les Sessions interactives (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objets de document de sortie (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Instructions de code

- [Dériver à partir de l’applet de commande ou les Classes de PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Spécifiez l’attribut de l’applet de commande (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Remplacer une entrée de traitement (méthode) (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Spécifier l’attribut OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Ne conservent pas les Handles vers des objets de sortie (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Gérer efficacement les erreurs (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Utiliser un Module PowerShell de Windows pour déployer vos applets de commande (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Règles de conception

Les instructions suivantes doivent être suivies lors de la conception des applets de commande pour garantir une expérience utilisateur cohérente entre l’utilisation de vos applets de commande et d’autres applets de commande. Lorsque vous trouvez une indication de conception qui s’appliquent à votre situation, veillez à consulter les instructions de Code pour obtenir des instructions similaires.

### <a name="use-only-approved-verbs-rd01"></a>Utilisez uniquement les verbes approuvés (RD01)

Le verbe spécifié dans l’attribut de l’applet de commande doit provenir de l’ensemble reconnu de verbes fournis par Windows PowerShell. Il ne doit pas être un de ses synonymes interdites. Utilisez les chaînes constantes qui sont définies par les énumérations suivantes pour spécifier les verbes d’applet de commande :

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Pour plus d’informations sur les noms de verbe approuvé, consultez [verbes d’applet de commande](./approved-verbs-for-windows-powershell-commands.md).

Les utilisateurs ont besoin d’un ensemble de noms de l’applet de commande détectable et attendu. Utilisez le verbe approprié afin que l’utilisateur peut effectuer une évaluation rapide de ce que fait une applet de commande et à découvrir facilement les fonctionnalités du système. Par exemple, la commande de ligne de commande suivante obtient une liste de toutes les commandes sur le système dont les noms commencent par « start » : `get-command start-*`. Les noms dans vos applets de commande permet de différencier vos applets de commande à partir d’autres applets de commande. Le nom indique que la ressource sur laquelle l’opération sera exécutée. L’opération elle-même est représentée par le verbe.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Noms d’applet de commande : Les caractères qui ne peut pas être utilisés (RD02)

Lorsque vous nommez des applets de commande, n’utilisez pas un des caractères spéciaux suivants.

|Caractère|Name|
|---------------|----------|
|#|signe dièse|
|,|comma|
|()|Parenthèses|
|{}|accolades|
|[]|crochets|
|&|« et commercial »|
|-|trait d’union **Remarque :**  Le trait d’union peut être utilisé pour séparer le verbe à partir du substantif, mais il ne peut pas être utilisé dans le nom ou le verbe.|
|/|marque de barre oblique|
|\|barre oblique inverse|
|$|Signe dollar|
|^|Signe insertion|
|;|Point-virgule|
|:|colon|
|"|guillemet double|
|'|guillemet simple|
|<>|crochets pointus|
|&#124;|barre verticale|
|?|point d’interrogation|
|@|arobase|
|' | sauvegarde tick (accent grave)|
|*|Astérisque|
|%|Signe de pourcentage|
|+|Signe plus|
|=|Signe égal|
|~|tilda|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Les noms de paramètres qui ne peut pas être utilisés (RD03)

Windows PowerShell fournit un ensemble commun de paramètres toutes les applets de commande ainsi que des paramètres supplémentaires qui sont ajoutés dans des situations spécifiques. Lorsque vous concevez vos propres applets de commande, vous ne pouvez pas utiliser les noms suivants : Confirmer, Debug, ErrorAction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction et Verbose. Pour plus d’informations sur ces paramètres, consultez [les noms de paramètres courants](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Prise en charge les demandes de confirmations (RD04)

Pour les cmdlets qui exécutent une opération qui modifie le système, ils doivent appeler le [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode pour demander de confirmation et dans certains cas appeler le [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode). (Le [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode doit être appelée uniquement après que le [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode est appelée.)

Pour effectuer ces appels de l’applet de commande doit spécifier qu’il prend en charge les demandes de confirmation en définissant le `SupportsShouldProcess` mot clé de l’attribut de l’applet de commande. Pour plus d’informations sur la définition de cet attribut, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Si l’attribut de l’applet de commande de la classe de l’applet de commande indique que l’applet de commande prend en charge les appels à la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode) et l’applet de commande ne peut pas effectuer l’appel à la [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode), l’utilisateur peut modifier le système de manière inattendue.

Utilisez le [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode pour la modification de n’importe quel système. Une préférence utilisateur et le `Whatif` contrôle des paramètres de la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). En revanche, le [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) appel effectue une vérification supplémentaire pour les modifications potentiellement dangereuses. Cette méthode n’est pas contrôlée par les préférences utilisateur ou le `Whatif` paramètre. Si votre applet de commande appelle le [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode), il doit avoir un `Force` paramètre qui ignore les appels à ces deux méthodes, et qui exécute l’opération. Ceci est important, car elle permet à votre applet de commande à utiliser dans les hôtes et les scripts non interactifs.

Si vos applets de commande prend en charge ces appels, l’utilisateur peut déterminer si l’action doit réellement être effectuée. Par exemple, le [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) applet de commande appelle le [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode avant d’arrêter un ensemble de processus essentiels, y compris le système, Winlogon, et Processus de Spoolsrv.

Pour plus d’informations sur la prise en charge de ces méthodes, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Prend en charge le paramètre Force pour les Sessions interactives (RD05)

Si votre applet de commande est utilisée de manière interactive, toujours fournir un paramètre Force pour remplacer les actions interactives, telles que les invites ou lire des lignes d’entrée). Ceci est important, car elle permet à votre applet de commande à utiliser dans les hôtes et les scripts non interactifs. Les méthodes suivantes peuvent être implémentées par un hôte interactif.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objets de document de sortie (RD06)

Windows PowerShell utilise les objets qui sont écrits dans le pipeline. Pour permettre aux utilisateurs de tirer parti des objets qui sont retournées par chaque applet de commande, vous devez documenter les objets qui sont retournées, et vous devez documenter ce que les membres de ces objets retournés sont utilisés pour.

## <a name="code-guidelines"></a>Instructions de code

Les instructions suivantes doivent être suivies lors de l’écriture de code de l’applet de commande. Lorsque vous trouvez une indication de Code qui s’appliquent à votre situation, veillez à examiner les règles de conception pour obtenir des instructions similaires.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Dériver à partir de l’applet de commande ou les Classes de PSCmdlet (RC01)

Une applet de commande doit être dérivé du [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) ou [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe de base. Applets de commande qui dérivent de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe ne dépendent pas de l’exécution de Windows PowerShell. Elles peuvent être appelées directement à partir de n’importe quel langage Microsoft .NET Framework. Applets de commande qui dérivent de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe dépendent de l’exécution de Windows PowerShell. Par conséquent, elles exécutent au sein d’une instance d’exécution.

Toutes les classes d’applet de commande que vous implémentez doivent être des classes publiques. Pour plus d’informations sur ces classes de l’applet de commande, consultez [vue d’ensemble de l’applet de commande](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Spécifiez l’attribut de l’applet de commande (RC02)

Pour une applet de commande être reconnus par Windows PowerShell, sa classe de .NET Framework doit être décorée avec l’attribut de l’applet de commande. Cet attribut spécifie les fonctionnalités suivantes de l’applet de commande.

- La paire verbe-substantif qui identifie l’applet de commande.

- Le jeu de paramètres par défaut qui est utilisé lorsque plusieurs jeux de paramètres est spécifiés. Le jeu de paramètres par défaut est utilisé lorsque Windows PowerShell n’a pas suffisamment d’informations pour déterminer le jeu de paramètres à utiliser.

- Indique si l’applet de commande prend en charge les appels à la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). Cette méthode affiche un message de confirmation à l’utilisateur avant de l’applet de commande effectue une modification dans le système. Pour plus d’informations sur la façon dont les demandes de confirmation sont effectuées, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

- Indiquer le niveau d’impact (ou la gravité) de l’action associée au message de confirmation. Dans la plupart des cas, la valeur par défaut du support de doit être utilisée. Pour plus d’informations sur la façon dont le niveau d’impact affecte les demandes de confirmation qui sont affichent à l’utilisateur, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).

Pour plus d’informations sur la façon de déclarer l’attribut de l’applet de commande, consultez [déclaration CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Remplacer une entrée de traitement (méthode) (RC03)

L’applet de commande participer à l’environnement Windows PowerShell, il doit substituer au moins une de ces *d’entrée des méthodes de traitement*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cette méthode est appelée une seule fois et il est utilisé pour fournir des fonctionnalités de pré-traitement.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cette méthode est appelée plusieurs fois, et il est utilisé pour fournir des fonctionnalités d’enregistrement par enregistrement.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cette méthode est appelée une seule fois et il est utilisé pour fournir des fonctionnalités de post-traitement.

### <a name="specify-the-outputtype-attribute-rc04"></a>Spécifier l’attribut OutputType (RC04)

L’attribut OutputType (introduite dans Windows PowerShell 2.0) spécifie le type de .NET Framework que votre applet de commande retourne au pipeline. En spécifiant le type de sortie de vos applets de commande, vous vérifiez les objets retournés par votre applet de commande plus détectables par les autres applets de commande. Pour plus d’informations sur la décoration de la classe d’applet de commande avec cet attribut, consultez [déclaration d’attribut OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Ne conservent pas les Handles vers des objets de sortie (RC05)

Votre applet de commande ne doit pas conserver des handles pour les objets qui sont passés à la [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode). Ces objets sont passés à l’applet de commande suivante dans le pipeline, ou elles sont utilisées par un script. Si vous conservez les poignées pour les objets, deux entités seront propriétaire de chaque objet, ce qui provoque des erreurs.

### <a name="handle-errors-robustly-rc06"></a>Gérer efficacement les erreurs (RC06)

Par nature, un environnement d’administration détecte et apporte des modifications importantes au système que vous administrez. Par conséquent, il est essentiel qu’applets de commande gérer correctement les erreurs. Pour plus d’informations sur les enregistrements d’erreur, consultez [rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md).

- Lorsqu’une erreur empêche une applet de commande de continuer à traiter les enregistrements de plus, c’est une erreur avec fin d’exécution. L’applet de commande doit appeler le [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) méthode qui fait référence à un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet. Si une exception n’est pas interceptée par l’applet de commande, le runtime de Windows PowerShell lui-même lève une erreur avec fin qui contient moins d’informations.

- Pour une erreur sans fin d’exécution qui n’empêche pas d’opération du prochain enregistrement provenant du pipeline (par exemple, un enregistrement généré par un processus différent), l’applet de commande doit appeler le [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode qui fait référence à un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet. Un exemple d’une erreur sans fin d’exécution est l’erreur qui se produit si un processus particulier ne parvient pas à arrêter. Appel de la [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode permet à l’utilisateur à effectuer de manière cohérente les actions requises et conserver les informations des actions particulières qui ne respectent pas. Votre applet de commande doit gérer chaque enregistrement de manière indépendante que possible.

- Le [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet qui est référencé par le [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) et [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthodes nécessite une exception en son cœur. Suivez les instructions de conception .NET Framework vous aider à déterminer l’exception à utiliser. Si l’erreur est sémantiquement identique à une exception existante, utilisez cette exception ou dériver de cette exception. Sinon, dérivez une nouvelle exception ou la hiérarchie des exceptions directement à partir de la [System.Exception](/dotnet/api/System.Exception) type.

Un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet nécessite également une catégorie d’erreur qui regroupe les erreurs pour l’utilisateur. L’utilisateur peut afficher les erreurs basées sur la catégorie en définissant la valeur de la `$ErrorView` variable d’environnement à CategoryView. Les catégories possibles sont définies par le [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) énumération.

- Si une applet de commande crée un nouveau thread, et si le code qui s’exécute dans ce thread lève une exception non gérée, Windows PowerShell n’intercepte pas l’erreur et le processus prendra fin.

- Si un objet a du code dans son destructeur qui lève une exception non gérée, Windows PowerShell n’intercepte pas l’erreur et le processus prendra fin. Cela se produit également si un objet appelle les méthodes Dispose qui provoquent une exception non gérée.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Utiliser un Module PowerShell de Windows pour déployer vos applets de commande (RC07)

Créer un module Windows PowerShell pour empaqueter et déployer vos applets de commande. Prise en charge pour les modules est introduite dans Windows PowerShell 2.0. Vous pouvez utiliser les assemblys qui contiennent vos classes de l’applet de commande directement en tant que fichiers de module binaire (c’est très utile lorsque vous testez vos applets de commande), ou vous pouvez créer un manifeste de module qui référence les assemblys de l’applet de commande. (Vous pouvez également ajouter des assemblys de composant logiciel enfichable existants lors de l’utilisation de modules.) Pour plus d’informations sur les modules, consultez [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Voir aussi

[Instructions vous êtes vivement invité du développement](./strongly-encouraged-development-guidelines.md)

[Directives de développement de Conseil](./advisory-development-guidelines.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
