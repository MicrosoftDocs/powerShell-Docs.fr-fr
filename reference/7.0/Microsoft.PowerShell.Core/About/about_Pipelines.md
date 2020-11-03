---
description: Combinaison de commandes dans des pipelines dans PowerShell
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: bf5e57389d286a2bb1cca9b3dd73ea59674461ec
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207837"
---
# <a name="about-pipelines"></a>À propos des pipelines

## <a name="short-description"></a>Description courte

Combinaison de commandes dans des pipelines dans PowerShell

## <a name="long-description"></a>Description longue

Un pipeline est une série de commandes connectées par des opérateurs de pipeline ( `|` ) (ASCII 124). Chaque opérateur de pipeline envoie les résultats de la commande précédente à la commande suivante.

La sortie de la première commande peut être envoyée pour traitement comme entrée à la deuxième commande. Et cette sortie peut être envoyée à une autre commande. Le résultat est une chaîne de commande complexe ou un _pipeline_ qui est composé d’une série de commandes simples.

Par exemple,

```powershell
Command-1 | Command-2 | Command-3
```

Dans cet exemple, les objets qui `Command-1` émettent sont envoyés à `Command-2` .
`Command-2` traite les objets et les envoie à `Command-3` . `Command-3` traite les objets et les envoie dans le pipeline. Étant donné qu’il n’y a plus de commandes dans le pipeline, les résultats s’affichent dans la console.

Dans un pipeline, les commandes sont traitées dans l’ordre de gauche à droite. Le traitement est géré comme une opération unique et la sortie est affichée au fur et à mesure de sa génération.

Voici un exemple simple. La commande suivante obtient le processus du bloc-notes, puis l’arrête.

Par exemple,

```powershell
Get-Process notepad | Stop-Process
```

La première commande utilise l' `Get-Process` applet de commande pour récupérer un objet représentant le processus du bloc-notes. Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet processus à l’applet de commande `Stop-Process` , qui arrête le processus Notepad. Notez que la `Stop-Process` commande n’a pas de paramètre **Name** ou **ID** pour spécifier le processus, car le processus spécifié est soumis via le pipeline.

Cet exemple de pipeline obtient les fichiers texte dans le répertoire actif, sélectionne uniquement les fichiers dont la longueur est supérieure à 10 000 octets, les trie par longueur et affiche le nom et la longueur de chaque fichier dans une table.

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

Ce pipeline se compose de quatre commandes dans l’ordre spécifié. L’illustration suivante montre la sortie de chaque commande telle qu’elle est transmise à la commande suivante dans le pipeline.

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a>Utilisation des pipelines

La plupart des applets de commande PowerShell sont conçues pour prendre en charge les pipelines. Dans la plupart des cas, vous pouvez _diriger_ les résultats d’une applet de commande **obtenir** vers une autre applet de commande du même nom.
Par exemple, vous pouvez diriger la sortie de l' `Get-Service` applet de commande vers les `Start-Service` applets de commande ou `Stop-Service` .

Cet exemple de pipeline démarre le service WMI sur l’ordinateur :

```powershell
Get-Service wmi | Start-Service
```

Pour un autre exemple, vous pouvez diriger la sortie de `Get-Item` ou `Get-ChildItem` dans le fournisseur de Registre PowerShell vers l’applet de commande `New-ItemProperty` . Cet exemple ajoute une nouvelle entrée de Registre, **NoOfEmployees** , avec une valeur de **8124** , à la clé de Registre **MyCompany** .

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

La plupart des applets de commande utilitaires, telles que,,, `Get-Member` `Where-Object` `Sort-Object` `Group-Object` et `Measure-Object` sont utilisées presque exclusivement dans des pipelines. Vous pouvez diriger tout type d’objet vers ces applets de commande. Cet exemple montre comment trier tous les processus sur l’ordinateur en fonction du nombre de descripteurs ouverts dans chaque processus.

```powershell
Get-Process | Sort-Object -Property handles
```

Vous pouvez diriger les objets vers les applets de commande de mise en forme, d’exportation et de sortie, telles que,,, `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` et `Out-File` .

Cet exemple montre comment utiliser l' `Format-List` applet de commande pour afficher la liste des propriétés d’un objet processus.

```powershell
Get-Process winlogon | Format-List -Property *
```

Avec un peu de pratique, vous constaterez que la combinaison de commandes simples dans des pipelines permet d’économiser du temps et de la saisie, et d’améliorer l’efficacité de vos scripts.

## <a name="how-pipelines-work"></a>Fonctionnement des pipelines

Cette section explique comment les objets d’entrée sont liés aux paramètres d’applet de commande et traités lors de l’exécution du pipeline.

### <a name="accepts-pipeline-input"></a>Accepte l’entrée de pipeline

Pour prendre en charge le traitement en pipeline, l’applet de commande de réception doit avoir un paramètre qui accepte l’entrée de pipeline. Utilisez la `Get-Help` commande avec les options **Full** ou **Parameter** pour déterminer les paramètres d’une applet de commande acceptant l’entrée de pipeline.

