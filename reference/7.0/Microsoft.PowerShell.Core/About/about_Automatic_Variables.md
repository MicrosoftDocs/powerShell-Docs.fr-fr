---
description: Décrit les variables qui stockent des informations d’État pour PowerShell. Ces variables sont créées et gérées par PowerShell.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: d99d800680c5cf5ae01ac0cbb16ccaf6a91aada5
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577255"
---
# <a name="about-automatic-variables"></a>À propos des variables automatiques

## <a name="short-description"></a>Description courte

Décrit les variables qui stockent des informations d’État pour PowerShell. Ces variables sont créées et gérées par PowerShell.

## <a name="long-description"></a>Description longue

Conceptuellement, ces variables sont considérées comme étant en lecture seule. Même s’ils **peuvent** être écrits dans, pour des raisons de compatibilité descendante, ils ne **doivent pas** être écrits.

Voici une liste des variables automatiques dans PowerShell :

### <a name=""></a>$$

Contient le dernier jeton de la dernière ligne reçue par la session.

### <a name=""></a>$?

Contient l’état d’exécution de la dernière commande. Elle contient la **valeur true** si la dernière commande a réussi et **false** si elle a échoué.

Pour les applets de commande et les fonctions avancées qui sont exécutées à plusieurs étapes dans un pipeline, par exemple dans les `process` `end` blocs et, l’appel de `this.WriteError()` ou, respectivement, `$PSCmdlet.WriteError()` à n’importe quel point, est défini `$?` sur **false**, comme c’est le cas `this.ThrowTerminatingError()` et `$PSCmdlet.ThrowTerminatingError()` .

L' `Write-Error` applet de commande affecte toujours la `$?` **valeur false** immédiatement après son exécution, mais elle n’a pas la valeur `$?` **false** pour une fonction qui l’appelle :

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

Dans ce dernier cas, `$PSCmdlet.WriteError()` doit être utilisé à la place.

Pour les commandes natives (exécutables), a la valeur `$?` **true** lorsque a la valeur `$LASTEXITCODE` 0, et la valeur **false** lorsque `$LASTEXITCODE` est une autre valeur.

> [!NOTE]
> Jusqu’à PowerShell 7, contenant une instruction dans les parenthèses, la syntaxe de sous-expression `(...)` ou l’expression de tableau est `$(...)` `@(...)` toujours réinitialisée `$?` à **true**, de sorte que `(Write-Error)` affiche la `$?` **valeur true**.
> Cela a été modifié dans PowerShell 7, afin de `$?` refléter toujours la réussite réelle de la dernière commande exécutée dans ces expressions.

### <a name=""></a>$^

Contient le premier jeton de la dernière ligne reçue par la session.

### <a name="_"></a>$_

Comme pour `$PSItem`. Contient l’objet actuel dans l’objet de pipeline. Vous pouvez utiliser cette variable dans les commandes qui exécutent une action sur chaque objet ou sur les objets sélectionnés dans un pipeline.

### <a name="args"></a>$args

Contient un tableau de valeurs pour les paramètres non déclarés passés à une fonction, à un script ou à un bloc de script. Lorsque vous créez une fonction, vous pouvez déclarer les paramètres à l’aide du `param` mot clé ou en ajoutant une liste de paramètres séparés par des virgules entre parenthèses après le nom de la fonction.

Dans une action d’événement, la `$Args` variable contient des objets qui représentent les arguments d’événement de l’événement en cours de traitement. Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement.
La valeur de cette variable peut également être trouvée dans la propriété **SourceArgs** de l’objet **PSEventArgs** `Get-Event` retourné par.

### <a name="consolefilename"></a>$ConsoleFileName

Contient le chemin d’accès du fichier de console ( `.psc1` ) qui a été le plus récemment utilisé dans la session. Cette variable est remplie lorsque vous démarrez PowerShell à l’aide du paramètre **PSConsoleFile** ou lorsque vous utilisez l' `Export-Console` applet de commande pour exporter des noms de composant logiciel enfichable vers un fichier de console.

