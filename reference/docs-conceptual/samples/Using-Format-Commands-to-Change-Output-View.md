---
ms.date: 11/22/2019
keywords: powershell,applet de commande
title: Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417587"
---
# <a name="using-format-commands-to-change-output-view"></a>Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie

PowerShell dispose d’un ensemble d’applets de commande qui vous permettent de contrôler la façon dont les propriétés s’affichent pour certains objets. Le nom de toutes les applets de commande commence par `Format`. Vous pouvez sélectionner les propriétés que vous voulez afficher.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

Cet article décrit les applets de commande `Format-Wide`, `Format-List` et `Format-Table`.

Dans PowerShell, chaque type d’objet possède des propriétés qui sont utilisées par défaut si vous ne précisez celles qui doivent être affichées. De même, chaque applet de commande utilise le même paramètre **Property** pour spécifier les propriétés à afficher. Comme `Format-Wide` n’affiche qu’une seule propriété, son paramètre **Property** n’accepte qu’une seule valeur, mais les paramètres des propriétés de `Format-List` et `Format-Table` acceptent une liste de noms de propriétés.

Dans cet exemple, la sortie par défaut de l’applet de commande `Get-Process` montre qu’il y a deux instances d’Internet Explorer en cours d’exécution.

```powershell
Get-Process -Name iexplore
```

Par défaut, les objets **Process** affichent les propriétés présentées ici :

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Utilisation de l’applet de commande Format-Wide pour une sortie d’élément unique

Par défaut, l’applet de commande `Format-Wide` affiche uniquement la propriété par défaut d’un objet. Les informations associées à chaque objet s’affichent dans une seule colonne :

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

Vous pouvez également spécifier une propriété autre que celle par défaut :

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Contrôle de l’affichage de Format-Wide avec une colonne

La cmdlet `Format-Wide` ne permet d’afficher qu’une seule propriété à la fois. Cela s’avère utile pour afficher des listes volumineuses dans plusieurs colonnes.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Utilisation de l’applet de commande Format-List pour un Affichage Liste

L’applet de commande `Format-List` affiche un objet sous forme de liste, chaque propriété étant étiquetée et affichée sur une ligne distincte :

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

Vous pouvez spécifier autant de propriétés que vous le souhaitez :

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Obtention d’informations détaillées en utilisant l’applet de commande Format-List avec des caractères génériques

L’applet de commande `Format-List` permet d’utiliser un caractère générique comme valeur de son paramètre **Property**. Cela permet d’afficher des informations détaillées. Souvent, les objets contiennent plus d’informations qu’il n’en faut. C’est pourquoi, par défaut, PowerShell n’affiche pas les valeurs de toutes les propriétés. Pour afficher toutes les propriétés d’un objet, utilisez la commande `Format-List -Property *`. La commande suivante génère plus de 60 lignes de sortie pour un seul processus :

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

Bien que la commande `Format-List` soit utile pour afficher des détails, si vous voulez obtenir une vue d’ensemble d’une sortie qui comporte un grand nombre d’éléments, une simple vue tabulaire est souvent plus utile.

## <a name="using-format-table-for-tabular-output"></a>Utilisation de l’applet de commande Format-Table pour une sortie tabulaire

Si vous utilisez l’applet de commande `Format-Table` sans spécifier de noms de propriétés pour mettre en forme la sortie de la commande `Get-Process`, vous obtenez exactement la même sortie que si vous n’utilisiez pas d’applet de commande `Format`. Par défaut, PowerShell affiche les objets **Process** dans un format tabulaire.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Amélioration de la sortie de l’applet de commande Format-Table (AutoSize)

Bien qu’une vue tabulaire soit utile pour afficher beaucoup d’informations, elle peut être difficile à interpréter si l’affichage est trop étroit pour les données. Dans l’exemple précédent, la sortie est tronquée. Si vous spécifiez le paramètre **AutoSize** quand vous exécutez la commande `Format-Table`, PowerShell calcule les largeurs des colonnes en fonction des données réelles affichées. Les colonnes deviennent ainsi lisibles.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

L’applet de commande `Format-Table` peut continuer de tronquer des données, mais cela ne se produit qu’à la fin de l’écran. Les propriétés, à l’exception de la dernière affichée, disposent de la taille nécessaire pour que leur élément de données le plus long s’affiche correctement.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

La commande `Format-Table` part du principe que les propriétés sont listées par ordre d’importance. Elle tente donc d’afficher entièrement les propriétés les plus proches du début. Si la commande `Format-Table` ne peut pas afficher toutes les propriétés, elle supprime certaines colonnes de l’affichage. Vous pouvez observer ce comportement dans l’exemple précédent de la propriété **DependentServices**.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Retour automatique à la ligne de la sortie de l’applet de commande Format-Table dans les colonnes (Wrap)

Vous pouvez forcer le retour automatique à la ligne des données `Format-Table` retournées en nombre dans leur colonne d’affichage en utilisant le paramètre **Wrap**. L’utilisation du paramètre **Wrap** ne produit pas nécessairement le résultat escomptés, car si vous ne spécifiez pas **AutoSize**, les paramètres par défaut sont utilisés :

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

L’utilisation du paramètre **Wrap** par lui-même ne ralentit considérablement le traitement. Cependant, si vous voulez mettre en forme une liste récursive de fichiers d’une structure d’annuaire volumineuse en utilisant le paramètre **AutoSize**, celui-ci tardera à afficher les premiers éléments de sortie et mobilisera beaucoup de mémoire.

Si vous n’êtes pas préoccupé par la charge du système, **AutoSize** fonctionne bien avec le paramètre **Wrap**.
Les premières colonnes continuent d’utiliser la largeur nécessaire à l’affichage des éléments sur une même ligne, mais la colonne finale est réduite, si nécessaire.

> [!NOTE]
> Il se peut que certaines colonnes ne s’affichent pas si vous spécifiez les colonnes les plus larges en premier. Pour de meilleurs résultats, spécifiez les éléments de données les plus petits en premier.

Dans l’exemple suivant, les propriétés les plus larges sont spécifiées en premier.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

Même avec le retour automatique à la ligne, la dernière colonne **Id** est omise :

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>Organisation de la sortie de table (-GroupBy)

Un autre paramètre utile pour le contrôle de la sortie tabulaire est **GroupBy**. Des listes tabulaires plus longues en particulier peuvent être difficiles à comparer. Le paramètre **GroupBy** groupe la sortie en fonction d’une valeur de propriété. Par exemple, nous pouvons grouper les services en fonction du paramètre **StartType** pour faciliter l’inspection, en omettant la valeur de **StartType** de la liste des propriétés :

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