Par exemple, pour déterminer les paramètres de l’applet de commande qui `Start-Service` accepte l’entrée de pipeline, tapez :

```powershell
Get-Help Start-Service -Full
```

ou

```powershell
Get-Help Start-Service -Parameter *
```

L’aide de l' `Start-Service` applet de commande montre que seuls les paramètres **InputObject** et **Name** acceptent l’entrée de pipeline.

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

Lorsque vous envoyez des objets via le pipeline à `Start-Service` , PowerShell tente d’associer les objets aux paramètres **InputObject** et **Name** .

### <a name="methods-of-accepting-pipeline-input"></a>Méthodes d’acceptation de l’entrée de pipeline

Les paramètres des applets de commande peuvent accepter l’entrée de pipeline de deux façons différentes :

- **ByValue** : le paramètre accepte les valeurs qui correspondent au type .net attendu ou qui peuvent être converties en ce type.

  Par exemple, le paramètre **Name** de `Start-Service` accepte les entrées de pipeline par valeur. Il peut accepter des objets de chaîne ou des objets qui peuvent être convertis en chaînes.

- **ByPropertyName** : le paramètre accepte l’entrée uniquement lorsque l’objet d’entrée a une propriété du même nom que le paramètre.

  Par exemple, le paramètre Name de `Start-Service` peut accepter des objets qui ont une propriété **Name** . Pour répertorier les propriétés d’un objet, dirigez-le vers `Get-Member` .

Certains paramètres peuvent accepter des objets par nom de valeur ou de propriété, ce qui facilite l’entrée du pipeline.

### <a name="parameter-binding"></a>Liaison de paramètres

Lorsque vous dirigez des objets d’une commande vers une autre commande, PowerShell tente d’associer les objets dirigés à un paramètre de l’applet de commande de réception.

Le composant de liaison de paramètre de PowerShell associe les objets d’entrée aux paramètres d’applet de commande en fonction des critères suivants :

- Le paramètre doit accepter l’entrée d’un pipeline.
- Le paramètre doit accepter le type d’objet envoyé ou un type qui peut être converti vers le type attendu.
- Le paramètre n’a pas été utilisé dans la commande.

Par exemple, l' `Start-Service` applet de commande a plusieurs paramètres, mais seuls deux d’entre eux, **Name** et **InputObject** acceptent l’entrée de pipeline. Le paramètre **Name** prend des chaînes et le paramètre **InputObject** prend des objets de service. Par conséquent, vous pouvez diriger des chaînes, des objets de service et des objets avec des propriétés qui peuvent être converties en objets de service ou de chaîne.

PowerShell gère la liaison de paramètre aussi efficacement que possible. Vous ne pouvez pas suggérer ou forcer PowerShell à établir une liaison avec un paramètre spécifique. La commande échoue si PowerShell ne peut pas lier les objets redirigés.

