---
title: Système d’aide
description: La maîtrise du système d’aide est la clé d’une utilisation optimale de PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 43d2de7e1f59ce5e980c192decb5309d3f6d0ff8
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438110"
---
# <a name="chapter-2---the-help-system"></a>Chapitre 2 – Le système d’aide

Deux groupes de professionnels de l’informatique ont été soumis à une épreuve écrite sans ordinateur pour déterminer leur niveau de compétence PowerShell. Les utilisateurs novices de PowerShell ont été placés dans un groupe et les experts dans un autre.
Au vu des résultats de l’épreuve, le niveau de compétence entre les deux groupes ne semblait pas très différent. Une deuxième épreuve comparable à la première a été soumise aux deux groupes. Cette fois, un ordinateur leur a été fourni avec PowerShell, mais sans accès à Internet. Les résultats de la deuxième épreuve ont révélé une grande différence dans le niveau de compétence entre les deux groupes. Les experts ne connaissaient pas toujours les réponses, mais ils savaient comment les trouver.

Quelle a été la différence dans les résultats des première et deuxième épreuves entre ces deux groupes ?

Les différences observées dans ces deux épreuves ne s’expliquent pas par le fait que les experts savent comment utiliser les milliers de commandes qui existent dans PowerShell. Ils apprennent à utiliser parfaitement le système d’aide de PowerShell.
Ils peuvent ainsi trouver les commandes nécessaires quand ils en ont besoin et savoir comment les utiliser une fois qu’ils les ont trouvées.

J’ai souvent entendu Jeffrey Snover, l’inventeur de PowerShell, dire des choses similaires.

La maîtrise du système d’aide est la clé d’une utilisation optimale de PowerShell.

## <a name="discoverability"></a>Détectabilité

Les commandes compilées dans PowerShell s’appellent des applets de commande. Leur abréviation en anglais est « cmdlet », qui se prononce « command-let » (et non CMD-let). Le nom des applets de commande se présente sous la forme « Verbe-Nom » pour en faciliter la recherche. Par exemple, l’applet de commande permettant d’identifier les processus en cours d’exécution est `Get-Process` et l’applet de commande destinée à récupérer la liste des services et leur état est `Get-Service`. Il existe d’autres types de commandes dans PowerShell comme les alias et les fonctions qui seront abordées plus loin dans ce livre. Le terme « commande PowerShell » est un terme générique qui est souvent employé pour désigner n’importe quel type de commande dans PowerShell, qu’il s’agisse d’une applet de commande, d’une fonction ou d’un alias.

## <a name="the-three-core-cmdlets-in-powershell"></a>Les trois principales applets de commande dans PowerShell

- `Get-Command`
- `Get-Help`
- `Get-Member` (décrite dans le chapitre 3)

On me pose souvent la question suivante : comment savoir à quoi servent les différentes commandes dans PowerShell ? `Get-Command` et `Get-Help` permettent toutes deux d’identifier les commandes.

## <a name="get-help"></a>Get-Help

`Get-Help` est une commande polyvalente. `Get-Help` vous indique comment utiliser les commandes une fois que vous les avez trouvées. `Get-Help` permet aussi de localiser les commandes, mais pas de la même manière qu’avec `Get-Command` et pas de façon aussi directe.

Quand la commande `Get-Help` est utilisée pour localiser des commandes, l’entrée fournie est d’abord comparée aux noms de commandes. Si l’opération ne donne rien, la recherche porte alors sur les rubriques d’aide proprement dites. Si aucune correspondance n’est trouvée, une erreur est retournée. Contrairement à l’idée reçue, `Get-Help` peut servir à rechercher des commandes pour lesquelles il n’existe pas de rubriques d’aide.

La première chose à savoir concernant le système d’aide de PowerShell, c’est la façon d’utiliser l’applet de commande `Get-Help`. La commande suivante sert à afficher la rubrique d’aide pour `Get-Help`.

```powershell
Get-Help -Name Get-Help
```

