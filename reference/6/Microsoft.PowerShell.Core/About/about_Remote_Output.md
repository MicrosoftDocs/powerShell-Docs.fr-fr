---
description: Décrit comment interpréter et mettre en forme la sortie des commandes distantes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: dd3f1e3dedf69f185db17253177e07a3331679a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206917"
---
# <a name="about-remote-output"></a>À propos de la sortie à distance

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment interpréter et mettre en forme la sortie des commandes distantes.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

La sortie d’une commande exécutée sur un ordinateur distant peut ressembler à la sortie de la même commande exécutée sur un ordinateur local, mais il existe des différences significatives.

Cette rubrique explique comment interpréter, mettre en forme et afficher la sortie des commandes exécutées sur des ordinateurs distants.

## <a name="displaying-the-computer-name"></a>AFFICHAGE DU NOM DE L’ORDINATEUR

Lorsque vous utilisez l’applet de commande Invoke-Command pour exécuter une commande sur un ordinateur distant, la commande retourne un objet qui comprend le nom de l’ordinateur qui a généré les données. Le nom de l’ordinateur distant est stocké dans la propriété PSComputerName.

Pour de nombreuses commandes, PSComputerName est affiché par défaut. Par exemple, la commande suivante exécute une commande Get-Culture sur deux ordinateurs distants, serveur01 et Server02. La sortie, qui apparaît ci-dessous, comprend les noms des ordinateurs distants sur lesquels la commande a été exécutée.

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

Vous pouvez utiliser le paramètre HideComputerName de Invoke-Command pour masquer la propriété PSComputerName. Ce paramètre est conçu pour les commandes qui collectent des données à partir d’un seul ordinateur distant.

La commande suivante exécute une commande Get-Culture sur l’ordinateur distant SERVEUR01. Elle utilise le paramètre HideComputerName pour masquer la propriété PSComputerName et les propriétés associées.

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

Vous pouvez également afficher la propriété PSComputerName si elle n’est pas affichée par défaut.

Par exemple, les commandes suivantes utilisent l’applet de commande Format-Table pour ajouter la propriété PSComputerName à la sortie d’une commande de Get-Date à distance.

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a>AFFICHAGE DE LA PROPRIÉTÉ MACHINENAME

Plusieurs applets de commande, y compris obtenir-process, obtenir-service et obtenir-EventLog, ont un paramètre ComputerName qui obtient les objets sur un ordinateur distant.
Ces applets de commande n’utilisent pas la communication à distance PowerShell. vous pouvez donc les utiliser même sur des ordinateurs qui ne sont pas configurés pour la communication à distance dans Windows PowerShell.

Les objets que ces applets de commande retournent stockent le nom de l’ordinateur distant dans la propriété MachineName. (Ces objets n’ont pas de propriété PSComputerName.)

Par exemple, cette commande obtient le processus PowerShell sur les ordinateurs distants SERVEUR01 et Server02. L’affichage par défaut n’inclut pas la propriété MachineName.

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

Vous pouvez utiliser l’applet de commande Format-Table pour afficher la propriété MachineName des objets de processus.

Par exemple, la commande suivante enregistre les processus dans la variable $p, puis utilise un opérateur de pipeline (|) pour envoyer les processus dans $p à la commande Format-Table. La commande utilise le paramètre Property de Format-Table pour inclure la propriété MachineName dans l’affichage.

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

La commande suivante plus complexe ajoute la propriété MachineName à l’affichage du processus par défaut. Il utilise des tables de hachage pour spécifier des propriétés calculées. Heureusement, vous n’avez pas à le comprendre pour l’utiliser.

(Notez que la Supercycle ['] est le caractère de continuation.)

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a>OBJETS DÉSÉRIALISÉS

Lorsque vous exécutez des commandes distantes qui génèrent une sortie, le résultat de la commande est transmis sur le réseau à l’ordinateur local.

Étant donné que la plupart des objets en direct Microsoft .NET Framework (tels que les objets retournés par les applets de commande PowerShell) ne peuvent pas être transmis sur le réseau, les objets actifs sont « sérialisés ». En d’autres termes, les objets actifs sont convertis en représentations XML de l’objet et de ses propriétés. Ensuite, l’objet sérialisé XML est transmis sur le réseau.

Sur l’ordinateur local, PowerShell reçoit l’objet sérialisé XML et le « désérialise » en convertissant l’objet XML en un objet de .NET Framework standard.

Toutefois, l’objet désérialisé n’est pas un objet actif. Il s’agit d’un instantané de l’objet au moment où il a été sérialisé, et il comprend des propriétés, mais pas de méthodes. Vous pouvez utiliser et gérer ces objets dans PowerShell, y compris les transmettre dans des pipelines, afficher les propriétés sélectionnées et les mettre en forme.

La plupart des objets désérialisés sont automatiquement mis en forme pour être affichés par les entrées dans les fichiers XML Types.ps1XML ou Format.ps1. Toutefois, l’ordinateur local n’a peut-être pas de fichier de mise en forme pour tous les objets désérialisés qui ont été générés sur un ordinateur distant. Lorsque les objets ne sont pas mis en forme, toutes les propriétés de chaque objet s’affichent dans la console dans une liste de diffusion en continu.

Lorsque les objets ne sont pas mis en forme automatiquement, vous pouvez utiliser les applets de commande de mise en forme, telles que Format-Table ou format-list, pour mettre en forme et afficher les propriétés sélectionnées. Vous pouvez utiliser l’applet de commande Out-GridView pour afficher les objets dans une table.

En outre, si vous exécutez une commande sur un ordinateur distant qui utilise des applets de commande que vous n’avez pas sur votre ordinateur local, les objets renvoyés par la commande peuvent ne pas être correctement mis en forme, car vous ne disposez pas des fichiers de mise en forme de ces objets sur votre ordinateur. Pour récupérer des données de mise en forme à partir d’un autre ordinateur, utilisez les applets de commande Get-FormatData et Export-FormatData.

Certains types d’objets, tels que les objets DirectoryInfo et les GUID, sont reconvertis en objets dynamiques lorsqu’ils sont reçus. Ces objets n’ont pas besoin d’une gestion ou d’une mise en forme spéciale.

## <a name="ordering-the-results"></a>CLASSEMENT DES RÉSULTATS

L’ordre des noms d’ordinateur dans le paramètre ComputerName des applets de commande détermine l’ordre dans lequel PowerShell se connecte aux ordinateurs distants. Toutefois, les résultats s’affichent dans l’ordre dans lequel l’ordinateur local les reçoit, ce qui peut être un ordre différent.

Pour modifier l’ordre des résultats, utilisez l’applet de commande Sort-Object. Vous pouvez effectuer un tri sur la propriété PSComputerName ou MachineName. Vous pouvez également effectuer un tri sur une autre propriété de l’objet afin que les résultats de différents ordinateurs soient intercalés.

## <a name="see-also"></a>VOIR AUSSI

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Get-Process](xref:Microsoft.PowerShell.Management.Get-Process)

[Get-Service](xref:Microsoft.PowerShell.Management.Get-Service)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)
