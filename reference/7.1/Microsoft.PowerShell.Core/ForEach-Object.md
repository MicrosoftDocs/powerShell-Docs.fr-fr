---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 1b1824db5c5c20698d551a6277890ce6c82c4e11
ms.sourcegitcommit: fb9bafd041e3615b9dc9fb77c9245581b705cd02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725185"
---
# ForEach-Object

## Synopsis
Effectue une opération sur chaque élément d'une collection d'objets d'entrée.

## Syntaxe

### ScriptBlockSet (par défaut)

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ParallelParameterSet

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `ForEach-Object` applet de commande effectue une opération sur chaque élément d’une collection d’objets d’entrée. Les objets d’entrée peuvent être dirigés vers l’applet de commande ou spécifiés à l’aide du paramètre **InputObject** .

À compter de Windows PowerShell 3,0, il existe deux façons de construire une `ForEach-Object` commande.

- **Bloc de script**. Vous pouvez utiliser un bloc de script pour spécifier l'opération. Dans le bloc de script, utilisez la `$_` variable pour représenter l’objet actuel. Le bloc de script est la valeur du paramètre **Process**. Le bloc de script peut contenir n’importe quel script PowerShell.

  Par exemple, la commande suivante obtient la valeur de la propriété **ProcessName** de chaque processus sur l'ordinateur.

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` prend en charge les `begin` `process` blocs, et `end` comme décrit dans [about_Functions](about/about_functions.md#piping-objects-to-functions).

  > [!NOTE]
  > Les blocs de script s’exécutent dans la portée de l’appelant. Par conséquent, les blocs ont accès aux variables dans cette portée et peuvent créer de nouvelles variables qui persistent dans cette portée une fois l’applet de commande terminée.

- **Instruction Operation**. Vous pouvez également écrire une instruction d’opération, qui est bien plus similaire à un langage naturel. Vous pouvez utiliser l'instruction d'opération pour spécifier une valeur de propriété ou appeler une méthode. Les instructions d'opération ont été introduites dans Windows PowerShell 3.0.

  Par exemple, la commande suivante obtient également la valeur de la propriété **ProcessName** de chaque processus sur l'ordinateur.

  `Get-Process | ForEach-Object ProcessName`

- **Bloc de script en cours d’exécution parallèle**. À partir de PowerShell 7,0, un troisième jeu de paramètres est disponible qui exécute chaque bloc de script en parallèle. Le paramètre **ThrottleLimit** limite le nombre de scripts parallèles en cours d’exécution à la fois. Comme précédemment, utilisez la `$_` variable pour représenter l’objet d’entrée actuel dans le bloc de script. Utilisez le `$using:` mot clé pour passer des références de variable au script en cours d’exécution.

  Dans PowerShell 7, une nouvelle instance d’exécution est créée pour chaque itération de boucle afin de garantir un isolement maximal.
  Il peut s’agir d’un impact important sur les performances et les ressources si le travail que vous effectuez est faible par rapport à la création de nouveaux instances d’exécution ou si un grand nombre d’itérations effectuent un travail important. À partir de PowerShell 7,1, instances d’exécution à partir d’un pool d’instances d’exécution sont réutilisés par défaut. La taille du pool d’instances d’exécution est spécifiée par le paramètre **ThrottleLimit** . La taille du pool d’instances d’exécution par défaut est 5. Vous pouvez toujours créer une nouvelle instance d’exécution pour chaque itération à l’aide du commutateur **UseNewRunspace**

  Par défaut, le scriptblocks parallèle utilise le répertoire de travail actuel de l’appelant qui a démarré les tâches parallèles.

  Les erreurs sans fin d’exécution sont écrites dans le flux d’erreur de l’applet de commande à mesure qu’elles se produisent en parallèle, scriptblocks. Étant donné que l’ordre d’exécution d’un scriptblock parallèle ne peut pas être déterminé, l’ordre dans lequel les erreurs apparaissent dans le flux d’erreur est aléatoire. De même, les messages écrits dans d’autres flux de données, tels que les avertissements, les commentaires ou les informations, sont écrits dans les flux de données dans un ordre indéterminé.

  L’arrêt des erreurs, telles que les exceptions, met fin à l’instance parallèle individuelle du scriptblocks dans lequel elles se produisent. Une erreur d’arrêt dans un scriptblocks peut ne pas entraîner l’arrêt de l’applet de commande `Foreach-Object` . L’autre scriptblocks, s’exécutant en parallèle, continue à s’exécuter, sauf s’il rencontre également une erreur de fin d’exécution. L’erreur de fin est écrite dans le flux de données d’erreur en tant que **ErrorRecord** avec un **FullyQualifiedErrorId** de `PSTaskException` .
  Les erreurs de fin peuvent être converties en erreurs sans fin d’arrêt à l’aide de blocs try/catch ou Trap PowerShell.

## Exemples

### Exemple 1 : diviser des entiers dans un tableau

Cet exemple prend un tableau de trois entiers et divise chacun d’eux par 1024.

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### Exemple 2 : obtenir la longueur de tous les fichiers d’un répertoire

Cet exemple traite les fichiers et les répertoires dans le répertoire d’installation de PowerShell `$PSHOME` .

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

Si l’objet n’est pas un répertoire, le bloc de script obtient le nom du fichier, divise la valeur de sa propriété **Length** par 1024 et ajoute un espace ("") pour le séparer de l’entrée suivante. L’applet de commande utilise la propriété **PSISContainer** pour déterminer si un objet est un répertoire.

### Exemple 3 : utiliser les événements système les plus récents

Cet exemple écrit les événements les plus récents 1000 du journal des événements système dans un fichier texte. L’heure actuelle est affichée avant et après le traitement des événements.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` Obtient les 1000 événements les plus récents du journal des événements système et les stocke dans la `$Events` variable. `$Events` est ensuite redirigé vers l’applet de commande `ForEach-Object` . Le paramètre **Begin** affiche la date et l'heure actuelles. Ensuite, le paramètre **Process** utilise l' `Out-File` applet de commande pour créer un fichier texte nommé events.txt et stocke la propriété message de chacun des événements dans ce fichier. Enfin, le paramètre **End** est utilisé pour afficher la date et l'heure une fois l'ensemble du traitement terminé.