```Outpout
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Depuis PowerShell version 3, l’aide de PowerShell n’est pas intégrée au système d’exploitation. La première fois que `Get-Help` est exécutée pour une commande, le message précédent s’affiche. Si la fonction `help` ou l’alias `man` est utilisé à la place de l’applet de commande `Get-Help`, vous n’obtenez pas cette invite.

Si vous répondez par Oui en appuyant sur <kbd>Y</kbd>, l’applet de commande `Update-Help` s’exécute, ce qui nécessite un accès à Internet par défaut. `Y` peut être spécifié en majuscules ou en minuscules.

Une fois que l’aide est téléchargée et la mise à jour terminée, la rubrique d’aide est retournée pour la commande spécifiée :

```powershell
Get-Help -Name Get-Help
```

Prenez le temps d’exécuter cet exemple sur votre ordinateur, d’examiner la sortie et d’observer la façon dont les informations sont regroupées :

- NOM
- RÉSUMÉ
- SYNTAXE
- DESCRIPTION
- LIENS CONNEXES
- REMARQUES

Comme vous pouvez le constater, les rubriques d’aide peuvent contenir une masse d’informations, encore que vous ne voyez là qu’une partie de la rubrique d’aide.

Bien que cela ne soit pas propre à PowerShell, un paramètre offre un moyen de fournir une entrée à une commande. `Get-Help` compte de nombreux paramètres qui, lorsqu’ils sont spécifiés, permettent de retourner l’intégralité de la rubrique d’aide ou une partie de celle-ci.

La section syntaxe de la rubrique d’aide présentée dans le jeu de résultats précédent liste tous les paramètres de `Get-Help`. À première vue, il semble que les mêmes paramètres sont listés à six différentes reprises. Chacun de ces différents blocs de la section syntaxe est un jeu de paramètres. Cela signifie que l’applet de commande `Get-Help` compte six jeux de paramètres différents. À y regarder de plus près, vous remarquerez que chaque jeu de paramètres contient un paramètre différent.

Les jeux de paramètres s’excluent mutuellement. Dès lors qu’un paramètre unique qui n’existe que dans un seul des jeux de paramètres est utilisé, seuls les paramètres contenus dans ce jeu de paramètres peuvent être utilisés. Par exemple, il n’est pas possible de spécifier les paramètres **Full** et **Detailed** en même temps, car ils se trouvent dans des jeux de paramètres différents.

Chacun des paramètres suivants se trouve dans des jeux de paramètres différents :

- Full
- Detailed
- Examples
- Online
- Parameter
- ShowWindow

Toute la syntaxe énigmatique comme les crochets et les accolades figurant dans la section syntaxe a une signification, mais ce point sera abordé dans l’Annexe A de ce livre. Bien qu’il soit important d’apprendre ce à quoi correspond cette syntaxe énigmatique, il est souvent difficile de s’en rappeler pour une personne qui débute sur PowerShell et qui ne l’utilise pas forcément tous les jours.

Pour plus d’informations sur la syntaxe énigmatique, consultez l’[Annexe A][].

Pour les débutants, il existe un moyen plus simple d’obtenir les mêmes informations, mais dans un langage compréhensible.

Quand le paramètre **Full** de `Get-Help` est spécifié, la rubrique d’aide entière est retournée.

```powershell
Get-Help -Name Get-Help -Full
```

Prenez le temps d’exécuter cet exemple sur votre ordinateur, d’examiner la sortie et d’observer la façon dont les informations sont regroupées :

- NOM
- RÉSUMÉ
- SYNTAXE
- DESCRIPTION
- PARAMÈTRES
- ENTRÉES
- SORTIES
- REMARQUES
- EXEMPLES
- LIENS CONNEXES

Notez que l’utilisation du paramètre **Full** a retourné plusieurs sections supplémentaires, dont celle intitulée PARAMÈTRES qui fournit davantage d’informations que la section SYNTAXE énigmatique.

Le paramètre **Full** est un paramètre booléen. Un paramètre booléen est un paramètre qui ne nécessite pas de valeur. Quand un paramètre de ce type est spécifié, sa valeur est true. Quand il ne l’est pas, sa valeur est false.

Si vous avez parcouru ce chapitre dans la console PowerShell, vous avez remarqué que la commande précédente qui permet d’afficher l’intégralité de la rubrique d’aide pour `Get-Help` est passée à toute vitesse sur l’écran sans même vous laisser le temps de la lire. Il existe une meilleure solution.

`Help` est une fonction qui canalise `Get-Help` vers une fonction nommée `more`, qui est un wrapper pour le fichier exécutable `more.com` dans Windows. Dans la console PowerShell, `help` fournit une page d’aide à la fois. Dans l’environnement ISE, elle fonctionne de la même façon que `Get-Help`. Ma recommandation est d’utiliser la fonction `help` à la place de l’applet de commande `Get-Help`, car elle offre une meilleure expérience et nécessite moins de saisie.

Cependant, saisir moins n’est pas toujours un avantage. Si vous envisagez d’enregistrer vos commandes sous forme de script ou de les partager avec d’autres utilisateurs, veillez à utiliser des noms complets d’applets de commande et de paramètres. Les noms complets sont explicites et plus faciles à comprendre. Pensez à la prochaine personne qui va devoir lire et comprendre vos commandes. Ce sera peut-être vous. Vos collègues et vous-même vous en féliciterez.

Essayez d’exécuter les commandes suivantes dans la console PowerShell de l’ordinateur de votre environnement lab Windows 10.

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

Après les avoir exécutées sur l’ordinateur de votre environnement lab Windows 10, avez-vous remarqué des différences par rapport à la sortie des commandes listées précédemment ?

Il n’y a pas de différences hormis le fait que les deux dernières options retournent les résultats une page à la fois.
Quand la fonction `Help` est utilisée, la <kbd>barre d’espace</kbd> permet d’afficher la page de contenu suivante, et <kbd>Ctrl</kbd>+<kbd>C</kbd> annule les commandes qui s’exécutent dans la console PowerShell.

Le premier exemple fait appel à l’applet de commande `Get-Help`, le deuxième utilise la fonction `Help` et le troisième omet le paramètre **Name** quand la fonction `Help` est utilisée. **Name** est un paramètre positionnel qui est utilisé de façon positionnelle dans cet exemple. Cela signifie que la valeur peut être spécifiée sans indiquer le nom du paramètre, du moment que la valeur proprement dite est spécifiée au bon endroit. Comment savoir à quel endroit spécifier la valeur ? En lisant l’aide qui est illustrée dans l’exemple suivant.

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

Notez que dans l’exemple précédent, le paramètre **Parameter** a été utilisé avec la fonction Help pour retourner uniquement les informations de la rubrique d’aide se rapportant au paramètre **Name**. C’est bien plus simple que d’essayer de passer au crible une rubrique d’aide d’une centaine de pages.

Sur la base de ces résultats, vous pouvez voir que le paramètre **Name** est positionnel et qu’il doit être spécifié à la position zéro (première position) quand il est utilisé de façon positionnelle. L’ordre dans lequel les paramètres sont spécifiés n’a pas d’importance si le nom du paramètre est spécifié.

Un autre point important à noter est que le paramètre **Name** attend une valeur sous la forme d’une chaîne unique, ce qui est indiqué par `<String>`. S’il acceptait plusieurs chaînes, le type de données indiqué serait `<String[]>`.

Parfois, il n’est pas utile d’afficher l’intégralité de la rubrique d’aide d’une commande. Avec `Get-Help` ou `Help`, il est possible de spécifier plusieurs autres paramètres, en plus de **Full**. Essayez d’exécuter les commandes suivantes sur l’ordinateur de votre environnement lab Windows 10 :

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

En général, j’utilise `help <command name>` avec le paramètre **Full** ou **Online**. Si je suis intéressé uniquement par les exemples, j’utilise le paramètre **Examples** ; si je suis intéressé uniquement par un paramètre spécifique, j’utilise le paramètre **Parameter**. Le paramètre **ShowWindow** ouvre la rubrique d’aide dans une fenêtre de recherche distincte qui peut être affichée sur un autre écran, le cas échéant. J’ai évité le paramètre **ShowWindow**, car un bogue connu l’empêche d’afficher l’intégralité de la rubrique d’aide.

Si vous souhaitez afficher l’aide dans une fenêtre distincte, il est préférable d’utiliser le paramètre **Online** ou **Full** et de canaliser les résultats vers `Out-GridView`, comme dans l’exemple suivant.

```powershell
help Get-Command -Full | Out-GridView
```

L’applet de commande `Out-GridView` et le paramètre **ShowWindow** de l’applet de commande `Get-Help` nécessitent un système d’exploitation doté d’une interface graphique utilisateur (GUI). Si vous tentez de les utiliser sur un système Windows Server installé avec l’option d’installation Server Core (sans interface graphique), ils généreront un message d’erreur.

Pour rechercher des commandes à l’aide de `Get-Help`, utilisez le caractère générique `*` (astérisque) avec le paramètre **Name**. Spécifiez la valeur du paramètre **Name** avec le terme que vous recherchez dans les noms de commandes, comme l’illustre l’exemple suivant.

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

Dans l’exemple précédent, les caractères génériques `*` ne sont pas obligatoires et vous obtenez les mêmes résultats si vous les omettez. `Get-Help` ajoute automatiquement les caractères génériques en arrière-plan.

```powershell
help process
```

La commande précédente produit les mêmes résultats que si le caractère générique `*` est spécifié de part et d’autre de « process ».

Je préfère les ajouter, car c’est l’option qui fonctionne toujours et avec constance. En revanche, ils sont nécessaires dans certains scénarios, mais pas dans d’autres. Dès lors que vous ajoutez un caractère générique au milieu de la valeur, ils ne sont plus ajoutés automatiquement en arrière-plan à la valeur que vous spécifiez.

```powershell
help pr*cess
```

Aucune valeur n’est retournée par cette commande, à moins que le caractère générique `*` soit ajouté au début, à la fin ou de part et d’autre de `pr*cess`.

Si la valeur que vous avez spécifiée commence par un tiret, une erreur est générée, car PowerShell l’interprète comme un nom de paramètre. Or, il n’existe pas de nom de paramètre pour l’applet de commande `Get-Help`.

```powershell
help -process
```

Si vous essayez de rechercher des commandes qui se terminent par `-process`, il vous suffit d’ajouter le caractère générique `*` au début de la valeur.

```powershell
help *-process
```

Quand il s’agit de rechercher des commandes PowerShell avec `Get-Help`, soyez un peu plus vague dans vos recherches et moins précis.

Dans la recherche précédente qui portait sur le terme `process`, seules les commandes dont le nom contenait `process` ont été trouvées et aucun autre résultat n’a été retourné. Avec `Get-Help`, le terme de recherche `processes` ne correspond à aucun nom de commande. De ce fait, la recherche porte sur chaque rubrique d’aide PowerShell de votre système et retourne toutes les correspondances trouvées. Le nombre de résultats retournés est alors immense.

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

La recherche avec `Help` a retourné 10 résultats pour le terme `process` et 68 résultats pour le terme `processes`. Si un seul résultat est trouvé, la rubrique d’aide proprement dite s’affiche à la place de la liste de commandes.

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

Maintenant, nous allons tordre le cou à une fausse idée selon laquelle `Help` dans PowerShell peut trouver uniquement les commandes associées à des rubriques d’aide.

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

À noter que dans l’exemple précédent, il n’existe pas de rubrique d’aide pour `more` alors que ce terme a été trouvé par le système `Help` dans PowerShell. Il a trouvé une seule correspondance et a retourné les informations de syntaxe de base qui s’affichent quand une commande n’a pas de rubrique d’aide.

PowerShell contient de nombreuses rubriques d’aide conceptuelles (À propos de). La commande suivante permet de retourner la liste de toutes les rubriques d’aide **À propos de** présentes sur votre système.

```powershell
help About_*
```

En limitant les résultats à une seule rubrique d’aide À propos de, ce n’est pas la liste qui est retournée mais bien la rubrique d’aide qui s’affiche.

```powershell
help about_Updatable_Help
```

Le système d’aide de PowerShell doit être mis à jour pour que les rubriques d’aide **À propos de** soient présentes. Si, pour une raison ou une autre, la mise à jour initiale du système d’aide échoue sur votre ordinateur, les fichiers ne sont pas disponibles tant que l’applet de commande `Update-Help` n’est pas exécutée avec succès.

## <a name="get-command"></a>Get-Command

`Get-Command` vise à vous aider à localiser les commandes. L’exécution de `Get-Command` sans aucun paramètre retourne la liste de toutes les commandes de votre système. L’exemple suivant vous montre comment l’applet de commande `Get-Command` est utilisée pour identifier les commandes existantes qui fonctionnent avec des processus :

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

Notez que dans l’exemple précédent où `Get-Command` est exécuté, le paramètre **Noun** est utilisé et `Process` est spécifié comme valeur du paramètre **Noun**. Et si vous n’aviez pas su utiliser l’applet de commande `Get-Command` ? Vous auriez pu utiliser `Get-Help` pour afficher la rubrique d’aide pour `Get-Command`.

Les paramètres **Name**, **Noun** et **Verb** acceptent les caractères génériques. Dans l’exemple suivant, des caractères génériques sont utilisés avec le paramètre **Name** :

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

Je ne suis pas très favorable à l’utilisation de caractères génériques avec le paramètre **Name** de `Get-Command`, car celui-ci retourne aussi les fichiers exécutables qui ne sont pas des commandes PowerShell natives.

Si vous envisagez d’utiliser des caractères génériques avec le paramètre **Name**, je vous recommande de limiter les résultats avec le paramètre **CommandType**.

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

Une meilleure option consiste à utiliser le paramètre **Verb** ou **Noun** ou les deux à la fois, car seules les commandes PowerShell comportent à la fois un verbe et un nom.

Vous avez trouvé des erreurs dans une rubrique d’aide ? La bonne nouvelle c’est que les rubriques d’aide de PowerShell sont désormais en open source et disponibles dans le dépôt [PowerShell-Docs][] sur GitHub. Apportez votre contribution en corrigeant les informations incorrectes non seulement pour vous-même, mais aussi pour tous les autres utilisateurs. Il vous suffit de dupliquer (fork) le dépôt de documentation PowerShell sur GitHub, de mettre à jour la rubrique d’aide, puis d’envoyer une demande de tirage (pull request).
Une fois la demande de tirage acceptée, la documentation corrigée est mise à la disposition de tous.

## <a name="updating-help"></a>Mise à jour de l’aide

La copie locale des rubriques d’aide PowerShell a été mise à jour précédemment la première fois que de l’aide sur une commande a été demandée. Il est recommandé de mettre à jour régulièrement le système d’aide, car le contenu de l’aide peut de temps à autre faire l’objet de mises à jour. La mise à jour des rubriques d’aide s’effectue à l’aide de l’applet de commande `Update-Help`.
Elle nécessite par défaut un accès à Internet et vous devez exécuter PowerShell avec une élévation de privilèges en tant qu’administrateur.

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

Des erreurs ont été retournées par deux modules, ce qui n’est pas rare. Si l’ordinateur n’a pas accès à Internet, vous pouvez utiliser l’applet de commande `Save-Help` sur un autre ordinateur connecté à Internet de façon à enregistrer dans un premier temps les informations d’aide mises à jour sur un partage de fichiers de votre réseau. Ensuite, spécifiez cet emplacement réseau pour les rubriques d’aide avec le paramètre **SourcePath** de `Update-Help`.

Envisagez de configurer une tâche planifiée ou d’ajouter une logique à votre script de profil dans PowerShell pour mettre régulièrement à jour le contenu de l’aide sur votre ordinateur. Les scripts de profil seront abordés dans un prochain chapitre.

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez appris à rechercher les commandes avec `Get-Help` et `Get-Command`. Vous avez appris à utiliser le système d’aide pour savoir comment utiliser les commandes une fois que vous les avez trouvées. Vous avez aussi découvert comment mettre à jour le contenu des rubriques d’aide quand des mises à jour sont disponibles.

Je vous lance le défi d’apprendre une commande PowerShell par jour.

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a>Révision

1. Le paramètre **DisplayName** de `Get-Service` est-il positionnel ?
1. Combien de jeux de paramètres compte l’applet de commande `Get-Process` ?
1. Quelles sont les commandes PowerShell qui peuvent fonctionner avec les journaux des événements ?
1. Quelle est la commande PowerShell qui permet de retourner la liste des processus PowerShell qui s’exécutent sur votre ordinateur ?
1. Comment mettre à jour le contenu de l’aide PowerShell qui est stocké sur votre ordinateur ?

## <a name="recommended-reading"></a>Lecture recommandée

Si vous souhaitez en savoir plus sur les sujets abordés dans ce chapitre, je vous conseille de lire les rubriques d’aide PowerShell suivantes.

- [Get-Help][]
- [Get-Command][]
- [Update-Help][]
- [Save-Help][]
- [about_Updatable_Help][]
- [about_Command_Syntax][]

Dans le prochain chapitre, vous découvrirez l’applet de commande `Get-Member` ainsi que des objets, des propriétés et des méthodes.

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[Annexe A]: appendix-a.md
