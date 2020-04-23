---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Obtention d’informations sur les commandes
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030946"
---
# <a name="getting-information-about-commands"></a>Obtention d’informations sur les commandes

La cmdlet `Get-Command` de PowerShell affiche les commandes disponibles dans la session active.
Lorsque vous exécutez la cmdlet `Get-Command`, vous obtenez une sortie similaire à ce qui suit :

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Cette sortie ressemble beaucoup à la sortie Help de **cmd.exe**, à savoir un résumé des commandes internes sous forme de tableau. Dans l’extrait de la sortie de la commande `Get-Command` ci-dessus, chaque commande est de type Cmdlet (« applet de commande »). Une cmdlet est le type de commande intrinsèque de PowerShell. Ce type correspond à peu près à des commandes telles que `dir` et `cd` dans **cmd.exe** ou aux commandes intégrées des interpréteurs de commandes Unix tels que bash.

La cmdlet `Get-Command` dispose d’un paramètre **Syntax** qui retourne la syntaxe de chaque cmdlet. L’exemple suivant montre comment obtenir la syntaxe de la cmdlet `Get-Help` :

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Affichage des types de commandes disponibles

La commande `Get-Command` répertorie uniquement les cmdlets dans la session active. PowerShell prend en charge plusieurs autres types de commandes :

- Alias
- Fonctions
- Scripts

Les fichiers externes exécutables, ou les fichiers possédant un gestionnaire de type de fichier inscrit, sont également considérés comme des commandes.

Pour obtenir toutes les commandes dans la session, tapez :

```powershell
Get-Command *
```

Cette liste recense les commandes externes dans votre chemin de recherche, elle peut donc contenir des milliers d'éléments.
Il est plus judicieux d'examiner un ensemble réduit de commandes.

> [!NOTE]
> L’astérisque (\*) est utilisé comme caractère générique dans les arguments de commande PowerShell. Le symbole \* représente un ou plusieurs caractères. Vous pouvez taper `Get-Command a*` pour rechercher toutes les commandes dont le nom commence par la lettre « a ». Contrairement aux caractères génériques dans **cmd.exe**, un caractère générique peut représenter un point dans PowerShell.

Pour obtenir les commandes natives d’autres types, utilisez le paramètre **CommandType** de la cmdlet `Get-Command`.
applet de commande.

Pour obtenir les alias des commandes, c'est-à-dire les surnoms affectés aux commandes, tapez :

```powershell
Get-Command -CommandType Alias
```

Pour obtenir les fonctions dans la session active, tapez :

```powershell
Get-Command -CommandType Function
```

Pour afficher les scripts dans le chemin de recherche de PowerShell, tapez :

```powershell
Get-Command -CommandType Script
```