### Exemple 4 : modifier la valeur d’une clé de Registre

Cet exemple modifie la valeur de l’entrée de Registre **remotePath** dans toutes les sous-clés sous la `HKCU:\Network` clé en texte en majuscules.

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

Vous pouvez utiliser ce format pour modifier la forme ou le contenu d'une valeur d'entrée de Registre.

Chaque sous-clé de la clé **réseau** représente un lecteur réseau mappé qui se reconnecte au moment de l’authentification. L'entrée **RemotePath** contient le chemin d'accès UNC du lecteur connecté. Par exemple, si vous mappez le lecteur E : à `\\Server\Share` , une sous-clé **e** est créée dans `HKCU:\Network` avec la valeur de Registre **remotePath** définie sur `\\Server\Share` .

La commande utilise l' `Get-ItemProperty` applet de commande pour récupérer toutes les sous-clés de la clé **réseau** et l’applet de commande `Set-ItemProperty` pour modifier la valeur de l’entrée de Registre **remotePath** dans chaque clé.
Dans la `Set-ItemProperty` commande, le chemin d’accès est la valeur de la propriété **PSPath** de la clé de registre. Il s’agit d’une propriété de l’objet Microsoft .NET Framework qui représente la clé de Registre, et non une entrée de registre. La commande utilise la méthode **ToUpper ()** de la valeur **remotePath** , qui est une chaîne (REG_SZ).

Étant donné que `Set-ItemProperty` modifie la propriété de chaque clé, l’applet de commande `ForEach-Object` est nécessaire pour accéder à la propriété.

### Exemple 5 : utiliser la variable automatique $Null

Cet exemple montre l’effet de la fonction de canalisation de la `$Null` variable automatique à l’applet de commande `ForEach-Object` .

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

Étant donné que PowerShell traite NULL comme un espace réservé explicite, l’applet de commande `ForEach-Object` génère une valeur pour `$Null` , comme c’est le cas pour les autres objets que vous dirigez vers celui-ci.

