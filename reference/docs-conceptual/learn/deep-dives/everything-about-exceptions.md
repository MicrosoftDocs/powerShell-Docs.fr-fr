---
title: Tout ce que vous avez toujours voulu savoir sur les exceptions
description: La gestion des erreurs fait partie intégrante du travail dès lors qu’il s’agit d’écrire du code.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: cd17ae6b5ded052c93923b648155a4dda8956b34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "90012559"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>Tout ce que vous avez toujours voulu savoir sur les exceptions

La gestion des erreurs fait partie intégrante du travail dès lors qu’il s’agit d’écrire du code. Le comportement attendu est couramment contrôlé par la vérification et la validation de conditions. En cas de problème inattendu, nous nous tournons vers la gestion des exceptions. Vous pouvez facilement gérer les exceptions générées par le code d’autres personnes, ou bien générer vos propres exceptions pour que d’autres les gèrent.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu. Consultez son blog à l’adresse [PowerShellExplained.com][].

## <a name="basic-terminology"></a>Terminologie de base

Examinons quelques termes de base avant de commencer.

### <a name="exception"></a>Exception

Une exception ressemble à un événement créé lorsque la gestion normale des erreurs ne parvient pas à traiter le problème.
Par exemple, une division par zéro ou le manque de mémoire provoquent une exception. Parfois, l’auteur du code que vous utilisez crée des exceptions pour certains problèmes lorsqu’ils se produisent.

### <a name="throw-and-catch"></a>Throw et catch

Quand une exception se produit, on dit qu’elle est levée (throw). Pour gérer une exception levée, vous devez l’intercepter ou la capturer (catch). Si une exception est levée mais n’est pas capturée, le script cesse de s’exécuter.

### <a name="the-call-stack"></a>Pile des appels

La pile des appels est la liste des fonctions qui se sont appelées. Chaque fonction appelée est ajoutée à la pile ou en haut de la liste. Lorsqu’elle se termine (exit ou return), elle est supprimée de la pile.

Quand une exception est levée, la pile des appels est vérifiée pour qu’un gestionnaire d’exceptions puisse l’intercepter.

### <a name="terminating-and-non-terminating-errors"></a>Erreurs bloquantes et non bloquantes

Une exception constitue généralement une erreur bloquante. Une fois levée, soit elle est interceptée, soit elle met fin à l’exécution en cours. Par défaut, une erreur non bloquante est générée par `Write-Error` et s’ajoute au flux de sortie sans lever d’exception.

C’est un point à savoir, car `Write-Error` et les autres erreurs non bloquantes ne déclenchent pas `catch`.

### <a name="swallowing-an-exception"></a>Dissimulation d’exceptions

Il s’agit de capturer une erreur pour se contenter de la supprimer. Utilisez ce procédé avec précaution, car il peut compliquer considérablement la résolution des problèmes.

## <a name="basic-command-syntax"></a>Syntaxe des commandes de base

Voici un tour d’horizon rapide de la syntaxe de gestion des exceptions de base utilisée dans PowerShell.

### <a name="throw"></a>Throw

Pour créer notre propre événement d’exception, nous levons une exception avec le mot clé `throw`,

```powershell
function Start-Something
{
    throw "Bad thing happened"
}
```

qui crée une exception à l’exécution. Il s’agit d’une erreur bloquante. Elle est gérée par un `catch` dans une fonction d’appel ou quitte le script avec un message comme celui-ci.

```powershell
PS> Start-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Write-Error -ErrorAction Stop

Comme nous l’avons vu, `Write-Error` ne génère pas d’erreur bloquante par défaut. Si l’on spécifie `-ErrorAction Stop` en revanche, `Write-Error` déclenche une erreur bloquante qui peut être gérée à l’aide d’un `catch`.

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

Merci à Lee Dailey d’avoir rappelé cette utilisation de `-ErrorAction Stop`.

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet -ErrorAction Stop

Spécifié sur une fonction ou une cmdlet avancée, `-ErrorAction Stop` convertit toutes les instructions `Write-Error` en erreurs bloquantes qui interrompent l’exécution ou qui peuvent être gérées par un `catch`.

```powershell
Start-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Try/Catch

La gestion des exceptions fonctionne ainsi dans PowerShell (et dans beaucoup d’autres langages) : on essaye (`try`) d’abord une section de code ; s’il génère une erreur, on peut l’intercepter (`catch`). Voici un exemple rapide.

