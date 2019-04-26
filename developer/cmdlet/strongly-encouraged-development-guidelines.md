---
title: Nous recommandons fortement d’indications de développement | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067363"
---
# <a name="strongly-encouraged-development-guidelines"></a>Instructions dont le suivi est fortement recommandé pour le développement

Cette section décrit les instructions que vous devez suivre lorsque vous écrivez vos applets de commande. Ils sont divisés en instructions pour la conception des applets de commande et des instructions pour l’écriture de votre code de l’applet de commande. Vous pouvez constater que ces instructions ne sont pas applicables pour chaque scénario. Toutefois, si elles s’appliquent et que vous ne suivez pas ces instructions, vos utilisateurs peuvent avoir une mauvaise expérience lorsqu’ils utilisent vos applets de commande.

## <a name="design-guidelines"></a>Règles de conception

- [Utiliser un nom spécifique pour un nom de l’applet de commande (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Utilisez la casse Pascal pour les noms d’applet de commande (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Instructions de conception de paramètre (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Fournir des commentaires à l’utilisateur (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Créer un fichier d’aide de l’applet de commande (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Instructions de code

- [Paramètres de codage (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Prise en charge d’entrée de Pipeline bien défini (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Écrire des enregistrements uniques dans le Pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Rendre les applets de commande non-respect de la casse et de la casse (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Règles de conception

Vous devraient suivre les indications suivantes lors de la conception des applets de commande pour garantir une expérience utilisateur cohérente entre l’utilisation de vos applets de commande et d’autres applets de commande. Lorsque vous trouvez une indication de conception qui s’appliquent à votre situation, veillez à consulter les instructions de Code pour obtenir des instructions similaires.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Utiliser un nom spécifique pour un nom de l’applet de commande (SD01)

Les noms utilisés dans l’applet de commande d’affectation de noms doivent être très spécifique pour que l’utilisateur puisse détecter vos applets de commande. Préfixe des noms génériques tels que « server » avec une version abrégée du nom du produit. Par exemple, si un nom fait référence à un serveur qui exécute une instance de Microsoft SQL Server, utilisez un nom, par exemple « SQLServer ». La combinaison de noms spécifiques et une brève liste des verbes approuvés permettre à l’utilisateur de découvrir rapidement et d’anticiper leurs fonctionnalités tout en évitant les doublons parmi les noms de l’applet de commande.

Pour améliorer l’expérience utilisateur, le nom que vous choisissez pour un nom de l’applet de commande doit être au singulier. Par exemple, utilisez le nom `Get-Process` au lieu de **Get-processus**. Il est préférable de suivre cette règle pour tous les noms d’applet de commande, même si une applet de commande est susceptible d’agir sur plusieurs éléments.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Utilisez la casse Pascal pour les noms d’applet de commande (SD02)

Utilisez la casse Pascal pour les noms de paramètre. En d’autres termes, mettre en majuscule la première lettre du verbe et tous les termes utilisés dans le substantif. Par exemple, «`Clear-ItemProperty`».

### <a name="parameter-design-guidelines-sd03"></a>Instructions de conception de paramètre (SD03)

Paramètres qui reçoivent les données sur lequel il doit fonctionner a besoin d’une applet de commande et paramètres qui renvoient des informations qui sont utilisées pour déterminer les caractéristiques de l’opération. Par exemple, une applet de commande peut avoir un `Name` paramètre qui reçoit des données à partir du pipeline et l’applet de commande peut avoir un `Force` paramètre pour indiquer que l’applet de commande peut être forcé pour effectuer son opération. Il n’existe aucune limite au nombre de paramètres permettant de définir une applet de commande.

#### <a name="use-standard-parameter-names"></a>Utiliser des noms de paramètres Standard

Votre applet de commande doit utiliser des noms de paramètres standard afin que l’utilisateur peut rapidement déterminer ce que signifie un paramètre particulier. Si un nom plus spécifique est requis, utilisez un nom de paramètre standard, puis spécifiez un nom plus spécifique en tant qu’alias. Par exemple, le `Get-Service` applet de commande possède un paramètre qui a un nom générique (`Name`) et un alias plus spécifique (`ServiceName`). Les deux termes peuvent être utilisés pour spécifier le paramètre.

Pour plus d’informations sur les noms de paramètres et leurs types de données, consultez [nom de paramètre d’applet de commande et des instructions de la fonctionnalité](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Utiliser des noms de paramètre au singulier

Évitez d’utiliser des noms au pluriel pour les paramètres dont la valeur est un élément unique. Cela inclut des paramètres qui acceptent les tableaux ou listes car l’utilisateur peut fournir un tableau ou une liste avec un seul élément.

Les noms de paramètre au pluriel doivent être utilisés uniquement dans les cas où la valeur du paramètre est toujours une valeur de plusieurs éléments. Dans ce cas, l’applet de commande doit vérifier que plusieurs éléments sont fournis, et l’applet de commande doit afficher un avertissement à l’utilisateur si plusieurs éléments ne sont pas fournis.

#### <a name="use-pascal-case-for-parameter-names"></a>Utilisez la casse Pascal pour les noms de paramètre

Utilisez la casse Pascal pour les noms de paramètre. En d’autres termes, mettre en majuscule la première lettre de chaque mot dans le nom du paramètre, y compris la première lettre du nom. Par exemple, le nom du paramètre `ErrorAction` utilise la casse correcte. Les noms de paramètre suivants utilisent la mise en majuscule :

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Paramètres qui acceptent une liste d’Options

Il existe deux façons de créer un paramètre dont la valeur peut être sélectionnée à partir d’un ensemble d’options.

- Définir un type d’énumération (ou utiliser un type énumération existant) qui spécifie les valeurs valides. Ensuite, utilisez le type d’énumération pour créer un paramètre de ce type.

- Ajouter le **ValidateSet** à la déclaration de paramètre d’attribut. Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Utilisez les Types Standard pour les paramètres

Pour garantir la cohérence avec les autres applets de commande, utilisez les types standard pour les paramètres maximum. Pour plus d’informations sur les types qui doit être utilisé pour le paramètre différentes, consultez [Standard noms de paramètre d’applet de commande et les Types](./standard-cmdlet-parameter-names-and-types.md). Cette rubrique fournit des liens vers des rubriques qui décrivent les noms et types .NET Framework pour les groupes de paramètres standard, tels que les paramètres « activité ».

#### <a name="use-strongly-typed-net-framework-types"></a>Utiliser des Types fortement typée de .NET Framework

Les paramètres doivent être définis en tant que types .NET Framework pour fournir une meilleure validation de paramètre. Par exemple, les paramètres qui sont limitées à une seule valeur à partir d’un ensemble de valeurs doivent être définis comme un type d’énumération. Pour prendre en charge une valeur de l’identificateur URI (Uniform Resource), définissez le paramètre comme un [System.Uri](/dotnet/api/System.Uri) type. Éviter les paramètres de chaînes de base pour les propriétés de tout sauf texte libre.

#### <a name="use-consistent-parameter-types"></a>Utiliser des Types de paramètre cohérents

Quand le même paramètre est utilisé par plusieurs applets de commande, utilisez toujours le même type de paramètre.  Par exemple, si le `Process` paramètre est un [System.Int16](/dotnet/api/System.Int16) type pour une applet de commande, n’apportez pas les `Process` paramètre pour une autre applet de commande un [System.Uint16](/dotnet/api/System.UInt16) type.

#### <a name="parameters-that-take-true-and-false"></a>Paramètres qui acceptent True et False

Si votre paramètre accepte uniquement `true` et `false`, définissez le paramètre en tant que type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Un paramètre de commutateur est traité comme `true` lorsqu’il est spécifié dans une commande. Si le paramètre n’est pas inclus dans une commande, Windows PowerShell considère que la valeur du paramètre à être `false`. Ne définissez pas les paramètres booléens.

Si votre paramètre doit faire la distinction entre les 3 valeurs : $true, $false et « non spécifiée », puis définir un paramètre de type Nullable\<bool >.  La nécessité d’un 3e, valeur « non spécifiée » se produit généralement lorsque l’applet de commande peut modifier la propriété booléenne d’un objet. Dans ce cas « non spécifiée » signifie de ne pas modifier la valeur actuelle de la propriété.

#### <a name="support-arrays-for-parameters"></a>Prise en charge des tableaux de paramètres

Souvent, les utilisateurs doivent effectuer la même opération par rapport à plusieurs arguments. Pour ces utilisateurs, une applet de commande doit accepter un tableau en tant que paramètre d’entrée afin qu’un utilisateur peut passer les arguments dans le paramètre comme une variable Windows PowerShell. Par exemple, le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande utilise un tableau pour les chaînes qui identifient les noms des processus à récupérer.

#### <a name="support-the-passthru-parameter"></a>Prend en charge le paramètre PassThru

Par défaut, nombreuses applets de commande qui modifient le système, telles que la [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) applet de commande, agir en tant que « récepteurs » pour les objets et ne retournent pas un résultat. Ces cmdlet doit implémenter le `PassThru` paramètre pour forcer l’applet de commande pour retourner un objet. Lorsque le `PassThru` paramètre est spécifié, l’applet de commande retourne un objet à l’aide d’un appel à la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode). Par exemple, la commande suivante arrête le processus Calc et transmet le processus résultant au pipeline.

```powershell
Stop-Process calc -passthru
```

Dans la plupart des cas, les applets de commande Add, Set et New doit prendre en charge un `PassThru` paramètre.

#### <a name="support-parameter-sets"></a>Prise en charge les jeux de paramètres

Une applet de commande est destinée à accomplir une seule fonction. Toutefois, il est souvent plusieurs façons pour décrire l’opération ou la cible de l’opération. Par exemple, un processus peut être identifié par son nom, par son identificateur ou par un processus. L’applet de commande doit prendre en charge toutes les représentations raisonnables de ses cibles. Normalement, l’applet de commande répond à cette exigence en spécifiant des jeux de paramètres (appelés jeux de paramètres) qui fonctionnent ensemble. Un seul paramètre peut appartenir à n’importe quel nombre de jeux de paramètres. Pour plus d’informations sur les jeux de paramètres, consultez [définit des paramètres d’applet de commande](./cmdlet-parameter-sets.md).

Lorsque vous spécifiez des jeux de paramètres, ne définissez qu’un seul paramètre dans le jeu de ValueFromPipeline. Pour plus d’informations sur la façon de déclarer la **paramètre** d’attribut, consultez [ParameterAttribute déclaration](./parameter-attribute-declaration.md).

Lorsque les jeux de paramètres sont utilisés, le jeu de paramètres par défaut est défini par le **applet de commande** attribut. Le jeu de paramètres par défaut doit inclure les paramètres susceptibles d’être utilisé dans une session Windows PowerShell interactive. Pour plus d’informations sur la façon de déclarer la **applet de commande** d’attribut, consultez [déclaration CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Fournir des commentaires à l’utilisateur (SD04)

Utilisez les instructions de cette section pour fournir des commentaires à l’utilisateur. Ces commentaires permet à l’utilisateur pour être conscient de ce qui se produit dans le système et prendre des décisions mieux d’administration.

Le runtime de Windows PowerShell autorise un utilisateur de spécifier comment gérer la sortie à partir de chaque appel à la `Write` méthode en définissant une variable de préférence. L’utilisateur peut définir plusieurs variables de préférence, y compris une variable qui détermine si le système doit afficher des informations et une variable qui détermine si le système doit interroger l’utilisateur avant d’entreprendre une autre action.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Prise en charge des WriteWarning, WriteVerbose, WriteDebug méthodes

Une applet de commande doit appeler le [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) méthode lors de l’applet de commande est sur le point d’effectuer une opération qui peut avoir un résultat inattendu. Par exemple, une applet de commande doit appeler cette méthode si l’applet de commande est sur le point de remplacer un fichier en lecture seule.

Une applet de commande doit appeler le [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) méthode lorsque l’utilisateur requiert certains détails sur ce que fait l’applet de commande. Par exemple, une applet de commande doit appeler ces informations si l’auteur de l’applet de commande pense qu’il existe des scénarios qui peuvent nécessiter plus d’informations sur ce que fait l’applet de commande.

L’applet de commande doit appeler le [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) méthode lorsqu’un ingénieur du support produit ou le développeur doit comprendre ce qui a endommagé l’opération de l’applet de commande. Il n’est pas nécessaire pour l’applet de commande pour appeler le [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) méthode dans le même code qui appelle le [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (méthode) Étant donné que le `Debug` paramètre présente deux ensembles d’informations.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>WriteProgress prise en charge pour les opérations qui prennent beaucoup de temps

Opérations de l’applet de commande qui prennent beaucoup de temps et qui ne peut pas s’exécuter en arrière-plan doit prendre en charge les cours de création de rapports via des appels périodiques à la [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (méthode).

#### <a name="use-the-host-interfaces"></a>Utiliser les Interfaces de l’hôte

Parfois, une applet de commande doit communiquer directement avec l’utilisateur au lieu d’à l’aide de divers écrivant ou doivent les méthodes prises en charge par le [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Dans ce cas, l’applet de commande doit dériver de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe et d’utiliser le [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propriété. Cette propriété prend en charge différents niveaux de type de communication, y compris les types PromptForChoice, une invite et WriteLine/ReadLine. Niveau au plus spécifique, il fournit également les méthodes pour lire et écrire des clés individuelles et faire face aux mémoires tampons.

Sauf si une applet de commande est spécifiquement conçu pour générer une interface utilisateur graphique (GUI), il ne doit pas contourner l’hôte à l’aide de la [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propriété. Est un exemple d’une applet de commande qui est conçu pour générer une interface utilisateur graphique la [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) applet de commande.

> [!NOTE]
> Applets de commande ne doivent pas utiliser le [System.Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Créer un fichier d’aide de l’applet de commande (SD05)

Pour chaque assembly de l’applet de commande, créez un fichier Help.xml qui contient des informations sur l’applet de commande. Ces informations comprennent une description de l’applet de commande, les descriptions des paramètres de l’applet de commande, les exemples d’utilisation de l’applet de commande et bien plus encore.

## <a name="code-guidelines"></a>Instructions de code

Les instructions suivantes doivent être observées lors du codage des applets de commande pour garantir une expérience utilisateur cohérente entre l’utilisation de vos applets de commande et d’autres applets de commande. Lorsque vous trouvez une indication de Code qui s’appliquent à votre situation, veillez à examiner les règles de conception pour obtenir des instructions similaires.

### <a name="coding-parameters-sc01"></a>Paramètres de codage (SC01)

Définir un paramètre en déclarant une propriété publique de la classe d’applet de commande qui est décorée avec le **paramètre** attribut. Paramètres n’ont pas à être des membres statiques de la classe dérivée de .NET Framework pour l’applet de commande. Pour plus d’informations sur la façon de déclarer la **paramètre** d’attribut, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Prend en charge les chemins d’accès de Windows PowerShell

Le chemin d’accès Windows PowerShell est le mécanisme de normaliser l’accès aux espaces de noms. Lorsque vous affectez un chemin d’accès Windows PowerShell à un paramètre dans l’applet de commande, l’utilisateur peut définir un personnalisé « lecteur » qui agit comme un raccourci vers un chemin d’accès spécifique. Lorsqu’un utilisateur désigne un lecteur de ce type, les données stockées, telles que les données dans le Registre, peuvent être utilisées de manière cohérente.

Si votre applet de commande permet à l’utilisateur spécifier un fichier ou une source de données, elle doit définir un paramètre de type [System.String](/dotnet/api/System.String). Si la prise en charge de plusieurs lecteurs, le type doit être un tableau. Le nom du paramètre doit être `Path`, avec un alias de `PSPath`. En outre, le `Path` paramètre doit prendre en charge les caractères génériques. Si prise en charge des caractères génériques n’est pas nécessaire, définissez un `LiteralPath` paramètre.

Si les données que l’applet de commande lit ou écrit doit être un fichier, l’applet de commande doit accepter l’entrée de chemin d’accès Windows PowerShell, et l’applet de commande doit utiliser le [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) propriété à traduire le Windows Chemins d’accès PowerShell en chemins d’accès qui reconnaît le système de fichiers. Les mécanismes spécifiques incluent les méthodes suivantes :

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Si les données que l’applet de commande lit ou écrit sont uniquement un ensemble de chaînes au lieu d’un fichier, l’applet de commande doit utiliser les informations de fournisseur de contenu (`Content` membre) pour lire et écrire. Ces informations sont obtenues à partir de la [System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) propriété. Ces mécanismes offrent d’autres magasins de données de participer à la lecture et l’écriture des données.

#### <a name="support-wildcard-characters"></a>Prise en charge des caractères génériques

Une applet de commande doit prendre en charge les caractères génériques si possible. Prise en charge des caractères génériques se produit à plusieurs emplacements dans une applet de commande (en particulier lorsqu’un paramètre accepte une chaîne pour identifier un objet à partir d’un ensemble d’objets). Par exemple, l’exemple **Stop-Process** applet de commande à partir de la [StopProc didacticiel](./stopproc-tutorial.md) définit un `Name` paramètre pour traiter les chaînes qui représentent les noms de processus. Ce paramètre prend en charge les caractères génériques afin que l’utilisateur peut spécifier facilement les processus à arrêter.

Lorsque la prise en charge pour le caractère générique caractères est disponible, une opération de l’applet de commande génère généralement un tableau. Parfois, il est inutile pour prendre en charge d’un tableau, car l’utilisateur peut utiliser qu’un seul élément à la fois. Par exemple, le [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) applet de commande n’a pas besoin prendre en charge d’un tableau, car l’utilisateur consiste à définir qu’un seul emplacement. Dans ce cas, l’applet de commande prend toujours en charge les caractères génériques, mais il force la résolution vers un emplacement unique.

Pour plus d’informations sur les modèles de caractère générique-caractères, consultez [prenant en charge les caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Définition d’objets

Cette section contient des instructions pour définir les objets pour les applets de commande et pour étendre les objets existants.

##### <a name="define-standard-members"></a>Définir les membres Standard

Définir des membres standards pour étendre un type d’objet dans un fichier Types.ps1xml personnalisé (utilisez le fichier PowerShell Types.ps1xml de Windows en tant que modèle). Les membres standards sont définis par un nœud portant le nom PSStandardMembers. Ces définitions autorisent d’autres applets de commande et l’exécution de Windows PowerShell pour travailler avec votre objet de manière cohérente.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Définir ObjectMembers à utiliser en tant que paramètres

Si vous créez un objet pour une applet de commande, assurez-vous que ses membres sont mappés directement aux paramètres des applets de commande qui va l’utiliser. Ce mappage permet à l’objet à envoyer facilement au pipeline et à passer d’une cmdlet vers un autre.

Objets .NET Framework qui sont retournés par les applets de commande fréquemment manque certains membres importants ou pratiques qui sont requises par le développeur de scripts ou l’utilisateur. Ces membres manquants peuvent être particulièrement importantes pour l’affichage et la création des noms le membre approprié afin que l’objet peut être correctement transmis au pipeline. Créer un fichier Types.ps1xml personnalisé pour documenter ces membres requis. Lorsque vous créez ce fichier, nous vous recommandons de la convention d’affectation de noms suivante : *< Your_Product_Name >*. Types.ps1xml.

Par exemple, vous pouvez ajouter un `Mode` script de propriété pour le [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type pour afficher les attributs d’un fichier plus clairement. En outre, vous pouvez ajouter un `Count` propriété d’alias vers la [System.Array](/dotnet/api/System.Array) type pour autoriser l’utilisation cohérente de ce nom de propriété (au lieu de `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implémentez l’Interface IComparable

Implémentez un [System.IComparable](/dotnet/api/System.IComparable) interface sur tous les objets de sortie. Ainsi, les objets de sortie être facilement transmis à diverses applets de commande de tri et l’analyse.

##### <a name="update-display-information"></a>Mettre à jour les informations d’affichage

Si l’affichage d’un objet ne fournit pas les résultats attendus, créer un personnalisé  *\<YourProductName >*. Fichier format.ps1xml pour cet objet.

### <a name="support-well-defined-pipeline-input-sc02"></a>Prise en charge d’entrée de Pipeline bien défini (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implémentez pour la partie centrale d’un Pipeline

Implémenter une applet de commande en supposant qu’elle sera appelée à partir du milieu d’un pipeline (autrement dit, autres applets de commande sera produire son entrée ou utiliser sa sortie). Par exemple, vous pouvez supposer que le `Get-Process` applet de commande, car elle génère des données, est utilisé uniquement comme la première applet de commande dans un pipeline. Toutefois, étant donné que cette applet de commande est destinée au milieu d’un pipeline, cette applet de commande permet d’applets de commande précédente ou les données dans le pipeline pour spécifier les processus à récupérer.

#### <a name="support-input-from-the-pipeline"></a>Entrée de prise en charge du pipeline

Dans chaque jeu de paramètres pour une applet de commande, inclure au moins un paramètre qui prend en charge d’entrée provenant du pipeline. Prise en charge pour l’entrée de pipeline permet à l’utilisateur à récupérer des données ou objets, de les envoyer à l’ensemble de paramètres corrects et pour passer les résultats directement à une applet de commande.

Un paramètre accepte une entrée du pipeline si la **paramètre** attribut inclut le `ValueFromPipeline` mot clé, le `ValueFromPipelineByPropertyName` attribut de mot clé, ou les deux mots clés dans sa déclaration. Si aucun des paramètres dans un paramètre de prise en charge set le `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` mots clés, l’applet de commande concrètement ne peut pas être placés après une autre applet de commande, car il ignore toute entrée de pipeline.

#### <a name="support-the-processrecord-method"></a>Prend en charge la méthode ProcessRecord

Pour accepter tous les enregistrements à partir de l’applet de commande précédent dans le pipeline, votre applet de commande doit implémenter le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode). Windows PowerShell appelle cette méthode plusieurs fois, une fois pour chaque enregistrement qui est envoyé à votre applet de commande.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Écrire des enregistrements uniques dans le Pipeline (SC03)

Quand une applet de commande retourne des objets, l’applet de commande doit écrire les objets immédiatement qu’ils sont générés. L’applet de commande ne devriez pas les conserver afin de les mettre en mémoire tampon dans un tableau combiné. Les applets de commande qui reçoivent les objets en tant qu’entrée sera ensuite en mesure de traiter, afficher, ou traiter et afficher les objets de sortie sans délai. Objets d’une applet de commande qui génère une sortie à la fois doit appeler le [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode). Une applet de commande qui génère des objets de sortie par lots (par exemple, car une API sous-jacente retourne un tableau d’objets de sortie) doit appeler la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) défini avec son deuxième paramètre (méthode) à `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Rendre les applets de commande non-respect de la casse et de la casse (SC04)

Par défaut, Windows PowerShell respecte la casse. Toutefois, comme il traite avec de nombreux systèmes préexistants, Windows PowerShell conserve les cas pour la facilité de fonctionnement et de compatibilité. En d’autres termes, si un caractère est fourni en lettres majuscules, Windows PowerShell met constamment en lettres majuscules. Pour les systèmes pour un fonctionnement optimal, une applet de commande doit suivre cette convention. Si possible, il doit fonctionner de la casse. Il doit, cependant, conserver le cas d’origine pour les applets de commande qui se produisent ultérieurement dans une commande ou dans le pipeline.

## <a name="see-also"></a>Voir aussi

[Directives de développement requis](./required-development-guidelines.md)

[Directives de développement de Conseil](./advisory-development-guidelines.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