### Exemple 6 : récupérer des valeurs de propriété

Cet exemple obtient la valeur de la propriété **path** de tous les modules PowerShell installés à l’aide du paramètre **MemberName** de l’applet de commande `ForEach-Object` .

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

La deuxième commande est équivalente à la première. Elle utilise l' `Foreach` alias de l' `ForEach-Object` applet de commande et omet le nom du paramètre **MemberName** , qui est facultatif.

L' `ForEach-Object` applet de commande est utile pour obtenir les valeurs de propriété, car elle obtient la valeur sans modifier le type, contrairement aux applets de commande **format** ou à l’applet de commande `Select-Object` , qui modifient le type de valeur de propriété.

### Exemple 7 : fractionner les noms de modules en noms de composants

Cet exemple illustre trois façons de fractionner deux noms de module séparés par des points en leurs noms de composants.

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

Elles appellent la méthode **Split** de chaînes. Les trois commandes utilisent une syntaxe différente, mais elles sont équivalentes et interchangeables.

La première commande utilise la syntaxe traditionnelle, qui comprend un bloc de script et l’opérateur d’objet en cours `$_` . Elle utilise la syntaxe à point pour spécifier la méthode et des parenthèses pour encadrer l'argument délimiteur.

La deuxième commande utilise le paramètre **MemberName** pour spécifier la méthode **Split** et le paramètre **ArgumentName** pour identifier le point (« . ») comme délimiteur de fractionnement.

La troisième commande utilise l’alias **foreach** de l' `ForEach-Object` applet de commande et omet les noms des paramètres **MemberName** et **argumentlist** , qui sont facultatifs.

### Exemple 8 : utilisation de ForEach-Object avec deux blocs de script

Dans cet exemple, nous passons deux blocs de script positionnels. Tous les blocs de script sont liés au paramètre **Process** . Toutefois, elles sont traitées comme si elles avaient été passées aux paramètres **Begin** et **Process** .

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### Exemple 9 : utilisation de ForEach-Object avec plus de deux blocs de script

Dans cet exemple, nous passons deux blocs de script positionnels. Tous les blocs de script sont liés au paramètre **Process** . Toutefois, elles sont traitées comme si elles avaient été passées aux paramètres **Begin**, **Process** et **end** .

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> Le premier bloc de script est toujours mappé au `begin` bloc, le dernier bloc est mappé au `end` bloc et les blocs entre sont tous mappés au `process` bloc.

### Exemple 10 : exécuter plusieurs blocs de script pour chaque élément de pipeline

Comme indiqué dans l’exemple précédent, plusieurs blocs de script passés à l’aide du paramètre **Process** sont mappés aux paramètres **Begin** et **end** . Pour éviter ce mappage, vous devez fournir des valeurs explicites pour les paramètres de **début** et de **fin** .

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### Exemple 11 : exécuter un script lent dans des lots parallèles

Cet exemple exécute un bloc de script simple qui évalue une chaîne et se met en veille pendant une seconde.

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

La valeur du paramètre **ThrottleLimit** est définie sur 4 afin que l’entrée soit traitée par lots de quatre.
Le `$using:` mot clé est utilisé pour transmettre la `$Message` variable dans chaque bloc de script parallèle.

### Exemple 12 : récupérer des entrées de journal en parallèle

Cet exemple récupère les entrées de journal 50 000 de 5 journaux système sur un ordinateur Windows local.

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

Le paramètre **Parallèle** spécifie le bloc de script exécuté en parallèle pour chaque nom du journal d’entrée. Le paramètre **ThrottleLimit** garantit que les cinq blocs de script s’exécutent en même temps.

### Exemple 13 : exécuter en parallèle en tant que tâche

Cet exemple exécute un bloc de script simple en parallèle, créant deux tâches en arrière-plan à la fois.

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

la `$job` variable reçoit l’objet de traitement qui collecte les données de sortie et surveille l’état d’exécution.
L’objet de traitement est dirigé vers `Receive-Job` avec le paramètre de commutateur **Wait** . Et cela diffuse la sortie vers la console, tout comme si `ForEach-Object -Parallel` a été exécuté sans **AsJob**.

