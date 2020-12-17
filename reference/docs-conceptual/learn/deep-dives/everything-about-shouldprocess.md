---
title: Tout ce que vous avez toujours voulu savoir sur ShouldProcess
description: ShouldProcess est une fonctionnalité importante qui est souvent négligée. Les paramètres WhatIf et Confirm facilitent l’ajout à vos fonctions.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 4f11ad84f5c89423fe56cfe438ed3cb1587ce59e
ms.sourcegitcommit: be1df0bf757d734975a9aa021727608a396059ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616044"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>Tout ce que vous avez toujours voulu savoir sur ShouldProcess

Les fonctions PowerShell disposent de plusieurs fonctionnalités qui améliorent de façon considérable la manière dont les utilisateurs interagissent avec ces fonctions.
Une fonctionnalité importante souvent négligée est la prise en charge de `-WhatIf` et `-Confirm`, et il est facile de l’ajouter à vos fonctions. Dans cet article, nous explorons en détail l’implémentation de cette fonctionnalité.

> [!NOTE]
> La [version d’origine][] de cet article est apparue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous. Consultez son blog à l’adresse [PowerShellExplained.com][].

Il s’agit d’une fonctionnalité simple que vous pouvez activer dans vos fonctions pour fournir un filet de sécurité aux utilisateurs qui en ont besoin. Il n’y a rien de plus effrayant que d’exécuter une commande dont vous savez qu’elle peut être dangereuse la première fois. L’option permettant de l’exécuter avec `-WhatIf` peut faire une grande différence.

## <a name="commonparameters"></a>CommonParameters

Avant de nous pencher sur l’implémentation de ces [paramètres communs][], je souhaite examiner rapidement la manière dont ils sont utilisés.

## <a name="using--whatif"></a>Utilisation de -WhatIf

Quand une commande prend en charge le paramètre `-WhatIf`, cela vous permet de voir ce que la commande aurait fait au lieu d’apporter des modifications. C’est un bon moyen de tester l’impact d’une commande, en particulier avant d’exécuter une action destructrice.

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Si la commande implémente correctement `ShouldProcess`, elle doit vous montrer toutes les modifications qu’elle aurait effectué. Voici un exemple d’utilisation d’un caractère générique pour supprimer plusieurs fichiers.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>Utilisation de -Confirm

Les commandes qui prennent en charge `-WhatIf` prennent également en charge `-Confirm`. Cela vous donne la possibilité de confirmer une action avant de l’exécuter.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Dans ce cas, vous avez plusieurs options qui vous permettent de continuer, d’ignorer une modification ou d’arrêter le script. L’invite d’aide décrit chacune de ces options.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>Localisation

Cette invite est localisée dans PowerShell afin que la langue change en fonction de la langue de votre système d’exploitation. C’est une autre chose que PowerShell gère pour vous.

### <a name="switch-parameters"></a>Paramètres de commutateur

Passons rapidement en revue les façons de passer une valeur à un paramètre de commutateur. La raison principale pour laquelle je m’y intéresse est que vous souhaitez souvent passer des valeurs de paramètre à des fonctions que vous appelez.

La première approche est une syntaxe de paramètre spécifique qui peut être utilisée pour tous les paramètres, mais elle est principalement utilisée pour les paramètres de commutateur. Vous spécifiez un signe deux-points pour joindre une valeur au paramètre.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

Vous pouvez faire de même avec une variable.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

La deuxième approche consiste à utiliser une table de hachage pour représenter la valeur sous forme de « splatte ».

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

Si vous débutez avec les tables de hachage ou la projection (splatting), j’ai écrit un autre article qui couvre [tout ce que vous souhaitiez savoir sur les tables de hachage][].

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

La première étape pour activer la prise en charge de `-WhatIf` et `-Confirm` consiste à spécifier `SupportsShouldProcess` dans `CmdletBinding` de votre fonction.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

