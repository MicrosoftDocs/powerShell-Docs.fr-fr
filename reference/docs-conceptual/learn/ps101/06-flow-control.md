---
title: Contrôle de flux
description: PowerShell fournit des méthodes pour créer des boucles, prendre des décisions et contrôler logiquement le flux du code dans les scripts.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 74595f8c6a5d4a49b05e72dd6bde1441fd2b464e
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598956"
---
# <a name="chapter-6---flow-control"></a>Chapitre 6 : Contrôle de flux

## <a name="scripting"></a>Création de scripts

Passer des one-liners PowerShell aux scripts est bien plus simple que ça n’en a l’air. Un script n’est rien de plus qu’un ensemble de commandes identiques ou similaires que vous exécutez de manière interactive dans la console PowerShell, sauf que ces commandes sont enregistrées dans un fichier `.PS1`. Vous pouvez utiliser certaines constructions de script, comme une boucle `foreach`, au lieu de l’applet de commande `ForEach-Object`. Pour les débutants, les différences peuvent porter à confusion, en particulier quand `foreach` est à la fois une construction de script et un alias de l’applet de commande `ForEach-Object`.

## <a name="looping"></a>Bouclage

L’un des avantages de PowerShell est que, une fois que vous avez trouvé comment faire pour un élément, il vous suffit presque de répéter la même chose pour des centaines d’autres. Vous n’avez qu’à exécuter un des nombreux types de boucle PowerShell sur les éléments.

### <a name="foreach-object"></a>ForEach-Object

`ForEach-Object` est une applet de commande pour effectuer des itérations au sein d’éléments dans un pipeline, par exemple avec les one-liners PowerShell. `ForEach-Object` envoie en streaming les objets dans le pipeline.

Bien que le paramètre **Module** de `Get-Command` accepte plusieurs valeurs sous forme de chaînes, il les accepte uniquement via une entrée de pipeline par nom de propriété ou via une entrée de paramètre. Dans le scénario suivant, si je veux envoyer deux chaînes par valeur vers `Get-Command` pour les utiliser avec le paramètre **Module**, je dois utiliser l’applet de commande `ForEach-Object`.

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

Dans l’exemple précédent, `$_` est l’objet actuel. À partir de la version 3.0 de PowerShell, `$PSItem` peut être utilisé à la place de `$_`. Mais je trouve que la plupart des utilisateurs expérimentés de PowerShell préfèrent encore utiliser `$_`, car il a une compatibilité descendante et est plus court à taper.

Quand vous utilisez le mot clé `foreach`, vous devez stocker tous les éléments en mémoire pour pouvoir lancer l’itération, ce qui peut être difficile si vous ne savez combien d’éléments vous utilisez.

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

La plupart du temps, une boucle comme `foreach` ou `ForEach-Object` est nécessaire. Sinon, vous recevez un message d’erreur.

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

Dans d’autres cas, vous pouvez obtenir les mêmes résultats tout en éliminant complètement la boucle. Consultez l’applet de commande pour comprendre vos options.

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Comme vous pouvez le voir dans les exemples précédents, le paramètre **Identity** pour `Get-ADComputer` accepte seulement une valeur quand elle est fournie par le biais d’une entrée de paramètre, mais il autorise plusieurs éléments quand l’entrée est fournie via une entrée de pipeline.

### <a name="for"></a>For

Une boucle `for` effectue une itération quand une condition spécifiée a la valeur true. Je n’utilise pas souvent la boucle `for`, mais elle a son utilité.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

Dans l’exemple précédent, la boucle effectue 4 itérations en commençant par le numéro 1 et continue tant que la variable de compteur `$i` est inférieure à 5. Elle se met en veille pendant un total de 10 secondes.

### <a name="do"></a>À faire

Il existe deux boucles `do` différentes dans PowerShell. `Do Until` s’exécute quand la condition spécifiée a la valeur false.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

L’exemple précédent est un jeu de nombres qui continue jusqu’à ce que la valeur que vous devinez soit égale au nombre généré par l’applet de commande `Get-Random`.

`Do While` est juste l’inverse. Elle s’exécute tant que la condition spécifiée a la valeur true.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

Les mêmes résultats sont obtenus avec une boucle `Do While` en inversant la condition de test (différent de).

Les boucles `Do` s’exécutent toujours au moins une fois, car la condition est évaluée à la fin de la boucle.

### <a name="while"></a>While

Tout comme la boucle `Do While`, une boucle `While` s’exécute tant que la condition spécifiée a la valeur true. À la différence que la boucle `While` évalue la condition en haut de la boucle avant l’exécution du code. Elle ne s’exécute donc pas si la condition a la valeur false.

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

L’exemple précédent calcule le jour auquel Thanksgiving a lieu aux États-Unis. C’est toujours le quatrième jeudi de novembre. Par conséquent, la boucle commence par le 22 novembre et ajoute un jour quand le jour de la semaine n’est pas égal à jeudi. Si le 22 est un jeudi, la boucle ne s’exécute pas du tout.

## <a name="break-continue-and-return"></a>Break, Continue et Return

L’instruction `Break` permet de casser une boucle. Elle est également couramment utilisée avec l’instruction `switch`.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

L’instruction `break` présentée dans l’exemple précédent casse la boucle à la première itération.

L’instruction Continue permet de passer à l’itération suivante d’une boucle.

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

L’exemple précédent génère les nombres 1, 2, 4 et 5. Il ignore le numéro 3 et continue avec l’itération suivante de la boucle. Tout comme `break`, `continue` interrompt la boucle, sauf pour l’itération actuelle. L’exécution se poursuit avec l’itération suivante au lieu de casser la boucle et de s’arrêter.

L’instruction Return permet de quitter l’étendue existante.

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

Notez que dans l’exemple précédent, return génère le premier résultat et n’existe plus dans la boucle. Une explication plus complète de l’instruction return est disponible dans l’un de mes articles de blog : [« The PowerShell return keyword »][].

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez découvert les différents types de boucles qui existent dans PowerShell.

## <a name="review"></a>Révision

1. Quelle est la différence entre l’applet de commande `ForEach-Object` et la construction de script ForEach ?
1. Quel est le principal avantage d’une boucle While par rapport à une boucle Do While ou Do Until ?
1. En quoi les instructions break et continue sont-elles différentes ?

## <a name="recommended-reading"></a>Lecture recommandée

- [ForEach-Object][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[« The PowerShell return keyword »]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
