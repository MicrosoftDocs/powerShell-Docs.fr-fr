---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 22e6a8de2b52039e0a23cab135f81ff74bdf929a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204973"
---
# Out-GridView

## SYNOPSIS
Envoie la sortie vers un tableau interactif dans une fenêtre distincte.

## SYNTAX

### PassThru (par défaut)

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### Wait

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### OutputMode

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## Description

L' `Out-GridView` applet de commande envoie la sortie d’une commande à une fenêtre d’affichage de grille dans laquelle la sortie est affichée dans un tableau interactif.

Étant donné que cette applet de commande nécessite une interface utilisateur, elle ne fonctionne pas sur Windows Server Core ou Windows nano Server.

Vous pouvez utiliser les fonctionnalités suivantes du tableau pour examiner vos données :

- Masquer, afficher et réorganiser les colonnes
- Trier les lignes
- Filtre rapide
- Filtre ajouter des critères
- Copier et coller

Pour obtenir des instructions complètes, consultez la section [Remarques](#notes) de cet article.

> [!NOTE]
> Cette applet de commande a été réintroduite dans PowerShell 7. Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows. Pour une version multiplateforme de cette applet de commande, consultez le module [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) dans le PowerShell Gallery.

## EXEMPLES

### Exemple 1 : processus de sortie vers un affichage de grille

Cet exemple obtient les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.

```powershell
Get-Process | Out-GridView
```

### Exemple 2 : utiliser une variable pour sortir des processus dans un affichage de grille

Cet exemple obtient également les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.

```powershell
$P = Get-Process
$P | Out-GridView
```

La sortie de l' `Get-Process` applet de commande est enregistrée dans la `$P` variable. Ensuite, `$P` est dirigé vers `Out-GridView` .

### Exemple 3 : afficher les propriétés sélectionnées dans un affichage de grille

Cet exemple affiche les propriétés sélectionnées des processus en cours d’exécution dans un affichage de grille.

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

La sortie de `Get-Process` est redirigée vers `Select-Object` pour sélectionner les propriétés **Name** , de la **plage** de **PeakWorkingSet** et de la propriété. Un autre opérateur de pipeline envoie les objets filtrés à l' `Sort-Object` applet de commande pour les trier dans l’ordre décroissant selon la valeur de la propriété de la **plage** de recherche.
Ensuite, les résultats triés sont dirigés vers `Out-GridView` . Vous pouvez maintenant utiliser les fonctionnalités de l'affichage de grille pour rechercher, trier ou filtrer les données.

### Exemple 4 : enregistrer la sortie dans une variable, puis générer une vue grille

Cet exemple enregistre la sortie de l’applet de commande dans une variable, puis l’envoie à `Out-GridView` .

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

`Get-ChildItem` Obtient tous les fichiers dans le répertoire d’installation de PowerShell et ses sous-répertoires à l’aide de la `$PSHOME` variable automatique. Les parenthèses de la commande établissent l'ordre des opérations. En conséquence, la sortie de la `Get-ChildItem` commande est enregistrée dans la `$A` variable avant d’être envoyée à `Out-GridView` .

### Exemple 5 : processus de sortie pour un ordinateur spécifié vers un affichage de grille

Cet exemple affiche les processus en cours d’exécution sur l’ordinateur SERVEUR01 dans une fenêtre d’affichage de grille.

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

Exemple utilise `ogv` , qui est l’alias de l’applet de commande `Out-GridView` . Le paramètre **title** spécifie le titre de la fenêtre.

### Exemple 6 : sortie des données des ordinateurs distants vers un affichage de grille

Cet exemple montre comment envoyer des données collectées à partir d’ordinateurs distants vers `Out-GridView` .

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

`Invoke-Command` s’exécute `Get-Culture` sur trois ordinateurs distants. Les données résultantes sont redirigées vers `Out-GridView` . Notez que le bloc de script qui s’exécute sur l’ordinateur distant n’inclut pas la `Out-GridView` commande. Si tel était le cas, la commande échouerait quand elle essaierait d'ouvrir une fenêtre d'affichage de grille sur chacun des ordinateurs distants.

### Exemple 7 : passer plusieurs éléments à `Out-GridView`

Cet exemple vous permet de sélectionner plusieurs processus dans la `Out-GridView` fenêtre. Les processus que vous sélectionnez sont passés à la `Export-Csv` commande et écrits dans le `ProcessLog.csv` fichier.

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

Le paramètre **PassThru** de `Out-GridView` vous permet d’envoyer plusieurs éléments vers le dessous du pipeline. Le paramètre **PassThru** équivaut à l'utilisation de la valeur **Multiple** du paramètre **OutputMode** .

### Exemple 8 : créer un raccourci Windows vers `Out-GridView`

Cet exemple montre comment utiliser le paramètre **Wait** de `Out-GridView` pour créer un raccourci Windows dans la `Out-GridView` fenêtre.

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

Cette ligne de commande peut être utilisée dans un raccourci Windows. Sans le paramètre **Wait** , PowerShell s’arrête dès que la fenêtre s’est `Out-GridView` ouverte, ce qui ferme la `Out-GridView` fenêtre presque immédiatement.

## PARAMETERS

### -InputObject

Spécifie l’objet que l’applet de commande accepte comme entrée pour `Out-GridView` .

Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Out-GridView` , `Out-GridView` traite la collection comme un objet de collection et affiche une ligne qui représente la collection. Pour afficher chaque objet de la collection, utilisez un opérateur de pipeline (|) pour envoyer des objets à `Out-GridView` .

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

### -Du outputmode

Spécifie les éléments que la fenêtre interactive envoie au pipeline en tant qu’entrée d’autres commandes.
Par défaut, cette applet de commande ne génère aucun résultat. Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.

Les valeurs de ce paramètre déterminent le nombre d'éléments que vous pouvez envoyer dans le pipeline.

- Aucun.  aucun élément. Il s’agit de la valeur par défaut.
- Unique. zéro ou un élément. Utilisez cette valeur lorsque la commande suivante ne peut prendre qu'un seul objet en entrée.
- Plusieurs. zéro, un ou plusieurs éléments. Utilisez cette valeur lorsque la commande suivante peut prendre plusieurs objets en entrée. Cette valeur est équivalente au paramètre **Passthru** .

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Indique que l’applet de commande envoie les éléments à partir de la fenêtre interactive dans le pipeline en tant qu’entrée d’autres commandes. Par défaut, cette applet de commande ne génère aucun résultat. Ce paramètre est équivalent à l'utilisation de la valeur **Multiple** du paramètre **OutputMode** .

Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK. MAJ+clic et Ctrl+clic sont pris en charge.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

Spécifie le texte qui apparaît dans la barre de titre de la `Out-GridView` fenêtre. Par défaut, la barre de titre affiche la commande qui appelle `Out-GridView` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

Indique que l’applet de commande supprime l’invite de commandes et empêche Windows PowerShell de se fermer jusqu’à la fermeture de la `Out-GridView` fenêtre. Par défaut, l’invite de commandes retourne quand la `Out-GridView` fenêtre s’ouvre.

Cette fonctionnalité vous permet d’utiliser les `Out-GridView` applets de commande dans les raccourcis Windows. Quand `Out-GridView` est utilisé dans un raccourci sans le paramètre **Wait** , la `Out-GridView` fenêtre s’affiche uniquement momentanément avant la fermeture de PowerShell.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez envoyer n’importe quel objet à cette applet de commande.

## SORTIES

### Aucun

Normalement, `Out-GridView` ne retourne pas d’objets. Lors de l’utilisation du paramètre **PassThru** , les objets représentant les lignes sélectionnées sont retournés au pipeline.

## REMARQUES

Vous ne pouvez pas utiliser une commande distante pour ouvrir une fenêtre d'affichage de grille sur un autre ordinateur.

La sortie de commande que vous envoyez à `Out-GridView` ne peut pas être mise en forme à l’aide des `Format` applets de commande, telles que `Format-Table` ou `Format-Wide` cmdlets. Pour sélectionner des propriétés, utilisez l’applet de commande `Select-Object` .

La sortie désérialisée à partir des commandes distantes ne peut pas être correctement mise en forme dans la fenêtre d'affichage de grille.

**Raccourcis clavier pour**`Out-GridView`

|              Utilisez cette clé :              |                                   Pour exécuter cette action :                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <kbd>Onglet</kbd>                          | Déplace le curseur de la zone **filtre** vers le menu **Ajouter des critères** vers la table et inversement. |
| <kbd>Haut</kbd>                      | Remonter d’une ligne. Se déplace vers les en-têtes de colonne à partir de la première ligne de données.                             |
| <kbd>Flèche</kbd>                    | Descendre d’une ligne.                                                                           |
| <kbd>Flèche gauche</kbd>                    | Dans ligne d’en-tête de colonne, déplacer d’une colonne vers la gauche.                                                  |
| <kbd>Flèche droite</kbd>                   | Dans ligne d’en-tête de colonne, déplacer vers la droite d’une colonne.                                                 |
| <kbd>ContextMenuKey</kbd>               | Dans ligne d’en-tête de colonne, affiche l’option Sélectionner les colonnes.                                    |
| <kbd>Entrée</kbd> ou <kbd>barre d’espace</kbd> | Dans la ligne d’en-tête de colonne, triez les données de la colonne (basculez A-Z, Z-A).                                    |

**Comment utiliser les fonctionnalités de la fenêtre d’affichage de grille**

**Pour masquer ou afficher une colonne :**

1. Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes** .
2. Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les touches de direction pour déplacer les colonnes entre les colonnes sélectionnées dans les zones colonnes disponibles. Seules les colonnes de la zone **Sélectionner les colonnes** s’affichent dans la fenêtre d’affichage de grille.

**Pour réorganiser les colonnes :**

Vous pouvez faire glisser et déposer des colonnes à l’emplacement souhaité. Ou procédez comme suit :

1. Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes** .
2. Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les boutons **monter** **et descendre pour** réorganiser les colonnes. Les colonnes en haut de la liste apparaissent à gauche des colonnes au bas de la liste dans la fenêtre d'affichage de grille.

**Comment trier les données de tableau**

- Pour trier les données, cliquez sur un en-tête de colonne.
- Pour modifier l’ordre de tri, cliquez de nouveau sur l’en-tête de colonne. Chaque fois que vous cliquez sur le même en-tête, l'ordre de tri bascule de croissant à décroissant (ou inversement). L'ordre actif est indiqué par un triangle dans l'en-tête de colonne.

**Comment sélectionner les données de tableau**

- Pour sélectionner une ligne, sélectionnez la ligne ou utilisez la flèche haut ou bas pour accéder à la ligne.
- Pour sélectionner toutes les lignes (à l’exception de la ligne d’en-tête), appuyez sur <kbd>CTRL</kbd> + <kbd>A</kbd>.
- Pour sélectionner des lignes consécutives, maintenez la touche <kbd>MAJ</kbd> enfoncée tout en cliquant sur les lignes ou en utilisant les touches de direction.
- Pour sélectionner des lignes non consécutives, appuyez sur la touche <kbd>CTRL</kbd> et cliquez pour ajouter une ligne à la sélection.
- Vous ne pouvez pas sélectionner des colonnes et vous ne pouvez pas sélectionner la ligne d'en-tête d'une colonne entière.

**Comment copier des lignes**

- Pour copier une ou plusieurs lignes de la table, sélectionnez les lignes, puis appuyez sur CTRL + C.

  Vous pouvez coller les données dans n'importe quel tableur ou traitement de texte. Vous ne pouvez pas copier des colonnes ou des parties de ligne et vous ne pouvez pas copier la ligne d'en-tête de colonne.

**Comment effectuer une recherche dans le tableau (filtre rapide)**

Utilisez la zone de filtre pour rechercher des données dans la table. Lorsque vous entrez une valeur dans la zone, seuls les éléments qui incluent le texte entré apparaissent dans le tableau.

- Recherchez du texte. Pour rechercher du texte dans le tableau, dans la zone de filtre, tapez le texte à rechercher.
- Rechercher plusieurs mots. Pour rechercher plusieurs mots dans le tableau, tapez les mots séparés par un espace. `Out-GridView` affiche les lignes qui incluent tous les mots (AND logique).
- Recherchez des expressions littérales. Pour rechercher une expression qui comporte des espaces ou des caractères spéciaux, placez-la entre guillemets. `Out-GridView` affiche les lignes qui incluent une correspondance exacte pour l’expression.
- Rechercher dans les colonnes. Pour rechercher un texte dans une ou plusieurs colonnes, utilisez le format suivant :

  `<column>:<text> [<column>:<text>] ...`

  Par exemple, pour rechercher « net » dans la colonne **DisplayName** , dans la zone de **filtre** , tapez :

  `displayname:net`

  Pour rechercher des lignes avec « net » dans les colonnes **DisplayName** et **Name** , dans la zone de **filtre** , tapez :

  `displayname:net name:net`

- Désactiver la recherche. Pour afficher à nouveau la totalité du tableau, cliquez sur le bouton X rouge dans le coin supérieur droit de la zone de **filtre** ou supprimez le texte de la zone de **filtre** .

**Utiliser des critères pour filtrer le tableau**

Vous pouvez utiliser des règles ou des critères pour déterminer les éléments qui sont affichés dans le tableau. Les éléments s’affichent uniquement lorsqu’ils répondent à tous les critères que vous établissez. Les critères disponibles sont déterminés par les propriétés des objets affichés dans la fenêtre d'affichage de grille et les types .NET Framework de ces propriétés.

Chaque critère a le format suivant :

`<column> <operator> <value>`

Les critères des différentes propriétés sont connectés par **et** . Les critères de la même propriété sont connectés par **ou** . Vous ne pouvez pas modifier les connecteurs logiques.

Les critères affectent uniquement l'affichage. Ils ne suppriment pas des éléments du tableau.

**Comment ajouter des critères**

1. Pour afficher le bouton de menu **Ajouter des critères** , dans le coin supérieur droit de la fenêtre, cliquez sur la flèche de développement.
2. Cliquez sur le bouton de menu **Ajouter des critères** .
3. Cliquez pour sélectionner les colonnes (propriétés). Vous pouvez sélectionner une ou plusieurs propriétés.
4. Lorsque vous avez fini de sélectionner les propriétés, cliquez sur le bouton **Ajouter** .
5. Pour annuler les ajouts, cliquez sur **Annuler** .
6. Pour ajouter d’autres critères, cliquez de nouveau sur le bouton **Ajouter des critères** .

**Comment modifier un critère**

- Pour modifier un opérateur, cliquez sur la valeur de l’opérateur bleu, puis sélectionnez un autre opérateur dans la liste déroulante.
- Pour entrer ou modifier une valeur, tapez une valeur dans la zone valeur. Si vous entrez une valeur qui n'est pas valide, une icône en forme de X s'affiche. Pour supprimer la valeur, modifiez-la.
- Pour créer une instruction **ou** , ajoutez un critère avec la même propriété.

**Comment supprimer des critères**

- Pour supprimer les critères sélectionnés, cliquez sur la Croix Rouge en regard de chaque critère.
- Pour supprimer tous les critères, cliquez sur le bouton **Effacer tout** .

## LIENS CONNEXES

[Out-File](Out-File.md)

[Out-Printer](Out-Printer.md)

[Out-String](Out-String.md)