En spécifiant `SupportsShouldProcess` de cette manière, nous pouvons maintenant appeler notre fonction avec `-WhatIf` (ou `-Confirm`).

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Notez que je n’ai pas créé de paramètre appelé `-WhatIf`. La spécification de `SupportsShouldProcess` le crée automatiquement pour nous. Lorsque nous spécifions le paramètre `-WhatIf` sur `Test-ShouldProcess`, certaines choses que nous appelons effectuent également un traitement `-WhatIf`.

### <a name="trust-but-verify"></a>Faire confiance mais vérifier

Il existe a un danger ici de croire que tout ce que vous appelez hérite des valeurs `-WhatIf`. Pour le reste des exemples, je vais supposer que cela ne fonctionne pas et je vais être très explicite lors de l’appel à d’autres commandes. Je vous recommande d’en faire de même.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIfPreference
}
```

Je reviendrai sur les nuances plus tard une fois que vous aurez une meilleure compréhension de tous les éléments en jeu.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet.ShouldProcess

La méthode qui vous permet d’implémenter `SupportsShouldProcess` est `$PSCmdlet.ShouldProcess`. Vous appelez `$PSCmdlet.ShouldProcess(...)` pour voir si vous devez traiter une certaine logique et que PowerShell s’occupe du reste. Commençons avec un exemple :

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

L’appel à `$PSCmdlet.ShouldProcess($file.name)` vérifie le `-WhatIf` (et le paramètre `-Confirm`), puis le gère en conséquence. Le `-WhatIf` oblige `ShouldProcess` à générer une description de la modification et à retourner `$false` :

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

Un appel à l’aide de `-Confirm` interrompt le script et invite l’utilisateur à continuer. Il retourne `$true` si l’utilisateur a sélectionné `Y`.

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Une fonctionnalité extraordinaire de `$PSCmdlet.ShouldProcess` est qu’elle sert aussi de sortie détaillée. J’utilise souvent cela lors de l’implémentation de `ShouldProcess`.

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>Surcharges

Il existe plusieurs surcharges différentes pour `$PSCmdlet.ShouldProcess` avec des paramètres différents pour la personnalisation des messages. Nous avons déjà vu la première dans l’exemple ci-dessus. Examinons-la de plus près.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

Cela produit une sortie qui comprend à la fois le nom de la fonction et la cible (valeur du paramètre).

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

La spécification d’un deuxième paramètre comme l’opération utilise la valeur de l’opération au lieu du nom de la fonction dans le message.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

L’option suivante consiste à spécifier trois paramètres pour personnaliser entièrement le message. Lorsque trois paramètres sont utilisés, le premier est le message entier. Les deux autres paramètres sont toujours utilisés dans la sortie du message `-Confirm`.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>Référence de paramètre rapide

Au cas où vous liriez ceci uniquement pour savoir quels paramètres utiliser, voici une référence rapide indiquant comment les paramètres modifient le message dans les différents scénarios de `-WhatIf`.

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

J’ai tendance à utiliser le scénario avec deux paramètres.

### <a name="shouldprocessreason"></a>ShouldProcessReason

Il existe une quatrième surcharge qui est plus avancée que les autres. Elle vous permet d’obtenir la raison pour laquelle `ShouldProcess` a été exécuté. Je l’ajoute ici pour des raisons d’exhaustivité, car nous pouvons simplement vérifier si `$WhatIfPreference` est `$true` à la place.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

Nous devons passer la variable `$reason` dans le quatrième paramètre en tant que variable de référence avec `[ref]`. `ShouldProcess` remplit `$reason` avec la valeur `None` ou `WhatIf`. Je n’ai pas dit que cela était utile et je n’ai jamais eu de raison de l’utiliser.

### <a name="where-to-place-it"></a>Où placer l’élément ?

Vous utilisez `ShouldProcess` pour rendre vos scripts plus sûrs. Vous l’utilisez donc lorsque vos scripts effectuent des modifications. J’aime placer l’appel à `$PSCmdlet.ShouldProcess` aussi proche que possible de la modification.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

Si je traite une collection d’éléments, je l’appelle pour chaque élément. L’appel est donc placé à l’intérieur de la boucle foreach.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

La raison pour laquelle je place `ShouldProcess` près de la modification est que je souhaite exécuter autant de code que possible lorsque `-WhatIf` est spécifié. Je souhaite que l’installation et la validation s’exécutent si possible de façon à ce que l’utilisateur soit en mesure de voir ces erreurs.

J’aime également utiliser cela dans mes tests Pester qui valident mes projets. Si j’ai une logique difficile à simuler dans Pester, je peux souvent l’encapsuler dans `ShouldProcess` et l’appeler avec `-WhatIf` dans mes tests. Il vaut mieux tester une partie de votre code plutôt que de ne rien tester du tout.

### <a name="whatifpreference"></a>$WhatIfPreference

La première variable de préférence que nous avons est `$WhatIfPreference`. Elle est `$false` par défaut. Si vous la définissez sur `$true`, votre fonction s’exécute comme si vous aviez spécifié `-WhatIf`. Si vous définissez cela dans votre session, toutes les commandes effectuent l’exécution de `-WhatIf`.

Lorsque vous appelez une fonction avec `-WhatIf`, la valeur de `$WhatIfPreference` est définie sur `$true` à l’intérieur de l’étendue de votre fonction.

## <a name="confirmimpact"></a>ConfirmImpact

La plupart de mes exemples s’appliquent à `-WhatIf` mais tout fonctionne également avec `-Confirm` pour inviter l’utilisateur. Vous pouvez définir le `ConfirmImpact` de la fonction sur la valeur High (Élevé) et cela invite l’utilisateur comme s’il était appelé avec `-Confirm`.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Cet appel à `Test-ShouldProcess` effectue l’action `-Confirm` en raison de l’impact `High`.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

Le problème évident est que cela est désormais plus difficile à utiliser dans d’autres scripts sans inviter l’utilisateur. Dans ce cas, nous pouvons transmettre un `$false` à `-Confirm` pour supprimer l’invite.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

Je vais vous expliquer comment ajouter la prise en charge de `-Force` dans une section ultérieure.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference` est une variable automatique qui contrôle quand `ConfirmImpact` vous demande de confirmer l’exécution. Voici les valeurs possibles pour `$ConfirmPreference` et `ConfirmImpact`.

