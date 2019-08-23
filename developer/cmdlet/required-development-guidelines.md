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
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986667"
---
# <a name="required-development-guidelines"></a>Instructions dont le suivi est impératif pour le développement

Les instructions suivantes doivent être suivies lors de l’écriture de vos applets de commande. Elles sont réparties en instructions pour concevoir des applets de commande et des instructions pour l’écriture de votre code d’applet de commande. Si vous ne suivez pas ces instructions, vos applets de commande peuvent échouer et vos utilisateurs peuvent avoir une expérience médiocre lorsqu’ils utilisent vos applets de commande.

## <a name="in-this-topic"></a>Dans cette rubrique

### <a name="design-guidelines"></a>Instructions de conception

- [Utiliser uniquement les verbes approuvés (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Noms des applets de commande: Caractères qui ne peuvent pas être utilisés (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Noms de paramètres qui ne peuvent pas être utilisés (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Demandes de confirmation de support (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Paramètre force de support pour les sessions interactives (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objets de sortie de document (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Instructions de code

- [Dérivation à partir de l’applet de commande ou des classes PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Spécifier l’attribut d’applet de commande (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Remplacer une méthode de traitement d’entrée (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Spécifier l’attribut OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Ne pas conserver les descripteurs des objets de sortie (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Gérer les erreurs de façon robuste (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Utiliser un module Windows PowerShell pour déployer vos applets de commande (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Instructions de conception

Les instructions suivantes doivent être suivies lors de la conception des applets de commande pour garantir une expérience utilisateur cohérente entre l’utilisation de vos applets de commande et d’autres applets de commande. Lorsque vous trouvez une instruction de conception qui s’applique à votre situation, veillez à consulter les instructions de code pour obtenir des instructions similaires.

### <a name="use-only-approved-verbs-rd01"></a>Utiliser uniquement les verbes approuvés (RD01)

Le verbe spécifié dans l’attribut d’applet de commande doit provenir du jeu de verbes reconnu fourni par Windows PowerShell. Il ne doit pas s’agir de l’un des synonymes interdits. Utilisez les chaînes constantes définies par les énumérations suivantes pour spécifier des verbes d’applet de commande:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Pour plus d’informations sur les noms de verbe approuvés, consultez verbes d' [applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

Les utilisateurs ont besoin d’un ensemble de noms d’applets de commande détectables et attendus. Utilisez le verbe approprié pour permettre à l’utilisateur d’effectuer une évaluation rapide de ce que fait une applet de commande et de découvrir facilement les fonctionnalités du système. Par exemple, la commande de ligne de commande suivante obtient une liste de toutes les commandes du système dont les noms commencent par «Start» `get-command start-*`:. Utilisez les noms de vos applets de commande pour différencier vos applets de commande des autres applets de commande. Le nom indique la ressource sur laquelle l’opération sera effectuée. L’opération elle-même est représentée par le verbe.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Noms des applets de commande: Caractères qui ne peuvent pas être utilisés (RD02)

Lorsque vous nommez des applets de commande, n’utilisez pas les caractères spéciaux suivants.

|Caractère|Name|
|---------------|----------|
|#|signe dièse|
|.|point|
|()|parenthèses|
|{}|accolades|
|[]|crochets|
|&|reprises|
|-|Note du trait d’Union **:**  Le trait d’Union peut être utilisé pour séparer le verbe du nom, mais il ne peut pas être utilisé dans le substantif ou dans le verbe.|
|/|barre oblique|
|\\| barre oblique inverse|
|$|signe dollar|
|^|signe insertion|
|;|virgule|
|:|signe|
|"|guillemet double|
|'|guillemet simple|
|<>|chevrons|
|&#124;|barre verticale|
|?|point d’interrogation|
|@|arobase|
|`|cycle d’arrière-plan (accent grave)|
|*|sert|
|%|signe de pourcentage|
|+|signe plus|
|=|signe égal|
|~|surmonté|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Noms de paramètres qui ne peuvent pas être utilisés (RD03)

Windows PowerShell fournit un ensemble commun de paramètres à toutes les applets de commande, ainsi que des paramètres supplémentaires qui sont ajoutés dans des situations spécifiques. Lorsque vous concevez vos propres applets de commande, vous ne pouvez pas utiliser les noms suivants: Confirm, Debug, ErrorAction, ErrorVariable, unbuffer, unvariable, WarningAction, WarningVariable, WhatIf, UseTransaction et Verbose. Pour plus d’informations sur ces paramètres, consultez [noms de paramètres communs](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Demandes de confirmation de support (RD04)

Pour les cmdlets qui effectuent une opération qui modifie le système, ils doivent appeler la méthode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour demander confirmation et, dans certains cas, appeler l' [applet de commande Méthode System. Management. Automation. applet de commande. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . (La méthode [System. Management. Automation. applet de commande. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doit être appelée uniquement après l’appel de la méthode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .)

Pour effectuer ces appels, l’applet de commande doit spécifier qu’elle prend en charge `SupportsShouldProcess` les demandes de confirmation en définissant le mot clé de l’attribut d’applet de commande. Pour plus d’informations sur la définition de cet attribut, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.

> [!NOTE]
> Si l’attribut d’applet de commande de la classe d’applet de commande indique que l’applet de commande prend en charge les appels à la méthode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et que l’applet de commande ne parvient pas à appeler l' [applet de commande Méthode System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l’utilisateur peut modifier le système de manière inattendue.

Utilisez la méthode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour toute modification du système. Une préférence de l’utilisateur `WhatIf` et le paramètre contrôlent la méthode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . En revanche, l’appel [System. Management. Automation. applet de commande. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) effectue une vérification supplémentaire pour les modifications potentiellement dangereuses. Cette méthode n’est pas contrôlée par une préférence utilisateur ni `WhatIf` par le paramètre. Si votre applet de commande appelle la méthode [System. Management. Automation. applet de commande. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , `Force` elle doit avoir un paramètre qui ignore les appels à ces deux méthodes et qui poursuit l’opération. C’est important, car cela permet d’utiliser votre applet de commande dans des hôtes et des scripts non interactifs.

Si vos applets de commande prennent en charge ces appels, l’utilisateur peut déterminer si l’action doit réellement être effectuée. Par exemple, l’applet de commande [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) appelle la méthode [System. Management. Automation. applet de commande. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) avant d’arrêter un ensemble de processus critiques, y compris les processus System, Winlogon et spoolsv.

Pour plus d’informations sur la prise en charge de ces méthodes, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Paramètre force de support pour les sessions interactives (RD05)

Si votre applet de commande est utilisée de manière interactive, fournissez toujours un paramètre force pour remplacer les actions interactives, telles que les invites ou la lecture des lignes d’entrée. C’est important, car cela permet d’utiliser votre applet de commande dans des hôtes et des scripts non interactifs. Les méthodes suivantes peuvent être implémentées par un hôte interactif.

- [System. Management. Automation. Host. PSHostUserInterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. Host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. Host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. Host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. Host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objets de sortie de document (RD06)

Windows PowerShell utilise les objets qui sont écrits dans le pipeline. Pour que les utilisateurs puissent tirer parti des objets retournés par chaque applet de commande, vous devez documenter les objets qui sont retournés, et vous devez documenter les membres desquels les objets retournés sont utilisés.

## <a name="code-guidelines"></a>Instructions de code

Les instructions suivantes doivent être suivies lors de l’écriture du code de l’applet de commande. Lorsque vous trouvez une indication de code qui s’applique à votre situation, veillez à consulter les instructions de conception pour obtenir des instructions similaires.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Dérivation à partir de l’applet de commande ou des classes PSCmdlet (RC01)

Une applet de commande doit dériver de la classe de base [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande ou [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Les applets de commande qui dérivent de la classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande ne dépendent pas du runtime Windows PowerShell. Elles peuvent être appelées directement à partir de n’importe quel langage Microsoft .NET Framework. Les applets de commande qui dérivent de la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) dépendent du runtime Windows PowerShell. Par conséquent, elles s’exécutent dans une instance d’exécution.

Toutes les classes d’applet de commande que vous implémentez doivent être des classes publiques. Pour plus d’informations sur ces classes d’applet de commande, consultez [vue d’ensemble](./cmdlet-overview.md)des applets de commande.

### <a name="specify-the-cmdlet-attribute-rc02"></a>Spécifier l’attribut d’applet de commande (RC02)

Pour qu’une applet de commande soit reconnue par Windows PowerShell, sa classe .NET Framework doit être décorée avec l’attribut applet de commande. Cet attribut spécifie les fonctionnalités suivantes de l’applet de commande.

- Paire verbe-and-substantif qui identifie l’applet de commande.

- Jeu de paramètres par défaut utilisé lorsque plusieurs jeux de paramètres sont spécifiés. Le jeu de paramètres par défaut est utilisé lorsque Windows PowerShell ne dispose pas de suffisamment d’informations pour déterminer le jeu de paramètres à utiliser.

- Indique si l’applet de commande prend en charge les appels à la méthode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Cette méthode affiche un message de confirmation à l’utilisateur avant que l’applet de commande apporte une modification au système. Pour plus d’informations sur la façon dont les demandes de confirmation sont effectuées, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

- Indiquez le niveau d’impact (gravité) de l’action associée au message de confirmation. Dans la plupart des cas, la valeur par défaut moyenne doit être utilisée. Pour plus d’informations sur la façon dont le niveau d’impact affecte les demandes de confirmation qui sont affichées à l’utilisateur, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).

Pour plus d’informations sur la façon de déclarer l’attribut d’applet de commande, consultez [déclaration CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Remplacer une méthode de traitement d’entrée (RC03)

Pour que l’applet de commande participe à l’environnement Windows PowerShell, elle doit remplacer au moins l’une des *méthodes de traitement d’entrée*suivantes.

[System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cette méthode est appelée une fois et elle est utilisée pour fournir des fonctionnalités de pré-traitement.

[System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cette méthode est appelée plusieurs fois, et elle est utilisée pour fournir des fonctionnalités d’enregistrement par enregistrement.

[System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cette méthode est appelée une fois, et elle est utilisée pour fournir la fonctionnalité de publication.

### <a name="specify-the-outputtype-attribute-rc04"></a>Spécifier l’attribut OutputType (RC04)

L’attribut OutputType (introduit dans Windows PowerShell 2,0) spécifie le type de .NET Framework que votre applet de commande retourne au pipeline. En spécifiant le type de sortie de vos applets de commande, vous rendez les objets retournés par votre applet de commande plus détectables par d’autres applets de commande. Pour plus d’informations sur la décoration de la classe cmdlet avec cet attribut, consultez la [déclaration d’attribut OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Ne pas conserver les descripteurs des objets de sortie (RC05)

Votre applet de commande ne doit pas conserver les descripteurs des objets passés à la méthode [System. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Ces objets sont passés à l’applet de commande suivante dans le pipeline, ou ils sont utilisés par un script. Si vous conservez les descripteurs aux objets, deux entités posséderont chaque objet, ce qui génère des erreurs.

### <a name="handle-errors-robustly-rc06"></a>Gérer les erreurs de façon robuste (RC06)

Un environnement d’administration détecte par nature et apporte des modifications importantes au système que vous gérez. Par conséquent, il est vital que les applets de commande gèrent correctement les erreurs. Pour plus d’informations sur les enregistrements d’erreurs, consultez [rapport d’erreurs Windows PowerShell](./error-reporting-concepts.md).

- Lorsqu’une erreur empêche une applet de commande de continuer à traiter d’autres enregistrements, il s’agit d’une erreur de fin. L’applet de commande doit appeler la méthode [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) qui référence un objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Si une exception n’est pas interceptée par l’applet de commande, le runtime Windows PowerShell lui-même lève une erreur de fin contenant moins d’informations.

- Pour une erreur sans fin d’exécution qui n’arrête pas l’opération sur l’enregistrement suivant provenant du pipeline (par exemple, un enregistrement produit par un processus différent), l’applet de commande doit appeler la méthode [System. Management. Automation. applet de commande. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) qui fait référence à un objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Un exemple d’erreur sans fin d’exécution est l’erreur qui se produit en cas d’échec de l’arrêt d’un processus particulier. L’appel de la méthode [System. Management. Automation. applet de commande. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) permet à l’utilisateur d’effectuer de manière cohérente les actions demandées et de conserver les informations pour des actions particulières qui échouent. Votre applet de commande doit gérer chaque enregistrement de la manière la plus indépendante possible.

- L’objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) qui est référencé par les méthodes [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) et [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) requiert un exception à son noyau. Suivez les instructions de conception de .NET Framework lorsque vous déterminez l’exception à utiliser. Si l’erreur est sémantiquement identique à une exception existante, utilisez cette exception ou dérivez de cette exception. Sinon, dérivez une nouvelle exception ou une nouvelle hiérarchie d’exception directement à partir du type [System. exception](/dotnet/api/System.Exception) .

Un objet [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nécessite également une catégorie d’erreur qui regroupe les erreurs de l’utilisateur. L’utilisateur peut afficher les erreurs en fonction de la catégorie en définissant la `$ErrorView` valeur de la variable d’interpréteur de commandes sur CategoryView. Les catégories possibles sont définies par l’énumération [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Si une applet de commande crée un nouveau thread et si le code qui s’exécute dans ce thread lève une exception non gérée, Windows PowerShell n’intercepte pas l’erreur et met fin au processus.

- Si un objet a du code dans son destructeur qui provoque une exception non gérée, Windows PowerShell n’intercepte pas l’erreur et met fin au processus. Cela se produit également si un objet appelle des méthodes dispose qui provoquent une exception non gérée.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Utiliser un module Windows PowerShell pour déployer vos applets de commande (RC07)

Créez un module Windows PowerShell pour empaqueter et déployer vos applets de commande. La prise en charge des modules est introduite dans Windows PowerShell 2,0. Vous pouvez utiliser les assemblys qui contiennent vos classes d’applet de commande directement comme fichiers de module binaire (cette fonctionnalité est très utile lors du test de vos applets de commande), ou vous pouvez créer un manifeste de module qui référence les assemblys d’applet de commande. (Vous pouvez également ajouter des assemblys de composant logiciel enfichable existants lors de l’utilisation de modules.) Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Voir aussi

[Instructions de développement vivement encouragées](./strongly-encouraged-development-guidelines.md)

[Conseils pour le développement d’avis](./advisory-development-guidelines.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