Lorsque vous utilisez l' `Export-Console` applet de commande sans paramètres, elle met à jour automatiquement le fichier de console qui a été utilisé le plus récemment dans la session. Vous pouvez utiliser cette variable automatique pour déterminer le fichier qui sera mis à jour.

### <a name="error"></a>$Error

Contient un tableau d’objets d’erreur qui représentent les erreurs les plus récentes.
L’erreur la plus récente est le premier objet d’erreur dans le tableau `$Error[0]` .

Pour éviter qu’une erreur ne soit ajoutée au `$Error` tableau, utilisez le paramètre commun **ErrorAction** avec la valeur **ignore**. Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).

### <a name="event"></a>$Event

Contient un objet **PSEventArgs** qui représente l’événement en cours de traitement. Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement, telle que `Register-ObjectEvent` . La valeur de cette variable est le même que celui retourné par l’applet de commande `Get-Event` . Par conséquent, vous pouvez utiliser les propriétés de la `Event` variable, telles que `$Event.TimeGenerated` , dans un `Action` bloc de script.

### <a name="eventargs"></a>$EventArgs

Contient un objet qui représente le premier argument d’événement qui dérive de **EventArgs** de l’événement en cours de traitement. Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement.
La valeur de cette variable peut également être trouvée dans la propriété **SourceEventArgs** de l’objet **PSEventArgs** `Get-Event` retourné par.

### <a name="eventsubscriber"></a>$EventSubscriber

Contient un objet **PSEventSubscriber** qui représente l’abonné aux événements de l’événement en cours de traitement. Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement. La valeur de cette variable est le même que celui retourné par l’applet de commande `Get-EventSubscriber` .

### <a name="executioncontext"></a>$ExecutionContext

Contient un objet **EngineIntrinsics** qui représente le contexte d’exécution de l’hôte PowerShell. Vous pouvez utiliser cette variable pour rechercher les objets d’exécution qui sont disponibles pour les applets de commande.

### <a name="false"></a>$false

Contient la **valeur false**. Vous pouvez utiliser cette variable pour représenter la **valeur false** dans les commandes et les scripts au lieu d’utiliser la chaîne « false ». La chaîne peut être interprétée comme **true** si elle est convertie en une chaîne non vide ou en un entier différent de zéro.

### <a name="foreach"></a>$foreach

Contient l’énumérateur (pas les valeurs résultantes) d’une boucle [foreach](about_ForEach.md) . La `$ForEach` variable existe uniquement pendant l' `ForEach` exécution de la boucle ; elle est supprimée une fois la boucle terminée.