- `High`
- `Medium`
- `Low`
- `None`

Avec ces valeurs, vous pouvez spécifier différents niveaux d’impact pour chaque fonction. Si vous avez `$ConfirmPreference` défini sur une valeur supérieure à `ConfirmImpact`, vous n’êtes pas invité à confirmer l’exécution.

Par défaut, `$ConfirmPreference` est défini sur `High` et `ConfirmImpact` est `Medium`. Si vous souhaitez que votre fonction invite automatiquement l’utilisateur, définissez votre `ConfirmImpact` sur `High`. Sinon, affectez-lui la valeur `Medium` si elle est destructive et utilisez `Low` si la commande est toujours exécutée sans risque en production. Si vous la définissez sur `none`, cela n’affiche pas d’invite même si `-Confirm` a été spécifié (mais vous bénéficiez toujours de la prise en charge de `-WhatIf`).

Lorsque vous appelez une fonction avec `-Confirm`, la valeur de `$ConfirmPreference` est définie sur `Low` à l’intérieur de l’étendue de votre fonction.

### <a name="suppressing-nested-confirm-prompts"></a>Suppression des invites de confirmation imbriquées

`$ConfirmPreference` peut être récupéré par les fonctions que vous appelez. Cela peut créer des scénarios où vous ajoutez une invite de confirmation et la fonction que vous appelez invite également l’utilisateur.

En général, je spécifie `-Confirm:$false` sur les commandes que j’appelle lorsque j’ai déjà traité l’invite.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