### Exemple 14 : utilisation de références de variable thread-safe

Cet exemple appelle des blocs de script en parallèle pour collecter des objets de processus portant un nom unique.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

Une seule instance d’un objet **ConcurrentDictionary** est passée à chaque bloc de script pour collecter les objets. Étant donné que le **ConcurrentDictionary** est thread-safe, il peut être modifié en toute sécurité par chaque script parallèle. Un objet non thread-safe, tel que **System. Collections. Generic. dictionary**, ne peut pas être utilisé en toute sécurité ici.

> [!NOTE]
> Cet exemple est une utilisation très inefficace du paramètre **Parallel** . Le script ajoute simplement l’objet d’entrée à un objet de dictionnaire simultané. Il est trivial et ne justifie pas la surcharge liée à l’appel de chaque script dans un thread séparé. `ForEach-Object`L’exécution normale sans le commutateur **parallèle** est beaucoup plus efficace et plus rapide. Cet exemple est uniquement destiné à illustrer l’utilisation de variables thread-safe.

### Exemple 15 : écriture d’erreurs avec exécution parallèle

Cet exemple écrit dans le flux d’erreur en parallèle, où l’ordre des erreurs écrites est aléatoire.

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### Exemple 16 : fin des erreurs d’exécution en parallèle

Cet exemple illustre une erreur de fin dans un scriptblock en cours d’exécution parallèle.

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

`Output: 3` n’est jamais écrit, car le scriptblock parallèle de cette itération a été arrêté.

## Paramètres

### -ArgumentList

Spécifie un tableau d’arguments pour un appel de méthode. Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Début

Spécifie un bloc de script qui s’exécute avant que cette applet de commande traite tous les objets d’entrée. Ce bloc de script n’est exécuté qu’une seule fois pour l’ensemble du pipeline. Pour plus d’informations sur le `begin` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fin

Spécifie un bloc de script qui s’exécute après que cette applet de commande a traité tous les objets d’entrée. Ce bloc de script n’est exécuté qu’une seule fois pour l’ensemble du pipeline. Pour plus d’informations sur le `end` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets d'entrée. `ForEach-Object` exécute le bloc de script ou l’instruction d’opération sur chaque objet d’entrée. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

Quand vous utilisez le paramètre **InputObject** avec `ForEach-Object` , au lieu de rediriger les résultats de la commande vers `ForEach-Object` , la valeur **InputObject** est traitée comme un objet unique. Cela est vrai même si la valeur est une collection qui est le résultat d’une commande, telle que `-InputObject (Get-Process)` .
Étant donné que **InputObject** ne peut pas retourner des propriétés individuelles d’un tableau ou d’une collection d’objets, il est recommandé, si vous utilisez, `ForEach-Object` d’effectuer des opérations sur une collection d’objets pour les objets qui ont des valeurs spécifiques dans les propriétés définies, `ForEach-Object` comme indiqué dans les exemples de cette rubrique.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberName

Spécifie la propriété à obtenir ou la méthode à appeler.

Les caractères génériques sont autorisés, mais ne fonctionnent que si la chaîne résultante correspond à une valeur unique.
Par exemple, si vous exécutez `Get-Process | ForEach -MemberName *Name` , le modèle de caractère générique correspond à plusieurs membres, ce qui provoque l’échec de la commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Processus

