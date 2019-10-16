---
title: Instructions de développement vivement encouragées | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369338"
---
# <a name="strongly-encouraged-development-guidelines"></a>Instructions dont le suivi est fortement recommandé pour le développement

Cette section décrit les instructions que vous devez suivre lorsque vous écrivez vos applets de commande. Elles sont réparties en instructions pour concevoir des applets de commande et des instructions pour l’écriture de votre code d’applet de commande. Vous pouvez constater que ces instructions ne s’appliquent pas à chaque scénario. Toutefois, s’ils s’appliquent et que vous ne suivez pas ces instructions, vos utilisateurs peuvent avoir une expérience médiocre lorsqu’ils utilisent vos applets de commande.

## <a name="design-guidelines"></a>Instructions de conception

- [Utiliser un nom spécifique pour un nom d’applet de commande (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Utiliser la casse Pascal pour les noms d’applets de commande (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Recommandations en matière de conception de paramètres (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Fournir des commentaires à l’utilisateur (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Créer un fichier d’aide d’applet de commande (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Instructions de code

- [Paramètres de codage (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Prendre en charge l’entrée de pipeline bien définie (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Écrire des enregistrements uniques dans le pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Rendre les applets de commande non sensibles à la casse et à la conservation de la casse (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Instructions de conception

Les instructions suivantes doivent être suivies lors de la conception des applets de commande pour garantir une expérience utilisateur cohérente entre l’utilisation de vos applets de commande et d’autres applets de commande. Lorsque vous trouvez une instruction de conception qui s’applique à votre situation, veillez à consulter les instructions de code pour obtenir des instructions similaires.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Utiliser un nom spécifique pour un nom d’applet de commande (SD01)

Les noms utilisés dans les applets de commande doivent être très spécifiques afin que l’utilisateur puisse découvrir vos applets de commande. Préfixez les noms génériques tels que « Server » avec une version abrégée du nom du produit. Par exemple, si un nom fait référence à un serveur qui exécute une instance de Microsoft SQL Server, utilisez un nom tel que « SQLServer ». La combinaison de noms spécifiques et la liste réduite de verbes approuvés permettent à l’utilisateur de découvrir et d’anticiper rapidement les fonctionnalités tout en évitant la duplication parmi les noms d’applets de commande.

Pour améliorer l’expérience utilisateur, le nom que vous choisissez pour un nom d’applet de commande doit être singulier. Par exemple, utilisez le nom `Get-Process` au lieu de « **obtenir-Processes »** . Il est préférable de suivre cette règle pour tous les noms d’applet de commande, même lorsqu’une applet de commande est susceptible d’agir sur plus d’un élément.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Utiliser la casse Pascal pour les noms d’applets de commande (SD02)

Utilisez la casse Pascal pour les noms de paramètres. En d’autres termes, mettez en majuscule la première lettre du verbe et tous les termes utilisés dans le nom. Par exemple, « `Clear-ItemProperty` ».

### <a name="parameter-design-guidelines-sd03"></a>Recommandations en matière de conception de paramètres (SD03)

Une applet de commande a besoin de paramètres qui reçoivent les données sur lesquelles elle doit s’exécuter, ainsi que des paramètres qui indiquent les informations utilisées pour déterminer les caractéristiques de l’opération. Par exemple, une applet de commande peut avoir un paramètre `Name` qui reçoit des données du pipeline, et l’applet de commande peut avoir un paramètre `Force` pour indiquer que l’applet de commande peut être forcée à exécuter son opération. Il n’existe aucune limite au nombre de paramètres qu’une applet de commande peut définir.

#### <a name="use-standard-parameter-names"></a>Utiliser des noms de paramètres standard

Votre applet de commande doit utiliser des noms de paramètres standard pour permettre à l’utilisateur de déterminer rapidement ce que signifie un paramètre particulier. Si un nom plus spécifique est requis, utilisez un nom de paramètre standard, puis spécifiez un nom plus spécifique en tant qu’alias. Par exemple, l’applet de commande `Get-Service` a un paramètre qui a un nom générique (`Name`) et un alias plus spécifique (`ServiceName`). Les deux termes peuvent être utilisés pour spécifier le paramètre.

Pour plus d’informations sur les noms de paramètres et leurs types de données, consultez [instructions relatives au nom du paramètre d’applet de commande et aux fonctionnalités](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Utiliser des noms de paramètres singuliers

Évitez d’utiliser des noms au pluriel pour les paramètres dont la valeur est un élément unique. Cela comprend les paramètres qui acceptent des tableaux ou des listes, car l’utilisateur peut fournir un tableau ou une liste avec un seul élément.

Les noms de paramètres au pluriel doivent être utilisés uniquement dans les cas où la valeur du paramètre est toujours une valeur à plusieurs éléments. Dans ces cas, l’applet de commande doit vérifier que plusieurs éléments sont fournis, et l’applet de commande doit afficher un avertissement à l’utilisateur si plusieurs éléments ne sont pas fournis.

#### <a name="use-pascal-case-for-parameter-names"></a>Utiliser la casse Pascal pour les noms de paramètres

Utilisez la casse Pascal pour les noms de paramètres. En d’autres termes, mettez en majuscule la première lettre de chaque mot dans le nom du paramètre, y compris la première lettre du nom. Par exemple, le nom du paramètre `ErrorAction` utilise la mise en majuscules correcte. Les noms de paramètres suivants utilisent une casse incorrecte :

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Paramètres qui acceptent une liste d’options

Il existe deux façons de créer un paramètre dont la valeur peut être sélectionnée à partir d’un ensemble d’options.

- Définissez un type d’énumération (ou utilisez un type d’énumération existant) qui spécifie les valeurs valides. Utilisez ensuite le type d’énumération pour créer un paramètre de ce type.

- Ajoutez l’attribut **ValidateSet** à la déclaration de paramètre. Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Utiliser des types standard pour les paramètres

Pour garantir la cohérence avec d’autres applets de commande, utilisez des types standard pour les paramètres dans la mesure du possible. Pour plus d’informations sur les types qui doivent être utilisés pour des paramètres différents, consultez [noms et types de paramètres d’applet](./standard-cmdlet-parameter-names-and-types.md)de commande standard. Cette rubrique fournit des liens vers plusieurs rubriques qui décrivent les noms et les types de .NET Framework pour les groupes de paramètres standard, tels que les « paramètres d’activité ».

#### <a name="use-strongly-typed-net-framework-types"></a>Utiliser des types de .NET Framework fortement typés

Les paramètres doivent être définis en tant que types de .NET Framework pour fournir une meilleure validation des paramètres. Par exemple, les paramètres qui sont limités à une valeur d’un ensemble de valeurs doivent être définis en tant que type énumération. Pour prendre en charge une valeur Uniform Resource Identifier (URI), définissez le paramètre en tant que type [System. Uri](/dotnet/api/System.Uri) . Évitez les paramètres de chaîne de base pour toutes les propriétés de texte de forme libre.

#### <a name="use-consistent-parameter-types"></a>Utiliser des types de paramètres cohérents

Lorsque le même paramètre est utilisé par plusieurs applets de commande, utilisez toujours le même type de paramètre.  Par exemple, si le paramètre `Process` est un type [System. Int16](/dotnet/api/System.Int16) pour une applet de commande, ne faites pas du paramètre `Process` pour une autre applet de commande de type [System. Uint16](/dotnet/api/System.UInt16) .

#### <a name="parameters-that-take-true-and-false"></a>Paramètres qui prennent la valeur true et false

Si votre paramètre accepte uniquement `true` et `false`, définissez le paramètre en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter). Un paramètre de commutateur est traité comme `true` lorsqu’il est spécifié dans une commande. Si le paramètre n’est pas inclus dans une commande, Windows PowerShell considère que la valeur du paramètre est `false`. Ne définissez pas de paramètres booléens.

Si votre paramètre doit faire la distinction entre 3 valeurs : $true, $false et "Unspecified", définissez un paramètre de type Nullable @ no__t-0bool >.  La nécessité d’une troisième valeur « non spécifiée » se produit généralement lorsque l’applet de commande peut modifier une propriété booléenne d’un objet. Dans ce cas, « non spécifié » signifie que vous ne pouvez pas modifier la valeur actuelle de la propriété.

#### <a name="support-arrays-for-parameters"></a>Tableaux de prise en charge pour les paramètres

Souvent, les utilisateurs doivent effectuer la même opération sur plusieurs arguments. Pour ces utilisateurs, une applet de commande doit accepter un tableau comme entrée de paramètre afin qu’un utilisateur puisse passer les arguments dans le paramètre en tant que variable Windows PowerShell. Par exemple, l’applet de commande [« obtenir-process »](/powershell/module/Microsoft.PowerShell.Management/Get-Process) utilise un tableau pour les chaînes qui identifient les noms des processus à récupérer.

#### <a name="support-the-passthru-parameter"></a>Prendre en charge le paramètre PassThru

Par défaut, de nombreuses applets de commande qui modifient le système, telles que l’applet de commande [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) , agissent en tant que « récepteurs » pour les objets et ne retournent pas de résultat. Ces applets de commande doivent implémenter le paramètre `PassThru` pour forcer l’applet de commande à retourner un objet. Lorsque le paramètre `PassThru` est spécifié, l’applet de commande retourne un objet à l’aide d’un appel à la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Par exemple, la commande suivante arrête le processus Calc et passe le processus résultant au pipeline.

```powershell
Stop-Process calc -passthru
```

Dans la plupart des cas, les applets de commande Add, Set et New doivent prendre en charge un paramètre `PassThru`.

#### <a name="support-parameter-sets"></a>Jeux de paramètres de prise en charge

Une applet de commande est destinée à atteindre un objectif unique. Toutefois, il existe souvent plusieurs façons de décrire l’opération ou la cible de l’opération. Par exemple, un processus peut être identifié par son nom, par son identificateur ou par un objet de processus. L’applet de commande doit prendre en charge toutes les représentations raisonnables de ses cibles. Normalement, l’applet de commande répond à cette exigence en spécifiant des jeux de paramètres (appelés jeux de paramètres) qui fonctionnent ensemble. Un paramètre unique peut appartenir à n’importe quel nombre de jeux de paramètres. Pour plus d’informations sur les jeux de paramètres, consultez [jeux de paramètres d’applet](./cmdlet-parameter-sets.md)de commande.

Lorsque vous spécifiez des jeux de paramètres, définissez un seul paramètre dans la valeur ValueFromPipeline. Pour plus d’informations sur la façon de déclarer l’attribut de **paramètre** , consultez [déclaration ParameterAttribute](./parameter-attribute-declaration.md).

Lorsque vous utilisez des jeux de paramètres, le jeu de paramètres par défaut est défini par l’attribut d' **applet** de commande. Le jeu de paramètres par défaut doit inclure les paramètres les plus susceptibles d’être utilisés dans une session Windows PowerShell interactive. Pour plus d’informations sur la façon de déclarer l’attribut d' **applet** de commande, consultez [déclaration CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Fournir des commentaires à l’utilisateur (SD04)

Utilisez les instructions de cette section pour fournir des commentaires à l’utilisateur. Ces commentaires permettent à l’utilisateur d’être conscient de ce qui se produit dans le système et de prendre de meilleures décisions administratives.

Le runtime Windows PowerShell permet à un utilisateur de spécifier comment gérer la sortie de chaque appel à la méthode `Write` en définissant une variable de préférence. L’utilisateur peut définir plusieurs variables de préférence, y compris une variable qui détermine si le système doit afficher des informations et une variable qui détermine si le système doit interroger l’utilisateur avant d’effectuer une action supplémentaire.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Prendre en charge les méthodes WriteWarning, WriteVerbose et WriteDebug

Une applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) quand l’applet de commande est sur le lieu d’effectuer une opération qui peut avoir un résultat inattendu. Par exemple, une applet de commande doit appeler cette méthode si l’applet de commande est sur le lieu de remplacer un fichier en lecture seule.

Une applet de commande doit appeler la méthode [System. Management. Automation. applet de commande. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) quand l’utilisateur a besoin de détails sur ce que fait l’applet de commande. Par exemple, une applet de commande doit appeler ces informations si l’auteur de l’applet de commande pense que des scénarios peuvent nécessiter des informations supplémentaires sur ce que fait l’applet de commande.

L’applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) lorsqu’un développeur ou un ingénieur du support technique doit comprendre ce qui a endommagé l’opération de l’applet de commande. Il n’est pas nécessaire que l’applet de commande appelle la méthode [System. Management. Automation. applet de commande. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dans le même code qui appelle la méthode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) , car le paramètre `Debug` présente les deux ensembles d’informations.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Prise en charge de WriteProgress pour les opérations qui prennent beaucoup de temps

Les opérations d’applet de commande qui prennent beaucoup de temps et qui ne peuvent pas s’exécuter en arrière-plan doivent prendre en charge la création de rapports de progression via des appels périodiques à la méthode [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

#### <a name="use-the-host-interfaces"></a>Utiliser les interfaces d’hôte

Parfois, une applet de commande doit communiquer directement avec l’utilisateur au lieu d’utiliser les différentes méthodes d’écriture ou de gestion prises en charge par la classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande. Dans ce cas, l’applet de commande doit dériver de la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) et utiliser la propriété [System. Management. Automation. PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Cette propriété prend en charge différents niveaux de type de communication, y compris les types PromptForChoice, prompt et WriteLine/ReadLine. Au niveau le plus spécifique, il fournit également des moyens de lire et d’écrire des clés individuelles et de gérer les mémoires tampons.

À moins qu’une applet de commande ne soit spécifiquement conçue pour générer une interface utilisateur graphique (GUI), elle ne doit pas ignorer l’hôte à l’aide de la propriété [System. Management. Automation. PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . L’applet de commande [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) est un exemple d’applet de commande conçue pour générer une interface graphique utilisateur.

> [!NOTE]
> Les applets de commande ne doivent pas utiliser l’API [System. console](/dotnet/api/System.Console) .

### <a name="create-a-cmdlet-help-file-sd05"></a>Créer un fichier d’aide d’applet de commande (SD05)

Pour chaque assembly d’applet de commande, créez un fichier Help. XML qui contient des informations sur l’applet de commande. Ces informations incluent une description de l’applet de commande, des descriptions des paramètres de l’applet de commande, des exemples de l’utilisation de l’applet de commande, etc.

## <a name="code-guidelines"></a>Instructions de code

Les instructions suivantes doivent être suivies lors du codage des applets de commande pour garantir une expérience utilisateur cohérente entre l’utilisation de vos applets de commande et d’autres applets de commande. Lorsque vous trouvez une indication de code qui s’applique à votre situation, veillez à consulter les instructions de conception pour obtenir des instructions similaires.

### <a name="coding-parameters-sc01"></a>Paramètres de codage (SC01)

Définissez un paramètre en déclarant une propriété publique de la classe cmdlet qui est décorée avec l’attribut **Parameter** . Les paramètres ne doivent pas nécessairement être des membres statiques de la classe de .NET Framework dérivée pour l’applet de commande. Pour plus d’informations sur la façon de déclarer l’attribut de **paramètre** , consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Prendre en charge les chemins Windows PowerShell

Le chemin d’accès Windows PowerShell est le mécanisme permettant de normaliser l’accès aux espaces de noms. Lorsque vous attribuez un chemin d’accès Windows PowerShell à un paramètre dans l’applet de commande, l’utilisateur peut définir un « lecteur » personnalisé qui agit comme raccourci vers un chemin d’accès spécifique. Lorsqu’un utilisateur désigne un tel lecteur, les données stockées, telles que les données du Registre, peuvent être utilisées de manière cohérente.

Si votre applet de commande permet à l’utilisateur de spécifier un fichier ou une source de données, il doit définir un paramètre de type [System. String](/dotnet/api/System.String). Si plusieurs lecteurs sont pris en charge, le type doit être un tableau. Le nom du paramètre doit être `Path`, avec l’alias `PSPath`. En outre, le paramètre `Path` doit prendre en charge les caractères génériques. Si la prise en charge des caractères génériques n’est pas nécessaire, définissez un paramètre `LiteralPath`.

Si les données que l’applet de commande lit ou écrit doivent être un fichier, l’applet de commande doit accepter l’entrée de chemin d’accès Windows PowerShell, et l’applet de commande doit utiliser la propriété [System. Management. Automation. SessionState. Path](/dotnet/api/System.Management.Automation.SessionState.Path) pour convertir les chemins d’accès Windows PowerShell en chemins d’accès reconnus par le système de fichiers. Les mécanismes spécifiques incluent les méthodes suivantes :

- [System. Management. Automation. PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Si les données que l’applet de commande lit ou écrit ne sont qu’un ensemble de chaînes au lieu d’un fichier, l’applet de commande doit utiliser les informations de contenu du fournisseur (`Content`) pour lire et écrire. Ces informations sont obtenues à partir de la propriété [System. Management. Automation. Provider. CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) . Ces mécanismes permettent à d’autres magasins de données de participer à la lecture et à l’écriture de données.

#### <a name="support-wildcard-characters"></a>Prendre en charge les caractères génériques

Une applet de commande doit prendre en charge les caractères génériques si possible. La prise en charge des caractères génériques se produit à de nombreux emplacements dans une applet de commande (surtout lorsqu’un paramètre prend une chaîne pour identifier un objet d’un ensemble d’objets). Par exemple, l’applet de commande **Stop-proc** du [didacticiel StopProc](./stopproc-tutorial.md) définit un paramètre `Name` pour gérer les chaînes qui représentent des noms de processus. Ce paramètre prend en charge les caractères génériques afin que l’utilisateur puisse spécifier facilement les processus à arrêter.

Lorsque la prise en charge des caractères génériques est disponible, une opération d’applet de commande produit généralement un tableau. Parfois, il n’est pas judicieux de prendre en charge un tableau, car l’utilisateur ne peut utiliser qu’un seul élément à la fois. Par exemple, l’applet de commande [set-location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) n’a pas besoin de prendre en charge un tableau, car l’utilisateur ne définit qu’un seul emplacement. Dans ce cas, l’applet de commande prend toujours en charge les caractères génériques, mais elle force la résolution sur un emplacement unique.

Pour plus d’informations sur les modèles de caractères génériques, consultez [prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md)commande.

#### <a name="defining-objects"></a>Définir des objets

Cette section contient des instructions pour la définition d’objets pour les applets de commande et pour l’extension d’objets existants.

##### <a name="define-standard-members"></a>Définir des membres standard

Définir des membres standard pour étendre un type d’objet dans un fichier. ps1xml de types personnalisés (utilisez le fichier Windows PowerShell types. ps1xml en tant que modèle). Les membres standard sont définis par un nœud portant le nom PSStandardMembers. Ces définitions autorisent d’autres applets de commande et le runtime Windows PowerShell à travailler avec votre objet de manière cohérente.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Définir ObjectMembers à utiliser comme paramètres

Si vous concevez un objet pour une applet de commande, assurez-vous que ses membres mappent directement aux paramètres des applets de commande qui l’utiliseront. Ce mappage permet d’envoyer facilement l’objet au pipeline et de le passer d’une applet de commande à l’autre.

Les objets .NET Framework préexistants retournés par les applets de commande sont souvent absents de certains membres importants ou pratiques qui sont requis par le développeur ou l’utilisateur de script. Ces membres manquants peuvent être particulièrement importants pour l’affichage et pour la création des noms de membres corrects afin que l’objet puisse être correctement transmis au pipeline. Créez un fichier Custom types. ps1xml pour documenter ces membres requis. Lorsque vous créez ce fichier, nous vous recommandons d’utiliser la Convention d’affectation de noms suivante : *< Your_Product_Name >* . Types. ps1xml.

Par exemple, vous pouvez ajouter une propriété de script `Mode` au type [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) pour afficher plus clairement les attributs d’un fichier. En outre, vous pouvez ajouter une propriété d’alias `Count` au type [System. Array](/dotnet/api/System.Array) pour permettre l’utilisation cohérente de ce nom de propriété (au lieu de `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implémenter l’interface IComparable

Implémentez une interface [System. IComparable](/dotnet/api/System.IComparable) sur tous les objets de sortie. Cela permet aux objets de sortie d’être facilement redirigés vers diverses applets de commande de tri et d’analyse.

##### <a name="update-display-information"></a>Mettre à jour les informations d’affichage

Si l’affichage d’un objet ne fournit pas les résultats attendus, créez un *> @no__t 1YourProductName*personnalisé. Fichier format. ps1xml pour cet objet.

### <a name="support-well-defined-pipeline-input-sc02"></a>Prendre en charge l’entrée de pipeline bien définie (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implémentez pour le milieu d’un pipeline

Implémentez une applet de commande en supposant qu’elle sera appelée à partir du milieu d’un pipeline (autrement dit, d’autres applets de commande produiront son entrée ou consomment sa sortie). Par exemple, vous pouvez supposer que l’applet de commande `Get-Process`, car elle génère des données, est utilisé uniquement comme première applet de commande dans un pipeline. Toutefois, étant donné que cette applet de commande est conçue pour le milieu d’un pipeline, cette applet de commande autorise les applets de commande ou les données précédentes dans le pipeline à spécifier les processus à récupérer.

#### <a name="support-input-from-the-pipeline"></a>Prendre en charge l’entrée à partir du pipeline

Dans chaque jeu de paramètres pour une applet de commande, incluez au moins un paramètre qui prend en charge l’entrée du pipeline. La prise en charge de l’entrée de pipeline permet à l’utilisateur de récupérer des données ou des objets, de les envoyer au jeu de paramètres correct et de transmettre les résultats directement à une applet de commande.

Un paramètre accepte l’entrée du pipeline si l’attribut de **paramètre** comprend le mot clé `ValueFromPipeline`, l’attribut de mot clé `ValueFromPipelineByPropertyName` ou les deux mots clés dans sa déclaration. Si aucun des paramètres d’un jeu de paramètres ne prend en charge les mots clés `ValueFromPipeline` ou `ValueFromPipelineByPropertyName`, l’applet de commande ne peut pas être placée de manière significative après une autre applet de commande, car elle ignore toute entrée de pipeline.

#### <a name="support-the-processrecord-method"></a>Prendre en charge la méthode ProcessRecord

Pour accepter tous les enregistrements de l’applet de commande précédente dans le pipeline, votre applet de commande doit implémenter la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Windows PowerShell appelle cette méthode plusieurs fois, une fois pour chaque enregistrement envoyé à votre applet de commande.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Écrire des enregistrements uniques dans le pipeline (SC03)

Lorsqu’une applet de commande retourne des objets, l’applet de commande doit écrire les objets immédiatement à mesure qu’ils sont générés. L’applet de commande ne doit pas les conserver pour les mettre en mémoire tampon dans un tableau combiné. Les applets de commande qui reçoivent les objets en entrée sont ensuite en mesure de traiter, d’afficher ou de traiter et d’afficher les objets de sortie sans délai. Une applet de commande qui génère des objets de sortie l’un après l’autre doit appeler la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Une applet de commande qui génère des objets de sortie par lots (par exemple, parce qu’une API sous-jacente retourne un tableau d’objets de sortie) doit appeler la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) avec le deuxième paramètre défini sur `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Rendre les applets de commande non sensibles à la casse et à la conservation de la casse (SC04)

Par défaut, Windows PowerShell lui-même ne respecte pas la casse. Toutefois, étant donné qu’il traite de nombreux systèmes préexistants, Windows PowerShell conserve la casse pour faciliter l’exploitation et la compatibilité. En d’autres termes, si un caractère est fourni en majuscules, Windows PowerShell le conserve en majuscules. Pour que les systèmes fonctionnent correctement, une applet de commande doit suivre cette Convention. Si possible, elle doit fonctionner sans respect de la casse. Toutefois, il doit conserver le cas d’origine des applets de commande qui se produisent ultérieurement dans une commande ou dans le pipeline.

## <a name="see-also"></a>Voir aussi

[Instructions de développement requises](./required-development-guidelines.md)

[Conseils pour le développement d’avis](./advisory-development-guidelines.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