Les énumérateurs contiennent des propriétés et des méthodes que vous pouvez utiliser pour récupérer des valeurs de boucle et modifier l’itération de boucle actuelle. Pour plus d’informations, consultez [utilisation d’énumérateurs](#using-enumerators).

### <a name="home"></a>$HOME

Contient le chemin d’accès complet du répertoire de destination de l’utilisateur. Cette variable est l’équivalent des `"$env:homedrive$env:homepath"` variables d’environnement Windows, en général `C:\Users\<UserName>` .

### <a name="host"></a>$Host

Contient un objet qui représente l’application hôte actuelle pour PowerShell. Vous pouvez utiliser cette variable pour représenter l’hôte actuel dans les commandes ou pour afficher ou modifier les propriétés de l’hôte, telles que `$Host.version` ou `$Host.CurrentCulture` , ou `$host.ui.rawui.setbackgroundcolor("Red")` .

### <a name="input"></a>$input

Contient un énumérateur qui énumère toutes les entrées passées à une fonction. La `$input` variable est disponible uniquement pour les fonctions et les blocs de script (qui sont des fonctions sans nom).

- Dans une fonction sans `Begin` bloc, `Process` ou `End` , la `$input` variable énumère la collection de toutes les entrées de la fonction.

- Dans le `Begin` bloc, la `$input` variable ne contient aucune donnée.

- Dans le `Process` bloc, la `$input` variable contient l’objet qui se trouve actuellement dans le pipeline.

- Dans le `End` bloc, la `$input` variable énumère la collection de toutes les entrées de la fonction.

  > [!NOTE]
  > Vous ne pouvez pas utiliser la `$input` variable à la fois dans le bloc de processus et dans le bloc de fin dans la même fonction ou le même bloc de script.

Étant donné que `$input` est un énumérateur, l’accès à l’une de ses propriétés `$input` n’est plus disponible. Vous pouvez stocker `$input` dans une autre variable pour réutiliser les `$input` Propriétés.

Les énumérateurs contiennent des propriétés et des méthodes que vous pouvez utiliser pour récupérer des valeurs de boucle et modifier l’itération de boucle actuelle. Pour plus d’informations, consultez [utilisation d’énumérateurs](#using-enumerators).

La `$input` variable est également disponible pour la commande spécifiée par le `-Command` paramètre de `pwsh` lorsqu’elle est appelée à partir de la ligne de commande. L’exemple suivant est exécuté à partir de l’interface de commande Windows.

```CMD
echo Hello | pwsh -Command """$input World!"""
```

### <a name="iscoreclr"></a>$IsCoreCLR

Contient `$True` si la session active est en cours d’exécution sur le Runtime .net Core (CoreCLR). Sinon, contient `$False` .

### <a name="islinux"></a>$IsLinux

Contient `$True` si la session active est exécutée sur un système d’exploitation Linux.
Sinon, contient `$False` .

### <a name="ismacos"></a>$IsMacOS

Contient `$True` si la session active est exécutée sur un système d’exploitation MacOS.
Sinon, contient `$False` .

### <a name="iswindows"></a>$IsWindows

Contient `$TRUE` si la session active est exécutée sur un système d’exploitation Windows. Sinon, contient `$FALSE` .

### <a name="lastexitcode"></a>$LastExitCode

Contient le code de sortie du dernier programme Windows exécuté.

### <a name="matches"></a>$Matches

La `Matches` variable fonctionne avec les `-match` `-notmatch` opérateurs et.
Lorsque vous envoyez une entrée scalaire à l' `-match` opérateur or et que l’une d’elles `-notmatch` détecte une correspondance, elle retourne une valeur booléenne et remplit la `$Matches` variable automatique avec une table de hachage de toutes les valeurs de chaîne qui ont été mises en correspondance. La `$Matches` table de hachage peut également être remplie avec des captures lorsque vous utilisez des expressions régulières avec l' `-match` opérateur.

Pour plus d’informations sur l' `-match` opérateur, consultez [about_Comparison_Operators](about_comparison_operators.md). Pour plus d’informations sur les expressions régulières, consultez [about_regular_expressions](about_Regular_Expressions.md).

### <a name="myinvocation"></a>$MyInvocation

Contient des informations sur la commande actuelle, telles que le nom, les paramètres, les valeurs de paramètre et les informations sur la façon dont la commande a été démarrée, appelée ou appelée, comme le nom du script qui a appelé la commande actuelle.

`$MyInvocation` est renseigné uniquement pour les scripts, les fonctions et les blocs de script. Vous pouvez utiliser les informations de l’objet **System. Management. Automation. InvocationInfo** qui `$MyInvocation` retourne dans le script actuel, comme le chemin d’accès et le nom de fichier du script ( `$MyInvocation.MyCommand.Path` ) ou le nom d’une fonction ( `$MyInvocation.MyCommand.Name` ) pour identifier la commande actuelle. Cela s’avère particulièrement utile pour rechercher le nom du script actuel.

À compter de PowerShell 3,0, `MyInvocation` possède les nouvelles propriétés suivantes.

| Propriété      | Description                                         |
| ------------- | --------------------------------------------------- |
| **PSScriptRoot**  | Contient le chemin d’accès complet au script qui a appelé   |
|               | commande actuelle. La valeur de cette propriété est  |
|               | renseigné uniquement lorsque l’appelant est un script.         |
| **PSCommandPath** | Contient le chemin d’accès complet et le nom de fichier du script  |
|               | qui a appelé la commande actuelle. Valeur de ce |
|               | la propriété est remplie uniquement lorsque l’appelant est un     |
|               | « Hello world! ».                                             |

Contrairement aux `$PSScriptRoot` `$PSCommandPath` variables automatiques et, les propriétés **PSScriptRoot** et **PSCommandPath** de la `$MyInvocation` variable automatique contiennent des informations sur le demandeur ou le script appelant, et non sur le script en cours.

### <a name="nestedpromptlevel"></a>$NestedPromptLevel

Contient le niveau d’invite actuel. La valeur 0 indique le niveau d’invite d’origine. La valeur est incrémentée lorsque vous entrez un niveau imbriqué et décrémenté lorsque vous la quittez.

Par exemple, PowerShell présente une invite de commandes imbriquée lorsque vous utilisez la `$Host.EnterNestedPrompt` méthode. PowerShell présente également une invite de commandes imbriquée lorsque vous atteignez un point d’arrêt dans le débogueur PowerShell.

Lorsque vous entrez une invite imbriquée, PowerShell suspend la commande active, enregistre le contexte d’exécution et incrémente la valeur de la `$NestedPromptLevel` variable. Pour créer des invites de commandes imbriquées supplémentaires (jusqu’à 128 niveaux) ou pour revenir à l’invite de commandes d’origine, exécutez la commande ou tapez `exit` .

La `$NestedPromptLevel` variable vous aide à suivre le niveau d’invite. Vous pouvez créer une autre invite de commandes PowerShell incluant cette valeur afin qu’elle soit toujours visible.

### <a name="null"></a>$null

`$null` variable automatique qui contient une valeur **null** ou vide. Vous pouvez utiliser cette variable pour représenter une valeur absente ou non définie dans les commandes et les scripts.

PowerShell traite `$null` comme un objet avec une valeur, autrement dit comme un espace réservé explicite, afin que vous puissiez utiliser `$null` pour représenter une valeur vide dans une série de valeurs.

Par exemple, lorsque `$null` est inclus dans une collection, il est compté comme l’un des objets.

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

Si vous dirigez la `$null` variable vers l’applet de commande `ForEach-Object` , elle génère une valeur pour `$null` , comme c’est le cas pour les autres objets

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

Par conséquent, vous ne pouvez pas utiliser `$null` pour signifier qu' **aucune valeur de paramètre n'** est utilisée. Une valeur de paramètre de `$null` remplace la valeur de paramètre par défaut.

Toutefois, étant donné que PowerShell traite la `$null` variable comme un espace réservé, vous pouvez l’utiliser dans des scripts comme celui qui suit, ce qui ne fonctionnerait `$null` pas si a été ignoré.

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a>$PID

Contient l’identificateur de processus (PID) du processus qui héberge la session PowerShell active.

### <a name="profile"></a>$PROFILE

Contient le chemin d’accès complet du profil PowerShell pour l’utilisateur actuel et l’application hôte actuelle. Vous pouvez utiliser cette variable pour représenter le profil dans les commandes. Par exemple, vous pouvez l’utiliser dans une commande pour déterminer si un profil a été créé :

```powershell
Test-Path $PROFILE
```

Ou vous pouvez l’utiliser dans une commande pour créer un profil :

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

Vous pouvez l’utiliser dans une commande pour ouvrir le profil dans **notepad.exe**:

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a>$PSBoundParameters

Contient un dictionnaire des paramètres qui sont passés à un script ou une fonction et leurs valeurs actuelles. Cette variable a une valeur uniquement dans une portée où les paramètres sont déclarés, comme un script ou une fonction. Vous pouvez l’utiliser pour afficher ou modifier les valeurs actuelles des paramètres ou pour passer des valeurs de paramètres à un autre script ou à une autre fonction.

Dans cet exemple, la fonction **Test2** passe `$PSBoundParameters` à la fonction **Test1** . Les `$PSBoundParameters` sont affichés dans le format de la **clé** et de la **valeur**.

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a>$PSCmdlet

Contient un objet qui représente l’applet de commande ou la fonction avancée en cours d’exécution.

Vous pouvez utiliser les propriétés et les méthodes de l’objet dans votre applet de commande ou code de fonction pour répondre aux conditions d’utilisation. Par exemple, la propriété **ParameterSetName** contient le nom du jeu de paramètres en cours d’utilisation, et la méthode **ShouldProcess** ajoute les paramètres **WhatIf** et **Confirm** à l’applet de commande de manière dynamique.

Pour plus d’informations sur la `$PSCmdlet` variable automatique, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) et [about_Functions_Advanced](about_Functions_Advanced.md).

### <a name="pscommandpath"></a>$PSCommandPath

Contient le chemin d’accès complet et le nom de fichier du script en cours d’exécution. Cette variable est valide dans tous les scripts.

### <a name="psculture"></a>$PSCulture

À compter de PowerShell 7, `$PSCulture` reflète la culture de l’instance d’exécution PowerShell actuelle (session). Si la culture est modifiée dans une instance d’exécution PowerShell, la `$PSCulture` valeur de cette instance d’exécution est mise à jour.

La culture détermine le format d’affichage des éléments, tels que les nombres, les devises et les dates, et est stocké dans un objet **System. Globalization. CultureInfo** . Utilisez `Get-Culture` pour afficher la culture de l’ordinateur. `$PSCulture` contient la valeur de la propriété **Name** .

### <a name="psdebugcontext"></a>$PSDebugContext

Lors du débogage, cette variable contient des informations sur l’environnement de débogage. Dans le cas contraire, elle contient une valeur **null** . Par conséquent, vous pouvez l’utiliser pour indiquer si le débogueur contrôle. Lorsqu’il est rempli, il contient un objet **PSDebugContext** qui a des **points d’arrêt** et des propriétés **InvocationInfo** . La propriété **InvocationInfo** possède plusieurs propriétés utiles, notamment la propriété **location** . La propriété **location** indique le chemin d’accès du script en cours de débogage.

### <a name="pshome"></a>$PSHOME

Contient le chemin d’accès complet du répertoire d’installation de PowerShell, en général, `$env:windir\System32\PowerShell\v1.0` dans les systèmes Windows. Vous pouvez utiliser cette variable dans les chemins d’accès des fichiers PowerShell. Par exemple, la commande suivante recherche dans les rubriques d’aide conceptuelle le mot **variable**:

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a>$PSItem

Comme pour `$_`. Contient l’objet actuel dans l’objet de pipeline. Vous pouvez utiliser cette variable dans les commandes qui exécutent une action sur chaque objet ou sur les objets sélectionnés dans un pipeline.

### <a name="psscriptroot"></a>$PSScriptRoot

Contient le répertoire à partir duquel un script est en cours d’exécution.

Dans PowerShell 2,0, cette variable est valide uniquement dans les modules de script ( `.psm1` ).
À compter de PowerShell 3,0, il est valide dans tous les scripts.

### <a name="pssenderinfo"></a>$PSSenderInfo

Contient des informations sur l’utilisateur qui a démarré la session PSSession, y compris l’identité de l’utilisateur et le fuseau horaire de l’ordinateur d’origine. Cette variable est disponible uniquement dans sessions PSSession.

La `$PSSenderInfo` variable inclut une propriété configurable par l’utilisateur, **ApplicationArguments**, qui, par défaut, contient uniquement le `$PSVersionTable` de la session d’origine. Pour ajouter des données à la propriété **ApplicationArguments** , utilisez le paramètre **ApplicationArguments** de l’applet de commande `New-PSSessionOption` .

### <a name="psuiculture"></a>$PSUICulture

Contient le nom de la culture de l’interface utilisateur qui est actuellement utilisée dans le système d’exploitation. La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages. Il s’agit de la valeur de la propriété **System.Globalization.CultureInfo.CurrentUICulture.Name** du système. Pour obtenir l’objet **System. Globalization. CultureInfo** du système, utilisez l' `Get-UICulture` applet de commande.

### <a name="psversiontable"></a>$PSVersionTable

Contient une table de hachage en lecture seule qui affiche des détails sur la version de PowerShell en cours d’exécution dans la session active. Le tableau comprend les éléments suivants :

| Propriété                  | Description                                   |
| ------------------------- | --------------------------------------------- |
| **PSVersion**             | Numéro de version de PowerShell                 |
| **PSEdition**             | Cette propriété a la valeur « Desktop » pour  |
|                           | PowerShell 4 et versions antérieures, ainsi que PowerShell  |
|                           | 5,1 sur les éditions Windows complètes.        |
|                           | Cette propriété a la valeur « Core » pour     |
|                           | PowerShell 6 et versions ultérieures, ainsi que PowerShell  |
|                           | PowerShell 5,1 sur les éditions à encombrement réduit  |
|                           | comme Windows nano Server ou Windows IoT.      |
| **GitCommitId**           | ID de validation des fichiers sources, dans GitHub, |
| **SE**                    | Description du système d’exploitation qui      |
|                           | PowerShell est en cours d’exécution sur.                     |
| **Plateforme**              | Plateforme exécutée par le système d’exploitation |
|                           | Activé. La valeur sur Linux et macOS est **UNIX**. |
|                           | Localisez `$IsMacOs` et `$IsLinux`.                |
| **PSCompatibleVersions**  | Versions de PowerShell compatibles    |
|                           | avec la version actuelle                      |
| **PSRemotingProtocolVersion** | Version de PowerShell à distance      |
|                           | Protocole de gestion.                          |
| **SerializationVersion**  | Version de la méthode de sérialisation       |
| **WSManStackVersion**     | Numéro de version de la pile de WS-Management |

### <a name="pwd"></a>$PWD

Contient un objet de chemin d’accès qui représente le chemin d’accès complet du répertoire actif.

### <a name="sender"></a>$Sender

Contient l’objet qui a généré cet événement. Cette variable est remplie uniquement dans le bloc d’action d’une commande d’inscription d’événement. La valeur de cette variable peut également se trouver dans la propriété sender de l’objet **PSEventArgs** qui `Get-Event` retourne.

### <a name="shellid"></a>$ShellId

Contient l’identificateur de l’interpréteur de commandes actuel.

### <a name="stacktrace"></a>$StackTrace

Contient une trace de la pile de l’erreur la plus récente.

### <a name="switch"></a>$switch

Contient l’énumérateur qui ne correspond pas aux valeurs résultantes d’une `Switch` instruction. La `$switch` variable existe uniquement lorsque l' `Switch` instruction est en cours d’exécution ; elle est supprimée à la fin de l’exécution de l' `switch` instruction. Pour plus d’informations, consultez [about_Switch](about_Switch.md).

Les énumérateurs contiennent des propriétés et des méthodes que vous pouvez utiliser pour récupérer des valeurs de boucle et modifier l’itération de boucle actuelle. Pour plus d’informations, consultez [utilisation d’énumérateurs](#using-enumerators).

### <a name="this"></a>$this

Dans un bloc de script qui définit une propriété de script ou une méthode de script, la `$this` variable fait référence à l’objet qui est étendu.

Dans une classe personnalisée, la `$this` variable fait référence à l’objet de classe lui-même autorisant l’accès aux propriétés et méthodes définies dans la classe.

### <a name="true"></a>$true

Contient la **valeur true**. Vous pouvez utiliser cette variable pour représenter la **valeur true** dans les commandes et les scripts.

## <a name="using-enumerators"></a>Utilisation d’énumérateurs

Les `$input` `$foreach` variables, et `$switch` sont tous des énumérateurs utilisés pour itérer au sein des valeurs traitées par leur bloc de code conteneur.

Un énumérateur contient des propriétés et des méthodes que vous pouvez utiliser pour avancer ou réinitialiser une itération, ou pour récupérer des valeurs d’itération. La manipulation directe d’énumérateurs n’est pas considérée comme meilleure pratique.

- Dans les boucles, les mots clés de contrôle de workflow [break](about_Break.md) et [continue](about_Continue.md) doivent être préférés.
- Dans les fonctions qui acceptent l’entrée de pipeline, il est recommandé d’utiliser des paramètres avec les attributs **ValueFromPipeline** ou **ValueFromPipelineByPropertyName** .

  Pour plus d’informations, consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

### <a name="movenext"></a>MoveNext

La méthode [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) avance l’énumérateur à l’élément suivant de la collection. **MoveNext** retourne **true** si l’énumérateur a été avancé avec succès, **false** si l’énumérateur a dépassé la fin de la collection.

> [!NOTE]
> La valeur **booléenne** retournée par mon **MoveNext** est envoyée au flux de sortie.
> Vous pouvez supprimer la sortie en la cast ou en la `[void]` canalisant vers [out-NULL](xref:Microsoft.PowerShell.Core.Out-Null).
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a>Réinitialiser

La méthode [Reset](/dotnet/api/system.collections.ienumerator.reset) affecte à l’énumérateur sa position initiale, qui **précède** le premier élément de la collection.

### <a name="current"></a>Actuel

La propriété [actuelle](/dotnet/api/system.collections.ienumerator.current) obtient l’élément dans la collection, ou le pipeline, à la position actuelle de l’énumérateur.

La propriété **actuelle** continue à retourner la même propriété jusqu’à ce que **MoveNext** soit appelé.

## <a name="examples"></a>Exemples

### <a name="example-1-using-the-input-variable"></a>Exemple 1 : utilisation de la variable $input

Dans l’exemple suivant, l’accès à la `$input` variable efface la variable jusqu’à la prochaine exécution du bloc de processus. L’utilisation de la méthode **Reset** réinitialise la `$input` variable à la valeur de pipeline actuelle.

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

Le bloc de processus avance automatiquement la `$input` variable même si vous n’y accédez pas.

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a>Exemple 2 : utilisation de $input en dehors du bloc Process

En dehors du bloc de processus `$input` , la variable représente toutes les valeurs redirigées dans la fonction.

- L’accès à la `$input` variable efface toutes les valeurs.
- La méthode **Reset** réinitialise l’ensemble de la collection.
- La propriété **actuelle** n’est jamais remplie.
- La méthode **MoveNext** retourne la valeur false, car la collection ne peut pas être avancée.
  - L’appel de **MoveNext** efface la `$input` variable.

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a>Exemple 3 : utilisation de l' $input. Propriété actuelle

À l’aide de la propriété **Current** , la valeur de pipeline actuelle est accessible plusieurs fois sans utiliser la méthode **Reset** . Le bloc Process n’appelle pas automatiquement la méthode **MoveNext** .

La propriété **actuelle** ne sera jamais remplie, sauf si vous appelez explicitement **MoveNext**. La propriété **actuelle** est accessible plusieurs fois dans le bloc de processus sans effacer sa valeur.

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a>Exemple 4 : utilisation de la variable $foreach

Contrairement `$input` à la variable, la `$foreach` variable représente toujours tous les éléments de la collection lorsque vous y accédez directement. Utilisez la propriété **Current** pour accéder à l’élément de collection actuel, et les méthodes **Reset** et **MoveNext** pour modifier sa valeur.

> [!NOTE]
> Chaque itération de la `foreach` boucle appellera automatiquement la méthode **MoveNext** .

La boucle suivante s’exécute deux fois seulement. Dans la deuxième itération, la collection est déplacée vers le troisième élément avant la fin de l’itération. Après la deuxième itération, il n’y a plus aucune valeur à itérer, et la boucle se termine.

La propriété **MoveNext** n’affecte pas la variable choisie pour itérer au sein de la collection ( `$Num` ).

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

L’utilisation de la méthode **Reset** réinitialise l’élément actuel dans la collection. L’exemple suivant effectue une boucle à deux **reprises** sur les deux premiers éléments, car la méthode de **réinitialisation** est appelée. Après les deux premières boucles, l' `if` instruction échoue et la boucle itère les trois éléments normalement.

> [!IMPORTANT]
> Cela peut entraîner une boucle infinie.

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a>Exemple 5 : utilisation de la variable $switch

La `$switch` variable a exactement les mêmes règles que la `$foreach` variable.
L’exemple suivant illustre tous les concepts de l’énumérateur.

> [!NOTE]
> Notez que le cas **NotEvaluated** n’est jamais exécuté, même s’il n’y a pas d' `break` instruction après la méthode **MoveNext** .

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a>Voir aussi

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)