Spécifie l'opération qui est effectuée sur chaque objet d'entrée. Ce bloc de script est exécuté pour chaque objet dans le pipeline. Pour plus d’informations sur le `process` bloc, consultez [about_Functions](about/about_functions.md#piping-objects-to-functions).

Lorsque vous fournissez plusieurs blocs de script au paramètre **Process** , le premier bloc de script est toujours mappé au `begin` bloc. S’il n’y a que deux blocs de script, le deuxième bloc est mappé au `process` bloc. S’il existe trois blocs de script ou plus, le premier bloc de script est toujours mappé au `begin` bloc, le dernier bloc est mappé au `end` bloc et les blocs entre sont tous mappés au `process` bloc.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

Spécifie tous les blocs de script qui ne sont pas pris par le paramètre **Process** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parallel

Spécifie le bloc de script à utiliser pour le traitement parallèle des objets d’entrée. Entrez un bloc de script décrivant l'opération.

Ce paramètre a été introduit dans PowerShell 7,0.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre de blocs de script en parallèle. Les objets d’entrée sont bloqués jusqu’à ce que le nombre de blocs de script en cours se situe en dessous du **ThrottleLimit**. La valeur par défaut est `5`.

Ce paramètre a été introduit dans PowerShell 7,0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

Spécifie le nombre de secondes à attendre que toutes les entrées soient traitées en parallèle. Après le délai d’expiration spécifié, tous les scripts en cours d’exécution sont arrêtés. Et tous les objets d’entrée restants à traiter sont ignorés. La valeur par défaut de `0` désactive le délai d’expiration et `ForEach-Object -Parallel` peut s’exécuter indéfiniment. La frappe de la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> à la ligne de commande arrête une commande en cours d’exécution `ForEach-Object -Parallel` . Ce paramètre ne peut pas être utilisé avec le paramètre **AsJob** .

Ce paramètre a été introduit dans PowerShell 7,0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewRunspace

Fait en sorte que l’appel parallèle crée une nouvelle instance d’exécution pour chaque itération de boucle au lieu de réutiliser instances d’exécution à partir du pool d’instances d’exécution.

Ce paramètre a été introduit dans PowerShell 7,1

```yml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

Provoque l’exécution de l’appel parallèle en tant que tâche PowerShell. Un objet de traitement unique est retourné à la place de la sortie des blocs de script en cours d’exécution. L’objet de traitement contient des tâches enfants pour chaque bloc de script parallèle qui s’exécute. L’objet de traitement peut être utilisé par toutes les applets de commande PowerShell Job pour surveiller l’État en cours d’exécution et récupérer des données.

Ce paramètre a été introduit dans PowerShell 7,0.

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Entrées

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers cette applet de commande.

## Sorties

### System. Management. Automation. PSObject

Cette applet de commande retourne les objets qui sont déterminés par l’entrée.

## Remarques

- L' `ForEach-Object` applet de commande fonctionne très bien comme l’instruction **foreach** , sauf que vous ne pouvez pas diriger d’entrée vers une instruction **foreach** . Pour plus d’informations sur l’instruction **foreach** , consultez [about_Foreach](./About/about_Foreach.md).

- À partir de PowerShell 4,0, `Where` les `ForEach` méthodes et ont été ajoutées pour être utilisées avec les collections. Vous pouvez en savoir plus sur ces nouvelles méthodes ici [about_Arrays](./About/about_Arrays.md)

- Le `ForEach-Object -Parallel` jeu de paramètres utilise l’API interne de PowerShell pour exécuter chaque bloc de script. Il s’agit d’une surcharge beaucoup plus lourde que l’exécution `ForEach-Object` normale avec un traitement séquentiel. Il est important d’utiliser **Parallel** lorsque la surcharge de l’exécution en parallèle est faible par rapport au travail effectué par le bloc de script. Par exemple :

  - Scripts de calcul intensif sur les ordinateurs multicœurs
  - Scripts qui consacrent du temps à attendre des résultats ou à exécuter des opérations sur les fichiers

  L’utilisation du paramètre **Parallel** peut entraîner une exécution beaucoup plus lente des scripts que la normale. Surtout si les scripts parallèles sont simples. Expérimentez en **parallèle** pour découvrir où il peut être bénéfique.

  > [!IMPORTANT]
  > Le `ForEach-Object -Parallel` jeu de paramètres exécute des blocs de script en parallèle sur des threads de processus distincts. Le `$using:` mot clé permet de passer des références de variable du thread d’appel d’applet de commande à chaque thread de bloc de script en cours d’exécution. Étant donné que les blocs de script s’exécutent dans des threads différents, les variables d’objet passées par référence doivent être utilisées en toute sécurité. En général, il est possible de lire en toute sécurité des objets référencés qui ne changent pas. Toutefois, si l’état de l’objet est modifié, vous devez utiliser des objets thread-safe, tels que les types .NET **System. collection. concurrent** (Voir l’exemple 11).

## Liens connexes

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-Object](Where-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)