Pour plus d’informations sur le dépannage des erreurs de liaison, consultez [examen des erreurs de pipeline](#investigating-pipeline-errors) plus loin dans cet article.

### <a name="one-at-a-time-processing"></a>Traitement une fois par heure

La redirection d’objets vers une commande est très similaire à l’utilisation d’un paramètre de la commande pour envoyer les objets. Examinons un exemple de pipeline. Dans cet exemple, nous utilisons un pipeline pour afficher une table d’objets de service.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

Fonctionnellement, cela revient à utiliser le paramètre **InputObject** de `Format-Table` pour envoyer la collection d’objets.

Par exemple, nous pouvons enregistrer la collection de services dans une variable qui est passée à l’aide du paramètre **InputObject** .

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

Ou nous pouvons incorporer la commande dans le paramètre **InputObject** .

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

Toutefois, il existe une différence importante. Lorsque vous dirigez plusieurs objets vers une commande, PowerShell les envoie un par un à la commande. Lorsque vous utilisez un paramètre de commande, les objets sont envoyés sous la forme d’un objet de tableau unique. Cette différence mineure a des conséquences significatives.

Lors de l’exécution d’un pipeline, PowerShell énumère automatiquement tout type qui implémente l' `IEnumerable` interface et envoie un à un les membres via le pipeline. L’exception est `[hashtable]` , qui requiert un appel à la `GetEnumerator()` méthode.

Dans les exemples suivants, un tableau et une table de hachage sont dirigés vers l' `Measure-Object` applet de commande pour compter le nombre d’objets reçus à partir du pipeline. Le tableau a plusieurs membres, et la table de hachage a plusieurs paires clé-valeur. Seul le tableau est énuméré un à la fois.

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

De même, si vous dirigez plusieurs objets de processus de l' `Get-Process` applet de commande vers l’applet de commande `Get-Member` , PowerShell envoie chaque objet de processus, un à la fois, à `Get-Member` . `Get-Member` affiche la classe .NET (type) des objets processus, ainsi que leurs propriétés et méthodes.

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> `Get-Member` élimine les doublons. par conséquent, si les objets sont tous du même type, il n’affiche qu’un seul type d’objet.

Toutefois, si vous utilisez le paramètre **InputObject** de `Get-Member` , `Get-Member` reçoit un tableau d’objets **System. Diagnostics. Process** comme une seule unité. Elle affiche les propriétés d’un tableau d’objets. (Notez le symbole de tableau ( `[]` ) après le nom du type **System. Object** .)

Par exemple,

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

Ce résultat n’est peut-être pas ce que vous souhaitiez. Mais une fois que vous l’avez compris, vous pouvez l’utiliser. Par exemple, tous les objets tableau ont une propriété **Count** . Vous pouvez l’utiliser pour compter le nombre de processus en cours d’exécution sur l’ordinateur.

Par exemple,

```powershell
(Get-Process).count
```

Il est important de se souvenir que les objets envoyés dans le pipeline sont remis un à la fois.

## <a name="investigating-pipeline-errors"></a>Examen des erreurs de pipeline

Lorsque PowerShell ne peut pas associer les objets dirigés à un paramètre de l’applet de commande de réception, la commande échoue.

Dans l’exemple suivant, nous essayons de déplacer une entrée de registre d’une clé de Registre vers une autre. L' `Get-Item` applet de commande obtient le chemin d’accès de destination, qui est ensuite redirigé vers l’applet de commande `Move-ItemProperty` . La `Move-ItemProperty` commande spécifie le chemin d’accès actuel et le nom de l’entrée de Registre à déplacer.

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

La commande échoue et PowerShell affiche le message d’erreur suivant :

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

Pour examiner, utilisez l' `Trace-Command` applet de commande pour suivre le composant de liaison de paramètre de PowerShell. L’exemple suivant effectue le suivi de la liaison de paramètre pendant l’exécution du pipeline. Le paramètre **PSHost** affiche les résultats de la trace dans la console et le paramètre **filePath** envoie les résultats de la trace au `debug.txt` fichier pour référence ultérieure.

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

Les résultats de la trace sont longs, mais ils affichent les valeurs qui sont liées à l’applet de commande, `Get-Item` puis les valeurs nommées qui sont liées à l’applet de commande `Move-ItemProperty` .

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

Enfin, il indique que la tentative de liaison du chemin d’accès au paramètre de **destination** de `Move-ItemProperty` a échoué.

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

Utilisez l' `Get-Help` applet de commande pour afficher les attributs du paramètre de **destination** .

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

Les résultats montrent que la **destination** prend uniquement l’entrée de pipeline « par nom de propriété ». Par conséquent, l’objet dirigé doit avoir une propriété nommée **destination** .

Utilisez `Get-Member` pour afficher les propriétés de l’objet provenant de `Get-Item` .

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

La sortie indique que l’élément est un objet **Microsoft. Win32. RegistryKey** qui n’a pas de propriété de **destination** . Cela explique pourquoi la commande a échoué.

Le paramètre **path** accepte l’entrée de pipeline par nom ou par valeur.

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

Pour corriger la commande, nous devons spécifier la destination dans l' `Move-ItemProperty` applet de commande et utiliser `Get-Item` pour obtenir le **chemin d’accès** de l’élément que vous souhaitez déplacer.

Par exemple,

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a>Continuation de ligne intrinsèque

Comme nous l’avons déjà vu, un pipeline est une série de commandes connectées par des opérateurs de pipeline ( `|` ), généralement écrits sur une seule ligne. Toutefois, pour des raisons de lisibilité, PowerShell vous permet de fractionner le pipeline sur plusieurs lignes.
Lorsqu’un opérateur de canal est le dernier jeton de la ligne, l’analyseur PowerShell joint la ligne suivante à la commande actuelle pour poursuivre la construction du pipeline.

Par exemple, le pipeline à ligne unique suivant :

```powershell
Command-1 | Command-2 | Command-3
```

peut être écrite comme suit :

```powershell
Command-1 |
  Command-2 |
    Command-3
```

Les espaces de début sur les lignes suivantes ne sont pas significatifs. La mise en retrait améliore la lisibilité.

PowerShell 7 ajoute la prise en charge de la continuation des pipelines avec le caractère de pipeline au début d’une ligne. Les exemples suivants montrent comment utiliser cette nouvelle fonctionnalité.

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> Lorsque vous travaillez de manière interactive dans l’interpréteur de commandes, collez le code avec des pipelines au début d’une ligne uniquement lorsque vous utilisez <kbd>CTRL</kbd> + <kbd>V</kbd> pour coller.
> Cliquez avec le bouton droit sur collage opérations insérer les lignes une par une. Étant donné que la ligne ne se termine pas par un caractère de pipeline, PowerShell considère que l’entrée est terminée et exécute cette ligne telle qu’elle a été entrée.

## <a name="see-also"></a>Voir aussi

[about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

[about_Objects](about_objects.md)

[about_Parameters](about_parameters.md)

[about_Command_Syntax](about_command_syntax.md)

[about_ForEach](about_foreach.md)
