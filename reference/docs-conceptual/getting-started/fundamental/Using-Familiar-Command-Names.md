---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de noms de commande familiers
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 37fc6dfad5a2f1363254744141dcab1e13aa5066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952679"
---
# <a name="using-familiar-command-names"></a>Utilisation de noms de commande familiers
Grâce à ce qu’on appelle des *alias*, Windows PowerShell permet aux utilisateurs de faire référence aux commandes par d’autres noms. Les alias permettent aux utilisateurs ayant l’expérience d’autres interpréteurs de commande (shells) de réutiliser des noms de commandes communes qu’ils connaissent déjà pour effectuer des opérations similaires dans Windows PowerShell. Bien que nous ne décrivions pas ici les alias Windows PowerShell en détail, vous pouvez toujours vous en servir lorsque vous commencez à utiliser Windows PowerShell.

Un alias associe un nom de commande que vous tapez à une autre commande. Par exemple, Windows PowerShell dispose d’une fonction interne nommée **Clear-Host** qui efface la fenêtre de sortie. Si vous tapez la commande **cls** ou **clear** à une invite de commandes, Windows PowerShell l’interprète comme un alias pour la fonction **Clear-Host** et exécute la fonction **Clear-Host**.

Cette fonctionnalité aide les utilisateurs à apprendre à utiliser Windows PowerShell. Tout d’abord, la plupart des utilisateurs d’UNIX et de Cmd.exe connaissent déjà un vaste éventail de commandes par leur nom. S’il se peut que certaines commandes équivalentes de Windows PowerShell ne pas produisent pas des résultats rigoureusement identiques, elles sont suffisamment proches dans leur mode d’utilisation pour que les utilisateurs puissent s’en servir dans le cadre de leur travail sans devoir préalablement mémoriser les noms des commandes dans Windows PowerShell. Ensuite, la principale source de frustration liée à l’apprentissage d’un nouvel interpréteur de commandes lorsque l’utilisateur est déjà familiarisé avec un autre, réside dans les erreurs résultant de la « mémoire des doigts ». Si vous avez utilisé Cmd.exe pendant des années, lorsque vous avez un écran saturé de sorties et souhaitez le nettoyer, vous tapez instinctivement la commande **cls**, puis appuyez sur la touche Entrée. Sans l’alias de la fonction **Clear-Host** dans Windows PowerShell, vous obtiendriez simplement un message d’erreur tel que « **Le terme " cls " n’est pas reconnu en tant qu’applet de commande, fonction, programme exécutable ou fichier de script.**  », et vous vous sentiriez désarmé quant à la manière de procéder pour effacer la sortie.

Voici une courte liste des commandes UNIX et Cmd.exe communes que vous pouvez utiliser dans Windows PowerShell :

|||||
|-|-|-|-|
|cat|dir|mount|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|type|
|del|lp|r|write|
|diff|ls|ren||

Si vous utilisez l’une de ces commandes instinctivement et souhaitez connaître le nom réel de la commande native correspondante dans Windows PowerShell, vous pouvez utiliser la commande **Get-Alias**:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Pour améliorer la lisibilité des exemples, le Guide de l’utilisateur de Windows PowerShell évite généralement d’utiliser des alias. Toutefois, en savoir plus sur les alias dès à présent peut toujours être utile si vous travaillez avec des extraits de code arbitraires de Windows PowerShell à partir d’une autre source ou souhaitez définir vos propres alias. Le reste de cette section traite des alias standard et de la manière de définir vos propres alias.

### <a name="interpreting-standard-aliases"></a>Interprétation des alias standard
Contrairement aux alias décrits ci-dessus, qui sont conçus pour permettre la compatibilité des noms avec d’autres interfaces, les alias intégrés dans Windows PowerShell sont généralement conçus avec un souci de concision. Ces noms courts peuvent être tapés rapidement, mais sont illisibles si vous ignorez les commandes auxquelles ils font référence.

Windows PowerShell tente de trouver un compromis entre la clarté et la concision, en fournissant un ensemble d’alias standards basés sur des mots abrégés pour les verbes et substantifs courants. Cela permet de constituer un ensemble de base d’alias pour les applets de commande communes, qui soient lisibles lorsque vous connaissez les noms abrégés. Par exemple, dans les alias standard, le verbe **Get** est abrégé en **g**, le verbe **Set** est abrégé en **s**, le substantif **Item** est abrégé en **i**, le substantif **Location** est abrégé en **l**, et le substantif Command est abrégé en **cm**.

Voici un bref exemple illustrant la manière dont cela fonctionne. L’alias standard pour Get-Item provient de combinaison de **g** pour Get et de **i** pour Item : **gi**. L’alias standard pour Set-Item provient de la combinaison de **s** pour Set et de **i** pour Item : **si**. L’alias standard pour Get-Location provient de la combinaison de **g** pour Get et de **l** pour Location : **gl**. L’alias standard pour Set-Location provient de la combinaison de **s** pour Set et de **l** pour Location : **sl**. L’alias standard pour Get-Command provient de la combinaison de **g** pour Get et de **cm** de Commande : **gcm**. Il n’existe pas d’applet de commande Set-Command mais, si elle existait, nous pouvons deviner que son alias standard serait composé de **s** pour Set et de **cm** pour Command : **scm**. Par ailleurs, des utilisateurs connaissant les alias de Windows PowerShell qui rencontreraient l’alias **scm** pourraient deviner que celui-ci fait référence à l’applet de commande Set-Command.

### <a name="creating-new-aliases"></a>Création d’alias
Vous pouvez créer vos propres alias à l’aide de l’applet de commande Set-Alias. Par exemple, les instructions suivantes créent les alias d’applet de commande décrit dans Interprétation des alias standard :

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

En interne, Windows PowerShell utilise de telles commandes au démarrage, mais ces alias ne sont pas modifiables. Si vous tentez d’exécuter réellement l’une de ces commandes, vous obtenez un message d’erreur expliquant que l’alias ne peut pas être modifié. Par exemple :

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```