Cela nous ramène à un avertissement antérieur : Il existe des nuances en ce qui concerne le moment où `-WhatIf` n’est pas passé à une fonction et lorsque `-Confirm` passe à une fonction. Je promets d’y revenir plus tard.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet.ShouldContinue

Si vous avez besoin de plus de contrôle que `ShouldProcess` ne fournit, vous pouvez déclencher l’invite directement avec `ShouldContinue`. `ShouldContinue` ignore `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference` et `-WhatIf`, car il affiche une invite à chaque fois qu’il est exécuté.

Au premier regard, il est facile de confondre `ShouldProcess` et `ShouldContinue`. J’ai tendance à me souvenir d’utiliser `ShouldProcess`, car le paramètre est appelé `SupportsShouldProcess` dans `CmdletBinding`.
Vous devriez utiliser `ShouldProcess` dans presque tous les scénarios. C’est pourquoi j’ai d’abord parlé de cette méthode.

Examinons `ShouldContinue` en action.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Cela nous offre une invite plus simple avec moins d’options.

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Le problème majeur avec `ShouldContinue` est qu’il faut que l’utilisateur l’exécute de manière interactive, car il affiche toujours une invite pour l’utilisateur. Vous devez toujours créer des outils qui peuvent être utilisés par d’autres scripts. Pour ce faire, vous devez implémenter `-Force`. Je reviendrai sur cette idée plus tard.

### <a name="yes-to-all"></a>Oui pour tout

Cette opération est gérée automatiquement avec `ShouldProcess` mais nous devons effectuer un peu plus de travail pour `ShouldContinue`. Il existe une deuxième surcharge de méthode où nous devons passer quelques valeurs par référence pour contrôler la logique.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

J’ai ajouté une boucle `foreach` et une collection pour la montrer en action. J’ai extrait l’appel `ShouldContinue` de l’instruction `if` pour la rendre plus facile à lire. L’appel d’une méthode avec quatre paramètres commence à devenir un peu brouillon, mais j’ai essayé de le rendre aussi propre que possible.

## <a name="implementing--force"></a>Implémentation de -Force

`ShouldProcess` et `ShouldContinue` doivent implémenter `-Force` de différentes façons. L’astuce pour ces implémentations est que `ShouldProcess` doit toujours être exécuté, mais `ShouldContinue` ne doit pas être exécuté si `-Force` est spécifié.

### <a name="shouldprocess--force"></a>ShouldProcess -Force

Si vous définissez votre `ConfirmImpact` sur `high`, la première chose que vos utilisateurs vont essayer de faire est de le supprimer avec `-Force`. Enfin, c’est la première chose que je ferais.

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

Si vous vous souvenez de la section `ConfirmImpact`, ils doivent en fait l’appeler comme suit :

```powershell
Test-ShouldProcess -Confirm:$false
```

Tout le monde ne réalise pas que cela doit être fait et que `-Force` ne supprime pas `ShouldContinue`.
Nous devons donc implémenter `-Force` pour le bien de nos utilisateurs. Jetez un coup d’œil à cet exemple complet ici :

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Nous ajoutons notre propre commutateur `-Force` en tant que paramètre. Le paramètre `-Confirm` est automatiquement ajouté lors de l’utilisation de `SupportsShouldProcess` dans `CmdletBinding`.

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

Pleins feux sur la logique `-Force` ici :

```powershell
if ($Force){
    $ConfirmPreference = 'None'
}
```

Si l’utilisateur spécifie `-Force`, nous voulons supprimer l’invite de confirmation, sauf s’il spécifie également `-Confirm`. Cela permet à un utilisateur de forcer une modification, tout en confirmant la modification. Ensuite, nous définissons `$ConfirmPreference` dans l’étendue locale. À présent, l’utilisation du paramètre `-Force` attribue temporairement la valeur None à `$ConfirmPreference`, ce qui désactive l’invite de confirmation.

