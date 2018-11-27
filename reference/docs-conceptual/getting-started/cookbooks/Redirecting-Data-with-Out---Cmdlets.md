---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Redirection de données à l’aide d’applets de commande Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321007"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Redirection de données à l’aide d’applets de commande Out-*

Windows PowerShell fournit plusieurs applets de commande qui vous permettent de contrôler directement la sortie de données. Ces applets de commande partagent deux caractéristiques importantes.

Tout d’abord, elles transforment généralement les données en une forme de texte. Elles opèrent de la sorte, car elles envoient les données à des composants système qui requièrent une entrée de texte. Cela signifie qu’elles doivent représenter les objets sous forme de texte. C’est pourquoi le texte est mis en forme tel qu’il apparaît dans la fenêtre de la console Windows PowerShell.

Ensuite, ces applets de commande utilisent le verbe Windows PowerShell **Out**, car elles envoient des informations de Windows PowerShell vers un autre emplacement. L’applet de commande **Out-Host** ne fait pas exception : l’affichage de la fenêtre hôte se trouve en dehors de Windows PowerShell. Ceci est important car, lorsque des données sont envoyées hors de Windows PowerShell, elles sont réellement supprimées. Vous pouvez le constater si vous tentez de créer un pipeline qui pagine les données vers la fenêtre hôte, puis tentez d’appliquer une mise en forme de liste, comme illustré ici :

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Vous pouvez vous attendre à ce que la commande affiche des pages d’informations sur le processus sous forme de liste. Au lieu de cela, elle affiche la liste tabulaire par défaut :

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

L’applet de commande **Out-Host** envoyant les données directement à la console, la commande **Format-List** ne reçoit jamais rien à mettre en forme.

La façon correcte de structurer cette commande consiste à placer l’applet de commande **Out-Host** à la fin du pipeline, comme illustré ci-dessous. Ainsi, les données du processus sont mises en forme de liste avant d’être paginées et affichées.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Cela s’applique à toutes les applets de commande **Out**. Une applet de commande **Out** doit toujours apparaître à la fin du pipeline.

> [!NOTE]
> Toutes les applets de commande **Out** restituent la sortie en tant que texte, en utilisant la mise en forme applicable à la fenêtre de console, y compris les limites de longueur de ligne.

#### <a name="paging-console-output-out-host"></a>Pagination de la sortie de la console (Out-Host)

Par défaut, Windows PowerShell envoie les données à la fenêtre hôte, ce qui est exactement ce que fait l’applet de commande Out-Host. La principale utilisation de l’applet de commande Out-Host est la pagination des données, que nous avons abordée précédemment. Par exemple, la commande suivante utilise l’applet de commande Out-Host pour paginer la sortie de l’applet de commande Get-Command :

```powershell
Get-Command | Out-Host -Paging
```

Vous pouvez également utiliser la fonction **more** pour paginer les données. Dans Windows PowerShell, la fonction **more** appelle l’applet de commande **Out-Host -Paging**. La commande suivante illustre l’utilisation de la fonction **more** pour paginer la sortie de l’applet de commande Get-Command :

```powershell
Get-Command | more
```

Si vous incluez un ou plusieurs noms de fichiers en tant qu’arguments pour la fonction more, celle-ci lit les fichiers spécifiés et pagine leur contenu vers l’hôte :

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Ignorance de la sortie (Out-Null)

L’applet de commande **Out-Null** est conçue pour ignorer toute entrée qu’elle reçoit. Cela est utile pour ignorer des données superflues que vous recevez suite à l’exécution d’une commande. Lorsque vous tapez la commande suivante, celle-ci ne retourne rien :

```powershell
Get-Command | Out-Null
```

L’applet de commande **Out-Null** n’ignore pas la sortie d’erreur. Par exemple, si vous entrez la commande suivante, un message s’affiche vous informant que Windows PowerShell ne reconnaît pas « Is-NotACommand » :

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Impression de données (Out-Printer)

L’applet de commande **Out-Printer** permet d’imprimer des données. Si vous ne fournissez pas de nom d’imprimante, l’applet de commande **Out-Printer** utilise votre imprimante par défaut. Vous pouvez utiliser n’importe quelle imprimante Windows en spécifiant son nom d’affichage. Vous n’avez pas besoin de mappage de port d’imprimante ou même d’une imprimante physique réelle. Par exemple, si les outils de Microsoft Office Document Imaging sont installés, vous pouvez envoyer les données vers un fichier image en tapant ce qui suit :

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Enregistrement de données (Out-File)

Vous pouvez envoyer une sortie vers un fichier plutôt que vers la fenêtre de console en utilisant l’applet de commande **Out-File**. La ligne de commande suivante envoie une liste de processus au fichier **C:\\temp\\processlist.txt** :

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Les résultats de l’utilisation de l’applet de commande **Out-File** peuvent différer de ce que vous attendez si vous êtes habitué à la redirection de sortie traditionnelle. Pour comprendre le comportement de l’applet de commande **Out-File**, vous devez connaître le contexte dans lequel elle opère.

Par défaut, l’applet de commande **Out-File** crée un fichier Unicode. Il s’agit de la meilleure option par défaut sur le long terme, mais elle signifie que les outils qui attendent des fichiers ASCII ne fonctionnent pas correctement avec le format de sortie par défaut. Vous pouvez modifier le format de sortie par défaut en ASCII à l’aide du paramètre **Encoding**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

L’applet de commande **Out-File** met en forme le contenu du fichier pour qu’il ressemble à une sortie de la console. Cela a pour effet que, dans la plupart des cas, la sortie est tronquée comme dans une fenêtre de console. Par exemple, si vous exécutez la commande suivante :

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

La sortie doit ressembler à ceci :

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Pour obtenir une sortie qui ne force pas de retour automatique à la ligne pour correspondre à la largeur de l’écran, vous pouvez utiliser le paramètre **Width** pour spécifier une largeur de ligne. Étant donné que le paramètre **Width** est un entier 32 bits, il peut atteindre la valeur de 2147483647. Pour définir la largeur de ligne sur cette valeur maximale, tapez la commande suivante :

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

L’applet de commande **Out-File** est particulièrement utile si vous souhaitez enregistrer la sortie telle qu’elle s’afficherait sur la console. Afin de mieux contrôler le format de sortie, vous avez besoin d’outils plus avancés. Nous allons les examiner dans le chapitre suivant, en même temps que certains détails sur la manipulation des objets.