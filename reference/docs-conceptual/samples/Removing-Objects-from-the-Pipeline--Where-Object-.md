---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Suppression d’objets du pipeline Where Object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737183"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Suppression d’objets du pipeline (Where-Object)

Dans PowerShell, vous générez et transmettez souvent à un pipeline plus d’objets que souhaité. Vous pouvez spécifier les propriétés d’objets particuliers à afficher à l’aide des cmdlets `Format-*`, mais cela ne résout pas le problème de la suppression d’objets entiers de l’affichage. Il se peut que vous souhaitiez filtrer des objets avant la fin d’un pipeline afin de pouvoir effectuer des actions uniquement sur un sous-ensemble des objets générés initialement.

PowerShell inclut une cmdlet `Where-Object` qui permet de tester chaque objet dans le pipeline et de le transmettre dans le pipeline uniquement s’il répond à une condition de test particulière. Les objets qui ne passent pas le test sont supprimés du pipeline. Vous fournissez la condition de test comme valeur du paramètre **FilterScript**.

## <a name="performing-simple-tests-with-where-object"></a>Exécution de tests simples avec l’applet de commande Where-objet

La valeur de **FilterScript** est un *bloc de script* : une ou plusieurs commandes PowerShell entourées d’accolades (`{}`) qui prend la valeur true ou false. Ces blocs de script peuvent être très simples, mais leur création nécessite de connaître un autre concept de PowerShell, à savoir les opérateurs de comparaison. Un opérateur de comparaison compare les éléments figurant de part et d’autre de celui-ci. Les opérateurs de comparaison commencent par un caractère (`-`) suivi d’un nom. Les opérateurs de comparaison de base fonctionnent sur pratiquement tout type d’objet. Certains opérateurs de comparaison plus avancés fonctionnent uniquement sur du texte ou des tableaux.

> [!NOTE]
> Par défaut, lorsque vous travaillez sur du texte, les opérateurs de comparaison PowerShell ne respectent pas la casse.

En raison de considérations liées à l’analyse, les symboles tels que `<`,`>` et `=` ne sont pas utilisés comme opérateurs de comparaison. Au lieu de cela, les opérateurs de comparaison sont constitués de lettres. Les opérateurs de comparaison de base sont répertoriés dans le tableau suivant.

| Opérateur de comparaison |                  Signification                   |    Exemple (retourne true)    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| -eq                 | Est égal à                                | 1 -eq 1                      |
| -ne                 | N’est pas égal à                            | 1 -ne 2                      |
| -lt                 | Est inférieur à                               | 1 -lt 2                      |
| -le                 | Est inférieur ou égal à                   | 1 -le 2                      |
| -gt                 | Est supérieur à                            | 2 -gt 1                      |
| -ge                 | Est supérieur ou égal à                | 2 -ge 1                      |
| -like               | Est comme (comparaison générique pour le texte)     | "file.doc" -like "f*.do?"    |
| -notlike            | N’est pas comme (comparaison générique pour le texte) | "file.doc" -notlike "p*.doc" |
| -contains           | Contient                                   | 1,2,3 -contains 1            |
| -notcontains        | Ne contient pas                           | 1,2,3 -notcontains 4         |

Les blocs de script `Where-Object` utilisent la variable spéciale `$_` pour faire référence à l’objet actuel dans le pipeline. Voici un exemple de son fonctionnement. Si vous avez une liste de nombres et souhaitez retourner uniquement ceux dont la valeur est inférieure à 3, vous pouvez utiliser `Where-Object` pour filtrer les nombres en tapant ce qui suit :

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtrage basé sur les propriétés de l’objet

Comme `$_` fait référence à l’objet de pipeline actif, nous pouvons accéder à ses propriétés pour nos tests.

Par exemple, nous pouvons examiner la classe **Win32_SystemDriver** dans WMI. Il peut y avoir des centaines de pilotes système sur un système particulier, mais il se peut que vous vous intéressiez uniquement à certains pilotes, par exemple, à ceux qui sont en cours d’exécution. Pour la classe **Win32_SystemDriver** la propriété appropriée est **État**. Vous pouvez filtrer les pilotes du système afin de sélectionner uniquement ceux qui sont en cours d’exécution, en tapant ce qui suit :

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

Cela génère toujours une longue liste. Il se peut que vouliez filtrer afin de sélectionner uniquement les pilotes configurés pour démarrer automatiquement, en testant également la valeur **StartMode** :

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

Cela produit un grand nombre d’informations dont nous n’avons plus besoin, car nous savons que les pilotes sont en cours d’exécution.
En fait, les seules informations dont nous ayons probablement besoin à ce stade sont le nom et le nom d’affichage. La commande suivante inclut uniquement ces deux propriétés, de sorte que la sortie est beaucoup plus simple :

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

Il existe deux éléments `Where-Object` dans la commande ci-dessus, mais ils peuvent être exprimés en un seul élément `Where-Object` à l’aide de l’opérateur logique `-and` comme suit :

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

Les opérateurs logiques standards sont répertoriés dans le tableau suivant.

| Opérateur logique |                 Signification                  |  Exemple (retourne true)  |
| ---------------- | ---------------------------------------- | ------------------------ |
| -and             | Opérateur logique et ; true si les deux côtés sont vrais | (1 -eq 1) -and (2 -eq 2) |
| -or              | Opérateur logique ou ; true si l’un des côtés est vrai  | (1 -eq 1) -or (1 -eq 2)  |
| -not             | Opérateur logique non ; inverse les valeurs true et false     | -not (1 -eq 2)           |
| \!               | Opérateur logique non ; inverse les valeurs true et false     | \!(1 -eq 2)              |