```powershell
try
{
    Start-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Start-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

Le script `catch` s’exécute seulement en cas d’erreur bloquante. Si le bloc `try` s’exécute correctement, le bloc `catch` est ignoré.

### <a name="tryfinally"></a>Try/Finally

Il peut arriver qu’il ne soit pas nécessaire de gérer une erreur, mais qu’il faille quand même exécuter du code si une exception se produit. C’est le rôle d’un script `finally`.

Regardez cet exemple :

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

À chaque fois que l’on ouvre une ressource ou que l’on s’y connecte, il faut la fermer. Si `ExecuteNonQuery()` lève une exception, la connexion n’est pas arrêtée. Voici le même code à l’intérieur d’un bloc `try/finally`.

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

Dans cet exemple, la connexion est fermée qu’il se produise une erreur ou non. Le script `finally` s’exécute à chaque fois.

Comme l’exception n’est pas interceptée, elle est quand même propagée en haut de la pile des appels.

### <a name="trycatchfinally"></a>Try/Catch/Finally

Il est tout à fait possible d’utiliser `catch` et `finally` ensemble dans certains scénarios, même si dans la plupart des cas ils sont employés séparément.

## <a name="psitem"></a>$PSItem

Maintenant que nous avons vu les principes de base, nous pouvons aller un peu plus loin.

Dans le bloc `catch` se trouve une variable automatique (`$PSItem` ou `$_`) de type `ErrorRecord` qui contient les détails de l’exception. Voici un tour d’horizon rapide de quelques propriétés de la clé.

Dans ces exemples, l’exception était générée en utilisant un chemin d’accès non valide dans `ReadAllText`.

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem.ToString()

Cette fonction donne le message le plus propre possible pour la journalisation et la sortie générale. `ToString()` est appelé automatiquement si `$PSItem` est placé à l’intérieur d’une chaîne.

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem.InvocationInfo

Cette propriété contient des informations supplémentaires collectées par PowerShell sur la fonction ou le script où l’exception a été levée. Voici la propriété `InvocationInfo` provenant de l’exemple d’exception créé précédemment.

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

Les informations importantes sont le nom du script (`ScriptName`), la ligne (`Line`) de code et le numéro de ligne (`ScriptLineNumber`) où l’appel a commencé.

### <a name="psitemscriptstacktrace"></a>$PSItem.ScriptStackTrace

Cette propriété montre l’ordre des appels de fonction qui conduisent dans le code où l’exception a été générée.

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Start-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

Il n’y a ici que des appels à des fonctions dans le même script, mais elle suivrait les appels si plusieurs scripts étaient impliqués.

### <a name="psitemexception"></a>$PSItem.Exception

Il s’agit de l’exception réelle qui a été levée.

#### <a name="psitemexceptionmessage"></a>$PSItem.Exception.Message

Il s’agit du message général qui décrit l’exception, un bon point de départ pour la résolution des problèmes. La plupart des exceptions comportent un message par défaut, mais elles peuvent également être définies sur un message personnalisé lorsqu’elles sont levées.

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

Il s’agit également du message retourné lorsque `$PSItem.ToString()` est appelé, si aucun n’a été défini sur `ErrorRecord`.

#### <a name="psitemexceptioninnerexception"></a>$PSItem.Exception.InnerException

Les exceptions peuvent contenir des exceptions internes. C’est souvent le cas lorsque le code appelé intercepte une exception et en lève une autre. L’exception d’origine est placée à l’intérieur de la nouvelle.

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

Nous reviendrons sur ce sujet plus tard lorsque nous parlerons de lever à nouveau des exceptions.

#### <a name="psitemexceptionstacktrace"></a>$PSItem.Exception.StackTrace

Il s’agit de l’arborescence des appels de procédure (`StackTrace`) de l’exception. Contrairement à la `ScriptStackTrace` ci-dessus, celle-ci concerne les appels au code managé.

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

Cette arborescence des appels de procédure n’est accessible que si l’événement est levé à partir de code managé. Ici, une fonction .NET Framework est appelée directement ; c’est tout ce que l’on peut voir dans cet exemple. En général, lorsque l’on examine une arborescence des appels de procédure, on recherche l’endroit où s’arrête le code et où commencent les appels système.

## <a name="working-with-exceptions"></a>Utilisation des exceptions

La question des exceptions dépasse la syntaxe de base et les propriétés des exceptions.

### <a name="catching-typed-exceptions"></a>Interception des exceptions typées

Il est possible de choisir les exceptions à intercepter. Elles possèdent en effet un type,

```powershell
try
{
    Start-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

qui est vérifié pour chaque bloc `catch` jusqu’à ce qu’il en soit trouvé un qui corresponde à l’exception.
Il est important de comprendre que les exceptions peuvent hériter d’autres exceptions. Dans l'exemple ci-dessus, `FileNotFoundException` hérite de `IOException`. Par conséquent, si `IOException` arrivait en premier, ce serait elle qui serait appelée. Un seul bloc catch est appelé, même s’il existe plusieurs correspondances.

`IOException` correspondrait avec `System.IO.PathTooLongException` ; en revanche, rien n’intercepterait `InsufficientMemoryException`, qui serait donc propagée en haut de la pile.

### <a name="catch-multiple-types-at-once"></a>Interception de plusieurs types à la fois

Il est possible d’intercepter plusieurs types d’exceptions avec la même instruction `catch`.

```powershell
try
{
    Start-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

Merci à `/u/Sheppard_Ra` d’avoir suggéré cet ajout.

### <a name="throwing-typed-exceptions"></a>Déclenchement des exceptions typées

Il est possible de lever des exceptions typées dans PowerShell. Au lieu d’appeler `throw` avec une chaîne :

```powershell
throw "Could not find: $path"
```

Utilisez un accélérateur d’exception :

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

Toutefois, il est alors nécessaire de spécifier un message.

Vous pouvez également créer une nouvelle instance d’une exception à lever. Dans ce cas, le message est facultatif, car le système possède des messages par défaut pour toutes les exceptions intégrées.

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

Si vous n’utilisez pas la version 5.0 ou une version ultérieure de PowerShell, vous devez utiliser l’ancienne approche `New-Object`.

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

Une exception typée peut être interceptée par son type, comme nous l’avons vu dans la section précédente.

#### <a name="write-error--exception"></a>Write-Error -Exception

Ces exceptions typées peuvent être ajoutées à `Write-Error`, sachant qu’il restera possible d’intercepter (`catch`) les erreurs par type d’exception. Utilisez `Write-Error` comme dans les exemples suivants :

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

Nous pouvons alors l’intercepter ainsi :

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>La grande liste des exceptions .NET

Avec l’aide de la [communauté Reddit/r/PowerShell][], j’ai compilé une liste principale contenant des centaines d’exceptions .NET pour compléter ce billet.

- [La grande liste des exceptions .NET][]

L’idée est de rechercher dans cette liste des exceptions qui semblent adaptées à la situation. Essayez d’utiliser des exceptions dans l’espace de noms `System` de base.

### <a name="exceptions-are-objects"></a>Les exceptions sont des objets

Si vous commencez à utiliser de nombreuses exceptions typées, n’oubliez pas qu’il s’agit d’objets. Des exceptions différentes possèdent différents constructeurs et différentes propriétés. Dans la documentation [FileNotFoundException][] de `System.IO.FileNotFoundException`, il apparaît que l’on peut transmettre un message et un chemin de fichier.

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

Elle possède également une propriété `FileName` qui expose ce chemin du fichier.

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

Pour découvrir d’autres constructeurs et propriétés d’objets, consultez la [documentation .NET][].

### <a name="re-throwing-an-exception"></a>Exception levée plusieurs fois

Si le bloc `catch` ne sert qu’à lever (`throw`) la même exception, ne l’interceptez (`catch`) pas. Il ne faut intercepter (`catch`) une exception que pour la gérer ou effectuer une action quand elle se produit.

Il peut arriver que l’on souhaite exécuter une action sur une exception, mais lever à nouveau l’exception pour qu’elle puisse être traitée en aval : par exemple, écrire un message ou consigner le problème au moment de la détection, pour le gérer plus haut dans la pile.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

Point intéressant, si l’on appelle `throw` à partir du `catch`, il lève à nouveau l’exception actuelle.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

Lever à nouveau l’exception permet de conserver les informations d’exécution d’origine, comme le script source et le numéro de ligne. Si l’on déclenche une nouvelle exception, cela a pour effet de masquer l’endroit où l’exception a commencé.

#### <a name="re-throwing-a-new-exception"></a>Nouvelle exception levée plusieurs fois

Si vous interceptez une exception mais que vous souhaitez en lever une autre, imbriquez l’exception d’origine à l’intérieur de la nouvelle. Ainsi, elle sera accessible plus bas dans la pile en tant que `$PSItem.Exception.InnerException`.

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet.ThrowTerminatingError()

Le seul inconvénient de `throw` pour les exceptions brutes est que le message d’erreur pointe vers l’instruction `throw` et indique la ligne où se trouve le problème.

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```

Le fait qu’il précise que l’exécution du script s’est arrêtée parce que `throw` a été appelé à la ligne 31 n’est pas pertinent pour les utilisateurs du script, car non instructif.

Dexter Dhami a souligné que l’on peut utiliser `ThrowTerminatingError()` pour y remédier.

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

Si l’on suppose que `ThrowTerminatingError()` a été appelé à l’intérieur d’une fonction nommée `Get-Resource`, c’est cette erreur que l’on verrait.

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

Comme on peut le constater, elle pointe vers la fonction `Get-Resource` comme source du problème, ce qui constitue une information utile pour l’utilisateur.

Étant donné que `$PSItem` est un `ErrorRecord`, il est également possible d’utiliser `ThrowTerminatingError` de cette façon pour un nouveau déclenchement.

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

La source de l’erreur devient la cmdlet et les éléments internes de la fonction sont cachés aux utilisateurs de la cmdlet.

## <a name="try-can-create-terminating-errors"></a>Try peut créer des erreurs bloquantes

Kirk Munro signale que certaines exceptions ne constituent des erreurs bloquantes que si elles sont exécutées dans un bloc `try/catch`. Voici son exemple, qui génère une exception de division par zéro à l’exécution.

```powershell
function Start-Something { 1/(1-1) }
```

Appelez-le ainsi : comme vous pouvez le constater, il génère l’erreur, mais donne quand même le message.

```powershell
&{ Start-Something; Write-Output "We did it. Send Email" }
```

Toutefois, en plaçant ce même code à l’intérieur d’un bloc `try/catch`, le résultat est différent.

```powershell
try
{
    &{ Start-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```

L’erreur devient bloquante et ne génère pas le premier message. Le problème est que ce code peut se trouver dans une fonction et agir différemment si quelqu’un utilise un bloc `try/catch`.

Je n’ai personnellement pas rencontré ce problème, mais il s’agit d’un cas particulier à connaître.

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet.ThrowTerminatingError() dans un bloc try/catch

L’une des nuances de `$PSCmdlet.ThrowTerminatingError()` est qu’elle crée une erreur bloquante dans la cmdlet, mais devient une erreur non bloquante une fois sortie de la cmdlet. C’est donc à la personne qui appelle la fonction de décider comment gérer l’erreur. Elle peut la retransformer en erreur bloquante en utilisant `-ErrorAction Stop` ou en l’appelant à partir d’un bloc `try{...}catch{...}`.

### <a name="public-function-templates"></a>Modèles de fonctions publics

Par ailleurs, Kirk Munro place un bloc `try{...}catch{...}` autour de chaque bloc `begin`, `process` ou `end` dans toutes ses fonctions avancées. Dans ces blocs Catch génériques, il se sert d’une ligne unique utilisant `$PSCmdlet.ThrowTerminatingError($PSItem)` pour traiter toutes les exceptions qui quittent ses fonctions.

```powershell
function Start-Something
{
    [CmdletBinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSItem)
        }
    }
}
```

Étant donné que tout se trouve dans une instruction `try` dans les fonctions, l’ensemble fonctionne de manière cohérente. L’utilisateur final obtient également des erreurs propres, qui masquent le code interne.

## <a name="trap"></a>Trap

Nous nous sommes concentrés sur l’aspect `try/catch` des exceptions. Cependant, il existe une fonctionnalité héritée qu’il faut mentionner avant de conclure.

Un bloc `trap` est placé dans un script ou une fonction pour intercepter toutes les exceptions qui se produisent dans cette portée. Quand une exception se produit, le code du bloc `trap` est exécuté, puis le code normal reprend. Si plusieurs exceptions se produisent, le bloc trap est appelé plusieurs fois.

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

Je n’ai personnellement jamais adopté cette approche, mais elle peut être intéressante dans les scripts d’administrateur ou de contrôleur qui journalisent toutes les exceptions, puis continuent à s’exécuter.

## <a name="closing-remarks"></a>Remarques finales

Ajouter une gestion des exceptions adaptée aux scripts les rend non seulement plus stables, mais permet également de résoudre plus facilement ces exceptions.

Nous avons longuement parlé de `throw`, car il s’agit d’un concept fondamental pour la gestion des exceptions. PowerShell propose également `Write-Error`, qui gère toutes les situations où `throw` peut être utilisé. Ne concluez pas que vous devez employer `throw` après avoir lu ce billet.

Maintenant que j’ai pris le temps d’écrire sur la gestion des exceptions dans le détail, je vais utiliser `Write-Error -Stop` pour générer des erreurs dans mon code. Je vais également suivre le conseil de Kirk et faire de `ThrowTerminatingError` mon gestionnaire d’exceptions de prédilection pour toutes les fonctions.

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[Version d’origine]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Communauté Reddit/r/PowerShell]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[La grande liste des exceptions .NET]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: /dotnet/api/System.IO.FileNotFoundException
[Documentation .NET]: /dotnet/api