```powershell
if ($Force -or $PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

Si quelqu’un spécifie à la fois `-Force` et `-WhatIf`, `-WhatIf` doit être prioritaire. Cette approche conserve le traitement `-WhatIf`, car `ShouldProcess` est toujours exécuté.

N’ajoutez pas de vérification pour la valeur `$Force` à l’intérieur de l’instruction `if` avec `ShouldProcess`. C’est un anti-modèle pour ce scénario spécifique, même si c’est ce que je vous montrerai dans la section suivante pour `ShouldContinue`.

### <a name="shouldcontinue--force"></a>ShouldContinue -Force

Il s’agit de la méthode correcte pour implémenter `-Force` avec `ShouldContinue`.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

En plaçant `$Force` à gauche de l’opérateur `-or`, il est évalué en premier. Le fait de l’écrire de cette manière court-circuite l’exécution de l’instruction `if`. Si `$force` est `$true`, `ShouldContinue` n’est pas exécuté.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

Nous n’avons pas à nous soucier de `-Confirm` ou `-WhatIf` dans ce scénario, car ils ne sont pas pris en charge par `ShouldContinue`. C’est la raison pour laquelle cela doit être géré différemment de `ShouldProcess`.

## <a name="scope-issues"></a>Problèmes d’étendue

L’utilisation de `-WhatIf` et `-Confirm` est censée s’appliquer à tout ce qui se trouve dans vos fonctions et tout ce qu’elles appellent. Pour ce faire, `$WhatIfPreference` est défini sur `$true` ou `$ConfirmPreference` est défini sur `Low` dans l’étendue locale de la fonction. Lorsque vous appelez une autre fonction, les appels à `ShouldProcess` utilisent ces valeurs.

La plupart du temps, cela fonctionne correctement. Chaque fois que vous appelez une cmdlet ou une fonction intégrée dans la même étendue, cela fonctionne. Cela fonctionne également lorsque vous appelez un script ou une fonction dans un module de script à partir de la console.

Le scénario spécifique où cela ne fonctionne pas est lorsqu’un script ou un module de script appelle une fonction dans un autre module de script. Cela peut ne pas sembler être un problème majeur, mais la plupart des modules que vous créez ou extrayez de PSGallery sont des modules de script.

Le problème principal est que les modules de script n’héritent pas des valeurs de `$WhatIfPreference` ou `$ConfirmPreference` (et plusieurs autres) lorsqu’ils sont appelés à partir de fonctions dans d’autres modules de script.

La meilleure façon de résumer ceci en règle générale est que cela fonctionne correctement pour les modules binaires et qu’il ne faut pas penser que cela fonctionne pour les modules de script. Si vous n’êtes pas sûr, testez-le ou supposez simplement que cela ne fonctionne pas correctement.

Personnellement, je pense que c’est très dangereux, car cela crée des scénarios dans lesquels vous ajoutez la prise en charge de `-WhatIf` à plusieurs modules qui fonctionnent correctement de manière isolée, mais qui ne fonctionnent pas correctement lorsqu’ils s’appellent l’un l’autre.

Un RFC GitHub travaille à la résolution de ce problème. Pour plus d’informations, consultez [Propager les préférences d’exécution au-delà de l’étendue du module de script][RFC].

## <a name="in-closing"></a>Conclusion

Je dois rechercher comment utiliser `ShouldProcess` à chaque fois que j’ai besoin de l’utiliser. Il m’a fallu beaucoup de temps pour distinguer `ShouldProcess` de `ShouldContinue`. Je dois presque toujours rechercher les paramètres à utiliser. Donc, ne vous inquiétez pas si vous vous trompez de temps à autre. Cet article est disponible lorsque vous en avez besoin. Je suis sûr d’y faire souvent référence moi-même.

Si vous avez aimé cette publication, veuillez nous faire part de vos commentaires sur Twitter en utilisant le lien ci-dessous. J’aime obtenir l’avis de ceux qui retirent de la valeur de mon contenu.

<!-- link references -->
[version d’origine]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[paramètres communs]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[tout ce que vous souhaitiez savoir sur les tables de hachage]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
